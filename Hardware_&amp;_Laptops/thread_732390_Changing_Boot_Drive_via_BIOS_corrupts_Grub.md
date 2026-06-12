---
title: "Changing Boot Drive via BIOS corrupts Grub"
date: 2008-03-22
forum: Hardware &amp; Laptops
---

### Post by MPH on 2008-03-22
I need to better understand how a BIOS setup program actually changes which hard drive it boots.  I *assumed* ](*,) that it stored the selected boot drive info in the ATA controller’s flash memory but it appears in my case that it modifies the disks’ Master Boot Records in some way.  In doing so, it apparently corrupts Grub and makes it unbootable.  (Yes, I’m sadly becoming an expert at using the Ubuntu LiveCD and restoring Grub. :-({|= )

This started when I moved my 2 Ubuntu drives (Gutsy and data) to another PC with more memory.  (The new PC still has a Windows 98SE drive in it that has valuable app setup information.)  The PC uses a Soyo SY-6BA+IV mobo.  The motherboard’s primary chipset is Intel and supported only ATA/33 so Soyo added a Highpoint (HPt) ATA/66 controller chip to the mobo, thus the board supports 8 IDE/ATAPI devices.  My 3 hard drives are connected to the HPt controller, which has its own BIOS setup program.  What I’ve discovered is that when I switch back and forth between booting the Windows and Ubuntu hard drives using the HPt BIOS setup, GRUB apparently becomes corrupted; that is, immediately after the POST messages when booting, “GRUB” is displayed on the PC monitor before the PC freezes.

To be certain what causes this problem, I fixed Grub once again from the LiveCD and then successfully rebooted the PC past the “freeze point” four times.  Actually, the third time, I let Ubuntu fully load and I logged in and then shut it down.  The point of this is to be certain that Ubuntu/Grub wasn’t causing the problem.

Next, I rebooted and activated the HPt BIOS setup.  In the setup, I changed the selected boot drive from the Ubuntu drive to the Windows drive.  Without leaving the HPt setup, I changed the boot drive selection back to the Ubuntu drive.  When I exited the setup, Grub froze again.

Has anyone else experienced this type of problem? :???: I was hoping to avoid all the dual boot issues by letting the BIOS handle it… but obviously I haven’t.

Has anyone successfully used their BIOS to change the boot drive without any problems?  I wonder if the problem is unique to the HPt BIOS.

Thanks for any insight you can give me besides the obvious… dual boot with Grub and leave that BIOS alone!

---

