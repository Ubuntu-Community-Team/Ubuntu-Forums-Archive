---
title: "[SOLVED] installer not recognizing existing partitions"
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by dwaggoner on 2009-01-07
I am trying to install kubuntu 8.04.1 on a dell latitude D620 laptop.  The existing partitions, as reported by fdisk, are

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            3421        6069    21278092+   c  W95 FAT32 (LBA)
/dev/sda2   *          12        3420    27382792+   7  HPFS/NTFS
/dev/sda3               1       12161    97683201    5  Extended
/dev/sda5               1          11       88294+  82  Linux swap / Solaris
/dev/sda6            6070        7343    10233373+  83  Linux
/dev/sda7            7344       12161    38700553+  83  Linux

Partition table entries are not in disk order

Currently, Windows XP and Mandriva 2007 are installed.

When trying to install kubuntu 8.04.1 from the live CD, at screen "Prepare disk space" where I should have several options, the only options presented are Guided-use entire disk and Manual.  In other words,
the installer is not recognizing my existing partitions!  On the other hand, when I boot from the live CD, all the partitions are recognized.

This has not happened when installing 8.04.1 on other machines.  Also, I get the same problem when trying to install 8.10.  From other posts in these forums, it seems that other users may be encountering similar problems, but I have seen no usable solutions.

Any help with why this is happing and a possible work around would be greatly appreciated.

Dan

---

### Post by Pumalite on 2009-01-07
Go 'Manual' and you'll probably see them all. You'll have to pick which ones you want to use. Don't forget the 4 primaries per disk rule.

---

### Post by dwaggoner on 2009-01-07
That was the second thing I tried, but it did not work.  Normally, in manual mode the existing partitions are displayed and you have the option of keeping some and doing what you will with the others.  It really does seem to be the case that the installer does not see any of the existing partitions.  The question is why and can anything be done short of nuking the existing setup?

Thanks

Dan

---

### Post by caljohnsmith on 2009-01-07
> **dwaggoner said:**
> 
```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            3421        6069    21278092+   c  W95 FAT32 (LBA)
/dev/sda2   *          12        3420    27382792+   7  HPFS/NTFS
[COLOR="Red"]/dev/sda3               1       12161[/COLOR]    97683201    5  Extended
/dev/sda5               1          11       88294+  82  Linux swap / Solaris
/dev/sda6            6070        7343    10233373+  83  Linux
/dev/sda7            7344       12161    38700553+  83  Linux

Partition table entries are not in disk order
```

It looks to me like your partition table is unfortunately corrupted, and that's why the installer is having problems with it. Note that your sda3 extended partition starts at the 1st cylinder and ends at the end of the drive, so that means all the partitions in it should be logical partitions. But you have sda1 and sda2 which are primary partitions, so it looks like your extended partition boundaries are off. Fortunately though, I think the problem might be easy to correct with sfdisk, so if you want some help fixing your partition table, how about posting the output of:
```
sudo fdisk -lu
sudo sfdisk -d /dev/sda

```
Also, assuming you can still boot into your current Mandriva install, please also post:
```
sudo blkid -c /dev/null
cat /etc/fstab
```
And we can work from there.

---

### Post by dwaggoner on 2009-01-07
Thanks for the reply.  The output of fdisk -lu is

```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1        54942300    97498484    21278092+   c  W95 FAT32 (LBA)
/dev/sda2   *      176715    54942299    27382792+   7  HPFS/NTFS
/dev/sda3              63   195366464    97683201    5  Extended
/dev/sda5             126      176714       88294+  82  Linux swap / Solaris
/dev/sda6        97498548   117965294    10233373+  83  Linux
/dev/sda7       117965358   195366464    38700553+  83  Linux

Partition table entries are not in disk order
```

The output of fsdisk -d /dev/sda is

```
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start= 54942300, size= 42556185, Id= c
/dev/sda2 : start=   176715, size= 54765585, Id= 7, bootable
/dev/sda3 : start=       63, size=195366402, Id= 5
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=      126, size=   176589, Id=82
/dev/sda6 : start= 97498548, size= 20466747, Id=83
/dev/sda7 : start=117965358, size= 77401107, Id=83
```

The output of blkid -c /dev/null is

