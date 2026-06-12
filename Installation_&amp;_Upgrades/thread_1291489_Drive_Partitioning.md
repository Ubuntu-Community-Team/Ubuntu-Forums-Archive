---
title: "Drive Partitioning"
date: 2009-10-14
forum: Installation &amp; Upgrades
---

### Post by Shibblet on 2009-10-14
Right now, I am running 9.04 Jaunty, and I set my drives up like so...

20g /
2g Swap
478g /home

Now, If I go to install Karmic, I only need to format my / drive, correct?

I only ask because I've done this before, and all of my settings are still there.  Themes, programs, etc.

What type of drive should I be using if I don't want any system files installed on it?

---

### Post by Bartender on 2009-10-14
Yeah, go into manual partitioning and mount the previous /home as /home again.
Use the same username (and password I imagine) as before, otherwise Ubuntu will ignore the existing /home and put a new one in /.

I don't know if the new version of GRUB in Karmic changes things or not.  I don't think so as long as this is a straightforward install without dual-booting and such (?)

---

### Post by raymondh on 2009-10-14
Remember ... mount, but DO NOT FORMAT,  /home.

Regards,

---

### Post by Shibblet on 2009-10-14
So certain things do get loaded on the /home drive that are used for the system.  Is there a way to mount the drive that it is only used as data storage?

---

### Post by raymondh on 2009-10-14
> **Shibblet said:**
> So certain things do get loaded on the /home drive that are used for the system.  Is there a way to mount the drive that it is only used as data storage?

Is there a second HD aside from the 480GB /home?  If so, Ubuntu ought to read it (see 'places') just like it is mounted right now (I presume it is).

---

### Post by Shibblet on 2009-10-14
> **raymondhenson said:**
> Is there a second HD aside from the 480GB /home?  If so, Ubuntu ought to read it (see 'places') just like it is mounted right now (I presume it is).

No, but I could set one up that way.

Are you supposed to do a 10g /, a 10g /home, and then a third partition?

---

### Post by raymondh on 2009-10-14
> **Shibblet said:**
> No, but I could set one up that way.

Are you supposed to do a 10g /, a 10g /home, and then a third partition?

Before I misunderstand you ;) .....

Your current set-up is nice and OK.  When you install Karmic, remember to mount /home but do not format.

If you decide to add another HD to be used as data ..... Ubuntu will automount.  If not, it'll be a terminal command to mount the drive.

Regards,

---

### Post by Shibblet on 2009-10-15
> **raymondhenson said:**
> Before I misunderstand you ;) .....

Your current set-up is nice and OK.  When you install Karmic, remember to mount /home but do not format.

If you decide to add another HD to be used as data ..... Ubuntu will automount.  If not, it'll be a terminal command to mount the drive.

Regards,

Right, but if I don't format the /home drive, my settings from the previous installation are still there.  Why is that?

---

### Post by helicase on 2009-10-15
Is there a particular reason why you want to do a fresh install instead of an upgrade? If you do an upgrade there's no need to meddle with any partitions.

---

### Post by Shibblet on 2009-10-15
> **helicase said:**
> Is there a particular reason why you want to do a fresh install instead of an upgrade? If you do an upgrade there's no need to meddle with any partitions.

Hey Mom, did you ever get that "not-so-fresh" feeling?

No, no particular reason.  Just wondering.

---

### Post by Niko Johnson on 2009-10-15
if you only want data storage you can always make a partition mounted on /data, we have most of our work servers set up that way

---

### Post by raymondh on 2009-10-15
> **Shibblet said:**
> Right, but if I don't format the /home drive, my settings from the previous installation are still there.  Why is that?

Think of mounting /home as "attaching it to root (/)".    So, when you mount and **FORMAT** ...... the installer **erases current** content, writes a new format and then attaches to root.  

