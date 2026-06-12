---
title: "How do I put XP back into a partition?"
date: 2009-07-11
forum: Installation &amp; Upgrades
---

### Post by creeper112 on 2009-07-11
Hello all,
 I'm a complete beginner when it comes to Ubuntu.  I've did a complete partition for ubuntu and wiped out my windows XP.  I enjoyed having ubuntu 8.10 but I want to do a dual partition with windows XP again.  I've tried booting from a live CD and when I tried doing the manual partition XP was nowhere to be found...I still want ubuntu, but I also want to use XP but I can't install it.  Can someone please help me.  Ive did a search, but there is no easy way to do it.  Please if someone knows of a easy step by step way that'll be great.  Thanks!

---

### Post by merlinus on 2009-07-11
Maybe I do not understand, but how can you expect the ubuntu partitioner to find something that is not there?

You can shrink your ubuntu partition to make space into which you can install xp.  Format it as ntfs beforehand, though, or xp will not see it.

Best to use gparted live cd:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by Mark Phelps on 2009-07-11
You have a couple of different options ...

If you want Ubuntu to automatically sense the presence of XP and add an entry to its boot menu, you will have to remove Ubuntu, wipe out the partitions, install XP, and then install Ubuntu.

If you instal XP now, you may have problems if it's not the first partition on the drive, so in that case, you would need to do the following:
1) Go to distrowatch.com and download the GParted LiveCD.  Burn that to a CD, and boot from that CD.
2) Once booted, use the partition editor to shrink the Ubuntu partition and move it to the right -- to make room for an XP partition.  Don't create an XP partition, just leave space for it.
3) Boot from your XP CD and install XP into the unallocated space.  That will overwrite the GRUB entry in the MBR, so you won't be able to boot into Ubuntu anymore.
4) Using your Ubuntu LiveCD, you can boot into it and restore GRUB using the link below:
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")
5) Boot back into Ubuntu and add a stanza to the /boot/grub/menu.lst file for MS Windows by opening a terminal and entering the following: "gksudo gedit /boot/grub/menu.lst". 
6) Then, enter the following lines  after the linux boot entries:
title		Windows XP
rootnoverify	(hd0,0)
savedefault
chainloader +1
7) save the changed file, exit Ubuntu, and reboot.  You should now see a GRUB menu with options for Ubuntu and Windows XP.

If you have any problems, just post back and we'll help

---

### Post by bigken on 2009-07-11
the simplest way for you would be to backup your data and boot from your windows xp cd 
and delete what ever is there then create a new partition for windows xp leave what is left 
for ubuntu after you have installed windows reinstall ubuntu

---

### Post by creeper112 on 2009-07-11
> **Mark Phelps said:**
> You have a couple of different options ...

If you want Ubuntu to automatically sense the presence of XP and add an entry to its boot menu, you will have to remove Ubuntu, wipe out the partitions, install XP, and then install Ubuntu.

If you instal XP now, you may have problems if it's not the first partition on the drive, so in that case, you would need to do the following:
1) Go to distrowatch.com and download the GParted LiveCD.  Burn that to a CD, and boot from that CD.
2) Once booted, use the partition editor to shrink the Ubuntu partition and move it to the right -- to make room for an XP partition.  Don't create an XP partition, just leave space for it.
3) Boot from your XP CD and install XP into the unallocated space.  That will overwrite the GRUB entry in the MBR, so you won't be able to boot into Ubuntu anymore.
4) Using your Ubuntu LiveCD, you can boot into it and restore GRUB using the link below:
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")
5) Boot back into Ubuntu and add a stanza to the /boot/grub/menu.lst file for MS Windows by opening a terminal and entering the following: "gksudo gedit /boot/grub/menu.lst". 
6) Then, enter the following lines  after the linux boot entries:
title		Windows XP
rootnoverify	(hd0,0)
savedefault
chainloader +1
7) save the changed file, exit Ubuntu, and reboot.  You should now see a GRUB menu with options for Ubuntu and Windows XP.

If you have any problems, just post back and we'll help

I did as followed.  I used the gparted to make room for the xp partition.  After that I tried to boot the xp windows and it stopped and stated to prevent damaged the installed has been stopped.  It wont let me boot the xp disc...please help.... should I deleted the whole partition and start fresh?

---

### Post by presence1960 on 2009-07-11
> **bigken said:**
> the simplest way for you would be to backup your data and boot from your windows xp cd 
and delete what ever is there then create a new partition for windows xp leave what is left 
for ubuntu after you have installed windows reinstall ubuntu

Why would you tell someone to remove a perfectly good OS? I know a bunch of people on here proclaim that you must install Windows first. That is a bunch of bolderdash and misinformation. See these links:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

