---
title: "Tablet PC LG C1 Express Dual Touch Screen"
date: 2007-05-12
forum: Hardware &amp; Laptops
---

### Post by vespagts on 2007-05-12
I've set up Feisty on my LG C1 tablet PC and got almost complete peripherals recognized and functioning except for the touch screen. I know it is produced by Fujitsu and I have installed the fpit driver, but no touch screen is recognized at all. I guess the input device is seen as "Machintosh Mouse  Button Emulation" but I really don't know how to set it.

Can anyone help me please?

---

### Post by Olangu on 2007-11-13
[http://gentoo-wiki.com/HARDWARE_LG_C1#Tablet](http://gentoo-wiki.com/HARDWARE_LG_C1#Tablet)

Happy hacking!

---

### Post by Olangu on 2007-11-14
I can confirm that this works now.

Some pointers:

On my computer the device is autoconfigured, so no setserial is needed. (also my device is at 0x0300 and not 0x0220)

The location for xorg input drivers is /usr/lib/xorg/modules/input/ in Ubuntu.

Only one corepointer is allowed. And the mouse is configured as corepointer in ubuntu, you dont need to set the touchscreen as corepointer, 

Good luck!

---

### Post by vespagts on 2007-12-03
thank you, I'll try...

---

### Post by oc666 on 2008-01-01
> **Olangu said:**
> I can confirm that this works now.

Some pointers:

On my computer the device is autoconfigured, so no setserial is needed. (also my device is at 0x0300 and not 0x0220)

The location for xorg input drivers is /usr/lib/xorg/modules/input/ in Ubuntu.

Only one corepointer is allowed. And the mouse is configured as corepointer in ubuntu, you dont need to set the touchscreen as corepointer, 

Good luck!
Hey, I'm the one who wrote the guide in the Gentoo wiki. Lately I'm trying xubuntu distribution. Could you be more specific with the instructions (include kernel patch)?

Thanks a lot.

---

### Post by Olangu on 2008-01-01
You have do download the kernel source and apply the patch to it.

apt-get install linux-source

its a bit of a hustle but I think you'll manage.

---

### Post by samsonite on 2008-02-07
Hi guys, I am a complete gimp when it comes to linux but I suppose I will get the hang of it sooner or later. I'm on gutsy Gibbon 7.10 and looking for anywhere I can get terminal window prompts to help me install the touchscreen on my LG C1 express dual. Tried the lijnks on this thread but they didnt work when i tried them...can anyone help?
:(

---

### Post by Tschengis on 2008-02-08
Use[google cache]("http://64.233.183.104/search?hl=de&client=firefox-a&rls=com.ubuntu%3Ade%3Aofficial&hs=Xuy&q=cache%3Agentoo-wiki.com%2FHARDWARE_LG_C1&btnG=Suche&meta=") (I did it, too).
The cache-page is not finally loading but you can copy the html-sourcecode.

cheers

---

### Post by samsonite on 2008-02-09
nice one..today it worked anyway and so i've save the pages just in case!! Cheers man.

---

### Post by oc666 on 2008-02-21
> **Olangu said:**
> You have do download the kernel source and apply the patch to it.

apt-get install linux-source

its a bit of a hustle but I think you'll manage.

OK. I install this. 
The compile is just like in gentoo or there is any differences?

For comparison:
[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=7](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=7)

---

### Post by oc666 on 2008-03-14
Hello
I still can't get my tablet to work.
I stuck with the kernel patch. 
Additionally, I would like to implement the [brightness]("http://gentoo-wiki.com/HARDWARE_LG_C1#Brightness"). How could I do this?
Also, not written in the Gentoo guide, I would like to give birth to the tablet buttons. How could I do this?
BT"W, ubuntu 8.04 come with the new kernel 2.6.24?

Thanks a lot.

---

### Post by oc666 on 2008-04-04
Hello
I need a tool to recognize the special keys like fn keys (function key button with other button sequence)?

Thanks

---

### Post by oc666 on 2008-04-06
I installed ubuntu 8.04 beta.
I get output from the next command (when pressing with the pen on the tablet):
[PHP]cat /dev/ttyS0[/PHP]
I also configure my X with the next configuration:
[PHP]Section "InputDevice"
	Driver        "wacom"
	Identifier    "stylus"
	Option        "Device"        "/dev/ttyS0"
	Option        "Type"          "stylus"
	Option        "ForceDevice"   "ISDV4"
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "eraser"
	Option        "Device"        "/dev/ttyS0"
	Option        "Type"          "eraser"
	Option        "ForceDevice"   "ISDV4"
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "cursor"
	Option        "Device"        "/dev/ttyS0"
	Option        "Type"          "cursor"
	Option        "ForceDevice"   "ISDV4"
EndSection
[/PHP]
But, the tablet doesn't work yet.

---

### Post by Olangu on 2008-04-07
It's because it's not a wacom touchscreen.

You need this driver:
[http://stz-softwaretechnik.com/~ke/touchscreen/p-series.html](http://stz-softwaretechnik.com/~ke/touchscreen/p-series.html)

Last time I tried, this driver failed in Hardy. But please try it and report your success.
My guess is that this driver is not compatible with the new xorg in hardy.

---

### Post by oc666 on 2008-04-07
Hey, I try this and I get the next output (from /var/log/Xorg.0.log):
> (II) LoadModule: "fujitsu"
(II) Loading /usr/lib/xorg/modules/input//fujitsu_drv.so
(II) Module fujitsu: vendor="Kenan Esau"
	compiled for 4.3.99.902, module version = 0.6.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(EE) module ABI major version (0) doesn't match the server's version (2)
(II) UnloadModule: "fujitsu"
(II) Unloading /usr/lib/xorg/modules/input//fujitsu_drv.so
(EE) Failed to load module "fujitsu" (module requirement mismatch, 0)

How I can fix this problem?

Thanks a lot.

---

### Post by Olangu on 2008-04-08
Try building the module from source.

---

### Post by oc666 on 2008-04-08
> **Olangu said:**
> Try building the module from source.

How do I build this from source with xubuntu 8.04?

Thanks

---

### Post by Olangu on 2008-04-09
* Download and extract source from:
[http://stz-softwaretechnik.com/~ke/touchscreen/xf86-input-fujitouch-0.6.5.tar.bz2](http://stz-softwaretechnik.com/~ke/touchscreen/xf86-input-fujitouch-0.6.5.tar.bz2)

* In source directory:
./configure --prefix=/usr && make && sudo make install

Then you are done.

I just tried this, but the xserver dies on me after initializing the touchscreen.

---

### Post by oc666 on 2008-04-09
I run the command you wrote and I get the the next output:> ...
checking for XORG... configure: error: Package requirements (xorg-server xproto ) were not met:

No package 'xorg-server' found
No package 'xproto' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.



---

### Post by Olangu on 2008-04-10
You need development packages of xorg.

---

### Post by oc666 on 2008-04-10
It's not work well and my X get messed out. How do I revert changes include reset the xorg.conf file to manufacture settings?

---

### Post by Olangu on 2008-04-11
Just comment the line that includes the touchscreen...

# InputDevice "touchscreen" "CorePointer"

---

### Post by japglish on 2008-04-12
Has anybody anywhere in the world EVER been able to make this touchscreen work with Ubuntu?  Have now spent two weeks using four different distros.  Absolutely no joy at all in Ubuntu but did manage to get it working after patching and recompiling the kernel in opensuse.  Only problem was that the recompiled kernel broke so many other things (wireless and sound) that it seemed barely worth the effort.  Can ANYBODY point to a successful installation on an ubuntu machine?  If so how??  Exactly???

---

### Post by Olangu on 2008-04-13
I had it working in Gutsy, after recompile of kernel.
I don't know if the patches are in the new kernel in Gutsy, if so, it should be a kids play to get it working.

How I did it in Gutsy:
Recompiled kernel, but made the new kernel with the same name as the precompiled one, to trick the precompiled modules to work on my kernel.

---

### Post by oc666 on 2008-04-14
> **japglish said:**
> Has anybody anywhere in the world EVER been able to make this touchscreen work with Ubuntu?  Have now spent two weeks using four different distros.  Absolutely no joy at all in Ubuntu but did manage to get it working after patching and recompiling the kernel in opensuse.  Only problem was that the recompiled kernel broke so many other things (wireless and sound) that it seemed barely worth the effort.  Can ANYBODY point to a successful installation on an ubuntu machine?  If so how??  Exactly???

Hey, I just work on xubuntu 8.04 beta to get it work. I hope that until 8.04 stable release (end of the month) I would get it work and publish guide on it.

---

### Post by japglish on 2008-04-15
That sounds great.  An idiot proof guide would be very useful..  Did you need to re-compile the kernel to get xubuntu to work??  The gentto wiki page on this tablet pc seems to indicate that the key patch is included in the newest hardy kernel.  Is this correct???

---

### Post by Olangu on 2008-04-16
The patch is included in Hardy.
But unfortunately the x-driver is not compatible with the newer xorg-server in hardy.

---

### Post by japglish on 2008-04-16
> **Olangu said:**
> I 
How I did it in Gutsy:
Recompiled kernel, but made the new kernel with the same name as the precompiled one, to trick the precompiled modules to work on my kernel.

not an uber-geek myself and need some help here.At what stage in the compiling process can you rename the kernel to be the same as the precompiled one?  An exact command would be unbelievably handy here.

---

### Post by Olangu on 2008-04-17
It's in the head of the Makefile if I remember correctly.

---

### Post by oc666 on 2008-05-08
> **oc666 said:**
> Hey, I just work on xubuntu 8.04 beta to get it work. I hope that until 8.04 stable release (end of the month) I would get it work and publish guide on it.

OK. I see that the only different between ubuntu and gentoo (in gentoo it's work just fine) is that the modules from the kernel 8250 & 8250_pci & 8250_pnp are not available from ubuntu. How could I enable this modules on ubuntu?

See also how I enabled this modules on gentoo [here]("http://gentoo-wiki.com/HARDWARE_LG_C1#Tablet").

Thanks

---

### Post by justynbutler on 2008-05-14
The fujitouch_drv.so module was causing X to die and running it through strace showed that it was due to "undefined symbol: xf86AlwaysCore".

This Debian patch for the related evtouch driver suggests that xf86AlwaysCore is no longer required:
[http://lists.debian.org/debian-x/2007/09/msg01230.html](http://lists.debian.org/debian-x/2007/09/msg01230.html)

Commenting out
xf86AlwaysCore(local, TRUE);
from the xf86-input-fujitouch 0.6.5 source and recompiling (use ./configure --prefix=/usr and make sure that xserver-xorg-dev and build-essential are installed) allows the driver to work on my P1610.

Make sure you make the relevant changes to your xorg.conf file, as per:
[http://www.conan.de/touchscreen/p-series.html](http://www.conan.de/touchscreen/p-series.html)
but without the "CorePointer" option.
I do not need the setserial command on my system.

There may well be further problems I have yet to come across. Trying the driver in Fedora 9 does not work due to further undefined xf86* symbols. I think this may be due to major changes in X. Really the driver needs to be worked on by someone who knows somethings about X.

Good luck.

p.s. In the excitement of getting my touchscreen working on my new P1610 I made a huge, horrible scratch across the middle with my fingernail. Anyone have any ideas on how to make it less noticeable? I'm currently polishing the screen with silver polish.

---

### Post by Olangu on 2008-05-15
Confirming.

Working perfect.

Thousand thanks justynbutler!

A quick howto:

* Download and extract source from:
[http://stz-softwaretechnik.com/~ke/touchscreen/xf86-input-fujitouch-0.6.5.tar.bz2](http://stz-softwaretechnik.com/~ke/touchscreen/xf86-input-fujitouch-0.6.5.tar.bz2)

* In source directory:
mv fujitsu.c fujitsu.c.old 
grep -v xf86AlwaysCore fujitsu.c.old > fujitsu.c 
./configure --prefix=/usr && make && sudo make install

* Edit /etc/X11/xorg.conf

---

### Post by oc666 on 2008-05-15
Works fine with this patch on xubuntu 8.04.

---

