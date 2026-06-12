---
title: "Unable to execute /bin/sh - Permission Denied"
date: 2008-01-10
forum: Hardware &amp; Laptops
---

### Post by julied on 2008-01-10
Hello,

I am currently running Fiesty Fawn and I modifed my fstab file  to automatically detect and mount the disk by any user in order to avoid having to type the root password everytime I wanted to access the drive (I did made a backup of fstab beforehand).

However, upon rebooting my machine, I am now receiving the error /etc/init.d/rc Permission Denied Unable to execute /bin/sh for rc-default.

Can anyone provide some assistance?

Thank you,
Julie

---

### Post by Sef on 2008-01-10
unlocked.

---

### Post by peitschie on 2008-01-10
Hi julied,

Can you please post up the original fstab and the modified fstab?

This sounds like a permissions problem on the drives you are mounting.

Also, is it possible to edit the first post and get rid of the triplicate content?

---

### Post by julied on 2008-01-10
I removed the duplicated content.  Unfortunately, I can't event boot the computer up in order to grab the original and modified fstab. 

I have the 7.04 installation CD in my CD rom and am attempting to boot from there but no success there either.

---

### Post by peitschie on 2008-01-11
Cant boot from the installation cd.... that is intruiging...

What do you mean you can't boot from the 7.04 installation CD?  As in you can't X to load?  No boot prompt after inserting the CD?  What CD did you use to install Ubuntu in the first place?

If we can get a Live CD to work, we can use that to get your fstab file :)

---

### Post by julied on 2008-01-11
I have the 7.04 installation CD in the CD rom drive and I made sure that the bios boots from the CD rom.  The CD only has one big .iso file on it.  Should it have more files than this?  I did a file check sum and it all checked out.  Not sure what else to do.

I was questioning whether the CD rom was working so I put in an XP installation unattended CD and my computer read that no problem therefore I know that the CD rom is workng.

Since I did make a back up of my fstab (/home/julie/Desktop), is there a way to copy the fstab from my home directory to the /etc/ directory using grub?  This may seem like a stupid question, I'm a newbie.

Thanks,
Julie

---

### Post by peitschie on 2008-01-11
Hi Julie,

That installation cdrom is not correct.  You will need to burn a new cd, following the instructions found on this ubuntu Wiki page: [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

Basically, the ISO file is a cd-image... it needs to be extracted to the cd essentially, it can't simply be copied onto the cdrom.  If you can burn a new copy, then it should boot and work.  Once we can get Ubuntu to work somehow, it is relatively straightforward to restore your fstab

In case you have internet space to burn, there is a newer release of Ubuntu, version 7.10 which I would highly recommend you download and try :-)

---

### Post by julied on 2008-01-11
Okay thank you.  I am in the process of creating a correct imaged Ubuntu 7.04 and Ubuntu 7.10 bootable CDs.  In the meantime, can you provide me with the appropriate command/steps for what I would need to do once I am successfully able to boot from the CD.

Thank you,
Julie

---

### Post by taurus on 2008-01-11
If you boot your machine from a LiveCD, then you need to mount your harddrive where / is located so you can modify /etc/fstab from it.  Assuming your / is resided on /dev/sda1, you can do something like

