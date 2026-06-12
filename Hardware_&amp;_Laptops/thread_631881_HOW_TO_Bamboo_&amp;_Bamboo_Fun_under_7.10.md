---
title: "HOW TO: Bamboo &amp; Bamboo Fun under 7.10"
date: 2007-12-04
forum: Hardware &amp; Laptops
---

### Post by narehart on 2007-12-04
This is a HOW TO on getting the Bamboo and Bamboo Fun working under Gutsy Gibbon.  The original information came from Philippe on the LinuxWacom mailing list.  I revised his instructions so that they're a little easier to follow.  Hope this will help some people.

First make two directories. One, for backups called **administration**:
```
sudo mkdir /home/administration
```

And one for the linuxwacom stuff called **linuxwacom**:

```
sudo mkdir /home/linuxwacom
```

Then, get the latest linuxwacom driver on [http://linuxwacom.sourceforge.net/]("http://linuxwacom.sourceforge.net/") and save it to **/home/linuxwacom**.

Then, copy the latest udev file from [http://git.debian.org/?p=users/ron/wacom-tools.git;a=blob_plain;f=debian/xserver-xorg-input-wacom.udev;hb=master]("http://git.debian.org/?p=users/ron/wacom-tools.git;a=blob_plain;f=debian/xserver-xorg-input-wacom.udev;hb=master")  

Create a new text file in your **/home/linuxwacom** folder called **xserver-xorg-input-wacom.udev**, paste the new udev file in it and save:

```
sudo gedit /home/linuxwacom/xserver-xorg-input-wacom.udev
```

Get the necessary dependencies:  

```
sudo apt-get install build-essential x11proto-core-dev libxau-dev libxdmcp-dev x11proto-input-dev x11proto-kb-dev xtrans-dev libx11-dev x11proto-xext-dev libxext-dev libxi-dev linux-libc-dev libc6-dev libncurses5-dev xserver-xorg-dev
```

Then backup the old rules:

```
cp /etc/udev/rules.d/50-xserver-xorg-input-wacom.rules /home/administrator/50-xserver-xorg-input-wacom.rules_orig
```

Navigate to your **/home/linuxwacom** folder and replace the old udev with the one you made:

```
sudo cd /home/linuxwacom 
cp xserver-xorg-input-wacom.udev /etc/udev/rules.d/50-xserver-xorg-input-wacom.rules
```

Then extract the wacom driver:

```
bunzip2 linuxwacom-0.7.9-3.tar.bz2
```

```
tar xvf linuxwacom-0.7.9-3.tar
```

Then go into the newly created folder and configure:

```
cd linuxwacom-0.7.9-3
```

```
./configure --enable-wacom
```

If everything went well, you should see something like this:

```
----------------------------------------
 BUILD ENVIRONMENT:
      architecture - i486-linux-gnu
      linux kernel - yes 2.6.22
 module versioning - yes -DCONFIG_MODVERSIONS -DMODVERSIONS -include
/lib/modules/2.6.22-14-generic/build/include/linux/modversions.h
     kernel source - yes /lib/modules/2.6.22-14-generic/build
          Xorg SDK - yes /usr/include/xorg
         XSERVER64 - no
          dlloader - yes
              XLib - yes /usr/lib
               TCL - yes /usr/include/tcl8.4/
                TK - yes /usr/include/tcl8.4/
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
       tabletdev.o - no
      wacom_drv.so - yes /usr/lib/xorg/modules/input
       wacom_drv.o - no
----------------------------------------

```

Then make and install:

```
make
sudo make install
```

Next, you have to edit your xorg file so that it will detect the Bamboo.  **Before you do any altering to your xorg.conf file, first make a backup!**

```
 cp /etc/X11/xorg.conf /home/administrator/xorg.conf_old
```

```
sudo gedit /etc/X11/xorg.conf
```

```
Section "InputDevice"
       Driver          "wacom"
       Identifier      "stylus"
       Option          "Device"        "/dev/input/wacom"
       Option          "Type"  "stylus"
       #Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
   Option "USB" "on"
EndSection

Section "InputDevice"
       Driver          "wacom"
       Identifier      "eraser"
       Option          "Device"        "/dev/input/wacom"
       Option          "Type"  "eraser"
       #Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
   Option "USB" "on"
EndSection

Section "InputDevice"
       Driver          "wacom"
       Identifier      "cursor"
       Option          "Device"        "/dev/input/wacom"
       Option          "Type"  "cursor"
       #Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
   Option "USB" "on"
EndSection

...
       # Uncomment if you have a wacom tablet
              InputDevice     "stylus"        "SendCoreEvents"
              InputDevice     "cursor"        "SendCoreEvents"
              InputDevice     "eraser"        "SendCoreEvents"

```

Add this under sections:

```
Section "InputDevice"
Driver "wacom"
Identifier "pad"
Option "Device" "/dev/input/wacom"
Option "Type" "pad"
Option "USB" "on"
EndSection
```

Add this to the lower section:

```
InputDevice "pad" "SendCoreEvents"
```

Now, back up the old driver:

```
cp /lib/modules/2.6.22-14-generic/kernel/drivers/input/tablet/wacom.ko /home/administrator/wacom.ko_old
```

Then, replace it with the new one:

```
sudo cp /home/linuxwacom/linuxwacom-0.7.9-3/src/2.6.22/wacom.ko /lib/modules/2.6.22-14-generic/kernel/drivers/input/tablet
```

Next, test the module to see if there is anything unresolved. If you get nothing back, your golden!

```
sudo depmod -e
```

Save any important data, reboot the system and see if it works:

```
sudo reboot
```

If it worked you can set the actions for the buttons with instructions like these:

```
xsetwacom set pad AbsWUp 4 #scroll up
xsetwacom set pad AbsWDn 5 #scroll down
xsetwacom set pad button3 4 #< key: scroll up
xsetwacom set pad button1 5 #> key: scroll dn
xsetwacom set pad button2 1 #FN1 key: left mouse button
xsetwacom set pad button4 3 #FN2 key: right mouse button

```

**[COLOR="Red"]Note:[/COLOR]** Sometimes this driver will stop working for me (like when using VirtualBox) and I have to execute these commands to get it working again. So, I created a script that will reinsert the driver and depmod it.  All you have to do is double click it, run it in a terminal, disconnect and reconnect the Bamboo and restart X. 

**This is NOT an instillation script.  It is only for those who have followed the guide through at least once:**

[ATTACH]52974[/ATTACH]

---

### Post by arelis on 2007-12-05
YES!!! thanks to you, i FINALLY got it to work in Linux! This thread should be stickied and kept safe in someplace, because this is the only one that -REALLY WORKS-.

I saw a few flaws in your guide though. Package names are hanging around in random places in your guide, such as in some command-line sections (i saw cp /home/youruser/something /usr/lib/something libsomething-dev libanother-dev), meaning that command would be flawed if you blindly copy and pasted it.
Still, thank you very much for this guide as it really works :)

EDIT: And for some reason the xsetwacom command will not work. I think you may have forgotten something.

---

### Post by narehart on 2007-12-05
Thanks.  All, the credit should go to the guys at the LinuxWacom website.  I just put it all together in an easy to understand guide.

As far as the xsetwacom goes, it worked for me but I know some people are having problems.

---

### Post by PatoLucas on 2007-12-06
YES!
Thank you!

I was losing hope, but now is back! Woohoo!

Works for me in GG with a regular Bamboo (not Fun)

---

### Post by PatoLucas on 2007-12-06
I forgot to say Gutsy Gibbon 64Bits BTW

---

### Post by Pauan on 2007-12-08
You, kind sir, are a God-send: I was nearly giving up hope when I saw your post. Whether or not you created the tutorial you still decided to post it, and for that I thank you. I have gotten my Bamboo Fun tablet working flawlessly; now to see about those custom button shortcuts....

---

### Post by eustaquiorangel on 2007-12-23
> **narehart said:**
> **[COLOR="Red"]Note:[/COLOR]** Sometimes this driver will stop working for me (like when using VirtualBox) and I have to execute these commands to get it working again. So, I created a script that will reinsert the driver and depmod it.  All you have to do is double click it, run it in a terminal, disconnect and reconnect the Bamboo and restart X. 

Hey, seems that this script really looks like an installation script, as it runs ./configure and make again. Should we remove and reinsert the driver when it stop working?

I'm facing a problem here with Bamboo that when connected when the computer is turned on, it does not works, I need to remove the USB cable and put it again to make it work. But then the xsetwacom tells me that there is no "pad" device and seems that the tablet works more like a mouse than a tablet. Do you guys have some tip about it?

Thanks!

---

### Post by jazzroy on 2007-12-24
similar here.. the tablet works like a mouse.

i tried the xsetwacom command and it said:

jazzroy@dell-covino:~$ xsetwacom
xsetwacom: error while loading shared libraries: libwacomcfg.so.0: cannot open shared object file: No such file or directory
jazzroy@dell-covino:~$ 


any hints?

---

### Post by em es on 2007-12-25
I followed your tutorial completely but when I configure it says:
```
***
*** WARNING:
*** Unable to compile wacom.o without kernel build environment
*** wacom.o will not be built
***

```
And in the configuration summary it then prints:
```
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

```

So in the respective source directory of my kernel version (2.6.22) there is no wacom.o or wacom.ko - which has to be copied to the module directory of the kernel, so it's the core component I suppose.

I think this problem is the "without kernel build environment" - problem is: I have no idea what I have to install orconfigure so that it HAS a build environment.
- Thanks for any help.

---

### Post by jaskah on 2007-12-25
hello
first off, thanks very much for posting your tutorial--although unfortunately it didn´t work for me.

when i ./configure --enable-wacom i get the following:

--------------------------------------------------------------------------------
BUILD ENVIRONMENT:
       architecture - i486-linux-gnu
       linux kernel - yes 
  module versioning - no 
      kernel source - no 
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - no
           dlloader - no
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
       wacom_drv.so - no
        wacom_drv.o - yes /usr/lib/xorg/modules/input 
--------------------------------------------------------------------------------

which doesn´t match the read-out in your tutorial.

secondly, regarding the command: sudo cd /home/linuxwacom 
cp xserver-xorg-input-wacom.udev /etc/udev/rules.d/50-xserver-xorg-input-wacom.rules

shouldn´t the new udev file have the 50- prefix, like the old one?
i.e. 50-xserver-xorg-input-wacom.rules

and lastly:
cp /lib/modules/2.6.22-14-generic/kernel/drivers/input/tablet/wacom.ko /home/administrator/wacom.ko_old

there is no wacom.ko in the linux driver package i downloaded:

i used the following driver package:
linuxwacom-0.7.9-4

i am on kernel 2.6.22-14-rt
lenovo t61 laptop, all intel drivers

wacom bamboo

and my xorg.conf is:

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
       Driver          "wacom"
       Identifier      "stylus"
       Option          "Device"        "/dev/input/wacom"
       Option          "Type"  "stylus"
EndSection

Section "InputDevice"
       Driver          "wacom"
       Identifier      "eraser"
       Option          "Device"        "/dev/input/wacom"
       Option          "Type"  "eraser"
EndSection

Section "InputDevice"
       Driver          "wacom"
       Identifier      "cursor"
       Option          "Device"        "/dev/input/wacom"
       Option          "Type"  "cursor"
EndSection

Section "InputDevice"
	Driver 		"wacom"
	Identifier 	"pad"
	Option "Device" "/dev/input/wacom"
	Option 		"Type" "pad"
	Option 		"USB" "on"
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice 	"pad" 		"SendCoreEvents"
EndSection


the wacom doesn´t work at all.

does anyone have a clue what i am doing wrong?
any help greatly appreciated!
thanks!

---

### Post by em es on 2007-12-25
jaskah, I think you might be having the same problem as me, it sounds like it. When you configure, do you get an error halfway, telling you that you do not have a kernel build environment?

EDIT. I notice that in your configuration summary it says you have no tk or tcl. I don't know how important they are, I've got them. (Two libraries you can install with synaptic)

In the "--help" parameter information for the configuration script it says that the "--enable-wacom" just enables the building of the wacom.o file, so that seems to be optional, it doesn't show any errors then, but still no .ko :-(

(the next kernel update includes native wacom bamboo support I've read)

---

### Post by jaskah on 2007-12-25
yes, and i get the following error messages to:

*** WARNING:
*** Unable to guess kernel source directory
*** Looked at /lib/modules/2.6.22-14-rt/source
*** Looked at /usr/src/linux
*** Looked at /usr/src/linux-2.6.22-14-rt
*** Looked at /usr/src/linux-2.4
*** Looked at /usr/src/linux-2.6
*** Kernel modules will not be built

*** WARNING:
*** The tcl development environment does not appear to
*** be installed. The header file tcl.h does not appear
*** in the include path. Do you have the tcl rpm or
*** equivalent package properly installed?  Some build
*** features will be unavailable.
***
checking for tk header files... not found; tried /usr/include and /include
***
*** WARNING:
*** The tk development environment does not appear to
*** be installed. The header file tk.h does not appear
*** in the include path. Do you have the tk rpm or
*** equivalent package properly installed?  Some build
*** features will be unavailable.
***

*** WARNING:
*** Unable to compile wacom.o without kernel build environment
*** wacom.o will not be built
***
***
*** WARNING:
*** libwacomxi requires tcl environment; libwacomxi will not be built.

very strange...i can´t figure it out.

anyone know what the problem here could be?
thanks!

---

### Post by em es on 2007-12-25
I would definitely install tcl and tk, I think they are needed.
```
sudo apt-get install tcl8.4 tcl8.4-dev tk8.4 tk8.4-dev
```

---

### Post by jaskah on 2007-12-25
thanks for your reply...i have all these installed already.

---

### Post by em es on 2007-12-25
weird... It doesn't show those error messages with me except the 
```
*** WARNING:
*** Unable to compile wacom.o without kernel build environment
*** wacom.o will not be built
***
```

---

### Post by jaskah on 2007-12-25
yes, it ***is*** weird...i can´t figure it out.

---

### Post by em es on 2007-12-25
Right, well I'm a complete noob, so I've really got no idea. But I think (*think*)  the problem might be the gcc. Which is the Gnu C Compiler. I've looked in the config.log file to see what it says about this build environment stuff. And I think I whittled the problem down to this:
```
...
configure:20952: result: no
configure:20987: checking for ncurses/ncurses.h
configure:20994: result: no
configure:21346: checking for Wacom X driver module path
configure:21363: result: /usr/lib/xorg/modules/input
configure:21550: checking if gcc accepts -fno-merge-constants
configure:21570: gcc -c -g -O2 -I/usr/include/tcl8.4/ -fno-merge-constants  conftest.c >&5
configure:21576: $? = 0
configure:21580: test -z 
			 || test ! -s conftest.err
configure:21583: $? = 0
configure:21586: test -s conftest.o
configure:21589: $? = 0
configure:21602: result: yes
configure:21822: creating ./config.status
...
```

So I'm guessing it could be that gcc doesn't accept the "-fno-merge-constants". I'm just playing around with gcc packages to see if it changes. I'll let you know if anything happens...

[B]
EDITJust found out that that was utter rubbish. While configuring it says: [/B]
```
checking ncurses.h usability... yes
checking ncurses.h presence... yes
checking for ncurses.h... yes
***
*** WARNING:
*** Unable to compile wacom.o without kernel build environment
*** wacom.o will not be built
***
checking for Wacom X driver module path... /usr/lib/xorg/modules/input
**checking if gcc accepts -fno-merge-constants... yes**
```

So it must be this ncurses.h:```
| #include <ncurses/ncurses.h>
configure:20952: result: no
configure:20987: checking for ncurses/ncurses.h
configure:20994: result: no
```

---

### Post by jaskah on 2007-12-25
thanks for your reply...i´m even more of a noob than you are! drop us a line if you find anything else.

---

### Post by em es on 2007-12-25
It just doesn't make any sense. If you have a look at the config.log it says this shortly before making config.status, which ist the last bit of the configuring:
```
.. configure:20771: $? = 0
configure:20774: test -s conftest.o
configure:20777: $? = 0
configure:20787: result: yes
configure:20791: checking ncurses.h presence
configure:20801: gcc -E  conftest.c
configure:20807: $? = 0
configure:20827: result: yes
configure:20862: checking for ncurses.h
configure:20869: result: yes
[B]
- And exactly at this place, between checking for ncurses.h and the wacom x driver module it shows this thing about the build environment. -[/B]

configure:21364: checking for Wacom X driver module path
configure:21381: result: /usr/lib/xorg/modules/input
configure:21787: checking if gcc accepts -fno-merge-constants
configure:21807: gcc -c -g -O2 -I/usr/include/tcl8.4/ -fno-merge-constants  conftest.c >&5
configure:21813: $? = 0
configure:21817: test -z 
			 || test ! -s conftest.err
configure:21820: $? = 0
configure:21823: test -s conftest.o
configure:21826: $? = 0
configure:21839: result: yes
configure:22059: creating ./config.status
```

---

### Post by jaskah on 2007-12-25
yeah, i just don´t get it, either. hmmm...i´m stumped.
anyone else?
thanks!

---

### Post by em es on 2007-12-25
**Whhhopeee!**

I've found it. They don't half make it difficult, do they. So, the problem was that "kernel build environment" means that it not only has to have all the proper libraries installed but also needs to know where you kernel source is. What I ended up as a configure command was this:
```
 ./configure --enable-modver --enable-wacom  -with-kernel=/lib/modules/2.6.22-14-generic/build

```

Be sure to ajust the path at the end to you kernel version.

Also, I think you have to install tcl and tk (In the first configure report you postet they were shown as not installed) this is my report, when it worked:
```
----------------------------------------
  BUILD ENVIRONMENT:
       architecture - i486-linux-gnu
       linux kernel - yes 2.6.22
  module versioning - yes -DCONFIG_MODVERSIONS -DMODVERSIONS -include /lib/modules/2.6.22-14-generic/build/include/linux/modversions.h
      kernel source - yes /lib/modules/2.6.22-14-generic/build
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - no
           dlloader - no
               XLib - yes /usr/lib
                TCL - yes /usr/include/tcl8.4/
                 TK - yes /usr/include/tcl8.4/
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
        tabletdev.o - no
       wacom_drv.so - no
        wacom_drv.o - yes /usr/lib/xorg/modules/input 
----------------------------------------

```
So I think if you install the things that ae missing at the moment and try my configure command there should be no error.

Then (sudo) make and sudo make install, then you can copy the wacom.ko, which has been created and it should reboot. I'll try that now. Let me know if it works.

---

### Post by jaskah on 2007-12-25
thanks for your reply, just one other question:

you write: then you can copy the wacom.ko, which has been created and it should reboot. 

but in my case no wacom.ko (in the driver installer) was created in linuxwacom-0.7.9-3/src/2.6.22/

how can i create a new driver? or is this just automatically installed?

---

### Post by em es on 2007-12-25
If you do the configure command, and then "sudo make" which compiles the code to binaries and the "sudo make install", which installs it, there should be, among other things, a wacom.ko file in the .../src/2.6.22/ folder. You replace the one in /lib/modules//$yourkernel$/kernel/drivers/input/tablet/ with it and then reboot.
- It *should* work then, if you have done the xorg.conf editing as seen at the bginning of the thread.

That said, it doesn't work with me after rebooting, I don't quite know why...

---

### Post by jaskah on 2007-12-25
thanks again....

yes, i tried this before but wacom.ko file wasn´t in the .../src/2.6.22/ folder after sudo make install.

---

### Post by em es on 2007-12-25
After another reboot and pluging the usb in another slot (obviously the previous one was a firewire slot, which is practically identical to usb) it works.

I hope it does work for you to. What I found too ist that in /lib/modules/ not all (I have three there) kernel versions have subdirectory called "build" (whih you have to point the configuration script to) - so take one that does have a build folder, mine was the "generic" version of 2.6.22. - but then you also have to replace the wacom.ko file in the /lib/modules/THE KERNEL WITH THE BUILD DIRECTORY/kernel/drivers...

Also, you have to, when you reboot boot into that same kernel. (you can select it right at startup in the GRUB menu)

Let me know if you have trouble.

---

### Post by em es on 2007-12-25
did you get any errors after you did the configure script with my parameter?

---

### Post by jaskah on 2007-12-25
thanks again...
one other question:
when you write
but then you also have to replace the wacom.ko file in the /lib/modules/THE KERNEL WITH THE BUILD DIRECTORY/kernel/drivers...
Also, you have to, when you reboot boot into that same kernel. (you can select it right at startup in the GRUB menu)

does this mean i can´t use my real time kernel, which is ***not*** THE KERNEL WITH THE BUILD DIRECTORY, as you pointed out. mine is the generic kernel, which i don´t use.

or will replacing the wacom.ko in /lib/modules/THE KERNEL WITH THE BUILD DIRECTORY/kernel/drivers...also apply to the real time kernel (img-2.6.22-14-rt)?

---

### Post by jaskah on 2007-12-25
i had this error message when with sudo make

 Building linuxwacom drivers for 2.6 kernel.
***Note: Drivers not enabled as modules in your kernel config but requested through configure are NOT built
make -C /lib/modules/2.6.22-14-generic/build M=/home/jason/Desktop/wacom/linuxwacom-0.7.8-3/src/2.6.19

i will have to test with the wacom, though. maybe this is ok,
thakns.

---

### Post by em es on 2007-12-25
concerning your first question:
Yes, you then have to boot into the generic one, but it's no big deal I think.

concerning your second question:
I had that message to, I think it's more of a warning rather than an error.

---

### Post by jaskah on 2007-12-25
ok, i will check it out later.
thanks again for all your help, i really appreciate it!

---

### Post by em es on 2007-12-25
> **jaskah said:**
> ok, i will check it out later.
thanks again for all your help, i really appreciate it!
my pleasure :-) enjoy your bamboo

---

### Post by neko18 on 2007-12-25
.
.
.
.
.


**There is a new guide**
Please go to the new, updated guide:
[http://ubuntuforums.org/showpost.php?p=4253232&postcount=133](http://ubuntuforums.org/showpost.php?p=4253232&postcount=133)

.
.
.
.

---

### Post by Flutterby on 2007-12-25
I have the same problem as one of the earlier posters in this thread: I have been able to set up the Wacom Bamboo, but I need to adjust the settings (it's too slow for example).
However when I try to run wacomcpl I get this:

> wacomcpl: using TCLLIBPATH="[list  /usr/local/lib ]"
Error in startup script: xsetwacom: error while loading shared libraries: libwacomcfg.so.0: cannot open shared object file: No such file or directory
    while executing
"exec xsetwacom list"
    (procedure "createDeviceList" line 4)
    invoked from within
"createDeviceList "
    (procedure "createControls" line 7)
    invoked from within
"createControls"
    (file "/usr/local/bin/wacomcpl-exec" line 1611)


Does anyone know how to fix this?

---

### Post by neko18 on 2007-12-25
I have the same problem, so I'll look into it.

Edit:
Fixed. See step 14 and 16 in my walkthrough.

---

### Post by ThomasWii on 2007-12-25
it don't work, I did all of it, and i did the 
sudo depmod -e and it came up with blank, please note that instead of 
linuxwacom-0.7.9-3 i used linuxwacom-0.7.8-3, and instead of 2.6.22 i used 2.6.19, can anyone help?

Thanks in advance,

Thomas

---

### Post by neko18 on 2007-12-25
@ThomasWii:
You used the wrong version of Linux Wacom.
You may want to try my walkthrough: [http://ubuntuforums.org/showpost.php?p=4014004&postcount=32](http://ubuntuforums.org/showpost.php?p=4014004&postcount=32)

---

### Post by ThomasWii on 2007-12-25
Thanks for your reply, but i have an error, when i put in ```
sudo cp linuxwacom-0.7.9-4/src/2.6.22/wacom.ko /lib/modules/2.6.22-14-generic/kernel/drivers/input/tablet/wacom.ko
```it comes up with ```
cp: cannot stat `linuxwacom-0.7.9-4/src/2.6.22/wacom.ko': No such file or directory

``` Thanks in advance,

Thomas

---

### Post by neko18 on 2007-12-25
@ThomasWii:
You will have to follow through the entire howto from the beginning, not just that part.

---

### Post by em es on 2007-12-25
> **ThomasWii said:**
> Thanks for your reply, but i have an error, when i put in ```
sudo cp linuxwacom-0.7.9-4/src/2.6.22/wacom.ko /lib/modules/2.6.22-14-generic/kernel/drivers/input/tablet/wacom.ko
```it comes up with ```
cp: cannot stat `linuxwacom-0.7.9-4/src/2.6.22/wacom.ko': No such file or directory

``` Thanks in advance,

Thomas
Maybe there was a problem with your configuration and it didn't compile the .ko file. You need tcl, tk and also to specify the path to your kernel source. This has been discussed in this thread previously...

---

### Post by em es on 2007-12-25
> **ThomasWii said:**
> it don't work, I did all of it, and i did the 
sudo depmod -e and it came up with blank, please note that instead of 
linuxwacom-0.7.9-3 i used linuxwacom-0.7.8-3, and instead of 2.6.22 i used 2.6.19, can anyone help?

Thanks in advance,

Thomas
depmod should come up blank, that means it didn't find any mistakes.

EDIT: I fear this is rather getting confusing. I think I'll list all the mistakes I made/read about until I got it working, maybe that will help...

---

### Post by ThomasWii on 2007-12-25
i did start at the beginning, you could attach the file?

---

### Post by neko18 on 2007-12-25
A note to all: be absolutely sure you use version 0.7.9-4 instead of 0.7.8-3. I tried 0.7.8-3 and it *will not work*.

**Edit:**
@ThomasWii: Yes, just a moment.

**Edit 2:**
@ThomasWii:
Attached. Download wacom.ko.gz to your desktop, then run the following commands:
```
cd ~/Desktop
gunzip wacom.ko.gz
sudo cp wacom.ko /lib/modules/2.6.22-14-generic/kernel/drivers/input/tablet/wacom.ko
```
Now continue with step 13

---

### Post by em es on 2007-12-25
**A few things before you begin:**
- make sure you have the dependencies installed. This includes tcl8.4 tcl8.4-dev tk8.4 and tk8.4-dev.
- When running the configure script be sure to use these parameters:
```
sudo ./configure --enable-modver --enable-wacom -with-kernel=/lib/modules/2.6.22-14-generic/build

```
- Also be careful when downloading the source of linuxwacom on the project website, the version has to be compatible with your kernel and obviously your tablet.

**It says my kernel build environment is not correct!**
This means that you have something not installed or properly set up. With me it was the parameter in the configure command to define the path to my kernel source. (You might have to download that through your package manager)

**It says there is no wacom.ko in the src folder of my kernel version!**
This means that there was a problem while configuring, check the output of the configure script and see what's the matter. (It could be, of course, that you have not yet compiled the code: sudo make and then sudo make install)

---

### Post by ThomasWii on 2007-12-25
ok, I've done all of it (except em es thing because i did not understand it) and it still dose not work, here is the xorg file if this helps. ```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "uk"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "stylus"
#    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
    Option        "USB"        "on"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "eraser"
#    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
    Option        "USB"        "on"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "cursor"
#    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
    Option        "USB"        "on"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "pad"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "pad"
    Option        "USB"        "on"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "pad"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "pad"
    Option        "USB"    "on"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "ZAxisMapping"        "4 5"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizEdgeScroll"    "0"
EndSection

Section "Device"
    Identifier    "Generic Video Card"
    Driver        "vesa"
    BusID        "PCI:1:0:0"
    VideoRam    64000
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    HorizSync    30-68
    VertRefresh    50-85
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1280x800" "1280x768" "1024x768" "800x600"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"

# Uncomment if you have a wacom tablet
    InputDevice     "stylus"    "SendCoreEvents"
    InputDevice     "cursor"    "SendCoreEvents"
    InputDevice     "eraser"    "SendCoreEvents"
    InputDevice    "pad"        "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection
```

---

### Post by ReconIsense on 2007-12-25
given this thread it's safe to assume intous3 will work in linux?

---

### Post by em es on 2007-12-25
:-D it's quite simple. You put this in your terminal first of all:
```
sudo apt-get install tcl8.4 tcl8.4-dev tk8.4 tk8.4-dev
```
then you follow the howto up to the poit where you are about to put in```
./configure --enable-wacom
```
Just that instead of that you use```
./configure --enable-modver --enable-wacom -with-kernel=/lib/modules/2.6.22-14-generic/build
```
then a lot of configuration information is printed in the terminal, some time there is a kind of list, which tells you what it has done. It looks something like this like this:```
----------------------------------------
  BUILD ENVIRONMENT:
       architecture - i486-linux-gnu
       linux kernel - yes 
  module versioning - yes -DCONFIG_MODVERSIONS -DMODVERSIONS -include /lib/modul/include/linux/modversions.h
      kernel source - no
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

If you can copy and paste your version of this block-thing that might tell us what the problem is.

---

### Post by ThomasWii on 2007-12-25
```
----------------------------------------
  BUILD ENVIRONMENT:
       architecture - i486-linux-gnu
       linux kernel - yes 2.6.22
  module versioning - yes -DCONFIG_MODVERSIONS -DMODVERSIONS -include /lib/modules/2.6.22-14-generic/build/include/linux/modversions.h
      kernel source - yes /lib/modules/2.6.22-14-generic/build
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - no
           dlloader - yes
               XLib - yes /usr/lib
                TCL - yes /usr/include/tcl8.4/
                 TK - yes /usr/include/tcl8.4/
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
        tabletdev.o - no
       wacom_drv.so - yes /usr/lib/xorg/modules/input 
        wacom_drv.o - no
----------------------------------------

```

---

### Post by em es on 2007-12-25
That looks excellent. Now try the command you were having difficulties with:```
sudo cp linuxwacom-0.7.9-4/src/2.6.22/wacom.ko /lib/modules/2.6.22-14-generic/kernel/drivers/input/tablet/wacom.ko
```

---

### Post by ThomasWii on 2007-12-25
nope, still dose not work, i will send in any file that you may need to look at.

---

### Post by neko18 on 2007-12-25
@ThomasWii:
What is the the output of these commands?
```
ls #if this gives any private information (filenames you don't want others to see), feel free to edit it out
ls linuxwacom-0.7.9-4
ls linuxwacom-0.7.9-4/src
ls linuxwacom-0.7.9-4/src/2.6.22
```

**Edit:**
@ThomasWii:
I noticed you have the same section listed twice in your xorg.conf. You have the following repeated twice. Remove one copy of it, save the file, then log out and back in.
```
Section "InputDevice"
    Driver        "wacom"
    Identifier    "pad"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "pad"
    Option        "USB"        "on"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "pad"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "pad"
    Option        "USB"    "on"
EndSection
```

---

### Post by ThomasWii on 2007-12-25
[FONT=monospace]1st one:```
acinclude.m4    config.h       depcomp     Makefile        prebuilt
aclocal.m4      config.h.in    docs        Makefile.am     README
AUTHORS         config.log     GPL         Makefile.in     src
autom4te.cache  config.status  install-sh  missing         stamp-h1
bootstrap       config.sub     LGPL        mkxincludes     wacom.ko
ChangeLog       configure      libtool     mkxincludes.in
config.guess    configure.in   ltmain.sh   NEWS

```
2nd:```
2.4           2.6.11  2.6.16  2.6.8     Makefile.am  wacom.4x.gz
2.4.22        2.6.13  2.6.18  2.6.9     Makefile.in  wacomxi
2.4.30x86-64  2.6.14  2.6.19  include   util         xdrv
2.6.10        2.6.15  2.6.22  Makefile  wacom.4x

```and the last one ```
built-in.o   Module.symvers  wacom.mod.c  wacom_sys.c  wacom_wac.h
Makefile     wacom.h         wacom.mod.o  wacom_sys.o  wacom_wac.o
Makefile.in  wacom.ko        wacom.o      wacom_wac.c

``` hope this helps :)
[/FONT]

---

### Post by em es on 2007-12-25
So you HAVE got a wacom.ko, that's a start. Have you tried deleting one of the wacom "pad" sections mentioned by neko18? and then rebooting?

---

### Post by ThomasWii on 2007-12-25
deleted one, no change.

---

### Post by neko18 on 2007-12-25
What is the output of:
1. ```
lsmod | grep wacom
```
2. ```
lsusb | grep -i wacom
```
3. ```
sudo rmmod wacom
sudo modprobe wacom
grep -i wacom /var/log/messages | tail
```
4. ```
md5sum /lib/modules/2.6.22-14-generic/kernel/drivers/input/tablet/wacom.ko
```

---

### Post by ThomasWii on 2007-12-25
1:```
wacom                  18944  0 
usbcore               138632  6 usbhid,wacom,lmpcm_usb,ehci_hcd,uhci_hcd

```

2:```
Bus 001 Device 003: ID 056a:0065 Wacom Co., Ltd 

```

3:```
root@thomas-laptop:/home/thomas# sudo rmmod wacom
root@thomas-laptop:/home/thomas# sudo modprobe wacom
root@thomas-laptop:/home/thomas# grep -i wacom /var/log/messages | tail
Dec 26 02:20:41 thomas-laptop kernel: [  324.816000] usbcore: deregistering interface driver wacom
Dec 26 02:20:49 thomas-laptop kernel: [  332.732000] input: Wacom Bamboo as /class/input/input13
Dec 26 02:20:49 thomas-laptop logger: device 1-2:1.0 is bound to the wacom driver
Dec 26 02:20:49 thomas-laptop kernel: [  332.784000] usbcore: registered new interface driver wacom
Dec 26 02:20:49 thomas-laptop kernel: [  332.784000] /home/thomas/bamboo/linuxwacom-0.7.9-4/src/2.6.22/wacom_sys.c: v1.46-pc0.2:USB Wacom Graphire and Wacom Intuos tablet driver
Dec 26 02:21:20 thomas-laptop kernel: [  364.220000] usbcore: deregistering interface driver wacom
Dec 26 02:21:20 thomas-laptop kernel: [  364.280000] input: Wacom Bamboo as /class/input/input14
Dec 26 02:21:20 thomas-laptop kernel: [  364.284000] usbcore: registered new interface driver wacom
Dec 26 02:21:20 thomas-laptop kernel: [  364.284000] /home/thomas/bamboo/linuxwacom-0.7.9-4/src/2.6.22/wacom_sys.c: v1.46-pc0.2:USB Wacom Graphire and Wacom Intuos tablet driver
Dec 26 02:21:20 thomas-laptop logger: device 1-2:1.0 is bound to the wacom driver

```

4:```
70fa0b2040bd0716f3c2643f7bd4276d  /lib/modules/2.6.22-14-generic/kernel/drivers/input/tablet/wacom.ko

``` I hope this helps to

---

### Post by neko18 on 2007-12-25
Two things different
1. Looks fine
2. My device ID is "056a:0017" (from the lsusb command).
3. Looks fine
4. My md5sum is "96ffeb12b1c2efd9c0b679978e38ad14"
I'm not sure if either difference is significant. What is the full name of your tablet model? (ex.: "Wacom Bamboo Fun (White, Small)")

---

### Post by ThomasWii on 2007-12-25
All i know is that its a wacom bamboo, it's black, i don't think its a fun one, and the model is MTE-450

---

### Post by neko18 on 2007-12-25
Oh I have a Bamboo Fun, so that accounts for the different "lsusb" ID. I'm not sure why the md5sum is different.

First, respond with a post telling me the output of ```
ls /dev/input
```

When you're done posting that, try following the instructions (again) that I posted under "Edit 2" on [http://ubuntuforums.org/showpost.php?p=4014522&postcount=42](http://ubuntuforums.org/showpost.php?p=4014522&postcount=42) . When you're done with those, reboot and tell me if your tablet works.

---

### Post by ThomasWii on 2007-12-25
output was ```
by-id    event1   event2  event5  event8  mouse0  mouse3  tablet-bamboo
by-path  event10  event3  event6  event9  mouse1  mouse4  uinput
event0   event11  event4  event7  mice    mouse2  mouse5  wacom

```

---

### Post by neko18 on 2007-12-25
No problems there. That output is what it should be.

---

### Post by ThomasWii on 2007-12-25
Copied with no errors, but still did not work. it's not going well, but we will get there at some point.

---

### Post by neko18 on 2007-12-25
Can you give me the output of this again, now that we have a new driver?
```
sudo rmmod wacom
sudo modprobe wacom
grep -i wacom /var/log/messages | tail
```
After you give me the output, unplug your tablet then plug it back in. Then log out, then log back in.

---

### Post by ThomasWii on 2007-12-25
```
thomas@thomas-laptop:~$ sudo rmmod wacom
thomas@thomas-laptop:~$ sudo modprobe wacom
thomas@thomas-laptop:~$ grep -i wacom /var/log/messages | tail
Dec 26 02:59:14 thomas-laptop kernel: [  150.972000] usbcore: deregistering interface driver wacom
Dec 26 02:59:19 thomas-laptop kernel: [  156.200000] input: Wacom Bamboo as /class/input/input12
Dec 26 02:59:19 thomas-laptop kernel: [  156.236000] usbcore: registered new interface driver wacom
Dec 26 02:59:19 thomas-laptop kernel: [  156.236000] /home/david/bamboo/linuxwacom-0.7.9-4/src/2.6.22/wacom_sys.c: v1.46-pc0.2:USB Wacom Graphire and Wacom Intuos tablet driver
Dec 26 02:59:19 thomas-laptop logger: device 1-2:1.0 is bound to the wacom driver
Dec 26 02:59:33 thomas-laptop kernel: [  170.464000] usbcore: deregistering interface driver wacom
Dec 26 02:59:33 thomas-laptop kernel: [  170.508000] input: Wacom Bamboo as /class/input/input13
Dec 26 02:59:33 thomas-laptop kernel: [  170.512000] usbcore: registered new interface driver wacom
Dec 26 02:59:33 thomas-laptop kernel: [  170.512000] /home/david/bamboo/linuxwacom-0.7.9-4/src/2.6.22/wacom_sys.c: v1.46-pc0.2:USB Wacom Graphire and Wacom Intuos tablet driver
Dec 26 02:59:33 thomas-laptop logger: device 1-2:1.0 is bound to the wacom driver
thomas@thomas-laptop:~$ 

```May i ask, what new driver?

Edit: Still dose not work:(

Edit2: I'm going to sleep at 3:45 GMT

---

### Post by neko18 on 2007-12-25
I had you install a new driver when I told you to do the contents of "Edit 2". The file "wacom.ko" is a driver.

I honestly have no idea why this isn't working. I'll think about it and get back to you if I have any ideas. Check this thread every so often in the meantime.

---

### Post by ThomasWii on 2007-12-25
Ok then, I'm going to sleep now, i will be back on about 11ish in the morning. GMT

---

### Post by neko18 on 2007-12-25
That's rather early where I am, so don't expect me to be back then :)

---

### Post by majje on 2007-12-26
Thanks for the how to:) It almost worked directly out of the box.

It's important that you choose the latest development, 0.7.9-4,  version of libwacom, as the version I tried at first, 0.7.8-3, can't build for a 2.6.22 system.

To get the ./configure output to be exactly as yours, I had to add the option --enable-dlloader.

---

### Post by ThomasWii on 2007-12-26
Here's the xorg if u can see anything wrong with is.```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"uk"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
	VideoRam	64000
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-68
	VertRefresh	50-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800" "1280x768" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"		"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection
```

Edit: when i went to /dev/input, the files "wacom" and "tablet-bamboo" linked to event9

---

### Post by em es on 2007-12-26
When you reboot you should see GRUB at the start, select this "2.6.22-14-generic" and see if it works.

---

### Post by ThomasWii on 2007-12-26
thats the one i use anyway

---

### Post by em es on 2007-12-26
Hmm... let me get this straight:
- your xorg.conf file looks fine
- The wacom.ko file has been compiled and now resides in the appropriate kernel module directory
- all this has been done using one kernel, so there is no mix-up

Now I know this sounds really stupid, but I discovered that I had plugged my bamboo in a firewire slot for some time and it didn't work. Maybe changing the usb slot and rebooting could help?

---

### Post by ThomasWii on 2007-12-26
Nope still dun work :(

---

### Post by em es on 2007-12-26
I've got a problem too:
Ever since I installed that driver the wacom does work. But not in the way t should.

You have to touch the pad with the pen in order to move the cursor and then it moves slowly. I think the cursor is supposed to move when you hover over the pad and click when you touch it. Wacomcpl does see all of these hovering x- and y-values etc but how do I apply that to the cursor?

It's basically as though you move your regular mouse and that movement is only trasferred to the cursor when you cick the mouse and then it moves extremely slowly, so you have to push the mouse across your desktop to move 10cm on the screen.

---

### Post by ThomasWii on 2007-12-26
i'v just discoved something, when i plug it in, for 2 secs i can move the mouse

Edit: when i put in wacomcpl this comes up ```
thomas@thomas-laptop:~$ wacomcpl
wacomcpl: using TCLLIBPATH="[list  /usr/local/lib ]"
Error in startup script: Error (2): WacomConfigOpenDevice: No such device
Get: Failed to open device 'Synaptics'
    while executing
"exec xsetwacom get $dev TabletID "
    (procedure "createDeviceList" line 14)
    invoked from within
"createDeviceList "
    (procedure "createControls" line 7)
    invoked from within
"createControls"
    (file "/usr/local/bin/wacomcpl-exec" line 1611)
thomas@thomas-laptop:~$ 



```

---

### Post by ThomasWii on 2007-12-26
bumb

---

### Post by em es on 2007-12-26
Sorry I've told you all I know, I'm not very experienced. I'm sure you will get it to work, if not immediately then after the next kernel update. (native wacom bamboo support)

---

### Post by neko18 on 2007-12-26
[QUOTE=em es]Ever since I installed that driver the wacom does work. But not in the way t should.

You have to touch the pad with the pen in order to move the cursor and then it moves slowly. I think the cursor is supposed to move when you hover over the pad and click when you touch it. Wacomcpl does see all of these hovering x- and y-values etc but how do I apply that to the cursor?

It's basically as though you move your regular mouse and that movement is only trasferred to the cursor when you cick the mouse and then it moves extremely slowly, so you have to push the mouse across your desktop to move 10cm on the screen.[/QUOTE]
I have this problem once in a while as well. It fixes itself when I log out then in again. It's rather annoying.

[QUOTE=ThomasWii]when i put in wacomcpl this comes up
```
thomas@thomas-laptop:~$ wacomcpl
wacomcpl: using TCLLIBPATH="[list  /usr/local/lib ]"
Error in startup script: Error (2): WacomConfigOpenDevice: No such device
Get: Failed to open device 'Synaptics'
    while executing
"exec xsetwacom get $dev TabletID "
    (procedure "createDeviceList" line 14)
    invoked from within
"createDeviceList "
    (procedure "createControls" line 7)
    invoked from within
"createControls"
    (file "/usr/local/bin/wacomcpl-exec" line 1611)
thomas@thomas-laptop:~$
```[/QUOTE]
I also have this problem on my laptop. Somehow the Syntaptics touchpad driver interferes with Wacomcpl. I reported the bug to the Linux Wacom Project yesterday. If you're interested, I can make a custom control panel for it. It will probably take about a week.

---

### Post by ThomasWii on 2007-12-26
What's  custom control panel?

---

### Post by em es on 2007-12-26
I think he means a graphical script/programm, so that you don't have to mess around with the terminal too much to set this thing up. Is that correct?

And the problem doesn't go away when I relogin. I wonder what could have caused it...

Well I am very interested in a custom control panel and I'd be very grateful to you if you made one.

---

### Post by ThomasWii on 2007-12-26
neko18, if you could make a custom control panel i would be very grateful, but it feels like a lot for you to do, and if your too busy i will understand.

Thomas

---

### Post by neko18 on 2007-12-26
@ThomasWii and @em es:
I actually meant a replacement for WacomCpl, a way to edit your tablet's settings (such as the keypad/button commands) after it was set up. I would rather not make an install script for this, because I've read from various sources that the next kernel (2.6.23) will support the Bamboo and Bamboo Fun by default.

---

### Post by ThomasWii on 2007-12-26
is 2.6.23 the same as 8.04?

---

### Post by neko18 on 2007-12-26
I think so. I don't think Ubuntu updates kernels within a release.

I will post instructions to compile and install the CVS (development) version in a moment.

**Edit:**
0. Install required packages
```
sudo apt-get install cvs autoconf automake libtool
```

1. Download the CVS version. Just press enter when it asks for a password.
```
cvs -d:pserver:anonymous@linuxwacom.cvs.sourceforge.net:/cvsroot/linuxwacom login
cvs -z3 -d:pserver:anonymous@linuxwacom.cvs.sourceforge.net:/cvsroot/linuxwacom co -P linuxwacom-dev
cd linuxwacom-dev
```

1.5. Generate a configure script
```
./bootstrap
```

2. Compile and install it
```
./configure --enable-wacom
make
sudo make install
```

3. Backup and replace your old Wacom driver
```
cp /lib/modules/2.6.22-14-generic/kernel/drivers/input/tablet/wacom.ko wacom.ko.backup
sudo cp src/2.6.22/wacom.ko /lib/modules/2.6.22-14-generic/kernel/drivers/input/tablet/wacom.ko
```

4. Check your drivers, this should have no output. If it does have output, respond with the output.
```
sudo depmod -e
```

5. Install more utilities
```
cd prebuilt
sudo ./uninstall
sudo ./install
```

6. Reboot

**Edit 2:**
P.S.: The world should be flat. You're probably sleeping right now.

---

### Post by ThomasWii on 2007-12-27
thomas@thomas-laptop:~/linuxwacom-dev$ ./configure --enable-wacom
bash: ./configure: No such file or directory

---

### Post by neko18 on 2007-12-27
Oh, sorry, I forgot a step. I'll edit the post in a couple minutes after I figure out what packages you'll need.

**Edit:**
Okay, I edited the post. Start from step 0.

---

### Post by Flutterby on 2007-12-27
Thanks to the kind people in this thread, it's helped me a lot. I've followed every instruction in this thread.

However, My Bamboo [not-Fun] is working in mouse-mode now, but xsetwacom isn't able to find it at all.  (And neither is gimp, for example.)  Anybody have any ideas on how to resolve this please?

---

### Post by neko18 on 2007-12-27
@Flutterby:
*em es* had the same problem, and I have that problem if I unplug my tablet (Bamboo Fun) then plug it back in. I don't really know how to help you on that. Mine fixes itself if I log out then log back in (i.e., restart X).

It seems the Bamboo Fun has better support by Linux Wacom.

If you have extra time, you could try following my instructions for the CVS version (post #83, [http://ubuntuforums.org/showpost.php?p=4020664&postcount=83](http://ubuntuforums.org/showpost.php?p=4020664&postcount=83) ). I haven't tried it yet myself, so I can't promise it will work.

---

### Post by ThomasWii on 2007-12-27
nope still dun work, why am i the only one who has this problem?

---

### Post by em es on 2007-12-27
The really weird thing is:

I've got two Ubuntu OS on my system, one is an Edgy Eft version in don't use anymore and the other is my Gutsy Gibbon.
And my bamboo works perfectly in Edgy Eft, the older one. In my Gutsy Gibbon install it doesn't recognise the stylus hovering while in Edgy Eft it does, and it does without me installing any additiional software.

I just tested it, I don't know why, but it is really weird since it is an old kernel and really shouldn't support the Bamboo when even the newest one doesn't...

---

### Post by neko18 on 2007-12-27
@em es:
No vanilla Ubuntu install supports the Bamboo or Bamboo Fun tablets, so you probably did install additional software at some point and either didn't know it or forgot about it.

---

### Post by em es on 2007-12-28
Ah... What exactly is vanilla ubuntu? - If we knew what additional software that was, wouldn't it help things?

---

### Post by Flutterby on 2007-12-28
@neko18: thanks for the reply, and all the work you've been putting into this, I installed the cvs version but sadly no dice; it's still "mouse only". I suppose it will not work for me. I will probably return it and exchange if for a Bamboo Fun, since that seems to be working better for people, and see if that works.

---

### Post by neko18 on 2007-12-28
@em es:
Vanilla Ubuntu just means Ubuntu without anything installed.
This is the definition I was going for (m-w.com):
Main Entry : vanilla 
Function : adjective
2 : lacking distinction : plain ordinary conventional

It would help to know the additional software, but I'm not sure how to find out what is actually going on to make it work correctly.

@Flutterby:
If possible, you may want to exchange for a Graphire instead, since those are fully supported by default. However, they are no longer in production so the store may not have them. Either way, I wish you better luck with the new tablet (if you do get a new one).

@both of you:
Can you give me the output of this (with the tablet plugged in)? I just want to know what tablet models aren't supported.
```
lsusb | grep -i wacom
```

---

### Post by Flutterby on 2007-12-28
@neko18: no Graphires at that place, only the Bamboo range.

Here is the information you asked for.

```
dok@dinah:~$ lsusb | grep -i wacom
Bus 001 Device 007: ID 056a:0065 Wacom Co., Ltd

```

---

### Post by neko18 on 2007-12-28
You have the same one as ThomasWii (056a:0065), he couldn't get his working either.

A Bamboo Fun should work though, I tried mine (056a:0017 / Bamboo Fun Small) on three different computers (my laptop, a friend's laptop, and another friend's desktop, all Ubuntu 7.10) with no issues.

---

### Post by hou5ton on 2007-12-28
neko18;

Worked perfectly.  Thank you very much for putting this information out there.

---

### Post by em es on 2007-12-29
my output to "lsusb | grep -i wacom"
is
```
Bus 001 Device 005: ID 056a:0065 Wacom Co., Ltd 

```

---

### Post by Flutterby on 2007-12-29
> **neko18 said:**
> You have the same one as ThomasWii (056a:0065), he couldn't get his working either.

A Bamboo Fun should work though, I tried mine (056a:0017 / Bamboo Fun Small) on three different computers (my laptop, a friend's laptop, and another friend's desktop, all Ubuntu 7.10) with no issues.

Yeah and em es has the same one as well, so I guess that is the problem.

D'you know if there's a way a relative noob like me can help the devs get issues fixed?

---

### Post by neko18 on 2007-12-29
@Flutterby:
You could report a bug to the Linux Wacom Project bug tracker. Its URL is [http://sourceforge.net/tracker/?group_id=69596&atid=525124](http://sourceforge.net/tracker/?group_id=69596&atid=525124) . Make sure you bookmark your bug report after you file it and check up every once in a while in case the developers have questions for you. When you report it, make sure you give them the output of `lsusb | grep -i wacom` and the output of `cat /etc/X11/xorg.conf`. Also, mention that you're using Ubuntu 7.10 with the CVS version of Linux Wacom.

@hou5ton:
Will you please give me the output of this command, so I can keep a list of which tablets do and do not work? Be sure to plug in your tablet before running it.
```
lsusb | grep -i wacom
```

---

### Post by linux_kid on 2007-12-30
Will this work in Feisty?  Thanks!

---

### Post by neko18 on 2008-01-01
No, not as-is. If you would like me to adapt some Feisty instructions for you, please post the output of:
```
uname -r
```

---

### Post by linux_kid on 2008-01-01
neko18, here's the output
```
kevin@ubuntu:~$ uname -r
           2.6.20-16-generic

```

---

### Post by neko18 on 2008-01-01
For Ubuntu 7.04 (Feisty). These instructions are **untested**.


0. Check to be sure the output is "2.6.20-16-generic":
```
uname -r
```

0.5. Plug in your tablet. Run this command:
```
lsusb | grep -i wacom
```
My output was "[...] ID 056a:0017 Wacom Co., Ltd". "056a:0017" is a Bamboo Fun Small. Yours may not work with these instructions if you have a different model. "056a:0065" is known not to work with these instructions.


1. Create a directory to work in
```
mkdir bamboo
cd bamboo
```


2. Install dependencies
```
sudo apt-get install build-essential x11proto-core-dev libxau-dev libxdmcp-dev x11proto-input-dev x11proto-kb-dev xtrans-dev libx11-dev x11proto-xext-dev libxext-dev libxi-dev linux-libc-dev libc6-dev libncurses5-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev
```


3. Download and extract Linux Wacom
```
wget http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.7.9-4.tar.bz2
tar xjf linuxwacom-0.7.9-4.tar.bz2 
cd linuxwacom-0.7.9-4/
```


4. Configure and ensure the output is correct.
```
./configure --enable-wacom
----------------------------------------
  BUILD ENVIRONMENT:
       architecture - i486-linux-gnu ## this does not have to be the same ##
       linux kernel - yes 2.6.20
  module versioning - yes -DCONFIG_MODVERSIONS -DMODVERSIONS -include /lib/modules/2.6.20-16-generic/build/include/linux/modversions.h
      kernel source - yes /lib/modules/2.6.20-16-generic/build
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - no
           dlloader - yes
               XLib - yes /usr/lib
                TCL - yes /usr/include/tcl8.4/
                 TK - yes /usr/include/tcl8.4/
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
        tabletdev.o - no
       wacom_drv.so - yes /usr/lib/xorg/modules/input 
        wacom_drv.o - no
----------------------------------------
```


5. Compile and install
```
make
sudo make install
```


6. Backup your X11 configuration then open it in Gedit
```
cd ..
cp /etc/X11/xorg.conf .
gksudo gedit /etc/X11/xorg.conf
```


7. Find the section that looks like this (should start at the third section in the file). This may be slightly different, but hopefully you can figure it out.
```
Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection
```


8. Replace those lines with this
```
Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection
```


9. Find the section that looks like this (should be the last section in the file). Again, this may be a bit different.
```
# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
```


10. Replace those lines with
```
# Uncomment if you have a wacom tablet
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"		"SendCoreEvents"
```


11. Save the file (Ctrl-S) and close Gedit (Ctrl-Q)


12. Backup your old Wacom module and replace it with the new one
```
cp /lib/modules/2.6.20-16-generic/kernel/drivers/input/tablet/wacom.ko .
sudo cp linuxwacom-0.7.9-4/src/2.6.20/wacom.ko /lib/modules/2.6.20-16-generic/kernel/drivers/input/tablet/wacom.ko
```


13. Check for any errors (this should have no output)
```
sudo depmod -e
```


14. Install Wacom utilities
```
cd linuxwacom-0.7.9-4/prebuilt
sudo ./uninstall
sudo ./install
```


15. Reboot your computer


16. If you want to configure your tablet, run the following command in a terminal
```
wacomcpl
```

---

### Post by ninique on 2008-01-03
I'm having trouble with these instructions. When I use the **--enable-wacom** command, it gets me this: 
```

......
***
*** WARNING:
*** The tcl development environment does not appear to
*** be installed. The header file tcl.h does not appear
*** in the include path. Do you have the tcl rpm or
*** equivalent package properly installed?  Some build
*** features will be unavailable.
***
checking for tk header files... not found; tried /usr/include and /include
***
*** WARNING:
*** The tk development environment does not appear to
*** be installed. The header file tk.h does not appear
*** in the include path. Do you have the tk rpm or
*** equivalent package properly installed?  Some build
*** features will be unavailable.
***
checking ncurses.h usability... yes
checking ncurses.h presence... yes
checking for ncurses.h... yes
***
*** WARNING:
*** libwacomxi requires tcl environment; libwacomxi will not be built.
***
checking for Wacom X driver module path... /usr/lib/xorg/modules/input
checking for pkg-config... no
checking for XSERVER... configure: error: The pkg-config script could not be fou                                                                                                                         nd or is too old.  Make sure it
is in your PATH or set the PKG_CONFIG environment variable to the full
path to pkg-config.

Alternatively, you may set the environment variables XSERVER_CFLAGS
and XSERVER_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


```

Does someone know what that means? What's going wrong? 

I'm using Kubuntu Gutsy, a bamboo fun, and the latest driver from the site ( linuxwacom-0.7.9-4). Actually, I did make a mistake at first and downloaded the 0.7.8-3 one and it didn't give me that message about the pkg-config (although the other three messages were there), but then I realised that my kernel wasn't supported.

---

### Post by ~/Chromekaldra/~ on 2008-01-05
I can't write to the directory...says i don't have permission, even though there is sudo throughout the commands...

---

### Post by sailesh on 2008-01-06
I have a Wacom Bamboo (not Fun) model "056a:0065" also.  It's working perfectly for me!  I am on Ubuntu 7.10.  This is what I did:
- Upgraded Kernel to 2.6.23
- Followed the instructions to modify the xorg.conf file ([http://linuxwacom.sourceforge.net/index.php/howto/inputdev](http://linuxwacom.sourceforge.net/index.php/howto/inputdev))

Now I have to figure out what other issues upgrading the kernel brings. (I am a noob).

---

### Post by neko18 on 2008-01-08
**@ninique:**
See my walkthrough on page 4 (direct link: [http://ubuntuforums.org/showpost.php?p=4014004&postcount=32](http://ubuntuforums.org/showpost.php?p=4014004&postcount=32) )

**@~/Chromekaldra/~**
Can you give me the full terminal output?

---

### Post by gottferdamnt on 2008-01-08
mmmmkay. My wacom works but the vertical scroll of my synaptic touchpad doesn't anymore. Weird.     Moreover I can't run wacomcpl.

---

### Post by jaskah on 2008-01-09
hello
i have two kernels installed on my computer:
2.6.22-14-generic
2.6.22-14-rt  (real time kernel)
i generally run the real time kernel.
i´ve been able to install my wacom bamboo on the 2.6.22-14-generic but when i boot into the 2.6.22-14-rt kernel the wacom doesn´t work.
does anyone know how i can have the wacom working with the 2.6.22-14-rt  kernel ***as well*** as the 2.6.22-14-generic kernel?
thanks in advance for any help!

---

### Post by Icemanyurt on 2008-01-11
I was able to get my wacom tablet working under 7.10 following the directions earlier in this thread, however wacomcpl does not work.  

I received this output at the end :
> 
Installing Wacom man page......
/usr/bin/install: cannot stat `wacom.4x.gz': No such file or directory
Installed under /usr/share/man/man4
./install: line 24: cd: 64: No such file or directory

Installing wacom_drv....
/usr/bin/install: cannot stat `wacom_drv.so': No such file or directory
/usr/bin/install: cannot stat `wacom_drv.so': No such file or directory
wacom_drv.so installed under /usr/lib64/xorg/modules/input

Installing utility programs (wacdump, xidump, xsetwacom....)
/usr/bin/install: cannot stat `libwacomcfg.la': No such file or directory
/usr/bin/install: cannot stat `.libs/libwacomcfg.so.0.0.1': No such file or directory
/usr/bin/install: cannot stat `.libs/libwacomcfg.lai': No such file or directory
/usr/bin/install: cannot stat `.libs/libwacomcfg.a': No such file or directory
chmod: cannot access `/usr/local/lib/libwacomcfg.a': No such file or directory
ranlib: '/usr/local/lib/libwacomcfg.a': No such file
/usr/bin/install: cannot stat `wacdump': No such file or directory
/usr/bin/install: cannot stat `xidump': No such file or directory
/usr/bin/install: cannot stat `.libs/xsetwacom': No such file or directory
Installed under /usr/local/bin
/usr/bin/install: cannot stat `wacomcfg.h': No such file or directory

Installing wacomcpl......
/usr/bin/install: cannot stat `wacomcpl': No such file or directory
/usr/bin/install: cannot stat `wacomcpl-exec': No such file or directory
Installed under /usr/local/bin
/usr/bin/install: cannot stat `pkgIndex.tcl': No such file or directory
/usr/bin/install: cannot stat `libwacomxi.la': No such file or directory
/usr/bin/install: cannot stat `.libs/libwacomxi.so.0.0.0': No such file or directory
/usr/bin/install: cannot stat `.libs/libwacomxi.lai': No such file or directory
/usr/bin/install: cannot stat `.libs/libwacomxi.a': No such file or directory
chmod: cannot access `/usr/local/lib/TkXInput/libwacomxi.a': No such file or directory
ranlib: '/usr/local/lib/TkXInput/libwacomxi.a': No such file


You need to compile and install wacom.(k)o manually if your kernel is out of date.

After adding your Wacom tools into /etc/X11/xorg.conf, please restart X server or simply reboot your system to run the new Wacom X driver.


When trying to run wacomcpl I get this error:
> 
bash: wacomcpl: command not found


Any help would be great...:)

---

### Post by neko18 on 2008-01-13
**@gottferdamnt**: Mine too. I just use the arrow keys, pgup/pgdn, and autoscroll (Firefox: Edit>Preferences>Advanced>General>Browsing>Use autoscrolling) now though.

What is the output of this command?
```
wacomcpl
```


**@jaskah**: Run this:
```
cp /lib/modules/2.6.22-14-generic/kernel/drivers/input/tablet/wacom.ko /lib/modules/2.6.22-14-rt/kernel/drivers/input/tablet/wacom.ko
```


**@Icemanyurt**: Did you follow my instructions ([link]("http://ubuntuforums.org/showpost.php?p=4014004&postcount=32"), on page 4 of this thread) or the instructions in the first post? I got that error when I initially followed the instructions in the first post.

---

### Post by ~/Chromekaldra/~ on 2008-01-15
Sorry, been held up a bit; this is what i get when i try to move/save stuff to the directory:

"you do not have write acess to the specified directory" -> this an opera pop up window when i try to save the linux-wacom drivers tarball. Furthermore, when i try to drag it to the directory after saving it to my desktop, i get: ''You do not have permissions to write to this folder.'' I also cannot create the new text file in the direc as per the instructions...it appears this is all a superuser problem?

thank you for offering help, i REALLY appreciate it as i know it must be hard trying to help when there is dozens upon dozens of people asking :(

---

### Post by ShelJ on 2008-01-18
> **ThomasWii said:**
> nope still dun work, why am i the only one who has this problem?

You're not the only one  ...  :(:(

---

### Post by autoexec on 2008-01-18
> **neko18 said:**
>  "056a:0065" is known not to work with these instructions.


havent read the whole thread, but ive got that device code and your instructions worked for me

---

### Post by ~/Chromekaldra/~ on 2008-01-18
BUMP

> **~/Chromekaldra/~ said:**
> Sorry, been held up a bit; this is what i get when i try to move/save stuff to the directory:

"you do not have write acess to the specified directory" -> this an opera pop up window when i try to save the linux-wacom drivers tarball. Furthermore, when i try to drag it to the directory after saving it to my desktop, i get: ''You do not have permissions to write to this folder.'' I also cannot create the new text file in the direc as per the instructions...it appears this is all a superuser problem?

thank you for offering help, i REALLY appreciate it as i know it must be hard trying to help when there is dozens upon dozens of people asking :(

---

### Post by neko18 on 2008-01-18
To all reading this thread who are requesting help: I will usually take 2 to 4 days to respond, but I *will* respond eventually. "Bumping" the thread probably won't help much.

@**~/Chromekaldra/~**:
I assume you are following the original instructions (the first post in this thread), which *do not work* as-is. I strongly suggest you follow my instructions, which are located at [http://ubuntuforums.org/showpost.php?p=4014004&postcount=32](http://ubuntuforums.org/showpost.php?p=4014004&postcount=32)

@**ShelJ**:
As I've said to others, have you tried my instructions at [http://ubuntuforums.org/showpost.php?p=4014004&postcount=32](http://ubuntuforums.org/showpost.php?p=4014004&postcount=32) ?

@**autoexec**:
Thanks, I'll modify the post

---

### Post by ShelJ on 2008-01-18
Ok, getting frustrated now  ...  :(

I've ben thru this entire post three times already, everything "appears" to work the way it should, however it tells me that there is no device present.

**lsusb** and **lsusb | grep -i wacom** identifies my tablet as

```
lsusb
Bus 001 Device 004: ID 056a:0065 Wacom Co., Ltd 
 lsusb | grep -i wacom
Bus 001 Device 004: ID 056a:0065 Wacom Co., Ltd 

```

and running **wacomcpl** shows no devices present, nor does **xsetwacom**.  I even tried unplugging and plugging it back in.  I've also downloaded everything to do w/ Wacom from Synaptic.

What is most frustrating is that I had it running last week using this thread, but I wanted to try Ubuntu-Studio which crashed my computer.  I'm running Xubuntu 7.10(64).

Everything I looked up refers me back to this thread  Please help, if you can.

---

### Post by jaskah on 2008-01-19
hello
i sent the post pasted below before, but no response.
can anyone help me out with this?
thanks!

> **jaskah said:**
> hello
i have two kernels installed on my computer:
2.6.22-14-generic
2.6.22-14-rt  (real time kernel)
i generally run the real time kernel.
i´ve been able to install my wacom bamboo on the 2.6.22-14-generic but when i boot into the 2.6.22-14-rt kernel the wacom doesn´t work.
does anyone know how i can have the wacom working with the 2.6.22-14-rt  kernel ***as well*** as the 2.6.22-14-generic kernel?
thanks in advance for any help!

---

### Post by ShelJ on 2008-01-19
Ok, nearly a day later, I went through the HOWTO on The Linux Wacom Project website.  Now my tablet works, however when I run **wacomcpl** and try to adjust the pad properties I get 

```
can't read "db(-1)": no such element in array
can't read "db(-1)": no such element in array
    while executing
"set db$cur $db($opt) "
    (procedure "expressKeys" line 25)
    invoked from within
"expressKeys"
    (procedure "initialButton" line 25)
    invoked from within
"$initial"
    (procedure "displaySubWindow" line 32)
    invoked from within
"displaySubWindow  updateButton defaultButton initialButton 6 0 3"
    invoked from within
".panel.button invoke"
    ("uplevel" body line 1)
    invoked from within
"uplevel #0 [list $w invoke]"
    (procedure "tk::ButtonUp" line 22)
    invoked from within
"tk::ButtonUp .panel.button"
    (command bound to event)
```

and the following when I run **xsetwacom**:

```
~$ xsetwacom set pad abswup 4 #scroll up
X Error: 8 BadMatch (invalid parameter attributes)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set pad value for 'AbsWUp'

```  and the same for AbsWDn

---

### Post by neko18 on 2008-01-20
@**jaskah**:
> **jaskah said:**
> i sent the post pasted below before, but no response.
I already responded to you. It's on the top of this page (page 12, post #111).

@**ShelJ**:
I've never needed `wacomcpl` and as long as you don't use the pad buttons (which I don't), `xsetwacom` isn't very useful either. I think it's a better idea to live with a partially working tablet (until the next Ubuntu release, which will support it by default) than to risk the possibility of the tablet not working at all.

---

### Post by jaskah on 2008-01-20
thanks for your reply, but post 111 is not an answer to my post, but someone else´s.
i am specifically asking about how to get the wacom running on both my kernels (as i only run the realtime kernel).

---

### Post by ShelJ on 2008-01-20
Thank-you so much for your help.  Like you say, partially wroking is sufficient for now.  Although it didn't totally work for me, I still think that this is a great thread, keep up the great work.

---

### Post by days_of_ruin on 2008-01-22
So in Hardy Heron it will be plug n play just like a mouse?

---

### Post by wgw on 2008-01-27
worked for my "056a:0065"  -- thanks!

---

### Post by kleinzeit on 2008-01-27
Yay! I had the same problems with wacomcpl as ThomasWii. But installing the latest version of linuxwacom - linuxwacom-0.7.9-7 rather than linuxwacom-0.7.9-4 - has sorted this out :)

My tablet is a 056a:0069 model

---

### Post by ~/Chromekaldra/~ on 2008-01-30
Thanks! You got it working! (Neko18 that is) How do i thank you? (forum wise?) 

ONE PROBLEM though: wacomcpl doesn't work, bash says no command exists...And i'd like to get rid of the full screen setting on the tablet (corners of tablet are screen's corners...sorry, i'm used to the mouse not being like that...)

I had this: 

```

Warning: wacomcpl requires tcl/tk being installed 

./install: line 99: yum: command not found 
./install: line 99: yum: command not found 

Please install tcl/tk then run this script again 

```

Doesn't stop the tablet from woring, just wacomcpl, so i went back through this thread, found that Em Es posted some help, ran the apt-get install for those...whatever they are...something ddl installed, dependancies and stuff...after it was done i tried Wacomcpl again and it still 'doesn't exist' and i wasn't able to run the ./configure commands as there is no configure file...apparently...:D

---

### Post by Mr. Picklesworth on 2008-01-30
Thanks for all the how-tos!

Quick note for anyone who gets really confused like I did: The current stable version (0.7.8.3) does not support Linux kernel 2.6.22. You need to use the development version for now.

---

### Post by cb_rex on 2008-01-31
Hi everyone, I'm totally new to Linux and this thread has been really useful for me.  I carefully followed neko18's instructions, copying and pasting code into the Terminal and I managed to get my Wacom graphics tablet, (056a:0018 Bamboo Fun Medium), working  in 64bit Ubuntu 7.10.

Thanks.


The only problem I've had is when the Wacom Control Panel opens, (see image), it doesn't provide me with any options to fully configure the tablet.  So I was just wondering if there's any way of manually configuring the graphics tablet to get things like pressure sensitivity and the eraser working in GIMP.

From the wacomcpl command I get this output:
wacomcpl: using TCLLIBPATH="[list  /usr/local/lib ]"

---

### Post by Buddy Gurt on 2008-01-31
Exactly the same problem for me. No Extended input devices in The Gimp (eraser, stylus, cursor), and just a blank screen when running wacomcpl.
The tablet works fine as a mouse, but nothing more than that...

---

### Post by linux operative on 2008-01-31
Buddy Gurt: 

I have the same experience.  I was fortunate to find that I have the same model versions, etc as posted in the the tutorial.  So I didn't have any trouble following the post, and cutting/pasting at the command line.  However, I also get errors when I attempt to configure the pad:

maxtor:~$ wacomcpl
wacomcpl: using TCLLIBPATH="[list  /usr/local/lib ]"
Error in startup script: Error (2): WacomConfigOpenDevice: No such device
Get: Failed to open device 'Synaptics'
    while executing
"exec xsetwacom get $dev TabletID "
    (procedure "createDeviceList" line 14)
    invoked from within
"createDeviceList "
    (procedure "createControls" line 7)
    invoked from within
"createControls"
    (file "/usr/local/bin/wacomcpl-exec" line 1611)


I think the "Synaptics" error may be due to using a laptop, and the entry was in the x config file already, and I left it untouched.

I am able to use the mouse, the top-center touch circle (lit in blue), and the stylus.  However, I was unable to get the pressure sensitivity working (even though the function appears to be set correctly within GIMP).

I remain hopeful in finding a solution as the primary reason for using this pad for me is to provide for pressure sensitive input.:confused:

---

### Post by stalkier on 2008-01-31
Do you know if this tutuorial would work for a Tooya Pro graphics tablet? Or any other graphics tablet for that matter? Thanks in advance.

---

### Post by neko18 on 2008-02-02
=========================================
====================

Sorry for the huge post. Just find the part that corresponds to you.

====================
=========================================

**@jaskah**
[quote=jaskah]thanks for your reply, but post 111 is not an answer to my post, but someone else´s.[/quote]
I answered two people in that post, one of them being you. Here's a direct link to the post I'm referring to: [http://ubuntuforums.org/showpost.php?p=4131578&postcount=111](http://ubuntuforums.org/showpost.php?p=4131578&postcount=111)

--------------------------------------------------------------------------

**@ShelJ and @wgw**
[quote=ShelJ]Thank-you so much for your help[/quote]
[quote=wgw]worked for my "056a:0065" -- thanks![/quote]
[quote=Mr. Picklesworth]Thanks for all the how-tos![/quote]
I'm glad I could help

--------------------------------------------------------------------------

**@days_of_ruin**
[quote=days_of_ruin]So in Hardy Heron it will be plug n play just like a mouse?[/quote]
Correct. All older Wacom tablets work like this in Gutsy, but the Bamboo doesn't because it requires a newer driver.

--------------------------------------------------------------------------

**@kleinzeit**
[quote=kleinzeit]But installing the latest version of linuxwacom - linuxwacom-0.7.9-7 rather than linuxwacom-0.7.9-4 - has sorted this out[/quote]
That's great! I'll make a new guide later on.

--------------------------------------------------------------------------

**@~/Chromekaldra/~**
[quote=~/Chromekaldra/~]wacomcpl doesn't work[/quote]
You probably need to install Tk and Tcl to get it working. I've personally never even used `wacomcpl` though, so you may just want to skip installing it. If you're persistent, here's the command to install Tk and Tcl then reinstall `wacomcpl`
```
sudo apt-get install tk8.4 tcl8.4
cd ~/bamboo/linuxwacom-0.7.9-4/prebuilt
sudo ./install
```

[quote=~/Chromekaldra/~]And i'd like to get rid of the full screen setting on the tablet (corners of tablet are screen's corners...sorry, i'm used to the mouse not being like that...)[/quote]
I think you should try absolute positioning mode (a.k.a. "corners" mode) and see if you can get used to it. I didn't like it at first but after a little getting used to I prefer it to the mouse-style motion (relative positioning).

--------------------------------------------------------------------------

**@cb_rex, @Buddy Gurt, and @linux operative**
I'm not sure what's wrong. Can you three post the output of:
```
cat /etc/X11/xorg.conf
```

After you're done with that, try this (read all five steps before beginning):
[LIST=1]
[*]Place your pen (and mouse) out of your tablet's range (10cm, for the sake of a definite measurement)
[*]Press Ctrl-Alt-F1
[*]Wait about 5 seconds
[*]Press Ctrl-Alt-F7
[*]Try out your tablet. Tell me if these instructions worked.
[/LIST]

By the way, I also have a Synaptics touchpad. `wacomcpl` doesn't even open at all for me :) . However, pressure sensitivity and Gimp work okay.

If you would like to see my Gimp settings (File>Preferences, Input Devices, Configure Extended Input Devices...), view the attached image. Please made note of the "Mode" that each "Device" is on.

--------------------------------------------------------------------------

**@stalkier**
[quote=stalkier]would work for a Tooya Pro graphics tablet?[/quote]
No, sorry. It will only work for Wacom tablets.

--------------------------------------------------------------------------

---

### Post by neko18 on 2008-02-02
New guide! If you already have your tablet working, please don't go through this guide. This is for people who are newly installing Linux Wacom.

---------------------------------------------

Plug in your tablet, then open a terminal (Applications > Accessories > Terminal). As you follow through the steps, paste the code (line-by-line) into the terminal and press enter after each line. If it prompts you for your password, type in your password (which will not show up as you type it) then press enter.

1.
```
uname -r
```
Make sure the output has "2.6.22-14" in it.

2.
```
lsusb | grep -i wacom
```
Look for the part of that line in the form "056a:####" ("#" being 0-9 or a-f)
Make sure yours is listed here: "056a:0017", "056a:0018", "056a:0065", "056a:0069"

3.
```
mkdir wacom
cd wacom
```

4.
```
sudo apt-get install linux-headers-`uname -r` build-essential x11proto-core-dev libxau-dev libxdmcp-dev x11proto-input-dev x11proto-kb-dev xtrans-dev libx11-dev x11proto-xext-dev libxext-dev libxi-dev linux-libc-dev libc6-dev libncurses5-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev
```
It may ask you for your password

5.
```
wget http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.7.9-7.tar.bz2
tar xjf linuxwacom-0.7.9-7.tar.bz2
cd linuxwacom-0.7.9-7/
```

6.
```
./configure --enable-wacom
make
sudo make install
```

7.
```
cd ..
cp /etc/X11/xorg.conf .
gksudo gedit /etc/X11/xorg.conf
```

8. Find the section that looks like this (should start at the third section in the file)
```
Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection
```

9. Replace those lines with this
```
Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection
```

10. Find the section that looks like this (should be near the end of the file)
```
# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
```

11. Replace those lines with
```
# Uncomment if you have a wacom tablet
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"		"SendCoreEvents"
```

12. Save the file (Ctrl-S) and close Gedit (Ctrl-Q)

13.
```
for kern in `ls /lib/modules`; do
cp /lib/modules/$kern/kernel/drivers/input/tablet/wacom.ko wacom.ko.$kern
sudo cp linuxwacom-0.7.9-7/src/2.6.22/wacom.ko /lib/modules/$kern/kernel/drivers/input/tablet/wacom.ko
done
```
You may get a couple errors such as "cp: cannot stat[...]" or "cp: cannot create regular file[...]" but you can just ignore those.

These may yield errors ("No such file or directory" or "Cannot create regular file"), but you may safely ignore them.

14.
```
sudo depmod -e
```
This command should have no output. If it does, please post with the output.

15.
```
cd linuxwacom-0.7.9-7/prebuilt
sudo ./uninstall
sudo ./install
```

16.
```
cd ../..
wget 'http://git.debian.org/?p=users/ron/wacom-tools.git;a=blob_plain;f=debian/xserver-xorg-input-wacom.udev;hb=master' -O wacom.udev
cp /etc/udev/rules.d/50-xserver-xorg-input-wacom.rules wacom.udev.backup
sudo cp wacom.udev /etc/udev/rules.d/50-xserver-xorg-input-wacom.rules
```

17. Reboot your computer

18. If you want to configure your tablet, open the terminal again and run this:
```
wacomcpl
```
This command may not work. If it doesn't, don't worry. It won't work on most laptops.

---

### Post by scunc_dvl on 2008-02-02
I have noticed serious stability problems with my X server:
- I cannot use CTRL+ALT+F1 and CTRL+ALT+F7 again without X restarting, even in the login and even when using ICEwm
- Wine causes X to restart often as well

Commenting these lines in my xorg.conf makes my X stable again:

#    InputDevice    "stylus" "SendCoreEvents"
#    InputDevice    "cursor" "SendCoreEvents"
#    InputDevice    "eraser" "SendCoreEvents"
#    InputDevice    "pad" "SendCoreEvents"

(With these lines commented, I can still see my tablet move the cursor slowly in "relative" mode, and the buttons are all different. *shrug*).

Some notes about my setup:
[INDENT]
I am using linuxwacom-0.7.9-6 (the development version), this could be causing the stability problems as there is already a new version of the drivers out by now.

I am using a dual-head Xinerama setup, and I'm using the nvidia drivers downloaded from nvidia.com.

Oh and I'm using Gutsy 7.10 amd64.

**EDIT: These crashes I have also duplicated on my 64-bit Gutsy laptop, which does Not have Xinerama running.**

[/INDENT]

Please fix, lead me to the fix or lead me to the place to submit a crash report, thanks.

---

### Post by neko18 on 2008-02-03
**@scunc_dvl**
> Commenting these lines in my xorg.conf makes my X stable again:
This is just a guess, but have you tried removing SendCoreEvents?
```

InputDevice "stylus"# "SendCoreEvents"
InputDevice "cursor"# "SendCoreEvents"
InputDevice "eraser"# "SendCoreEvents"
InputDevice "pad"# "SendCoreEvents"

```

> Please fix, lead me to the fix or lead me to the place to submit a crash report, thanks.
Here's the Linux Wacom bug tracker: [http://sourceforge.net/tracker/?group_id=69596&atid=525124](http://sourceforge.net/tracker/?group_id=69596&atid=525124)

---

### Post by cb_rex on 2008-02-03
> **neko18 said:**
> 
**@cb_rex, @Buddy Gurt, and @linux operative**
I'm not sure what's wrong. Can you three post the output of:
```
cat /etc/X11/xorg.conf
```

After you're done with that, try this (read all five steps before beginning):
[LIST=1]
[*]Place your pen (and mouse) out of your tablet's range (10cm, for the sake of a definite measurement)
[*]Press Ctrl-Alt-F1
[*]Wait about 5 seconds
[*]Press Ctrl-Alt-F7
[*]Try out your tablet. Tell me if these instructions worked.
[/LIST]

By the way, I also have a Synaptics touchpad. `wacomcpl` doesn't even open at all for me :) . However, pressure sensitivity and Gimp work okay.

If you would like to see my Gimp settings (File>Preferences, Input Devices, Configure Extended Input Devices...), view the attached image. Please made note of the "Mode" that each "Device" is on.


I've attached my output of "cat /etc/X11/xorg.conf" as a text file as its quite long.  The second instructions made no difference and GIMP doesn't recognize the graphics tablet as an extended input device, so it can't be configured.   

Thanks for looking into this problem, I'll be ok with the basic pen function for the time being anyways, as I'm dual booting with XP, also it gives me a good excuse to concentrate on vector art as the pen works really well for drawing and node editing in Inkscape.

---

### Post by neko18 on 2008-02-04
**@cb_rex**

Plug in your tablet and make sure it's working, then run these two commands:
```
ls -lR /dev/input > ~/Desktop/neko18_dev.txt
cat /proc/bus/input/devices > ~/Desktop/neko18_proc.txt
```

Two new files will appear on your desktop, neko18_dev.txt and neko18_proc.txt. Upload those here please (you can delete them when you're done).

One thing I noticed is that your default mouse doesn't have a device point (i.e. a `/dev/input/*` file) defined in `/etc/X11/xorg.conf`, so it's possible that your tablet is actually being detected as a mouse. The output of those commands will allow me to verify (or disprove) that and formulate a possible solution.

Vectors are fun :) Just a little tip: when doing vector art, you shouldn't need the path tool very much at all, unless you're just making straight lines. Coming from a raster background, I initially relied on the path tool much more than I should have.

---

### Post by cb_rex on 2008-02-05
You'll never believe this... I managed to get the tablet working fully earlier today, (even the wacomcpl displayed properly and I could define buttons, get pressure sensitivity, etc.). 

I achieved this by doing a clean install, downloading the updates, then the only different thing I did before attempting to set up the tablet was installing the "ubuntu-restricted-extras" this shouldn't make any difference?  Then I followed your latest instructions to set up the tablet, inserting the ubuntu CD when prompted and it worked perfectly.

However...  After playing with the tablet for about 20mins defining the buttons etc.  Some new linux headers updates appeared and after downloading, installing and rebooting the tablet no longer works at all, and the wacomcpl has returned to its useless state as before.

Unfortunately I didn't create any records of my system when the tablet was working, if i get it going again I'll make sure to.

Whats the best way to remove all of the wacom drivers and files so i can try reinstalling the tablet?

I've attached the files you mention, although the tablet isn't working so I'm not sure how much use they'll be.

---

### Post by red_Marvin on 2008-02-05
Nice to stumble upon a fix before I discovered the problem :)
The graphical configuring tool enabled me to configure the buttons nicely but I can't find the settings for all the buttons on the pad: '<' '>' 'FN1' and 'FN2', right now I've only been able to configure the '<' one...

---

### Post by McAviti on 2008-02-05
> **cb_rex said:**
> Y
..
However...  After playing with the tablet for about 20mins defining the buttons etc.  Some new linux headers updates appeared and after downloading, installing and rebooting the tablet no longer works at all, and the wacomcpl has returned to its useless state as before.
..


The same applies for me. Yesterday after a few hours I got my Bamboo Fun working (only with the prebuilt drivers, not the self-compiled). Meanwhile new kernel and kernel headers were installed - and today after booting my tablet didn't work anymore.
I tried to reinstall ist, but then it got worse - the mouse also stopped working.

I have now booted with the -generic instead of the -386 kernel. But the new kernel seems to do somthing nasty to the wacom drivers.

---

### Post by ShelJ on 2008-02-06
I had the exact same problem, I followed the new install instructions, everything worked great (finally) and I got the new updates mentioned.  I did some work with my tablet then went to do something and when I came home and turned on my computer nothing (w/ the tablet) worked, except the pretty lights!  Until this morning I was starting to think that there was something wrong w/ my tablet.

---

### Post by red_Marvin on 2008-02-06
You might already know this, but you need to connect the bamboo before X starts for it to work correctly.

---

### Post by ShelJ on 2008-02-06
Not too sure if you are replying to me, however, I did have it connected.

---

### Post by Buddy Gurt on 2008-02-06
**@neko18:**
This is the output of 'cat /etc/X11/xorg.conf':

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        #Option         "ForceDevice"   "ISDV4"         # Tablet PC ONLY
        Option          "USB"           "on"            # Toegevoegd voor Wacom Bamboo
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        #Option         "ForceDevice"   "ISDV4"         # Tablet PC ONLY
        Option          "USB"           "on"            # Toegevoegd voor Wacom Bamboo
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        #Option         "ForceDevice"   "ISDV4"         # Tablet PC ONLY
        Option          "USB"           "on"            # Toegevoegd voor Wacom Bamboo
EndSection

# Toegevoegd voor Wacom Bamboo:
Section "InputDevice"
        Driver          "wacom"
        Identifier      "pad"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "pad"
        Option          "USB"           "on"
EndSection
# Einde toevoeging

Section "Device"
        Identifier      "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-84
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1680x1050"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "pad"           "SendCoreEvents"        # Toegevoegd voor Wacom Bamboo
        InputDevice     "Synaptics Touchpad"
EndSection

```

Personally, I don't see any problems there, but maybe you're able to find some problems. The solution you suggested (using ctrl-alt-f1 and ctrl-alt-f7) didn't improve anything. Still wacomcpl does not detect any devices, and Gimp says there are "No extended input devices". The tablet still functions as a normal mouse though.

Furthermore, I attached the other two files you suggested.
Hope you can help here!

---

### Post by ~/Chromekaldra/~ on 2008-02-06
I can't set up my tablet in Photoshop to deal with things like pressure sensitivity, it doesn't see my tablet, neither does my VM (where Ps is) I run Windows XP in the Virtual Machine, tried the install CD, but it can't find the drivers, ddl the updated version off the net, doesn't work because it won't go to the next step w/o detecting the tablet, which it doesn't, idk why; as it's plugged directly into my comp, same as all my other devices...

And wacomcpl is still useless, it pops up, but no options other than exit...

And if the tablet is there since start up, it's in corners mode, but if i unplug, plug it in, it's in this useless drag mode where i can't tech 'drag' anything, only dbl touch. (plus i have to press the tablet hard to get the cursor to move)

---

### Post by neko18 on 2008-02-06
.
.
.
**@Anyone who downloaded the recent kernel updates and found their tablet not working**

Don't panic! It's really easy to fix. When the updates were downloaded, Ubuntu simply replaced your custom driver with its own. To fix:

Run this:
```
mkdir wacom2
cd wacom2
```

Go to [http://ubuntuforums.org/showpost.php?p=4253232&postcount=133](http://ubuntuforums.org/showpost.php?p=4253232&postcount=133) and follow steps 5, and 6.

Run this:
```
cd ..
```

Follow steps 13, 14, 15, and 16

Your tablet will work again now

**@cb_rex**

Follow the instructions in the first section of this post ("@Anyone who downloaded...")

When you're done and the tablet is working again, please give me the files generated by these again (the other ones didn't have references to the tablet):
```
ls -lR /dev/input > ~/Desktop/neko18_dev.txt
cat /proc/bus/input/devices > ~/Desktop/neko18_proc.txt
```

**@McAviti**

Follow the instructions in the first section of this post ("@Anyone who downloaded...")

**@ShelJ**

Good job getting it fixed on your own :)

**@Buddy Gurt**

I don't see anything wrong with the files you sent me. I have two suggestions:

Run these commands:
```
sudo cp /etc/X11/xorg.conf ~/xorg.conf.bkup
gksudo gedit /etc/X11/xorg.confg
```
Now find the section that says:
```
# Uncomment if you have a wacom tablet
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "pad"           "SendCoreEvents"
```
And replace it with:
```
# Uncomment if you have a wacom tablet
        InputDevice     "stylus"
        InputDevice     "cursor"
        InputDevice     "eraser"
        InputDevice     "pad"
```

If that doesn't work, try following the instructions in the first section of this post ("@Anyone who downloaded...")

**@~/Chromekaldra/~**
The tablet will not work through a Virtual Machine, sorry. I suggest you try Krita (in Add/Remove) as an alternative to Photoshop or Gimp. It does have CMYK support.

When you unplug and replug the tablet, there are two options to get it working in the correct mode:

Press Ctrl-Alt-F1, wait a couple seconds, then press Ctrl-Alt-F7
or
Log out then log back in (to do this without a mouse: < Alt-F1, Left, Up, Enter, Alt-L > or < Power button, Alt-L > or < Ctrl-Alt-Backspace > )

The first option may not always work and you will be forced to use the second

---

### Post by Robynsveil on 2008-02-06
Hi,
I started a separate thread on the subject when I should have just posted here, so anyway, here goes.

First off, I'm pretty sure I've read every thread on this forum on the subject, and inevitably bogged down at some stage. First I followed [this thread]("http://ubuntuforums.org/showthread.php?t=631881&highlight=Wacom+Bamboo"), and then I followed [another thread]("http://ubuntuforums.org/showthread.php?p=3728548#post3728548") which conflicted somewhat with the first one. Finally, I found[ this thread]("http://http://ubuntuforums.org/showthread.php?t=687746&highlight=Wacom+Bamboo+NVidia") where I once again carefully followed the instructions, but ran hard aground at Step 8 of the [recommended tutorial]("http://ubuntuforums.org/showpost.php?p=4014004&postcount=32")... turns out it was focused on the Bamboo Fun, whilst I have just the Bamboo. The author of the tutorial recommended to go to the [updated version of his tutorial]("http://ubuntuforums.org/showpost.php?p=4253232&postcount=133") which I did and promptly ran aground at the same step: 8.

In summary, what I did was the following (done in terminal, logged in as me, not root or su):
1._ uname -r_     .....     which gave me: **2.6.22-14-386**

2._ lsusb | grep -i wacom_   .....   which gave me: **Bus 001 Device 003: ID 056a:0065 Wacom Co., Ltd **

3.created the wacom folder and cded into it

4.sudo apt-get install build-essential x11proto-core-dev libxau-dev libxdmcp-dev x11proto-input-dev x11proto-kb-dev xtrans-dev libx11-dev x11proto-xext-dev libxext-dev libxi-dev linux-libc-dev libc6-dev libncurses5-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev
...which gave me... **[this]("http://www.tightbytes.com/Stuff/Install_devs.txt")**

5.Downloaded and untarred 'cd linuxwacom-0.7.9-7/', then went into that folder

6.Here's where I ran into my first quandary. One guru said to:
> ./configure --enable-wacom

where another advised against the " --enable-wacom" argument, as it applied only to older wacom tablet, or so he claimed. Not sure which to believe, I went with issuing the argument, and the terminal output was **[this]("http://www.tightbytes.com/Stuff/Configure_Enable_Wacom.txt")**. If I've got my ducks in a row, wacom.o was going to be built. I then issued a "make" which produced **[this]("http://www.tightbytes.com/Stuff/Make_Wacom.txt")** and then the "sudo make install" produced **[this]("http://www.tightbytes.com/Stuff/Sudo_Make_Install_Wacom.txt")**.

7.Did this:
> 
cd ..
cp /etc/X11/xorg.conf .
gksudo gedit /etc/X11/xorg.conf


and here was the **[xorg.conf]("http://www.tightbytes.com/Stuff/Xorg_dot_conf.txt")** this produced. Thought I'd have a quick look in the /dev/input folder: there is no wacom folder or file. Might there be an issue here?

Anyway, I did all the find (although there was nothing to find) and replace tasks, then 
> cp /lib/modules/2.6.22-14-generic/kernel/drivers/input/tablet/wacom.ko .
and 
> sudo cp linuxwacom-0.7.9-7/src/2.6.22/wacom.ko /lib/modules/2.6.22-14-generic/kernel/drivers/input/tablet/wacom.ko
gave me no back-chat, nor did:
> sudo depmod -e
...so I should assume that I've got an installed tablet.

I don't.

I've got [IMG]http://www.tightbytes.com/images/ubuntu/NoWacom.jpg[/IMG]

...so, what am I missing?

Thanks so much for your help on this - it's driving me up a tree...

---

### Post by cb_rex on 2008-02-06
@ neko18

Big thanks, everything works correctly now here's the files you asked for, if theres anything I can do to help others just let me know.

---

### Post by McAviti on 2008-02-06
SOLVED FOR ME! 

This was a more generic compile mistake: I wanted to install the driver for both the -generic and -386 kernels. When recompiling again for the -386 version, i just deleted the config and Makefile in the driver directory. This was simply not sufficient. I followed the instructions again as a whole (deleting the wacom2 directory in front) -- and voilá --> works.

Thank you once again!

---

Neko18 -- thanx a lot for your help! 

I followed your instructions, unfortunately I seemed to do something wrong, since the tablet is still dead. A symptom is definitely that I have no /dev/input/wacom device - which I had that day before.

From the xorg log file:
```
kdi@rigatoni:/var/log$ fgrep wacom Xorg.0.log
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
(**) pad device is /dev/input/wacom
(**) cursor device is /dev/input/wacom
(**) eraser device is /dev/input/wacom
(**) stylus device is /dev/input/wacom
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
Error opening /dev/input/wacom : Success
```

So the correct version ((II) Wacom driver level: 47-0.7.9-7 $) of the shared object seems to be loaded.

The kernel module seems to be in place as well
```
-rw-r--r-- 1 root root 234684 2008-02-07 00:09 /lib/modules/2.6.22-14-386/kernel/drivers/input/tablet/wacom.ko
```

Maybe this line in the messages log tells the problem?
```
messages:Feb  7 00:36:51 localhost kernel: [   41.550128] wacom: disagrees about version of symbol struct_module
```
Maybe I have a problem with my kernel header files?  But ```
sudo depmod -e
``` gives no error whatsoever.

Any clue what I've done wrong?

---

### Post by neko18 on 2008-02-06
**@Robynsveil**

Plug in your tablet, log out, log back in, then send the output of these commands:
```
ls -l /dev/input
ls -l /lib/modules
```

When you're done with that, please do step 3, 13, and 14 of [http://ubuntuforums.org/showpost.php?p=4253232&postcount=133](http://ubuntuforums.org/showpost.php?p=4253232&postcount=133)

**@cb_rex**
Congrats on getting the tablet working

**@McAviti**
I'm using generic, so can you tell me how you did it for 386? A couple other people are using that as well, and I'm not sure what all the directories are for it. I also have no clue what to pass to ./configure to get it to compile for a certain architecture.

---

### Post by McAviti on 2008-02-06
> **neko18 said:**
> 
**@McAviti**
I'm using generic, so can you tell me how you did it for 386? A couple other people are using that as well, and I'm not sure what all the directories are for it. I also have no clue what to pass to ./configure to get it to compile for a certain architecture.

Your recipie can be applied as well -- just within the copy commands the 'generic" has to be replaced with "386". That's all. The compile environment finds the other correct paths for itself.

```
cp /lib/modules/2.6.22-14-386/kernel/drivers/input/tablet/wacom.ko .
sudo cp linuxwacom-0.7.9-7/src/2.6.22/wacom.ko /lib/modules/2.6.22-14-386/kernel/drivers/input/tablet/wacom.ko
```

Now I'll start to configure buttons, scrolling etc :)

---

### Post by neko18 on 2008-02-06
**@McAviti**
Thanks, I'll integrate that into the tutorial now.

---

### Post by Robynsveil on 2008-02-06
> **McAviti said:**
> Your recipie can be applied as well -- just within the copy commands the 'generic" has to be replaced with "386". That's all. The compile environment finds the other correct paths for itself.

```
cp /lib/modules/2.6.22-14-386/kernel/drivers/input/tablet/wacom.ko .
sudo cp linuxwacom-0.7.9-7/src/2.6.22/wacom.ko /lib/modules/2.6.22-14-386/kernel/drivers/input/tablet/wacom.ko
```

Now I'll start to configure buttons, scrolling etc :)
Amazing how minds across the globe can come to exactly the same conclusion / deduction at the same time (replacing "generic" with "386". That was precisely what I did, and now I've *finally* got my tablet working! Thanks to all who have posted!!!

---

### Post by ShelJ on 2008-02-06
Thanks so much, this fix works, although I'm afraid to turn off my computer, just incase  ...  :S

---

### Post by fktt on 2008-02-08
so many posts that i wont even bother reading them all right now.. @__@

the only problem is on the gimp side.. for some reason the 'pointer' crosshead is off.. well.. maybe the image will illustrate better what i mean:

[IMG]http://i27.tinypic.com/27zkncw.jpg[/IMG]

thus far ive only noticed it in the GIMP... T__T''

also as you can see, the space between the os cursor and the gimps crosshair is bigger the more to the downright corner of the screen you get..

---

### Post by McAviti on 2008-02-08
Do you have choosen "Window" in File/Preferences/Input Devies/Configure Extended Input Devices..."?
In that case i experience a similar behaviour. When changing to "Screen" crosshair and effect are on the same place.

---

### Post by neko18 on 2008-02-08
**@fktt**
You have Gimp configured incorrectly. Here's some info on configuring Gimp: [https://help.ubuntu.com/community/Wacom#head-929f7242507f9630c22bacd764264465a7a3f59e](https://help.ubuntu.com/community/Wacom#head-929f7242507f9630c22bacd764264465a7a3f59e)

---

### Post by supersonicdarky on 2008-02-08
I have the same problem as the people who had the tablet just work as a mouse. I tried the solution that was proposed and apparenly worked but not for me.

My architecture is amd64.
```
Linux fission 2.6.22-14-generic #1 SMP Thu Jan 31 23:33:13 UTC 2008 x86_64 GNU/Linux
```

walcomcpl outputs **wacomcpl: using TCLLIBPATH="[list  /usr/local/lib ]"** when run (windows pops up with no options whatsoever)

Please help me as I need the pressure sensitivity and eraser capabilities.

---

### Post by neko18 on 2008-02-09
**@supersonicdarky**

I need a little more detail. Does it work like a touchpad (have to press down to move the mouse) or does it work in relative mode (if you place the stylus in range in the upper left corner, pull it out of range, then place it in range in the bottom right corner, does it jump to the bottom right of the screen, or just stay in the same postion?)

The two files you sent me show that your system is configured correctly.

---

### Post by fktt on 2008-02-09
no, actually i already had all set up to screen,
this is my sisters computer and she has a bamboo one,
yet again that might be the reason for the problem?

I personally own a Graphire4 Classic witch works just fine,
though i use feisty she here has got gutsy installed.

---

### Post by supersonicdarky on 2008-02-09
> **neko18 said:**
> **@supersonicdarky**

I need a little more detail. Does it work like a touchpad (have to press down to move the mouse) or does it work in relative mode (if you place the stylus in range in the upper left corner, pull it out of range, then place it in range in the bottom right corner, does it jump to the bottom right of the screen, or just stay in the same postion?)

The two files you sent me show that your system is configured correctly.

I only press down to click. First button works as middle click, second as right click and eraser as the writing tip. It moves the mouse when the pen is not touching the pad. The corners of the pad are corners of the screen. When pen is moved out of range, then placed in a different area it jumps. The scroll/touchpad at the top works as well. The buttons don't.

---

### Post by neko18 on 2008-02-10
**@fktt**
Sorry for the assumption about the Gimp configuration. I'm not really sure what's wrong.

**@supersonicdarky**
Okay, I understand now. You're talking about the "<", ">", "FN1", and "FN2" buttons. Those can be configured with the `xsetwacom` command.

Syntax:
```
xsetwacom set pad Button<X> "core key <Combination>"
```

<X> should be replaced with a number 1 to 4 (inclusive).
1: <
2: FN1
3: >
4: FN2

<Combination> should be replaced with a key combination.

Examples:
```
# Set the "FN1" button to "control c" (usually copy)
xsetwacom set pad Button2 "core key control c"

# Set the "<" button to "-" (zoom out in Gimp)
xsetwacom set pad Button1 "core key -"

# Set the "FN2" button to "alt f1" (open main menu in Gnome)
xsetwacom set pad Button4 "core key alt f1"

# Make the ">" button automatically type "xsetwacom rocks"
xsetwacom set pad Button3 "core key x s e t w a c o m space r o c k s"

# Set "FN1" to double click
xsetwacom set pad Button2 "dblclick"
```

---

### Post by Robynsveil on 2008-02-10
> **fktt said:**
> no, actually i already had all set up to screen,
this is my sisters computer and she has a bamboo one,
yet again that might be the reason for the problem?
...

I've got exactly the same problem - there appears to be an offset between the draw-point in The GIMP and the cursor. There is another thread that entertains the notion that one needs to modify some .c file and compile it:
[URL="http://ubuntuforums.org/showthread.php?p=4303631#post4303631"]
http://ubuntuforums.org/showthread.php?p=4303631#post4303631[/URL]
like on page 22 of that thread, but the how-to-do-it is a bit above and beyond me...

---

### Post by supersonicdarky on 2008-02-10
**@ neko18:**

```
kernel@fission:~$ xsetwacom set pad Button2 "core key control c"
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device 'pad'

```

also the keys were just one part of the problem. the tablet still only functions as a mouse (no pressure sensitivity or eraser (eraser is same as the writing tip))

for now, i just use vmware workstation with xp, hook it up to that and it works fine. but gimp functionality would be prefered

---

### Post by neko18 on 2008-02-10
**@Robynsveil (and @fktt)**
Thanks for the pointer there. I'll try out the patch on my computer and see if it does any good and if it does I'll give you guys modified (and easier) instructions to fix yours. I'll get back to you on that in a few days.

**@supersonicdarky**
Can you send me the output of 
```
cat /proc/bus/input/devices
```
By the way, did your draw your avatar? It's really cool.

---

### Post by Robynsveil on 2008-02-11
> **neko18 said:**
> **@Robynsveil (and @fktt)**
Thanks for the pointer there. I'll try out the patch on my computer and see if it does any good and if it does I'll give you guys modified (and easier) instructions to fix yours. I'll get back to you on that in a few days...
Neko, you're a legend! Thanks for looking into this, and looking forward to your findings...

---

### Post by gulincho on 2008-02-11
Hi!

my

2.
```
lsusb | grep -i wacom
```

say 056a:0018 but work fine anyway !!!

notebooks HP530 Core Duo & Lenovo 3000 C200

thanks you!!!

---

### Post by fktt on 2008-02-11
> **Robynsveil said:**
> Neko, you're a legend! Thanks for looking into this, and looking forward to your findings... +1 \\:D/ thanks, indeed! :)

---

### Post by oldsoundguy on 2008-02-11
been following this as I have an Intouos 3 - 9 1/2 x 12 and it has a lot of the same issues.  Using the synaptic install yields a pen that works but BARELY ..  have to really MOVE it to get the cursor to move and the button works and then doesn't work ..  forget trying to use the mouse if you use the "built in" drivers! And the AIRBRUSH?

I went to the development site and downloaded the page after page after page of instructions and codes.  I AM going to try and get it to work, but just as a project for something to do.  I can always migrate the pad back to a Windows box and still use GIMP on IT if need be. (my MS box has CS2 on it also!)

It looks to be that the Wacom folks have good intentions, but not the resources to actually get the open source up and running and have it be USER FRIENDLY.

It is amazing how many still feel that in order to do something in open source, you have to treat everyone like they are programmers in order to be taken seriously.  Time for a lot of them to realize that the majority of computer owners want to be computer USERS  and care very little about programming and entering line after line of code to get something to function and going into files and editing to accomplish that.  

The contributions on this thread are amazing and great, and many have done enormous amounts of research and are to be commended for such .. but time to SIMPLIFY (not the posters .. the code writers!) 

BUT a thought: MAYBE attempting to use a wrapper package MIGHT accomplish the goal .. who knows ....

If a photographer (even an advanced amateur) or an artist can not get their editing/printing  set up working on Linux, he/she will STAY on WinDOZE or (too high priced) MAC or at least keep a box in the corner for their editing and printing (something I have been forced to do).

---

### Post by wgw on 2008-02-11
Many thanks for this guide -- it was the only solution for me, with the bamboo -no-fun (mine shows Bus 003 Device 003: ID 056a:0065 Wacom Co., Ltd  when I do lsusb | grep -i wacom). 

I used this guide a few weeks back, and it worked first go. I reused it again when the kernel upgrade clobbered my previous install. Thanks as well for that tip; I was at a loss to know why my bamboo had stopped working when everything was fine before -- I will keep a sharper eye on kernel upgrades from now on.

One remark: step 13 hangs for me (unlucky number!) because I do not have a /lib/modules/2.6.22-14-38 directory. I just skipped it. 

> **neko18 said:**
> 

13.
```
cp /lib/modules/2.6.22-14-generic/kernel/drivers/input/tablet/wacom.ko .
sudo cp linuxwacom-0.7.9-7/src/2.6.22/wacom.ko /lib/modules/2.6.22-14-generic/kernel/drivers/input/tablet/wacom.ko
cp /lib/modules/2.6.22-14-386/kernel/drivers/input/tablet/wacom.ko wacom.ko-386
sudo cp linuxwacom-0.7.9-7/src/2.6.22/wacom.ko /lib/modules/2.6.22-14-386/kernel/drivers/input/tablet/wacom.ko
```


I also have a server kernel on the same machine, so I should probably adapt #13 accordingly. 

So, everything works (even wacomcpl !), thanks to all your good work. :popcorn:

---

### Post by neko18 on 2008-02-11
**@Robynsveil and @fktt**
Thanks :)

**@gulincho**
I'm glad I could help

**@oldsoundguy**
Did you follow my instructions on your tablet or did you try some other way? (there's a link in my signature to my instructions)

This thread isn't for complaining about your tablet not working. It's for getting your tablet working.

**@wgw**
Did it actually hang (terminal wouldn't bring you back to the `user@computer$` prompt) on that step or did it simply give an error?

I'm glad you got your tablet working!

---

### Post by oldsoundguy on 2008-02-11
I get to the xorg.conf point and my xorg is completely different an has NONE of the entries mentioned to change .. LOTS of stuff for failsafe for my monitor.

---

### Post by oldsoundguy on 2008-02-11
this is what I get:

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   
Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:0:10:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"NEC"
	Modelname	"NEC MultiSync LCD1810X"
	Horizsync	31.0-82.0
	Vertrefresh	56.0-85.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	Option		"AddARGBGLXVisuals"	"True"
	SubSection "Display"
		Depth	24
		Virtual	1600	1200
		Modes		"1024x768@85"	"1024x768@75"	"832x624@75"	"1024x768@70"	"800x600@60"	"1024x768@60"	"800x600@85"	"1152x864@75"	"800x600@75"	"1280x1024@75"	"800x600@72"	"1280x960@60"	"800x600@56"	"1280x1024@60"	"640x480@85"	"1280x960@75"	"640x480@75"	"1400x1050@60"	"640x480@72"	"1400x1050@75"	"640x480@60"	"1600x1200@65"	"1600x1200@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "device" #                
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:0:10:0"
	Driver		"nvidia"
	Screen	1
EndSection
Section "screen" #                
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	Option		"AddARGBGLXVisuals"	"True"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection
Section "monitor" #                
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

---

### Post by neko18 on 2008-02-11
**@oldsoundguy**
Thanks for posting your xorg.conf, that helps a lot.

Here are some modified instructions for you:

1. Open a terminal and run these commands:
```
cd wacom
cp /etc/X11/xorg.conf .
sudo cp /etc/X11/xorg.conf /home
gksudo gedit /etc/X11/xorg.conf
```

2. In gedit, replace the entire file with the following (Ctrl-A, Delete, then paste this in):
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#
Section "Files"
EndSection

Section "Module"
	Load "glx"
	Load "v4l"
EndSection

Section "InputDevice"
	Identifier "Generic Keyboard"
	Driver "kbd"
	Option "CoreKeyboard"
	Option "XkbRules" "xorg"
	Option "XkbModel" "pc105"
	Option "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "CorePointer"
	Option "Device" "/dev/input/mice"
	Option "Protocol" "ImPS/2"
	Option "ZAxisMapping" "4 5"
	Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection

Section "Device"
	Identifier "Failsafe Device"
	Boardname "vesa"
	Busid "PCI:0:10:0"
	Driver "nvidia"
	Screen 0
EndSection

Section "Monitor"
	Identifier "Failsafe Monitor"
	Vendorname "NEC"
	Modelname "NEC MultiSync LCD1810X"
	Horizsync 31.0-82.0
	Vertrefresh 56.0-85.0
	modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	modeline "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
	modeline "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
	modeline "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
	modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
	modeline "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
	modeline "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
	modeline "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
	modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	modeline "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
	modeline "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
	modeline "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
	modeline "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
	modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	modeline "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
	modeline "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
	modeline "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	modeline "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	modeline "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
	modeline "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	modeline "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
	modeline "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	modeline "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma 1.0
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device "Failsafe Device"
	Monitor "Failsafe Monitor"
	Defaultdepth 24
	Option "AddARGBGLXVisuals" "True"
	SubSection "Display"
		Depth 24
		Virtual 1600 1200
		Modes "1024x768@85" "1024x768@75" "832x624@75" "1024x768@70" "800x600@60" "1024x768@60" "800x600@85" "1152x864@75" "800x600@75" "1280x1024@75" "800x600@72" "1280x960@60" "800x600@56" "1280x1024@60" "640x480@85" "1280x960@75" "640x480@75" "1400x1050@60" "640x480@72" "1400x1050@75" "640x480@60" "1600x1200@65" "1600x1200@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier "Default Layout"
	screen 0 "Default Screen" 0 0
	Inputdevice "Generic Keyboard"
	Inputdevice "Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"		"SendCoreEvents"
EndSection

Section "device" #
	Identifier "device1"
	Boardname "vesa"
	Busid "PCI:0:10:0"
	Driver "nvidia"
	Screen 1
EndSection

Section "screen" #
	Identifier "screen1"
	Device "device1"
	Defaultdepth 24
	Monitor "monitor1"
	Option "AddARGBGLXVisuals" "True"
	SubSection "Display"
		Depth 24
		Modes "640x480@60"
	EndSubSection
EndSection

Section "monitor" #
	Identifier "monitor1"
	Vendorname "Plug 'n' Play"
	Modelname "Plug 'n' Play"
	modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma 1.0
EndSection

Section "ServerFlags"
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection
```

3. Continue with steps 12, 13, 14, and 15

4. Write this on a piece of paper or print it:
> If the computer does not work correctly after rebooting, press Ctrl-Alt-Backspace quickly followed by Ctrl-Alt-Delete, then boot into recovery mode and run these commands:
```
cp /home/xorg.conf /etc/X11/xorg.conf
reboot
```

To boot into recovery mode, press the escape/esc key when you see "Loading GRUB", use the arrow keys to select the item with "(recovery mode)" after it, then press enter

5. Reboot your computer

---

### Post by oldsoundguy on 2008-02-11
this line yields a "No such file or directory" comment line

cp /lib/modules/2.6.22-14-386/kernel/drivers/input/tablet/wacom.ko wacom.ko-386

The re write of the xorg file was what I assumed would be THAT answer and your reply verified same .. thanks thus far.

---

### Post by neko18 on 2008-02-11
**@oldsoundguy**
The "No such file or directory" is expected for many people, so it's nothing to worry about. I'll edit the guide and make a note about that.

---

### Post by oldsoundguy on 2008-02-11
the line:
sudo cp linuxwacom-0.7.9-7/src/2.6.22/wacom.ko /lib/modules/2.6.22-14-386/kernel/drivers/input/tablet/wacom.ko

gets a "cannot create regular file"

---

### Post by supersonicdarky on 2008-02-11
here you go

```
kernel@fission:~$ cat /proc/bus/input/devices
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=04d9 Product=1203 Version=0111
N: Name="HID 04d9:1203"
P: Phys=usb-0000:00:13.3-2/input0
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=120003
B: KEY=1000000000007 ff800000000007ff febeffdff3cfffff fffffffffffffffe
B: LED=7

I: Bus=0003 Vendor=04d9 Product=1203 Version=0111
N: Name="HID 04d9:1203"
P: Phys=usb-0000:00:13.3-2/input1
S: Sysfs=/class/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=39fad941d101 1e000000000000 0

I: Bus=0003 Vendor=045e Product=0040 Version=0110
N: Name="Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)"
P: Phys=usb-0000:00:13.0-2/input0
S: Sysfs=/class/input/input4
U: Uniq=
H: Handlers=mouse1 event4 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=103

I: Bus=0003 Vendor=056a Product=0065 Version=0108
N: Name="Wacom Bamboo"
P: Phys=
S: Sysfs=/class/input/input5
U: Uniq=
H: Handlers=mouse2 event5 
B: EV=1f
B: KEY=1c63 70033 0 0 0 0
B: REL=100
B: ABS=10003000103
B: MSC=1

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=button_power/button/input0
S: Sysfs=/class/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/class/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=3
B: KEY=10000000000000 0

kernel@fission:~$ 

```
btw, no I didn't draw the avy ;(

---

### Post by oldsoundguy on 2008-02-11
re-booted just fine, but the pen still has a problem .. movement has to be extremely exaggerated in order to move the cursor and there is still NO MOUSE or Air Brush.  So it is exactly the same as it was when I first started (although the sensitivity of the click button has increased slightly.)  No way to adjust the pen sensitivity with keystrokes, either. Only linking it to GIMP and choosing brushes would be the answer there.

This is what I meant when I posted the comments originally.  I have some knowledge of the system and of computers, but the average computer USER is not looking for a lesson in programming.  Fine for ME, but not for them.  A better way has to be worked on if Ubuntu or any other Linux build is to attract the artist and photographer.

You have spent a LOT of time and effort on this for really no reward other than satisfaction. For that I thank you and I thank you for your individual investment of time on my attempt.

---

### Post by neko18 on 2008-02-11
**@supersonicdarky** and **@oldsoundguy**
Please post the output of these commands:
```
xidump -l
xsetwacom list dev
ls -l /dev/input
```

**@supersonicdarky**
I don't see anything wrong with that output. I'll think about yours and get back to you if I have any ideas.

**@oldsoundguy**
It is against Ubuntu's policy to include development/unstable software in their distribution. If you would like to try to convince them otherwise, you can file a bug report/feature request at [https://bugs.launchpad.net/ubuntu/+source/wacom-tools](https://bugs.launchpad.net/ubuntu/+source/wacom-tools) . The developers do not read the forums, so there is no use discussing that here.

Satisfaction is enough of a reward for me, but you're ruining it by complaining.

**@Robynsveil** and **@fktt**
I tried to get that patch working, but I couldn't figure out where to put it. I think it may be for an older version of Linux Wacom.

**@fktt**
Would you mind trying your tablet out in `gsumi`? To install:
```
sudo apt-get install gsumi -y
```

To run:
```
gsumi
```

Make sure you configure your tablet with File>Input Dialog (and remember to hit the Save button).

---

### Post by oldsoundguy on 2008-02-12
first off not complaining.  I KNOW things sometimes do not work right out of the box.

 xidump -l
Configured Mouse               disabled
Generic Keyboard               keyboard

xsetwacom list dev
(nothing shows .. went back to prompt)

 ls -l /dev/input
total 0
drwxr-xr-x 2 root root     80 2008-02-11 19:30 by-id      (in blue)
drwxr-xr-x 2 root root    160 2008-02-11 19:30 by-path      "
crw-rw---- 1 root root 13, 64 2008-02-11 19:29 event0  (in yellow on black)
crw-rw---- 1 root root 13, 65 2008-02-11 19:29 event1       "
crw-rw---- 1 root root 13, 66 2008-02-11 19:29 event2       "
crw-rw---- 1 root root 13, 67 2008-02-11 19:29 event3       "
crw-rw---- 1 root root 13, 68 2008-02-11 19:29 event4       "
crw-rw---- 1 root root 13, 69 2008-02-11 19:29 event5       "
crw-rw---- 1 root root 13, 70 2008-02-11 19:29 event6       "
crw-rw---- 1 root root 13, 71 2008-02-11 19:30 event7       "
crw-rw---- 1 root root 13, 63 2008-02-11 19:29 mice          "
crw-rw---- 1 root root 13, 32 2008-02-11 19:29 mouse0     "
crw-rw---- 1 root root 13, 33 2008-02-11 19:29 mouse1     "
crw-rw---- 1 root root 13, 34 2008-02-11 19:30 mouse2     "
lrwxrwxrwx 1 root root      6 2008-02-11 19:30 wacom -> event7 (the word wacom appears in blue/green and the phase event7 is yellow on black)

---

### Post by oldsoundguy on 2008-02-12
OK .. here is what works and what does not.

Pen:
works but the SPEED is way slow and it takes covering a large distance to move the cursor a few inches.
Eraser shows.
Click button .. works .... sometimes .. will not work on a radio button or an "x out"

Mouse:
will not move cursor at all.
main left and right buttons and scroll wheel work.
far left and right buttons are do nothing  unless they are for GIMP only

---

### Post by oldsoundguy on 2008-02-12
bump

---

### Post by Robynsveil on 2008-02-12
> **neko18 said:**
> 
**@Robynsveil** and **@fktt**
I tried to get that patch working, but I couldn't figure out where to put it. I think it may be for an older version of Linux Wacom.


See [URL="http://ubuntuforums.org/showthread.php?t=25151&page=27"]
http://ubuntuforums.org/showthread.php?t=25151&page=27[/URL] for my blow-by-blow on what I've done so far. Essentially, I replaced:
```
totalWidth += screenInfo.screens[i]->width;
```
with
```
totalWidth += screenInfo.screens[priv->currentScreen]->width;
```

in two places in the xf86WcmSetScreen function:

```

static void xf86WcmSetScreen(LocalDevicePtr local, int *value0, int *value1)
{
	WacomDevicePtr priv = (WacomDevicePtr) local->private;
	int screenToSet = 0;
	int totalWidth = 0, maxHeight = 0, leftPadding = 0;
	int i, x, y, v0 = *value0, v1 = *value1;
	double sizeX = priv->bottomX - priv->topX - 2*priv->tvoffsetX;
	double sizeY = priv->bottomY - priv->topY - 2*priv->tvoffsetY;

	DBG(6, priv->debugLevel, ErrorF("xf86WcmSetScreen "
		"v0=%d v1=%d\n", *value0, *value1));

	if (!(local->flags & (XI86_ALWAYS_CORE | XI86_CORE_POINTER))) return;

	if (!(priv->flags & ABSOLUTE_FLAG))
	{
#if defined WCM_XFREE86 || GET_ABI_MAJOR(ABI_XINPUT_VERSION) == 0
		priv->currentScreen = miPointerCurrentScreen()->myNum;
#else
		priv->currentScreen = miPointerGetScreen(local->dev)->myNum;
#endif
		for (i = 0; i < priv->numScreen; i++)
[B][COLOR="Red"]/*... An effort of resolve the cursor-drawpoint offset...
	   from AlumaSqrl in Ubuntuforum post:
	
			totalWidth += screenInfo.screens[i]->width;
...*/
			totalWidth += screenInfo.screens[priv->currentScreen]->width;
/*... end mod  ...*/[/COLOR][/B]
		maxHeight = screenInfo.screens[priv->currentScreen]->height;
		priv->factorX = totalWidth / sizeX;
		priv->factorY = maxHeight / sizeY;
		DBG(10, priv->debugLevel, ErrorF(
			"xf86WcmSetScreen current=%d ToSet=%d\n", 
			priv->currentScreen, screenToSet));
		return;
	}

	if (priv->twinview == TV_NONE)
	{
		v0 = v0 > priv->bottomX ? priv->bottomX - priv->topX :
			v0 < priv->topX ? 0 : v0 - priv->topX;
		v1 = v1 > priv->bottomY ? priv->bottomY - priv->topY :
			v1 < priv->topY ? 0 : v1 - priv->topY;
	}

	/* set factorX and factorY for single screen setup since
	 * Top X Y and Bottom X Y can be changed while driver is running
	 */
	if (screenInfo.numScreens == 1 || !priv->common->wcmMMonitor)
	{
		if (priv->twinview != TV_NONE)
		{
			if (priv->screen_no == -1)
			{
				if (priv->twinview == TV_LEFT_RIGHT)
				{
					if (v0 > priv->bottomX - priv->tvoffsetX && v0 <= priv->bottomX)
						priv->currentScreen = 1;
					if (v0 > priv->topX && v0 <= priv->topX + priv->tvoffsetX)
						priv->currentScreen = 0;
				}
				if (priv->twinview == TV_ABOVE_BELOW)
				{
					if (v1 > priv->bottomY - priv->tvoffsetY && v1 <= priv->bottomY)
						priv->currentScreen = 1;
					if (v1 > priv->topY && v1 <= priv->topY + priv->tvoffsetY)
						priv->currentScreen = 0;
				}
			}
			else
				priv->currentScreen = priv->screen_no;
			priv->factorX = priv->tvResolution[2*priv->currentScreen] / sizeX;
			priv->factorY = priv->tvResolution[2*priv->currentScreen+1] / sizeY;
		}
		else
		{
			/* tool on the tablet when driver starts */
#if defined WCM_XFREE86 || GET_ABI_MAJOR(ABI_XINPUT_VERSION) == 0
			if (miPointerCurrentScreen())
				priv->currentScreen = miPointerCurrentScreen()->myNum;
#else
			if (miPointerGetScreen(local->dev))
				priv->currentScreen = miPointerGetScreen(local->dev)->myNum;
#endif
			priv->factorX = screenInfo.screens[priv->currentScreen]->width / sizeX;
			priv->factorY = screenInfo.screens[priv->currentScreen]->height / sizeY;
		}
		return;
	}

	if (priv->screen_no == -1)
	{
		for (i = 0; i < priv->numScreen; i++)
		{
	[COLOR="Red"][B]		/* totalWidth += screenInfo.screens[i]->width; */
			totalWidth += screenInfo.screens[priv->currentScreen]->width;
	[/B][/COLOR]		if (maxHeight < screenInfo.screens[i]->height)
				maxHeight = screenInfo.screens[i]->height;
		}
		for (i = 0; i < priv->numScreen; i++)
		{
			if (v0 * totalWidth <= (leftPadding + 
				screenInfo.screens[i]->width) * sizeX)
			{
				screenToSet = i;
				break;
			}
			leftPadding += screenInfo.screens[i]->width;
		}
	}
	else 
	{
		screenToSet = priv->screen_no;
		totalWidth = screenInfo.screens[screenToSet]->width;
		maxHeight = screenInfo.screens[screenToSet]->height;
	}
	priv->factorX = totalWidth/sizeX;
	priv->factorY = maxHeight/sizeY;
	x = (v0 - sizeX * leftPadding / totalWidth) * priv->factorX + 0.5;
	y = v1 * priv->factorY + 0.5;
		
	if (x >= screenInfo.screens[screenToSet]->width)
		x = screenInfo.screens[screenToSet]->width - 1;
	if (y >= screenInfo.screens[screenToSet]->height)
		y = screenInfo.screens[screenToSet]->height - 1;

	xf86XInputSetScreen(local, screenToSet, x, y);
	DBG(10, priv->debugLevel, ErrorF("xf86WcmSetScreen"
		" current=%d ToSet=%d\n", 
		priv->currentScreen, screenToSet));
	priv->currentScreen = screenToSet;
}


