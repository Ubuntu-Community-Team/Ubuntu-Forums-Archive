---
title: "Unable to boot using ati radeon 9250 PCI"
date: 2008-11-26
forum: General Help
---

### Post by Silenus on 2008-11-26
Specs:
1 Gb RAM
ATI Radeon 9250 PCI Video card
2.93Ghz CPU

When I try to use the ATI card for video output at boot I get a kernel panic error, stating failed to work with it, so I must revert to my old onboard Intel card. I have not been able to get help from anyone regarding this on the forums thus far, so help is appreciated, thank you.

---

### Post by cariboo on 2008-11-26
Can you boot up in recovery mode? If you can, at the menu select xfix and once it has finished select resume. This should get you to the desktop. I'm not sure if ATI still supports your video card, but you can try and see if there are any drivers for your video in System-->Administration-->Hardware Drivers.

Jim

---

### Post by Silenus on 2008-11-26
I've installed the drivers for it before, but never got it to work, not even in recovery.
I just tried agp=off and pci=nosort, got me to a login after some errors but never logged in because sbin wasnt mounting or something along those lines, said fsck failed check. Wouldn't even recognize sudo as a command.

---

### Post by Silenus on 2008-12-01
Bump for hopeful help.

---

### Post by nousernameavailable on 2008-12-30
I have a similar problem when using a ATI HD2400 Pro PCI. 
My mainboard is a d945gclf2 wich does not have a switch do disable the onboard graphics card in bios (I can only set the primary display adapter). 

When I try to install Ubuntu 8.04.1, 8.10, 8.10_64, 9.04 alpha 2 I keep getting the same error: some files could not be found, some segfaults and the cd stops booting.(I checked the cd first so it is not the cd). 
When I try to boot my old Ubuntu installation (before I installed the new graphics card) I get some segfaults and the system stops.

I have no idea what could cause the problem, I checked my ram and harddrive, my Windows install boots and detects the card so the card is installed correct.

If anyone encounterd a similar problem or knows whats wrong, plz help me!

---

### Post by gsunr on 2009-01-19
i have the same problem with intel atom 330 board and HD2400Pro PCI :(

---

### Post by pecko on 2009-01-20
hello!

i have mb intel i945gcpe and i was trying to plug-in ati radeon 9250 pci into it and boot. i experienced similar problems like you guys. initramfs loaded successfully but loading ubuntu failed with a lot of segfaults and some "permission denied".

it seems like there is some kind of problem with on-board graphics conflicting with pci one. i plugged-in this card into other mb without on-board graphics and ubuntu started normally. so i think that this is the problem because it is impossible to turn off (disable) on-board graphics on many intel boards. but i have no idea what to do and how to solve this except switch mainboard with some which is possible to disable on-board graphics...

if somebody have some suggestions or better some solution pls make a reply:)

thx

---

### Post by pecko on 2009-01-21
i probably found solution:)

add lines to /etc/modprobe.d/blacklist

blacklist intel_agp
blacklist agpgart

edit your xorg.conf and change lines

Section "Device"
	Identifier	"Intel Corporation 82945G/GZ Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

to

Section "Device"
	Identifier	"ATI Radeon 9250 PCI"
	Driver		"radeon"
EndSection

or something similiar which is your case...

poweroff, plug-in your ati radeon 9250 pci card and turn-on. hope this will work:)

---

### Post by gsunr on 2009-01-21
wow, i will try asap.

---

### Post by jeremey on 2009-01-30
Hi, I am having the EXACT same problem.  Did that work for you?  I have my 256MB PCI Radeon 9250 sitting here wanting to go back in my computer.

---

