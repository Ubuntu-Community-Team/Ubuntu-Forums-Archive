---
title: "Wacom CTH480 - how to install"
date: 2013-10-17
forum: Hardware
---

### Post by ctammes on 2013-10-17
Hi,

I have a Wacom CTH480, ID 056a:0302, and I am trying to get it running in 12.04.

I followed the instructions on
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom)
and 
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Input-wacom](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Input-wacom)
and compiled xf86-input-wacom-0.23.0 and input-wacom-0.19.0. The result is a new wacom.ko, which I copied to /lib/modules/`uname -r`/kernel/drivers/input/tablet/.

It is not in xinput list, but lsusb gives the id:
 Bus 008 Device 002: ID 056a:0302 Wacom Co., Ltd

When I add 'wacom' to /etc/modules, it shows up in lsmod:
wacom                  60266  0 

dmesg seems to find wacom:
[   15.121097] usbcore: registered new interface driver wacom
[   15.121100] wacom: v1.53:USB Wacom tablet driver
but I expect something like this (from another post):
[ 1.665392] usb 3-6: New USB device found, idVendor=056a, idProduct=0302

Also, in syslog there is an entry:
 wacom: v1.53:USB Wacom tablet driver


I saw that in wcmUSB.c there is no entry for 0x302. Does this mean that it will never be found? I understand from other posts that there are people who have this table running, but how??

OS: 
uname -m = i686
uname -r = 3.2.0-54-generic-pae
uname -s = Linux
uname -v = #82-Ubuntu SMP Tue Sep 10 20:29:22 UTC 2013

Any suggestions??

Chris

---

### Post by Favux on 2013-10-17
Hi ctammes,

Welcome to Ubuntu forums!


Nice job so far!  :)

First thing is since you are using Precise (12.04) did you use the Frankenserver patch for xf86-input-wacom?  If you don't handle the mutant ABI xf86-input-wacom will crash the X Server when the tablet is plugged in.

I was hoping from what I was seeing that the generic/unknown stylus code would pick up the Intuos Pen and Touch's Pen once the kernel driver was supporting it.  Or given that the things seem to be replacements for the BambooPTs their usb protocol is the same.  In which case some BambooPT code Chris added a while ago would pick them up or at worst with the same protocol being able to skip a new define and in wcmUSB.c maybe a line similar to?
```
	{ WACOM_VENDOR_ID, 0xDB, 100000, 100000, &usbBamboo,     "CTH-661/L"		},
```

---