```
...and rebuilt. No change in behaviour--the offset is still there.
Quick question: do I need to clear some cache or something I need to clear in order to prevent old code from being recompiled?
BTW, the path to my wcmCommon.c file is:
/home/robyn/bamboo/linuxwacom-0.7.9-4/src/xdrv/

---

### Post by neko18 on 2008-02-12
**@oldsoundguy**
I don't see anything wrong with those outputs. What's the output of
```
dmesg | grep -i wacom
```

**@supersonicdarky**
Also post the output of
```
dmesg | grep -i wacom
```

**@Robynsveil**
Yes, you may be correct about a cache. Try running ```
make clean
``` before ```
make
```.

I wish I could help more with the offset issue, but it's difficult since I don't experience the issue myself.

---

### Post by oldsoundguy on 2008-02-13
dmesg | grep -i wacom
[   67.639775] usbcore: registered new interface driver wacom
[   67.639956] /home/dave/wacom/linuxwacom-0.7.9-7/src/2.6.22/wacom_sys.c: v1.46-pc0.2:USB Wacom Graphire and Wacom Intuos tablet driver
[  122.541642] input: Wacom Intuos3 9x12 as /class/input/input7

re tested everything.  Same results as above post.

Is there a utility now installed to make "tweaks and adjustments"?  That seems to be what is needed for the pen.  But the mouse not being able to move the cursor at all is very strange!

---

### Post by oldsoundguy on 2008-02-13
OH, and I plugged the pad back into the Windows box from whence it came and ALL functions work as they should, so it is not the pen or the mouse or the pad.

---

### Post by oldsoundguy on 2008-02-13
bump another day

---

### Post by oldsoundguy on 2008-02-13
still trying to get this to work.

---

### Post by neko18 on 2008-02-13
**@oldsoundguy**
The `dmesg` output looks fine.

Actually, a "tweaks and adjustments" program would not work at this point. Your tablet is being registered as a mouse (normal input device) rather than a tablet (extended input device). The `xsetwacom list dev` command would have listed 4 devices (pad, eraser, cursor, stylus) if the tablet had registered correctly.

This is also the reason the mouse isn't working. Either the Linux kernel or the Wacom driver are not correctly detecting the "proximity" (whether or not the mouse/pen is in range) aspect of the tablet.

Try these:
```
mkdir wacom # ignore the error if this yields one
cd wacom
wget 'http://git.debian.org/?p=users/ron/wacom-tools.git;a=blob_plain;f=debian/xserver-xorg-input-wacom.udev;hb=master' -O wacom.udev
cp /etc/udev/rules.d/50-xserver-xorg-input-wacom.rules wacom.udev.backup
sudo cp wacom.udev /etc/udev/rules.d/50-xserver-xorg-input-wacom.rules
```
Now log out then log back in.

---

### Post by oldsoundguy on 2008-02-13
results:
 mkdir wacom # ignore the error if this yields one
mkdir: cannot create directory `wacom': File exists

