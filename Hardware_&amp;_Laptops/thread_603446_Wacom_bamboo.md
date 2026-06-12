---
title: "Wacom bamboo"
date: 2007-11-05
forum: Hardware &amp; Laptops
---

### Post by thelamb on 2007-11-05
I am aware that there are other threads concerning the wacom bamboo but I cannot find an answer to my problem there, and I have read posts from people with the same problem but no solution was posted.

So here we go:

I First tried to build the latest wacom driver (0.7.8 I think) myself, since the 0.7.7 do not support the bamboo yet.

I couldnt get it to work so I searched some forums and found out that the wacom is supported in the new 2.6.23-23 kernel. So I updated and voila - it seems to recognize the bamboo.

The problem is, however that it seems to work as a touchpad(I have a laptop so there is an actual touchpad present aswell).

When I open wacdump /dev/input/event10

It gives me the wacom screen. It recognizes when the styler tip is 'iin reach' so when I am hovering. It recognizes all the buttons/eraser of the styler and everything.

Now the problem is probably with X, I've read somewhere about a 'mousebug' - that the kernel sees the wacom tablet as a mouse, and handles the events through /dev/input/mice - this is of course not what we want.

Here's my xorg.conf(the relevant parts):

```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
#       Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
#       Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
#       Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Inputdevice"
        Driver          "wacom"
        Identifier      "pad"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "pad"
        Option          "USB"           "on"
EndSection

```

```

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "pad"           "SendCoreEvents"
        Inputdevice     "Synaptics Touchpad"
EndSection

```

So far so good in my opinion.
Now for the weird thing.

```
thelamb@thelamb:/dev/input$ lsmod | grep -i wacom
wacom                  18432  0 
usbcore               144008  14 wacom,usb_storage,pl2303,snd_usb_audio,snd_usb_lib,usblp,libusual,usbserial,asix,usbnet,usbhid,uhci_hcd,ehci_hcd

```
Looks good, right?

Now if I unload the module and load it back, then check /var/log/messages I get this:
```
thelamb@thelamb:/dev/input$ tail /var/log/messages
Nov  5 11:34:52 thelamb kernel: [  739.782249] usbcore: deregistering interface driver wacom
Nov  5 11:35:06 thelamb kernel: [  755.371797] input: Wacom Bamboo as /class/input/input15
Nov  5 11:35:06 thelamb kernel: [  755.376191] usbcore: registered new interface driver wacom
Nov  5 11:35:06 thelamb kernel: [  755.376204] drivers/input/tablet/wacom_sys.c: v1.47:USB Wacom Graphire and Wacom Intuos tablet driver
```

Again, seems perfectly fine to me.

Now here's for the really weird thing. If I restart X I get:

```
thelamb@thelamb:~$ sudo grep -i wacom /var/log/Xorg.0.log
(II) LoadModule: "wacom"
(WW) Warning, couldn't open module wacom
(II) UnloadModule: "wacom"
(EE) Failed to load module "wacom" (module does not exist, 0)
(EE) No Input driver matching `wacom'
(EE) No Input driver matching `wacom'
(EE) No Input driver matching `wacom'
(EE) No Input driver matching `wacom'
```

So it doesnt find the module(!)

Secondly I may not: if I unload the module 'wacom' (rmmod wacom) then the lights on the bamboo do not go out.

I am terribly sorry for the long read :) But I hope someone can help me out here

Cheers

---

### Post by thelamb on 2007-11-06
* BUMP * 

any idea's?

---

### Post by thelamb on 2007-11-08
*BUMP* 2

Dont tell me that I've been typing all that for nothing :P
Surely there is someone who has an idea?

---

### Post by cubeist on 2007-11-08
I just wrote a tutorial on this... even though you have upgraded to a kernel that supports bamboo I would use the linux wacom driver... it works great for me... check it out and post in that thread if you have more problems (I check that thread more often)..

[http://ubuntuforums.org/showthread.php?p=3728548#post3728548](http://ubuntuforums.org/showthread.php?p=3728548#post3728548)

also, I notice your xorg.conf file is missing the line: Option   "USB"    "on"       # USB ONLY

---

### Post by thelamb on 2007-11-08
I have read your thread actually.. but I couldnt get around building the driver.. Missing some libs I guess(can't say I'm an expert on that field :P)

But someone who is once told me to avoid building stuff if its supported in the kernel :)

I'll add the usb option thing next time I boot to linux to see if it makes a difference

---

### Post by cubeist on 2007-11-08
well one big feature with compiling the linux wacom driver is the associated apps you get with it to test if your driver is working as it should, such as wacdump which is essential to test all the features of the tablet...if you post the output of your configure I can tell you what you will need to do a successful compile.

