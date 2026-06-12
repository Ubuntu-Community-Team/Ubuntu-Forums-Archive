---
title: "Intalling Xp on extended parttion after installed ubuntu on primary partition"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by Texasguy on 2009-10-17
Hi Friends
    I have Ubuntu 9 Jaunty installed on primary partition c:(file system reiserfs) and XP on extended partition drive d:(file system NTFS).I need to reinstall XP on drive d:. But during installation of XP, it tells that to copy XP boot files the parttion c: needs to be changed to XP known file system. If i change the filesystem on partition c: where ubuntu is installed to fat32 or ntfs, will I be able to recover ubuntu data and boot into it.

Thanks
TG

---

### Post by norm7446 on 2009-10-17
You will need to install XP first if you are doing a dual boot. Due to the Windows having to be on the first part of the H/Drive. It neither can nor wont go anywhere else. Your only option is to install XP on an other Drive, that way you will not lose your Ubuntu partition

---

### Post by Bartender on 2009-10-17
I'm not clear on what it is you're trying to accomplish, but see at least two problems here.  Windows won't work from within an extended partition.  The Windows OS has to be in a primary partition.

Ubuntu can run from an extended partition.

Windows partitions have to be NTFS (or FAT of course, but that would be pointless).

The Ubuntu OS has to be installed to a Linux file system, which would be ext3 or ext4.  There are older file systems for Linux, but just like using FAT for Windows, there would be no point in doing so.

Windows really should be installed first, just because it's easier to do it that way.  So in a nutshell you've got it backwards.

Can you just copy your Ubuntu personal data to an external device, and start over?  Or maybe clone the Ubuntu install to a different drive, then install Windows, then place Ubuntu in an extended partition, etc.  That might be a little too complex.

---

### Post by oldfred on 2009-10-17
It is a lot easier to install Windows first as everyone else says. Do you have a boot flag on for the c: partition sda1? Ubuntu does not need that and that may confuse the windows installer. Windows will not see the ext3 ubuntu file system.

Backup whatever from windows, and use gparted to  delete the old windows partiton and if necessay temporarily delete swap. You should be able to create and format a new ntfs partition as primary, so the XP installer will see it. Do not forget to put back a swap partition, it can be in a extended partition. 

If you do delete swap you will create a new UUID for it, and will have to modify fstab in your ubuntu install to get it working again.

---

### Post by Texasguy on 2009-10-18
Thank you all to look into my issue.

These are the partitions on my hard drive
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1217     9775521   83  Linux
/dev/sda2            1218        4865    29302560    f  W95 Ext'd (LBA)
/dev/sda5            1218        2421     9671098+   7  HPFS/NTFS
/dev/sda6            2422        3625     9671098+   b  W95 FAT32
/dev/sda7            3626        4865     9960268+   b  W95 FAT32

      As you can see on Primary partion(/dev/sda1,drive c) I have ubuntu installed, and on Extended partion(/dev/sda5,logical drive d) I have Xp installed, the other logical drives(/dev/sda6,/dev/sda7) on the extended partition I have some data. GRUB is the boot manager using which I can dual boot Ubuntu and XP. No if I want to re-install XP without disturbing ubuntu I will need to delete the extended partition, I assume my other logical drives(/dev/sda6,/dev/sda7) will also get deleted. Is there any other way I can install XP on drive d without disturbing the primary  partitons and logical drives. Is there any way by which I can convert part of the extended partition to primary and install XP. In case in future if i want to re-install XP and ubuntu independently without requring to install the other OS when I re-install one of these, how should I partion my hard drive and on what parttion or logical drive  I should keep Ubuntu and XP.

Thanks
TG

---

### Post by bulldog on 2009-10-18
As other people have told,it's a windows behavior that it wants to be at the first partition on the first hdd.
Windows should be installed on a primary partition,ubuntu doesn't mind if it's on a primary or an extended partition.
For the future I would recommend to make at least two primary partitions,and put the rest of your partitions in an extended partition.
This way you have always a primary in spare.
There is practical no difference between the behavior of a primary or a logical partition,so there is nothing to gain,BUT windows exist to be on a primary that's all.

Now we are talking about making new partitions,how about a separate /home?
It can be very useful when you have to do a re-install or if you want to install a second copy of any distro or even ubuntu.
I would not use any FAT32 partition anymore if I where you,just use NTFS,but that's just my opinion.

---

### Post by presence1960 on 2009-10-18
[https://www.linuxquestions.org/questions/linux-software-2/grub-windows-on-logical-partition-607114/](https://www.linuxquestions.org/questions/linux-software-2/grub-windows-on-logical-partition-607114/)

See there. Supposedly you have to edit the boot.ini file to get windows to boot from an extended partition. Haven't tried it myself though.

If that does not work then you need to install windows to a primary partition- **and NO you don't need to install windows first, you have a working Ubuntu OS so let it be.**

Create a primary NTFS partition for windows, install to it. Windows will overwrite the MBR so you will need to restore GRUB to MBR like this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,0)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,0)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

Then you will have to boot into Ubuntu and edit your menu.lst to add windows to the GRUB menu. If you don't know how to do that post back when windows is installed and GRUB is restored.

**_You don't have to wipe Ubuntu to install windows. That is a lot of unneccessary work just to avoid 2 minutes of using terminal to restore GRUB and add windows to GRUB menu!_**