But, since it already existed, I did the rest as the comment stated ..


TAHHHHDAAAHH!!  IT NOW WORKS!

Have read elsewhere that the "tilt" does not work yet and they are working on that.  But it is now USABLE and very reasonably so.

Thank you very much!

I have NO CLUE as to what we did and I do hope that the next time around they have it ready to install without the hassle.

I sure would have had a really hard time if I had been a total noob to the system.

---

### Post by sentientd on 2008-02-13
I used the How To neko18 posted on page 4 of this thread.

I had some problems with step 12 that I think were similar to what ThomasWii ran into:

> **ThomasWii said:**
> Thanks for your reply, but i have an error, when i put in ```
sudo cp linuxwacom-0.7.9-4/src/2.6.22/wacom.ko /lib/modules/2.6.22-14-generic/kernel/drivers/input/tablet/wacom.ko
```it comes up with ```
cp: cannot stat `linuxwacom-0.7.9-4/src/2.6.22/wacom.ko': No such file or directory

``` Thanks in advance,

Thomas

So  I tried the following recommendation:

> **neko18 said:**
> A note to all: be absolutely sure you use version 0.7.9-4 instead of 0.7.8-3. I tried 0.7.8-3 and it *will not work*.

**Edit:**
@ThomasWii: Yes, just a moment.

**Edit 2:**
@ThomasWii:
Attached. Download wacom.ko.gz to your desktop, then run the following commands:
```
cd ~/Desktop
gunzip wacom.ko.gz
sudo cp wacom.ko /lib/modules/2.6.22-14-generic/kernel/drivers/input/tablet/wacom.ko
```
Now continue with step 13

I also tried the following, but I think I already had tcl and tk:

> **em es said:**
> :-D it's quite simple. You put this in your terminal first of all:
```
sudo apt-get install tcl8.4 tcl8.4-dev tk8.4 tk8.4-dev
```
then you follow the howto up to the poit where you are about to put in```
./configure --enable-wacom
```
Just that instead of that you use```
./configure --enable-modver --enable-wacom -with-kernel=/lib/modules/2.6.22-14-generic/build
```


Here is my output after trying that

BUILD ENVIRONMENT:
architecture - i486-linux-gnu
linux kernel - yes 2.6.22
module versioning - yes -DCONFIG_MODVERSIONS -DMODVERSIONS -include /lib/modules/2.6.22-14-generic/build/include/linux/modversions.h
kernel source - yes /lib/modules/2.6.22-14-generic/build
Xorg SDK - yes /usr/include/xorg
XSERVER64 - no
dlloader - yes
XLib - yes /usr/lib
TCL - yes /usr/include/tcl8.4/
TK - yes /usr/include/tcl8.4/
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
tabletdev.o - no
wacom_drv.so - yes /usr/lib/xorg/modules/input 
wacom_drv.o - no

I've searched the synaptic package manager and I have these three things installed:
xserver-xorg-input-wacom
wacom-tools
wacom-kernel-source

I tried step 14 and then I got this: 

 cd: linuxwacom-0.7.9-4/prebuilt: No such file or directory

I actually got the wacom tablet for my birthday the day before yesterday and I installed it after a few difficulties it was working fine... I think I used the How To from page 4.

The problems seemed to start after I checked for and applied updates  this morning.

I thought I read that a few people had the same problem so they just used the How To again and that fixed it, but I'm having no luck. I've tried it several times. 

This is my first Wacom tablet and I've only just begun to learn to use Ubuntu. So far I've been loving it except for these Wacom difficulties.

I have the Wacom Bamboo Fun Medium: ID 056a:0018 Wacom Co., Ltd 

Anyone have any suggestions?

---

### Post by neko18 on 2008-02-13
**@oldsoundguy**
I'm really glad you got your tablet working! I'll definitely add the udev file to my instructions now.

If you're curious, what we did is replace X.org's tablet recognition file so that it would be able to load the correct driver for your tablet.

**@sentientd**
You were following the wrong guide. That one was really old. Here is a link to the new one (also linked to in my signature): [http://ubuntuforums.org/showpost.php?p=4253232&postcount=133](http://ubuntuforums.org/showpost.php?p=4253232&postcount=133)

Good luck getting your tablet working and happy birthday!

---

### Post by sentientd on 2008-02-13
> **neko18 said:**
> [B]

**@sentientd**
You were following the wrong guide. That one was really old. Here is a link to the new one (also linked to in my signature): [http://ubuntuforums.org/showpost.php?p=4253232&postcount=133](http://ubuntuforums.org/showpost.php?p=4253232&postcount=133)

Good luck getting your tablet working and happy birthday!

It works!! It works!!! ^_^

Thank you so very much for doing all of this!!!   And thanks for the happy birthday sentiments!  Your contributions here have really helped to make it a good one!  I want to tell you that I am so happy right now! :D

I really appreciate all the help and advice you've been giving everyone!

---

### Post by neko18 on 2008-02-13
**Everyone who hasn't gotten their tablet working yet**
Please follow the instructions on [http://ubuntuforums.org/showpost.php?p=4253232&postcount=133](http://ubuntuforums.org/showpost.php?p=4253232&postcount=133) again! I updated them with some new discoveries (thanks to oldsoundguy!) and they may just get your tablet working correctly.

**@sentientd**
I'm glad you got it working

---

### Post by cb_rex on 2008-02-14
Its a shame that every time theres new linuxheaders updates we have to go through the rigmarole of setting up our tablets again.  

Also, using the wacomcpl I've managed to map the tablet buttons <, >, FN1 and FN2 to the shortcuts I want but it forgets the settings every time I switch off my machine.  Does anyone know if theres anyway to make the wacomcpl permanently remember these settings for mapping the tablet buttons?

---

### Post by neko18 on 2008-02-14
**@cb_rex**
If you don't want to run through all the steps, just do this command (assuming you didn't delete the ~/wacom folder)
```
sudo cp wacom/linuxwacom-0.7.9-7/src/2.6.22/wacom.ko /lib/modules/2.6.22-14-generic/kernel/drivers/input/tablet/wacom.ko
```

To edit your buttons, run this:
```
gedit ~/.bashrc
```
Type in the `xsetwacom` commands that you want, save+quit, then run:
```
source ~/.bashrc
```
The second command just applies the changes you made in ~/.bashrc

---

### Post by Xfcn on 2008-02-14
> **neko18 said:**
> .
.
.
.
.


**There is a new guide**
Please go to the new, updated guide:
[http://ubuntuforums.org/showpost.php?p=4253232&postcount=133](http://ubuntuforums.org/showpost.php?p=4253232&postcount=133)

.
.
.
.

Please put these back. The new instructions fail on my AMD64 installation and these instructions always worked perfectly. I don't mind using an older version of the driver, I just want one that works.

*EDIT* Nevermind, I figured it out myself. I don't know why the older version works when the newer one doesn't, but it does. It really does beat me.

---

### Post by neko18 on 2008-02-14
**@Xfcn**
Sorry, I don't have an archive of the old instructions. Here are the differences though (as I remember them):

5. Change 0.7.9-7 to 0.7.9-4 in all three commands
13. Do this instead:
```
cp /lib/modules/2.6.22-14-generic/kernel/drivers/input/tablet/wacom.ko wacom.ko
sudo cp linuxwacom-0.7.9-4/src/2.6.22/wacom.ko /lib/modules/2.6.22-14-generic/kernel/drivers/input/tablet/wacom.ko
```
15. Change 0.7.9-7 to 0.7.9-4
16. Skip this step

Just wondering, what did you do to fix yours?

---

### Post by Xfcn on 2008-02-14
You got it, Ace. That's exactly what I did. I ignored all the 386 information and downloaded 0.7.9-4 instead. I can only guess that the newer instructions specifically reference 386 and the older ones are purely generic. Just at a guess.

---

### Post by neko18 on 2008-02-14
**@Xfcn**
It was probably the use of 0.7.9-4 that made the difference. In the new instructions I included both generic *and* 386. (Though I just recently updated them so they just install the driver to all available kernels.)

---

### Post by Robynsveil on 2008-02-16
> **neko18 said:**
> ...
**@Robynsveil** and **@fktt**
I tried to get that patch working, but I couldn't figure out where to put it. I think it may be for an older version of Linux Wacom.

I think a solution for the GIMP cursor/drawpoint offset issue has been found. My Bamboo now works appropriately. Please peruse this [thread]("http://ubuntuforums.org/showthread.php?t=696160") ... if a more detailed handholding is required, I'll try to put something together. In any event, everything now works! BTW, here is my xorg.conf:
```
# xorg.conf (xorg X Window System server configuration file)

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"USB"		"on"
	[COLOR="Red"][B]Option		"Mode"		"Absolute"
        Option		"PressCurve"	"50,0,100,50"
	Option		"Gimp"		"on"[/B][/COLOR]
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"USB"		"on"
	[COLOR="Red"][B]Option		"Mode"		"Absolute"
	Option		"Gimp"		"on"[/B][/COLOR]
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	[COLOR="Red"][B]Option		"Type"		"cursor"
	Option		"USB"		"on"[/B][/COLOR]
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV43 [GeForce 6600 GT]"
	Boardname	"NVIDIA GeForce FX (generic)"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