Also, while drivers included in a kernel do make life easier, they are not always the best for each system.

---

### Post by thelamb on 2007-11-08
Ok cheers for helping m8, I'll post the output here tomorrow.

You can skip to my last post - everything went fine untill there. Cheers :)

---

### Post by thelamb on 2007-11-09
Ok I've might have found something here.

I just removed the wacom drivers, but still the tablet is working exactly the same(like a touchpad). The lights and all are still on.

So it seems that the kernel is recognizing the tablet as a touchpad...

Anyway, I guess we have to go with building the driver and then linking the correct event to the correct driver?

To start off:
In section 2.4 of the linuxwacom guide (further referred to as LW) it sais I have to navigate to /prebuilt and do ./uninstall and ./install. So that is what I do:

```
thelamb@thelamb:~/linuxwacom-0.7.8-3$ cd prebuilt/
thelamb@thelamb:~/linuxwacom-0.7.8-3/prebuilt$ sudo ./uninstall
Removing Wacom X driver related utility programs....
Wacom X driver related utility programs have been removed
thelamb@thelamb:~/linuxwacom-0.7.8-3/prebuilt$ sudo ./install
Installing Wacom man page......
Installed under /usr/share/man/man4

Installing wacom_drv....
WARNING: Can not install Wacom X driver (wacom_drv)
since the proper directory has not been found

You need to compile and install wacom.(k)o manually if your kernel is out of date.

After adding your Wacom tools into /etc/X11/xorg.conf, please restart X server or simply reboot your system to run the new Wacom X driver
```.

Now, I guess installing the prebuilt thing doesn't work... so I run ./uninstall again just to make sure and proceed.

So, your guide tells me to run ./configure
Here is the output (had some problem here but not anymore, new ./configure output:)

```
thelamb@thelamb:~/linuxwacom-0.7.8-3$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gawk... (cached) mawk
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for arch type... i486-linux-gnu
checking for kernel type... Linux
checking for linux-based kernel... yes
checking for kernel sources... /lib/modules/2.6.23-23/source
checking for kernel module support... yes
checking for kernel module versioning... yes
checking for valid Xorg SDK... ok
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for stack-protector flags support in gcc... yes
checking for X lib directory... found
checking for tclsh... /usr/bin/tclsh
checking for tcl version... 8.4
checking for tcl header files... /usr/include/tcl8.4/
checking for tk header files... found
checking ncurses.h usability... yes
checking ncurses.h presence... yes
checking for ncurses.h... yes
checking for Wacom X driver module path... /usr/lib/xorg/modules/input
checking if gcc accepts -fno-merge-constants... yes

configure: creating ./config.status
config.status: creating Makefile
config.status: creating mkxincludes
config.status: creating src/Makefile
config.status: creating src/util/Makefile
config.status: creating src/xdrv/Makefile
config.status: creating src/2.4/Makefile
config.status: creating src/2.4.22/Makefile
config.status: creating src/2.6.8/Makefile
config.status: creating src/2.6.9/Makefile
config.status: creating src/2.6.10/Makefile
config.status: creating src/2.6.11/Makefile
config.status: creating src/2.6.13/Makefile
config.status: creating src/2.6.14/Makefile
config.status: creating src/2.6.15/Makefile
config.status: creating src/2.6.16/Makefile
config.status: creating src/2.6.18/Makefile
config.status: creating src/2.6.19/Makefile
config.status: creating src/wacomxi/Makefile
config.status: creating src/wacomxi/wacomcpl
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

----------------------------------------
  BUILD ENVIRONMENT:
       architecture - i486-linux-gnu
       linux kernel - yes 2.6.19
  module versioning - yes -DCONFIG_MODVERSIONS -DMODVERSIONS -include /lib/modules/2.6.23-23/source/include/linux/modversions.h
      kernel source - yes /lib/modules/2.6.23-23/source
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - no
           dlloader - no
               XLib - yes /usr/lib
                TCL - yes /usr/include/tcl8.4/
                 TK - yes /usr/include/tcl8.4/
            ncurses - yes

  BUILD OPTIONS:
            wacom.o - no
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
        tabletdev.o - no
       wacom_drv.so - no
        wacom_drv.o - yes /usr/lib/xorg/modules/input 
----------------------------------------

```

---

### Post by thelamb on 2007-11-09
Ok I have actually got around that problem by installing xorg dev.
So let me continue :)

I see in the BUILD environment that the linux kernel is 2.6.19??
This is my uname -a output:
```
thelamb@thelamb:~/linuxwacom-0.7.8-3$ uname -a
Linux thelamb 2.6.23-23 #1 SMP Sun Nov 4 00:21:28 CET 2007 i686 GNU/Linux
```

