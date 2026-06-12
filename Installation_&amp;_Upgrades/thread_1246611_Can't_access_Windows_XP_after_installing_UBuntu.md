---
title: "Can't access Windows XP after installing UBuntu"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by Kat_129 on 2009-08-21
Hi guys, 
So before I installed Ubuntu i did look up on how to do the dual boot setup. And followed each step by setup. I am quite sure I didn't touch C:, but did delete the D: while creating the partitions- for ubnutu primary, swap and logical shared for both windows and ubnutu contents. But after I finished the installation, I wasn't able to access or log into windows at all. 
I know the partition is there, I am quite certain there is a way to get to working again like normal. But I don't want to be taking risk; it just that i dont want to reinstall Windows XP again since this was installed by school and i need to give in laptop in the same condition and setting for Windows XP  Please guide me, how I can fix this problem.  Thanks a lot in Advance! Kat =) 


Here is the Summary output when i checked the partition by fdisk -l:
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe2e26367

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440088+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            7649       15810    65550781+  83  Linux
/dev/sda3           15811       16357     4393777+  82  Linux swap / Solaris
/dev/sda4           16358       19457    24900750    5  Extended
/dev/sda5           16358       19457    24900718+   b  W95 FAT32

Disk /dev/sdb: 2062 MB, 2062548992 bytes
16 heads, 32 sectors/track, 7868 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0xef5198c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7868     2014192    6  FAT16

---

### Post by running_rabbit07 on 2009-08-21
Go to System>Administration>Synaptic Package Manager and install startupmanager. 

Once install open it @ System>Administration>Startup Manager.

There should be a scroller that has your OSes on it. See if it lists Windows.

---

### Post by Kat_129 on 2009-08-21
Hey 
I did exactly what you said to do! It does say that their is a Windows XP for the default OS menu!. I tried to select that partition when i boot up, but it does nothing and comes back to OS selection menu. 
I checked and confirmed that it was installed after by using the GParted.
[http://depositfiles.com/files/us2bi77ja](http://depositfiles.com/files/us2bi77ja)

Thanks in advance!

---

### Post by running_rabbit07 on 2009-08-22
> **Kat_129 said:**
> Hey 
I did exactly what you said to do! It does say that their is a Windows XP for the default OS menu!. I tried to select that partition when i boot up, but it does nothing and comes back to OS selection menu. 
I checked and confirmed that it was installed after by using the GParted.
[http://depositfiles.com/files/us2bi77ja](http://depositfiles.com/files/us2bi77ja)

Thanks in advance!

I don't know how to fix it, but you need to find out how to repair your MBR. (Master Boot Record) 

I could see that you still had the NTFS partition so it is just a matter of repairing that. 

Be patient while trying to get a fix. If you need any files from that partition you should be able to mount it and copy folders and files. You should be able to access that partition via your Places Menu.

Edit: BTW you can attach photos in the reply window.

---

