---
title: "Dual boot swapping: from Win 2k-Win XP to Ubuntu-Win XP"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by frsfrs on 2009-06-16
Hi,
maybe this has been answered somewhere else, however...
The problem: single hard disk, swap the dual boot Win2k-Win XP to the dual boot Ubuntu-Win XP without re-installing Win XP.

To be more precise: Win2K was the first to be installed and he is on the primary bootable partition, Win XP, installed successively is on a secondary partition of the same physical hard disk. 
Unfortunately this means that the boot.ini & Co. of Win XP reside on the first parition and not on the second (!).

Something experienced:

1) simply formatting the primary partition: the boot.ini & Co are lost, Win XP does not start;

2) installing Ubuntu in the first primary portion, cancels similarly the boot.ini. In addition the MBR is altered to point to Grub but Grub cannot boot Win XP because boot.ini& co. are not present in the secondary partition.

In this second case, simply copying the boot.ini & Co. in the second partition seems not enough to start Win Xp from Grub: the system freezes (maybe I overlooked something?).

I can propose myself a solution but I wonder whether there is something better:
resize the primary partition to a very small one containing only boot.ini & Co. and installing Ubuntu in the empty remaining space.
At the end this should result in having 3 partitions. Ubuntu, Win XP and a small primary partition for loading XP.

That's not bad, however it would be better to have Ubuntu in the first and Win XP in the second partition.

Any idea? (Please do ask me to reinstall XP, it is so fine tuned...)

BYe

---

### Post by dstew on 2009-06-16
> In this second case, simply copying the boot.ini & Co. in the second partition seems not enough to start Win Xp from Grub: the system freezes (maybe I overlooked something?).Yes, your XP partition needs the Windows boot sector code installed in order to boot. You can do this with the [Windows Recovery Console]("http://support.microsoft.com/kb/314058"), fixboot command. Then, grub can chainload XP. You need a Windows CD to access the recovery console.

---

### Post by frsfrs on 2009-06-17
Thanks,
it seems however tricky to plan the exact procedure, I still wonder which should be the final architecture of the disk: MBR pointing to Grub and Grub pointing either to boot.ini or to Ubuntu?

Do you think it is possible for the Windows Recovery Console to modify the MBR to point to Grub?

---

### Post by dstew on 2009-06-17
> I still wonder which should be the final architecture of the disk: MBR pointing to Grub and Grub pointing either to boot.ini or to Ubuntu?If you want to have a dual-boot system, I would recommend using grub as the boot loader. You can dual-boot using the Windows boot loader, but it is more difficult. When you chain load Windows using grub, grub does not point to boot.ini, but rather to the Windows boot sector code, which in turns points to ntldr and boot.ini. That is why you need to put the boot sector code into the Windows partition boot sector in order for grub to be able to chainload Windows.

> Do you think it is possible for the Windows Recovery Console to modify the MBR to point to Grub?What I think you are asking is if you can boot Ubuntu using the Windows boot loader, and the answer is yes. See [this page]("http://wintendo.wetpaint.com/page/Dual+boot+Windows+XP+with+Ubuntu+Linux+-+using+the+Windows+bootloader"). If you want to do it this way, you tell the installer to install grub to the Linux *partition*, and _not_ to the MBR. This puts the grub boot loader into the partition boot sector. Once grub is installed, you use the Linux command dd ("data dump") to copy the grub code from the boot sector of the partition into a file named ubuntu.bin. Then, you put this file into your Windows boot directory, and have boot.ini use this file to boot your Ubuntu system.

---

### Post by frsfrs on 2009-06-18
Thanks again for the explanations!

  I’m indeed oriented to follow your advice for GRUB and dual boot with it.
   
  As I had no clear procedures for my configuration case last week, I’ve unfortunately lost many data and I therefore prefer to proceed very slowly to set it out.
   
  Configuration: 1 Hard Disk, the MBR is a XP type, the main partition contains only boot.ini&Co, the second partition only Xp without boot.ini&Co.
   
  Ubuntu could be installed in the main partition or in a third partition (as the second is fulfilled by XP). 
   
  I try to figure out what could happen in the two cases by analysing the booting process (full details [here]("http://duartes.org/gustavo/blog/post/how-computers-boot-up/")):
   
  1) The BIOS seeks a boot device;
  2) It finds (supposedly) the HD;
  3) The BIOS reads the first 512byte of the sector zero: the MBR;
  4) The BIOS loads the MBR in the memory and executes the code contained in the MBR;
  5) The code contained in the MBR is a GRUB code: the GRUB stage 1;
  6) An additional bootstrap code is loaded from another sector;
  7) The MBR GRUB code + the additional bootstrap code load the GRUB stage 2;

