---
title: "Corrupt superblock, can't access my data!"
date: 2006-02-20
forum: Hardware &amp; Laptops
---

### Post by wr0x2 on 2006-02-20
I have a 300gb sata drive with partition 1 formatted as ext3. The device is /dev/sdb, or my second sata drive. Somehow, I corrupted the superblock of this drive and I can't mount the partition (containing ubuntu). I am on livecd now. How do I fix my superblock?

```

ubuntu@ubuntu:~$ sudo e2fsck -b 8193 /dev/sdb
e2fsck 1.38 (30-Jun-2005)
e2fsck: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

ran e2fsck with the reccomended arguments after fsck declined to give any useful info.

---

### Post by wr0x2 on 2006-02-20
OK I found out where my backup superblocks are stored and I'm fscking the partition as we speak. How can I swap out a backup superblock for the main block?

---

### Post by wr0x2 on 2006-02-20
fsck worked fixed my block. After messing around with grub in recovery mode everyhting works. w00t.

---

### Post by wishyjr on 2006-12-12
hi.

can you elaborate a little on how to do this? i have the same problem. 

I can access my drive (which has been formatted ext3) but there's a .wma file that just won't budge -i cant move it, delete it, rename it and i need to get rid of it as i suspect that its causing my system to run a filesystem check every time i boot up. When booting the check fails and tells me to run fsck manually. after doing that i get the same message as you posted up.

can someone please explain to me the basics of a superblock and where a so-called backup superblock is? and what has grub got to do with all this?

thanks

---

### Post by Herman on 2006-12-13
First, before you do anything, check to make sure that it is really an ext3 filesystem that this your operating system was trying to check when it gave you the warning message about the superblock being missing or corrupted. 99 times out of 100, there is nothing wrong except the user (you or I), forgot to update /etc/fstab after changing partitions around with partition editing software. 

This has nothing at all to do with Grub, but the first time people often notice that something is wrong is when they are trying to boot up. The operating system does an automatic filesystem check during boot up and  if there is a filesystem in their /etc/fstab files that doesn't seem right to  it halts with the error message about a bad superblock. 
It might even be a different partition (or filesystem) than the root filesystem that causes the filesystem check to fail. If it is, you can usually continue to boot up sucessfully by pressing 'enter', and 'ctlr+d' keys, and then edit your /etc/fstab file with the correct partition information.
About Edgy Eft's new /etc/fstab files with UUID filesystem ID added....[GO]("http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with") 

If it is in the root filesytem or if it really does seem as if it might be a bad superblock (which would be rare), filesystem checking and repair should be done from a LiveCD, on an unmounted filesystem.

**What to do if you have a bad superblock..........................**.[GO]("http://users.bigpond.net.au/hermanzone/p10.htm#superblock_restoration_frombackup")
 
If you really did have a bad superblock, you should be careful from now on about how you shut your computer down. never 'pull the plug' or power off suddenly, alway shut down properly, even if you are in a hurry.
I use UPS units on all my computers due to frequent electrical supply interruptions and out of spec electricity supply faults in my area. (Rural Australia). 
Also, if it happens again, have your computer's power supply checked by your friendly computer shop technician. Or go into BIOS and look for 'system health check' or something similar, and check your readings there are normal. (voltages etc).

Regards, Herman :D

---

### Post by bolucpap on 2007-10-24
I get the same message as the OP (except that it is /dev/hdb1), I started getting this message at the first reboot after upgrading from Feisty to Gutsy. I am running in a VMWare 6 workstation guest under an XP host. Unfortunately, my /usr is supposed to be mounted on that device, so the bootup cannot continue because all the necessary stuff is there. When I boot up with the Dapper live CD, I can see all hard drives fine and mount them, and all the data is intact. If I hit esc during grub and boot from the previous (2.6.20) kernel, the system starts up fine. It's all very weird, I am currently practicing and building my skills on a virtual ubuntu to prepare myself for the big switch to a real world ubuntu box, but I need to know what to do before I switch because it would really suck to have that problem on a non virtual box.

Thanks in advance.

---

