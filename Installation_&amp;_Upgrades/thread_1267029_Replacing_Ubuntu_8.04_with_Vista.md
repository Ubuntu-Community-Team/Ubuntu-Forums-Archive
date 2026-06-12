---
title: "Replacing Ubuntu 8.04 with Vista"
date: 2009-09-15
forum: Installation &amp; Upgrades
---

### Post by Otiosedodge on 2009-09-15
Hi All,

Despite a great initial experience with Ubuntu, for university-related reasons I have to switch back to Windows completely. I've looked at a lot of sites on the web explaining how to do this and have tried what they suggested, but still haven't had any luck. Whenever I simply put the Vista recovery DVD in the drive and boot, Ubuntu still comes up. I'm thinking that it might be a good idea to boot from the Ubuntu Live CD, fire up the partition manager, allocate all the space on my hard disk to an NTFS file system, and then try to boot up from the Vista recovery DVD, but I'm a little scared of ending up with absolutely no operating system! Any thoughts? Thanks in advance.

Otio

---

### Post by ajgreeny on 2009-09-15
If I remember correctly, a disk that is filled with a linux ext3 filesystem will not be seen by the windows install disk nor by some manufacturers' recovery disks, so I think you are right that you will either have to make some unallocated space, or make a new ntfs partition to install to.

Don't forget that you could easily shrink ubuntu and leave it on the machine, install vista, and then restore grub with the live CD, to allow you to dual boot.

---

### Post by .nedberg on 2009-09-15
In the BIOS, is your computer set to boot from CD before hard drive?

On a lot of computers you have to press F12 or F10 to select boot device.

---

### Post by presence1960 on 2009-09-15
> **ajgreeny said:**
> If I remember correctly, a disk that is filled with a linux ext3 filesystem will not be seen by the windows install disk nor by some manufacturers' recovery disks, so I think you are right that you will either have to make some unallocated space, or make a new ntfs partition to install to.

Don't forget that you could easily shrink ubuntu and leave it on the machine, install vista, and then restore grub with the live CD, to allow you to dual boot.

+1

ajgreeny is correct. Why wipe ubuntu if you like it? Set up a dual boot and use windows for the university and Ubuntu for your personal stuff. That way you can have the best of both worlds. If you need help doing this post back.

P.S. he is correct about the windows installer not recognizing linux partitions as being able to install windows onto. You must have free space or unallocated space or NTFS or a FAT partition for the installer to recognize it.

---

### Post by Otiosedodge on 2009-09-16
Hi Everyone,

Thanks for your helpful responses. :) I've decided that I'd like the dual boot option. I've looked for help in the forums and on the web and haven't had any luck yet. Can you please walk me through it?

Otio

---

### Post by presence1960 on 2009-09-16
> **Otiosedodge said:**
> Hi Everyone,

Thanks for your helpful responses. :) I've decided that I'd like the dual boot option. I've looked for help in the forums and on the web and haven't had any luck yet. Can you please walk me through it?

Otio

first boot into Ubuntu, open a terminal and run this command ```
sudo fdisk -l
```
that is a lowercase L in -l

paste the output of that command back here. We need to see your partition table to advise how to proceed.

---

### Post by Otiosedodge on 2009-09-16
Hi again,

Here it is. I have to say that I may have made a mess of things, because I partitioned the disk into two sections in an attempt to dual boot, but it didn't work, and now that I think about it, it probably didn't work because I didn't make the file system on the new section NTFS.   

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfc4a5a0f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7820    62814118+  83  Linux
/dev/sda2           14220       14593     3004155    5  Extended
/dev/sda5           14220       14593     3004123+  82  Linux swap / Solaris
diego@diego-laptop:~$

---

### Post by JK3mp on 2009-09-16
I'd suggest just backing up all your stuff off ubuntu, then doing as you said and format all space to NTFS and then Install Vista, afterwards, ReInstall Ubuntu and restore all your stuff. Sounds like alot of work but it doesn't take that much time to reinstall ubuntu, and your already installing Vista anyways. Very easy and simple with ubuntu though it does feel intimidating the first time.

---

### Post by Otiosedodge on 2009-09-16
I don't have to do anything to the master boot record, right? Just repartitioning and changing the file system to NFTS will be enough, right?

---

### Post by presence1960 on 2009-09-16
This should be easy. Boot off the Ubuntu Live CD and choose "try ubuntu without any changes". When the desktop loads open gparted by going System > Administration > Partition Editor. When gparted opens right click on the sda1 partition and click Resize/Move. When the graphic comes up grab the right partition boundary and drag it to the left until you have made enough space for your windows install. Click the green check mark at top (Apply). Then right click the space you just created and choose new. create a **Primary NTFS or FAT32 partition** Click the green check mark (Apply). When complete exit and reboot with your windows install CD. Chosse the partition you just created to install Windows onto. After windows is installed reboot and make sure it boots right into windows. 

