---
title: "Optimus Mini Three driver from Ookoo.org"
date: 2007-10-02
forum: Hardware &amp; Laptops
---

### Post by Keith_Beef on 2007-10-02
Anybody had any luck compiling this?

I downloaded the source, but rn into errors when I try to compile...

```
 $ make
Package libglade-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libglade-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libglade-2.0' found
make: gtk-config: Command not found
Package libglade-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libglade-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libglade-2.0' found
make: gtk-config: Command not found
make[1]: Entering directory `/media/vol_1/Subversion_local/trunk/src_liboptimususb'
gcc -ggdb -Wall -O0 --std=gnu99 -D__DEBUG -D_REENTRANT -I. -I"/media/vol_1/Subversion_local/trunk" -I"/media/vol_1/Subversion_local/trunk/include" -I"/media/vol_1/Subversion_local/trunk/src_liboptimususb" -D_LIBOPTIMUSUSB -D_HAVE_SOURCE_FOR_MINITHREE -D_HAVE_SOURCE_FOR_OPTIMUS_IMAGE -D_HAVE_SOURCE_FOR_USB_MAIN   -c -o optimus_image.o optimus_image.c
optimus_image.c:18:17: error: png.h: No such file or directory
optimus_image.c: In function ‘load_png_file’:
optimus_image.c:90: error: ‘png_structp’ undeclared (first use in this function)
optimus_image.c:90: error: (Each undeclared identifier is reported only once
optimus_image.c:90: error: for each function it appears in.)
optimus_image.c:90: error: expected ‘;’ before ‘png_ptr’
optimus_image.c:91: error: ‘png_infop’ undeclared (first use in this function)
optimus_image.c:91: error: expected ‘;’ before ‘info_ptr’
optimus_image.c:92: error: ‘png_bytep’ undeclared (first use in this function)
optimus_image.c:92: error: ‘row_pointers’ undeclared (first use in this function)
optimus_image.c:99: warning: implicit declaration of function ‘png_sig_cmp’
optimus_image.c:100: error: ‘png_ptr’ undeclared (first use in this function)
optimus_image.c:100: warning: implicit declaration of function ‘png_create_read_struct’
optimus_image.c:100: error: ‘PNG_LIBPNG_VER_STRING’ undeclared (first use in this function)
optimus_image.c:102: error: ‘info_ptr’ undeclared (first use in this function)
optimus_image.c:102: warning: implicit declaration of function ‘png_create_info_struct’
optimus_image.c:104: warning: implicit declaration of function ‘setjmp’
optimus_image.c:104: warning: implicit declaration of function ‘png_jmpbuf’
optimus_image.c:105: warning: implicit declaration of function ‘png_init_io’
optimus_image.c:106: warning: implicit declaration of function ‘png_set_sig_bytes’
optimus_image.c:107: warning: implicit declaration of function ‘png_read_info’
optimus_image.c:114: error: ‘PNG_COLOR_TYPE_RGBA’ undeclared (first use in this function)
optimus_image.c:114: error: ‘PNG_COLOR_TYPE_RGB’ undeclared (first use in this function)
optimus_image.c:119: warning: implicit declaration of function ‘png_read_update_info’
optimus_image.c:121: error: expected expression before ‘)’ token
optimus_image.c:123: error: ‘png_byte’ undeclared (first use in this function)
optimus_image.c:123: error: expected expression before ‘)’ token
optimus_image.c:124: warning: implicit declaration of function ‘png_read_image’
optimus_image.c:131: error: ‘row’ undeclared (first use in this function)
optimus_image.c:133: error: ‘ptr’ undeclared (first use in this function)
make[1]: *** [optimus_image.o] Error 1
make[1]: Leaving directory `/media/vol_1/Subversion_local/trunk/src_liboptimususb'
make: *** [liboptimususb.a] Error 2
```

Beef.

---

### Post by Keith_Beef on 2007-10-03
OK, so I persevered and got it to compile...

