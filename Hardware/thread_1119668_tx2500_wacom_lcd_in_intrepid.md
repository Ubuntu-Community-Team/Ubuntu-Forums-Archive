---
title: "tx2500 wacom lcd in intrepid"
date: 2009-04-08
forum: Hardware
---

### Post by AxelK on 2009-04-08
Hello everyone,

as all the threads about tablet support for this model seem to have changed to jaunty and i don't want to cange yet i decided to start a new thread for my problem.

i had  [my laptop perfectly working]("http://ubuntuforums.org/showpost.php?p=6658142&postcount=525") at least for my purposes but yesterday it suddenly stopped working.

i already have had this before everytime the kernel version changed so i decided to just rerun my linuxwacom-compilation-script (you can find it attached to my [original post]("http://ubuntuforums.org/showpost.php?p=6658142&postcount=525")). But that didn't solve the problem as the script returned:
```
cp: Aufruf von stat für „./src/2.6.27/wacom.ko“ nicht möglich: No such file or directory

```

this was strange as the same script worked the last time and i haven't changed it. i also tried different linuxwacom versions without success.
in the output of make i found a strange note but i don't know whether it has been there the last time (as someone in another forum said that he has this message too and it worked nevertheless):
```
***Note: Drivers not enabled as modules in your kernel config but requested through configure are NOT built

```

My build environment/options:
```
  BUILD ENVIRONMENT:
       architecture - x86_64-linux-gnu
       linux kernel - yes 2.6.27
  module versioning - no 
      kernel source - yes /lib/modules/2.6.27-11-generic/build
     XFree86 source - no 
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - yes
           dlloader - yes
               XLib - yes /usr/lib
         xf86config - no
                TCL - yes /usr/include/tcl8.4
                 TK - yes /usr/include/tcl8.4
            ncurses - yes

  BUILD OPTIONS:
            wacom.o - yes
            wacdump - yes 
             xidump - yes 
        libwacomcfg - yes
         libwacomxi - yes
          xsetwacom - yes
              hid.o - no 
         usbmouse.o - no
            evdev.o - no
         mousedev.o - no
            input.o - no
       wacom_drv.so - yes /usr/lib/xorg/modules/input 
        wacom_drv.o - no
  wacom*_drv quirks - Uninit-called IsXExtensionPointer key-events dixScreenOrigins

```

i hope that someone can help me with this.

alex

---

### Post by Favux on 2009-04-08
Hi alex,

There was a kernel header update for 2.6.27-11 the other day which broke the kernel module again as usual.  I went through the HOW TO again here:

[http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

Using the new development 0.8.3-1 and had no problems.  Wacom works fine.  It's now been replaced with 0.8.3-2 which I think is Jaunty compatible.

---

### Post by AxelK on 2009-04-09
Hi Favux,

thanks for the fast reply.

My try was based on gali's tut on wich your's is based.
i now addes the lines installing and purging the wacom tools and tried different linuxwacom versions.

but i think the problem has to be somewhere else as as i said the same script worked for me when i updated to 2.6.27-11 from 2.6.27-9.

are the build environment options identical with yours?

i appended the output of my script to this post


alex

---

