---
title: "IASL errors"
date: 2007-05-19
forum: Hardware &amp; Laptops
---

### Post by Ryanson on 2007-05-19
Hello all.

I am trying to fix my DSDT. The first thing I am doing is trying to install the IASL compiler, but I keep getting errors.

Here is what I am getting when I try 'make' in the 'compiler' directory.

bison -v -d -y -pAslCompiler aslcompiler.y
aslcompiler.y:1114.7-1117.75: warning: unused value: $6
aslcompiler.y:1329.7-1337.134: warning: unused value: $6
aslcompiler.y:1481.7-1486.74: warning: unused value: $10
aslcompiler.y:1481.7-1486.74: warning: unused value: $12
aslcompiler.y:2585.7-2600.120: warning: unused value: $5
aslcompiler.y:2657.7-2671.116: warning: unused value: $5
aslcompiler.y:2818.7-2833.120: warning: unused value: $5
aslcompiler.y:2929.7-2944.120: warning: unused value: $5
aslcompiler.y:3083.37-48: warning: rule never reduced because of conflicts: OptionalResourceType: /* empty */
cp y.tab.c aslcompilerparse.c
cp y.tab.h aslcompiler.y.h
cc -Wall -O2 -Wstrict-prototypes -D_LINUX -DACPI_ASL_COMPILER -I../include    -c -o aslcompilerparse.o aslcompilerparse.c
In file included from aslcompiler.y:127:
aslcompiler.h:134:19: error: stdio.h: No such file or directory
aslcompiler.h:135:20: error: stdlib.h: No such file or directory
aslcompiler.h:137:20: error: string.h: No such file or directory
aslcompiler.h:138:19: error: errno.h: No such file or directory
aslcompiler.h:139:19: error: ctype.h: No such file or directory
In file included from ../include/platform/acenv.h:215,
                 from ../include/acpi.h:127,
                 from aslcompiler.h:142,
                 from aslcompiler.y:127:
../include/platform/aclinux.h:148:20: error: unistd.h: No such file or directory
In file included from aslcompiler.h:149,
                 from aslcompiler.y:127:
asltypes.h:221: error: expected specifier-qualifier-list before ‘FILE’
In file included from aslcompiler.h:150,
                 from aslcompiler.y:127:
aslglobal.h:143: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
aslglobal.h:254: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
In file included from aslcompiler.y:127:
aslcompiler.h:188: error: expected ‘)’ before ‘*’ token
y.tab.c:7381: error: expected ‘)’ before ‘*’ token
y.tab.c:7413: error: expected ‘)’ before ‘*’ token
y.tab.c: In function ‘yy_stack_print’:
y.tab.c:7447: warning: implicit declaration of function ‘fprintf’
y.tab.c:7447: warning: incompatible implicit declaration of built-in function ‘fprintf’
y.tab.c:7447: error: ‘stderr’ undeclared (first use in this function)
y.tab.c:7447: error: (Each undeclared identifier is reported only once
y.tab.c:7447: error: for each function it appears in.)
y.tab.c: In function ‘yy_reduce_print’:
y.tab.c:7478: warning: incompatible implicit declaration of built-in function ‘fprintf’
y.tab.c:7478: error: ‘stderr’ undeclared (first use in this function)
y.tab.c:7484: warning: implicit declaration of function ‘yy_symbol_print’
y.tab.c: In function ‘yydestruct’:
y.tab.c:7758: warning: incompatible implicit declaration of built-in function ‘fprintf’
y.tab.c:7758: error: ‘stderr’ undeclared (first use in this function)
y.tab.c: In function ‘AslCompilerparse’:
y.tab.c:7872: warning: incompatible implicit declaration of built-in function ‘fprintf’
y.tab.c:7872: error: ‘stderr’ undeclared (first use in this function)
y.tab.c:7958: warning: incompatible implicit declaration of built-in function ‘fprintf’
y.tab.c:7965: warning: incompatible implicit declaration of built-in function ‘fprintf’
y.tab.c:7987: warning: incompatible implicit declaration of built-in function ‘fprintf’
y.tab.c:7994: warning: incompatible implicit declaration of built-in function ‘fprintf’
y.tab.c:7999: warning: incompatible implicit declaration of built-in function ‘fprintf’
y.tab.c:8025: warning: incompatible implicit declaration of built-in funbison -v -d -y -pAslCompiler aslcompiler.y
aslcompiler.y:1114.7-1117.75: warning: unused value: $6
aslcompiler.y:1329.7-1337.134: warning: unused value: $6
aslcompiler.y:1481.7-1486.74: warning: unused value: $10
aslcompiler.y:1481.7-1486.74: warning: unused value: $12
aslcompiler.y:2585.7-2600.120: warning: unused value: $5
aslcompiler.y:2657.7-2671.116: warning: unused value: $5
aslcompiler.y:2818.7-2833.120: warning: unused value: $5
aslcompiler.y:2929.7-2944.120: warning: unused value: $5
aslcompiler.y:3083.37-48: warning: rule never reduced because of conflicts: OptionalResourceType: /* empty */
cp y.tab.c aslcompilerparse.c
cp y.tab.h aslcompiler.y.h
cc -Wall -O2 -Wstrict-prototypes -D_LINUX -DACPI_ASL_COMPILER -I../include    -c -o aslcompilerparse.o aslcompilerparse.c
In file included from aslcompiler.y:127:
aslcompiler.h:134:19: error: stdio.h: No such file or directory
aslcompiler.h:135:20: error: stdlib.h: No such file or directory
aslcompiler.h:137:20: error: string.h: No such file or directory
aslcompiler.h:138:19: error: errno.h: No such file or directory
aslcompiler.h:139:19: error: ctype.h: No such file or directory
In file included from ../include/platform/acenv.h:215,
                 from ../include/acpi.h:127,
                 from aslcompiler.h:142,
                 from aslcompiler.y:127:
