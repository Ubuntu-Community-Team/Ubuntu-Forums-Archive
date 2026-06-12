---
title: "Oh Noes!  Ubuntu will not start..."
date: 2008-08-17
forum: General Help
---

### Post by Ubun00btu on 2008-08-17
Bad times.

I started ubuntu last night and it had some problems.  It kept locking up hard, no mouse - nothing worked;  this would happen at login or randomly after 1-5 minutes after logging in to the desktop.  otherwise I had to do a hard reset of the system and start again.  It finally stabilized for no apparent reason and I did a quick backup and tried to do an update via the update manager to see if that might take care of things in case something got damaged. 

The update froze hard and I had to reboot again.

It will no longer start, it goes through most messages and randomly seems to fail.

I tried the recovery option to do begin the apt-get install -f process and that went into a bunch of errors as well, such as:

Failed to read log page
ATA 2.00 logical block error
Comreset Failed
ext3-fs error
Buffer I/O error on the drive containing the OS.

Running 7.10 (I think).
There have been NO hardware changes.
The drive containing the OS is in good condition.

Is there any way to repair the installation?

---

### Post by cariboo on 2008-08-17
According to what you posted you have a problem with your hard dirve

> Failed to read log page
ATA 2.00 logical block error
Comreset Failed
ext3-fs error
Buffer I/O error on the drive containing the OS.

If you have a LiveCD us it to boot into the desk top, then in a terminal run fsck eg:

```
sudo e2fsck -n /dev/hdX
```

Where /dev/hdX is you hard drive it could /dev/hda1 or /dev/sda1

Jim

---

### Post by Ubun00btu on 2008-08-17
Command returns:

/dev/sda2: clean, xxxxx/xxxxxx files, xxxxxx/xxxxxx blocks (check in 2 mounts)

I left the numbers out, I figured the "clean" was the important part.  I can access all the files on the EXT3 disk no problem.  Everything is there.

---

### Post by Ubun00btu on 2008-08-17
Is there a way to install the new 8.04 or 8.10 while keeping my files and structure accessible under the installation, or will everything be overwritten?  I don't care about the apps, I can reinstall them, I just don't want to lose the files.

---

### Post by Ubun00btu on 2008-09-11
Anybody?  Still no Ubuntu for me...

---

### Post by Ubun00btu on 2008-09-15
*bump*:confused:

---

### Post by Corporal Nickel on 2008-09-15
you said your possibly running 7.10, just upgrade to hardy ive had MAJOR Problems with 7.1 Gutsy. maybe doing that will solve it ;O?

---

### Post by Ubun00btu on 2008-09-15
Can an upgrade be done if I can't start the current installation?  i.e. using a CD?

---

### Post by Ubun00btu on 2008-09-17
Okeedokee then... Guess I'll try the CD and see what happens.

---

### Post by Ubun00btu on 2008-09-17
OK, I tried the Ubuntu LTS CD and it looked like overwriting my previous installation and losing everything was my only option, no "repair" option available.  Isn't there a way to fix Linux like windows where you can replace "registry hives" (I know there isn't a registry in Linux, it just a concept I'm trying to get across)and get things back on the road?  If this is what happens to Linux whenever there's a software problem that doesn't really instill any confidence in me to do anything important on/with this OS again if there's no recourse in the event of failure.

One last request for ideas other than "too bad, so sad...start from scratch."?

---

### Post by wolfen69 on 2008-09-17
insert live cd and a flash drive and save your stuff. then reinstall.

---

### Post by technotitclan on 2008-09-17
that sort of problem doesn't sound like a software problem, honestly sounds like the hard disk is getting a little bit of normal damage (depending on the age of your hard drive). how old is your hdd? and is it a IDE or SATA?

---

### Post by Ubun00btu on 2008-09-18
Less than 1.5 years old, eSATA.  It's partitioned into NTFS, Swap, and EXT3 areas.  The NTFS partition is by far the largest and has no issues, I've checked it.  I also did the file system check in a previous post and it looked OK.  

Not sure what you mean by live CD and flash drive; you mean simply copy everything to the flash drive and start from scratch?  This a dual-boot XP/Ubuntu system with IFSdrives installed on the XP side, so accessing the Linux partition and working with files is no problem whatsoever while in XP, copying them to another drive is no trouble.  I'd really rather avoid having to scrounge through my EXT3 looking for all of my files and moving them and overwriting all of my installed apps and anything important I've missed. You know how it is when you've been using your OS for a while, files tend to get scattered around... Wish I'd been better organized.

---

### Post by Ubun00btu on 2008-09-18
I moved what files I could find to the NTFS partition and tried reinstalling Ubuntu on the EXT3 partition.  The installation "reset" ??? and went back to step 4 on the installation process where you select if you want to do a manual/automatic/guided installation and no longer displayed the HDD that the linux/swap/NTFS partition was on.  For a second there I panicked and thought it had wiped out the partition table and MBR for the HDD, but it was an error with the installation.  

What gives?

---

### Post by Ubun00btu on 2008-09-19
NVM.  Installed over the old one.  Starting again.

---

