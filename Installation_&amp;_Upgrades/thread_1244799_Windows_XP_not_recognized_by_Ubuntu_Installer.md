---
title: "Windows XP not recognized by Ubuntu Installer"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by Miles B on 2009-08-19
I'm attempting to load Ubuntu 9.04 onto my new Lenovo SL400, with Factory settings. I have Windows XP Pro installed onto my Preloaded (C: ) drive, and want to partition this drive so I can have both Ubuntu and XP installed on my computer. When running the Ubuntu installer off the CD, I am told that there is no operating system detected, and have only two options: Install Ubuntu on all 250G of my hard drive, or perform a manual partition. I've tried cleaning up Windows XP, running many disk defragmentations, but the Ubuntu installer still won't recognize that I've got XP already installed.
I've looked at all the similar threads I can find, and tried some of the suggested solutions, including:
- Going to GParted and trying to create a new partition, but I'm told I have one "unallocated" partition (250G) and creating a new partition will erase everything I have on the entire disk (dev/sda) (So I didn't do that).
- I also ran the sudo fdisk -l command, and got back
 
/dev/sda1 * 1 29572 237537058 7 HPFS/NTFS
/dev/sda2 29573 30402 6659517 12 Compaq diagnostics
 
I'm new to Ubuntu, and would really like to run it as my main OS, but XP is also rather necessary for a number of other functions.
 
Any suggestions?

---

### Post by stlsaint on 2009-08-19
ok have you tried using disk management to create a seperate partition for ubuntu off of your c drive?

---

### Post by Miles B on 2009-08-19
I've been trying to, however Window's Disk Management software isn't giving me the option to partition the C: drive. If it helps, the application shows this:
 
Volume.................Layout...............Type.............File System.................Status 
Preload (C: )........ Partition ............Basic ............NTFS .................Healthy (System) 
SERVICEV001...... Partition............ Basic............ FAT32 ............Healthy (EISA Configuration)
 
Capacity ......Free Space ..........% Free....... Fault Tolerance....... Overhead
226.53 GB..... 213.75 GB .........94%............... No.......................... 0%
6.33 GB .........275 MB ..............4% ................No.......................... 0%

---

### Post by stlsaint on 2009-08-19
and you say booting to the livecd and using gparted does nothing?! try booting to the cd again and this time go to add/remove option under applications tab...then type in NTFS and make sure that the NTFS configuration tool is installed...if not do it and then try to re-partition again...post results!!

---

### Post by presence1960 on 2009-08-19
[gparted live CD]("http://gparted.sourceforge.net/livecd.php") Use the gparted Live CD to partition the windows drive. Shrink XP's partition then create 2 partitions from the unallocated space- one for ubuntu (minimum 20 GB, I suggest as much as you can spare) and one partition for swap which if you want to use suspend/hibernate should be the same size as your installed RAM. Set Ubuntu's partition as ext 3 or ext 4 and the swap as linux-swap. When you install Ubuntu from Ubuntu Live CD choose manual option.

Or you can just create unallocated space by shrinking XP's partition and leaving it as unallocated space. When you install Ubuntu you should get the option of "use largest continuous free space". Choose that option.

You will have to download the iso of gparted Live Cd and burn as an image to CD or make a bootable USB. Boot from that and set up your partitions.

If you need more help post back here.

If all else fails try the [alternate text based installer]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

---

### Post by Miles B on 2009-08-19
Tried that, but I'm still getting the "This computer has no operating systems on it." message in step 4 of 7 (Prepare disk space) of the install.

---

### Post by raymondh on 2009-08-19
> **Miles B said:**
> Tried that, but I'm still getting the "This computer has no operating systems on it." message in step 4 of 7 (Prepare disk space) of the install.

Are there any mounted media when you installed (except for the liveCD in the CD drive)?  i.e.  a external HD attached or a flash drive attached, etc.  If so, do a clean unmount/eject of said media and then boot into the ubuntu liveCD to try to install again.

---

### Post by Miles B on 2009-08-20
Nope, my laptop is free of any mounted media, and still won't work. I tried using the GParted Live CD I burnt, but it won't load on startup, and I can't even get the Boot from CD option. I burnt the ISO file onto a CD-RW, if that makes any difference. Would the text based installer work where the CD isn't? I'm assuming I'd still have the partitioning problems.

---