Dunno if thats a problem, but I'll continue.

So according to your guide I need to sudo make install and make install now. This is where it went wrong last time.. so fingers crossed:

Aaand that went fine now I think :), guess it was the xorg dev files causing some trouble before.. I'll continue though, might find an error later on.
Ok, there is something I noticed last time aswell. 

This my more /proc/bus/input/devices output:
```
I: Bus=0003 Vendor=056a Product=0065 Version=0108
N: Name="Wacom Bamboo"
P: Phys=
S: Sysfs=/class/input/input7
U: Uniq=
H: Handlers=mouse2 event7 
B: EV=1f
B: KEY=1c63 0 70033 0 0 0 0 0 0 0 0
B: REL=100
B: ABS=100 3000103
B: MSC=1

```
So that seems ok.. apart from the fact that P: phys: is empty
And atm it is handles by mouse2 event 7, so that might be where the problem is? Since I dont want it to be handles as a mouse.

But I will continue for now.

When I disconnect and reconnect the tablet and do tail /var/log/messages I get the following:

```
Nov  9 14:59:27 thelamb kernel: [ 6793.870854] usb 1-1: USB disconnect, address 2
Nov  9 15:05:10 thelamb kernel: [ 7137.839395] usb 5-1: USB disconnect, address 2
Nov  9 15:05:13 thelamb kernel: [ 7139.332581] usb 5-1: new full speed USB device using uhci_hcd and address 3
Nov  9 15:05:13 thelamb kernel: [ 7139.493608] usb 5-1: configuration #1 chosen from 1 choice
Nov  9 15:05:13 thelamb kernel: [ 7139.495865] input: Wacom Bamboo as /class/input/input15
```

So it is now registered to input15.

Ok - I followed chapter 3 of the LW thing, something went wrong;

```
thelamb@thelamb:~/linuxwacom-0.7.8-3/src$ cd 2.6.19
thelamb@thelamb:~/linuxwacom-0.7.8-3/src/2.6.19$ ls
built-in.o  Makefile.in     wacom.h   wacom.mod.c  wacom.o      wacom_sys.o  wacom_wac.h
Makefile    Module.symvers  wacom.ko  wacom.mod.o  wacom_sys.c  wacom_wac.c  wacom_wac.o
thelamb@thelamb:~/linuxwacom-0.7.8-3/src/2.6.19$ sudo /sbin/rmmod wacom
thelamb@thelamb:~/linuxwacom-0.7.8-3/src/2.6.19$ sudo /sbin/insmod ./wacom.o
insmod: error inserting './wacom.o': -1 Invalid module format

```

I think that is not a good thing..

---

### Post by cubeist on 2007-11-09
actually everything looks like it is going ok... the configure was normal, same with the make and make install... no worries.

however, where you are going wrong is trying to use the wacom.o driver with a 2.6.xx kernel.  You need to navigate to the /src/2.6.19 folder within your linux-wacom folder (where you built the software) and then re-type the sudo sbin/rmmod wacom and then sudo /sbin/insmod ./wacom.ko (note the .ko not .o)cross your fingers, this should install the driver and if it works you will see in you tail /var/log/messages a line that says something like wacom registered using driver 1.4.x -pc  If you don't see that 1.4.something dash pc line then it isn't installed.  If you continue getting errors trying to install this driver, then you will have to start all over again from the beginning with the 7.9 package from linux-wacom as that package has better support for newer kernels...

good luck... keep trying, it will work eventually

ps - the prebuilt never worked for me either... and don't worry about which event is assigned at boot up... sometimes my system assigns it in event 9, sometimes event 10... it depends which usb port you plug it in to and what other usb devices are running... just remember in your xorg.conf file to keep the path as /dev/input/wacom (the wacom folder is an auto-created link to the correct event)  also, don't worry about the blank phys line... mine is blank too

---

### Post by thelamb on 2007-11-09
ok m8 I'll have a go at that when I'm back home(at my parents right now and I didnt bring the tablet).

Thanks for you help

---

### Post by meanmrmustard on 2008-05-11
So how'd it go?

---

### Post by geobiker on 2008-05-23
I have followed the tutorial to install my new Bamboo (MTE-450) but cannot seem to get it to work completely.  Specifically, I cannot get wacomcpl to see the device.  Also, I cannot get it configured in GIMP because GIMP does not see the Bamboo as an Extended Input Device.  As a result I have no pressure sensitivity or other functionality in GIMP.  The wacdump command gives me the output in the attached file.

So it appears the Bamboo is installed and working, but not fully functional. I've spent hours poring through the various postings and have tried many things--any suggestions?

---

