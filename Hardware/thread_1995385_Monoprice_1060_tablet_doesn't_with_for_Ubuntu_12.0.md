---
title: "Monoprice 1060 tablet doesn't with for Ubuntu 12.04"
date: 2012-06-03
forum: Hardware
---

### Post by makechanges on 2012-06-03
Hello,

I'm trying to get my Monoprice 1060-HA60 tablet to work with Ubuntu 12.04 and am not having any luck finding anything that is helpful. Does anyone have any suggestions for me? 

Thanks,

Ben

---

### Post by Bucky Ball on 2012-06-03
1/ Your thread title doesn't really make a lot of sense;
2/ You haven't really told us what it is that you are having problems with.

Please be more specific and help us to help you. What exactly can't you get working??? ;)

---

### Post by Favux on 2012-06-03
Hi makechanges/Ben,

Welcome to Ubuntu forums!


Your Monoprice 1060-HA60 tablet is likely a re-branded UC-Logic tablet.  We need to find out which one to determine if it is supported.  Open up a terminal and type:
```
lsusb
```
and hit enter.

Post the output.  In it will be the tablet line, if you have the tablet plugged in, that will tell us the product ID (PID).

---

### Post by makechanges on 2012-06-04
Sorry about the title of the message, had meant to say my tablet isn't 
'working' with ubuntu 12.04. 

When I plug in the tablet I get some response, but the tablet doesn't function in any usable way. 

In Natilus, touching the stylus to the tablet  moves the window up one directory and clicking the first button moves  down one directory. 

In Inkscape, I think the tablet is showing up as an input device named HA605, but selecting it  as an input device doesn't affect the tablets interaction with 12.04. 

The Wacom Graphics Tablet application doesn't recognize it.

The output of lsusb is:
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 064e:d104 Suyin Corp. 
Bus 005 Device 002: ID 5543:0781 UC-Logic Technology Corp.

Thanks a bunch for your help.

---

### Post by Favux on 2012-06-04
It is a UC-Logic like I suspected:
> Bus 005 Device 002: ID 5543:0781 UC-Logic Technology Corp.
But a new one.
ID 5543:0781
Vendor ID = 5543 = UC-Logic
Product ID = 0781
It does not appear to be supported as of yet:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)  I do not even know if the DIGI*mend* project is aware of this new model.

What is needed for support for a new model is to follow the instructions here:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Collecting_tablet_diagnostics](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Collecting_tablet_diagnostics)

Nick then has the information needed to write a kernel driver for the tablet.

We could try a few more things like looking at your Xorg.0.log in /var/log.  But without the proper kernel driver we likely won't get far in getting it to function.

---

### Post by IReadTheManual on 2013-02-18
Any luck with this? I too have one of these tablets, assuming the tablet is this one: [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=UC-Logic_Tablet_TWHA60](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=UC-Logic_Tablet_TWHA60).

I used to have an older 'UC-Logic Technology Corp.' tablet, the "Genius Mouse/Pen 8x6" so I was surprised when this one arrived and support was missing.

