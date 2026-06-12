---
title: "Wacom Bamboo with 7.04"
date: 2007-06-29
forum: Hardware &amp; Laptops
---

### Post by teiro on 2007-06-29
Hi there!
Guess what: I have problems getting my tablet working ;).
It is a wacom bamboo and I'm running ubuntu 7.04.
What i've done so far:
I first tried to follow the brief [HOW-TO]("http://linuxwacom.sourceforge.net/index.php/minihowto"), but gave up as my terminal couldn't recognize the command "yum remove kernel-devel".
After that I followed the instructions at [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom) but even with the "in case it doesn't wokr"-tutorial, my pad wont even light up(it has four blue led's lightened up  when connected to the PC using windows)
Beeing not an experienced ubuntu-user, i now have totally no clue what I could do.

IN hope for someone to help me
Teiro

---

### Post by tariqf on 2007-07-26
I have the same problem it wont even light up in ubuntu but works fine when I boot into windows or plug into osx.

Did you resolve this?

---

### Post by madjo on 2007-07-26
I'm hoping someone has solved it. 
I know I should have investigated whether this tablet would work on Linux, and I thought that I had: according to the [Linux Wacom driver](http://linuxwacom.sourceforge.net/) website the Bamboo is supported by their driver since 0.7.7
But apparently it doesn't work automagically. :(

---

### Post by jazzroy on 2007-07-29
I'm in the same situation, maybe it's a matter of kernel.
Somebody with some more knowledge could help?

---

### Post by tenbones on 2007-07-29
Have you had a look here: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_a_Wacom_tablet](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_a_Wacom_tablet) ?

Guess you have.

I had a look here: [http://linuxwacom.sourceforge.net/index.php/dl](http://linuxwacom.sourceforge.net/index.php/dl) and it looks to me like only driver linuxwacom-0.7.8-2 have support for bamboo. So far ubuntu only have 7.7.7 in its repo.

Does this make any sense to you?

---

### Post by robgill on 2007-07-29
This got my Graphire4 working great

[http://ubuntuforums.org/showthread.php?t=25151&highlight=wacom+tools](http://ubuntuforums.org/showthread.php?t=25151&highlight=wacom+tools)

PS yum is not for debian based linux (Ubuntu is debian based)

---

### Post by tenbones on 2007-07-29
I believe only version 7.7.12 have support for bamboo. This is also a beta version so it is not included in the ubuntu repo. Bamboo is however now included in stable version 0.7.8-2 so perhaps it will only be a matter of time before it is included in the ubuntu repo. I don't know how the Ubuntu policy is for updating their packages.

---

### Post by madjo on 2007-07-29
Yes, tenbones, I have seen that page and followed it. But sadly it doesn't do much.

It's a recently reinstalled Xubuntu 7.04 machine. 

I dug a little deeper, and after I did 'more /proc/bus/usb/devices' I retrieved this bit of info:

```
T:  Bus=02 Lev=01 Prnt=01 Port=03 Cnt=03 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=056a ProdID=0065 Rev= 1.08
S:  Manufacturer=Wacom Co.,Ltd.
S:  Product=MTE-450
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr= 44mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=   9 Ivl=4ms
```

Note the Driver=(none).
It should at least say something, like wacom or usbhid (at least according to the Linux Wacom project page). :)

But I'll try Robgill's link also.
(and after that I'll try if I can upgrade the Wacom drivers) :)

---

### Post by tenbones on 2007-07-29
Yes, madjo, I think you need to upgrade the driver. I don't think the one in the ubuntu repo (7.7.7) have bamboo support.

---

### Post by tariqf on 2007-07-29
I havi installed the latest wacom 0.7.8-2 (and did the various settings in xorg.conf manually)..

Installing Wacom man page......
Installed under /usr/share/man/man4

Installing wacom_drv....
wacom_drv.so installed under /usr/lib/xorg/modules/input

Installing utility programs (wacdump, xidump, xsetwacom....)
Installed under /usr/local/bin

Installing wacomcpl......
Installed under /usr/local/bin


You need to compile and install wacom.(k)o manually if your kernel is out of date.


Now what? The problem seems to be that the device does not power up. It always flashes on for a second then goes off.

Tried Mandriva 2007 with newest driver and opensuse 10.2 and both power up (which is more than ubuntu does!) but does not work!

---

### Post by madjo on 2007-07-29
How did you fix the 'yum' reference in the prebuilt/install file? *update* never mind I was missing the tcl and tk packages.

I, too, have the problem that it doesn't power up.Just at boot time I can see the lights turn on. But right before the drivers being loaded (according to the start up screen), they go out, never to be heard of again.



BTW, Tariqf, you might need to alter your xorg.conf file. Perhaps instead of pointing to /dev/input/wacom, it could be /dev/input/eventX (where X is a number)

---

### Post by tariqf on 2007-07-29
Hi yes I tried /dev/input/wacom and /dev/input/event2 still nothing. I`ve run out of ideas now!

Have successfully installed Vista in virtualbox and it powers up and works perfect within that though but really want this to work in ubuntu :(

---

### Post by madjo on 2007-07-31
well I tried to install the latest driver. still no result. :(
It just won't start up, nor does it work.

This is the output of dmesg, when it's just been detached and then re-attached:
```
[19507.496000] usb 2-4: USB disconnect, address 4
[19511.652000] usb 2-4: new full speed USB device using ohci_hcd and address 6
[19511.868000] usb 2-4: configuration #1 chosen from 1 choice
```

And this is from 'more /proc/bus/usb/devices':
```
T:  Bus=02 Lev=01 Prnt=01 Port=03 Cnt=03 Dev#=  6 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=056a ProdID=0065 Rev= 1.08
S:  Manufacturer=Wacom Co.,Ltd.
S:  Product=MTE-450
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr= 44mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=   9 Ivl=4ms
```

I have a feeling that it's because of 'Driver=(none)', but I am at a loss on how to solve that problem.

---

### Post by madjo on 2007-07-31
Ok. dug deeper still.
I tried regenerating the makefiles. And I found something:

When I invoked configure like this:
./configure --enable-hid --with-kernel=/usr/src/linux-source-2.6.20/ 
I got this at some point:
```
./configure: line 21197: test: -ge: unary operator expected
***
*** WARNING:
*** Unable to compile hid.o without kernel build environment
*** hid.o will not be built
***
```
And at line 21197 I saw this: 	"if test $kver -ge 18; then"
I have no clue what that should be. could be != or >= or ==. I don't know.

btw, how does one enable 'module support' on a newly downloaded kernel? 
For the wacom.o file the configure script looks for this file:
$WCM_KERNELDIR/include/linux/autoconf.h
(where $WCM_KERNELDIR is the location I have set with --with-kernel.)
That file does not exist on my computer. 
So './configure --enable-wacom --with-kernel=/usr/src/linux-source-2.6.20' fails with the message:
```
***
*** WARNING:
*** Unable to compile wacom.o without kernel build environment
*** wacom.o will not be built
***
```

I am not sure what I should do now.

---

### Post by elaking on 2007-07-31
I got the exact same problem and I also think the 'Driver=(none)' is the problem.
According to the [Howto](http://linuxwacom.sourceforge.net/index.php/howto/testtablet) at the Linux Wacom Project page "If you see anything other than wacom after Driver=, at least hid-core.c needs to be updated".
A quick search about updating hid.c gave me nothing, though, so I'm at a loss.

Edit: I'm running 2.6.20 kernel and according to the Howto:
"Note, for kernel 2.6.18 and later, no need to build hid any more. For other kernels, refer to Testing Tablet Detection to see if you need to build hid or not."
That makes it even weirder it won't work.

Edit2: Read some and [apparently kernel 2.6.23](http://kernel.org/pub/linux/kernel/v2.6/testing/ChangeLog-2.6.23-rc1) will add support for the Bamboo tablet, guess it adds support in the wacom driver.
I bet one could add all this now as well but I really have no idea how to get the new driver patched into the current kernel..
I've played some with the 2.6.22 kernel source and patched the 2.6.23-rc1 into it but I don't think I cba since I need to play with the restricted modules and whatnot.

---

### Post by madjo on 2007-08-01
> **elaking said:**
> Edit2: Read some and [apparently kernel 2.6.23](http://kernel.org/pub/linux/kernel/v2.6/testing/ChangeLog-2.6.23-rc1) will add support for the Bamboo tablet, guess it adds support in the wacom driver.
I bet one could add all this now as well but I really have no idea how to get the new driver patched into the current kernel..
I've played some with the 2.6.22 kernel source and patched the 2.6.23-rc1 into it but I don't think I cba since I need to play with the restricted modules and whatnot.

Then I hope that Ubuntu 7.10 will ship with that newer kernel. :)
I'm not going to hose my system, by screwing around with the kernel. Done that too many times in the past, when I tried Slackware and Redhat.
I never want to see another 'kernel panic' again. :)

---

### Post by naught101 on 2007-08-21
so.. I got mine brand new bamboo working in 7.04, at least a bit. I still need some help

What's working: buttons, lights, position of pen
what's not working: position of pen, any of the more advanced features (pressure, angle), the gtk Options dialogue box (in gimp and inkscape).

For some reason, the tablet is working something like a touchpad, in that movement from one corner to the opposite corner only moves the cursor half way across the screen. this is my first tablet, so I don't know if it's meant to work that way, but I doubt it. each corner of the tablet should correspond to a corner of the screen..

I can draw with it partially, if I use the "<" button at the top of the tablet and move the pen, but I can't use pressure, or angle this way. for some reason, my normal laptop mouse buttons (Clit mouse and track pad) stopped working in gimp temporarily, but now they are working again. I can now also draw spots purely with the pen in Gimp (when the pen first touches the surface, it paints a little)

Basically, I got it to work thus:
followed all the steps in this forum thread, and a previous one on wacom tablets generally, then:
1. download the newest linuxwacom source (0.7.8 from [http://linuxwacom.sourceforge.net/](http://linuxwacom.sourceforge.net/))
2. unzip to ~
3. open a console
4. run "cd ~/linuxwacom(version)"  (or whatever, you might need to use tab)
5. run "./configure --enable-wacom"
6. run "make"
7. run "sudo make install"
8. run "sudo rmmod wacom"
9. run "sudo insmod ~/linuxwacom(version)/src/wacom.ko"

some wierd **** happened after that, but seems to be working fine now. Haven't rebooted yet.

I'm using /dev/input/event4 in /etc/X11/xorg.conf, instead of /dev/input/wacom. wacom-tools didn't work for me (probably because it's not a late enough version). you can find the right event number by following the instructions on the wacom page on the ubuntu wiki.

I'd love to know whether other people have made it any further than this, and if they know the solutions to any of my problems, to let me know...

cheers
ned

---

### Post by naught101 on 2007-08-21
everything seems to work fine in wacdump, although my bamboo is now on event9. I fixed this with the udev suggestion from here: [http://forums.fedoraforum.org/showthread.php?t=160969](http://forums.fedoraforum.org/showthread.php?t=160969)

basically, there's a udev rule that precedes the /etc/udev/65-wacom.rules, to fix this, change the name of that file to 20-wacom.rules.  /dev/input/wacom is then created as a symlink to the relevant event# when the tablet is plugged in. although now gtk doesn't seem to be registering a stylus/eraser (when I go into the input dialogue from either gimp or inkscape (it's the same dialogue, right?)..

Like I said, everything is working in wacdump, to some extent, I can see the pressure changing, buttons being pressed, "eraser" and "pen" show up (should "pen" be "stylus"?), and "touch".

But still no joy with drawing - I get a click when I "touch", but that's it. I'd really enjoys some help on this. the two basic problems are that the pressure doesn't register in Gimp or inkscape, and that the resolution of the tablet doesn't match the screen.

---

### Post by elaking on 2007-08-21
I followed your steps and got the same result. Haven't changed anything in xorg.conf but got the same functionality as you with the tablet, that is: need to press '<' to write and wrong resolution etc.

---

### Post by tariqf on 2007-08-24
ok followed the instructions and am at the same point as you guys. Pen kinda works but resolution wrong and you have to press down on the tablet to move the mouse whereas on windows or mac I can just hover above the tablet to move the mouse and only press when I want to drag or draw.

Still googling but cannot find out how to get these annoying issues sorted - until then the tablet is useless!

---

### Post by naught101 on 2007-09-03
There's a new Kernel update available. Can someone try it with the bamboo? I'm not at home, but I'll try it as soon as I can.

---

### Post by jazzroy on 2007-09-03
Tried.. it's the same.
the tablet lights on when plugged but turns off in a second. :(

---

### Post by naught101 on 2007-09-04
Jazzroy; you need to follow the instructions above to get the LEDs to stay on.

Unfortunately, it's still not working, even on the 2.6.20 kernel.

go here: [http://www.wacom-europe.com/forum/topic.asp?lang=uk&TOPIC_ID=9134](http://www.wacom-europe.com/forum/topic.asp?lang=uk&TOPIC_ID=9134) and make a noise. Something might happen.

---

### Post by jazzroy on 2007-09-08
thanks, I was hoping the kernel to fix everything :)

---

### Post by jun_shindo on 2007-09-16
I used The Linux Wacom Project Guide and worked.
I'm a quite new user of linux and ubuntu, sorry for my bad description and sorry for my bad English...
Using Ubuntu 7.04 and Wacom Bamboo tablet
using linux wacom guite, my steps:
-backup of xorg.conf (in /etc/X11/)
-edited xorg.conf, commented the sections rows in *Section "InputDevice"* having Identifier stilus/eraser/pad/cursor, commented the rows in *Section "ServerLayout"* stilus/eraser/pad/cursor 
-downloaded drivers from wacom project
-./configure to prepare installation
-oh, some warnings.... missing linux sources and libraries
-installed the packages missing for complete installation (linux headers, some libraries)
-./configure
-ok, no more warnings....
-compile and install
-added modules in kernel (see *3.5 - Testing If wacom.(k)o Will Load*)
-now tablet swithed on and works! but using the tablet the cursor is very slow
-testing of raw data.... Ok! (if you don't edit xorg.conf in step 2, I noticed that you can't see any raw data)
-added the sections in xorg.conf stilus/eraser/pad/cursor
-restart X....
-wow! works! and cursor is fast now!
-added permanently the modules...
-configure the inputs/shortcuts with xsetwacom

---

### Post by tariqf on 2007-09-16
does the mouse move when you are hovering the pen over the tablet as it should and then press onto the tablet for left click?

---

### Post by madjo on 2007-09-19
Woohoo! indeed that works! :)
Now only to figure out how xsetwacom works :)
So that I can also use that little round thing at the top.
BTW, does the tablet also hum for you guys? (there is a high pitched sound coming from it)

> **tariqf said:**
> does the mouse move when you are hovering the pen over the tablet as it should and then press onto the tablet for left click?

Yes it does for me. :)

---

### Post by tariqf on 2007-09-20
yes high pitched hum is a common fault and you will need to send the bamboo back to wacom in germany to get a replacement. I have the same problem and am still wating for wacom to collect my bamboo for over 2 months now!!! Will have to call them again today they supposedly arranged collection via DHL.

Going to build a new buntu box today and get it working though.

---

### Post by madjo on 2007-09-20
okay, thanks.

One downer for me, after a reboot, the resolution was off again :( 

*edit* Ah it was on a different event this time. And I don't appear to have a wacom rules file.

> But still no joy with drawing - I get a click when I "touch", but that's it. I'd really enjoys some help on this. the two basic problems are that the pressure doesn't register in Gimp or inkscape, and that the resolution of the tablet doesn't match the screen.
Did you also add a 'pad' to your xorg file?

```

# This section is for Intuos3, Cintiq 21UX, Graphire4, or Bamboo
Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
  Option 	"Device" 	"/dev/input/event6" 	#Change to /dev/input/event for USB
  Option        "Type"          "pad"
  Option        "USB"           "on"                  # USB ONLY
EndSection
```
And then of course to the bottom of that file: 
```
Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"pad"		"SendCoreEvents"
EndSection
```

---

### Post by naught101 on 2007-09-21
Sweet. Tablet is working swell. Both Inkscape and GIMP like it very much.

I still have two problems:
1. the GTK Input Devices dialogue isn't working properly. I go into it from either program, and the "pad" settigns come up. I can change them, in both the "axes" and "keys" tabs, and I can also change the mode, though I don't know if this does anything (th pad is just the buttons up the top, right?). the problem is that when I select any of the other input devices ("cursor", "stylus", "eraser", or "synaptics touchpad" (on a laptop)), all the settings disappear. When I change back to the "pad", they don't re-appear. Anyone else having this problem?

2. The eraser's pressure is shot.  I can't get mid way pressure, it's pretty much all or nothing, and I have to press pretty hard to get all...
Does anyone know how the presscurve option works? what are each of the four numbers?

---

### Post by naught101 on 2007-09-21
The pen also seems to die after a certain amount of time without use (20 mins?), and reverts to usb mouse mode. Unplugging and replugging doesn't fix it. Restarting X probably will...

---

### Post by madjo on 2007-09-22
> **naught101 said:**
> Sweet. Tablet is working swell. Both Inkscape and GIMP like it very much.

I still have two problems:
1. the GTK Input Devices dialogue isn't working properly. I go into it from either program, and the "pad" settigns come up. I can change them, in both the "axes" and "keys" tabs, and I can also change the mode, though I don't know if this does anything (th pad is just the buttons up the top, right?). the problem is that when I select any of the other input devices ("cursor", "stylus", "eraser", or "synaptics touchpad" (on a laptop)), all the settings disappear. When I change back to the "pad", they don't re-appear. Anyone else having this problem?
You mean like in GIMP? Yes, I have the same problem there.

2. The eraser's pressure is shot.  I can't get mid way pressure, it's pretty much all or nothing, and I have to press pretty hard to get all...
Does anyone know how the presscurve option works? what are each of the four numbers?[/QUOTE]
I have noticed this too. Have no idea hov to solve i though. :(

---

### Post by gali98 on 2007-09-24
okay, I have a Graphire4 (which kinda makes me mad cause I just bought it and then bamboo with it's cool little ring came out... oh well I got a sweet deal on it), but I'm pretty sure you should just leave the pad option off (as in not screen or window) 
what that guy jun_shindo did sounds about right to me. but for a good support you'll probably have to wait for the next kernel release. That stinks... as for button and pad support I'll get to that in a minute.
Presscurve is to change to curve of the pressure(obviously that's the best way to explain it) as for how it works here it goes...
Okay basically it designing a belzier curve. You have two set points: (0,0) and (100,100)
The four values you choose define the support points. i.e. where you have your four values of presscurve:
"x1,y1,x2,y2"
(x1,y1) is your support curve for the set point (0,0) and (x2,y2) is the support point for (100,100)
Therefore you can set the curve of this belzier curve however you want. If you had
Presscurve  "0,0,100,100" this would give you a straight line and eveen pressure whereas
Presscurve  "0,75,25,100" would give you a very steep curve and a soft pressure feel and
presscurve "75,0,100,25" would give a very shallow curve and a firm pressure feel. You'll have to experiment to find how you really want it.
Okay for pad support I use [expresskeys.]("http://freshmeat.net/projects/wacomexpresskeys/")
I have a wacom tutorial I am compiling here...
[http://ubuntuforums.org/showthread.php?t=553573]("http://ubuntuforums.org/showthread.php?t=553573")
 that shows all about that and how to fix some problems and such. Visit that and stay tuned cause I will add to it later tonight. For right now, a lot of the stuff may not apply to the bamboo, but ahng around... there's still hope. I am hoping for it to be a general troubleshooter that can bring together a load of stuff from all around. That's it for here, but check the tutorial for maybe some more help,
Kory

---

### Post by JoeM13 on 2007-10-01
> **madjo said:**
> You mean like in GIMP? Yes, I have the same problem there.

2. The eraser's pressure is shot.  I can't get mid way pressure, it's pretty much all or nothing, and I have to press pretty hard to get all...
Does anyone know how the presscurve option works? what are each of the four numbers?


I am thinking about buying the Bamboo myself, so I had a look at the specifications. Now there are new versions of the Bamboo called Bamboo One and Bamboo Fun. It becomes obvious that the eraser has only an on or off function with the original Bamboo whereas the new Bamboo Fun has 512 degrees in pressure there. Aside from this, there is only a difference in design and software. The Bamboo One has only half the pads resolution and is missing the extra keys.
I just hope that someone gets the Bamboo working properly and consistently under Ubuntu. Then I would consider buying it.

---

### Post by gali98 on 2007-10-08
I don't think it's a matter or will, but more of a matter of when.

---

### Post by elaking on 2007-10-22
Any updates on the Bamboo and 7.10?
After I updated to 7.10 with the 2.6.22 kernel my Bamboo is on at all times but I can't find it with "more /proc/bus/input/devices" or such.
Maybe I should just install Win XP on my girlfriend's computer..

---

### Post by Low Life Rising on 2007-10-22
I'm having trouble compiling the latest linuxwacom drivers for my new Bamboo tablet. The configure runs fine but I get this when I run make:

```
grw@toshy-the-laptop:~/Desktop/linuxwacom$ make
make  all-recursive
make[1]: Entering directory `/home/grw/Desktop/linuxwacom'
Making all in src
make[2]: Entering directory `/home/grw/Desktop/linuxwacom/src'
Making all in .
make[3]: Entering directory `/home/grw/Desktop/linuxwacom/src'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/grw/Desktop/linuxwacom/src'
Making all in wacomxi
make[3]: Entering directory `/home/grw/Desktop/linuxwacom/src/wacomxi'
/bin/bash ../../libtool --tag=CC --mode=link gcc -Wall -g -O2 -I/usr/include/tcl8.4/   -o libwacomxi.la -rpath /usr/local/lib/TkXInput -no-undefined wacomxi.lo -L/usr/lib -lX11 -lXi 
gcc -shared  .libs/wacomxi.o  -L/usr/lib -lX11 -lXi  -Wl,-soname -Wl,libwacomxi.so.0 -o .libs/libwacomxi.so.0.0.0
/usr/bin/ld: cannot find -lXi
collect2: ld returned 1 exit status
make[3]: *** [libwacomxi.la] Error 1
make[3]: Leaving directory `/home/grw/Desktop/linuxwacom/src/wacomxi'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/grw/Desktop/linuxwacom/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/grw/Desktop/linuxwacom'
make: *** [all] Error 2
```

Can anyone suggest what is wrong and how to fix it? Or when the 2.6.23 kernel will be released which should support the Bamboo (according to the Linux Wacom Project site)?

Cheers

---

### Post by JoeM13 on 2007-10-24
> **Low Life Rising said:**
> 
Can anyone suggest what is wrong and how to fix it? Or when the 2.6.23 kernel will be released which should support the Bamboo (according to the Linux Wacom Project site)?

Cheers

I compiled the wacom driver at home yesterday according to the protocols at the linuxwacom site without encountering your problems. However, I made sure that all necessary libraries were installed. Did you check this?
The build options should look like this:
[http://linuxwacom.sourceforge.net/index.php/howto/buildwacom6]("http://linuxwacom.sourceforge.net/index.php/howto/buildwacom6")
After that everything went fine and the bamboo works well.

Cheers,

Joe

---

### Post by JoeM13 on 2007-10-24
> **elaking said:**
> Any updates on the Bamboo and 7.10?
After I updated to 7.10 with the 2.6.22 kernel my Bamboo is on at all times but I can't find it with "more /proc/bus/input/devices" or such.
Maybe I should just install Win XP on my girlfriend's computer..

I have updated to Gutsy a couple days ago and tried to connect the bamboo yesterday. I couldn't find the proper devices file either. I had to download the linux wacom driver and compile it myself. After following the instructions, I got it working now...

---

### Post by justin_w on 2007-10-24
> **elaking said:**
> Any updates on the Bamboo and 7.10?
After I updated to 7.10 with the 2.6.22 kernel my Bamboo is on at all times but I can't find it with "more /proc/bus/input/devices" or such.
Maybe I should just install Win XP on my girlfriend's computer..

I have no listings for it under /proc/bus/input/devices either. I do have a few odd listings though. One for a Macintosh one button mouse emulation and two having to do with a power switch. Checking logs the device is seen when plugging and unplugging but seems to never be picked up by the latest Linux Wacom drivers, or any driver at all. I also have 7.10 with the 2.6.22 kernel and followed the instructions on the Linux Wacom site exactly and the correct version of the driver loads but has no effect on the tablet. Bamboo Fun btw. I might have to use it on my wife's PowerMac for now just so I can get some use out of it until this is resolved(hopefully in soon to be picked up 2.6.23 kernel).

---

### Post by Low Life Rising on 2007-10-24
> **JoeM13 said:**
> I compiled the wacom driver at home yesterday according to the protocols at the linuxwacom site without encountering your problems. However, I made sure that all necessary libraries were installed. Did you check this?
The build options should look like this:
[http://linuxwacom.sourceforge.net/index.php/howto/buildwacom6]("http://linuxwacom.sourceforge.net/index.php/howto/buildwacom6")
After that everything went fine and the bamboo works well.

Cheers,

Joe

Yeah, I installed libraries until the configure gave no more warnings. My build config:

```
  BUILD ENVIRONMENT:
       architecture - i486-linux-gnu
       linux kernel - yes 2.6.19
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
```

Thanks anyway.

---

### Post by Curtisc on 2007-10-24
Hi,

I'm trying to build the driver for 7.10 (Kernel 2.6.22-14), and everything goes well following the linuxwacom directions up until I try insmod.  I get this error:
```
insmod: error inserting './wacom.o': -1 Invalid module format
```
I removed everything I could find to do with wacom, and tried again, and still the same problem.  Anyone else get this message?

---

### Post by Curtisc on 2007-10-24
Whoops, posted too soon... looks like it accepts wacom.ko as a valid module, even though wacom.o is supposed to be the right one for my kernel.

Everything is working now except for the buttons and eraser pressure sensitivity, although I'm not even sure if the bamboo is supposed to have that.  Thanks for the help here!

---

### Post by justin_w on 2007-10-24
> **Curtisc said:**
> Whoops, posted too soon... looks like it accepts wacom.ko as a valid module, even though wacom.o is supposed to be the right one for my kernel.

Everything is working now except for the buttons and eraser pressure sensitivity, although I'm not even sure if the bamboo is supposed to have that.  Thanks for the help here!

The wacom.o is for 2.4 and wacom.ko for 2.6 from what I gathered from the walkthrough.

---

### Post by justin_w on 2007-10-24
I found this patch for the latest wacom driver for the bamboo fun tablets which worked for me.

[http://sourceforge.net/tracker/index.php?func=detail&aid=1802837&group_id=69596&atid=525126](http://sourceforge.net/tracker/index.php?func=detail&aid=1802837&group_id=69596&atid=525126)

---

### Post by quinnten83 on 2007-10-26
I've tried following the instructions on the linux wacom project, but the manual is so extensive i get lost. I run ubuntu 7.04 and soon  7.10 and I have a bamboo one tablet. I don't think I need any XFree86 modules cause I think 7.04/ 7.10 runs X11. I just do not know how to get this working, I am completely lost and I am getting frustrated having to tinker with Ubuntu constantly just to get some things to work.
Usually I don't mind, but this is getting to me now (Okay, end rant).

So exactly which part of the instructions did you follow? Please help me, and how do I apply that patch if it is needed and what do I need to run before applying the patch?

Is there an easy manual anywhere?

---

### Post by salemboot on 2007-10-28
I have the Bamboo Fun, which isn't working :)

The patch pertains to the linuxwacom driver.

You have to add these lines to the appropriate place linuxwacom-0.7.8-3/src/2.6.19/wacom_wac.c

{ "Wacom Bamboo Fun Small", 9,14760, 9225,  511, 63, WACOM_MO },
{ "Wacom Bamboo Fun Medium",9,21648,13530,  511, 63, WACOM_MO },

{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x17) },
{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x18) },

Edit:
take out the smiley face its actually 0 x 1 8 


I think you have to patch the xorg driver as well but I haven't seen that mentioned anywhere.

It shows my device as connected and the driver loaded.  As well, I can setup the different devices within The Gimp.

Nothing moves.  The cursor just sits there and I can't draw anything!

I've seen two different websites stating different options for the xorg.conf file.

I saw the system mouse configured with the "SendCoreEvents" instead of the "CorePointer"

Again this is very agravating.

---

### Post by madjo on 2007-10-30
Salemboot, did you reboot? Or otherwise reloaded X? Also make sure you are using the right 'device' in your xorg. (might take some trial and error, best done with wacdump. Just try the different events or other input devices in your /dev/input folder.


I have my Bamboo (just plain Bamboo, not the Fun or the One) working on Gutsy, but I've hit a new snag, and I can't seem to find a solution. (the search term "xsetwacom 'failed to set' AbsWUp" comes up with just one hit, and that's one without resolution.
I can set the buttons on my Bamboo just fine, I'm just unable to apply any event to the scroll ring of the Bamboo. I've tried AbsW, I've tried RelW and even StripL or StripR. Nothing it all returns largely the same error:

```
$ xsetwacom set pad AbsWUp "CORE key Up"
X Error: 8 BadMatch (invalid parameter attributes)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set pad value for 'AbsWUp'
```

Can anyone give me some advise?

---

### Post by madjo on 2007-10-31
I solved my problem by installing the latest dev version. :)

---

### Post by Dan_Dranath999 on 2007-11-02
How can i get the xorg sdk build enviroment ???  (it's a stupid question, right?) :confused:

---

### Post by quinnten83 on 2007-11-12
does anyone know if there is a way to get the wacom bamboo one working with 7.10 now?
prefferably an instruction that does not require a degree in advanced engineering?

---

### Post by ajselvig on 2007-11-13
Hi all-

I've been having the same sort of troubles. I'm trying to get my Bamboo Fun working on my Gutsy machine. Here's a thurough rundown of the steps I've taken and the issues I've seen (prepared as a separate thread until I found this one, read all of the posts, and couldn't find an answer):


I understand that only the new Linux Wacom beta drivers (0.7.9.1) work with the Bamboo AND the 2.6.22 kernel, so I downloaded them and tried to compile and install.

I followed the tutorial on the Linux Wacom website rather closely. The first concern I had in the process was from Testing Tablet Detection ([http://linuxwacom.sourceforge.net/index.php/howto/testtablet](http://linuxwacom.sourceforge.net/index.php/howto/testtablet)) when trying to run 

$ more /proc/bus/input/devices

and not getting any entry for the tablet. The tutorial seems to think that you'll get something, even if it isn't right. This is, of course, after plugging in the tablet and restarting X. The tablet is getting power (the pretty blue LED's are on). 

So, I proceeded anyway hoping the installation would still work. I edited wacom_wac.c per this ticket regarding the support for Bamboo fun [http://sourceforge.net/tracker/index.php?func=detail&aid=1802837&group_id=69596&atid=525126](http://sourceforge.net/tracker/index.php?func=detail&aid=1802837&group_id=69596&atid=525126).

I configured the build with --enable-wacom, made, and installed it. Everything seemed to work fine. I then tested that the module will load per the tutorial ([http://linuxwacom.sourceforge.net/index.php/howto/testwacom):](http://linuxwacom.sourceforge.net/index.php/howto/testwacom):)

andy@andy-desktop:~/linuxwacom-0.7.9-1/src/2.6.22$ sudo /sbin/rmmod wacom
andy@andy-desktop:~/linuxwacom-0.7.9-1/src/2.6.22$ sudo /sbin/insmod ./wacom.ko
andy@andy-desktop:~/linuxwacom-0.7.9-1/src/2.6.22$ tail /var/log/messages
Nov 12 23:00:42 andy-desktop kernel: [ 5108.442228] usbcore: deregistering interface driver wacom
Nov 12 23:01:50 andy-desktop kernel: [ 5177.116496] usbcore: registered new interface driver wacom
Nov 12 23:01:50 andy-desktop kernel: [ 5177.116505] /home/andy/linuxwacom-0.7.9-1/src/2.6.22/wacom_sys.c: v1.46-pc0.1:USB Wacom Graphire and Wacom Intuos tablet driver

So, this seems to give a similar, but not exact, result as the tutorial. It does indeed have v1.46pc0.1 as the version number (not the original 1.46). 

I then installed the wacom.ko by copying it to the approraite kernel directory:

andy@andy-desktop:~/linuxwacom-0.7.9-1/src/2.6.22$ sudo cp wacom.ko lib/modules/2.6.22-14-generic/kernel/drivers/input/tablet/wacom.ko 

Then I test whether or not I can load it:

andy@andy-desktop:~/linuxwacom-0.7.9-1/src/2.6.22$ sudo rmmod wacom
andy@andy-desktop:~/linuxwacom-0.7.9-1/src/2.6.22$ sudo modprobe wacom
andy@andy-desktop:~/linuxwacom-0.7.9-1/src/2.6.22$ grep -i wacom /var/log/messages | tail
Nov 12 23:08:04 andy-desktop kernel: [ 5550.145879] usbcore: deregistering interface driver wacom
Nov 12 23:08:49 andy-desktop kernel: [ 5595.098179] usbcore: registered new interface driver wacom
Nov 12 23:08:49 andy-desktop kernel: [ 5595.098189] /home/andy/linuxwacom-0.7.9-1/src/2.6.22/wacom_sys.c: v1.46-pc0.1:USB Wacom Graphire and Wacom Intuos tablet driver

Again, not quite the same thing. I'm getting output from wacom_sys.c instead of wacom.c like in the tutorial.

From my understanding, this should be all the setup I need to do besides modifying xorg.conf. So, I restart X, uncomment all the wacom related stuff from xorg.conf, and restart X again. Nothing works. I've tried both GIMP and Inkscape (although I think they use the exact same configuration tool) and they give me the following message when I try to configure the tablet (File->Input-> in Inkscape):

 No Extended Input Devices

Does anyone have any idea what's going wrong? It seems to me that there's something off right from the start since everything goes smoothly but I never quite get the right output. Has anyone had any successes with using the Bamboo Fun? Would I have better luck switching back to 7.04?

Thanks in advance for you help.

---

### Post by Melodic_BM on 2007-11-20
[I have got the same problem.]("http://ubuntuforums.org/showthread.php?t=617699")

---

