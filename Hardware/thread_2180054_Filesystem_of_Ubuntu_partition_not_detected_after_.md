---
title: "Filesystem of Ubuntu partition not detected after Win 8 installation"
date: 2013-10-11
forum: Hardware
---

### Post by arnold_layne2 on 2013-10-11
I installed Windows 8 over an existing dual boot of Windows 7 and Ubuntu. I thought, like all times, a simple grub reinstall would fix the issue. But this time something weird happened.

I ran boot-repair from a liveUSB, rebooted, but still didn't get GRUB. Then I started investigating a bit. Here's fdisk:

```
       Device Boot      Start         End      Blocks   Id  System
    /dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
    /dev/sda2          206848   204802047   102297600    7  HPFS/NTFS/exFAT
    /dev/sda3       204804094   283410431    39303169    5  Extended
    Partition 3 does not start on physical sector boundary.
    /dev/sda4       283410432   976773119   346681344    7  HPFS/NTFS/exFAT
    /dev/sda5       267788288   283410431     7811072   82  Linux swap / Solaris
```

Windows is in sda2 and Ubuntu in sda3 (ext3). If I try to mount it:

    sudo mount /dev/sda3 /mnt
    mount: you must specify the filesystem type

Here's parted -l:

```
    Number  Start   End    Size    Type      File system     Flags
     1      1049kB  106MB  105MB   primary   ntfs            boot
     2      106MB   105GB  105GB   primary   ntfs
     3      105GB   145GB  40.2GB  extended
     5      137GB   145GB  7999MB  logical   linux-swap(v1)
     4      145GB   500GB  355GB   primary   ntfs

```

So I'm not able to detect the file system of my Ubuntu partition! 

