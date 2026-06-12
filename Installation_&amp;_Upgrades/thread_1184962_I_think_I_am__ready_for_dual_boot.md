---
title: "I think I am  ready for dual boot"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by kd0afk on 2009-06-11
I have partitioned my hard drive thus:
35 GB for linux (tiny, I know)
15 for windows
5 for swap

the windows partiton is formatted FAT32
Should I be good to go to install windows?

I have read and printed out these directions [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1)
And I have a copy of Super Grub Disk to get me out of trouble.

Comments?

---

### Post by presence1960 on 2009-06-11
install windows first. Then to install Ubuntu boot the Live CD and choose check disk for defects. if it checks ok then install. When you get to the window of the partitioner titled "Prepare disk space" choose the manual option. Then select the partition you created for Ubuntu and install it by choosing file system on "use as" , partition type, and mountpoint choose "/". when you get to the screen that is attached below click advanced and choose to install GRUB to hd0 or sda to install GRUB to MBR of your hard disk. Then click install.

---

### Post by ChemShock on 2009-06-11
My WinXP needed 15 just to run at base level after all of Windows updates. No anti-virus, nothing.

My jaunty install, after I have every program and file I could ever want (minus music), takes up only 17 GB

Just food for thought....

---

### Post by H2SO_four on 2009-06-11
> **kd0afk said:**
> I have partitioned my hard drive thus:
35 GB for linux (tiny, I know)
15 for windows
5 for swap

the windows partiton is formatted FAT32
Should I be good to go to install windows?

I have read and printed out these directions [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1)
And I have a copy of Super Grub Disk to get me out of trouble.

Comments?

5GB for swap? that seems quite large, no?

---

### Post by ChemShock on 2009-06-11
> **H2SO_four said:**
> 5GB for swap? that seems quite large, no?

Yeah, I agree mine is only 3.5 and that my be on the larger side. I auto partitioned.

---

### Post by presence1960 on 2009-06-11
> **ChemShock said:**
> Yeah, I agree mine is only 3.5 and that my be on the larger side. I auto partitioned.

I have 4 GB swap, but i want to be able to use suspend & hibernate so I made it equal to my RAM. But then again I have 2 hard disks so I have plenty of space.

---

### Post by synapsys on 2009-06-11
Yeah install windows first and install windows on the first partition of the first disk, or else it refuses to install.

---

### Post by kd0afk on 2009-06-12
Great advice guys, thanks.

---

### Post by sxe4ever on 2009-06-12
Let us know if you have any problems with the install!!!!

---

