---
title: "Windows 7 dual boot install problem"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by xeddog on 2009-05-16
OK, first off I know there are several threads written regarding dual booting with linux and Windws Vista/7.  I have read a lot of them until it has given me a headache.  But here is MY story.

I have an old 32 bit system that had just one drive in it, the 80GB drive.   I had xubuntu 9.04 installed using the entire drive so there were two partitions on it.  There was sda1 which was the large partition for linux itself, there was sda2 which was an extended partition that contained sda5 linux swap.

Then I added the 60GB and wanted to install Windows 7 RC on it.  My first problem was that this computer would not boot the Windows 7 RC dvd.  I had two other computers that did, so the disk was fine.  Just THIS machine would not boot it.  It was like there was no dvd in the drive.  So I booted a Vista dvd, and started trying to install Vista.  That was my next problem.  As long as sda was formatted as ext3 for linux, "Windows is unable to find a system volume that meets it's criteria for installation".

SO %#@& FINE!!!   I deleted all partitions from BOTH drives, recreated ntfs partitions on both drives, formatted them, and was then able to install Vista on sdb.  Sheez.  Now both sda and sdb contain single primary partitions that take the entire drives except for a very small amount (1MB) of unallocated space on sdb.

Then I re-installed Xubuntu 9.04 on sda, again using the entire drive, and formatting the partitions as ext3.  That did not quite go as planned.  I was hoping that the Xubuntu installer would recognise the Vista OS and just add it to the GRUB menu, but that didn't happen.  It DID recognise the Vista partition, but told me that it would not be able to access it.  (Sorry I don't remember the exact message).  But the rest of the Xubuntu install went normally.

Most of you now know what my problem is now.  After the Xubuntu install, Vista is nowhere to be found.  I have added various flavors of strings to the /boot/grub/menu.lst, and I am now at the point where when I select Vista from the Grub menu, I get the "BOOTMGR is missing" message.  So it seems apparent that the boot manager for Vista HAD to be installed on the first disk and it HAD to be in an ntfs partition.  Even though Vista itself was installed on the second disk.  The linux install then formatted the Vista bootmgr out of existence.  

This is the part of reading all the preceding threads that has given me the headache.  There is just something that I am not understanding about all of it.  So are there some step by step instructions that anyone from an old fart to a 4 year old can understand and follow (okay . . .a 6 year old) to get a working bootmgr for Vista so I can upgrade it to Windows 7?

I want my drives set up this way because in a little while I will be through with the Windows 7 and I can then just remove the disk or maybe put karmic on it.  If I put 7 on the first disk and then Xubuntu on the second, that would involve a lot more work and I might even have to re-install Xubuntu again.  I'd rather not do that.

So Thanks in advance for any help that you can offer.

xeddog

---

### Post by zvacet on 2009-05-16
```
sudo fdisk -l
```

Post it here.

---

### Post by xeddog on 2009-05-16
Here ya go,
> 

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d038d03

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9826    78927313+  83  Linux
/dev/sda2            9827       10011     1486012+   5  Extended
/dev/sda5            9827       10011     1485981   82  Linux swap / Solaris

Disk /dev/sdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xabdeabde

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7476    60049408    7  HPFS/NTFS



Thanks,

xeddog

---

### Post by zvacet on 2009-05-17
```
gksudo gedit /boot/grub/menu.lst
```

and find this line 

> ### END DEBIAN AUTOMAGIC KERNELS LIST


and add below

> # This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows 
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

Save and close file.Restart and you should be able to boot windows.

---

### Post by xeddog on 2009-05-17
I did a copy/paste with the information you provided and I still get the bootmgr is missing error.  I had actually tried this before with no success then either (duh!) but tried it anyway in case maybe I misspelled something or . . .???

Any other ideas???


Thanks,

xeddog

---

### Post by Mark Phelps on 2009-05-17
Presuming you have a Vista DVD, disconnect the Ubuntu drive, boot using the Vista DVD, run Startup Repair (several times), reconnect the Ubuntu drive, boot from that drive -- now the menu.lst entries provided previously should work OK.

---

### Post by walker9010 on 2009-05-17
As far as I know, Windows is never happy being installed to a second hard drive. You probably would just be better off installing Win 7 to the first, and then Xubuntu to the 2nd.
Check out this blog post: [http://www.weiqigao.com/blog/2004/01/14/1074144025000.html]("http://www.weiqigao.com/blog/2004/01/14/1074144025000.html") and see if that helps, in terms of getting the files onto the first hard disk that windows needs to boot.

Of course, the recovery console Mark Phelps mentioned may work...however, I've found recovery console to be a bit temperamental.

---

### Post by presence1960 on 2009-05-17
> **walker9010 said:**
> As far as I know, Windows is never happy being installed to a second hard drive. You probably would just be better off installing Win 7 to the first, and then Xubuntu to the 2nd.
Check out this blog post: [http://www.weiqigao.com/blog/2004/01/14/1074144025000.html]("http://www.weiqigao.com/blog/2004/01/14/1074144025000.html") and see if that helps, in terms of getting the files onto the first hard disk that windows needs to boot.

Of course, the recovery console Mark Phelps mentioned may work...however, I've found recovery console to be a bit temperamental.

The map lines in the windows entry of menu.lst take care of that problem. When Windows is installed on a drive that doesn't boot first the map lines "trick" windows into thinking it is on the first drive.

---

### Post by presence1960 on 2009-05-17
> did a copy/paste with the information you provided and I still get the bootmgr is missing error

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