Section "Monitor"
	Identifier	"CM753"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV43 [GeForce 6600 GT]"
	Monitor		"CM753"
	DefaultDepth	24
	SubSection "Display"
	Modes		"1600x1280" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

---

### Post by fktt on 2008-02-16
hey, thanks! that looks pretty clear, will have to try it out! :)

---

### Post by ShelJ on 2008-02-17
It happened once again!!!  I installed updates and my tablet nolonger works again.  I tried reinstalling, like last time, three times but it did not work.

nm, got it figured you thanks.  Just like to add my frustration, to  cb_rex, at having to reinstall this every time I get security updates.

---

### Post by Prinssimikko on 2008-02-17
Hi!

Thanks for this unbelievable thread. With the guide I was able to install my Wacom Bamboo Fun Small for Linux Mint, but now i'm running Ubuntu Studio and for some reason i can't make it work. I assume the problem is with real time -kernel? does anyone have any clues?

Here is what i get after ./configure --enable-wacom 
- it doesnt seem right (too many no's!)

  BUILD ENVIRONMENT:
       architecture - i486-linux-gnu
       linux kernel - yes 
  module versioning - no 
      kernel source - no 
     XFree86 source - no 
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - no
           dlloader - yes
               XLib - yes /usr/lib
                TCL - yes /usr/include/tcl8.4
                 TK - yes /usr/include/tcl8.4
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
       wacom_drv.so - yes /usr/lib/xorg/modules/input 
        wacom_drv.o - no

---

### Post by tlevine on 2008-02-17
This doesn't work for me. I know step 13 said that errors are fine, but will it really work if there's no wacom.ko in my linuxwacom-0.7.9-7/src/2.6.22?

---

### Post by Prinssimikko on 2008-02-17
the problem with me is as well that there seems to be no wacom.ko -file. I actually now copied the wacom.ko file from my previous succesfull linux Mint install, and the installation seemed to go ok, but there is no response whatsoever from Bamboo.

---

### Post by tlevine on 2008-02-17
> **Prinssimikko said:**
> the problem with me is as well that there seems to be no wacom.ko -file. I actually now copied the wacom.ko file from my previous succesfull linux Mint install, and the installation seemed to go ok, but there is no response whatsoever from Bamboo.The whole point of compiling the module is that the module on vanilla install was the old one that didn't have support for Bamboo, so it's quite understandable that this would happen.

I had no errors in my installation after this step either.

---

### Post by supersonicdarky on 2008-02-17
```
kernel@fission:~$ dmesg | grep -i wacom
[   37.924555] input: Wacom Bamboo as /class/input/input5
[   37.926962] usbcore: registered new interface driver wacom
[   37.926969] /home/kernel/wacom2/linuxwacom-0.7.9-7/src/2.6.22/wacom_sys.c: v1.46-pc0.2:USB Wacom Graphire and Wacom Intuos tablet driver

```

---

### Post by neko18 on 2008-02-18
**@Prinssimikko**
You are correct about the `./configure --enable-wacom` output. It should be building a "wacom.o" file. Will you please send me the entire output of `./configure --enable-wacom`?

**@tlevine**
You appear to have the exact same issue as Prinssimikko. Please send me the output of
```
ls /lib/modules
```

**@supersonicdarky**
The output looks fine. I'll tell you if I get any other ideas.

---

### Post by tlevine on 2008-02-18
> **neko18 said:**
> **@Prinssimikko**
You are correct about the `./configure --enable-wacom` output. It should be building a "wacom.o" file. Will you please send me the entire output of `./configure --enable-wacom`?

**@tlevine**
You appear to have the exact same issue as Prinssimikko. Please send me the output of
```
ls /lib/modules
```

**@supersonicdarky**
The output looks fine. I'll tell you if I get any other ideas.
```
tlevine@tlevine-desktop:~$ ls /lib/modules
2.6.22-14-generic  2.6.22-14-rt
tlevine@tlevine-desktop:~$ uname -r
2.6.22-14-rt
```But the problem is that wacom.ko is not being built or
something.```
tlevine@tlevine-desktop:~/wacom/linuxwacom-0.7.9-7/src/2.6.22$ ls
Makefile  Makefile.in  wacom_sys.c  wacom_wac.h
```The output from my configure is attached. Here's the interesting part.```
checking for kernel source/headers... not found
***
*** WARNING:
*** Unable to guess kernel source directory
***   Looked at /lib/modules/2.6.22-14-rt/source, /lib/modules/2.6.22-14-rt/build,
***     /usr/src/linux, /usr/src/linux-2.6.22-14-rt, /usr/src/linux-2.4, and
***     /usr/src/linux-2.6
*** Kernel modules will not be built
***
```Oops! I installed the headers, and it works now. Thanks! Now to do something to make the cube rotate more easily...maybe I'll just go back to clicking the workspace switcher.

---

### Post by Prinssimikko on 2008-02-18
TLEVINE: how did you exactly install the headers??? I think i'm having similar problem...

---

### Post by tlevine on 2008-02-18
> **Prinssimikko said:**
> TLEVINE: how did you exactly install the headers??? I think i'm having similar problem...I did it in synaptic, but the command would be```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by Prinssimikko on 2008-02-18
oh. i did that, and this time installation went better. except for that "no wacom.ko file"-error...  after reboot, Bamboo doesnt work at all... but now my .configure... -output looks much better! (attached)

any other ideas?

---

### Post by Prinssimikko on 2008-02-18
there is this input if it's helpful:

lsusb | grep -i wacom:
Bus 005 Device 002: ID 056a:0017 Wacom Co., Ltd

nothing wrong with that...

and with "wacomclp" the editor(?) opens up, but there is nothing showing...


What is the easiest way to COMPLETELY uninstall and remove my previous attempts and try a clear install???

---

### Post by tlevine on 2008-02-18
> **Prinssimikko said:**
> there is this input if it's helpful:

lsusb | grep -i wacom:
Bus 005 Device 002: ID 056a:0017 Wacom Co., Ltd

nothing wrong with that...

and with "wacomclp" the editor(?) opens up, but there is nothing showing...


What is the easiest way to COMPLETELY uninstall and remove my previous attempts and try a clear install???I didn't uninstall anything; I figured the install would re-write anything from the previous install. I just ran make clean and then followed the guide again, ignoring steps like editing xorg.conf that didn't have to be redone. I've read that there's sometimes a make command that uninstalls.

---

### Post by Prinssimikko on 2008-02-18
Thanks!!!!!!!!!
it works now! i suppose "make clean" did it!!! after that the installation went just fine!

---

### Post by neko18 on 2008-02-19
**@Prinssimikko and @tlevine**
I'm glad you two got your tablets working. I'll add the kernel header install to my guide.

---

### Post by vpik01 on 2008-02-19
**neko18** - great post and guide. I am new this week to ubuntu and trying to get my thinkpad x41 tablet functioning.  I'v run through your guide (#133) twice to no avail... Going back to the beginning. I am not getting the correct output for step #2, the response I get is 
```
lsub | grep -i wacom
bash: lsub: command not found
```

Could this be preventing the rest of the steps from working properly? Thanks!

FIXED - After posting i found [another guide]("http://ubuntuforums.org/showthread.php?t=590747").  Following it I was able to get the stylus working and the 'double click' functionality as well.  Thanks anyway!

---

### Post by neko18 on 2008-02-19
**@vpik01**
The guide says `lsusb | grep -i wacom`, not `lsub | grep -i wacom` ;)

