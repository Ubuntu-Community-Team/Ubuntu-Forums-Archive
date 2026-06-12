---
title: "Have I got any solutions left for a dual boot install? Detailed issue..."
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by Pott on 2009-10-22
Alright sorry for this but I figured a new thread is in order, here's the situation:

My HDD (160GB) has 4 partitions:
2 which are not accessible through the system (Windows Vista Loader sda1 (9.6GB)/Microsoft Windows XP Embedded sda4 (3.2GB)
Here's a screenshot
[IMG]http://i7.photobucket.com/albums/y300/PierreEmmanuel/DSCF0436.jpg[/IMG]

The other two are C/D from Vista. C is 69GB, D is 66GB.

As D had 40GB free, I decided to shrink it using Gparted and create a 15GB free space.

Now because I have 4 primary partitions, there is no way to create any more nor to make an Extended one where I can shove Ubuntu.

I have a HDD with 30GB free which is pretty much always connected to my laptop (I use the whole thing as a desktop in fact).

As we can see from the screenshot, Ubuntu can't be installed on the spare 15GB, which were created for nothing. They can't go onto the other partitions as it'd erase everything. 

Here are the fdisk results:
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x007e7baf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  12  Compaq diagnostics
/dev/sda2   *        1275       10383    73162752    6  FAT16
/dev/sda3           10384       17076    53761522+   7  HPFS/NTFS
/dev/sda4           19034       19458     3398656   12  Compaq diagnostics
ubuntu@ubuntu:~$

The two solutions I can see are:

Take everything that's in D: and put it on the HDD. Which would in a way make sense as these are my own files and should be moveable. It'd involve manually moving all my 'Documents' files back to C and try to trim it down (C only has about 12GB left!). But this would leave me my D for Ubuntu. All 50GB of it...

Or I could install Ubuntu on the external HDD.

My questions are...

Which solution seems to be the better in terms of speed, stability and reliability on Ubuntu?
Have I lost those 15GB forever since they can't be set into a partition...? Or with will Vista let me once Ubuntu is on D? I do get the option under 'Manage'/Drive Management to assign it a name and format, but that'd create a 5th partition in essence... I've not tried to press OK yet. 

Thanks...

---

### Post by andymorton on 2009-10-22
> **Pott said:**
> Alright sorry for this but I figured a new thread is in order, here's the situation:

My HDD (160GB) has 4 partitions:
2 which are not accessible through the system (Windows Vista Loader sda1 (9.6GB)/Microsoft Windows XP Embedded sda4 (3.2GB)
Here's a screenshot
[IMG]http://i7.photobucket.com/albums/y300/PierreEmmanuel/DSCF0436.jpg[/IMG]

The other two are C/D from Vista. C is 69GB, D is 66GB.

As D had 40GB free, I decided to shrink it using Gparted and create a 15GB free space.

Now because I have 4 primary partitions, there is no way to create any more nor to make an Extended one where I can shove Ubuntu.

I have a HDD with 30GB free which is pretty much always connected to my laptop (I use the whole thing as a desktop in fact).

As we can see from the screenshot, Ubuntu can't be installed on the spare 15GB, which were created for nothing. They can't go onto the other partitions as it'd erase everything. 

Here are the fdisk results:
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x007e7baf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  12  Compaq diagnostics
/dev/sda2   *        1275       10383    73162752    6  FAT16
/dev/sda3           10384       17076    53761522+   7  HPFS/NTFS
/dev/sda4           19034       19458     3398656   12  Compaq diagnostics
ubuntu@ubuntu:~$

The two solutions I can see are:

Take everything that's in D: and put it on the HDD. Which would in a way make sense as these are my own files and should be moveable. It'd involve manually moving all my 'Documents' files back to C and try to trim it down (C only has about 12GB left!). But this would leave me my D for Ubuntu. All 50GB of it...

Or I could install Ubuntu on the external HDD.

My questions are...

Which solution seems to be the better in terms of speed, stability and reliability on Ubuntu?
Have I lost those 15GB forever since they can't be set into a partition...? Or with will Vista let me once Ubuntu is on D? I do get the option under 'Manage'/Drive Management to assign it a name and format, but that'd create a 5th partition in essence... I've not tried to press OK yet. 

Thanks...

Could you install Ubuntu using Virtualbox? I don't know whether that will work with such a limit on HDD space. But it's just an idea. 

:)

---

### Post by itsjareds on 2009-10-22
It really comes down to whichever you prefer. You could copy over your D: partition to the second hdd if you want to be more organized and have all your boot files on one hdd and regular documents on another. If you're more concerned about time or keeping boot loaders in place, I would just install Ubuntu on that second hard drive. 

My suggestion is to use the external hard drive because this way the Ubuntu boot loader will install on that drive, not messing with your Vista boot loader installed on the first hdd. Also, there will be no need to copy files anywhere (unless you have to move files on the second hdd). The main issue will be changing your BIOS boot order to boot from your second hard drive instead of your first. Grub allows booting from multiple hard drives so I would keep your BIOS booting from the second hdd first.

If you decide to use the external drive and not install into the free space freed by D:, you can always grow (resize) your D: partition to include those 15gb. To do this, use the Ubuntu LiveCD (Not running the installer, just the live demo) and go to System > Administration > GParted. This gives you a detailed partition editor. Select your /dev/sda3 partition and choose to resize it, then just stretch the partition over the 15gb free space.

edit: Also, I read part of your other thread, and I wanted to reply to this:
> **Pott said:**
> Both my extra two partitions aren't accessible from Windows. No way I can look at what's into them. I also don't know if the system needs them or if they're sitting there for nothing. I did a search on how to create an Extended partition on Vista and it's not possible anymore (though I could use Gparted of course anyway)

The Compaq Diagnostic partitions are where your computer stores your BIOS. Read more on Compaq Diagnostic here:
[URL="http://forums.techguy.org/windows-nt-2000-xp/80422-remove-compaq-partition.html"]
http://forums.techguy.org/windows-nt-2000-xp/80422-remove-compaq-partition.html[/URL]

I'm not sure if I read these forums correctly, but it seems that you can delete the diagnostic partitions (except for the first!):
[http://forums.windrivers.com/showthread.php?t=48483]("http://forums.windrivers.com/showthread.php?t=48483")
[http://www.linuxquestions.org/questions/linux-general-1/vista-dual-boot-with-linux-536775/]("http://www.linuxquestions.org/questions/linux-general-1/vista-dual-boot-with-linux-536775/")

So AFAIK you can delete sda4 and create a primary partition from the end of sda3 to the end of your hdd, if you don't want to install on the second hdd. I'm not an expert though so don't take my word for it. If you want to be safe, just install on the second hdd.

---

### Post by Pott on 2009-10-22
Well sda4 is only 3.2GB in the end, and the sda1 is needed. So it looks like these are set. If I figure out that it is 100% safe then I'll do it to save a primary and make it bigger using some free space but for now, not much I can do...

I'll first revert the free space into D using the live Ubuntu. But I can't set partitions on the external HDD so I can't install it there either in the end, it'd erase all my music. And D's too big now to go on the external HDD (25GB left on the external, D is 20GB of data...)

I think I'll wait to get another external HDD, though I'm fast running out of USB ports, not to mention funds :(

Looks like I won't get Ubuntu running for a while.

Thanks for the help! I've read through these links a bit.

---

### Post by itsjareds on 2009-10-22
Oh. Thought I read you had full space on that second drive. If you've got reports of plenty of space left on that second drive but GParted is telling you it can't resize, it's probably because the drive is fragmented. You can use some tools to move files to the front of the partition in order to resize the partition, if you want.

---

