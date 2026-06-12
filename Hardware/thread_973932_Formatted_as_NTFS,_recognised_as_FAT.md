---
title: "Formatted as NTFS, recognised as FAT?"
date: 2008-11-07
forum: Hardware
---

### Post by Fuwisu on 2008-11-07
Hello,

I want to install windows xp on another partition. Using mkntfs I created an NTFS Partition, I rebooted my laptop with the windows xp cd, and when it showed me the only free partition on my disk I had my doubts if it was the partition I just created or my linux partition. It said:

C: Partition1(kingston) [FAT] 1906MB (1841MB Free)

I didn't select it because I was quite sure it wasn't the partition I wanted and I was afraid it would wipe off my linux.
2 reasons:  - It says FAT while it clearly is NTFS
            - Afaik 1906MB is little over 1 gigabyte, and my partition   
              is 106 gigabyte.

In ubuntu partition manager I see the following:

-dev/sda1          ext3         size : 35,81gig    used : 10,67gig
-dev/sda3          ntfs         size : 107,44gig   used : 67,80MB
-dev/sda2          extended     size:  5,79gig     ---


Can anyone clarify this please?

Thanks in advance

---

### Post by Fuwisu on 2008-11-07
Anyone?

---

### Post by taurus on 2008-11-07
Use gparted (install it if you don't have it on your system) and use it to reformat that partition to ntfs.

---

### Post by Fuwisu on 2008-11-07
Did you even read my post? I said I formatted it to NTFS, gparted doesn't work with me.

---

### Post by Coreigh on 2008-11-07
I recommend reformatting the Windows partition during the installation anyway. Windows will like it better. As long as you are sure about the partition that you are installing on you will not affect the Linux partitions.

However, if you install Windows AFTER Ubuntu (or any Linux) Windows will steal the boot record and make it difficult to dual boot. It works much better to install Windows and THEN Ubuntu. grub is a more friendly boot manager than Windows.

There are ways to repair the grub boot manager after a Windows install but I recommend researching them before you go through with your plan.

All in all if I was faced with this I would probably back up all my data and settings and start from scratch with Windows going in first.

---

### Post by Fuwisu on 2008-11-08
Thank you, but my question was actually if the partition I saw was the real partition I formatted (so I won't wipe off ubuntu) :)

---

### Post by ad_267 on 2008-11-08
Can you post the output of "sudo fdisk -l" from the terminal in Ubuntu (Applications - Accessories - Terminal). That will list all of your partitions.

---

### Post by Fuwisu on 2008-11-08
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x45759115

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4675    37551906   83  Linux
/dev/sda2           18702       19457     6072570    5  Extended
/dev/sda3            4676       18701   112663845    7  HPFS/NTFS
/dev/sda5           18702       19457     6072538+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by Fuwisu on 2008-11-08
And?

---

### Post by ad_267 on 2008-11-08
Well you have about a 100 GB NTFS partition there, a 36 GB ext3, and a 6 GB swap partition, which matches what the Ubuntu partition manager said. There's definitely no FAT32 partition there, and no partition 1906 MB. I don't know why Windows would be seeing that.

---

### Post by Fuwisu on 2008-11-08
Maybe he means the amount of space he needs to install windows?

---

### Post by Fuwisu on 2008-11-08
With "he" I mean the computer ofc :)

---

### Post by Fuwisu on 2008-11-09
Anyone got suggestions?

---

### Post by Fuwisu on 2008-11-09
bump

---

### Post by ad_267 on 2008-11-09
Doesn't look like anyone has any ideas. Maybe providing a screenshot of the Windows install screen would help.

---

### Post by Coreigh on 2008-11-10
I think the problem you are running in to here is that Windows does not like to install on an extended partition. In fact it may require being on a primary. If I read the posts right you are trying to install Windows on the extended partition (/dev/sda3 whis is on the extended patition /dev/sda2) I do not thnk this will work and probably explains why windows is not seeing it the way Linux does. I have seen the Windows installer identify an NTFS partition created by fdisk or gparted as a FAT partition, this is why I recommended installing Windows first, using the Windows installer to divide up the disk in to partitions. And then installing Ubuntu after Windows is setup and running.

---

### Post by dabl on 2008-11-10
I think Coreigh is exactly right.

The good news is, if you will boot a GParted Live CD, you can delete the extended /dev/sda2 partition and everything in it, and replace them with 2 or 3 new primary partitions (you are allowed a max of four primary partitions).  You do need a swap partition for Linux, and you'll probably have to edit /etc/fstab to fix the UUID number afterward, but you need not disturb the existing Ubuntu installation to do what you want to do.

Don't try doing it from the running Ubuntu system -- it is using swap and has that partition (at least) mounted.

Once you have changed it to primary partitions, then you can format the one you want as NTFS, for Windows, set the small one to "Linux swap" and if you made a fourth, it can be whatever you want.  Or you can skip the fourth since you have not said you needed it.  :)

---