I am under the impression that you wanted to retain your current /home (and its' contents, settings, etc) hence the advise to MOUNT /home .... do not format.

Regards,

---

### Post by Shibblet on 2009-10-15
> **raymondhenson said:**
> Think of mounting /home as "attaching it to root (/)".    So, when you mount and **FORMAT** ...... the installer **erases current** content, writes a new format and then attaches to root.  

I am under the impression that you wanted to retain your current /home (and its' contents, settings, etc) hence the advise to MOUNT /home .... do not format.

Regards,

I don't want to retain the system information on /home, just my media.  And it sounds like that would be better set up as /data.

---

### Post by raymondh on 2009-10-15
> **Shibblet said:**
> I don't want to retain the system information on /home, just my media.  And it sounds like that would be better set up as /data.

This is my set-up in my test computer (which is also the general household computer). Hopefully it can give you clues on what you want to accomplish.

3 HD's
HD1 - Jaunty and Windows (full production)
HD2 - Karmic (for testing and tweaking only)
HD3 - data and media storage (in NTFS) which can be accessed by any OS

My ubuntu installs (Jaunty and karmic)
root  - 10GB
/home - 30GB (for distro specific configuration files, settings)
swap  - 2GB

GRUB is installed in the MBR of HD1 and HD2 (GRUB2 in HD2).  BIOS is set to boot HD1 first.  When I want to work on tweaking Karmic, I change the order in BIOS.

When I am happy with Karmic, I then set BIOS to boot HD2 first .... then add windows on it .... then use HD1 as a testing ground for the next version.

I have windows in it's own partition (50GB) but rarely access it as I virtualize windows XP (as guest) in Ubuntu (the host).  I just have it there just in case virtualbox borks and I need, at that moment, to get into windows.

Regards,

---

### Post by Andrews222 on 2009-10-15
Hi,
I'm VERY new to Ubuntu and the learning curve is a bit steep (to grasp the under the hood stuff).  I'm on 9.04 and recently read that some users will do fresh installs once a new version is out.  Sounds fine.

However, when I installed this laptop, I used the "entire disk" option which (I think) means that I have only one large partition.  Seems there's a school of thought that suggests that a "system" partition should be installed so re-installations could be performed without putting data at risk.

Is there a utility (like the old DOS/Windows FDISK that shows the current setup?  Can it be modified at this late stage.  I haven't modified my directory/storage structures at all, but I HAVE loaded up my HOME folder with LOTS of data.

Any suggestions as to how I might approach this would be much appreciated.

---

### Post by Shibblet on 2009-10-15
> **Andrews222 said:**
> Is there a utility (like the old DOS/Windows FDISK that shows the current setup?  Can it be modified at this late stage.  I haven't modified my directory/storage structures at all, but I HAVE loaded up my HOME folder with LOTS of data.

Any suggestions as to how I might approach this would be much appreciated.

That one I do know.  Go to Add/Remove Programs and search for "GParted"  That's the gnome partition editor.  It will do what you are asking.

---

### Post by Andrews222 on 2009-10-15
Perfect... I think.
I'll have to go through the help facility in order to understand what I'm looking at, but it's nice to have a graphical utility to use.

Quick jump-off question... the attached image shows the GPARTED screen.  Is my assumption correct that this is one large partition?

[IMG]file:///home/andrew/Desktop/Screenshot--dev-sda%2520-%2520GParted.png[/IMG]Note:  I'm hoping the image actually got attached.  I can't tell.

---

### Post by Shibblet on 2009-10-15
> **Andrews222 said:**
> Quick jump-off question... the attached image shows the GPARTED screen.  Is my assumption correct that this is one large partition?

It is.

---

### Post by raymondh on 2009-10-15
> **Andrews222 said:**
> Hi,
I'm VERY new to Ubuntu and the learning curve is a bit steep (to grasp the under the hood stuff).  I'm on 9.04 and recently read that some users will do fresh installs once a new version is out.  Sounds fine.

However, when I installed this laptop, I used the "entire disk" option which (I think) means that I have only one large partition.  Seems there's a school of thought that suggests that a "system" partition should be installed so re-installations could be performed without putting data at risk.

Is there a utility (like the old DOS/Windows FDISK that shows the current setup?  Can it be modified at this late stage.  I haven't modified my directory/storage structures at all, but I HAVE loaded up my HOME folder with LOTS of data.

Any suggestions as to how I might approach this would be much appreciated.

If you just want to see how your HD is partitioned (**without touching it**), go to system > administration > partition editor (gparted).  Gparted will open (after the mandatory type-your-password) and show you how it is partitioned.

Another way is to access a terminal (applications > accessories) and type
```

sudo fdisk -l
```

small L, not 1 nor I.  Your password will be required which when you type, will be invisible so don't worry.


If you want to "work" on those partitions, you need to use gparted from the liveCD.  Boot into the liveCD and go live session (TRY UBUNTU...).  **That will unmount the partitions allowing you to work on them.**

Another tool is to go ahead and download the latest gparted and burn it into a CD (making a live gparted CD).  That will also unmount the partitions for working.

As for separating /home at this "late stage" ... it is possible.  Here is a tutorial from psychocats.  It may be detailed and look daunting so post back for clarifications or even better, send psychocats an email.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

As always, have a back-up of your valuable files before proceeding.  Most important !

Happy ubuntu-ing.

---

### Post by Andrews222 on 2009-10-17
Thanks a lot Raymond.  As soon as I find the intestinal fortitude, I'll move forward on all this - got to find a backup solution first though.  Thanks for that good advice.
I'll let y'all know how it all turns out.

---

### Post by Andrews222 on 2009-10-17
Fantastic.

Thanks Raymond.  Worked like a charm.  I plan to send thank you's to psychocats as well.

- Andrew

---

### Post by raymondh on 2009-10-17
> **Andrews222 said:**
> Thanks a lot Raymond.  As soon as I find the intestinal fortitude, I'll move forward on all this - got to find a backup solution first though.  Thanks for that good advice.
I'll let y'all know how it all turns out.

For back-up .... I use RSYNC in conjunstion with GRSYNC (the GUI).  Both are in the repos.  Back-up is done weekly.

I also use PING to clone my partitions (or HD) just in case.

[http://ping.windowsdream.com/](http://ping.windowsdream.com/)

Happy ubuntu-ing.

---

### Post by raymondh on 2009-10-17
> **Andrews222 said:**
> Fantastic.

Thanks Raymond.  Worked like a charm.  I plan to send thank you's to psychocats as well.

- Andrew

well done. Glad to hear the good news.

---