Please see [http://thread.gmane.org/gmane.linux.kernel.input/26544](http://thread.gmane.org/gmane.linux.kernel.input/26544) for the patch post which *should be part of kernel 3.7. I have 3.5 and not yet upgraded. I will try after I backup. It looks like 3.7 was released in a couple of months ago in December, [http://linux.slashdot.org/story/12/12/11/160259/linux-37-released](http://linux.slashdot.org/story/12/12/11/160259/linux-37-released).  There is also more information about various Digimend tablet support located here: [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status).

I have not tried this tablet on a Mac yet, but I have tried it on Windows. Please note WinXP does support the mouse part of this tablet without drivers (pressure-sensitivity requires the XP drivers).

---

### Post by Favux on 2013-02-18
Support is also in the latest [kernel patchset]("http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Kernel_patches") so you should be able to backport it without having to update the entire kernel:  [http://digimend.git.sourceforge.net/git/gitweb.cgi?p=digimend/kernel-patches.git;a=blob_plain;f=COMPATIBILITY;hb=v6](http://digimend.git.sourceforge.net/git/gitweb.cgi?p=digimend/kernel-patches.git;a=blob_plain;f=COMPATIBILITY;hb=v6)

---

### Post by IReadTheManual on 2013-02-19
@Favux: I'm not quite sure how to do that.

I tried linux-image-3.7.9-030709-generic_3.7.9-030709.201302171607_i386.deb found here [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/), but along with the expected low graphics and absent wifi, it did not properly handle the drawing tablet.

That said, ***lsusb*** reports the following from both ***3.5* **and** *3.7.9*:**
```
Bus 003 Device 002: ID 5543:0781 UC-Logic Technology Corp
```I should note that it appears as though there are multiple types of tablets with various power requirements and button features which all report as usb chipset 5543:0781. My specific one, which I assume is the same for the OP is the "Monoprice 10x6.25 inches Graphic Drawing TABLET w/8 Hot Keys", which takes +5V (USB) and is listed as model #: "160-HA60-990". It registers in VirtualBox (using the linux that doesn't recognize it as host) as `HA60` which on pass-through mode WindowsXP correctly detects.

My installed xserver ***evdev*** version is ***1:2.7.3-0ubuntu2** , *so I'm not quite sure why it isn't working at all. Evdev is supposed to work with this tablet for versions greater than or equal to [I]**2.5.99**.

[/I]Should I start getting diagnostics as described here?: i[URL="http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Collecting_tablet_diagnostics"]http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Collecting_tablet_diagnostics. 
[/URL]

---

### Post by Favux on 2013-02-19
Have you looked at this HOW TO?  [http://ubuntuforums.org/showthread.php?t=1946486](http://ubuntuforums.org/showthread.php?t=1946486)

Admittedly because we can no longer update our tutorials it is for patchset 5 not 6,  But it should give you the idea on what to do.  Anyway I thought this would be a little simpler way to go.  Unfortunately with HID modules not as simple as is could/should be.

Yes, I saw where Nick says there are two power variants.  Not totally clear to me if he has them both working.

---

### Post by IReadTheManual on 2013-02-20
I grabbed fedora18 - [Design-suite]("http://spins.fedoraproject.org/design-suite/")  spin, thinking that it had 3.7 in it, but on boot found it was 3.6 - as  would be expected with 3.6 it did not recognize the tablet.

I am currently installing today's daily build of Ubuntu 13.04 (Pre-Release of Raring Ringtail) in a VM: [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/).  It seems to run fine with mypaint. I haven't tested all the buttons,  but pressure and location work which is what I care about. 

Krita does not work however, and I believe this is caused by a bug in Qt. I  think this link might lead to figuring out how to make it work: [http://forum.kde.org/viewtopic.php?f=139&t=98347](http://forum.kde.org/viewtopic.php?f=139&t=98347) .

---

### Post by Favux on 2013-02-20
> **IReadTheManual said:**
> 
I am currently installing today's daily build of Ubuntu 13.04 (Pre-Release of Raring Ringtail) in a VM: [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/).  It seems to run fine with mypaint. I haven't tested all the buttons,  but pressure and location work which is what I care about. 
Good.  So your tablet is supported.  It is the high power one, correct?
> **IReadTheManual said:**
> 
Krita does not work however, and I believe this is caused by a bug in Qt. I  think this link might lead to figuring out how to make it work: [http://forum.kde.org/viewtopic.php?f=139&t=98347](http://forum.kde.org/viewtopic.php?f=139&t=98347) .
Viktoria S.'s fix should work.  More interesting to me is why there is no activity from the Qt dev.s on the bug report.  This seems like an obvious bug with a simple fix.  It seems silly not to be compatible with the evdev driver.  Unless a true fix is far more invasive than it would appear.

Have they fixed the problem and the bug report just isn't the place to look?  That's what I'd like to know.

---

