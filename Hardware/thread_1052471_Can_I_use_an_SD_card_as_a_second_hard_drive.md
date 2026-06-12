---
title: "Can I use an SD card as a second hard drive?"
date: 2009-01-27
forum: Hardware
---

### Post by wordrush on 2009-01-27
Let me explain my dilemma. I have a Dell Mini 9 that comes with a solid state hard drive which has a capacity of only 4 GB. I tried to install some programs that I need for school onto the hard drive but it took up 100% of my space.

I bought a 16 GB SD card so that I could instead install these programs onto the SD card, run the programs from there, and keep the OP on the system hard drive. Simply put I want to use the SD card as a secondary hard drive.

I am not used to ubuntu, and I have no idea how to compile programs.  Right now I don't have the time to learn how either.  I want to be able to install programs directly to the SD card using the add/remove applications utility.  Is that possible?

---

### Post by paulisdead on 2009-01-27
Ok, Linux and *nix based OSes don't install most things to a single folder, they tend to have files spread around in different directories.  I know coming from the windows world, this seems stupid and wrong, but there are reasons behind it.  Different directories are for different things, like /sbin is for system binaries (executables), /usr tends to be for user based executables, /etc is for configuration files.  So it's sorted more by what they are and what they do, than by the individual app typically.  Another reason it's done this way, is programs will share and utilize each others files.  Lots of programs are very small because of this.  For example, The GIMP, Nautilus, and firefox are all using the same libpng files in the OS to render .png files.

So, to answer your question is, sort of.  I'd expect it won't be anywhere near as fast as the internal drive, for one thing.  The easiest way to make this happen is to simply use the drive as the /usr partition.  I think the easiest way for you to accomplish that is to reinstall, do manual partitioning, and create a partition on the SD drive for use as /usr.  I normally run /usr as a seperate partition, and it's like 2.4GBs on my system right now, so that could save you some space.  Asides from /home, /usr is normally the biggest folder on my systems since it contains the most programs, so that likely will help the most.  I've never tried partitioning an sd card, but I'd expect it'll work, so you could get /home on there as well.

There's another way to accomplish this without reinstalling, but could be tricky for you.  You boot a livecd, and as root (or sudo'd), you copy over all the data from the /usr or /home directories to where they should go on the SD card.  If you do that you have to use the command line, since you need to do it as a cp -Rp for the copy command, otherwise it'll screw up all the permissions and you'll be hosed.  Once the files are copied to the new locations, edit the /etc/fstab file as needed for the new partitions, then you can do a test boot.  If everything works, boot the livecd, and remove the files from the original location.

So it's probably a lot easier for you to reinstall, pick advanced partitioning, and tell it to put /home and /usr on the SD card during the install.  On the main drive you just need / and a swap partition.

---

### Post by electrogeist on 2009-01-27
Another approach might be using UnionFS?

> **wordrush said:**
> Right now I don't have the time to learn how either.  But then again, probably a No

---

### Post by wordrush on 2009-01-29
> **paulisdead said:**
> So, to answer your question is, sort of.  I'd expect it won't be anywhere near as fast as the internal drive, for one thing.  The easiest way to make this happen is to simply use the drive as the /usr partition.  I think the easiest way for you to accomplish that is to reinstall, do manual partitioning, and create a partition on the SD drive for use as /usr.  I normally run /usr as a seperate partition, and it's like 2.4GBs on my system right now, so that could save you some space.  Asides from /home, /usr is normally the biggest folder on my systems since it contains the most programs, so that likely will help the most.  I've never tried partitioning an sd card, but I'd expect it'll work, so you could get /home on there as well.

Thanks, I'll have to give that a try whenever I get a chance.  I am not sure how easy it will be to reinstall on this computer though.  Thanks again.

---

### Post by jerome1232 on 2009-01-29
Well it could all be done from a live cd without reinstalling, You'll basically format and partition the sd card, copy all files under /usr (using rsync or something that handles symlinks and hardlinks correctly) to it, then delete all the files in your old /usr, then edit /etc/fstab to mount the sd card as /usr.

---

### Post by wordrush on 2009-01-29
> **jerome1232 said:**
> Well it could all be done from a live cd without reinstalling, You'll basically format and partition the sd card, copy all files under /usr (using rsync or something that handles symlinks and hardlinks correctly) to it, then delete all the files in your old /usr, then edit /etc/fstab to mount the sd card as /usr.Ok, I'll try that first.  Problem is, I don't have a cd drive, but granted, I will have to get one for both ways.  Thanks.

---

### Post by paulisdead on 2009-01-29
> **jerome1232 said:**
> Well it could all be done from a live cd without reinstalling, You'll basically format and partition the sd card, copy all files under /usr (using rsync or something that handles symlinks and hardlinks correctly) to it, then delete all the files in your old /usr, then edit /etc/fstab to mount the sd card as /usr.

cp -Rp has worked fine for me when cloning systems in the past.  I mentioned this method in my first post, but I really think it's easier for him to just reinstall.  I don't think he'll be entirely comfortable with the command line to do it, unless he has step by step instructions.  If you go this route, don't delete the old /usr until you've done a test boot, verify it's mounted correctly (df -h will show you), then you can boot the livecd again and delete the files/folders inside the old /usr.  Always test before you do anything you can't take back.

---

### Post by jerome1232 on 2009-01-29
> **paulisdead said:**
> cp -Rp has worked fine for me when cloning systems in the past.  I mentioned this method in my first post, but I really think it's easier for him to just reinstall.  I don't think he'll be entirely comfortable with the command line to do it, unless he has step by step instructions.  If you go this route, don't delete the old /usr until you've done a test boot, verify it's mounted correctly (df -h will show you), then you can boot the livecd again and delete the files/folders inside the old /usr.  Always test before you do anything you can't take back.

I didn't even see that you did mention it. I didn't think anyone mentioned it's possible to do without reinstalling. Only reason I brought it up.

yes I agree, it is a task best left to someone familiar with linux command line tools that's for certain.

Although if you copy /usr over to the sd card I don't see the problem with deleting it off your root partition, you've still got a copy you can restore from the sd card.

---

### Post by paulisdead on 2009-01-29
> **jerome1232 said:**
> I didn't even see that you did mention it. I didn't think anyone mentioned it's possible to do without reinstalling. Only reason I brought it up.

yes I agree, it is a task best left to someone familiar with linux command line tools that's for certain.

Although if you copy /usr over to the sd card I don't see the problem with deleting it off your root partition, you've still got a copy you can restore from the sd card.

That's assuming you copied it to the SD card correctly.  It would not be a pretty site if he didn't preserve permissions on those files when he did it.

---

