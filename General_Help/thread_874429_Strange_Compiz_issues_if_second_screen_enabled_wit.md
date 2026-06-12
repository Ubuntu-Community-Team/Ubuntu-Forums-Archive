---
title: "Strange Compiz issues if second screen enabled with Nvidia card"
date: 2008-07-29
forum: General Help
---

### Post by John C. Wright on 2008-07-29
Hello. I'm rather new here -- if there's a better place to address this, or if I haven't provided the right information, please let me know.

I have a problem with Compiz, which works great unless I enable my second display. I do the latter simply by using the 'NVIDIA X Server Settings' gui. I configure it as a separate X screen, with a different resolution.

If I do this, the primary display becomes unusable. Rather subtly so, because there is a delay of half a second, sometimes more, to open any new window or display a menu (including Applications/Places/System). However, effects from Wobbly Windows to Desktop Cube continue to function normally. The second display appears to be free of issues.

If I disable compiz, everything is fine (though rather boring).

It's likely to be a thorny problem, so I'd appreciate any help with potential workarounds, including somehow running a completely separate X display on the second screen, if possible.

Below are all of the relevant details that I could think of:

The hardware:
(--) PCI:*(1:0:0) nVidia Corporation G70 [GeForce 7600 GS] rev 161, Mem @ 0xfd000000/24, 0xc0000000/28, 0xfc000000/24, I/O @ 0x8c00/7, BIOS @ 0xfe7e0000/17
The primary screen is a generic flat panel connected via DVI. The second screen is a 16:9 aspect LCD projector connected via HD15.
The system is an Asus P5B Deluxe board, Intel Core 2 Duo 6600. The card is MSI-branded.

The software:
Ubuntu 8.04.1 - fresh install + updates
compiz 0.7.4
Linux mooby 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux
ii  nvidia-glx-new 169.12+2.6.24. NVIDIA binary XFree86 4.x/X.Org 'new' driver
ii  nvidia-kernel- 20051028+1ubun NVIDIA binary kernel module common files

Interestingly, the X log file says:
This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
...X.Org X Server 1.4.0.90
Release Date: 5 September 2007
The entire log file is attached.

The configuration has been tampered with minimally since fresh install, simply using the provided tools -- Appearance (under Preferences), Nvidia X Server Settings and simple-ccsm (except that this behavior is observed even prior to installing and using the latter). The only thing I've had to do manually was to add
/etc/X11/xorg.conf:    Option         "UseDisplayDevice" "DFP"

This is to prevent the nvidia driver from giving the '0' screen to the analog screen over the digital, which it does regardless of which plug is labeled 0 and 1 on the card.

Oh, I'll attach the X

That's all I can think of. If you know anything about this, please help! :-)

---

### Post by jakommo on 2008-08-09
Hi John,

I got the same Problem, I've configured (using nvidia-settings) my TV as second display with Seperate X because its FullHD and my monitor is only 1650x1080 and Twinview doesnt work right when you use different resolutions.

I first encountered this behavior some month ago under gentoo and was thinking its because I installed compiz from an unstabe overlay. So I decided to install ubuntu on another partition and used it quite a while. Some days ago I switched on the TV under ubuntu as well and now the Problem is also on my ubuntu installation.
As I found your post I booted back to gentoo and switched of the second screen and now its working without the delay.

At work I use ubuntu with two 19" monitors running twinview (also configured with nvidia-settings) and also compiz enabled and the problem doesn't appear there.

I use a nvidia 8800gts512 (at home) and a nvidia 8500 (at work).

Some Data:
Ubuntu 8.04 latest updates

gentoo:
xserver 1.3.0.0-r6
nvidia-drivers 173.14.09
kernel 2.6.25-gentoo-r6

greez

jakommo

---

