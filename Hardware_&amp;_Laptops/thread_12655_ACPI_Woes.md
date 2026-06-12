---
title: "ACPI Woes"
date: 2005-01-26
forum: Hardware &amp; Laptops
---

### Post by bitfoo on 2005-01-26
Hello! I am trying to get my acpi to work correctly on ubuntu.  Unfortunately it is not.  I have an Asus M6N and have been reading at other sites at tuxmobil.org on what to do. The ac adapter status will only show that it is plugged in not the amount of batter life that is left.  I tried to dmesg to see if acpi was installed and i believe it is.

bitfoo@horus:~ $ dmesg | grep acpi
bitfoo@horus:~ $

So I have the choice to either patch the kernel with some patch for 2.6.5 kernel, or hack a dsdt table to fix Asus's mistake. The kernel patching sounds tough, and since i did an apt-get install linux-686 to replace the 386 kernel I am afraid things have changed. :/ So I decided to go with the hacking. Unfortunately the acpi sourceforge page says to use intel's IASL compiler to recompile a DSDT table.  But intel only makes unix and window's versions, and the unix version doesn't compile! Argh.

```
bitfoo@horus:~/acpica-unix-20041203/compiler $ make
bison -v -d -y -pAslCompiler aslcompiler.y
conflicts: 57 shift/reduce, 50 reduce/reduce
aslcompiler.y:913.7-81: warning: rule never reduced because of conflicts: TermArg: Type2IntegerOpcode
aslcompiler.y:914.7-81: warning: rule never reduced because of conflicts: TermArg: Type2StringOpcode
aslcompiler.y:915.7-81: warning: rule never reduced because of conflicts: TermArg: Type2BufferOpcode
aslcompiler.y:916.7-81: warning: rule never reduced because of conflicts: TermArg: Type2BufferOrStringOpcode
aslcompiler.y:958.7-82: warning: rule never reduced because of conflicts: OptionalParameterTypePackage: ','
aslcompiler.y:981.7-82: warning: rule never reduced because of conflicts: OptionalParameterTypesPackage: ','
aslcompiler.y:1572.7-38: warning: rule never reduced because of conflicts: CaseTermList: CaseTerm
aslcompiler.y:1581.7-38: warning: rule never reduced because of conflicts: DefaultTermList: CaseTerm
aslcompiler.y:3062.37-48: warning: rule never reduced because of conflicts: OptionalResourceType: /* empty */
cp y.tab.c aslcompilerparse.c
cp y.tab.h aslcompiler.y.h
cc -Wall -O2 -Wstrict-prototypes -D_LINUX -D_ACPI_ASL_COMPILER -I../include    -c -o aslcompilerparse.o aslcompilerparse.c
flex -i -PAslCompiler -oaslcompilerlex.c aslcompiler.l
cc -Wall -O2 -Wstrict-prototypes -D_LINUX -D_ACPI_ASL_COMPILER -I../include    -c -o aslcompilerlex.o aslcompilerlex.caslcompiler.l: In function `comment':
aslcompiler.l:846: error: `yytext_ptr' undeclared (first use in this function)
aslcompiler.l:846: error: (Each undeclared identifier is reported only once
aslcompiler.l:846: error: for each function it appears in.)
make: *** [aslcompilerlex.o] Error 1
bitfoo@horus:~/acpica-unix-20041203/compiler $ acpi -V
     Thermal 1: ok, 60.0 degrees C
  AC Adapter 1: on-line
bitfoo@horus:~/acpica-unix-20041203/compiler $
```

So I am at my wits end.  And all I want is for the damn battery status to show.  I know when it is plugged in.  I want to know how much battery life I have left. :(

/me cries

---

### Post by hardcandy on 2005-01-26
Did not know if you had seen these sites:
[http://m6n.ath.cx/m6n.html](http://m6n.ath.cx/m6n.html)

[http://m6n.ath.cx/forum/viewforum.php?f=6&sid=8c7d66d4e45260443d3ef1ba63f3e17a](http://m6n.ath.cx/forum/viewforum.php?f=6&sid=8c7d66d4e45260443d3ef1ba63f3e17a)

---

### Post by bitfoo on 2005-01-26
Yes that is where I got the information from on how to do what I need to do.  But it doesn't compile. :|

EDIT: I have managed to compile it using WINE and the win32 binary.  It still looks insanely tough so I may just have to recompile the kernel. Which I have no idea how to do :D

---

### Post by briguy on 2005-03-16
I have the exact same problem compiling the intel compiler.  It wouldn't even get that far until I installed bison and flex through synaptic.  Anyone know the other packages required to compile this program?

---

### Post by lizhao on 2005-08-24
[QUOTE=briguy]I have the exact same problem compiling the intel compiler.  It wouldn't even get that far until I installed bison and flex through synaptic.  Anyone know the other packages required to compile this program?[/QUOTE]

flex_old

---

