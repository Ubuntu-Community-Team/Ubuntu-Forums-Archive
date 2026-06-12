---
title: "CD/DVD drive won't mount"
date: 2009-08-08
forum: Hardware
---

### Post by TexLogic on 2009-08-08
Hello,

I have a new Acer 5810 Timeline on which I've installed Jaunty.  After a bit of tweaking everything is working beautifully -- except that it doesn't appear to be mounting CDs and DVDs.  The drive itself is fine (I installed Jaunty from a DVD that I burned on the now deleted copy of Vista that came on the machine).  If I insert a CD or DVD, the drive spins up but does not appear to mount; the drive never shows up in the file manager and media/cdrom is empty.  /etc/fstab reads:

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0 0

dmesg |grep -i dvd shows:

[    6.653922] ata5.00: ATAPI: TSSTcorp CDDVDW TS-U633A, AC01, max UDMA/100, ATAPI AN
[    6.695563] scsi 4:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-U633A  AC01 PQ: 0 ANSI: 5
[    6.707170] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray

Help/suggestions greatly appreciated.

TexLogic

---

### Post by TexLogic on 2009-08-09
> **TexLogic said:**
> Hello,

I have a new Acer 5810 Timeline on which I've installed Jaunty.  After a bit of tweaking everything is working beautifully -- except that it doesn't appear to be mounting CDs and DVDs....

**UPDATE**: If I stick a CD/DVD into the tray while the machine is suspended or hibernating, the drive mounts when I wake the machine.  Curious.  Again, ideas/help/suggestions much appreciated.

TexLogic

---

### Post by TexLogic on 2009-08-09
> **TexLogic said:**
> **UPDATE**: If I stick a CD/DVD into the tray while the machine is suspended or hibernating, the drive mounts when I wake the machine.  Curious.  Again, ideas/help/suggestions much appreciated.

TexLogic

**Solved:** I didn't search hard enough. Found the extremely simple solution in [_another Forum thread_]("http://ubuntuforums.org/archive/index.php/t-1135452.html").  The default line in /etc/fstab for mounting the cd/dvd drive is: 

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

The fix was simply to switch "udf" and "iso9660" thus:

/dev/scd0 /media/cdrom0 iso9660,udf user,noauto,exec,utf8 0 0

Reboot and that's it.

TexLogic

---

### Post by BluJai on 2009-08-12
I'm not having any luck with this resolution. I have the Acer Aspire Timeline 4810T (basically the same machine, just a 14" screen).

Changing the order of udf and iso9660 seems to have no effect for me, even after reboot. Is it possible there were other changes that were also made which might have affected the optical drive?

---

### Post by escuadra1941 on 2009-08-26
I have the Timeline 5810 and I haven't any solution too. Could anyone tell  another one? And how can I do it, step by step.
 
Thanks

---

