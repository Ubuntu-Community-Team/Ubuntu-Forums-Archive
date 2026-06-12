---
title: "installing Synchronet bbs"
date: 2008-09-21
forum: General Help
---

### Post by lanr01 on 2008-09-21
Hello from a newbie to ubuntu or any nix... I have been running a bbs for a fair number of years. started under dos and then qemm with desqview. on to Windblows for long time.. I have just finished getting my system setup with ubuntu and want to install synchronet, but I am having a bit of tough time installing it. I wanted to see who here was running it and ask how they did the initial install. I have downloaded the  sbbs_src.tgz file and unpacked it in its own sbbs dir. But everytime I try to set it up and install I get no where.. I know I need to do this from a command line, but nothing I do does much of anything other than error out. I am out of my element and lost...

Rick

---

### Post by L0cKd0wN on 2008-09-21
Hi Rick.  First off, I would make no comparison between DOS and a GNU/Linux bash shell.  They are horses of a different color.  I've never used Synchronet personally, but it looks like they have rather extensive documentation on their web site at:

[http://www.synchro.net/docs/index.htm](http://www.synchro.net/docs/index.htm)

I suggest following along with their installation guide FIRST, and then post specific problems or errors you come across.  Typically, source installs will require a "./configure, make, make install" routine for getting them compiled (and more importantly useful).  Saying you are "getting no where" isn't helpful for us, nor is it helpful for you. Try not to be vague! Finally, it looks like your proficiency may be low, so I recommend the following link to help get you up to speed, and more comfortable with the shell:

[http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz) 

Hope this pushes you in the right direction.  

Regards,
L0cK

---

### Post by Gun_Smoke on 2008-09-28
Where am I going wrong/missing?

#make

```
make -C /sbbs/src/sbbs3/../smblib lib
make[1]: Entering directory `/sbbs/src/smblib'
make[1]: Nothing to be done for `lib'.
make[1]: Leaving directory `/sbbs/src/smblib'
make -C /sbbs/src/sbbs3/../xpdev mtlib
make[1]: Entering directory `/sbbs/src/xpdev'
make[1]: Nothing to be done for `mtlib'.
make[1]: Leaving directory `/sbbs/src/xpdev'
Compiling ansiterm.cpp
In file included from ansiterm.cpp:38:
sbbs.h:109:20: warning: jsapi.h: No such file or directory
sbbs.h:110:53: warning: jsprf.h: No such file or directory
sbbs.h:111:45: warning: jsnum.h: No such file or directory
sbbs.h:116:22: warning: cryptlib.h: No such file or directory
In file included from ansiterm.cpp:38:
sbbs.h:180: error: ‘CRYPT_SESSION’ does not name a type
sbbs.h:228: error: ISO C++ forbids declaration of ‘JSRuntime’ with no type
sbbs.h:228: error: expected ‘;’ before ‘*’ token
sbbs.h:229: error: ISO C++ forbids declaration of ‘JSContext’ with no type
sbbs.h:229: error: expected ‘;’ before ‘*’ token
sbbs.h:230: error: ISO C++ forbids declaration of ‘JSObject’ with no type
sbbs.h:230: error: expected ‘;’ before ‘*’ token
sbbs.h:930: error: ‘JSNative’ does not name a type
sbbs.h:931: error: ‘uint8’ does not name a type
sbbs.h:940: error: ‘int8’ does not name a type
sbbs.h:941: error: ‘uint8’ does not name a type
sbbs.h:959: error: ‘JSTYPE_LIMIT’ was not declared in this scope
sbbs.h:974: error: ‘JSBool’ does not name a type
sbbs.h:975: error: ‘JSBool’ does not name a type
sbbs.h:976: error: ‘JSBool’ does not name a type
sbbs.h:977: error: ‘JSBool’ does not name a type
sbbs.h:978: error: ‘JSBool’ does not name a type
sbbs.h:979: error: ‘JSBool’ does not name a type
sbbs.h:980: error: ‘JSBool’ does not name a type
sbbs.h:982: error: ‘JSContext’ was not declared in this scope
sbbs.h:982: error: ‘cx’ was not declared in this scope
sbbs.h:982: error: ‘jsval’ was not declared in this scope
sbbs.h:982: error: expected primary-expression before ‘*’ token
sbbs.h:982: error: ‘len’ was not declared in this scope
sbbs.h:982: error: initializer expression list treated as compound expression
sbbs.h:987: error: expected constructor, destructor, or type conversion before ‘*’ token
sbbs.h:991: error: expected constructor, destructor, or type conversion before ‘*’ token
sbbs.h:992: error: expected constructor, destructor, or type conversion before ‘*’ token
sbbs.h:1006: error: expected constructor, destructor, or type conversion before ‘*’ token
sbbs.h:1007: error: ‘JSBool’ does not name a type
sbbs.h:1008: error: variable or field ‘js_EvalOnExit’ declared void
sbbs.h:1008: error: ‘JSContext’ was not declared in this scope
sbbs.h:1008: error: expected primary-expression before ‘,’ token
sbbs.h:1008: error: ‘JSObject’ was not declared in this scope
sbbs.h:1008: error: expected primary-expression before ‘,’ token
sbbs.h:1008: error: expected primary-expression before ‘*’ token
sbbs.h:1008: error: expected primary-expression before ‘)’ token
sbbs.h:1011: error: expected constructor, destructor, or type conversion before ‘*’ token
sbbs.h:1017: error: expected constructor, destructor, or type conversion before ‘*’ token
sbbs.h:1020: error: expected constructor, destructor, or type conversion before ‘*’ token
sbbs.h:1021: error: expected constructor, destructor, or type conversion before ‘*’ token
sbbs.h:1023: error: ‘JSBool’ does not name a type
sbbs.h:1027: error: expected constructor, destructor, or type conversion before ‘*’ token
sbbs.h:1031: error: expected constructor, destructor, or type conversion before ‘*’ token
sbbs.h:1033: error: ‘JSContext’ was not declared in this scope
sbbs.h:1033: error: ‘cx’ was not declared in this scope
sbbs.h:1033: error: expected primary-expression before ‘*’ token
sbbs.h:1033: error: ‘cfg’ was not declared in this scope
sbbs.h:1034: error: ‘JSObject’ was not declared in this scope
sbbs.h:1034: error: ‘subobj’ was not declared in this scope
sbbs.h:1034: error: expected primary-expression before ‘subnum’
sbbs.h:1034: error: initializer expression list treated as compound expression
sbbs.h:1037: error: expected constructor, destructor, or type conversion before ‘*’ token
sbbs.h:1041: error: expected constructor, destructor, or type conversion before ‘*’ token
sbbs.h:1042: error: ‘JSContext’ was not declared in this scope
sbbs.h:1042: error: ‘cx’ was not declared in this scope
sbbs.h:1042: error: ‘JSObject’ was not declared in this scope
sbbs.h:1042: error: ‘hdrobj’ was not declared in this scope
sbbs.h:1042: error: expected primary-expression before ‘*’ token
sbbs.h:1042: error: expected primary-expression before ‘)’ token
sbbs.h:1042: error: initializer expression list treated as compound expression
sbbs.h:1045: error: expected constructor, destructor, or type conversion before ‘*’ token
sbbs.h:1046: error: expected constructor, destructor, or type conversion before ‘*’ token
sbbs.h:1048: error: variable or field ‘js_timeval’ declared void
sbbs.h:1048: error: ‘JSContext’ was not declared in this scope
sbbs.h:1048: error: ‘cx’ was not declared in this scope
sbbs.h:1048: error: ‘jsval’ was not declared in this scope
sbbs.h:1048: error: expected primary-expression before ‘struct’
sbbs.h:1049: error: ‘JSContext’ was not declared in this scope
sbbs.h:1049: error: ‘cx’ was not declared in this scope
sbbs.h:1049: error: ‘jsval’ was not declared in this scope
sbbs.h:1049: error: initializer expression list treated as compound expression
sbbs.h:1052: error: expected constructor, destructor, or type conversion before ‘*’ token
sbbs.h:1053: error: expected constructor, destructor, or type conversion before ‘*’ token
sbbs.h:1055: error: ‘JSContext’ was not declared in this scope
sbbs.h:1055: error: ‘cx’ was not declared in this scope
sbbs.h:1055: error: expected primary-expression before ‘*’ token
sbbs.h:1055: error: ‘q’ was not declared in this scope
sbbs.h:1055: error: ‘jsval’ was not declared in this scope
sbbs.h:1055: error: expected primary-expression before ‘char’
sbbs.h:1055: error: initializer expression list treated as compound expression
sbbs.h:1058: error: expected constructor, destructor, or type conversion before ‘*’ token
sbbs.h:1061: error: ‘JSContext’ was not declared in this scope
sbbs.h:1061: error: ‘cx’ was not declared in this scope
sbbs.h:1061: error: expected primary-expression before ‘argn’
sbbs.h:1061: error: ‘uintN’ was not declared in this scope
sbbs.h:1061: error: ‘jsval’ was not declared in this scope
sbbs.h:1061: error: ‘argv’ was not declared in this scope
sbbs.h:1061: error: initializer expression list treated as compound expression
sbbs.h:1065: error: expected constructor, destructor, or type conversion before ‘*’ token
sbbs.h:1068: error: expected constructor, destructor, or type conversion before ‘*’ token
sbbs.h:1071: error: expected constructor, destructor, or type conversion before ‘*’ token
sbbs.h:1074: error: expected constructor, destructor, or type conversion before ‘*’ token
make: *** [gcc.linux.obj.debug-mt/ansiterm.o] Error 1
```

---

### Post by Gun_Smoke on 2008-09-28
Got it..

---

### Post by Sierra-X on 2008-10-01
> **Gun_Smoke said:**
> Got it..

Care to enlighten the rest of us?  I'm having similar issues.

---

### Post by Gun_Smoke on 2008-10-01
build-essentials libncurses5-dev g++ libnspr4-dev libmozjs-dev


give it a go with those

---

### Post by Sierra-X on 2008-10-01
Ah, thank you very much - now to get LORD working.  Apparently the dosemu from the repos doesn't like to run as anything but root...

---

