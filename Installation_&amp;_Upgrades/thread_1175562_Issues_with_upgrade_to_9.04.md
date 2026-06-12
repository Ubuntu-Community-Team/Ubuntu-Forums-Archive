---
title: "Issues with upgrade to 9.04"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by naugiedoggie on 2009-06-01
Hello,

Over the weekend I upgraded 8.04->8.10->9.04.  Right now, it's looking like a total f-job.  My CDROM/DVD drive, which was perfectly functional on Friday, has completely disappeared from Ubuntu and Xorg is sucking up 30%-100% of my CPU full time.  I can barely open a browser and type this message.

The fstab line for the drive is still there, but if you try to execute it, mount just messages "special device does not exist."  Possibly, the system moved the drive to another device and didn't update the fstab.  I have no idea what device that would be.

The Xorg thing is equally worrying.  How am I going to figure out what it is doing to cause it to use all the processor all the time?  Right now, system monitor is showing 100% CPU usage nonstop.

Any tips would be appreciated.

Thanks.

mp

---

### Post by drs305 on 2009-06-01
For the xorg issue, were you using proprietary drivers? You can see if they are available but not selected by checking System, Administration, Hardware Drivers. Proprietary video driver selection has come a long way in the past couple of versions - EnvyNG is no longer required in most cases if you are familiar with it from the past.

I think the fstab entry for my cdrom for as long as I can remember has been/is:
> 
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


---

### Post by naugiedoggie on 2009-06-02
> **drs305 said:**
> For the xorg issue, were you using proprietary drivers? You can see if they are available but not selected by checking System, Administration, Hardware Drivers. Proprietary video driver selection has come a long way in the past couple of versions - EnvyNG is no longer required in most cases if you are familiar with it from the past.

I think the fstab entry for my cdrom for as long as I can remember has been/is:

Hello,

Thanks for the reply.  The hardware drivers wizard reports that no prop drivers are in use.  This situation did not occur until 9.04, so I really have no idea what they've done to this new version but it looks like I'm screwed.

I only upgraded so that I could use MonoDevelop 2.0, which requires 9.04.  It's looking like a bad decision.

Re: the ROM drive, the fstab has an entry -- which I'm assuming is from the original file before the upgrade.  It points to /dev/hdd.  Mount reports that there is no such device and indeed, there is no 'hdd' in the /dev directory.  Nor anything else that immediately 'looks like' a ROM drive.

Thanks.

mp

---

### Post by presence1960 on 2009-06-02
From what I have been reading most of the posts complaining about Jaunty have been written by people who have upgraded rather than performing a clean install. For whatever reason the upgrade process seems to be missing the mark. If one backs up their home directory if they don't have a separate home partition then all their data & config files will be retained when they put it back after the install. To save time reinstalling their programs again one can do this from their current install and after the clean install follow the rest of the directions:
```
To replicate your packages selection on another machine (or restore it if re-installing), you can run this:

dpkg --get-selections > ~/my-packages


This will save a file called my-packages in your home directory. Make a backup of it, install the fresh release, then restore the file "my-packages" to new home partition and run this code in the terminal:

sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade


It will download and install all the programs for you, except those that you installed manually, if they are not in the new repository. I did this with Jaunty and a lot of packages I installed manually on Hardy were available in the Jaunty repos. So I didn't search for many applications after the fresh install.
```

P.S. The only programs not covered by the above are those manually installed. You will have to install those again

---

### Post by naugiedoggie on 2009-06-02
> **presence1960 said:**
> From what I have been reading most of the posts complaining about Jaunty have been written by people who have upgraded rather than performing a clean install. For whatever reason the upgrade process seems to be missing the mark. If one backs up their home directory if they don't have a separate home partition then all their data & config files will be retained when they put it back after the install. To save time reinstalling their programs again one can do this from their current install and after the clean install follow the rest of the directions:
```
To replicate your packages selection on another machine (or restore it if re-installing), you can run this:

dpkg --get-selections > ~/my-packages


This will save a file called my-packages in your home directory. Make a backup of it, install the fresh release, then restore the file "my-packages" to new home partition and run this code in the terminal:

sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade


It will download and install all the programs for you, except those that you installed manually, if they are not in the new repository. I did this with Jaunty and a lot of packages I installed manually on Hardy were available in the Jaunty repos. So I didn't search for many applications after the fresh install.
```

P.S. The only programs not covered by the above are those manually installed. You will have to install those again

Hello,

Thanks for the reply.  The effect of a complete reinstall is a bit more complicated than that.  For example, any major software that you use, such as Apache, MySQL, or sendmail, will not be in your home directory.  It's particularly tricky because Ubuntu scatters config files all over the filesystem, so you can't just zip up /etc and be done with it.  I spent a considerable amount of time doing the upgrade, and a complete from-ground-up install is not trivial.  Granted, that is probably the only option I have left, short of going somewhere else.  But, I'm not grooving on it.

Thanks for the tips, I will keep them in mind.

mp

---

### Post by ebb3771 on 2009-07-04
My cdrom also quit working after upgrading from 8.04 -> 8.10 -> 9.04.  I could not mount the cdrom using [FONT=Courier New]mount /media/cdrom[/FONT] in terminal, and [FONT=Courier New]/dev[/FONT] didn't have anything resembling a cdrom drive in it (i.e., no [FONT=Courier New]/dev/dvd[/FONT] or [FONT=Courier New]/dev/sr0[/FONT] or [FONT=Courier New]dev/scd[/FONT] or [FONT=Courier New]/dev/hdb[/FONT]).  

This post solved it for me: [https://answers.launchpad.net/ubuntu/+question/68113](https://answers.launchpad.net/ubuntu/+question/68113)

My cdrom drive is an ISA drive that was jumpered to be a "slave."  When I turned the computer on after changing the jumper to "master," I put in a CD and jaunty recognized it, no problem.

I had already changed the cdrom line in my [FONT=Courier New]/etc/fstab[/FONT] to point to [FONT=Courier New]/dev/sr0[/FONT] instead of [FONT=Courier New]/dev/hdb[/FONT], prior to moving the jumper.   It might be necessary to make this change to your [FONT=Courier New]/etc/fstab[/FONT], too, if you're having the same issue.  The cdrom is now [FONT=Courier New]/dev/sr0[/FONT] ; prior to upgrading my distro, my cdrom was [FONT=Courier New]/dev/hdb[/FONT] .  Something to do with [FONT=Courier New]udev[/FONT] in the new distro I think.

---

