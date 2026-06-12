---
title: "Command Prompt"
date: 2008-07-27
forum: General Help
---

### Post by Zer0noise on 2008-07-27
Ok, im just going to cut right to the chase and explain my situation. I currently have Ubuntu 7.10 installed. Now, I want to uninstall it! (for personal reasons) After discussing this with the support team for my Acer Laptop, we found out the problem to why i was unable to use the [Alt] + [F10] eRecovery function on my computer was because Grub rewrote over my MBR with its own version. Now the only way to restore my MBR is to open up command prompt and type in a few codes. Ok, heres the real problem! After installing Ubuntu, i found out that it erased my C: and D: (i was able to find this out by using Wine and installing a windows program, which revealed the directories) Now, i still have my "PQSERVICE" drive, which contains all the restore files. I need to find out is it still possible to run the Windows Command Prompt on Ubuntu. ( btw, I can't boot in Windows, at all) 



My email: [email]Zer0noise@yahoo.com[/email]

---

### Post by caljohnsmith on 2008-07-27
Just because you don't see a C and D drive when running a Windows app under Wine does not mean you necessarily deleted Windows from your HDD. Do a "sudo fdisk -l" in a terminal Window, and see if it lists more then one partition, and if any of the partitions say they are NTFS (post the output back here so we can all see it). 

And to remove Grub from the MBR, you don't have to use your PQSERVICE partition and try to run Windows commands from it; all you need to do is replace the Grub MBR with a Windows MBR. You can do that many ways, but the easiest I think in your particular case would be to download the Super Grub Disk from supergrubdisk.org. Boot from the Super Grub Disk, and it allows you to easily replace the Grub MBR with a Windows MBR.

---

### Post by Zer0noise on 2008-07-27
> **caljohnsmith said:**
> Just because you don't see a C and D drive when running a Windows app under Wine does not mean you necessarily deleted Windows from your HDD. Do a "sudo fdisk -l" in a terminal Window, and see if it lists more then one partition, and if any of the partitions say they are NTFS (post the output back here so we can all see it). 

And to remove Grub from the MBR, you don't have to use your PQSERVICE partition and try to run Windows commands from it; all you need to do is replace the Grub MBR with a Windows MBR. You can do that many ways, but the easiest I think in your particular case would be to download the Super Grub Disk from supergrubdisk.org. Boot from the Super Grub Disk, and it allows you to easily replace the Grub MBR with a Windows MBR.


No, thats not what i meant. I CAN see C: and D:. Ubuntu just erased the files on those drives and hide them in the GUI. I can also see new drives called H: which Ubuntu is using. I hope that further explain my situation.Im downloading super grub disk this very moment. I'll let you know how it goes

---

### Post by cariboo on 2008-07-27
Did you do a wubi install, that is what it sounds like. As the previous poster mentioned in a terminal type:

```
sudo fdisk -l
```

If you see ntfs listed beside any of the partitions, try to mount the partiton and check to se if the data is still there. Using a filemanager of some sort in wine is not going to give you a true reading of what is on your hard drive, as wine sets up a virtual c:\ drive in your home directory. Trust the people on this board they know a lot more about recovering your data than a phone support person, they can only work with the scripts they are given by the company they work for and cannot and should not give you any advise outside of the scripts they use.

Jim

---

### Post by Zer0noise on 2008-07-28
Ok, i typed in "Sudo fdisk -1" and this is what i got:

---------------------------------------------------------------------
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5ea4f703

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       10176    81738688+  83  Linux
/dev/hda2           13938       14593     5269320    5  Extended
/dev/hda3           10177       11362     9526545    c  W95 FAT32 (LBA)
/dev/hda4           11363       13937    20683687+  83  Linux
/dev/hda5           14229       14593     2931831   82  Linux swap / Solaris
/dev/hda6           14056       14228     1389559+  82  Linux swap / Solaris
/dev/hda7           13938       14055      947772   82  Linux swap / Solaris

Partition table entries are not in disk order
Note: sector size is 4096 (not 512)

Disk /dev/sda: 79.8 GB, 79824777216 bytes
26 heads, 50 sectors/track, 14991 cylinders
Units = cylinders of 1300 * 4096 = 5324800 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14992    77953628    b  W95 FAT32
---------------------------------------------------------------------

I want to remove the Linux partitions so i can install Windows xp. I only want one OS and i dont want to leave any unused space.

---

### Post by zvacet on 2008-07-28
> I want to remove the Linux partitions so i can install Windows xp.

Windows install Cd will do it for you.If not download [Gparted live cd]("http://gparted.sourceforge.net/") and do it with it.

---

