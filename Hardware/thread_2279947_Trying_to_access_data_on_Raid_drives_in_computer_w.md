---
title: "Trying to access data on Raid drives in computer with corrupt OS"
date: 2015-05-26
forum: Hardware
---

### Post by jnealand on 2015-05-26
I am trying to recover data from a laptop that is configured with two drives as a raid 0.  The windows OS is corrupt and I have been unsuccessful with several repair attempts.  I am using a Ubunto live Cd with persistence and booting from a USB flash drive.  I can see the two disks in the disks app.  The first is /dev/sda1 and the second is /dev/sdb and both are noted as an Intel Matrix raid members with the note Disk is ok.  I have installed mdadm, and have been trying various commands in terminal, but I'm getting nowhere as I am a linux newbie (but a very experienced Windows guy).  The owner has a lot of vacation photos on the drives that have not been backed up.  I am trying to recover that data for him.  Any help would be appreciated.

Since I am new to the ubunto forums, I'm not sure I have even posted this is the right place.  Moderators feel free to move as long as I can find it again, LOL

---

### Post by weatherman2 on 2015-05-26
mdadm is for making a software RAID in Linux.  This won't help you at all with a Windows RAID.

Is the Windows RAID a hardware or software RAID?  Is it really RAID 0 (stripes for performance not redundancy)?  If it's a software RAID, it's probably done with dynamic disks, not something you'll have much luck with in Linux anyway.  I think you might have better luck using another Windows installation or a Windows boot disk or something.  You'll have to import the dynamic disks in the new Windows you're using.

---

### Post by jnealand on 2015-05-26
I found this post
[http://ubuntuforums.org/showthread.php?t=2259077&highlight=access+raid](http://ubuntuforums.org/showthread.php?t=2259077&highlight=access+raid)

which talks about using a tool called ldmtool, but when I try to do the apt-get install I get the message "unable to locate package ldmtool.

Got to give up for tonight, all my attempts to repair the windows installation have not worked.  I can do a factory reinstall, but it destroys the data and so I am spending a lot of time trying to access and save the data before doing a factory reinstall.  The laptop is an Acer ultrabook that comes from the factory with Raid 0 on two 128gb sata disks.

---

### Post by tgalati4 on 2015-05-26
I have seen some factory Windows installs with RAID0.  I presume this is done for performance and cost-savings, but reliability suffers.  For a typical Windows installation, disk reliability is usually not an issue, because the OS will ball itself up without any help from a failing disk.  Of course when a RAID0 does fail, you are really out of luck. 1/2 the data is striped on one disk and 1/2 is on the other.  If one disk fails, then you really do lose all of your data.

As I recall, you need to install the Intel Matrix RAID drivers in Windows to be able to read and write to the RAID pool.  There is no equivalent in linux.  You can either use hardware RAID (set up in BIOS) or mdadm.  I'm pretty sure that Matrix RAID is fakeraid, which is software-based and requires the Windows driver.

---

### Post by jnealand on 2015-05-27
This was a factory install setup that I was trying to repair for a friend.  I found a program WinToUSB that lets you install windows to a portable USB drive.  Since I had the factory DVD for Windows it had the drivers needed on it and was successful at being able to salvage the data - a huge quantity of photos, more than 55gb worth.  Once those are all copied to the external hard drive we can start a windows reinstall.  Hopefully this will teach the owner of the laptop the importance of backup.  I know I had to learn that lesson the hard way myself many years ago.  Now I have backups of my backups.  LOL

---

### Post by tgalati4 on 2015-05-28
I'm glad you got it solved.  RAID0 is really not a good idea for an OS drive, but vendors do strange things to save money.

---

