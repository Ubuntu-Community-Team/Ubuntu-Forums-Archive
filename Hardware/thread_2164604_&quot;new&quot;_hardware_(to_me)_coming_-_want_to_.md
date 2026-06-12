---
title: "&quot;new&quot; hardware (to me) coming - want to be prepared"
date: 2013-08-01
forum: Hardware
---

### Post by squakie on 2013-08-01
I probably made a mistake getting rid of all my other computers and just trying settle for a zbox hooked to my TV - the performance isn't anything like what I was used to.

To that end, I have ordered some new hardware to build another desktop.  It is supposed to be all new and still sealed, however it's not the newest or greatest motherboard - just what I could afford right now.

The motherboard is a [SIZE=1]Asus F1A55-M LE[/SIZE] and the web site says it has UEFI bios.  I had a new laptop that used UEFI and had a *heck* of a time but did get ubuntu dual-booting with Windows 8.  I hated it, so I sold it with my other computers just 2 months ago or so.

My plans are to have Windows XP (i have an old copy and the updates) and Ubuntu for dual boot on this motherboard.  So before it even arrives, I want to know if I'm going to facing problems trying to install ubuntu on it since it is UEFI.  I only want dual-boot with XP as I have a couple of things I need to do that require it.

So - with a brand-new setup, no OS installed yet, what is the BEST way to install ubuntu and xp for dual-boot on a UEFI machine?  I can't use a VM at this time for my xp projects, so I do need to dual boot.

oldfred helped me out SO much on the laptop and getting ubuntu installed and dual-booting with the pre-installed Windows 8.  I'm hoping it won't be so many steps and worries about the boot drive in the BIOS as I had with that laptop.

Thanks in advance!

---

### Post by JDorfler on 2013-08-01
I have two Asus boards.  One running straight Ubuntu for a server and the other dual booting for fun and games.  I'm Dual Booting Win 8 and 13.04 Xubuntu using UEFI mode and UEFI mode with the server.  What I recommend is make sure your BIOS is fully updated to the latest and greatest.  Then, make sure that your UEFI settings are set to No Secure Boot and "Other OSes" in your boot options.  Each board with this UEFI garbage is different.  Each one has it's own issues and it's own fix actions.  I have an HP Laptop that came with Win8.  I dumped Win8 for Linux Mint just because what is the point of having Windows if I'm not gaming on it.  (I really hope Steam takes off big time on Linux.  Really tired of maintaining two OSes on one box.)  

Good luck.

---

### Post by oldfred on 2013-08-01
XP has no compatibility or drivers for gpt partitioned drives. And UEFI uses gpt partitioned drives only. 

You may be able to install in the CSM/Legacy/BIOS mode with MBR(msdos) partitioning as if it is an old computer. But then be sure to boot Ubuntu in BIOS mode also as both systems must be in the same mode.

I have BIOS, but converted one older drive to gpt with 10.10. I dual booted with XP on another MBR drive without issue. But XP does not have gpt drivers. Then I got a new SSD which I wanted trim. Trim needs AHCI and again XP does not have AHCI drivers. I did find a way to install those but it was a new install, so I shut XP down (finally).  I did test turning AHCI back off and was able to boot XP, but that is such a hassle, I just preferred to stop using the one XP app I was using.

---

### Post by squakie on 2013-08-01
Thanks to both of you!

