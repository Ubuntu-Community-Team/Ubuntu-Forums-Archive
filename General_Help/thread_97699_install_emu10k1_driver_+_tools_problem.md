---
title: "install emu10k1 driver + tools problem"
date: 2005-12-01
forum: General Help
---

### Post by Vilhelmo on 2005-12-01
I've been trying to get my Emu10k1 based soundcard to work since i installed Ubuntu, about 2 weeks ago (so I'm new to linux). I've searched through the forums with no luck. 

When I am about to compile my drivers or tools the results are just the following:
```
vilhelm@dumburken:~/Desktop/emu-tools-0.9.4$ sudo make install
cd as10k1 && make
make[1]: Entering directory `/home/vilhelm/Desktop/emu-tools-0.9.4/as10k1'
cc -M *.c -W -Wall > .depend
cc -W -Wall   -c -o as10k1.o as10k1.c
as10k1.c:42: error: missing terminating " character
as10k1.c:43: error: ‘Usage’ undeclared here (not in a function)
as10k1.c:43: error: syntax error before ‘:’ token
as10k1.c:46: error: missing terminating ' character
as10k1.c:48: error: stray ‘@’ in program
as10k1.c:49: error: stray ‘@’ in program
as10k1.c:52: error: stray ‘\’ in program
as10k1.c:68: error: missing terminating " character
as10k1.c:84: error: syntax error before ‘-’ token
as10k1.c:84: varning: type defaults to ‘int’ in declaration of ‘exit’
as10k1.c:84: error: conflicting types for ‘exit’
as10k1.c:84: varning: datadefinition har ingen typ eller lagringsklass
as10k1.c:86: varning: type defaults to ‘int’ in declaration of ‘output’
as10k1.c:86: error: conflicting types for ‘output’
as10k1.c:35: error: previous definition of ‘output’ was here
as10k1.c:86: error: ‘argv’ undeclared here (not in a function)
as10k1.c:86: error: ‘i’ undeclared here (not in a function)
as10k1.c:86: error: fältindex är inte ett heltal
as10k1.c:86: varning: datadefinition har ingen typ eller lagringsklass
as10k1.c:87: error: syntax error before ‘break’
as10k1.c:91: error: syntax error before string constant
as10k1.c:91: varning: type defaults to ‘int’ in declaration of ‘printf’
as10k1.c:91: error: conflicting types for ‘printf’
as10k1.c:91: note: a parameter list with an ellipsis can’t match an empty parameter name list declaration
as10k1.c:91: varning: datadefinition har ingen typ eller lagringsklass
as10k1.c:96: error: syntax error before string constant
as10k1.c:96: varning: type defaults to ‘int’ in declaration of ‘printf’
as10k1.c:96: error: conflicting types for ‘printf’
as10k1.c:96: note: a parameter list with an ellipsis can’t match an empty parameter name list declaration
as10k1.c:96: varning: datadefinition har ingen typ eller lagringsklass
as10k1.c:105: error: syntax error before string constant
as10k1.c:105: varning: type defaults to ‘int’ in declaration of ‘printf’
as10k1.c:105: error: conflicting types for ‘printf’
as10k1.c:105: note: a parameter list with an ellipsis can’t match an empty parameter name list declaration
as10k1.c:105: varning: datadefinition har ingen typ eller lagringsklass
as10k1.c:109: error: syntax error before string constant
as10k1.c:109: varning: type defaults to ‘int’ in declaration of ‘printf’
as10k1.c:109: error: conflicting types for ‘printf’
as10k1.c:109: note: a parameter list with an ellipsis can’t match an empty parameter name list declaration
as10k1.c:109: varning: datadefinition har ingen typ eller lagringsklass
as10k1.c:113: error: syntax error before string constant
as10k1.c:113: varning: type defaults to ‘int’ in declaration of ‘printf’
as10k1.c:113: error: conflicting types for ‘printf’
as10k1.c:113: note: a parameter list with an ellipsis can’t match an empty parameter name list declaration
as10k1.c:113: varning: datadefinition har ingen typ eller lagringsklass
as10k1.c:117: error: syntax error before string constant
as10k1.c:117: varning: type defaults to ‘int’ in declaration of ‘printf’
as10k1.c:117: error: conflicting types for ‘printf’
as10k1.c:117: note: a parameter list with an ellipsis can’t match an empty parameter name list declaration
as10k1.c:117: varning: datadefinition har ingen typ eller lagringsklass
as10k1.c:122: error: syntax error before ‘-’ token
as10k1.c:122: varning: type defaults to ‘int’ in declaration of ‘exit’
as10k1.c:122: error: conflicting types for ‘exit’
as10k1.c:122: varning: datadefinition har ingen typ eller lagringsklass
as10k1.c:126: error: syntax error before string constant
as10k1.c:126: varning: type defaults to ‘int’ in declaration of ‘printf’
as10k1.c:126: error: conflicting types for ‘printf’
as10k1.c:126: note: a parameter list with an ellipsis can’t match an empty parameter name list declaration
as10k1.c:126: varning: datadefinition har ingen typ eller lagringsklass
as10k1.c:134: error: syntax error before ‘-’ token
as10k1.c:134: varning: type defaults to ‘int’ in declaration of ‘exit’
as10k1.c:134: error: conflicting types for ‘exit’
as10k1.c:134: varning: datadefinition har ingen typ eller lagringsklass
as10k1.c:136: varning: type defaults to ‘int’ in declaration of ‘listing’
as10k1.c:136: error: conflicting types for ‘listing’
as10k1.c:35: error: previous definition of ‘listing’ was here
as10k1.c:136: error: fältindex är inte ett heltal
as10k1.c:136: varning: datadefinition har ingen typ eller lagringsklass
as10k1.c:139: error: syntax error before ‘break’
as10k1.c:142: error: syntax error before string constant
as10k1.c:142: varning: type defaults to ‘int’ in declaration of ‘printf’
as10k1.c:142: error: conflicting types for ‘printf’
as10k1.c:142: note: a parameter list with an ellipsis can’t match an empty parameter name list declaration
as10k1.c:142: varning: datadefinition har ingen typ eller lagringsklass
as10k1.c:151: error: syntax error before numeric constant
as10k1.c:151: varning: type defaults to ‘int’ in declaration of ‘exit’
as10k1.c:151: error: conflicting types for ‘exit’
as10k1.c:151: varning: datadefinition har ingen typ eller lagringsklass
as10k1.c:160: error: syntax error before string constant
as10k1.c:160: varning: type defaults to ‘int’ in declaration of ‘as_exit’
as10k1.c:160: error: conflicting types for ‘as_exit’
proto.h:6: error: previous declaration of ‘as_exit’ was here
as10k1.c:160: varning: datadefinition har ingen typ eller lagringsklass
as10k1.c: In function ‘main’:
as10k1.c:176: varning: implicit declaration of function ‘parse_cli_args’
as10k1.c:186: varning: jämförelse mellan pekare och heltal
as10k1.c:187: varning: passing argument 1 of ‘fopen’ makes pointer from integer without a cast
as10k1.c:193: varning: jämförelse mellan pekare och heltal
as10k1.c:197: varning: assignment makes integer from pointer without a cast
as10k1.c:201: varning: passing argument 1 of ‘fopen’ makes pointer from integer without a cast
make[1]: *** [as10k1.o] Fel 1
make[1]: Leaving directory `/home/vilhelm/Desktop/emu-tools-0.9.4/as10k1'
make: *** [As10k1] Fel 2

``` 

The same things happen when i try just "sudo make" or when I try to install the driver (which I think already is included in Ubuntu).
 I know some expressions are in swedish but maybe someone can give me a hint of what can be wrong?

btw I found this program today called Gemu which is a graphical editor for the settings for my soundcard (just what I want), but it needs the drivers to work. I can't install that program neither. The most important is not to get the graphical view, i just need to be able to use the tools to route my outputs so I can hear sound! please try to help me!

---