Applications -> Accessories -> Terminal
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda1 /media/ubuntu
gksudo gedit /media/ubuntu/etc/fstab
```

---

### Post by Keith Hedger on 2008-01-11
try mounting the disk and right click->proerties->volume and set mount options to exec

---

### Post by julied on 2008-01-11
Thank you!  This did the trick.  I am now back in business.  

This whole problem started because I edited my fstab tab.  My  goal is to eliminate having to type in the "Access to this internal disk is restricted to system administrators for security reasons.  Please enter your password to proceed." every time I select a certain drive.

Here is a copy of my fstab.  What is the correct way to edit this file so that I do not have to type in the administrator password everytime?  Should I open up a new post for this?  The disk (mount point?) is /dev/sda1

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=a2ae5cb6-26bd-4e79-a94a-807381f11ed4 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=1fdc3693-349e-4ea0-bb89-0a464ce1747a none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
#Added by diskmounter utility
/dev/sdd2 /media/sdd2 vfat rw,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0

Thanks,
Julie

---

### Post by julied on 2008-01-11
Through what application can I right click->proerties->volume and set mount options to exec?

Thanks,
Julie

---

### Post by taurus on 2008-01-11
> **julied said:**
> 
Here is a copy of my fstab.  What is the correct way to edit this file so that I do not have to type in the administrator password everytime?  Should I open up a new post for this?  The disk (mount point?) is /dev/sda1

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
**[COLOR="Blue"]UUID=a2ae5cb6-26bd-4e79-a94a-807381f11ed4 / ext3 defaults,errors=remount-ro 0 1[/COLOR]**
# Entry for /dev/sda5 :
UUID=1fdc3693-349e-4ea0-bb89-0a464ce1747a none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
#Added by diskmounter utility
/dev/sdd2 /media/sdd2 vfat rw,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0

Thanks,
Julie

Wait a second.  /dev/sda1 is your / so what are you trying to do with it?  You shouldn't play around with permissions for your / because you could break your system beyond repair.

If you want to edit /etc/fstab, just open a terminal and run

```
gksudo gedit /etc/fstab
```

---

### Post by Keith Hedger on 2008-01-11
from the desktop do right clic etc.
to auto mount  your disk crate a folder somewher ie ```
mkdir /media/THEDISK
```
and add this line to your fstab ```
UUID=THEDISKSUUID /media/THEDISK               ext3    defaults 0       0
```

the uuid for your disk can be found by right clicking it on the desktop and going to properties->volume or using the vol_id command from the terminal. you should also adjust the type (ext3), reboot and the disk should mount ok

---

### Post by peitschie on 2008-01-11
Are you sure it was /dev/sda1?  As taurus commented, this is your root drive!  If you didn't have proper permissions to this drive your computer wouldn't boot ;-)... and that fstab line looks fine.  I suspect the line causing you the problem *might* be the last one:

```
/dev/sdd2 /media/sdd2 vfat rw,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0
```

the "uid=...gid=..." hard-codes the user this drive belongs to, which may not be your user's values.  You can check by opening up a terminal (Applications->terminal), and typing
```
id <username>
```

Is this the non-working fstab or the working one?  You said this was the original one... what did you attempt to modify it to?

---

### Post by julied on 2008-01-13
I truly appreciate everyone's knowledge and help here but am a bit lost.  I have to say that I am very confused at this point. 

My goal here is that when the Ubuntu OS has completed booting up and I go to Places=>Computer and then I double click on my 465.8GB Volume: disk, I do not want to be prompted to enter a password everytime I try to access this drive right after the computer has completed booting up.  Am I making sense?  Is it possible to suppress this prompting of the password?

Thank you,

Julie

---

### Post by peitschie on 2008-01-14
It's ok... as long as you keep asking we can continue to attempt to clarify!

Basically, I believe you are being prompted for your password because of some misconfiguration in your current fstab file.  

[LIST]
[*]You mentioned that this prompting is happening when you click on your 465Gb volume... is this the volume that Ubuntu is stored on?  Or is this a seperate partition?  
[*]What is the mount point (/media/?? or / if its the root partition) of this drive when you open it?
[*]Are you prompted for a username and password (with the option to remember the password), or is it similar to the gksu prompt (more like this: [http://www.howtogeek.com/wp-content/uploads/2006/11/WindowsLiveWriter/StartanUbuntuGnomeApplicationasRootUser_4218/gksupass.png](http://www.howtogeek.com/wp-content/uploads/2006/11/WindowsLiveWriter/StartanUbuntuGnomeApplicationasRootUser_4218/gksupass.png))
[*]Is the fstab you posted the one you are currently using?
[/LIST]

Sorry it's taking so long to find the problem :(... don't give up yet though!

---

### Post by julied on 2008-01-14
Thank you for being so patient and understanding with me. :KS

When I perform a fdisk -l, here are my mount points:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60044   482303398+  83  Linux
/dev/sda2           60045       60801     6080602+   5  Extended
/dev/sda5           60045       60801     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux


I believe that the 465 Gb hard drive which I'm access is "/dev/sdb1" which to me navigating through the GUI OS translates to "/media/disk".  So to answer your question, I don't know if this is the partition that Ubuntu is stored on.  Let me know if there is something I can do to find this out.

I am also attaching my live production fstab file.

Thank you,
Julie

---

### Post by polmir on 2008-01-14
type in terminal

```
ls -l /dev/disk/by-uuid
```

and copy out info here.

---

### Post by Yellow Pasque on 2008-01-14
Ok. It should be pretty simple from here. First, you need to decide what directory you want to mount to, so look in your media directory and see if there's a folder already created for it:
```
cd /media; ls
```
Note that sdd2, cdrom0 and floppy0 are already in use. So if there's not another directory, make one with a sudo mkdir <nameofdir> command (omit brackets).

Then add the appropriate entry to your fstab:
```
/dev/sdb1  /media/<nameofdir>  auto   auto,exec,user   0 0
```
Note that the first 'auto' is the file system type. If you know what type it is (e.g. ext3), go ahead and put that instead.

---

### Post by peitschie on 2008-01-14
> **julied said:**
> 
I believe that the 465 Gb hard drive which I'm access is "/dev/sdb1" which to me navigating through the GUI OS translates to "/media/disk".

Hmm... the plot thickens...  /media/disk is usually used by Ubuntu to mount connected USB drives!  Is the hard-drive an external USB drive by chance?  Either way, Temüjin's advice about the addition to the fstab is good and may get the drive mounting properly.  Give that a shot and lest us know how it goes :)

Could you please also paste the output from running:
```
sudo mount
```

Post up both PRIOR to trying to open the drive (i.e., just after a clean boot before you have opened the disk), and then AFTER you have opened the drive (and entered your password).  This will tell us fairly definitely which disk it is mounting and how :)

Keep up the good work too by the way... many other people would have stopped providing useful information and taken to complaining by now lol.  We'll get this fixed.

---

### Post by polmir on 2008-01-14
Temüjin
```
cd /media; ls -l
```

---

