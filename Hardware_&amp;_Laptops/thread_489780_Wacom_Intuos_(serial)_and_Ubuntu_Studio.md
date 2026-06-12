---
title: "Wacom Intuos (serial) and Ubuntu Studio"
date: 2007-07-01
forum: Hardware &amp; Laptops
---

### Post by ltkitty on 2007-07-01
I'm running Ubuntu Studio Feisty Fawn on a Dell laptop.  I was given a first generation Intuos tablet with a serial interface, got a serial>USB adapter for it, and am trying to install in using the intructions at the Linux Wacom Project.

I tried the install with both linuxwacom-0.7.2.tar.bz2 (which is the first pkg I found), and linuxwacom-0.7.8.tar.bz2 from the LWP website.  

The build environment on the newest linuxwacom package misidentified my architecture as i486 (0.7.2 had identified it properly as i686), and also did not find the source (which was a problem I had with the 0.7.2 pkg as well), so I attempted to specify architecture and source.

Output at ./configure --with-arch=i686 --with-kernel=/usr/src/linux/

  BUILD ENVIRONMENT:
       architecture - i686
       linux kernel - yes 
  module versioning - no 
      kernel source - no /usr/src/linux/
           Xorg SDK - no /usr
          XSERVER64 - no
           dlloader - yes
               XLib - yes /usr/lib
                TCL - no 
                 TK - no 
            ncurses - yes

  BUILD OPTIONS:
            wacom.o - no
            wacdump - yes 
             xidump - yes 
        libwacomcfg - yes
         libwacomxi - no
          xsetwacom - yes
              hid.o - no 
         usbmouse.o - no
            evdev.o - no
         mousedev.o - no
            input.o - no
        tabletdev.o - no
       wacom_drv.so - no /usr/lib/xorg/modules/input 
        wacom_drv.o - no

The first time I tried to install it (using 0.7.2), I made and installed the package and then ran the wacdump and xidump tests, but got blank or no outputs.   I think this all has to do with the original build not identifying the source either on its own or when specified.

I did have to run aptitude install to get the source as I had no /usr/src/linux from the installation, and after unpacking the src, this is what is in /usr/src/linux:

ltkitty@mycomputer:/usr/src/linux$ ls
linux-source-2.6.20  linux-source-2.6.20.tar.bz2

Before I did aptitude install linux-source-2.6.20, the /usr/src dir looked like this:

ltkitty@mycomputer:/usr/src$ ls
fglrx-kernel-source.tar.gz  linux-headers-2.6.20-15-generic  modules
inux-headers-2.6.20-16    linux-headers-2.6.20-15     linux-headers-2.6.20-16-generic

and I tried specifying linux-headers-2.6.20-16 as the src to see if that would do anything, but it did not.

Can anyone help?

---

