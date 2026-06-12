---
title: "I need help with install - ( initramfs) error"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by abzerov on 2009-08-19
Hello, I installed 9.04 on my desktop and it worked perfectly I am hooked !
 
 I would like to do a single install of 9.04:
 
Then I tried to install on laptop hp pavilion zv5000 and I have been having problems.
I am starting with fresh install of windows xp home edition version 2002 service pack 1. I have installed updated BIOS . It is Pentium 4 cpu 2.66Ghz  384MB ram. Chipset AT: Radeon 9100 1GP:FSB:133
 
Error I am getting is MP-Bios bug: 8254 timer not connected to IO-APIC .
Could not load library files no such directory then it goes to (Initramfs) and stops.
I have tried doing different boot parameters . Am I doing these incorrectly ? Do I need to erase quiet splash then add noapci....  i think I have tried all of this in many different ways and believe I have exhausted this approach? I appreciate your help !

---

### Post by jerrrys on 2009-08-19
doesn't seem to be one fix for all

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/283489](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/283489)

---

### Post by gonnoc on 2009-08-20
Hi,
I'll relate my experiences here - seems as good as anywhere and lets hope it helps you out.
I was getting the same error and I checked the web and found all sorts of suggestions. All of the noapic, acpi=off pci=noapic, etc... options in the kernel statement didn't work.

What has worked for me is a combination of two things firstly include in the grub kernel statement options rootdelay=60 (may need to specify >60 say 180?). I suspect that this actually fixed (got over) my 8254 but I was also getting I SUSPECT but I don't know for sure some sort of splash screen error that was causing the boot to crash. I assume this because when I removed the 'splash' option from the kernel statement in grub the machine (an old Dell 1650 server) booted up - I still received my 8254 error but ubuntu seemed to get over it and booted up. 
So my kernel statement in grub goes something like

kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=xxxxxxxxxxx rootdelay=60 ro quiet

I'm pretty much a linux newbie so if someone out there can confirm the splash option does actually display the ubuntu splash screen it'd be much appreciated.
Hope this helps

---

### Post by abzerov on 2009-08-20
Thanks for your help. I may try to edit grub kernel statement options rootdelay=60 (may need to specify >60 say 180?) like you mentioned.  I am so new I need to learn how to do this.  I love learning new things but would appreciate pointers as to how to do this. Thanks again!          abzerov

---

