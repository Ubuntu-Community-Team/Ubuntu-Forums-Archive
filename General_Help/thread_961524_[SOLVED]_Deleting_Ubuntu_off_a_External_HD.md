---
title: "[SOLVED] Deleting Ubuntu off a External HD"
date: 2008-10-28
forum: General Help
---

### Post by RichieH on 2008-10-28
I really want to delete Ubuntu from my external HD, but the thing is I've tried to run XP Installation over it and still nothing. Ubunto gobbled over 600+GB of my External and I really need it back, anyone mind helping me? I'm already frustrated as it is.

---

### Post by Titan8990 on 2008-10-28
Have you tried reformatting via fdisk from the live CD?

---

### Post by RichieH on 2008-10-28
I really have no clue what do with the repartitioning. I am still a novice on how it works and right now it has me over the edge.

---

### Post by Titan8990 on 2008-10-28
Alright, first boot the live CD.

Now you need to find you drive letter given to your device. I typically find this based on the size of the drive. Issue the following command:

sudo fdisk -l


I get these results:

```
jordan@einstein:~$ sudo fdisk -l
[sudo] password for jordan:

Disk /dev/sda: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10c310fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux

Disk /dev/sdb: 250.0 GB, 250057219584 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b3151

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29920   240332368+  83  Linux
/dev/sdb2           29921       30401     3863632+  82  Linux swap / Solaris
```

Here I can see that my external is /dev/sda1.


So, we issue the fdisk command again only this time we specify which drive we are going to reformat:

sudo fdisk /dev/sda1

Then you will be presented with an interactive mode.

hit d and then enter to delete the partition then w followed by enter to write the changes.

**This will wipe all data on the partition.**


Good luck.

> I really have no clue what do with the repartitioning. I am still a novice on how it works and right now it has me over the edge.

The key to learning and understanding computers is patience and willingness to fight through frustration.

Out of curiosity, how did you manage to eat that much space? I have many dual boot systems and my largest HDD is 320GB. I have never filled a drive...

---

### Post by RichieH on 2008-10-28
Okay then, let's see if this would work. If I know where to run it.

---

### Post by Titan8990 on 2008-10-28
Applications -> Accessories -> Terminal

---

### Post by caljohnsmith on 2008-10-28
Personally I would use Ubuntu's GUI partition editor, gparted. You can access it under System > Admin > Partition Editor I think, or you can always run it by pressing ALT + F2, and entering:
```
gksudo gparted
```

---

### Post by RichieH on 2008-10-28
Still nothing, I've been trying and trying and nothing it still says I have little memory. I know I have like 620+GB Unused that was taken away from the Linux OS

---

### Post by Titan8990 on 2008-10-28
What is it that you tried?

---

### Post by RichieH on 2008-10-28
What you told me and yet nothing has worked, both parts. Look this is what it tells me when I go to gparted:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19ff272c

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9091    73023426    c  W95 FAT32 (LBA)
/dev/sda2            9092       91025   658134855   83  Linux
/dev/sda3           91026       91201     1413720    5  Extended
/dev/sda5           91026       91201     1413688+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 



```

---

### Post by Titan8990 on 2008-10-28
Looks like /dev/hda1 is a Windows drive and /dev/sda is your Linux drive.


Delete all the partitions off of /dev/sda. And again, you will lose all data on the drive.

---

### Post by RichieH on 2008-10-28
So this is what I do just to be sure, I do sudo fdisk /dev/sda then Enter, Then I press D and hit enter, after that I press W and also hit Enter.

Correct?

---

### Post by Titan8990 on 2008-10-28
Yes, but in my first example I assumed the drive was one partition. After you have hit d you will be asked which partition to delete.

Hit d followed by your partition number (which will be 1, 2, 3, and 5) until they have all been deleted. Then hit w to write the changes.

---

### Post by RichieH on 2008-10-28
I did as you told me and this is what i got:
```
ubuntu@ubuntu:~$ sudo fdisk /dev/sda

The number of cylinders for this disk is set to 91201.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): d
Partition number (1-5): 5

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.
ubuntu@ubuntu:~$ sudo fdisk /dev/sda

The number of cylinders for this disk is set to 91201.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): d
Partition number (1-5): sda2
Partition number (1-5): 2

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.



```

---

### Post by Titan8990 on 2008-10-28
Show the results of the following command:


sudo mount

---

### Post by RichieH on 2008-10-28
Here they are, seems every time I use the partition it still happens with that error as you've seen.

```
ubuntu@ubuntu:~$ sudo mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/sda1 on /media/My Book type vfat (rw,nosuid,nodev,shortname=mixed,uid=999,utf8,umask=077,usefree)
ubuntu@ubuntu:~$ 



```

---

### Post by Titan8990 on 2008-10-28
issue this command before doing fdisk again:


sudo umount /dev/sda1

---

### Post by RichieH on 2008-10-28
This is what I got after the command

```
ubuntu@ubuntu:~$ sudo umount /dev/sda1
ubuntu@ubuntu:~$ sudo umount /dev/sda1
umount: /dev/sda1: not mounted
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19ff272c

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/sda (Sun disk label): 255 heads, 63 sectors, 25665 cylinders
Units = cylinders of 16065 * 512 bytes

   Device Flag    Start       End    Blocks   Id  System
ubuntu@ubuntu:~$ sudo fdisk /dev/sda




```

---

### Post by Titan8990 on 2008-10-28
umount should not remove the device from the fdisk table like shown. So nothing happened when you did fdisk /dev/sda after umount?

---

### Post by RichieH on 2008-10-28
It just asked me what command I should use.

---

### Post by Titan8990 on 2008-10-28
ehh, I actually meant for you to follow all the steps that you did in post #14 after doing umoumt.

Sorry for the confusion.

---

### Post by RichieH on 2008-10-28
I actually did all that I thought I made an error... So I did it by mistake without knowing what I was doing then I umount it.

---

### Post by Titan8990 on 2008-10-28
Well, since it is no longer showing a partition table for the drive then it could have worked successfully one of the times you tried.


Pop in your Windows disk and see if the drive is recognized (although I have a feeling it will never detect a USB drive during installation).

---

### Post by RichieH on 2008-10-28
Ever since I did umount my External HD is not being detected from any of my two computer.

---

### Post by Titan8990 on 2008-10-28
What are your other computers running?

---

### Post by RichieH on 2008-10-28
I am Running a Windows XP OS on my Emachine ( The one I was working on), and a Windows Vista OS on a Gateway. And it wont recognize the External HD anymore. It shows its there in Safely Remove Hardware and thats it.

---

### Post by Titan8990 on 2008-10-28
Where are you checking to see if the drive is present?

---

### Post by RichieH on 2008-10-28
It works now thank you very much for all of your help ^^

---

### Post by Titan8990 on 2008-10-29
Good to hear. Don't forget to mark your thread as solved.

---