Next step is to restore GRUB to MBR by doing this:
```

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,0)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,0)"
6. Type "setup (hd0)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

Reboot and GRUB should take over. If there is no Windows entry in the GRUB menu that is a quick fix, post back if that happens. Then you will have your dual boot set up. 

**_Why would you want to remove a perfectly good Ubuntu OS to install windows?_**

---

### Post by presence1960 on 2009-09-16
> **Otiosedodge said:**
> I don't have to do anything to the master boot record, right? Just repartitioning and changing the file system to NFTS will be enough, right?

Read my instructions, after installing windows you will have to restore GRUB. I would disregard the other suggestion about removing your Ubuntu install to install Vista- that is totally unnecessary and it is a lot of work.

That is a myth perpetuated on here by some that you must install windows first to set up a dual boot. They just don't understand that when you install windows after Ubuntu windows overwrites the MBR & all you need to do is a quick 45 second process to restore GRUB to MBR

**_Why would you want to remove a perfectly good Ubuntu OS to install windows?_**

---

### Post by presence1960 on 2009-09-16
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

as proof that you can install windows after Linux (Ubuntu)

---

### Post by Otiosedodge on 2009-09-16
I partitioned part of my hard disk to be NTFS, then tried to boot off the Vista CD, but no luck; it went into Ubuntu again. Any thoughts?

---

### Post by presence1960 on 2009-09-16
> **Otiosedodge said:**
> I partitioned part of my hard disk to be NTFS, then tried to boot off the Vista CD, but no luck; it went into Ubuntu again. Any thoughts?

Boot into Ubuntu again and run that same command ```
sudo fdisk -l
```
post the output back here.

a few thoughts:

did you give the NTFS partition at least 30 GB?
is your optical drive set to boot first in BIOS?
I have an OEM version of Vista and a couple of times it would not recognize the NTFS partition. What I had to do was go back in partition editor and delete the NTFS partition and leave it as unallocated space. it is weird because sometimes it will install to NTFS and others it would only install to unallocated space.

---

### Post by Otiosedodge on 2009-09-16
Here is the output:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfc4a5a0f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7820    62814118+  83  Linux
/dev/sda2           14220       14593     3004155    5  Extended
/dev/sda3            7821       14219    51399967+   7  HPFS/NTFS
/dev/sda5           14220       14593     3004123+  82  Linux swap / Solaris

Partition table entries are not in disk order

In response to your thoughts:

did you give the NTFS partition at least 30 GB?

Yep.

is your optical drive set to boot first in BIOS?

Yep.

I have an OEM version of Vista and a couple of times it would not recognize the NTFS partition. What I had to do was go back in partition editor and delete the NTFS partition and leave it as unallocated space. it is weird because sometimes it will install to NTFS and others it would only install to unallocated space. 		 

I don't know what you mean by OEM, but I've already tried to boot from the Vista disc with the partition as unallocated space, and that didn't work.

Oh, and there's something that's creeping me out a little: when I last opened Ubuntu (not from the Live CD), the Vista disc showed up on the desktop as a blank disc. I hope that doesn't mean that I wiped it somehow...

---

### Post by salemboot on 2009-09-16
Boot your recovery disc:

Usually there is an option to open a command prompt.

Bootrec.exe /fixMBR
Bootrec.exe /fixBoot

[http://www.winvistatips.com/fix-mbr-t116.html](http://www.winvistatips.com/fix-mbr-t116.html)

Also consider using VirtualBox to run Windows.  It sandboxes you're win32 environment so if Viruses present themselves you generally would have a backup of the virtual disk.

Vista checks for 512 Mb of ram during installation.  Afterwards you can drop the ram available to 256 Mb.  It runs fine.

---

### Post by presence1960 on 2009-09-16
> **Otiosedodge said:**
> 

I don't know what you mean by OEM, but I've already tried to boot from the Vista disc with the partition as unallocated space, and that didn't work.

Oh, and there's something that's creeping me out a little: when I last opened Ubuntu (not from the Live CD), the Vista disc showed up on the desktop as a blank disc. I hope that doesn't mean that I wiped it somehow...

OEM stands for Original Equipment Manufacturer. I bought the OEM version of Vista when I built my machine.

That can be a problem if your disk is blank. Boot into ubuntu and when ubuntu loads put the vista disk in the optical drive. Use file browser to make sure it has all it's files on the DVD.

---

### Post by presence1960 on 2009-09-16
Everything else looks good, it is probably your install DVD that is the problem. Your partition table is fine, your optical drive is set to boot first. It is either your optical drive or the Vista install disk that is the problem.

---

### Post by presence1960 on 2009-09-16
> **salemboot said:**
> Boot your recovery disc:

Usually there is an option to open a command prompt.

Bootrec.exe /fixMBR
Bootrec.exe /fixBoot

[http://www.winvistatips.com/fix-mbr-t116.html](http://www.winvistatips.com/fix-mbr-t116.html)



That will work if he has Vista installed. Currently he has only Ubuntu installed and an empty NTFS partition onto which he wants to install Vista.

---

### Post by Otiosedodge on 2009-09-16
I don't know if my copy of the Vista disc (assuming it's not wiped; see below) is OEM -- I ordered it from HP after buying my HP comp.

More info about the disc that can maybe resolve the problem: it definitely says that the disc is blank when I insert it during an Ubuntu session. Then when I try to browse the disc, I get an error message which says: "Cannot mount volume. Invalid mount option when attempting to mount the volume." Then I get a message which says that it's trying to open the location, and end up with this: "DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

I've used the disc twice in the past; once to recover my system and once after that to recover a friend's. I know you guys aren't Windows people, but do you think that the disc somehow erased itself since I used it on two different comps? Wouldn't it make sense that it just wouldn't let me perform the recovery on my friend's comp because it was somehow tied to mine?

---

### Post by presence1960 on 2009-09-16
> **Otiosedodge said:**
> I don't know if my copy of the Vista disc (assuming it's not wiped; see below) is OEM -- I ordered it from HP after buying my HP comp.

More info about the disc that can maybe resolve the problem: it definitely says that the disc is blank when I insert it during an Ubuntu session. Then when I try to browse the disc, I get an error message which says: "Cannot mount volume. Invalid mount option when attempting to mount the volume." Then I get a message which says that it's trying to open the location, and end up with this: "DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

I've used the disc twice in the past; once to recover my system and once after that to recover a friend's. I know you guys aren't Windows people, but do you think that the disc somehow erased itself since I used it on two different comps? Wouldn't it make sense that it just wouldn't let me perform the recovery on my friend's comp because it was somehow tied to mine?

It is irrelevant if the disk is an OEM or just a regular install disk. The difference is the OEM is tied directly to your hardware. if you try to install with different hardware or on another machine you will have to call Microsoft to activate it. That happened to me. I swapped out a hard drive and it wouldn't let me activate vista until I called Microsoft and explained why my hardware was different. Just one reason why I use Linux!

it looks like your disk is toast. But try it in another machine just to be sure!

---

### Post by Otiosedodge on 2009-09-16
Sigh... OK. Thanks to everyone for their help, especially Presence.

---

### Post by presence1960 on 2009-09-16
Sorry, let us know what happens.

---

### Post by Otiosedodge on 2009-09-16
Just to take one more stab at it: what if I boot up from the Ubuntu live CD, then devote the entire hard drive to the NTFS system, then try to reboot from the Vista CD? And most importantly, if the Vista CD doesn't work then, how do I reinstall Ubuntu?

---

### Post by ajgreeny on 2009-09-16
Whoa!  Not so fast.

Before you do all that, I think from your ```
fdisk -l
``` output that your ntfs partition is within an extended partition, which is probably part of the reason for your problem.

Windows will not boot from an extended/logical partition, only from a primary partition.  I am not sure if this fact actually stops windows installing to such a partition, but it could be so, and I should hate you to wipe everything just for that, when you could just delete that new ntfs partition and make another primary one to replace it.

---

### Post by presence1960 on 2009-09-16
sda3 is NTFS. if it were in an extended partition it would be sda5 or higher. numbering for logical partitions inside an extended partition begin at sda5, even if there is only 1 primary partition.

But as ajgreeny said Whoa! hold on there. You need to make sure your disk is ok for windows before you go trashing your whole partition table and have no OS on your machine.

if there are no files & directories on that disk it is useless to do what you want to do. **You should try that Vista install disk on another machine first to verify it is in fact a good disk or a blank disk.**

---

### Post by rmeske on 2009-09-16
Actually could it be that the Vista Disc requires a restore partition that was originally on the hard-disk?  

If that is the case you may need to do some extra work before being able to run the Vista Install on your CD.

---

### Post by Otiosedodge on 2009-09-16
Shoot. I already started wiping everything to replace it with a full NTFS system. It's a long process, apparently another three hours to go. Are you guys saying that I won't be able to boot from the Ubuntu live CD if I can't boot from the Windows CD??

---

### Post by presence1960 on 2009-09-16
> **Otiosedodge said:**
> Shoot. I already started wiping everything to replace it with a full NTFS system. It's a long process, apparently another three hours to go. Are you guys saying that I won't be able to boot from the Ubuntu live CD if I can't boot from the Windows CD??

If the CD is no good how is it going to boot. That's why I said check the Cd on another computer first before wiping your disk. if the CD is no good then you wasted all that time & don't have an OS.

---

### Post by Otiosedodge on 2009-09-16
I assumed that maybe there was still a chance of the Vista CD booting if I had my entire hard drive set up with NFTS, and when I didn't get a quick response about it in this forum, my impatience got the better of me. A dumb decision. Is there any way for me to salvage this situation? Can't I just re-partition and set up the hard drive with ext3 now, given that I've still got this OS up and running, and just re-install Ubuntu from here?

---

