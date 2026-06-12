---
title: "ubuntu boot disk freezes"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by kazneus on 2009-08-29
Hi
Im trying to install ubuntu on my new compaq 515 laptop because I'm sick of windows. I made a boot disk using a downloaded 64 bit version by creating a disk image with InfraRecorder as instructed in the, uh, instructions. The disk loads up the boot menu: try ubuntu without installing it, install ubuntu, check memmory, check disk for errors, etc... But whenever I choose any of the options, my computer freezes. What should I do? 

Many thanks

---

### Post by raymondh on 2009-08-29
Try the safe graphics mode (press F4) ... or an alternate install.

This is assuming that you have checked the system requirements vis-a-vis your hardware, as well as read the release notes or the compatibility list.

Good luck, back-up ;)

---

### Post by kazneus on 2009-08-29
just tried safe graphics mode with the same result. Any other ideas?

---

### Post by raymondh on 2009-08-29
Kindly verify the [MD5]("https://help.ubuntu.com/community/HowToMD5SUM") of the image.

Did you verify your machine with the compatibility list (it may give clues)

[https://wiki.ubuntu.com/HardwareSupport/](https://wiki.ubuntu.com/HardwareSupport/)
[http://ubuntuforums.org/showthread.php?t=2457](http://ubuntuforums.org/showthread.php?t=2457)

I have never used infrarecorder to burn the image.  I do know (and advocate) burning the iso image as slow as possible to minimize burning errors.

One option is also the alternate install method ... it's the same desktop, is text based instead of GUI.  This is more for low-end systems but, can be used as well for powerful systems.

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)
[https://help.ubuntu.com/community/BootOptions#Changing%20the%20CD%27s%20Default%20Boot%20Options](https://help.ubuntu.com/community/BootOptions#Changing%20the%20CD%27s%20Default%20Boot%20Options)

Back-up. Good luck.

---

### Post by currentresident on 2009-09-19
The 515 is supposed to be compatable with SUSE linux you could try that.

---

### Post by Peter Becker on 2009-10-01
I tried a Ubuntu 9.10 alpha 6 alternate AMD64 CD and a 8.10 i386 DVD, both hang once it is time to detect the network. The screen turns black and that's it.

The issue seems the WLAN chipset. If the WLAN device is turned off in the BIOS, the setup process continues.

According to [a thread on the OpenSuSE forums]("http://forums.opensuse.org/tech-news/420199-compaq-515-claims-suse-compatability.html"), the chipset requires a proprietary driver, which is available only with Novell SuSE. I'll investigate some more tomorrow or on the weekend, it is getting late here. I think I might file a bug, too -- even if the chipset is not supported crashing seems a bit rude to me.

---

### Post by Peter Becker on 2009-10-02
I managed to get everything running (actually: I haven't checked webcam or modem yet, but I don't really care about those).

The offending item is the Broadcom WLAN chipset, 14e4:4315. It is listed as "in progress" for the Broadcom OSS driver -- whatever that means. But it turns out Ubuntu offers you the proprietary driver if you manage to boot with an enabled WLAN chipset.

Here is what I did:

[LIST]
[*]turn the WLAN hardware off in the BIOS
[*]install an Ubuntu (I tried a 9.10 alpha6 AMD64 first, but that had other issues -- so I ended up with a 8.10 i386 as the next best thing lying around)
[*]blacklist the broadcom OSS drivers in /etc/modprobe.d/blacklist -- I added both "b43" and "ssb" to the blacklist, I suspect one of those would be sufficient, but I don't know which one
[*]turn the hardware back on in the BIOS
[*]reboot into Linux --> Ubuntu offers me a proprietary driver for the chipset via hardware manager
[*]activate the proprietary driver --> this results in another dead computer with a blank screen, but on the next reboot it seems all good
[/LIST]
I haven't tested it well yet, but I am downloading the 8.10->9.04 upgrade as I'm typing this and it is looking fine -- about 60% done at the speed I expect from our DSL line.

---

### Post by currentresident on 2009-10-02
I knew this was going to happen novell has become the new microsoft. The propritory broadcom drivers are contrary to the linux philosphy. I expect the only reason red flag linux works is broadcom is a japanese company. Do we really need all this nonsence HP buys laptops from oversees puts their name on them then sells them oversees. Without the HP and microsoft cuts the 515 would cost $229.

---