```
/dev/sda1: LABEL="hout delay." UUID="4547-4EA1" TYPE="vfat"
/dev/sda2: TYPE="ntfs"
/dev/sda5: TYPE="swap" UUID="ecd315f9-654d-41ef-afc4-616901a0e357"
/dev/sda6: UUID="03ff376b-412a-405d-9806-4e11d4dda504" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda7: UUID="4c1dbf5b-46f7-43a4-9ccd-3002bbc77cfa" SEC_TYPE="ext2" TYPE="ext3"
```

The output of cat /etc/fstab is

```
/dev/sda6 / ext3 noatime 1 1
/dev/sda1 /common vfat umask=0,iocharset=utf8 0 0
/dev/sda7 /home ext3 noatime 1 2
/dev/sr0 /mnt/cdrom auto umask=0,users,iocharset=utf8,noauto,ro,exec 0 0
//192.168.1.5/Volume_1 /mnt/dlink smbfs noauto,users,username=%,uid=daniel,gid=daniel 0 0
none /proc proc defaults 0 0
/dev/sda2 /windows ntfs umask=0,nls=utf8,ro 0 0
/dev/sda5 swap swap defaults 0 0

```

I can boot into Mandriva and Windows just fine and when I use the live CD to boot into Kubuntu, it can read all of the hard drive partitions.  To be perfectly honest, dealing with partitions makes me very cautious and I really appreciate the help you are giving me.

Dan

---

### Post by caljohnsmith on 2009-01-07
OK, to correct your partition table problem, we will need to make your swap sda5 partition a primary partition, and then correct the starting point of the sda3 extended partition. Fortunately it is not hard to do this with sfdisk, so how about downloading the attached "partition_table.txt" to your desktop, and then do:
```
sudo sfdisk --force /dev/sda < ~/Desktop/partition_table.txt
```
That will produce a lot of output, including some warnings, so don't be alarmed; please post the output though so I can check it. Next boot your Live CD, open a terminal (or Konsole in Kubuntu), and do:
```

sudo fdisk -lu
sudo sfdisk -d /dev/sda
sudo grub
grub> root (hd0,4)
grub> setup (hd0)
grub> quit
```
And please post the output of the all the above commands before doing the "quit". Next do:
```
sudo mount /dev/sda5 /mnt
gksudo gedit /mnt/etc/fstab
```
Or use "kdesu kate" instead instead of "gksudo gedit" in the command above if you are using your Kubuntu Live CD, and then change the fstab to:
```
/dev/[COLOR="Blue"]sda5 [/COLOR]/ ext3 noatime 1 1
/dev/sda1 /common vfat umask=0,iocharset=utf8 0 0
/dev/[COLOR="Blue"]sda6[/COLOR] /home ext3 noatime 1 2
/dev/sr0 /mnt/cdrom auto umask=0,users,iocharset=utf8,noauto,ro,exec 0 0
//192.168.1.5/Volume_1 /mnt/dlink smbfs noauto,users,username=%,uid=daniel,gid=daniel 0 0
none /proc proc defaults 0 0
/dev/sda2 /windows ntfs umask=0,nls=utf8,ro 0 0
/dev/[COLOR="Blue"]sda4[/COLOR] swap swap defaults 0 0
```
Next open up your menu.lst:
```
gksudo gedit /mnt/boot/grub/menu.lst
```
And for all the Mandriva entries, change their "root" line to use (hd0,4) and not the current (hd0,5). Then reboot, and you should be able to boot into Mandriva again if all goes well. Let me know how it goes or if you run into problems. :)

---

### Post by dwaggoner on 2009-01-07
Wow, thanks for the really quick reply.  It's getting late on the east coast, so I will probably try this tomorrow or Friday.  To understand what is going on, it seems the the info for the extended partition (which is the partition that gets subdivided into smaller partitions?) somehow got corrupted and sfdisk can be used to fix this.  After this fix the two linux partitions will be the pieces in the extended partitions and we will have to fix all the names.  Who knows what is going on with sda4?

As I said before, dealing with partitions makes me cautious.  Of course, I have backed up all my data and I do not really care if the Mandriva or the fat32 partitions get hosed since they may well be used for the Kubuntu installation, but the Windows XP partition is a different matter.  If this partition is damaged, then I will have to grovel before a coworker to get Windows, and some Windows applications, reinstalled.  While I know that you cannot guarantee that this will work, I am curious -- if this were your machine and the cost of failure is some groveling, would you attempt this?