Oldfred - *IF* I could get my DVC-100 vhs capture device to work ok in Ubuntu then I think I chuck Windows - just having a very hard time with that (long story - 3rd different type of adapter I've tried with no luck, and this one was supposed to work ;)  ).

I'll wait until things get here and hopefully find some way to get the DVC-100 working in the mean time.

Thanks again!

---

### Post by squakie on 2013-08-05
The cpu will be quad-core 3 ghz amd, 4gb of memory.  It's set to be delivered on Monday.  I have the case, power supply, optical drive and 120gb bare disk here.  Hopefully, since it will be a "new" install of ubuntu 13.04 (64-bit) it will install to the uefi enabled motherboard, and maybe I'll be able to run XP in a VM.  I couldn't do that with the previous vhs to disk adapters since they didn't show in ubuntu (they both showed as USB devices, but no linux drivers).  At least this DVC-100 does seem to be recognized by ubuntu, so I'm hoping USB pass-through to a Windows XP VM will be fast enough to capture my old tapes in XP.

---

### Post by oldfred on 2013-08-05
If XP is something you may only use occasionally, you can have it on a separate MBR(msdos) drive and dual boot. It just is you have to go into UEFI and change to CSM mode to boot XP and then have to go into UEFI and turn off CSM or turn on UEFI to boot everything installed in UEFI mode. Not the easiest way to dual boot. Not sure if VM will work or not as I have not tried VM at all.

---

### Post by squakie on 2013-08-05
If I have a completely bare drive like this, is it possible to just turn off UEFI all together before I even install Ubuntu?  Would that solve the UEFI "problem" or is that normally just for a single boot?

Thanks!

---

### Post by oldfred on 2013-08-05
All the UEFI systems have CSM/BIOS/Legacy mode which is just the old BIOS.

Some newer hardware may work better with UEFI, but for now just about everything should work just as well either way. It depends on new drivers for UEFI or whether older drivers with BIOS still work with newer hardware.

I prefer to keep Ubuntu on one drive and Windows on another drive. Then you can boot both with BIOS. And you can have the Ubuntu drive be partitioned with gpt and the XP drive as MBR and dual boot. I used that configuration with 10.10 on a gpt drive and XP on a MBR drive booting with BIOS (no UEFI at all).

If you use gpt I might create an efi partition as the first partition or leave 250MB as space for a future efi partition as the efi partition needs to be first and would be difficult to add later if you wanted to later try UEFI booting. But that only works if you have two drives.

---

### Post by squakie on 2013-08-05
Darn - I only have 1 drive for now.  I hope to (sometime after Christmas when I'm able to save a little money again) buy 2 big drives and try raid - maybe I should wait and just get another drive at that time instead of 2 then I would be able to divide things up.

I guess time will tell - all of the hardware pieces I was waiting on arrived today so it's time to start building.  Hopefully I still remember enough of that to not screw it up ;)

Thanks for the help - I'll let you know what happens!

---

### Post by squakie on 2013-08-08
Well, the VHS to disk drama gets worse:  Got all of my new hardware and assembled, running 13.04 64-bit.  Installed virtualbox, put Windows XP as a guest and installed the guest additions.  Well, I now have a driver for the DVC-100, but I don't have any software for it!  Tried installing the Roxio VHS to DVD package and using the adapter that came with it - the install aborts.  So, went all the way back to EasyCAP usb capture device - driver and software installs, device works (video looks fine in preview), BUT....I get an error whenever I click on record.   AARRGGHHH!!

At least I can report the new hardware is working fine, and installing Ubuntu as the only OS onto the bare drive just went real smooth.

I never should have sold my old hardware and settled on a zbox.  My zbox just has a dual-core Atom in it and the performance just isn't up to par for me.  At least this new hardware is a big step forward from that (AMD A8, quad-core 3 ghz).  Still not as nice as what I had, but a lot better than the zbox.  Means the zbox is going to become the media center for my sister and brother in-law, and I'll be keeping the Pi around to play some more.

At any rate - this all worked out fine, so thread solved!

---

### Post by squakie on 2013-08-11
I have officially solved my VHS to disk "problem".  Even the book that came with my motherboard said it was UEFI bios.  I've tried going to the BIOS setup screens at boot, but there must be something about where it expects to send video, as it only shows dark gray backlit screen, so I never see what's there to verify UEFI.

However, I cleared the disk and I *WAS* able to install Windows XP Pro, defrag, shrink the partition and install Ubuntu 12.04 (haven't run the upgrade yet) and can dual-boot!!  SO......that means I can use the EasyCAP device on the Windows side and record perfectly!

So, the new hardware even allowed me to dual-boot so I can capture my VHS tapes to disk for the entertainment center!

---

