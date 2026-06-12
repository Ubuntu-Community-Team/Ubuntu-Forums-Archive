---
title: "how to read .so file in ubuntu"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by earth_tech on 2009-09-03
hi every one,
I am again face a problem. According your suggestion i can convert a .c file to .so file and tell me in which way i can open that .so file i.e. i want to see what will be the code after creating my .so file. I will be highly obliged if any one can give me more information .so file related.

---

### Post by miklcct on 2009-09-03
.so file is a shared library. It is not directly usable. It is fed into the linker when linking your programs.

Example:

foo.c:
```

#include<stdio.h>
#include"foo.h"

void foo(void){
 puts("foo");
}

```

foo.h:
```

#ifndef __foo_h
# define __foo_h
# ifdef __cplusplus
extern "C"{
# endif
void foo(void);
# ifdef __cplusplus
}
# endif
#endif

```

Build the library:
```

$ cc -std=c99 -fPIC -c foo.c -o foo.o # preprocess, compile, assemble foo.c to yield object file foo.o
$ cc -shared -Wl,-soname,libfoo.so.1 foo.o -o libfoo.so.1.0.0 # link foo.o to yield shared object libfoo.so.1.0.0
$ ln -s libfoo.so.1.0.0 libfoo.so.1
$ ln -s libfoo.so.1 libfoo.so # libfoo.so.1 is needed for run-time linking, libfoo.so is needed for compile-time linking

```

Install the library:
```

# cp foo.h /usr/local/include
# cp -a libfoo.so* /usr/local/lib
# chown root:root /usr/local/lib/libfoo.so* /usr/local/include/foo.h
# ldconfig

```

To see what functions are inside the library
```

$ nm /usr/local/lib/libfoo.so | grep ' T '

```

Output:
```

0000000000000648 T _fini
00000000000004e8 T _init
00000000000005fc T foo

```

The first 2 are added by the linker, the last one is the one that comes from the object code.

To build an application against this library:

test.c
```

#include<foo.h> // note that foo.h is now a standard header
int main(void){
 foo();
}

```

```

$ cc -std=c99 test.c -lfoo -o test # /usr/local/lib/libfoo.so is used
$ ./test # /usr/local/lib/libfoo.so.1 is used

```

output:
```

foo

```

To verify that the shared library is really used:
```

$ ldd test

```

output:
```

        linux-vdso.so.1 =>  (0x00007fffbc9d9000)
        libfoo.so.1 => /usr/local/lib/libfoo.so.1 (0x00002b82fa537000)
        libc.so.6 => /lib/libc.so.6 (0x00002b82fa739000)
        /lib64/ld-linux-x86-64.so.2 (0x00002b82fa317000)

```

To see which functions in test come from the shared libraries:
```

$ nm test | grep ' U '

```

Output:
```

                 U __libc_start_main@@GLIBC_2.2.5
                 U foo

```

In this place, __libc_start_main@@GLIBC_2.2.5 is a symbol defined by the C library, foo is a symbol defined by our shared library. It is completed by loading /usr/local/lib/libfoo.so.1 at runtime.

---

### Post by earth_tech on 2009-09-03
> **miklcct said:**
> .so file is a shared library. It is not directly usable. It is fed into the linker when linking your programs.

Example:

foo.c:
```

#include<stdio.h>
#include"foo.h"

void foo(void){
 puts("foo");
}

```foo.h:
```

#ifndef __foo_h
# define __foo_h
# ifdef __cplusplus
extern "C"{
# endif
void foo(void);
# ifdef __cplusplus
}
# endif
#endif

```Build the library:
```

$ cc -std=c99 -fPIC -c foo.c -o foo.o # preprocess, compile, assemble foo.c to yield object file foo.o
$ cc -shared -Wl,-soname,libfoo.so.1 foo.o -o libfoo.so.1.0.0 # link foo.o to yield shared object libfoo.so.1.0.0
$ ln -s libfoo.so.1.0.0 libfoo.so.1
$ ln -s libfoo.so.1 libfoo.so # libfoo.so.1 is needed for run-time linking, libfoo.so is needed for compile-time linking

```Install the library:
```

# cp foo.h /usr/local/include
# cp -a libfoo.so* /usr/local/lib
# chown root:root /usr/local/lib/libfoo.so* /usr/local/include/foo.h
# ldconfig

```To see what functions are inside the library
```

$ nm /usr/local/lib/libfoo.so | grep ' T '

```Output:
```

0000000000000648 T _fini
00000000000004e8 T _init
00000000000005fc T foo

```The first 2 are added by the linker, the last one is the one that comes from the object code.

To build an application against this library:

test.c
```

#include<foo.h> // note that foo.h is now a standard header
int main(void){
 foo();
}

``````

$ cc -std=c99 test.c -lfoo -o test # /usr/local/lib/libfoo.so is used
$ ./test # /usr/local/lib/libfoo.so.1 is used

```output:
```

foo

```To verify that the shared library is really used:
```

$ ldd test

```output:
```

        linux-vdso.so.1 =>  (0x00007fffbc9d9000)
        libfoo.so.1 => /usr/local/lib/libfoo.so.1 (0x00002b82fa537000)
        libc.so.6 => /lib/libc.so.6 (0x00002b82fa739000)
        /lib64/ld-linux-x86-64.so.2 (0x00002b82fa317000)

```To see which functions in test come from the shared libraries:
```

$ nm test | grep ' U '

```Output:
```

                 U __libc_start_main@@GLIBC_2.2.5
                 U foo

```In this place, __libc_start_main@@GLIBC_2.2.5 is a symbol defined by the C library, foo is a symbol defined by our shared library. It is completed by loading /usr/local/lib/libfoo.so.1 at runtime.

Hi

Thanks for your help. Since i am new in ubuntu so  there arise few questions. These are as follows:

1) In your comments you wrote foo.h. Now my question is whether it is (filename.h) necessary or not.

2) If you know any URL link on .so file related please post here for developing my knowledge on Ubuntu and .so file related.

---

### Post by miklcct on 2009-09-06
Here's a HOWTO for libraries:

[http://tldp.org/HOWTO/Program-Library-HOWTO/](http://tldp.org/HOWTO/Program-Library-HOWTO/)

The source codes contain .c and .h files. To convert a .c file to a .so file, the compiler actually performs 4 steps:

[LIST=1]
[*]Run cpp to generate .i file from .c file (Preprocessing)
[*]Run cc1 to generate .s file from .i file (Compiling)
[*]Run as to generate .o file from .s file (Assembling)
[*]Run ld to generate .so file from .o file(s) (Linking) (A shared object can contain more than 1 .o files)
[/LIST]

The .h file is needed in the cpp stage. When you distribute a binary image of the library, only the .so.a and .so.a.b.c (where .a.b.c is the version number) is needed. When you distribute the development files of the library, the .so and .h files is needed. Normally, .so.a and .so.a.b.c is placed in /usr/lib, for essential libraries (needed for programs in /bin), they are placed in /lib. The .so file is placed in /usr/lib and the .h file is placed in /usr/include. There may be some additional files (like libtool, pkg-config) but they are not relevant to the topic. Local-installed libraries by hand (out of package management) are normally installed in /usr/local/{lib,include}.

---