Again, thanks much for your time.

Dan

---

### Post by caljohnsmith on 2009-01-08
> **dwaggoner said:**
> While I know that you cannot guarantee that this will work, I am curious -- if this were your machine and the cost of failure is some groveling, would you attempt this?

Again, thanks much for your time.

Dan
I can understand and respect your cautiousness about changing your HDD's partition table; but to answer your question, yes, I would not hesitate to do it if it were my own machine, because in fact I have done the exact same type of repartitioning with sfdisk on my own computer just recently. I changed my swap partition, which was a primary partition, into a logical partition inside my extended partition, so I can resize one of my linux partitions to make room for another primary partition. And in case it makes you feel at little more at ease, I've helped several people in the forums to correct their partition tables using the same sfdisk technique with no problems. Keep in mind that when we use sfdisk, we are just changing the partition table in the MBR (Master Boot Record) and the partition table in each of the EBRs (Extended Boot Records) associated with each logical partition, so it's not like we are moving/resizing/formatting partitions; we are just changing a few numbers in the partition tables. Also, because you posted the output of "sfdisk -d", we have a perfect online backup of your present partition table. So the bottom line is I don't think you will have to grovel to your coworker for another copy of Windows; but like I said, I totally respect your wanting to exercise caution, yet I think you will be just fine. :)

---

### Post by dwaggoner on 2009-01-08
I decided to try to repair the partition table.  The outcome was good, but not perfect.  First the output you requested:

```
[root@localhost daniel]# sfdisk --force /dev/sda < /home/daniel/Desktop/partition_table.txt
Checking that no-one is using this disk right now ...
BLKRRPART: Device or resource busy

This disk is currently in use - repartitioning is probably a bad idea.
Umount all file systems, and swapoff all swap partitions on this disk.
Use the --no-reread flag to suppress this check.

Disk /dev/sda: 12161 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1       3420    6068    2649   21278092+   c  W95 FAT32 (LBA)
/dev/sda2   *     11    3419    3409   27382792+   7  HPFS/NTFS
/dev/sda3          0+  12160   12161-  97683201    5  Extended
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5          0+     10      11-     88294+  82  Linux swap / Solaris
/dev/sda6       6069+   7342    1274-  10233373+  83  Linux
/dev/sda7       7343+  12160    4818-  38700553+  83  Linux
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1      54942300  97498484   42556185   c  W95 FAT32 (LBA)
/dev/sda2   *    176715  54942299   54765585   7  HPFS/NTFS
/dev/sda3      97498485 195366464   97867980   5  Extended
/dev/sda4           126    176714     176589  82  Linux swap / Solaris
/dev/sda5      97498548 117965294   20466747  83  Linux
/dev/sda6     117965358 195366464   77401107  83  Linux
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed
Reboot your system now, before using mkfs

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)
```

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1        54942300    97498484    21278092+   c  W95 FAT32 (LBA)
/dev/sda2   *      176715    54942299    27382792+   7  HPFS/NTFS
/dev/sda3        97498485   195366464    48933990    5  Extended
/dev/sda4             126      176714       88294+  82  Linux swap / Solaris
/dev/sda5        97498548   117965294    10233373+  83  Linux
/dev/sda6       117965358   195366464    38700553+  83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo sfdisk -d /dev/sda
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start= 54942300, size= 42556185, Id= c
/dev/sda2 : start=   176715, size= 54765585, Id= 7, bootable
/dev/sda3 : start= 97498485, size= 97867980, Id= 5
/dev/sda4 : start=      126, size=   176589, Id=82
/dev/sda5 : start= 97498548, size= 20466747, Id=83
/dev/sda6 : start=117965358, size= 77401107, Id=83
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
ubuntu@ubuntu:~$
```

These two proceedures went well, but

```
grub> root (hd0,4)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

