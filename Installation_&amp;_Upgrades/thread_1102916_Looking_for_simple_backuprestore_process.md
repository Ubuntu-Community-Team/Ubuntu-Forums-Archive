---
title: "Looking for simple backup/restore process"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by deviant78 on 2009-03-22
Done a search on Google but want to ask here as i'm not too sure.

I recently did a clean installation of Ubuntu 8.10 64bit after deciding to ditch Windows.

The system is up and running just how I want it, so I want to make a backup 'just in case.'

What I'd preferably like, is a way to backup the entire system to a USB stick.

Then, if I need to or want to do a fresh installation I want to be able to boot with a live cd, drop in the USB stick and restore the drive, reboot and its how it was when I made the backup.

Don't know if this is possible, or if there is a better way to do it.

Please explain in easy steps as i'm still learning!

Thanks.

---

### Post by dandnsmith on 2009-03-22
Somewhere in the last couple of days I came across a method of remastering your linux installation to create an ISO file. I thought I got it from [the pendrive linux site](http://www.pendrivelinux.com/), but cannot see it there on a quick hunt. It may even be somewhere on this (forums) site.

Another thought was to use [partimage](http://www.partimage.org/Main_Page) for the backup - I'm not sure if it will write directly to, and restore from a usb stick. I think you'd need a bootable CD to get to restore a wiped system - but that is available (see partimage site) anyway.

---

### Post by wangsuda on 2009-03-22
you could try Quick Start. It is a system backup program with tons of options. you can read more about it here: [http://www.quickstart.freeforums.org/](http://www.quickstart.freeforums.org/)

---

### Post by Mark Phelps on 2009-03-22
Another approach that works (I know, I use it all the time) is to download the P.I.N.G ISO from windowsdream.com, burn it to CD, boot with it, and image your system off to a USB stick.   You can restore your system by rebooting from the CD, and selecting Restoration.

It's a GUI front end to PartImage.

I've used it over a dozen times and it's never failed me.

Check their website for downloads, documentation, and a support forum.

---

### Post by deviant78 on 2009-03-24
Just had a thought, would this work:

To Backup:
1) Boot with live CD and mount the disc where Ubuntu is installed.
2) Copy the contents of that drive to another drive / USB stick.

To Restore:
1) Boot with live CD and mount the disc where Ubuntu is to be installed.
2) Copy the contents of backup drive / USB stick to the installation drive.

Reboot.

To me this would be a nice simple way to do it, but would it work?

The problem I can see if permissions/ownership.
When ever I've copied backups from a disc before they are read only and I have to chmod -R 777.
I guess I would need to run a command to keep ownership, rather than just copy and paste.

---

### Post by happyhacker on 2009-03-25
I am interested in backup (not having a system in place yet). Which backup method will ensure all the aptget installed programs get put back, so effectively no further work is needed to restore to the last state?

PS I would much rather backup to the laptop I use for managing the network (including the server). I visit once per week and would like to just copy the latest image across. Or maybe webmin can do this when I plug the laptop into the system?

---

