---
title: "cannot boot 7.10 kubuntu, Averatec 3270 w/viachrome video"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by revdjenk on 2007-10-21
First, don't know if gutsy liveCD is trying to load compbiz/beryl, but I know that my viachrome video will NOT do OpenGL...

Second, I have tried defining video resolution for boot, and the 'safe video mode', but either blank dark screen or the boot process attempts at starting video but each resetting ends up going through this pattern:
blue screen
dark screen with X cursor
blue screen with arrow cursor
then primarily scarlet and white pixeled screen blinking at about 1/2 second cycle

...have let this go about ten repeats, but never gets to desktop or startup screen.

BTW running PCLinuxOS at 1028X768 X 24bits resolution currently. 
7.04 kubuntu liveCD started with no problem...

God Bless
Doug

---

### Post by cdean on 2007-12-18
I'm having this same problem, too. I had Feisty installed and upgraded to Gutsy with apt, but I've managed to munge the desktop hardcore, and it takes forever to boot.

I've tried booting from Xubuntu, Ubuntu, and Kubuntu CDs, with very little luck.

I did have a modicum of success when I hit F6 and removed 'quiet splash --' from the kernel command line and added 'xforcevesa pci=noacpi' but then I still have issues with X. 

There's a reserve command to use, too, but I've not had to use it since Edgy: 'reserve=0x1e000000,0x20000000'.

I'm going to try a few other Ubuntu-based distros before I try Knoppix or others. IIRC I have gOS downloaded somewhere.

I don't know to what the problem is related. Nothing out-of-the-ordinary shows in the kernel scroll, EXCEPT *one* boot, I got a series of messages from powernowd-k8 about it not being able to change the processor speed. I've not been able to reproduce it, though.

I'd love to supply a dmesg, but I've not been able to get it interactive yet.

Any ideas, folks?

---

### Post by cdean on 2008-02-28
The workaround I found was to use the netboot CD, install using the text-mode installer, and install ubuntu-desktop on the next reboot.

---