grub>
```

Also, the file /boot/grub/menu.lst does not exist and I could not boot into Mandriva.  I am not sure if Mandriva used grub as its boot loader.  

On the good side, I could boot into Windows -- no groveling for me!  Unless you have a better idea, I plan to install Kubuntu over the FAT32 partition and after that I may be able to boot into either Kubuntu or Mandriva or Windows.  However, I will not do that until the weekend.

Again, I thank you for all your expert help.

Dan

---

### Post by caljohnsmith on 2009-01-09
When you ran the Grub commands, did you make sure to do it as root user, i.e. with "sudo grub"? That is often a cause of getting that file not found error when actually the Grub files exist. I looked over your new partition table, and it looks like everything went as planned; all the partition start/end points are what they should be. So in order to get a better idea of which steps we need to do to get Grub working again and booting all your OSes, how about doing:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post and we can work from there.

---

### Post by dwaggoner on 2009-01-09
Attached are the results of the script.

Thanks,

Dan

---

### Post by caljohnsmith on 2009-01-09
Great, it looks like all your partitions are just fine since they all mounted OK and are readable; but you were right about Mandriva using Lilo instead of Grub it appears. How about trying the following:
```
sudo mount /dev/sda5 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt /bin/bash
liloconfig
exit
```
And see if you can get through the "liloconfig" prompts OK in order to reinstall Lilo to your MBR for Mandriva. If you run into problems, please let me know exactly what errors you might receive. We can work from there.

---

### Post by dwaggoner on 2009-01-09
Here is the output of the commands you suggested I run.

```
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo chroot /mnt /bin/bash
bash-3.1# liloconfig
bash: liloconfig: command not found
bash-3.1# liloconfig
bash: liloconfig: command not found
bash-3.1# sudo liloconfig
sudo: liloconfig: command not found
bash-3.1# exit

```

After some poking around, it seems that the file liloconfig should be in the /usr/sbin directory, at least in ubuntu.  That file is not in the Mandriva installation.  Below is the contents of the Mandriva lilo.config file

```
# File generated by DrakX/drakboot
# WARNING: do not forget to run lilo after modifying this file

default="linux"
boot=/dev/sda
map=/boot/map
keytable=/boot/us.klt
menu-scheme=wb:bw:wb:bw
compact
prompt
nowarn
timeout=6000
message=/boot/message
image=/boot/vmlinuz
	label="linux"
	root=/dev/sda6
	initrd=/boot/initrd.img
	append=" splash=verbose"
	vga=788
image=/boot/vmlinuz
	label="linux-nonfb"
	root=/dev/sda6
	initrd=/boot/initrd.img
	append=" splash=verbose"
image=/boot/vmlinuz
	label="failsafe"
	root=/dev/sda6
	initrd=/boot/initrd.img
	append="failsafe"
other=/dev/sda2
	label="windows"
	table=/dev/sda
```

Surely the sda6 in this file should be sda5 now.  What do you say about making this change, running lilo, and then seeing if I can boot into Mandriva.

Dan

---

### Post by caljohnsmith on 2009-01-09
> **dwaggoner said:**
> 

Surely the sda6 in this file should be sda5 now.  What do you say about making this change, running lilo, and then seeing if I can boot into Mandriva.

Dan
Yes, I agree, the references in the lilo config file should use sda5 now. I've never used lilo for anything other than as a replacement for a Windows MBR, so I'm sorry I can't be of more help about restoring lilo. I would have to research it, because I thought "liloconfig" was the way to reinstall lilo; but I must be wrong. Let me know how that goes.

---

### Post by dwaggoner on 2009-01-09
Success!

A million thanks.  While I would not have been unhappy continuing with the Mandriva distro, it was getting long in the tooth.  I've been using Ubuntu for a few months now on other machines and am very pleased with it.  I have used linux for the last seven or so years and Ubuntu is the first distribution that I would recommend to a novice user - it is a really clean easy to use setup.

Dan

---

### Post by caljohnsmith on 2009-01-09
> **dwaggoner said:**
> Success!

A million thanks.  While I would not have been unhappy continuing with the Mandriva distro, it was getting long in the tooth.  I've been using Ubuntu for a few months now on other machines and am very pleased with it.  I have used linux for the last seven or so years and Ubuntu is the first distribution that I would recommend to a novice user - it is a really clean easy to use setup.

Dan
That's great news, Dan. Glad to hear it's working, so you should be able to install Kunbuntu/Ubuntu now without any partition table problems. Cheers and have fun with all your OSes. :)

---