---

### Post by presence1960 on 2009-10-18
> **bulldog said:**
> As other people have told,it's a windows behavior that it wants to be at the first partition on the first hdd.


That is not true I have used windows XP & Vista on sda4. What windows requires is that it's bootloader be on the first hard disk to boot. It is suggested that windows be on a primary partition also. If windows is on the first hard disk to boot then GRUB will take care of it with no added measures. But if windows is on another disk in the boot order in BIOS that is when you need the map lines in menu.lst to "trick" windows into thinking it is on the first disk to boot. here is an example: windows is on the second disk to boot in BIOS:

```
title           Windows XP Professional
rootnoverify    (hd1,1)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1
```

**Why is there still all this confusion about dual booting Linux & windows? **There are a lot of untrue myths propagated in this forum about this. A lot of people say it is easier to install windows first. True if your hard disk is empty. But what if you have a working Linux OS and want to add windows? Hardly easier to wipe your linux OS and then install windows first just to avoid 2 minutes of using terminal to restore GRUB and then edit your menu.lst to add the windows entry.

---

### Post by bulldog on 2009-10-18
For your info,I have three linux distro's running along side with XP and Windows 7 on three hdd's.
I know what I'm doing,and I agree with you on several points.
However not everyone knows how to do things.
And the easiest way is to create a new primary for windows.
We can make things very difficult and complex,but you can ask yourself,is this what topic starter is looking for?
I always tell people to create a separate /home,so a re install is much easier to do,without loosing to much data.
We all are trying to help the topic starter,and some tips are better than others,but we all try to help,and that's what counts in my opinion.

---

### Post by presence1960 on 2009-10-18
> **bulldog said:**
> For your info,I have three linux distro's running along side with XP and Windows 7 on three hdd's.
I know what I'm doing,and I agree with you on several points.
[B]However not everyone knows how to do things.
[/B]

Exactly, and that's why the OP posted on here. We should teach those who do not know how to do things, instead of treating them as if they are incapable of learning. I still stand by my words- It is way easier to install windows after linux than it is to wipe your linux and install windows then reinstall Ubuntu. That is a lot of work. it is way easier to install windows to aprimary partition and then with our help restore GRUB and add windows to menu.lst

How is one supposed to learn linux if we don't show them how? It is not difficult to use the terminal for 2 minutes to restore GRUB and add windows to menu.lst, unless one who has not ever done it is left to his/her own devices. But that is where **_WE_** come in.

Stop babying people and keeping them in the dark. Educate them about Linux so they can become for the most part self sufficient.

---

### Post by bulldog on 2009-10-18
Well.I leave you to it then :)

---

### Post by Bartender on 2009-10-18
> **Texasguy said:**
> I need to reinstall XP on drive d:. But during installation of XP, it tells that to copy XP boot files the parttion c: needs to be changed to XP known file system.

I gotta go with bulldog on this one.  The OP wants to reinstall XP anyway.  Reinstalling Ubuntu is simple compared to XP.  It's certainly not a half-day ordeal like XP is, and once the install has started you can walk away.  Unlike XP, which stops along the way and requires user input.

The OP's partitioning is backwards and inside-out.  Windows on logical??  Why not just do it right once and be done with it?

---

### Post by bulldog on 2009-10-18
TY Bartender,but it can be even more simple.
If he just copies his data from all the partitions in the extended partition,remove all logical partitions and finally removes the extended partition,he can make new partitions,without deleting his ubuntu install.
Just create a new primary for windows and then create an extended and logical partitions if he wants to do so.
There can and will be an issue with the fstab file,but we can catch that one.

---

### Post by presence1960 on 2009-10-18
All he needs to do is backup his windows data, delete the logical windows partition, create a primary NTFS partition and install windows to the primary. Then restore GRUB and windows to menu.lst

Why are we afraid to tell people the truth and then walk them through the steps so they not only learn Linux, but gain confidence in performing tasks with Linux?

I still find it hard to believe one would want to reinstall a perfectly good Ubuntu install to install windows. Restoring GRUB and adding windows to menu.lst is not a task that requires a great degree of computer knowledge. As a matter of fact it will take a newbie all of two to three minutes to perform those tasks in terminal, even if they copy and paste the commands in terminal.

We should be teaching new users how to use Linux, not pampering them because we assume they aren't capable of performing the most basic tasks in Linux.

I thank God I wasn't taught that way in here. I was told how to install windows after Linux,  given precise directions on how to do it and then I went ahead & tried. Got stuck once in terminal but with a little help got it right.

I still stick by my words and say that not only is it stupid to remove a perfectly good OS to install another one, but counterproductive as the OP will not learn a thing about Linux and the boot process as it pertains to MBR.

P.S. that is why I believe I am good at GRUB and boot problems because when I did it the way I was told to everything made sense and the light bulb went off in my mind. I finally understood that the only thing that happens when you install windows after linux is that GRUB gets overwritten by windows on the MBR. And the solution is to simply restore GRUB to MBR then add the windows entry to menu.lst

It is so easy a caveman can do it and I don't have the right to assume anyone is not capable of doing the same. The best things that ever happened to me with Linux is when people gave me straightforward solutions and explained why it works. With their help I was able to learn a lot. I still need to learn and admire the people in here who are willing to show me the ropes because they don't decide that I am not capable of doing what they are showing me.

---