The GRUB stage 2 loads the grub.conf and the boot choices are displayed to the user on the screen.
   
  Now comes interesting, as the article cited does not deal with multi-boot.
   
  When choosing Ubuntu, the kernel is loaded from the partition chosen in the installation process. If Ubuntu is in the first or in the third partition, the kernel is pointed and loaded.  No problem.
   
  On the other hand, when choosing XP, you mentioned that GRUB:
  > **dstew said:**
>  grub does not point to boot.ini, but rather to the Windows boot sector code, which in turns points to ntldr and boot.ini. That is why you need to put the boot sector code into the Windows partition boot sector in order for grub to be able to chainload Windows.


Now where do all these items should reside?
  When installing Ubuntu is in the first partition, then the boot.ini& Co. are deleted and the MBR is turned into a Grub MBR.
  As far as I understand your suggestion, the Windows Recovery Console (WRC) should be used to: 
  -put the Windows boot sector code in the secondary partition boot sector;
  -put boot.ini&co somewhere (second partition?) and make the boot sector to point them.
   
  When installing Ubuntu in the third partition, then the boot.ini& Co. are still there but the MBR is a Grub MBR.
  In this case the WRC should be used to:
  -put the Windows boot sector code in the secondary partition boot sector;
  -point the secondary partition boot sector to the primary partition where boot.ini& Co. are located.
   
  Is it the procedure correct?
  Is WRC able to carry out all that?
   
  Bye.

---

### Post by dstew on 2009-06-18
> The MBR GRUB code + the additional bootstrap code load the GRUB stage 2;This is essentially correct, but I think actually stage 1 can load stage 2 without any extra code. There is sometimes a grub stage 1.5 file loaded in the sector immediately after the MBR, if this sector can be used, but it is not absolutely necessary. Grub stage 1 is "hard wired" by the installation process to get stage2 from a particular block on the disk. Stage 1.5 allows grub to look in the filesystem for stage2, in case you moved it.

> When installing Ubuntu is in the first partition, then the boot.ini& Co. are deleted and the MBR is turned into a Grub MBR.

If you install Ubuntu into the first partition, then the Windows files there will be gone, since you need to format the parititon. Grub is installed into the MBR by default. You can tell the installer to put grub stage 1 into a partition boot sector, or not to install grub at all if you want (Step 7, Advanced tab).

> As far as I understand your suggestion, the Windows Recovery Console (WRC) should be used to:
-put the Windows boot sector code in the secondary partition boot sector;
-put boot.ini&co somewhere (second partition?) and make the boot sector to point them. The Windows boot loader, whether it is started from the MBR or a partition boot sector, looks for the active partition (boot flag set in partition table) and loads ntldr from the root directory of the active partition. Ntldr then looks at boot.ini (which has to be in the same root directory) for boot information. My guess is that in your original W2000/XP dual boot system, you had ntldr and boot.ini in your first partition root directory, and that ntldr was directed by boot.ini to start XP in your other partition. You did not need to have ntldr or boot.ini in the XP partition in order to boot it. However, these files will still be needed to boot XP, even if grub is your primary boot loader. I think fixboot only puts in boot sector code, and does not put ntldr or boot.ini into the root directory. Probably, you could just copy these files from the old W2000 partition root directory into your XP root directory, and it might work. You could also just leave it as it is, and put Ubuntu into a third partition.

---

### Post by frsfrs on 2009-07-01
Well,
I've spent all this time in trying both the solutions without any success.

Killing Win2k in the first partition in favour of Ubuntu, destabilizes XP which still looks for boot.ini & Co. in the first partition.

The second option to have only boot.ini & Co. in the first partition, XP in the second and Ubuntu in the third, did not work as well, notwithstanding MBR and boot.ini care processing.
I don't know what happened, XP still could not boot after Grub, always looking for boot.ini.

I gave up and adopted the classical solution: I reinstalled XP in the first partition and gave Ubuntu the second.

End.

---

