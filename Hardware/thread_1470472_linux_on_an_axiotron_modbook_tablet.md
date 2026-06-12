---
title: "linux on an axiotron modbook tablet"
date: 2010-05-02
forum: Hardware
---

### Post by Sam~ on 2010-05-02
Hello
Been switching between Fedora and Ubuntu every release over the  last few years, but I think 10.04 has impressed me enough to keep me on  Ubuntu for a while--excellent release!
I've got everything working  on my macbook (and got the power consumption down from 17W to 12W thanks  to this forum), and I was impressed enough to give things a try on my  Axtiotron Modbook.
The Modbook is sort of a hackjob, a plastic  macbook that has had its screen and keyboard removed and replaced by a  custom-made case with a wacom tablet behind the new screen, turning it  into a slate tablet mac.  [http://axiotron.com](http://axiotron.com)
I've been trying  without success to get Linux working on the modbook since about Fedora  9, three years ago.  The install goes fine, just as it would on a  regular macbook, but since this is a slate tablet there is no built in  keyboard or mouse--it's rather important that the tablet bit works, else  my only input with the machine is the power button, which is less than  opportune.
The tablet is not detected at all by Ubuntu as far as I  can figure out, I believe it could have something to do with the  internal USB hub the tablet is connected to (viewing the tablet in OS  X's system profiler reveals a bit of a mess of USB hubs plugged into USB  hubs), but I don't know where to start or what to look for.  Does  anyone have experience setting up a wacom tablet on the more modern  versions of the wacom driver?  Most things I can find just tell me the  tablet will be automatically detected, which isn't happening.  Thanks in  advance, I hope to bring years of trying to an end on this install!

---

### Post by Favux on 2010-05-02
Hi Sam~,

Welcome to Ubuntu forums!

I've got a little experience installing linuxwacom.  I thought the modbook was extremely cool and toyed with getting one.

You can plug in a usb keyboard, correct?

If so let's start with, in a terminal:
```
lsusb
```
and
```
lspci
```
and
```
lsmod | grep [Ww]acom
```
and
```
dmesg | grep [Ww]acom
```
and
```
modinfo -n wacom
```

You are right and the usb hubs could mess us up.  I gather that it's a usb Wacom digitizer, not a serial one then?

Hope I can help.

---

### Post by Sam~ on 2010-05-03
Thanks for the reply.  The wacom board is connected through USB, though it uses a custom controller Axiotron appears to have produced itself, which might cause problems.  But I'll worry about that later--made some progress with your help already!

lsusb returns
```
Bus 007 Device 002: ID 05ac:8242 Apple, Inc. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 006: ID 05ac:8205 Apple, Inc. Bluetooth HCI
Bus 003 Device 005: ID 05ac:020b Apple, Inc. Pro Keyboard [Mitsumi, A1048/US layout]
Bus 003 Device 004: ID 05ac:0304 Apple, Inc. Optical USB Mouse [Mitsumi]
Bus 003 Device 003: ID 05ac:1003 Apple, Inc. Hub in Pro Keyboard [Mitsumi, A1048]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 056a:0097 Wacom Co., Ltd 
Bus 002 Device 004: ID 1bf7:1a76  
Bus 002 Device 002: ID 05ac:8501 Apple, Inc. Built-in iSight [Micron]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

This is the first confirmation I've received that a wacom device is even connected under Linux (whee!).  

I understand the output of lspci a bit less, but here it is:
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 04)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
02:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller (rev 13)
04:03.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 61)
```

lsmod | grep [Ww]acom and dmesg | grep [Ww]acom both return nothing.

modinfo -n wacom gives:
```
/lib/modules/2.6.32-21-generic/kernel/drivers/input/tablet/wacom.ko
```

(I remember looking for something like 056a:0097 last time I tried to get this to work, but I never found it and have since forgotten why I was looking for it.)
Hope this is good information.

---

### Post by Favux on 2010-05-03
Hi Sam~,

You are right, progress!

OK, the line:
```
Bus 002 Device 005: ID 056a:0097 Wacom Co., Ltd 

```
tells us the digitizer is seen, as you know.  056a is the Wacom Vendor ID and 0097 is the tablet/digitizer's Product ID.

The modinfo -n wacom command shows us the wacom.ko, the usb kernel driver/module is in the right directory.  But the blank lsmod | grep [Ww]acom shows that the wacom.ko is not auto-loading (as does dmesg).  This happens on some systems.  So you want to add 'wacom', without the quotes, to the bottom of the modules list in /etc/.   That will "force" wacom.ko to load:
```
gksudo gedit /etc/modules
```
then reboot.

Fingers crossed.

---

### Post by Sam~ on 2010-05-03
Okay, I added wacom to the modules list.  No response to the pen, however I re-ran the commands that weren't giving a response earlier and they do bring up something now.

lsmod | grep [Ww]acom
```

[COLOR=Red]wacom[/COLOR]                  25044  0 

```

dmesg | grep [Ww]acom
```

[   13.173960] usbcore: registered new interface driver [COLOR=Red]wacom[/COLOR]
[   13.173963] [COLOR=Red]wacom[/COLOR]: v1.52:USB [COLOR=Red]Wacom[/COLOR] tablet driver

```

I also just discovered my ubuntu install has no xorg.conf (that's been replaced by automagic detection, I hear) so pretty much everything I knew about trying to get a tablet to work in linux is out the window.  Is there a clear direction to proceed from here?

---

### Post by Favux on 2010-05-03
Good, so now usb communication is established because the wacom.ko is loading.  That was the first hurdle.

The 10-wacom.conf should be at /usr/lib/X11/xorg.conf.d/:
```
gksudo gedit /usr/lib/X11/xorg.conf.d/10-wacom.conf
```
The first section/snippet should be the usb one.  Let's see what it looks like.

You might want to try telling Synaptic Package Manager to reinstall xserver-xorg-input-wacom and rebooting.

Also check and see if you have a "40-xserver-xorg-input-wacom.rules" at "/lib/udev/rules.d/".

What I've discovered is your digitizer, 0097 or 0x97, is not in the table.  It also is not listed in the source code in wcmUSB.c.  This may be the problem.  It is possible that the Linux Wacom Project (LWP) is not aware of your Axiotron Wacom digitizer Product ID and has not included it in the code.

---

### Post by Sam~ on 2010-05-03
10-wacom.conf looks like this:
```

Section "InputClass"
    Identifier "Wacom class"
    MatchProduct "Wacom|WACOM"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

Section "InputClass"
    Identifier "Wacom serial class"
    MatchProduct "Serial Wacom Tablet"
    Driver "wacom"
    Option "ForceDevice" "ISDV4"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
    Identifier "Wacom N-Trig class"
    MatchProduct "HID 1b96:0001"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

```

I've reinstalled xserver-xorg-input-wacom from synaptics, no difference.

I do not have a 40-xserver-xorg-input-wacom.rules file at /lib/undev/rules.d/

I was afraid the driver just wouldn't support the 13 inch digitizer, a while back I was searching for a part number to see if I could order one for a personal project and was unable to find a single computer besides the modbook that had a 13.3 inch widescreen wacom tablet--seems it is not a common component, possibly even custom made for Axiotron.  Things worked out of the box on a windows install without wacom's tabletpc driver however, so I'm holding on to hope that this could be a configuration issue.
Perhaps I should bring this issue up to the people in charge of the wacom-tools project?

---

### Post by Favux on 2010-05-03
The 10-wacom.conf.
> was unable to find a single computer besides the modbook that had a 13.3 inch widescreen wacom tablet--seems it is not a common component, possibly even custom made for Axiotron.
I think it is custom made for the Axiotron, and that's why the LWP is unaware of it.

We could try hacking the wcmUSB.c and see if that gets us anywhere.  I think your tablet doesn't have touch, correct?  It has a stylus, with two buttons?  And an eraser?  If so then the closet tablet to yours format in wcmUSB.c is:
```
	{ 0x90, 2540, 2540, &usbTabletPC   }, /* TabletPC 0x90 */ 
```
and the udev rule in 40-xserver-xorg-input-wacom.rules looks like:
```
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0090", SYMLINK="input/tablet-tpc90"
```
If you know the resolution we could add a similar line to wcmUSB.c to the source code from a clone from the xf86-input-wacom and then compile it and see if that gets us anywhere.
> Perhaps I should bring this issue up to the people in charge of the wacom-tools project? 
That's what we may need to do.  Post all the details, technical and otherwise on [linuxwacom-discuss]("https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss") and see if Peter Hutterer will add it in a patch to xf86-input-wacom for you.  Then you could clone the git and Bob's your uncle.

---

### Post by toprowguywithfeet on 2011-02-27
The last post in this thread was a long time ago and it ended kinda abruptly.  Was a solution ever found?  I'd like to get Ubuntu fully working on my Modbook as well.

---

### Post by Favux on 2011-02-27
Hi toprowguywithfeet,

Welcome to Ubuntu forums!

Yeah, I guess he lost interest.  Let's see what product ID your digitizer is.  Also enter:
```
lsusb
```
in a terminal and post the Wacom line or output.

We can then check the code to see if support has been added.  If not I probably can help you add it in and if it works submit a patch for the Axiotron to the linuxwacom project.

To do that I would need to know what Axiotron says the resolution is, how many levels of pressure, screen dimensions, all that kind of stuff.

---

### Post by toprowguywithfeet on 2011-03-14
> **Favux said:**
> Hi toprowguywithfeet,

Welcome to Ubuntu forums!

Yeah, I guess he lost interest.  Let's see what product ID your digitizer is.  Also enter:
```
lsusb
```
in a terminal and post the Wacom line or output.

We can then check the code to see if support has been added.  If not I probably can help you add it in and if it works submit a patch for the Axiotron to the linuxwacom project.

To do that I would need to know what Axiotron says the resolution is, how many levels of pressure, screen dimensions, all that kind of stuff.

Thanks for the reply Favux!

I would have responded earlier, but I didn't receive a notification that you replied.

I will do that as soon as I get my new Modbook.  I upgraded to the most recent version and it's in the mail.  My next post will be the results of that command.  Thanks again!

---

### Post by toprowguywithfeet on 2011-03-20
I am going ahead and simply pasting the entirety of the output.  Here 'tis:

Bus 004 Device 003: ID 05ac:8215 Apple, Inc. Bluetooth USB Host Controller
Bus 004 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 05ac:8242 Apple, Inc. IR Receiver [built-in]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[B]Bus 001 Device 009: ID 056a:0097 Wacom Co., Ltd 
Bus 001 Device 008: ID 1bf7:1a77  
Bus 001 Device 007: ID 192f:0616 Avago Technologies, Pte. [/B]
Bus 001 Device 006: ID 05ac:0220 Apple, Inc. Aluminum Keyboard (ANSI)
Bus 001 Device 005: ID 1bf7:1a76  
Bus 001 Device 003: ID 05ac:8300 Apple, Inc. Built-in iSight (no firmware loaded)
Bus 001 Device 002: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

The highlighted lines seem out of the norm, but I am by no means versed in this.  It may prove a challenge just in getting me to understand what steps I need to take.  I really appreciate any help at all though!

---

### Post by Favux on 2011-03-20
Alright, I checked and the 0x97 isn't in the code so we need to put it in before compiling the Wacom kernel and X drivers.  Did you install Maverick or some other Ubuntu release on the Modbook?

This line is what we needed:
```
Bus 001 Device 009: ID 056a:0097 Wacom Co., Ltd 
```
Vendor ID = 056a = Wacom
Product ID = 0097 = the Wacom digitizer Axiotron is using.

So now I need to know whatever technical specifications you have on the digitizer.  For example:
- Is it a 12.1 screen?
- How many pressure levels does it have?
- What's the resolution of the digitizer?
etc.
- Stylus plus eraser?
- How many side buttons on the stylus?
- Does it have touch?  If it does is it single finger or two finger touch?

---

### Post by jdonigan on 2011-03-28
Here's data from the Axiotron website:
13.3-inch 1280x800 screen

Wacom® Penabled® digitizer:

[LIST]
[*]Pressure sensing: 512 levels
[IMG]http://www.axiotron.com/fileadmin/templates/axt/img/spacer.gif[/IMG]
[*]Recognition resolution: 20x display resolution
[IMG]http://www.axiotron.com/fileadmin/templates/axt/img/spacer.gif[/IMG]
[*]Recognition rate: 133 position updates per second
[/LIST]
Axiotron Digitizer Pen with two programmable side buttons, digital eraser

(no listing on touch)

Hope this helps!

---

### Post by Favux on 2011-03-28
Hi jdonigan,

Welcome to Ubuntu forums!

Thanks!  Other than having double the pressure levels of most tablet PCs and being 13.3 rather than 12.1 everything else looks roughly the same.  So with any luck adding it should be easy enough.  If I'm wrong on a guess or two shouldn't be hard to tweak it.

Are you interested in trying?

---

### Post by Favux on 2011-03-28
OK, let's first work on the usb kernel driver wacom.ko.

Since linuxwacom is in maintenance I suppose it makes the most sense to use input wacom.  Input-wacom should work for either Lucid or Maverick.  Let me know which release you are using.

Use the alternate Section 1 in the [linuxwacom HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949") to compile input-wacom-0.10-11.  After you've unpacked the downloaded tar stop and do the following.

Go into the input-wacom-0.10.11/2.6.30 folder and open the wacom_wac.c file and at line 1437 add/enter these two lines:
```

static const struct wacom_features wacom_features_0x97 =
	{ "Wacom ISDv4 93",       WACOM_PKGLEN_GRAPHIRE,  26202, 16325,  511,  0, TABLETPC };

```
Make sure your identation is the same as the code's, that's important.  You're inserting it between two lines so the finish product looks like:
```

static const struct wacom_features wacom_features_0x93 =
	{ "Wacom ISDv4 93",       WACOM_PKGLEN_GRAPHIRE,  26202, 16325,  255,  0, TABLETPC };
static const struct wacom_features wacom_features_0x97 =
	{ "Wacom ISDv4 93",       WACOM_PKGLEN_GRAPHIRE,  26202, 16325,  511,  0, TABLETPC };
static const struct wacom_features wacom_features_0x9A =
	{ "Wacom ISDv4 9A",       WACOM_PKGLEN_GRAPHIRE,  26202, 16325,  255,  0, TABLETPC };

```
With gedit to enable the line numbers go to Edit > Preferences > and check the box in front of 'Display line numbers' in the View tab.

Next go to line 1533 (was 1531) and add this line:
```
	{ USB_DEVICE_WACOM(0x97) },
```
so it looks like:
```

	{ USB_DEVICE_WACOM(0x93) },
	{ USB_DEVICE_WACOM(0x97) },
	{ USB_DEVICE_WACOM(0x9A) },

```
Save your changes.  That should take care of the wacom.ko.  Go ahead and finish compiling and installing it.  That just leaves the X driver.

---

### Post by toprowguywithfeet on 2011-04-06
Okay, I think I did everything as you instructed.

I am using the very latest Ubuntu distro, Maverick w/ all updates.

What do I have to do with the x driver?

---

### Post by Favux on 2011-04-06
Hi toprowguywithfeet,

Alrighty.

Now use part II. of the [Bamboo Pen and Touch HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") to clone xf86-input-wacom (the X driver).  Before you run the line:
```
./autogen.sh --prefix=/usr
```
go into the xf86-input-wacom folder into the /src directory.  Open the wcmUSB.c file in a text editor and after line #267 add this line:
```
	{ WACOM_VENDOR_ID, 0x97, 100000, 100000, &usbTabletPC   }, /* TabletPC 0x97 */
```
so it looks like:
```
	{ WACOM_VENDOR_ID, 0x93, 100000, 100000, &usbTabletPC   }, /* TabletPC 0x93 */
	{ WACOM_VENDOR_ID, 0x97, 100000, 100000, &usbTabletPC   }, /* TabletPC 0x97 */
	{ WACOM_VENDOR_ID, 0x9A, 100000, 100000, &usbTabletPC   }, /* TabletPC 0x9A */
```
Save and close that file and open the wcmValidateDevice.c file.  After line # 261 add this line:
```
		case 0x97: /* TPC */
```
so it looks like:
```
		case 0x93: /* TPC with 1FGT */
		case 0x97: /* TPC */
		case 0x9A: /* TPC with 1FGT */
		case 0x90: /* TPC */
```
Then finish compling by running the configure line etc. and rebooting.

With luck it should be working.

---

### Post by toprowguywithfeet on 2011-04-10
IT WORKED!!  :KS

YOU SIR ARE AMAZING!! :popcorn:

Now, am I able to delete the folders on my desktop?

I'm going to try it out in some drawing programs and report back.  It doesn't seem to need calibration, but if that ever becomes an issue, what options are there?

I was going to attached the terminal output for the entire process so others can duplicate the results, or use it for comparison, but I keep getting invalid file.  It's just a text edit doc.

Truly, awesome work.  Is there a way to donate to you Favux?  :D

---

### Post by Favux on 2011-04-10
Hi toprowguywithfeet,

Outstanding!  Nice work.  :)

Before I submit patches to add support for it the the linux wacom project I need a few things.  For some diagnostics can you post the output of the following commands in a terminal:
```
xinput list
```
and
```
xsetwacom list
```
Also attach to your next post your Xorg.0.log in /var/log.  Because it is a big file you can compress it by right clicking on it and chose Create Archive.  Then use Manage Attachments below to attach it.

> Now, am I able to delete the folders on my desktop?

Yes, but I wouldn't, especially the input-wacom folder.  Move the folders into your /home/yourusername folder.  With a kernel update the usb kernel driver from input-wacom will seem to break.  What happens is the new kernel has a new modules directory which has the old non-working (as far as you are concerned) wacom.ko.  So you need to recompile it from your patched input-wacom folder.  That will take just a couple of minutes.  No reason to re-download input-wacom and repatch now that you've already done it.
> I'm going to try it out in some drawing programs and report back.

Please do.  I'm especially interested in Pressure in Gimp etc.  As you know the modbook apparently has twice the pressure levels of other tablets and I'd like to verify it is working.  That's something the Xorg.0.log will help with too.
> I was going to attached the terminal output for the entire process so others can duplicate the results, or use it for comparison, but I keep getting invalid file. It's just a text edit doc.
In Manage Attachments it will tell you what file types are acceptable to upload to the forums.  For example .txt should be OK.
> It doesn't seem to need calibration, but if that ever becomes an issue, what options are there?
Sure.  Both HOW TOs I linked you to have stuff on configuration.  See also the linux wacom project's mediawiki HOW TO page:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)

---

### Post by toprowguywithfeet on 2011-05-13
Hello Favux!

Don't know if I need to apologize, but I fell bad for being away for a while in the middle of trying to get this working.  Life came up, you know how it goes I'm sure.  During that time I wasn't able to try out the programs with the pen functioning.

And now . . . we have a new problem . . .

Next time I booted Ubuntu up, I was offered the chance to upgrade to 11.04.  I usually never hesitate to upgrade because of potential security fixes and this time was no different.  I didn't think about the upgrade breaking the progress we had made.

So now what?

---

### Post by Favux on 2011-05-13
Hi again toprowguywithfeet,

Sure, I know how that goes.

Unfortunately with no diagnostics/feedback from you or anyone else I couldn't submit patches to the Linux Wacom Project's xf86-input-wacom or input-wacom.  And of course not the the kernel's linux-input either.  Another thing that is useful is the tester's name and e-mail so I can put a tested-by in the patches.  More likely they'll take them then.  You can PM me that info. if you don't want to broadcast it.

I don't even know if the window for xf86-input-wacom-0.11.0 was still open, but whatever, we missed it.

Now regarding Natty we have a wee bit of a problem.  Starting with the 2.6.37 the usb kernel stuff, i.e. wacom.ko, goes to linux input.  Linuxwacom is in maintainance and input-wacom won't compile on 2.6.37 and up.  So unless we use the kernel I don't know how to add your model to the wacom.wac.c code.  So one of us needs to figure out how you can just get and compile the Wacom module (wacom.ko) from the 2.6.38 kernel Natty uses.  I know how to retrieve the linux-input git repository so that's part of the process.  But I think last time I looked that was broken and I couldn't do a *git pull*.  If so I have to see if I can resync it.  I think it might be from them not accepting a patch until it was resubmitted.

Any way figuring that out is on my my to do list.

So Lucid and Maverick, yes.  Natty, not so much.

---

### Post by Favux on 2011-05-17
Hi toprowguywithfeet,

Luckily I have a friend who knows more than I do.  After talking it over with him it looks doable.  Not the cleanest maybe but not too bad.  I'll check it out in a bit and see if it works.  Basically you end up compiling all of the Ubuntu kernel modules rather than just the wacom.ko and then copy your new wacom.ko into place.  So not nearly as bad as I feared.

---

### Post by Favux on 2011-05-18
Alright for Natty here it goes.

First download your current Natty kernel's Ubuntu source code onto your Desktop.
```
cd Desktop

apt-get source linux-image-`uname -r`
```
The kernel is about 94 MB and takes a few minutes to download depending on your connection.  You'll see linux_2.6.38.orig.tar.gz, linux_2.6.38-8.42.dsc, linux_2.6.38-8.42.diff.gz, and linux-2.6.38.

Then go into the kernel's folder (linux-2.6.38 ) and navigate to drivers/input/tablet/wacom_wac.c using Places/Nautilus.  Right click on wacom_wac.c and make the changes in the wacom_wac.c file as before in [post #16]("http://ubuntuforums.org/showpost.php?p=10612956&postcount=16").  Except the first two lines are inserted at line #1426 and the third line at line #1544 (was 1542).  Then in the terminal navigate to the same directory using:
```
cd linux-2.6.38/drivers/input/tablet
```
Then compile it with:
```
make -C/lib/modules/`uname -r`/build M=`pwd` modules

```
You may have to install the gcc compiler if you haven't already.

Copy the newly compiled wacom.ko from the current tablet directory into your system's kernel tablet directory with:
```
sudo cp wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/
```
Rebuild all of the module dependencies:
```
sudo depmod -a
```
Then reboot.

Then follow post #18 for the xf86-input-wacom changes.  Good luck.  :)

---

### Post by Favux on 2011-05-24
Well what do you know?  It turns out input-wacom does compile on the 2.6.38 kernel after all.  Last I heard it only compiled on 2.6.36 and I didn't hear of anything to make it work with 2.6.38.  And according to some Arch folks it compiles on 2.6.39 also.

So you can use input-wacom as before.  Although it is probably more technically correct to use the Ubuntu 2.6.38 wacom.ko source code wacom_wac.c.

---

