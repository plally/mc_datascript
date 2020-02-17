# Minecraft Datapack scripting language
check out [example_script](https://github.com/PLally/mc_datascript/blob/master/example_script) for an example of this language in use
### TODO
- print location of errors
- better error handling
- allow calling functions from different namespaces
- rewrite compile.go
- move lex.go and compile.go into separate packages
- add CONST support outside strings and commands 

### Info
- language keywords are allways uppercase e.g. `FUNC` `CONST` `SET` and are always followed by an identifier (a-z and `_`)
- `{` and `}` open and close a block, everything in a block will eventually be translated into a list of minecraft commands
- text enclosed in \` is interpreted as a minecraft command e.g. \`say "Hello World"\`
- `#{name}`  will look up any defined  `CONST` with that name, and `#{name}` will be replaced with the  `CONST`

### Keywords
- SET name = value    
can only be used inside a `{ Block }` sets a scoreboard variable in the scoreboard \<namespace\>_vars   
e.g. `SET foo = 10`
- FUNC name { Block }   
creates a new mc function with the commands generating by evaluating `{ Block }`   
e.g. `FUNC foo { CALL bar }`

- CONST name = value   
creates a constant that can be referenced in "strings" and \`commands\` using the syntax `#{name}`
- IF name comparison value { block }   
executes the commands generated by evaulating `{ Block }` if the condition is true   
e.g. `IF foo < 10 { CALL bar }`
