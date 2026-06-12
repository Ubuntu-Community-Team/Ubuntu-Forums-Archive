---
title: "GRUB error 17 (have tried several fixes...)"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by pandaconda on 2009-05-18
I'm a linux newbie trying to dual-boot ubuntu with Vista on my system.  I know there are several posts about "error 17", but none of them have worked for me and it seems that this error may be slightly different concerning 9.04. I apologize if this is redundant.

My setup is like this: 2 HDs in a RAID 0 plus one more just by itself

I first tried putting ubuntu on the seperate HD that doesn't have windows, but GRUB  didn't like that (error 22).  I then removed it and reinstalled it on my main RAID drive, but GRUB is still giving me error 17 before I see any OS option.

I have tried:
1. doing a file system check on the partitions I made
2. using a Super Grub disk, but this doesn't show anything when I boot with it
3. the 'find /boot/grub/stage1' (find /grub/stage1) command after entering 'sudo grub'.  This returns '(hd1,0)' but I'm unsure what to do from here other than assign grub to it by 'root (hd1,0)' and 'setup (hd1,0)'.  I tried using [this thread]("http://ubuntuforums.org/showthread.php?t=1133288&highlight=grub+error+17&page=2") (which was never clearly resolved) and when I type 'sudo sfdisk -l' I get:

```
Disk /dev/sda: 38913 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+  77825-  77826- 625135616    7  HPFS/NTFS
/dev/sda2          0       -       0          0    0  Empty
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty

Disk /dev/sdb: 38913 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1      37697   38912    1216    9767520   83  Linux
/dev/sdb2      36115   37696    1582   12707415    5  Extended
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty
/dev/sdb5      36481+  37696    1216-   9767488+  83  Linux
/dev/sdb6      36116+  36480     365-   2931831   82  Linux swap / Solaris

Disk /dev/sdc: 60801 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdc1          0+  60474   60475- 485765406    c  W95 FAT32 (LBA)
/dev/sdc2          0       -       0          0    0  Empty
/dev/sdc3          0       -       0          0    0  Empty
/dev/sdc4          0       -       0          0    0  Empty
```I also saw something that said it will work if I just disable the RAID function in my BIOS, but won't that kill my Vista install and any other data on the drives? Ubuntu is super awesome from what little I've seen, but I still want Vista for games and stuff...

Any help or further simplification of earlier posts would be greatly appreciated, as I've been at it all day with no progress. Thanks!

---

### Post by ronparent on 2009-05-18
(hd1,0) agrees with the fdisk output you posted above. Assuming that you are booting from that same drive (boot order set in bios) the next command would be setup (hd1). This last command will write grub to the sdb mbr and point it to (hd1,0) to find stage1 etc on boot. I am uncertain whether or not the sda and sdc will configure properly as your raid 0 however. But that can be addressed separatly once the ubuntu boot problem is solved.

---

### Post by pandaconda on 2009-05-18
Thanks, ronparent.  I ran 'setup (hd1)' (I had been doing 'setup (hd0)', which now I realize doesn't make sense).  It looked like it worked, saying it reassigned things and ending with 'done!'

It still doesn't work, though.  I get the same 'error 17' message.

Also, to clarify, I'm pretty sure it's the sda and sdb drives that make up my Raid config.  The sdc then represents the free-standing HD.  ( I have 2x320gb HDs in the RAID array, giving the formatted 625gb figure seen at the top of what I posted.  The other is a 500gb, so the 485gb in the sdc makes sense too)

To set the partitions up, I used the manual partition option because it was the only one that would work on the array, then went back and double checked it twice against other threads to make sure I did it right.  Maybe the problem is that I shouldn't have tried to do this on a RAID array in the first place.  Now everything seems all jumbled up, with Ubuntu residing on only the second drive of the RAID and the grub not being able to see that.

It probably would have been easier to just have installed it all on the stand-alone drive (sdc) like I tried to in the first place, although I'm still not sure how I could get grub to recognize two OSs on two seperate drives.  Both ways seem fine to me once they start working, so any advice on either would be greatly appreciated.  Thanks again!

---

### Post by ronparent on 2009-05-19
How did you partition for ubuntu install (ie entire disk, guided, manual)?

---

### Post by pandaconda on 2009-05-19
Well at first I had tried a manual install because that was the only way it would let me take up less than the full RAID drive.

Now, though, I've just unplugged the two drives I had in RAID and did a guided install on the other drive (just to have a full OS for now).  I've got ubuntu fully up and running now, but I need to figure out a way to dual boot from different drives.  I guess also it would be good to know if it is possible to read the data from the RAID drive in ubuntu (since that is where my documents, pictures, etc. are).

Thanks again, and for any further help.  I didn't find much info in my initial attempt to do the two-drive thing, and I'm not sure if it even applies when one disk was actually an array.

---

### Post by dstew on 2009-05-19
Grub is not able to recognize and mount RAID file systems generally. I am not sure if your RAID is software or "Fake Raid" (semi-hardware), but in either case you were bound to have problems. If software RAID, grub will not be able to recognize the filesystem, hence error 17. You could get around this by creating an un-RAIDed /boot partition at install time, and installing the kernel there. Then, after grub loads the kernel, it can potentially recognize and mount a RAID because it has the software to do that. You could also create a software RAID 1 (mirrored). If the kernel is there, grub will load it, since it will treat it as a normal file system, without caring that there is an identical twin somewhere else. But striped RAIDs 1 and 5 are not compatible with grub.

You can install Ubuntu to a "Fake Raid" with the ability to boot using grub, but it is difficult. See the [FakeRaid How-To]("https://help.ubuntu.com/community/FakeRaidHowto").

The Alternate Install CD can create and install Ubuntu to a software RAID. But the problem with grub is as above.

---

### Post by pandaconda on 2009-05-19
Ok, it looks like dual-booting with my current Vista install is going to be a little above my expertise level.  

What if I wanted to try a VM setup instead?  Would that work either on the RAID or on the separate disk?  I know it is more taxing on my system, but I have a quad-core cpu with power to spare.

I suppose my next step for trying that would be to boot up in Vista, and maybe get rid of my current ubuntu install?  Unfortunately, going all-linux isn't really an option for me right now.

---

### Post by dstew on 2009-05-19
I do not have any experience with virtual machines, but I know that you can install Ubuntu as a Windows file with [Wubi]("http://wubi-installer.org/"). Since this uses the intact Windows file system without modifying it, the Vista RAID will not be changed. Wubi does not try to install grub.

---