../include/platform/aclinux.h:148:20: error: unistd.h: No such file or directory
In file included from aslcompiler.h:149,
                 from aslcompiler.y:127:
asltypes.h:221: error: expected specifier-qualifier-list before ‘FILE’
In file included from aslcompiler.h:150,
                 from aslcompiler.y:127:
aslglobal.h:143: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
aslglobal.h:254: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
In file included from aslcompiler.y:127:
aslcompiler.h:188: error: expected ‘)’ before ‘*’ token
y.tab.c:7381: error: expected ‘)’ before ‘*’ token
y.tab.c:7413: error: expected ‘)’ before ‘*’ token
y.tab.c: In function ‘yy_stack_print’:
y.tab.c:7447: warning: implicit declaration of function ‘fprintf’
y.tab.c:7447: warning: incompatible implicit declaration of built-in function ‘fprintf’
y.tab.c:7447: error: ‘stderr’ undeclared (first use in this function)
y.tab.c:7447: error: (Each undeclared identifier is reported only once
y.tab.c:7447: error: for each function it appears in.)
y.tab.c: In function ‘yy_reduce_print’:
y.tab.c:7478: warning: incompatible implicit declaration of built-in function ‘fprintf’
y.tab.c:7478: error: ‘stderr’ undeclared (first use in this function)
y.tab.c:7484: warning: implicit declaration of function ‘yy_symbol_print’
y.tab.c: In function ‘yydestruct’:
y.tab.c:7758: warning: incompatible implicit declaration of built-in function ‘fprintf’
y.tab.c:7758: error: ‘stderr’ undeclared (first use in this function)
y.tab.c: In function ‘AslCompilerparse’:
y.tab.c:7872: warning: incompatible implicit declaration of built-in function ‘fprintf’
y.tab.c:7872: error: ‘stderr’ undeclared (first use in this function)
y.tab.c:7958: warning: incompatible implicit declaration of built-in function ‘fprintf’
y.tab.c:7965: warning: incompatible implicit declaration of built-in function ‘fprintf’
y.tab.c:7987: warning: incompatible implicit declaration of built-in function ‘fprintf’
y.tab.c:7994: warning: incompatible implicit declaration of built-in function ‘fprintf’
y.tab.c:7999: warning: incompatible implicit declaration of built-in function ‘fprintf’
y.tab.c:8025: warning: incompatible implicit declaration of built-in function ‘fprintf’
y.tab.c:12290: warning: incompatible implicit declaration of built-in function ‘fprintf’
y.tab.c:12444: warning: incompatible implicit declaration of built-in function ‘fprintf’
aslcompiler.y: In function ‘AslLocalAllocate’:
aslcompiler.y:3175: error: ‘struct asl_file_info’ has no member named ‘Filename’
aslcompiler.y:3176: warning: implicit declaration of function ‘exit’
aslcompiler.y:3176: warning: incompatible implicit declaration of built-in function ‘exit’
make: *** [aslcompilerparse.o] Error 1
ction ‘fprintf’
y.tab.c:12290: warning: incompatible implicit declaration of built-in function ‘fprintf’
y.tab.c:12444: warning: incompatible implicit declaration of built-in function ‘fprintf’
aslcompiler.y: In function ‘AslLocalAllocate’:
aslcompiler.y:3175: error: ‘struct asl_file_info’ has no member named ‘Filename’
aslcompiler.y:3176: warning: implicit declaration of function ‘exit’
aslcompiler.y:3176: warning: incompatible implicit declaration of built-in function ‘exit’
make: *** [aslcompilerparse.o] Error 1

I am pretty much a linux newbie, so I have no idea what the problem may be.

Any idea would be much appreciated, thank you.

---

### Post by kadirmalak on 2007-12-23
I think some header files are missing,
try to install missing development files 
(for example libstdc++X.XX-dev : where X is an integer)

---