---

### Post by vpik01 on 2008-02-19
Ah the old fat-fingering... I didn't cut and paste directly from the terminal so I'm not sure if I made the mistake there or not. Either way its working now and I don't think I'll mess with it. 

Write, re-read, re-read, execute... :)

Thanks again!

---

### Post by similas on 2008-02-23
Hello all!

I am digging through the thread, but there is always basic setup. Does anybody has an idea how to switch between windowed and screen mode in gimp? Another way - how to bind to the key (scroll lock for example) function of sending or not sending core events to X by stylus device?

I have Bamboo One tablet and situation looks like this:
when I put "SendCoreEvents" to xorg.conf for stylus device, tablet works as an absolute mouse (tablet area = screen area)...
when I do not put "SendCoreEvents" statement - stylus is not moving the mouse pointer, but when I enter the Gimp, open new picture and put the mouse over the picture area, I can draw, and the picture area = tablet area (assuming I've set gimp to work in window mode)... 

What I want to set is a combination that would allow me to enter windowed mode when I am drawing, but quickly change to screen mode when I would like to do something else... Somebody has an idea how to do it?

Setting different behavior to stylus and eraser makes no point because Bamboo One has only stylus and no buttons...

---

### Post by ClaudioVC on 2008-02-23
Hello everybody!
I'm having troubles at the very beginning of the Guide:

"Get the necessary dependencies:

Code:

sudo apt-get install build-essential x11proto-core-dev libxau-dev libxdmcp-dev x11proto-input-dev x11proto-kb-dev xtrans-dev libx11-dev x11proto-xext-dev libxext-dev libxi-dev linux-libc-dev libc6-dev libncurses5-dev xserver-xorg-dev"

When I type this in a terminal it says that 

"the package x11proto-core-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package x11proto-core-dev has no installation candidate."

Can anybody help me?

---

### Post by oldsoundguy on 2008-02-23
Off chance you do not have the repository for the files listed in synaptic.  Double check that.

---

### Post by oldsoundguy on 2008-02-23
looking again at your post .. you are trying to install from the CD.  You need to read on how to set up your repositories HERE: [http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

---

### Post by madtownmike1 on 2008-02-23
It works for me on an old Satellite notebook, 1.5ghz celeron. Thanks for the step by step.

---

### Post by ClaudioVC on 2008-02-24
oldsoundguy, thanks a lot, I've solved that...it was really that silly repository thing :)

Now I've gone through all the guide, but I still can't get it to work....

The blue led now works fine, like it was "breathing", but it doesn't recognize the pen or the mouse.....the command "wacomcpl" opens up the pop-up window but the "Select the device list" is empty! I can't figure what the problem could be.... :-?

Thanks

---

### Post by oldsoundguy on 2008-02-24
this is the total picture and updated .. it worked for me using a Intuos 3 pad.  And it has taken him a lot of time and effort to compile it:

[http://ubuntuforums.org/showpost.php?p=4253232&postcount=133](http://ubuntuforums.org/showpost.php?p=4253232&postcount=133)

Tilt on the pen is still not operational on mine, nor are there any drivers for the airbrush YET.

It takes time and effort to install, but that is the way of hardware when it is migrated from either/or the PC or Mac systems into Linux.  At least Wacom is co-operating in this unlike so many other hardware manufacturers.

Once my photography lab stuff is all running Linux properly, I will TOTALLY blow out any Windows system on any of my computers.

---

### Post by ClaudioVC on 2008-02-24
I just followed the guide once again, and now it's working!
I had almost lost all hope in using my tablet with Ubuntu.
Thanks so much for this thread, you guys are amazing :)

---

### Post by neko18 on 2008-02-24
**@similas**
These commands should switch between sending or not sending core events:
```
xsetwacom set stylus CoreEvent
xsetwacom set eraser CoreEvent
xsetwacom set cursor CoreEvent
```

I don't think it's possible to switch between Screen and Window mode in Gimp, short of going through all the menus.

**@madtownmike1**
I'm glad it worked for you

**@ClaudioVC**
Congrats on getting your tablet working

**@oldsoundguy**
Thanks for helping out ClaudioVC

Tilt should be supported on your tablet. Does this command give you "x-tilt" and "y-tilt" readings?
```
xidump stylus
```

---

### Post by oldsoundguy on 2008-02-24
Yes it does, along with pressure readings.  I could not get it to work so it must be something mechanical or I am doing something wrong!! LOL

Will give it a shot again when I have something I want to edit. (at least I now know that the options are loaded.)

---

### Post by neko18 on 2008-02-24
**@oldsoundguy**

Try using the "Ink" tool in Gimp. It's between the "Airbrush" tool and the "Clone" tool and its default shortcut key is K.

Also, if you're willing to give it a try, Krita has tilt support.

---

### Post by rospo84 on 2008-02-27
when i give the command:
```
lsusb | grep -i wacom
```
doesn't appear nothing... :(:(have u got any ideas???
Sorry for my english

---

### Post by neko18 on 2008-02-27
**@rospo84**
You have to plug in your tablet before running that command. I'll note that in the guide.

---

### Post by rospo84 on 2008-02-27
the tablet is plugged in and i restarted the PC, too. But when i launch the command nothing happens...

---

### Post by neko18 on 2008-02-29
**@rospo84**
Sorry for my late response. What is the output of this command?
```
lsusb
```

---

### Post by rospo84 on 2008-03-04
> **neko18 said:**
> **@rospo84**
Sorry for my late response. What is the output of this command?
```
lsusb
```

Sorry for my late response, too:)
the output is nothing, i mean that don't appear nothing.

---

### Post by Kasa on 2008-03-04
Hello.
I have one little problem.
after typeing

```
wacomcpl
```

in the terminal the window opens with nothing on it other then "click this for help" which does nothing.
this is my first install, clean install.
never used my Wacom bamboo on it :?.

---

### Post by neko18 on 2008-03-05
**@rospo84**
Are you using a USB tablet? If you are using a serial tablet, I suggest just skipping that step.

**@Kasa**
If the tablet itself works, I suggest not worrying about `wacomcpl`.

---

### Post by rospo84 on 2008-03-06
it's very strange. because i installed this usb tablet (wacom bamboo fun ) on another pc desktop with ubuntu gutsy following this wiki everything went allright and the tablet perfectly work on the other desktop. The problem is on this desktop.

---

### Post by gulincho on 2008-03-11
Thank you very much NEKO18!!!

```
lsusb | grep -i wacom
```
Look for the part of that line in the form "056a:####" ("#" being 0-9 or a-f)
Make sure yours is listed here: "056a:0017", "056a:0065", "056a:0069"

this command in my laptop return "056a:0018",  but work perfectly to.

thanks egain

Lenovo 3000 C200 - Ubuntu 7.10 - Wacom Bamboo Fun Medium

---

### Post by neko18 on 2008-03-11
**@rospo84**
You seem to have a problem beyond the tablet driver itself. I suggest opening another thread in the hardware forum.

**@gulincho**
I'm glad you got your tablet working. I'll add your tablet ID to the list of working tablets.

---

### Post by tuxdrummer on 2008-03-21
I have got one problem the command "wacomcpl" is working but no device is showing and my Tablet isn't working either.
i did like in that how to. 

I'm using ubuntu 7.10
my tablet is a Bamboo no Fun

mabe someone can help me

---

### Post by Killer Cop on 2008-03-25
> **neko18 said:**
> 

1.
```
uname -r
```
Make sure the output has "2.6.22-14" in it.


And if it isn't?! What do I do then?

---

### Post by ShelJ on 2008-03-27
After giving up on getting this thing to work, consistently, for a couple of weeks, I upgraded to Hardy Heron yesterday and my tablet worked right away.

Thought y'd all like to know!!  :popcorn:

---

### Post by cpzeb1 on 2008-03-27
hi, im new to all this:confused::P i´ve followed the guide, but after finished it and rebooted my computer, it still doesn´t seem to find my bamboo drawing tablet:S any ideas about why and how i fix it?

---

### Post by DonQuichote on 2008-03-29
> **tuxdrummer said:**
> I have got one problem the command "wacomcpl" is working but no device is showing and my Tablet isn't working either.
i did like in that how to. 

I'm using ubuntu 7.10
my tablet is a Bamboo no Fun

mabe someone can help me

My tablet is a Bamboo One, but I had the same problem. For some reason, there was just no device /dev/input/wacom, so the Xserver could not reach it. However, the hardware seemed to be present when I typed lsusb.

In the original post on page 15 of this thread, it copies the wacom.ko module to /lib/modules... I think this is where it went wrong. After getting a directory listing of /lib/modules/<version>/kernel/drivers/tablet/ , I noticed that the wacom.ko file there was just too old to be just compiled. So I had to do this by hand. I guess we should take the error messages seriously after all. That is the only thing I did different, apart from getting the drivers a minor version later (linuxwacom-0.7.9-8.tar.bz2).

So, more specific, when you are in the directory where you called configure from:
```
sudo cp src/2.6.22/wacom.ko /lib/modules/2.6.22-14-generic/kernel/drivers/input/tablet/
```

Hope this helps! I am enjoying the tablet now!

:biggrin:

---

### Post by tuxdrummer on 2008-03-29
It really worked

thx

---

### Post by DavidFourer on 2008-03-30
Re: Wacom configuration GUI
wacom-tools and wacomcpl and tablet-apps
I'm trying to get my tablet configured.  Here's what I found.

tablet-apps looks good so far.  Info and download at [http://alexmac.cc/tablet-apps/](http://alexmac.cc/tablet-apps/)
It's not in universe or multiverse ???  Installed OK on my computer.
also mentioned here   [http://ubuntufs.wordpress.com/2007/02/25/gnome-graphics-tablet-apps/](http://ubuntufs.wordpress.com/2007/02/25/gnome-graphics-tablet-apps/)

wacomcpl info on linuxwacom
[http://linuxwacom.sourceforge.net/index.php/howto/wacomcpl](http://linuxwacom.sourceforge.net/index.php/howto/wacomcpl)  but where to get it???

The ubuntu repository has a package called wacom-tools:
> utilities for wacom tablets and other hid devices 
This package provides utilities to test and configure wacom graphics tablets.
You will need kernel modules built from the wacom-kernel-source package to
use them with such devices.  It also provides hotplug and udev scripts which
may be useful without these tools and (later) with the wacom support in the
mainline kernel packages as well (2.6.11 or later).
I installed this with synaptic but can't find the application to launch.

---

### Post by azanutta on 2008-04-01
> **cpzeb1 said:**
> hi, im new to all this:confused::P i´ve followed the guide, but after finished it and rebooted my computer, it still doesn´t seem to find my bamboo drawing tablet:S any ideas about why and how i fix it?

i've also this sort of problem... it works only if my pc starts with the table connected....

and more .... it seems that it looses all the configurations about the buttons, so every reboot i have to XSETWACOM any button again.... how annoing....
 any trick?!?
tnx gurus

---

### Post by Evan.chung on 2008-04-03
Seems I met a strange problem:

Thanks for this thread, all things installed successfully and my Bamboo Fun can work well.
But in GIMP or in other pen tool applications, the pen point can't match the mouse point, that sucks!
Who can help to this issue? UUUUU....
[IMG]http://widget.slide.com/rdr/1/1/1/W/19000000067a1c51/1/199/ilRUis5L6j_92moZIh9emETVCDPRstYj.jpg[/IMG]

---

### Post by neko18 on 2008-04-10
I'm very sorry I haven't been keeping up on this thread. I don't have time to look through all of the new posts, but I suggest that everyone just wait 2 more weeks then install Ubuntu 8.04. It has full support of the Wacom Bamboo series tablets.

---

### Post by arelis on 2008-04-24
> **neko18 said:**
> I'm very sorry I haven't been keeping up on this thread. I don't have time to look through all of the new posts, but I suggest that everyone just wait 2 more weeks then install Ubuntu 8.04. It has full support of the Wacom Bamboo series tablets.

Hardy's been released today. However, my Bamboo Fun isn't working out of the box. Would you create a new guide, please?

---

### Post by neko18 on 2008-04-24
I'll create a new guide as soon as I get my tablet working in 8.04/Hardy.

I'm not sure why it isn't working. 8.04 should have better hotplugging support, so the entries in xorg.conf shouldn't be needed. 8.04 also comes with the new development version of Linux Wacom, so Bamboo support should not be a problem.

If you (or anyone else) have any luck at all with your tablet, please tell me how you did it.

**Edit**
I now have my tablet working. I'm currently writing up how I got it working, and will post this in a new thread (and link to it) as soon as I am finished.

**Edit 2**
I posted the new thread. It is located at [http://ubuntuforums.org/showthread.php?p=4785779](http://ubuntuforums.org/showthread.php?p=4785779)

---

### Post by arelis on 2008-04-25
> **neko18 said:**
> I'll create a new guide as soon as I get my tablet working in 8.04/Hardy.

I'm not sure why it isn't working. 8.04 should have better hotplugging support, so the entries in xorg.conf shouldn't be needed. 8.04 also comes with the new development version of Linux Wacom, so Bamboo support should not be a problem.

If you (or anyone else) have any luck at all with your tablet, please tell me how you did it.

**Edit**
I now have my tablet working. I'm currently writing up how I got it working, and will post this in a new thread (and link to it) as soon as I am finished.

**Edit 2**
I posted the new thread. It is located at [http://ubuntuforums.org/showthread.php?p=4785779](http://ubuntuforums.org/showthread.php?p=4785779)

I got my tablet to work, too, using that guide.

---

### Post by waspinator on 2008-05-02
probably not the right place to ask this but whats the difference (besides the look, and the mouse) of the two bamboos? And which one works better under hardy?

Thanks

---

### Post by Stoodle on 2008-05-04
Hello everyone. I was following this guide and had no problems. I didn't update the driver but whatever. I rebooted and now I'm having a problem with graphics. It couldn't find what it needed or whatever for the graphics and then it stopped accepting any keyboard input. I don't think that it's accepting mouse input either. The way I'm posting is I went  into recovery mode, loaded up w3m, and found the post again in google. I don't think I got instructions for xorg.conf very well. How do I fix this graphics problem? Sorry for the wall of text, but I'm using nano which I've never used before.
:(
:confused:

---

### Post by BobtheBlueBerry on 2008-05-07
It didn't work for me.

---

### Post by oldsoundguy on 2008-05-07
bob, the Great Kweskin is not a contributor to the Ubuntu forums.  "it doesn't work" will not get you help.  WHAT doesn't work and what did you do?
You have to follow ALL of the steps as the instructions are NOT a menu in a Chinese restaurant where you pick what you want to do and if that doesn't get done go ahead and skip to the next item or skip around. It has to be done in the order shown as each item of the install builds on the previous item.

The install worked fine for me.  Had an issue with xorg that had to be resolved, but not part of the install issue itself.

---

