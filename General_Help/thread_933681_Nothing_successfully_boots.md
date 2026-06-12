---
title: "Nothing successfully boots"
date: 2008-09-29
forum: General Help
---

### Post by sricketts on 2008-09-29
I have a Dell Precision 390 that was sitting in a room for a while running ubuntu and connected to the LAN for shared use. The other day I tried logging in a noticed it was down (but powered on), so I tried to reboot. Unfortunately, I can't get anything to boot.

When I start Ubuntu, it splashes a few lines like "Kernel alive" and then goes to a black screen.

When I start Ubuntu in recovery mode, it runs through a bunch of system messages and freezes at "usb 1-2: new low speed USB device using uhci_hcd and address 2"

I ran memtest86+ for 4 passes without any errors.

When I start Windows XP, it goes to the logo splash screen and freezes.

When I start Windows XP in safe mode, it runs through a bunch of messages that look like ```
multi(0)disk(0)partition(2)\WINDOWS\System32\Drivers\Mup.sys
``` and then freezes on that screen.

I can't think of any changes since the last time I used the machine successfully. The only major change to the system in general that I made (besides partitioning and installing Ubuntu) was swapping graphics cards. Still, the machine was working fine (Windows and Ubuntu) with the new graphics card.

I'd appreciate any trouble shooting strategies from here. There is some data on the Ubuntu partition that I would like to recover if possible. If I could pull that, then I wouldn't be against a fresh reinstall of the operating system(s).

Thanks,
Scott

---

### Post by Patb on 2008-09-29
Scott, I cannot think of what the cause might be but it sounds as if your system cannot find the files to boot. Try booting from a live CD and reinstalling grub. Details here: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Hope this helps. Cheers, Pat

---

### Post by sricketts on 2008-09-30
> **Patb said:**
> Scott, I cannot think of what the cause might be but it sounds as if your system cannot find the files to boot. Try booting from a live CD and reinstalling grub.

I tried booting from a ubuntu live cd, and using both normal and safe graphics modes, the boot freezes on the ubuntu splash screen.

As a sanity check I booted the live cd on my laptop, and it worked fine.

Does this mean there is a hardware failure somewhere? How could I troubleshoot this?

Thanks,
Scott

---

### Post by Patb on 2008-10-02
> **sricketts said:**
> Does this mean there is a hardware failure somewhere? How could I troubleshoot this?
I'm afraid it looks like that to me, Scott. Try going into your BIOS menu and see if the BIOS can recognise the hard drive. But I'm not too optimistic. Even if your hard drive is somehow unreadable, I would have thought your system should be able to boot from a live CD. 

Good luck, Pat.

---

### Post by sricketts on 2008-10-03
> **Patb said:**
> Try going into your BIOS menu and see if the BIOS can recognise the hard drive.

I'm not really sure what to look for. Under Drives, I see

```

Diskette Drive
SATA-0
SATA-1
SATA-2
SATA-3
PATA-0
PATA-1
SATA Operation
SMART Reporting
```

SATA-0 is recognized and turned on. It gets seen as 160 GB and has a Drive ID. SATA-1, SATA-2, and SATA-3 are turned off (I assume these don't exist in my machine, but I'm not sure). PATA-0 and PATA-1 are both recognized as the CD and DVD drives.

What else can I look at?

Thanks,
Scott

---

### Post by Patb on 2008-10-04
Sorry Scott, I'm stumped on this one. Your BIOS does seem to recognise your hard drive. Both the linux and Windows errors you cite appear to emerge before the boot process has read any files from the hard drive. But I cannot suggest where to go from here. I cannot see why your system cannot boot from a live CD. Do you know whether it has done so before? If not, can you perhaps post the system specs. 

Cheers, Pat.

---

### Post by sricketts on 2008-10-06
> **Patb said:**
> I cannot see why your system cannot boot from a live CD. Do you know whether it has done so before?

Well, I know I installed ubuntu from a live cd, but I can't think of any other time when I booted from a live cd on the machine.

> **Patb said:**
> If not, can you perhaps post the system specs.

Dell Precision 390 ConvertibleMiniTower, PC Processor E6320 1.86GHz,1066,4MB L2/Dual-Core
Mini-Tower Chassis Configuration
4GB, 667MHz, DDR2 ECC SDRAM Memory, 4X1GB
160GB SATA 3.0Gb/s with NCQ and 8MB DataBurst Cache

When i bought it, it had a Quadro FX 3450, then I swapped that out for a GeForce 8800 GTS so I could run CUDA.

---

### Post by inigomontoya on 2008-10-06
Unplug the drive and try to boot a live cd.  If that doesn't work then disable your SATA controller in your BIOS and try again.

---

### Post by uidb4056 on 2008-10-06
> **sricketts said:**
> Well, I know I installed ubuntu from a live cd, but I can't think of any other time when I booted from a live cd on the machine.



Dell Precision 390 ConvertibleMiniTower, PC Processor E6320 1.86GHz,1066,4MB L2/Dual-Core
Mini-Tower Chassis Configuration
4GB, 667MHz, DDR2 ECC SDRAM Memory, 4X1GB
160GB SATA 3.0Gb/s with NCQ and 8MB DataBurst Cache

When i bought it, it had a Quadro FX 3450, then I swapped that out for a GeForce 8800 GTS so I could run CUDA.

May be it not helps but have you tested putting back again your previous video card instead of the new GeForce?

---

### Post by sricketts on 2008-10-06
> **inigomontoya said:**
> Unplug the drive and try to boot a live cd.  If that doesn't work then disable your SATA controller in your BIOS and try again.

I tried both suggestions, in each case I observed the same frozen logo screen.

I don't want to give up on restoring the usefulness of the machine itself, but at this point I would like to make an attempt to recover the files from the ubuntu partition. There are some that were never backed up that are valuable to me. Should I plug the drive into another desktop?

Thanks,
Scott

---

### Post by Therion on 2008-10-06
Going to toss this out there in hopes it MIGHT work...

Boot using the LiveCD and go into the BIOS.  

Look for the section on/for Storage Configuration (that's what my BIOS calls it) and look for the SATA setting.  See if it's set to "AHCI".  If it is, use the menu to change that setting to "IDE" instead.  Save and continue booting from the LiveCD and see what happens.

---

### Post by sricketts on 2008-10-06
> **Therion said:**
> Boot using the LiveCD and go into the BIOS.  

Look for the section on/for Storage Configuration (that's what my BIOS calls it) and look for the SATA setting.  See if it's set to "AHCI".  If it is, use the menu to change that setting to "IDE" instead.  Save and continue booting from the LiveCD and see what happens.

I have a section called SATA Operation. The options are
```

RAID Autodetect / AHCI
RAID Autodetect / ATA
RAID On

```
Previously, the first option had been selected. I tried the other two both with the hard disk plugged in and removed. Booting from the live cd under all scenarios caused the same freezing behavior.

---

### Post by sricketts on 2008-10-06
> **uidb4056 said:**
> May be it not helps but have you tested putting back again your previous video card instead of the new GeForce?

Yes, I switched back to the old card -- same problem.

---

### Post by sricketts on 2008-10-07
Update: I plugged the hard disk into another machine, booted with a ubuntu live cd, and recovered the important files.

So the hard disk does not seem to be the problem. The broken machine was somewhat expensive, so I would like to continue troubleshooting to find out where the hardware failure(s) is(are). If anyone has any suggestions, now the pressure of losing hard disk data is at least lifted.

Thanks,
Scott

---

### Post by Soupcan on 2008-10-07
Bring it to a repairman? I can't think of a single thing that would cause that.

---