Here's the boot-repair log: 
[http://paste.ubuntu.com/6221718/](http://paste.ubuntu.com/6221718/)

What can I do?

---

### Post by Mark Phelps on 2013-10-11
There is no Linux partition other than swap.  sda3 is an Extended partition -- which is only a container for other partitions -- which is why you can't mount sda3. Perhaps is was previously sda4 -- but that is not a Linux filesystem (anymore).

---

### Post by coffeecat on 2013-10-11
There are about 30-32 GB of unused space in your sda3 extended partition, before the smaller swap partition. I'd put good money on that being where your Ubuntu ext3 root partition was before the Windows installer ran. Windows installers are known to do strange things with Linux logical partitions and I am saddened but not particularly surprised that it could still be happening with Windows 8. See here for some experiments I did a couple of years ago:

Windows XP installer does the impossible and "converts" a Linux logical partitition into a primary one sitting inside an extended partition - [http://ubuntuforums.org/showthread.php?t=1687873&page=2&p=10468958#post10468958](http://ubuntuforums.org/showthread.php?t=1687873&page=2&p=10468958#post10468958)

The Windows Vista installer goes one better and simply deletes the Linux logical partition - [http://ubuntuforums.org/showthread.php?t=1687873&page=2&p=10470071#post10470071](http://ubuntuforums.org/showthread.php?t=1687873&page=2&p=10470071#post10470071)

It looks as though the Windows 8 installer might be doing what the Vista one does.

My suggestion would be to run testdisk from a live CD/USB -  you have a good chance of recovering the lost partition with it. This link is a bit old, but a good start:

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

I'll see if I can find another howto for testdisk.

**EDIT**: here's another one:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Testdisk doesn't come in the box with a live CD/USB, but so long as you can connect to the internet in the live session you can install it, and it will usable as long as the live session is running.

---

### Post by arnold_layne2 on 2013-10-11
> **coffeecat said:**
> There are about 30-32 GB of unused space in your sda3 extended partition, before the smaller swap partition. I'd put good money on that being where your Ubuntu ext3 root partition was before the Windows installer ran. Windows installers are known to do strange things with Linux logical partitions and I am saddened but not particularly surprised that it could still be happening with Windows 8. See here for some experiments I did a couple of years ago:

Windows XP installer does the impossible and "converts" a Linux logical partitition into a primary one sitting inside an extended partition - [http://ubuntuforums.org/showthread.php?t=1687873&page=2&p=10468958#post10468958](http://ubuntuforums.org/showthread.php?t=1687873&page=2&p=10468958#post10468958)

The Windows Vista installer goes one better and simply deletes the Linux logical partition - [http://ubuntuforums.org/showthread.php?t=1687873&page=2&p=10470071#post10470071](http://ubuntuforums.org/showthread.php?t=1687873&page=2&p=10470071#post10470071)

It looks as though the Windows 8 installer might be doing what the Vista one does.

My suggestion would be to run testdisk from a live CD/USB -  you have a good chance of recovering the lost partition with it. This link is a bit old, but a good start:

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

I'll see if I can find another howto for testdisk.

**EDIT**: here's another one:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Testdisk doesn't come in the box with a live CD/USB, but so long as you can connect to the internet in the live session you can install it, and it will usable as long as the live session is running.

So I tried testdisk, and it infact does recognize my Linux partition. Here's a screenshot:

[IMG]http://i.imgur.com/iZIKHrR.png?1[/IMG]

The left window is showing the disk structure with the 'Free Space 32GB' being the Linux partition I want to recover.  

On the right, the 3rd partition with label 'Linux' is the one I want to recover.
Now I'm supposed to set these drives as P, L,E,D and *. Please suggest what should I do here, I don't want to mess things up further here :S

EDIT: One thing, I'm not getting an option to select 'E' for any of the partitions. So the only options I'm able to select are P,L,D,*.

---

### Post by oldfred on 2013-10-11
You are now allowed to create an extended partition. It is the container for your logical and will be automatically used.
Since your Linux partition was in the extended partition, you need to change it and make it L or logical. Partitions may be renumbered from original install but with UUIDs you should not have issues. If you had created mounts with device like /dev/sda5 then you may have to update those.

Not sure why it is showing all your other active partitions as D?

---

### Post by coffeecat on 2013-10-11
> **arnold_layne2 said:**
> 
On the right, the 3rd partition with label 'Linux' is the one I want to recover.
Now I'm supposed to set these drives as P, L,E,D and *. Please suggest what should I do here, I don't want to mess things up further here :S

EDIT: One thing, I'm not getting an option to select 'E' for any of the partitions. So the only options I'm able to select are P,L,D,*.

You need P for primary for the three NTFS partitions and L for logical for the two Linux partitions. It isn't showing you the extended partition so you don't need E. It'll sort that out for you because as Mark Phelps explained, an extended partition is simply a container for logicals.

I'm a bit worried that all 5 partitions have a D for deleted by them. Did you choose that?

---

### Post by arnold_layne2 on 2013-10-11
Not sure why it's D for all of them. I didn't change anything. Here's what I see before clicking on 'Quick Search':

[IMG]http://i.imgur.com/k4N7TZJ.png[/IMG]


After clicking on QuickSearch, I tried coffeecat's suggestion about P for all NTFS and L for both Linux and Swap. But it doesn't allow me to proceed :s

[IMG]http://i.imgur.com/XqkHh57.png[/IMG]

Choosing 'D' for Swap makes structure 'OK'.

---

### Post by arnold_layne2 on 2013-10-11
Okay so I went for it, set all drives as P, Linux as L, and my Swap as D. Completed the process, restored GRUB, rebooted into Ubuntu and re-formatted the now deleted Swap. 
Works now. It'd be nice if I could understand the problem thoguh.

---

### Post by oldfred on 2013-10-11
The problem is Windows. It rewrites partition table, but does not see Linux partitions, so when it rewrites it, it leaves off the Linux partition. I am surprised it does write the swap. 
Not sure why you had to delete swap from testdisk. You do have to update UUID in fstab if you have not.

We have seen several identical cases where Windows 8 just leaves off the Linux partition.
Probably the only only work around if not changing partition sizes is to backup partition table and restore it.

For MBR(msdos) only, not gpt
 First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

And if you change partitions sizes, then you cannot restore backup without losing changes.

---

### Post by coffeecat on 2013-10-11
> **arnold_layne2 said:**
> It'd be nice if I could understand the problem thoguh.

The original problem is what I described earlier - the failure of Windows installers to respect Linux logical partitions.

There is one other potential problem that you might want to check for before it causes confusion further down the line. Testdisk has - or at least did have - a bug where it sometimes defined the final sector in the partition table outside the physical boundary of the disk after a partition table recovery such as you have done here. This usually didn't affect the installed operating systems but it did confuse Gparted, which would show unallocated for the whole of a hard drive where there were clearly partitions. It's easy to check this out - run Gparted either from the live session or install it in your Ubuntu system and run it. If Gparted shows your partitions, forget this - you haven't been hit by the bug. If it shows "unallocated" for the whole drive, post back. It's easily fixed and I can point you in the right direction.

---