with all the resources in this community and on the web why are we still giving bad information on this subject? I think it is perpetuated because those proclaiming you must install windows first don't understand the installation process for windows and/or Linux and the boot process. When you install windows after Linux it must be on a primary partition (it doesn't have to be first partition on the disk). Windows will overwrite GRUB and the windows bootloader will take over next time you boot. To restore GRUB boot off the Ubuntu live CD and restore GRUB to MBR like this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

In #6 use setup (hd0) or whatever HDD your booting from. Then add a windows entry in menu.lst so it shows on the GRUB menu at boot.

Don't uninstall a perfectly good Ubuntu OS to reinstall windows. it is not necessary and don't take my word for it, read the documentation and educate yourself.

here is my setup:> 

raz@sabayon ~ $ sudo fdisk -l

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

Password: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d179

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       25064   201326548+  83  Linux
/dev/sda2   *       25065       30401    42869452+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7a57e45

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2863    22997016   83  Linux
/dev/sdb2            2864        3361     4000185   82  Linux swap / Solaris
/dev/sdb3            3362       19457   129291120    5  Extended
/dev/sdb5   *        3362        6625    26218048+  83  Linux
/dev/sdb6            6626        9889    26218048+   7  HPFS/NTFS
/dev/sdb7            9890       19457    76854928+   7  HPFS/NTFS

sda1 is a Linux data partition, sda2 is windows 7 RC (and installed after Ubuntu) sdb1 is Jaunty, sdb5 is sabayon 4.1 Linux

---

### Post by presence1960 on 2009-07-11
Here is what I have done in the past and still would do:

1.Boot gparted Live CD and resize Ubuntu partition to create space for XP install. Then create an NTFS partition from that space. Mark's suggestion of leaving it unallocated will also work.
2. Boot from the XP install CD and install to the new partition or unallocated space
3. After XP is installed and booted into to make sure it is successfully working boot from Ubuntu live CD and follow instructions on how to restore GRUB in my previous post. Then the only thing left to do is to edit your menu.lst file and add a windows entry so it will show up on your GRUB menu when you boot your rig.

P.S. I see you have a failed install message. Boot into Ubuntu and open a terminal and run this command > sudo fdisk -l that is a lowercase L. post the output from that command here so we can see your disk setup.

---

### Post by raymondh on 2009-07-11
> **presence1960 said:**
>  you must install windows first. That is a bunch of bolderdash and misinformation. See these links:

