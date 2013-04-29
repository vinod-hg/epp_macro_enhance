epp_macro_enhance
=================

Enhancement to Erlang epp module to handle complex user defined macros

Current epp module does not handle functions as macros. Function is passed instead of its structure which cannot be handled.

This is enhanced by adding a new function clause (three new lines) with the type as complex.

open(FileName, IncludePath, PredefMacros) -> {ok, Epp} | {error, ErrorDescriptor}

parse_file(FileName, IncludePath, PredefMacros) -> {ok, [Form]} | {error, OpenError}


PredefMacros = macros()
macros() = [{atom(), term()}] | [{atom(), Args, Definition}] 
Args = [atom()]
Definition = string()

Calling Example
---------------

epp:parse_file("../src/macro_test.erl", [], 
              [{'MUL', ['A','B'], "fun()-> io:format(\"~p*~p = ~p\", [A,B,A*B]) end" , complex}]),