### Post by MORUNDAH 1 on 2009-03-25
High` I am new to ubuntu and would like to know how you loaded it onto your hard drive .I have tried booting it onto my corrupted second hard drive from BIOS, but it just goes past the- boot from cd- prompt and loads the stuffed windows up to login request and does nothing else, thanks GRAHAM

---

### Post by wkulecz on 2009-03-25
IMHO, rsync is the best solution to this issue.  The only fly in the ointment is the USB stick has to be as large as your system and in a Linux format to be sure permissions are preserved properly.  I use a hard drive and a USB to IDE adapter ($20), but a USB stick will work if you format it to match your / filesystem and its large enough.

Backup:
sudo rsync -ax / /media/usbstick (or whatever it gets named)
(you can ignore the *.gvfs errors from rsync)

Repeat the command after every system change, I run it nightly from a cron job surrounded by mount and umount commands so its not always on-line for possible accidental corruption.


Restore:
Boot a live CD, and start a root terminal 
mount what will be your new / partition and  the USB stick.
rsync -ax /media/usbstick/ /media/sda1 (or wherever they end up)

The trailing / on the source directory of rsync is important!

As long as your restore partition is the same layout as before, all you need to do is re-install grub and you are back in business.  If not you'll have to edit /etc/fstab and /boot/grub/menu.lst to account for the new partition layout before the first boot.  Again this can be done from the live CD once the rsync is complete.

The "Super Grub Boot CD" is good to have on hand for that first bootup after a restore, but you can reinstall grub using the live CD as well.  Instructions are on the forum.

HTH,
--wally.

The above assumes everything is on one  partition, otherwise you have to account for the different partitions with multiple rsync commands.

---

### Post by bigbencg on 2009-03-25
I also use partimage, I found a nice disk with several utilities on it at [http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page"), this does not have a GUI and is prompt based.  The thing with partimage is the file systems you are backing up cannot be in use.  You have to boot from some other media, like the rescue CD, and mount the drives once booted from the CD.  So you will mount the drive to be backed up, mount the destination drive, and simply type partimage.  From there it is pretty easy, just select your options and the image will be created.

---

### Post by fourthofjuly on 2009-03-25
[COLOR="Teal"][SIZE="4"]hi,

your entire ubuntu installation with all your settings, applications, themes can be backed up in a tarball (a single tar file that can be saved to your thumbdrive) from the command line... you need not install any utility for this purpose... everything is built-in you see, you only need to know how to use it!!!

the best part is, you can do this on a live system...

if you wish to restore your original settings after a crash, 

1) reinstall ubuntu from the install cd/dvd and
2) untar all files back to / folder in your newly installed system.

check out this excellent tutorial ...

[http://ubuntuforums.org/showthread.php?t=81311&highlight=backup]("http://ubuntuforums.org/showthread.php?t=81311&highlight=backup")

be careful if you have multi-boot systems though as you will have to restore grub, which i found a little tricky...

cheers!

fourthofjuly.

  [/SIZE][/COLOR]

---

### Post by happyhacker on 2009-03-25
> **fourthofjuly said:**
> [COLOR="Teal"][SIZE="1"]hi,

your entire ubuntu installation with all your settings, applications, themes can be backed up in a tarball (a single tar file that can be saved to your thumbdrive) from the command line... you need not install any utility for this purpose... everything is built-in you see, you only need to know how to use it!!!

the best part is, you can do this on a live system...

if you wish to restore your original settings after a crash, 

1) reinstall ubuntu from the install cd/dvd and
2) untar all files back to / folder in your newly installed system.

check out this excellent tutorial ...

[http://ubuntuforums.org/showthread.php?t=81311&highlight=backup]("http://ubuntuforums.org/showthread.php?t=81311&highlight=backup")

be careful if you have multi-boot systems though as you will have to restore grub, which i found a little tricky...

cheers!

fourthofjuly.

  [/SIZE][/COLOR]

So, is this sufficient if the hard drive is changed due to it being faulty?

---

### Post by wkulecz on 2009-03-25
> **cantthinkofanickname said:**
> So, is this sufficient if the hard drive is changed due to it being faulty?

Yes, becuase the tar/untar method requires you to reinstall from the CD and then restore.

The rsync method "clones" your system to a freshly formatted drive which can be larger (or smaller as long as its bigger the the actually used space).  The reinstalling grub is practically automatic if you have the "Super Grub Boot CD".

I find the rsync method far superior, although tar and rsync are about the same speed for the initial backup, rsync is much faster for subsequent updates as the system evolves, as only changed data is copied.  Not having to install the basic OS before the restore saves time too, although you can do this with the rsync method as well if you are really afraid of installing grub.

Partimage is a poor imitation of Ghost, and the fact you have to shutdown to backup practically insures you will have an out of date backup should you need it. I used it (and tar/untar back in my RedHat 3 days) before I discovered rsync, never looked back since. 

As I said rsync can run as a cron job and keep your system backup up to date automatically.  If my hard drive died right now, I'd only lose changes to my hard drive since 1AM last night!

Ubuntu's excellent automatic driver installation has even allowed me to restore my system to grossly different motherboards with only the occasional Xserver issue due to different video boards.  Good luck with this on a Windows system!

--wally.

---

### Post by fourthofjuly on 2009-03-27
> **cantthinkofanickname said:**
> So, is this sufficient if the hard drive is changed due to it being faulty?
i don't think so ... it may create problems if there are hardware changes... because your original configuration is set for the older hard drive (which you are backing up), and if you try to force this config to the new hardware, it may lead to undesirable results...

please do not experiment until you receive further confirmation...

---

### Post by wkulecz on 2009-03-27
I should mention one "new" feature does cause me trouble with 8.04 -- the mounting of partitions by UUID instead of device names for the partitions.

My solution is to edit /etc/fstab amd /boot/grub/menu.lst to change all the installer created UUID references back to the /dev/hd or /dev/sd device names.  For a reason I don't understand, some motherboards the installer sets up as /dev/hd for the IDE ports and others set them up /dev/sd.  Its another "glitch" caused by "improvements" but is easily fixed with the live CD and  edits of the restored /etc/fstab and /boot/grub/menu.lst files if it causes issues with a restore to a new motherboard.

I'd really like to know the logic behind mounting by UUID which appears to change everytime a partition is formated.  Maybe partimage preserves the UUIDs, but the trade-off of not being able to back up a mounted partition is too big a price to pay in terms of keeping backups current and up to date.

RedHat's mount by partition label looked good initially but collision of installer created label names made multi-boot setups a royal PITA!

So I guess the short answer is: there really is no "simple" backup/restore method.  Although I claim rsync on a single drive system with only / and swap partitions is about as good as it'll likely ever get if you rsync nightly to a second drive.

--wally.

---

### Post by wkulecz on 2009-03-27
> **fourthofjuly said:**
> i don't think so ... it may create problems if there are hardware changes... because your original configuration is set for the older hard drive (which you are backing up), and if you try to force this config to the new hardware, it may lead to undesirable results...

please do not experiment until you receive further confirmation...

I've cloned Ubuntu systems to very different hardware, for example from Dual CPU PIII to Athelon K7 changing partition sizes along the way (both smaller and larger).  The auto hardware detection is way more effective than with Windows and in fact, my only issues have been with the X server when using binary drivers, which again, is easily fixed with boot to recovery mode and edit of xorg.conf, if a second boot attempt doesn't automagically rewrite xorg.conf.

I can't possibly stress how much of a time saver Linux's lack of "activation" is when you replace a failed motherboard!

You may run into trouble if you use a highly tuned and specific kernel, but as long as you keep a -generic around in your menu.lst file, odds are you can get the restored system running quickly again after hardware failures.

--wally.

---

### Post by fourthofjuly on 2009-03-29
> **wkulecz said:**
> I've cloned Ubuntu systems to very different hardware, for example from Dual CPU PIII to Athelon K7 changing partition sizes along the way (both smaller and larger).  The auto hardware detection is way more effective than with Windows and in fact, my only issues have been with the X server when using binary drivers, which again, is easily fixed with boot to recovery mode and edit of xorg.conf, if a second boot attempt doesn't automagically rewrite xorg.conf.

I can't possibly stress how much of a time saver Linux's lack of "activation" is when you replace a failed motherboard!

You may run into trouble if you use a highly tuned and specific kernel, but as long as you keep a -generic around in your menu.lst file, odds are you can get the restored system running quickly again after hardware failures.

--wally.
thanks for sharing your experience... 

if i understand this correctly, even if my harddrive fails, i can swap it with a new one (different capacity drive) and restore my backup from the zipped archive file i backed up with my old harddrive? will not cause problems, right?

if it works with a new motherboard, i suppose it will work with a different harddrive as well, right?

---