[https://help.ubuntu.com/community/recoveringubuntuafterinstallingwindows](https://help.ubuntu.com/community/recoveringubuntuafterinstallingwindows)
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

when you install windows after linux it must be on a primary partition (it doesn't have to be first partition on the disk). Windows will overwrite grub and the windows bootloader will take over next time you boot. 

+ 1

---

### Post by bigken on 2009-07-12
> **presence1960 said:**
> Why would you tell someone to remove a perfectly good OS? I know a bunch of people on here proclaim that you must install Windows first. That is a bunch of bolderdash and misinformation. See these links:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

with all the resources in this community and on the web why are we still giving bad information on this subject? I think it is perpetuated because those proclaiming you must install windows first don't understand the installation process for windows and/or Linux and the boot process. When you install windows after Linux it must be on a primary partition (it doesn't have to be first partition on the disk). Windows will overwrite GRUB and the windows bootloader will take over next time you boot. To restore GRUB boot off the Ubuntu live CD and restore GRUB to MBR like this:




```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```In #6 use setup (hd0) or whatever HDD your booting from. Then add a windows entry in menu.lst so it shows on the GRUB menu at boot.

Don't uninstall a perfectly good Ubuntu OS to reinstall windows. it is not necessary and don't take my word for it, read the documentation and educate yourself.

here is my setup:

sda1 is a Linux data partition, sda2 is windows 7 RC (and installed after Ubuntu) sdb1 is Jaunty, sdb5 is sabayon 4.1 Linux

I was giving him the simplest way as he is a total novice :rolleyes:

---

### Post by renbla on 2009-07-12
> **presence1960 said:**
> Why would you tell someone to remove a perfectly good OS? I know a bunch of people on here proclaim that you must install Windows first. That is a bunch of bolderdash and misinformation. See these links:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

with all the resources in this community and on the web why are we still giving bad information on this subject? I think it is perpetuated because those proclaiming you must install windows first don't understand the installation process for windows and/or Linux and the boot process. When you install windows after Linux it must be on a primary partition (it doesn't have to be first partition on the disk). Windows will overwrite GRUB and the windows bootloader will take over next time you boot. To restore GRUB boot off the Ubuntu live CD and restore GRUB to MBR like this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```In #6 use setup (hd0) or whatever HDD your booting from. Then add a windows entry in menu.lst so it shows on the GRUB menu at boot.

Don't uninstall a perfectly good Ubuntu OS to reinstall windows. it is not necessary and don't take my word for it, read the documentation and educate yourself.

here is my setup:

sda1 is a Linux data partition, sda2 is windows 7 RC (and installed after Ubuntu) sdb1 is Jaunty, sdb5 is sabayon 4.1 Linux


I thought you have a better way :p, this reinstall-grub way is so popular that it's the first to appear if you search for XP-ubuntu dual ;)

---

### Post by presence1960 on 2009-07-12
> **bigken said:**
> I was giving him the simplest way as he is a total novice :rolleyes:

I hardly call uninstalling a perfectly good OS and then installing 2 OS's the simplest way. That is way too much work for a "novice". When we install Windows to a primary partition after linux has been installed the only thing that happens which requires 1 step to correct is that Windows overwrites GRUB. At that point when you boot your computer the windows bootloader will take over and it will "appear" to the untrained eye that Ubuntu does not exist. It is our responsibility to inform the "untrained eye" that Ubuntu is installed and only needs to have GRUB restored to be able to boot into either OS. Let me ask you would you rather restore GRUB with a few commands like this:
> 1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD. or would you rather go through the work of installing 2 OS's? In light of your explanation of providing the "simplest way" your idea makes absolutely no sense. That is hardly the simplest way!

P.S. if you would rather do all that extra work be my guest, but our community documentation provides us with the **_simplest way to do this._**

---

### Post by Post Monkeh on 2009-07-13
while i wouldn't describe myself as a computer novice, i wouldn't consider myself to be an ubuntu expert and yesterday, i was able to install xp over vista, and easily restore my grub boot loader.

once i'd installed xp, it took me all of 5 minutes to load up the ubuntu cd and restore grub using the easily followed instructions.

of course it did me no good anyway, i decided to get rid of windows altogether and just go with a virtulbox, given that because i had a "data" drive , xo basically demanded that because it was already fomatted, it had to be drive c, even though the unpartitioned space i wanted to install xp to was actually before it on the disk.  because of my cd drive and ubuntu partitions, windows then ended up installed on the "m" drive.  it may be petty, but i just couldn't accept that and away it went. if only windows wasn't so unconfigurable (is that even a word?) it would still be on my hard disk.  i'm turning into a linux geek :-(

anyway, my point is, it's easy to install windows if you already have ubuntu installed, and it's a 5 minute job to fix the stuff that windows breaks.

---

### Post by presence1960 on 2009-07-13
> **Post Monkeh said:**
> while i wouldn't describe myself as a computer novice, i wouldn't consider myself to be an ubuntu expert and yesterday, i was able to install xp over vista, and easily restore my grub boot loader.

once i'd installed xp, it took me all of 5 minutes to load up the ubuntu cd and restore grub using the easily followed instructions.

of course it did me no good anyway, i decided to get rid of windows altogether and just go with a virtulbox, given that because i had a "data" drive , xo basically demanded that because it was already fomatted, it had to be drive c, even though the unpartitioned space i wanted to install xp to was actually before it on the disk.  because of my cd drive and ubuntu partitions, windows then ended up installed on the "m" drive.  it may be petty, but i just couldn't accept that and away it went. if only windows wasn't so unconfigurable (is that even a word?) it would still be on my hard disk.  i'm turning into a linux geek :-(

anyway, my point is, it's easy to install windows if you already have ubuntu installed, and it's a 5 minute job to fix the stuff that windows breaks.

+1

my point exactly. would someone rather restore GRUB after installing windows or remove Ubuntu to wind up having to install 2 OS's? It is not hard to do, I just can not understand why people insist Windows must be installed before Linux. Glad you were able to do it. Now I wish I could get rid of windows- I have it for work and only use it once, sometimes twice a month...lol.

---

### Post by raymondh on 2009-07-13
> **presence1960 said:**
> +1

my point exactly. would someone rather restore GRUB after installing windows or remove Ubuntu to wind up having to install 2 OS's? It is not hard to do, I just can not understand why people insist Windows must be installed before Linux. Glad you were able to do it. Now I wish I could get rid of windows- I have it for work and only use it once, sometimes twice a month...lol.

Virtualize .... :)

---

### Post by merlinus on 2009-07-13
+110!  But you will need a bunch of system resources to make it work well...

My VB with win 2000 uses 7G dynamic space, 1.5G RAM, and 128VRAM.  Works like a charm for the one and only app I need, including printing.

---

### Post by presence1960 on 2009-07-13
I hear you both- but I have had it on a partition for a while now. I have the resources to give it: plenty of disk space, I have 4 GB ram so I could give it 2 GB with no problemo. 2.8 GHz Athlon64 x2 CPU. I am hoping I can get rid of Windows soon.

---

### Post by Post Monkeh on 2009-07-14
i need it for work too. luckily i have a work laptop with xp, and anything i need to check can be done inside a virtualbox. in fairness i don't mind xp and would have kept it on if it hadn't buggered about with my drive letters, but vista is the devil.

---