### Post by mopay on 2009-08-27
I`ve Timeline 4810T and this fix work for me with cd/dvd:

Tipe "eject cdrom" (without the quotes) in the console.

---

### Post by executorvs on 2009-09-28
the fstab edit has no luck for me.
the eject cdrom command will eject the drive, but won't always get it to mount.

this is still an issue in Jaunty and Karmic as of updates yesterday.

---

### Post by BoneZZZ on 2009-11-19
Have you changed AHCI to IDE in BIOS?. This solved my problem with CD/DVD

---

### Post by ziret on 2009-11-21
Thanks for the idea, but I have no idea what you are talking about. At any rate, I'm still not ready to tackle the problem.

---

### Post by executorvs on 2009-11-22
didn't seem to make a difference on my 5810T

---

### Post by jynyl on 2009-11-23
Same symptoms here, running Kubuntu Karmic 64bit.
The system does not automount cd when placed in drive, but Jaunty did on this hardware.
The cd can be mounted manually, as a user.
```
mount /media/cdrom0
```

Swapping udf and iso9660 in fstab (and rebooting) didn't make any difference.

TIA

---

### Post by acpride on 2009-11-24
Hi,

Same problem here with an Acer 5810T. No effect changing the fstab. No effect typing "eject cdrom" on console. No effect changing the BIOS to IDE. If I reboot with a cd/dvd inside the drive, it's automounted. Also, when this occurs, if I eject the cd and put it inside again, it's also automounted. Only if I previously had rebooted with a cd inside!

With Jaunty worked perfectly.

Any ideas?

Thanks

---

### Post by Zeenomorph on 2009-11-24
Same issue here.  I can see the DVD drive under places > computer only until I put a DVD in.  Then it disappears from the menu.  The drive spins up, and stops.  But the contents won't mount, and hence can't be read.  A fix would be awesome!

---

### Post by Zeenomorph on 2009-11-25
It seems as though the last automatic update fixed the problem for me.

---

### Post by smotsie on 2009-11-26
> **BoneZZZ said:**
> Have you changed AHCI to IDE in BIOS?. This solved my problem with CD/DVD

Wow, I think that has solved it for me on my Timeline 5810T / Ubuntu 9.10 32 Bit. I only have data cd's to hand but my first test worked. Unfortunately (do I mean this?) it causes the dual boot-windows to fail on boot. Seems Microsplot can't cope with the disk changing from sata to IDE, where Ubuntu just shrugs it's slopey Penguin shoulders and say "Oh, OK we're IDE now!"
:popcorn:

---

### Post by barkhan on 2009-11-29
I am using NEC Versa S3500 and I am also having the same problem. After booting up, I am unable to mount any CD/DVD.

In order to "solve" this, I put a CD/DVD in there, go to Standby, and when it returns from Standby I can read the CD and any other CDs after that. ;)

So far the updates has not been able to solve my problem.. I also have no problem whatsoever in Jaunty.

---

### Post by acpride on 2009-12-14
Hi, 

I decided to reinstall completely ubuntu 9.10 using the cd I just got instead of network upgrading from 9.04, and then install all the updates available.

Now all works perfectly, except the internal mic.

I know it's a pity a "clean" reinstall, but for me the other solutions didn't work, and I need the laptop to be completely functional for working.

---

### Post by executorvs on 2009-12-14
I have still found no way to avoid opening the drive with terminal on my 5810TZ. I have the most up to date bios and have tried a clean install. the one thing I plan on checking after my exams are done is if there are any firmware patches for the DVD drive itself.

---

### Post by executorvs on 2009-12-14
I forgot to add the other "one thing" I plan on trying is testing the newer kernel to see if it works any better. it had mixed results on my desktop, but it's still worth checking on different hardware.

---

### Post by zeroid on 2009-12-24
Wondering if anyone truly fixed this problem. I'm a new Unix user. Installed 9.04 and have just encountered this rather ridiculous problem of not being able to use the CD drive. Have tried all of the above options other than the BIOS one (apparently my BIOS doesn't seem to offer the option to change that particular function). Everytime I put a CD in the drive all of the icons (i.e. files etc) disappear from my desktop, the drive spins up then nothing. If I click on "Computer" I get nothing, so it effectively shuts me out of the file manager altogether. The only way out is "eject cdrom" or a reboot. Meanwhile if I use "Search for Files" it lets me see and open files on the CD. So I guess what I am saying is putting a CD in my computer effectively kills my "File Manager". I am reluctant to upgrade to 9.10 because this is my first time using UNIX and I don't know what to anticipate. Do I have to backup all of my settings? Or does the upgrade retain them? Does the upgrade "wipe" my hard drive? Any help for a very frustrated newbie would be most welcome.

Thanks

---

### Post by willgb54 on 2009-12-24
I am wondering the same thing. Same story Acer 5810 can't use CD properly. Installed Ubuntu using CD, have switched the utf ISO thing, which seemed to work ONCE, then not. I am trying to switch over to (away from Windows!) Ubuntu, but can't find a whole lot to recommend it. BIOS changes did not help. How basic is normal operation of a CDROM? Always took it for granted on Windows. May have to pay up and keep Widows.

---

### Post by Roger N on 2009-12-28
Hi Have posted this to an old problem else where -  a possible solution. 
I have been having the same sort of problems in being unable to mount DVDs that I wrote with Ubuntu - Just upgraded to 9.4 and had problems reading all DVDs now - spent ages reading the posts and changing fstab settings for the Cdrom - all without success.

The Solution - Have deleted the whole line in fstab relating to the cdrom, and it all works ok now - can auto mount and read DVDs.

---

### Post by zeroid on 2009-12-28
Thanks Roger N for replying. Unfortunately I just removed all signs of CD from fstab and it made no difference. Effectively what happens is that as soon as I put a CD in my drive, it sees it in the "Places" menu, allows me to search it in the search function but it completely kills any access directly to my hard drive through "Computer". It has to be the goofiest problem I've ever encountered. I have to use "eject CDROM" to get the disc out, and then I have to do a complete reboot to get control back. So my question is if I upgrade to 9.10 will this be fixed, and will the upgrade over-write all of my settings? (I have LAMP server running and I'd really hate to have to reinstall the whole thing from scratch just to do the upgrade to 9.10.) Thanks in advance.

---

### Post by Roger N on 2009-12-28
Hi zeroid

cannot really comment as I am no Linux expert - I just keep trying things until something works. Below is my fstab. Before the change I could create DVDs with brasero - but could not mount them (although I could see them in a file browser, it just said could not mount) and some commercial DVDs I could not mount either. After the change I can now mount the DVD I created wit Brasero and CDs etc
I can see the disks through  Removable media,  Computer and Dolphin
Cannot comment about upgrade to 9.10 - only just come up to 9.04

if you use the upgrade manager you should not lose your settings - I did not lose mine on the upgrade - but then I have my /Home on a separate partition. 

I would not have thought that changing the CD settings would have affected the Hd access. With my limited experience of problems in linux that sounds like a Hardware problem/conflict.

It is obviously something that needs further investigation, by an expert

fstab before

proc /proc proc defaults 0 0
UUID=33fdc306-38ee-49df-8fe6-3e912706cf64 / ext3 relatime,errors=remount-ro 0 1
UUID=60496650-4d30-4c4a-befe-8060f1269d98 /home ext3 relatime 0 2
UUID=62858c54-c700-47e8-9a0f-e27688fb7477 none swap sw 0 0
/dev/scd0 /media/cdrom0 iso9660,udf users,noauto,exec,umask=000,utf8 0 0
/dev/sdb1 /media/INTRIM_DISK ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sda1 /media/System_XP ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sda5 /media/Photos_images ntfs-3g defaults,locale=en_GB.UTF-8 0 0



fstab after

proc /proc proc defaults 0 0
UUID=33fdc306-38ee-49df-8fe6-3e912706cf64 / ext3 relatime,errors=remount-ro 0 1
UUID=60496650-4d30-4c4a-befe-8060f1269d98 /home ext3 relatime 0 2
UUID=62858c54-c700-47e8-9a0f-e27688fb7477 none swap sw 0 0 
/dev/sdb1 /media/INTRIM_DISK ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sda1 /media/System_XP ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sda5 /media/Photos_images ntfs-3g defaults,locale=en_GB.UTF-8 0 0 

This fstab workes perfactly for me.

Only other thing to mention is that I did have mount manager loaded but it would not open after the upgrade so I removed it completly.

regards

---

### Post by n.masarone on 2010-01-05
Hi all,
I didn't apply any change on my 5810TG with a fresh new Ubuntu 9.10 and was using CD-ROM typing *eject* command in the terminal window. 
A few days ago I added KDE 4.3.4 desktop and used K3B ver. 1.68.0 within Gnome session; there, just using the eject command in the device menu, I can open the empty tray and load a disk. After that action Gnome also detects and mounts disk. Seems to be a problem related to Gnome interface more than to hardware or Ubuntu/Linux.
Can someone more expert confirm that ?

---

### Post by zeroid on 2010-01-07
Hey Roger N,
Thanks for that fstab breakdown. I'm at a loss what to do at this point. I used my CD drive to install ubuntu on the machine in the first place and it worked fine. Once the OS was up and running I suddenly developed this ridiculous problem. I sure wish an experienced LINUX user would join this forum and help me out here. I'm using a factory default setup of a Hewlett Packard computer. The odds of it being a hardware problem is pretty slim as it worked fine before putting Ubuntu onto the machine. You can dig around for days on these forums trying to find an answer to what is probably a really easy question. Thanks again.

---

### Post by Spongeloaf on 2010-01-08
I have the same problem as everybody else. After upgrading to Karmic, my DVD drive wont mount. It will eject, and spin up, but it wont mount. It would be awesome if somebody who knows a lot more than me came along with a solution.

---

### Post by executorvs on 2010-03-10
I'm not sure if this is still a problem in lucid. I'll check and get back here later.

---

### Post by Samwise Hamfast on 2010-03-18
> **Spongeloaf said:**
> I have the same problem as everybody else. After upgrading to Karmic, my DVD drive wont mount. It will eject, and spin up, but it wont mount. It would be awesome if somebody who knows a lot more than me came along with a solution.

I too am experiencing the same problem and would appreciate any help anyone can give. After looking at the previous postings in this thread, I have tried altering line 13 in file /etc/fstab and have restored line 13 back to its original state (I hope!). I now have the following error message:

Unable to mount DVD_VIDEO_RECORDER
Error mounting: mount exited with exit code 1: helper failed with:
[mntent]: line 13 in /etc/fstab is bad
mount: can't find /dev/sr0 in /etc/fstab or /etc/mtab

The two files /etc/fstab and /etc/mtab are:

fstab:
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=9b48063a-f8c9-4405-bf5c-291c0c1d5054 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=06e35798-7c90-4b3a-bb96-d0fc2c0d78be none            swap    sw              0       0
/dev/scd0 /media/cdrom0 udf,iso9660 user, noauto, exec, utf8 0       0

mtab:
/dev/sda5 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/fred/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=fred 0 0

I'm using Karmic (9.10) on a Toshiba Satellite Pro and used the CD/DVD RW drive to install Ubuntu. Is what we are seeing a bug in this release? Why does the error message say that the system is looking for drive sr0 when it's a problem with scd0, the cdrom (or is it? Does Karmic see this CD/DVD drive as something else? And if so, where else does Ubuntu define drives?)

Any help would be appreciated,

Many thanks,

Samwise

---

### Post by anivegmin on 2010-05-07
Similar problem here was happening with Karmic and now with Lucid -

When I start my Ubuntu Lucid system both cd rom drives work fine; then after what seems like a random length of time - anything from minutes to hours - they will both become inaccesible. They will either unmount cd's already in the drawers or refuse to mount newly inserted discs

$ sudo gedit /etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda1 during installation
UUID=16931e94-ed47-474e-812a-62539e100e29 / ext4 defaults 0 1
# swap was on /dev/sda5 during installation
UUID=4dfcdf04-940a-4215-8309-83bed499f55c swap swap sw 0 0
/dev/fd0 /media/floppy0 vfat noauto 0 0

$ ls -l /dev/{cd,dvd}*

lrwxrwxrwx 1 root root 3 2010-05-06 13:34 /dev/cdrom -> sr1
lrwxrwxrwx 1 root root 3 2010-05-06 13:34 /dev/cdrom1 -> sr0
lrwxrwxrwx 1 root root 3 2010-05-06 13:34 /dev/cdrw -> sr1
lrwxrwxrwx 1 root root 3 2010-05-06 13:34 /dev/cdrw1 -> sr0
lrwxrwxrwx 1 root root 3 2010-05-06 13:34 /dev/dvd1 -> sr0

sudo hdparm -I /dev/{sr0,sr1}

/dev/sr0:

ATAPI CD-ROM, with removable media
Model Number: TSST CD-RW/DVD-ROM TSH492B 
Serial Number: 
Firmware Revision: TB04 
Standards:
Supported: CD-ROM ATAPI-1 -2 -3 
Configuration:
DRQ response: 50us.
Packet size: 12 bytes
cache/buffer size = unknown
Capabilities:
LBA, IORDY(can be disabled)
DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2 
Cycle time: min=120ns recommended=120ns
PIO: pio0 pio1 pio2 pio3 pio4 
Cycle time: no flow control=240ns IORDY flow control=120ns
Commands/features:
Enabled	Supported:
PACKET command feature set
DEVICE_RESET command
*	DOWNLOAD_MICROCODE
Removable Media Status Notification feature set
HW reset results:
CBLID- above Vih
Device num = 0

/dev/sr1:

ATAPI CD-ROM, with removable media
Model Number: HL-DT-ST GCE-8320B 
Serial Number: 
Firmware Revision: 1.01 
Standards:
Likely used CD-ROM ATAPI-1
Configuration:
DRQ response: 50us.
Packet size: 12 bytes
cache/buffer size = unknown
Capabilities:
LBA, IORDY(cannot be disabled)
DMA: mdma0 mdma1 *mdma2 
Cycle time: min=120ns recommended=120ns
PIO: pio0 pio1 pio2 pio3 pio4 
Cycle time: no flow control=227ns IORDY flow control=120ns

After the drives have unmounted or fail to mount -

$ sudo hdparm -I /dev/{sr0,sr1}

/dev/sr0:
HDIO_DRIVE_CMD(identify) failed: Invalid exchange

/dev/sr1:
HDIO_DRIVE_CMD(identify) failed: Invalid exchange

Help please. This is driving me nuts.
Only solution I have seen on the forums is adding or removing the cdrom line in fstab. This makes no difference to me.

Aaaaaaaaaaargh !

---

### Post by anivegmin on 2010-05-08
Solved my problem - just disconnected one of the drives - now everything works perfectly.

For some unknown reason Ubuntu couldn't cope with having 2 cd/dvd drives connected a the same time.

Only need 1 drive anyway, so now all is fine here.

---

### Post by dino99 on 2010-05-08
think that the problem is about the order : which one is master, which one is slave, read your manual hardware

---

### Post by anivegmin on 2010-05-08
Yeah I tried that.
Read my motherboard manual.

Tried different IDE connector cable configurations (master,slave / master,master) and device jumpers in different configurations, according to the table in the manual.

Maybe I missed the the correct one somehow.

It does make sense that this could be the problem.
Might try again - but just happy it's all working now.

---

### Post by anivegmin on 2010-05-11
Spoke too soon !

Same problem. Even with one drive.

Opened up the computer and checked all IDE connections and device jumper settings.

Both drives show up in BIOS.

Both drives work fine in Windows (which I want to get rid of)

Both drives show up in Disk Utility.

They always work immediately after starting computer - just randomly become inaccessible or wont mount while still showing up as drives in Disk Utility, but with "no medium detected"

Somebody please help me.

---

### Post by osced on 2010-06-13
I have also a similar problem with my DVD and I already have tried all the suggestion here and the only one who have worked is if i put a CD into my DVD player before I start Ubuntu.

//Osced

---

### Post by anivegmin on 2010-06-13
This is it - problem solved at last !

This thread - [http://http//ubuntuforums.org/showthread.php?t=1502874]("http://http//ubuntuforums.org/showthread.php?t=1502874")

Follow these instructions - [https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds]("https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds") for installing the 2.6.34 kernel.

Updating the kernel has fixed the problem for me.
Hurray !

---

### Post by anivegmin on 2010-06-15
Aaaaargh thought it had worked !!!!

Kernel upgrade did not work !!!!!

Problem is worse than ever now !!!!!!!!

I am getting seriously pissed off now !!!!!!!!!!!

This is a major show stopping problem that a lot of other users seem to be experiencing. See various other threads and bug reports.

Why isn't it being fixed ?

---

### Post by allmyfingersandtoes on 2010-06-27
I've just solved a non-mounting DVD drive on a desktop with just the one DVD drive and some hard disks. Problem started on upgrade from karmic to lucid. For weeks I've only been able to access disks by inserting them and restarting. My fix was uninstalling several kernels in 2.6.17 through 2.6.31. I now have only 2.6.32-21 and 2.6.32-22. Maybe unrelated: all the offending kernels have since recently complained of lacking the nvidia driver when I tried to boot them.

---

### Post by anivegmin on 2010-08-05
Well the latest kernel (2.6.35) was released for Ubuntu a couple of days back. After a couple of days testing this has DEFINITELY solved my CD/DVD mounting problems.

Add ppa:kernel-ppa/ppa to your software source list

Reload - then search for "2.6.35" in Synaptic.

Install the following 3 packages (make sure you choose the correct 3 for either 32 or 64 bit. 14 is the latest in the repository so this may change)

linux-headers-2.6.35-14
linux-headers-2.6.35-14-generic
linux-image-2.6.35-14-generic

This kernel will now be the default. Everything now works for me and I have had no problems with it.

---

### Post by Uppsala9496 on 2010-09-11
I recently ran into the same issue.  Here is how I solved it:

Open:  /etc/fstab

You should have the following in the output:
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=987da615-9107-4dd2-8a72-78ab394c50a8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f7f8fcc5-c883-4b19-85fe-9085b22cc8ff none            swap    sw              0       0
/dev/scd0       /media/cdrom0   [COLOR="Red"]udf,iso9660[/COLOR] user,noauto,exec,utf8 0       0

I don't claim to know why the following change works, but it does.
We need to edit the fstab file to swap where "udf" is.

sudo gedit /etc/fstab

Once you enter your password, gedit will open the file.

Move "udf" so the file reads:
/dev/scd0       /media/cdrom0   [COLOR="Red"]iso9660,udf[/COLOR] user,noauto,exec,utf8 0       0



My complete file now looks like:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=987da615-9107-4dd2-8a72-78ab394c50a8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f7f8fcc5-c883-4b19-85fe-9085b22cc8ff none            swap    sw              0       0
/dev/scd0       /media/cdrom0   [COLOR="Red"]iso9660,udf[/COLOR] user,noauto,exec,utf8 0       0

Save the file.  Restart your computer.

My cd/dvd drive has now been able to mount and play/see dvd's.

---

### Post by lbmounse on 2010-09-15
> Well the latest kernel (2.6.35) was released for Ubuntu a couple of days back. After a couple of days testing this has DEFINITELY solved my CD/DVD mounting problems.

Add ppa:kernel-ppa/ppa to your software source list

Reload - then search for "2.6.35" in Synaptic.

Install the following 3 packages (make sure you choose the correct 3 for either 32 or 64 bit. 14 is the latest in the repository so this may change)

linux-headers-2.6.35-14
linux-headers-2.6.35-14-generic
linux-image-2.6.35-14-generic

This kernel will now be the default. Everything now works for me and I have had no problems with it. 

This solved the problem for me.  CD/DVD works fine with 2.6.35-14.  I am currently testing out the latest kernel, 2.6.35-21.

---

