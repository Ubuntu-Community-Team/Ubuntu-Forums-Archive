---
title: "Boot with liveCD fails on thinkpad T20"
date: 2006-10-28
forum: Hardware &amp; Laptops
---

### Post by qriopal on 2006-10-28
I am trying to install Xubuntu Edgy Eft on Thinkpad T20 with 128mb RAM but it hangs up after I get the following message during booting with the liveCD:

"[ 126.547156] piix4_smbus 0000:00:07.3: IBM Laptop detected, may corrupt your serial eeprom Refusing to load module

* Activating swap...
mount: Function not implemented

* Checking file system...
fsck 1.39 (29-May-2006)

_"

Any Idea what the problem maybe? I tried to boot using this CD several times on this machine and every time the computer hangs up right after the above message during booting. I also tried acpi=off as a boot code. The liveCD is working fine when used on my desktop with 512mb RAM.

Hope someone can let me know what the problem might be.

---

### Post by meng on 2006-10-28
LiveCD is not recommended for systems below 192MB RAM. Sometimes even 192MB is not enough. Would recommend downloading, burning and installing from the Alternate CD.

---

### Post by qriopal on 2006-10-28
Thanks. I will upgrade my RAM to 256MB soon and try it again. But the message regarding corrupting serial eeprom...what should I do about it? Will that not happen when I install it with upgraded RAM?

"may corrupt your serial eeprom | Refusing to load module"

---

### Post by meng on 2006-10-28
A good point, and I don't know. But if Ubuntu fails, there are other Linux distros.

---

### Post by qriopal on 2006-10-30
Thanks Meng. 

So you mean to say that there is no way of getting around this problem? Thats too unfortunate. I like Xubuntu very much and would like to use it for my upgraded laptop.

---

### Post by qriopal on 2006-10-31
Ok...I gave up on XUbuntu. I upgraded my ram to 384MB and I get the same warning about corrupting my serial EEPROM because of which it does not load module. 

This happens with Ubuntu 6.06 CD and Xubuntu 6.10 CD but it does not happen with Ubunty 5.10 live CD....just so that the developers know about this and try to fix it in the subsequent releases. Ubuntu 5.1 liveCD boots and works fine on this same laptop. 

I finally found BeaFanatIX2006.2-beta6 which they claim is based on Ubuntu which I could successfully install on my Thinkpad. It is working fine so far.

---

### Post by mattotoole on 2006-11-04
I get the same message with my T20.  I think it has something to do with an old BIOS that Edgy doesn't officially support, but it doesn't seem to be an issue.

I have 384MB.

The problem for me is getting the video running in anything but safe mode, as well as the wifi networking.  So I'm still running 5.10.

FWIW, Mepis 6.0, supposedly based on Ubuntu 6.x, works fine on my T20.  I prefer the Gnome desktop though, and Mepis uses KDE.

I'm puzzled by Ubuntu's problems with T-Series Thinkpads, which have a reputation for being Linux-friendly, and are as common as dirt.

---

### Post by po0f on 2006-11-04
I've a T22 and also get that message.  Nothing happens because guess what?  The module doesn't get loaded.  That is just the kernel's way of telling you that it *didn't* do something bad.  And as an aside, this would be a problem on other distros as well, if they bothered compiling the IBM Thinkpad modules for their kernels.

---

### Post by drseuk on 2006-11-08
I've just installed Ubuntu 6.10 on my Thinkpad T20 without problems (except it coughed a bit on the very first boot after install). I only have 128Mb of RAM in it. I used the alternate 6.10 i386 distribution.

OpenGL accelarated rendering works great with Planet Penguin racer. the other mission-critical application, ahem, GL testing software, I need (a.k.a., TuxKart) seems to struggle with the default level for some strange reason. Let me know if you need the xorg.conf.

DVDs play nice once you've added all the totem-xine plugins etc..

Eclipse, being the resource hog that it is (~123Mb just to start), works but only with massive swapping (which effectively makes it unusable). As reported elsewhere, Sun Java works better (and faster) than gcj at the moment.


If only Gnome could e.g., have a System Resource Monitor that itself doesn't use 6Mb to run ](*,)

---