### Post by Bartender on 2009-08-20
I'm guessing that both the GParted LiveCD and the Ubuntu installer CD's were burned at ludicrous speed and they're no good...

EDIT:  Just noticed the last comment.  Yeah, it's been said often that you should not burn to CD-RW.  Use good-quality CD-R, burn them slowly.  8X is probably safe on a modern PC.  Go slower than that on an older PC.  Even if the CPU is capable, the optical drive may not be up to the task.

---

### Post by Miles B on 2009-08-20
The Ubuntu installer CD I got in the mail, so there shouldn't be a problem with how it was burnt. I tried burning the GParted LiveCD to a CD-R, slowly, but when it's in my CD drive, I just get a black screen with a flashing white line on startup.
 
Edit:
 
I've also tried a number of free partitioning programs, both bootable and not, and none of them seem to work. Apparently I can't resize my C: drive from a program which runs on that drive, and I also can't boot a partitioning program (as my computer freezes). My next course of action is probably going to be to reinstall XP, and partition my hard drives then, and after XP is reinstalled, install Ubuntu on the free space. Thoughts?

---

### Post by presence1960 on 2009-08-20
> **Miles B said:**
> The Ubuntu installer CD I got in the mail, so there shouldn't be a problem with how it was burnt. I tried burning the GParted LiveCD to a CD-R, slowly, but when it's in my CD drive, I just get a black screen with a flashing white line on startup.

I would think that there is a possibility that your optical drive is faulty. It may read data disks but an install disk burned from an image may be too much for it if it is failing or is faulty. 

Have you tried booting from USB using [unetbootin]("http://unetbootin.sourceforge.net/") to create the bootable USB medium?

---

### Post by zboot on 2009-08-20
I have a better solution for you.

1. Inside of Windows, create a two new partitions, one large one the hold ubuntu, and a smaller one for swap.

2. Run the installation cd. Choose to manually specify your partitions.

3. Format them so that the large one will be where you mount root (/) and the small one will be your swap.

4. After installation, your bootloader (grub) will likely only have an entry for linux, so you'd need to add the entry to boot windows.

  a. Log into your ubuntu installation and start a terminal. From Applications -> Accessories->Terminal.

  b. Enter this command, gksudo gedit /boot/grub/menu.lst

  c. Add these lines:

title        Windows XP
rootnoverify    (hd0,0)
savedefault
chainloader    +1

I am assuming that your xp installation is on hard drive 0 partition 0. That may not be the case (it probably is so you may as well just try it first). You can find out quite easily by doing the following:
  - Start another terminal window
 - Start grub using this command: sudo grub
- type root (hd0,
- hit tab, grub will attempt to autocomplete the command. However, since you have multiple partitions listed, it will instead show you a list of your partions and their type. Unlikely your windows partition will be marked "unknown". However, unless your particular drive has a recovery partition, that should be the only unknown one.
- The partition that corresponds to your windows drive (ie one of the unknowns) is the one you want to use with the second line in part c above. If you have more than one, just try each until they work.

So, you've added those lines to menu.lst. Save, close, reboot your machines, and select Windows XP when grub comes up. If that does not work (and you had more unknown partitions, then you probably picked the wrong one) (You will know it didn't work if your machine seems to hang without showing you any of the usual Windows XP booting activity for more than 10 seconds - Just power off your machine, power it back on, and boot into ubuntu to make changes).

BTW - I'm running Windows 7 alongside Ubuntu on a Lenovo Thinkpad X60 tablet.

---

### Post by presence1960 on 2009-08-20
> **zboot said:**
> I have a better solution for you.

1. Inside of Windows, create a two new partitions, one large one the hold ubuntu, and a smaller one for swap.


 he said he already tried that and XP wouldn't allow him to shrink the XP partition. maybe he is doing something wrong. But stlsaint suggested that early on in the thread.

---

### Post by raymondh on 2009-08-20
> **zboot said:**
> 
1. Inside of Windows, create a two new partitions, one large one the hold ubuntu, and a smaller one for swap.

XP's disk utility does not have the option to resize from right > left (shrink).  OP has to use a 3rd party, 'non-windows' disk management tool to resize.  However, his problem is that when using gparted, it does not detect partitions in his HD.  

@ OP .... if you cannot boot into the cd drive, consier trying a USB boot (if BIOS allows it) as presence suggested.

---

