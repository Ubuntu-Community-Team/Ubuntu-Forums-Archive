---
title: "Booting Windows from GRUB?Help please!"
date: 2008-11-02
forum: General Help
---

### Post by nickguletskii on 2008-11-02
Hi!

I have a problem with dual-booting Windows from GRUB.Yes, that S*** booter.
Launch Widows XP Professional SP2:Error:<Windows Root>/System32/hal.dll is missing or corrupted! It is not!
Partition info by fdisk:
Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)

What to do?
I have tried this:
```

map (hd0) (hd2)
map (hd2) (hd0)
rootnoverify (hd0,2)
chainloader +1
boot
```

Error:Error reding disk.

I can view and change everything using UBUNTU on the C:/ partition, but boot will not work.

**[SIZE="4"]AND I DO NOT HAVE THE WINDOWS CD!!![/SIZE]**

:mad::confused::(

Can you please help?I also tried the trick above with disk 1,3,4,5 and it is useless.

Thanks!
[-o<

---

### Post by Sef on 2008-11-02
Try [Super GRUB Disk]("http://supergrubdisk.org").

---

### Post by TeXtonyx on 2008-11-02
That is a Windows error message which means grub succeeds in 
starting up Windows. So I tend to doubt that grub is the problem.

Computer error messages are approximate and can have several other causes
besides the most literal meaning. [http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm)

"Causes of the "missing or corrupt hal.dll" error include, naturally, a damaged hal.dll file or a hal.dll file that has been deleted or moved from its intended location. Additional causes may include a damaged or missing boot.ini file or possibly a physically damaged hard drive.
Resolution

   1. Restart the PC. The hal.dll error could be a fluke.

   2. Check for proper boot order in BIOS. You might see the hal.dll error if the boot order in BIOS is first looking at a hard drive other than your main hard drive.

      If you've recently changed your boot order or recently flashed your BIOS, this may be what's causing your problem.

   3. Run Windows XP System Restore from a command prompt. If this doesn't work or you're receiving the hal.dll error message before you're able to complete this process, move on to Step 3.

   4. Repair or replace the boot.ini file. This will work if the cause of the problem is actually Windows XP's boot.ini file and not the hal.dll file, which is often times the case.

   5. Write a new partition boot sector to the Windows XP system partition. If the partition boot sector has become corrupt or isn't properly configured, you may receive the hal.dll error."

TeX: Using Ubuntu, sometimes partitions are resized which can damage Windows.
Download Testdisk and run it, perhaps it will help fix the problem.

---

### Post by nickguletskii on 2008-11-04
1. Not a fluke.
2.?
3.I have not got the CD
4.Boot.ini is alright.
5.How?
TeX:Where to download from?

---

### Post by I'm a bus driver really on 2008-11-04
I had this problem with me trying to dual-boot Vista with XP (Vista installed first) And the way I fixed it was by downloading FreeBSD and re-writing Vistas Boot-Loader. But as you cannot do that, I am not sure what you could do.. I suppose you could download an XP Recovery ISO and burn it to a CD, then boot from the CD and fix the boot loader. Then, boot normally into XP and download FreeBSD and write a new Boot.ini with the Ubuntu partion included. I prefer to boot with a Microsoft BootLoader, personally. Just a thought.

---