I installed a few more development packages, then the compilation worked...
That gave me two executables, that are not executable...

```
$ ls -al
total 288
drwxr-xr-x 10 beef beef  4096 2007-10-03 21:48 .
drwxr-xr-x  5 beef beef  4096 2007-10-02 21:36 ..
-rw-r--r--  1 beef beef  8433 2007-10-02 21:36 configurator.glade
drwxr-xr-x  3 beef beef  4096 2007-10-02 21:36 img
drwxr-xr-x  3 beef beef  4096 2007-10-02 21:36 include
-rwxr-xr-x  1 beef beef 21457 2007-10-03 21:48 liboptimusclient.so
-rw-r--r--  1 beef beef 56946 2007-10-03 21:48 liboptimususb.a
-rw-r--r--  1 beef beef 18009 2007-10-02 21:36 LICENCE
-rw-r--r--  1 beef beef  2289 2007-10-02 21:36 Makefile
-rwxr-xr-x  1 beef beef 18173 2007-10-03 21:48 optimus
-rwxr-xr-x  1 beef beef 95944 2007-10-03 21:48 optimusd
-rw-r--r--  1 beef beef   594 2007-10-02 21:36 optimusd.conf
-rw-r--r--  1 beef beef  2554 2007-10-02 21:36 README
drwxr-xr-x  3 beef beef  4096 2007-10-03 21:48 src_liboptimusclient
drwxr-xr-x  3 beef beef  4096 2007-10-03 21:48 src_liboptimususb
drwxr-xr-x  3 beef beef  4096 2007-10-03 21:48 src_optimus
drwxr-xr-x  3 beef beef  4096 2007-10-03 21:48 src_optimusd
drwxr-xr-x  6 beef beef  4096 2007-10-02 21:37 .svn
drwxr-xr-x  5 beef beef  4096 2007-10-02 21:36 win32
```

As you can see, I have both optimus and optimusd, but I can execute neither...

Any clues, please?

Beef.

---

### Post by Horsman on 2007-10-04
What do you mean you can't execute them?

./optimusd doesnt work? Are they kernel modules?

---

### Post by Keith_Beef on 2007-10-04
> **Horsman said:**
> What do you mean you can't execute them?

./optimusd doesnt work? Are they kernel modules?

I mean exactly that.

I compiled them as myself, and as you can see from the permissions, they should be executable.

But when I try to execute either optimus or optimusd, I get a message like "cannot execute"...

I can't check again, because I'm at work right now.

But I also tried to execute optimus as root. This gave me a different reply, something along the lines of "could not load shared library liboptimusclient.so: no such file or object"

The Makefile in the project doesn't have a "make install" rule.

I wonder if I need to install the liboptimusclient.so file somewhere, or add its path to some environment variable. I tried copying it to /usr/local/lib, and putting the two others (optimus and optimusd) in /usr/local/bin, but that didn't help. I still got the "could not load shared library" message...


Beef.

---

### Post by Keith_Beef on 2007-10-06
OK, I seem to be getting somewhere!

[LIST]
[*]I became root
[*]I copied optimus and optimusd to /usr/local/bin
[*]I copied the libraries to /lib and ran ldconfig
[/LIST]

I ran optimusd and then stopped being root

I ran optimus, nd saw this:
```
Server: Optimus OLED-based keyboard driver version 0.1.0, by MagicalTux <MagicalTux@ookoo.org> - http://oledkbd.dns.st
sent file test1.png to key 1
sent file test2.png to key 2
```

But nothing happened.

I unplugged the OM3 and plugged it in again, this seemed to re-initialise the device, or wake the daemon, because I saw:
```

$ [USB] Driver `pl2303' is currently using device `Optimus Mini Three keyboard', attempting to shutdown it...
[USB] Found a `Optimus Mini Three keyboard' device at address 004
```

Now, when I ran optimus, I got the neat configurator utility on my screen, and test pictures appeared on the OM3 keys!

I'm happy! :D


Beef

---