### Post by ctammes on 2013-10-18
I read about the [COLOR=#000000]Frankenserver patch, but did not apply it yet. Nothing crashes with the tablet attached or being connected, at least I do not see it. Could it be that the crash does not happen anymore on my Ubuntu release or with this (new) tablet? I think I am on Xserver 1.13 (cannot verify it now). Alternative: the newly compiled code does not load at all, for some reason ...

Chris


[/COLOR]

---

### Post by Favux on 2013-10-18
Well, you have the Precise (12.04) 3.2 kernel.  If Precise then the 1.11/1.12 hybrid X Server should identify itself as 1.11.3 or such.  To check run:
```
Xorg -version
```
> Alternative: the newly compiled code does not load at all, for some reason ...
This sounds like the case because **oops**...  My bad, didn't read your first post carefully enough.  Your model is not yet supported by input-wacom-0.19.0.  See this link:  [http://ubuntuforums.org/showthread.php?t=1515562&p=12817974&viewfull=1#post12817974](http://ubuntuforums.org/showthread.php?t=1515562&p=12817974&viewfull=1#post12817974)

So we have the code for support in a wacom.ko submitted upstream to the kernel.  If you wanted to use the patches to compile a working wacom.ko the question becomes what would be the best way to do that?

---

### Post by ctammes on 2013-10-18
I wonder if it would be enough just to add my model (CTH480/[COLOR=#000000]056a:0302[/COLOR]) to [COLOR=#000000]wcmUSB.c and see what happens. Is that the only place where a device is recognized??[/COLOR]

---

### Post by Favux on 2013-10-18
The kernel driver, wacom.ko, from input-wacom-0.19.0 doesn't support your model, only the new Intuos Pro's.  That's your main problem and why you don't see the tablet in **xinput list**.

---

### Post by ctammes on 2013-10-18
So I added a line to [COLOR=#000000]wcmUSB.c and still don't see the tablet in xinput. Is there any more documentation about these xf86-input and input modules? When these are the only drivers needed to make the Wacom running, it must be possible to patch something so xinput recognizes it?
 
I guess this is the repository: [/COLOR][http://sourceforge.net/p/linuxwacom/input-wacom/ci/input-wacom-0.19.0/tree/](http://sourceforge.net/p/linuxwacom/input-wacom/ci/input-wacom-0.19.0/tree/) ??

Is my model too new to be supported or not sold outside Europe (I am from Holland)? I am happy to try things out, but I don't even know what Intuos type I have, only CTH-480/S. The device cannot be very different from the others, can it?

Chris

---

### Post by Favux on 2013-10-18
Chris, please re-read my last two posts.

First you need a working Wacom kernel driver i.e. wacom.ko.  That translates the raw usb protocol/input from the tablet into something the Wacom X driver (xf86-input-wacom) can handle.  Then xf86-input-wacom tells the X Server what to do.

The wcmUSB.c is in xf86-input-wacom, the second part of the chain.  So of course that doesn't do anything.  Nothing is handling the usb input from the kernel.  First you need a working wacom.ko.

The working wacom.ko should be available in input-wacom in the next few weeks.  I think you'll need to wait until then and once it is available you'll be able to compile that wacom.ko.

---

### Post by ctammes on 2013-10-18
Thanks, that is what I wanted to know. I knew I didn't have to recompile the kernel, but could not figure out how both drivers were related to each other. I did generate a new wacom.ko. And I am interested how this driver business works. I did rewrite a Windows NT printer driver once, so this cannot be that different :-)

I'll be happy to test if you need someone. I wait till then.

Thanks in advance.

Chris

P.S. a lot of technical details are in lsusb, am I correct?

P.P.S. I read in a post [COLOR=#555555][FONT=arial]From: Shreyas Mandre <shreyasmandre@gm...> -	2013-10-09 17:24[/FONT][/COLOR]  that there is working code ... [FONT=arial, helvetica, clean, sans-serif][COLOR=#555555]  [/COLOR][/FONT]

---

### Post by Favux on 2013-10-18
> P.S. a lot of technical details are in lsusb, am I correct?
Yes.  Run lsusb and get the bus and device number, e.g. 001:006.  Then use the show switch -s to specify just the Wacom tablet with this command:
```
sudo lsusb -s 001:006 -vvv
```
Developer type info:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:DeveloperPages](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:DeveloperPages)

In the forum thread I linked you to above there is a link to Jason (linuxwacom/Wacom developer) linking to the code submitted to the kernel.  He suggests using the development kernel to get the wacom.ko,  I suggest the wacom-kernel.  Or maybe if lucky it might be easier to add the code to input-wacom and use that.

---

### Post by ctammes on 2013-10-18
Thanks for your support. I'll check the pages regularly.

---

### Post by Favux on 2013-11-07
Hi,

I have some patches and instructions to get the new Intuos Pen and Touches working in post #3 of the new [BambooPT HOW TO]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110408").

---

### Post by ctammes on 2013-11-07
[FONT=arial]I got my CTH-480 running on 12.04 (3.2.0-55-generic-pae) after applying the patches!! I had to manually patch input-wacom-0.19.0 (2.6.38) and xf86-input-wacom-0.23.0 and applied the build_against_frankenserver.patch. [/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]However, I had to make some extra changes to get the input module through the compiler. The code is attached. (INPUT_MT_POINTER is unknown and the call to input_mt_init_slots() uses two arguments in my kernel.)[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I still have to test thoroughly, but I can use the mouse from the tablet and I get output from xsetwacom list:[/FONT]
[FONT=arial]Wacom Intuos PT S Pen stylus    	id: 14	type: STYLUS    
Wacom Intuos PT S Pen eraser    	id: 15	type: ERASER    
Wacom Intuos PT S Finger touch  	id: 16	type: TOUCH     
Wacom Intuos PT S Finger pad    	id: 17	type: PAD       
Wacom Intuos PT S Finger touch  	id: 18	type: TOUCH     
Wacom Intuos PT S Finger pad    	id: 19	type: PAD  
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Also, Gimp recognizes the tablet and seems to work with it.

Chris[/FONT]

---

### Post by Favux on 2013-11-07
Thank you ctammes!  Let us know how the testing goes.  Being able to add support to Precise would be very nice.

---

### Post by ctammes on 2013-11-07
Well, I already noticed that the one-finger touch is taken as a two finger touch (right mouseclick). Three fingers for scroll does work. Is there a way in the code that I can adjust this?

I used the pen with Gimp and it works fine for drawing, but the eraser does not. I still have to experiment with the expresskeys.

Chris

---

### Post by Favux on 2013-11-07
So the small's Pen also has an eraser?  Fancy!  Is that two side buttons on a rocker switch?
> I already noticed that the one-finger touch is taken as a two finger touch (right mouseclick). Three fingers for scroll does work. Is there a way in the code that I can adjust this?
Probably not.  What I know about multi-touch is in part X. of the [Bamboo and Intuos PT HOW TO]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110408")  &  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Multitouch](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Multitouch).
> I still have to experiment with the expresskeys.
I'm very interested in hearing if the ExpressKeys are still out of sequence like the BambooPTs.

---

### Post by ctammes on 2013-11-07
The side switch defaults to right mouseclick (upper side) and double click (lower side). At least the upper side works. The eraser is the thick rubberish point on the top. It has no effect in Gimp.

---

### Post by carnrightchris on 2013-11-21
> **ctammes said:**
> [FONT=arial]I got my CTH-480 running on 12.04 (3.2.0-55-generic-pae) after applying the patches!! I had to manually patch input-wacom-0.19.0 (2.6.38) and xf86-input-wacom-0.23.0 and applied the build_against_frankenserver.patch. [/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]However, I had to make some extra changes to get the input module through the compiler. The code is attached. (INPUT_MT_POINTER is unknown and the call to input_mt_init_slots() uses two arguments in my kernel.)[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I still have to test thoroughly, but I can use the mouse from the tablet and I get output from xsetwacom list:[/FONT]
[FONT=arial]Wacom Intuos PT S Pen stylus        id: 14    type: STYLUS    
Wacom Intuos PT S Pen eraser        id: 15    type: ERASER    
Wacom Intuos PT S Finger touch      id: 16    type: TOUCH     
Wacom Intuos PT S Finger pad        id: 17    type: PAD       
Wacom Intuos PT S Finger touch      id: 18    type: TOUCH     
Wacom Intuos PT S Finger pad        id: 19    type: PAD  
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Also, Gimp recognizes the tablet and seems to work with it.

Chris[/FONT]
Could someone explain how to apply these patches? I just got my tablet and I'm trying to get it to work, I think I got the input-wacom-0.19.0_patched to work fine but when I run ./configure on the xf86, I get ```
 configure: error: Package requirements (xorg-server >= 1.7.0 xproto xext kbproto inputproto randrproto) were not met:

No package 'xorg-server' found
No package 'xproto' found
No package 'xext' found
No package 'kbproto' found
No package 'inputproto' found
No package 'randrproto' found



```

---

### Post by Favux on 2013-11-21
Hi Chris,

Welcome to Ubuntu forums!


Did you install the dependencies?  For Ubuntu:
```
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libncurses5-dev autoconf libtool
```
See part I. of the [Intuos Pen and Touch HOW TO]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110408").

---

### Post by LillyDragon on 2013-12-26
I hate bumping the topic, but I've been trying to wrap my head around installing the drivers myself for the past two days. (Recently got a CTH-480 and it worked great on Windows.)

I understand that the wacom.co is the actual driver, while the Xorg input driver acts as the medium between the drivers and the kernel. Both are important I can't skip installing either in the proper order. I am also glad the frankenpatch is no longer necessary after recent updates to 12.04 LTS kernels.

However, I was rather green during the process, and tried installing the xf64-input driver first. (Oops!) Thankfully, no harm has been done yet, I didn't compile and install the drivers because of a build error I was getting. I got all the dependencies necessary to compile, so I fear this might pose an obstacle once the input-wacom is compiled and installed.

```
checking for X11... no
configure: error: Package requirements (x11 xi xrandr xinerama) were not met:

No package 'xinerama' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables X11_CFLAGS
and X11_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

Either I'm missing X11, or Ubuntu has put it somewhere else. My head hurts at the prospect of the latter, Ubuntu has done some non-standard arrangements in the past before.

---

### Post by LillyDragon on 2013-12-27
Slight bump, the dependencies were easily obtained; I was overlooking a line talking about them in the Linux Mint forum topic. So I was able to install both drivers successfully without errors, and a reboot for each.

However, the tablet is still doing nothing. The blue light activates whenever there is activity on the surface, and the tablet does show up in lsusb, but it is not detected as a pointing device or by the Wacom settings manager. Are there are other ways I can confirm the drivers were properly installed, or their version numbers? Did I install to the wrong kernel folder? Mine is 3.2.0-57-generic, according to sysinfo.

EDIT : After trying again, I think the driver must be working, because it's causing the X-server to crash when the tablet's plugged in. (I get a black screen if I try to boot the OS with the tablet plugged in.) I thought we didn't need the frankenpatch anymore?

EDIT THE SEQUEL : So there's a slight chance the module wasn't auto-loading upon reboot during the first attempt, according to the mailing list. WTF, this potential snag was not mentioned in the How-to. I need to try it if plugging in my tablet won't cause a system crash.

---

### Post by LillyDragon on 2013-12-29
After more attempts, it turns out my X server version was out of date. (I installed Ubuntu 12.04.1 instead of 12.04.2, so that may be why.) The installation of the drivers were easy once I wrapped my head around it, but without the frankenpatch, my screen gets turned off.

Thankfully, this also was easy to patch into xf86-input driver, just like the instructions say. For anybody with a newer version of Precise, this isn't necessary, but early bird ISOs of it do need it, and it works like a charm! To make sure the drivers auto-load, I also added "wacom" (Without the quotations.) to the end of /etc/modules to be on the safe side.

So I'm posting in this thread as thanks to Favux for providing that massive, but resourceful wall of text on the Linux Mint forums! I am very happy to have my tablet fully working on both Windows and Linux. Even the rocker switches and eraser are working on the CTH-480. I couldn't be happier to fully migrate to an fully-Ubuntu hard drive.

---

### Post by jasonadamlong on 2013-12-31
> **johnluke728 said:**
> I hate bumping the topic, but I've been trying to wrap my head around installing the drivers myself for the past two days. (Recently got a CTH-480 and it worked great on Windows.)

I understand that the wacom.co is the actual driver, while the Xorg input driver acts as the medium between the drivers and the kernel. Both are important I can't skip installing either in the proper order. I am also glad the frankenpatch is no longer necessary after recent updates to 12.04 LTS kernels.

However, I was rather green during the process, and tried installing the xf64-input driver first. (Oops!) Thankfully, no harm has been done yet, I didn't compile and install the drivers because of a build error I was getting. I got all the dependencies necessary to compile, so I fear this might pose an obstacle once the input-wacom is compiled and installed.

```
checking for X11... no
configure: error: Package requirements (x11 xi xrandr xinerama) were not met:

No package 'xinerama' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables X11_CFLAGS
and X11_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

Either I'm missing X11, or Ubuntu has put it somewhere else. My head hurts at the prospect of the latter, Ubuntu has done some non-standard arrangements in the past before.


Hi John Luke, 

I received the exact same error message as above, but I can't find the line in the LinuxMint forum which refers to those missing dependencies. Can you point me in the right direction? 

Thanks,

Jason

---

### Post by LillyDragon on 2014-01-01
The Linux Mint thread is a lot to sift through. :P I think I needed a good two days to let it all sink in, but it was worth it!

Anyway, this is the line you were looking for. It's very easy to get the dependencies you are missing :

```
sudo apt-get update

sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libncurses5-dev autoconf libtool
```

Don't forget to check which version of X you're using as well, because whether or not you need the frankenpatch depends on it. Simply type this into the terminal.

```
X -version
```

If your X version is 1.13 or above, you don't need it, just compile xf86-input as-is and you're good to go. :) If you have an older version, you'll need to apply the patch to xf86-input's source before compiling, otherwise X will crash when the tablet is plugged in.

---

### Post by jasonadamlong on 2014-01-01
Thank you! 

Jason

---

### Post by scu on 2014-04-03
I'm currently very confused about the installation process of CTH480. Gnome-control-center doesnt recognize the tablet and lsmod doesnt show wacom module. Lsusb shows wacom.

Ubuntu 10.04 and later should include xf86-input-wacom and a properly patched kernel out of the box. Xserver-xorg-input-wacom 0.20.0 is available and installed from repository, kernel version is 3.11 and X.Org X Server version is 1.14.5. Should I still be installing or enabling something?

---

