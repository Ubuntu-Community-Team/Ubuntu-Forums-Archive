---
title: "Ubuntu is destroying partition tables for Windows machines?!"
date: 2008-08-22
forum: Hardware
---

### Post by fogster74 on 2008-08-22
Hi all,

I have a bit of an odd situation and this seems similar to the following (unsolved) post: [http://ubuntuforums.org/showthread.php?t=857036](http://ubuntuforums.org/showthread.php?t=857036) (I'll point a link in that thread to this..)

I have a laptop with a large (500GB) internal hard drive; this was partitioned to include a partition for Vista (NTFS), a partition for Ubuntu (EXT3) and a 'data' partition (NTFS). This was a new build on a new laptop with Hardy Heron 8.04; previous laptop worked perfectly like this and I was able to share data between Vista and Ubuntu by writing to the DATA partition (D: drive in Windows).

I booted into Vista a few weeks ago and, on booting, windows stated it needed to ru checkdisk on D: and this reported no errors. On logging into windows, found that the 'D: drive', although visible, was no longer accessible (message 'Drive not accessible') but, on booting into Ubuntu, get message 'disk needs to be checked for consistency'... completes, get into ubuntu and it can access/ read it all perfectly. Weird....?

It get weirder..! 

I also have an external hard drive (500GB). Two partitions, one NTFS, the other FAT32. Accessible perfectly well between Windows and Ubuntu - but no longer. Ubuntu can see both perfectly, read, write no problems. Attach the drive when booted into Vista (or XP on my second laptop) and same result - 'The drive has malfunctioned' and the drive is inaccessible.

So I reformat the FAT32 partition in Vista - it's fine. Reboot into Vista, still fine. Drop a test text file into it - no problem. Reboot again into Vista - still works fine. Disconnect the drive, boot into Vista, connect the drive - perfect. Reboot into Ubuntu, open the test text file, make a change, save the change to the drive, shut down Ubuntu. Reboot into Vista - drive no longer accessible. Same behaviour regardless of whether I access a FAT32 or NTFS partition - once Ubuntu has had a touch, Windows can no longer access the drive. Most frustrating!

Any ideas on what on earth is going on???! I've trawled the forums but am no closer to finding a resolution...

---

### Post by omns on 2008-08-22
> **fogster74 said:**
> Any ideas on what on earth is going on???!.

Egads, Vista is a nightmare. Nuke it or install XP

---

### Post by CTRLurself on 2008-08-22
> **GrantG said:**
> Egads, Vista is a nightmare. Nuke it or install XP

That was completely useless, OP even said they tried it on an XP box, but had the same problem. Next time read the whole post before responding, and remember all OS's have their flaws, but they all have their strengths too... Let's see XP not BSOD when your graphics card crashes.

As for the OP, I have run into this problem a few times on my HP laptop. It's actually (from what I've found) an Ubuntu problem. I just re-installed Ubuntu, and got it fully updated before I tried to access another hard drive, and it's always worked. Be sure to NEVER hibernate Windows, and then boot into Ubuntu because it's what caused this problem for me in the past (And also Windows doesn't react well to this at all).

What I did was boot windows, delete the ubuntu partition completely (leave it unallocated), reboot with ANY windows _vista_ DVD (the actual DVD, not restore discs) in the drive, click on repair, then select command prompt and type in

bootrec.exe /fixboot

then

bootrec.exe /fixmbr

*This gets GRUB off your computer (which will prevent you from rebooting after editing your partition tables)*

Close command prompt, reboot. Boot windows again, make your Ubuntu partition any size you want, and then shut down windows, and boot off of the Live disc, and install normal.

Hope this helps.

---

### Post by fogster74 on 2008-08-22
> **CTRLurself said:**
> Be sure to NEVER hibernate Windows

Awesome quick reply - I have the strangest feeling you have hit the nail on the head - this may well have started after I used hibernation in Windows and then booted into Ubuntu without thinking (doh!).

I'll post again to let you know how I get on... may be a couple of days as obviously I have an Ubuntu install to look forward too... :-o

Really pleased to have received such a quick response ... many thanks!!

---

### Post by omns on 2008-08-23
> **CTRLurself said:**
> and remember all OS's have their flaws, but they all have their strengths too...

yada yada yada. I feel appropriately chastised...

---

### Post by CTRLurself on 2008-08-23
> **fogster74 said:**
> I have an Ubuntu install to look forward too... :-o


I've been trying to figure something out on my laptop, and have installed ubuntu 8 times in the past 2 days (three different versions)... It's not as hard as you'd think to brick an Ubuntu install's cooperation with other OS's and vice-versa.

I keep on running into disk permission problems trying to swap files between OS's.

---

### Post by fogster74 on 2008-08-23
> What I did was boot windows, delete the ubuntu partition completely (leave it unallocated)

How did you / would you suggest I delete the partition within Vista? I have an old version of Partition Magic but that does not work in Vista. Would booting off an Ubuntu Live CD and using partition editor on that to delete the partition have the same effect?

Also - I can see that this could solve the problem with my internal data partition through playing with the MBR - but how will I solve the problem of my external drive that is not readable on any XP or Vista machine now that Ubuntu has had a little taste...?

---

### Post by CTRLurself on 2008-08-24
> **fogster74 said:**
> How did you / would you suggest I delete the partition within Vista? I have an old version of Partition Magic but that does not work in Vista. Would booting off an Ubuntu Live CD and using partition editor on that to delete the partition have the same effect?

Also - I can see that this could solve the problem with my internal data partition through playing with the MBR - but how will I solve the problem of my external drive that is not readable on any XP or Vista machine now that Ubuntu has had a little taste...?

1 - boot windows
2 - open the start menu and search "manage"
3 - computer management will be one of the only results
4 - go to storage in the left menu tray
5 - right click the partition you want to delete and select delete
6 - repeat for all partitions you want to delete
7 - when you go to reboot you'll need to remove GRUB otherwise you'll get a GRUB 22 error (meaning the partitions have changed and it doesn't know what to do anymore)

at this point you either need to boot off a vista disk and go into "repair" and then "command prompt" and do the "*bootrec.exe /fixmbr*" and "*bootrec.exe /fixboot*" or immediately reboot off your live cd and re-install (which will reinstall GRUB with the new partition data).

I just did this using the second (just reinstall ubuntu) method to repair all my drive permission problems

hope this helps

---

### Post by CTRLurself on 2008-08-26
> **fogster74 said:**
> Also - I can see that this could solve the problem with my internal data partition through playing with the MBR - but how will I solve the problem of my external drive that is not readable on any XP or Vista machine now that Ubuntu has had a little taste...?

sorry, I missed this question originally...

1 - boot up ubuntu (live CD or installed doesn't matter)
2 - plug in the external drive
3 - click on the "places" menu and select "computer" from the list.
4 - double click on the one that is your window's partition, and then do the same and make sure that the external drive is mounted as well
5 - dig through the external drive, and copy-paste the files you want from the external to your window's hard drive. Put them someplace obvious, so you can quickly dump them back to the external drive.

Hopefully you'll have enough space to temporarily copy it all, if not it'll be up to you to perform a bit of triage.

6 - restart into windows double check that the files from the external drive are where you put them.
7 - open up computer management, click storage, and right click the external drive and reformat it to NTFS. If you'd like, make multiple partitions so you can use part of it for external storage for ubuntu and part for windows.

ENJOY!!!

reformatting it is just about the only way to get it back... if Window's doesn't see the drive at all, then instead of using computer management to reformat it,

in ubuntu install GParted (sudo apt-get install gparted) and run it... it'll be under system->administration->partition editor in the top menu. click the drop down in the top corner and select the external drive, reformat it.

and hopefully it'll recognize in windows now.

---

### Post by CTRLurself on 2008-08-26
Sorry, I forgot to ask a few things (may solve your problem in a less drastic manner)

the first thing to try, that has worked for me before is unplug it from everything (computers, power, everything) let it set for a few minutes. Come back, plug in power, plug into a computer with ubuntu running, right-click and unmount it. test it on your window's machine.

---

### Post by fogster74 on 2008-11-12
Sorry for not replying - this is now solved :-)

I did exactly as you said, reinstalled Ubuntu and it all just came back... the disk is now fully readable in XP and Vista again....

Many thanks guys - a great result!

PS I didn't need to go as far as formatting the external drive (which would have been a nightmare as it was 500GB and pretty full...!

---

### Post by h4mx0r on 2008-11-12
bootloader malware infected through vista, maybe partition editing/imaging, or some other trajedy? What do you think caused it?

---

### Post by CTRLurself on 2009-03-31
> **h4mx0r said:**
> bootloader malware infected through vista, maybe partition editing/imaging, or some other trajedy? What do you think caused it?

Sorry for bumping an otherwise dead topic, but I think I've found the root cause of the OP's error for the external drive. I've met quite a few people who work between OS's who have this problem.

Boot ubuntu, open up gParted, plug in the drive, force it to mount. it'll say it can't mount, hit ignore, it will mount anyways. Once mounted, just right click on the drive on your desktop now, and hit Unmount.

What it is, is actually pretty odd... On rare occasion when the OS (whichever it may be) shuts down, it doesn't always properly close the session on the drive (equivalent to an improper unmount, but it won't generate the same error). So simply forcing a mount (which Ubuntu is the most successful at) and then properly unmounting it fixes the session error.

NOTE: If the GParted method doesn't work, there is a terminal command for force mounting a drive that can be found from a quick google search... but personally, I've only had 1 drive out of about 20 that GParted wasn't able to force mount. And this has _practically_ no threat to your data's integrity just because this isn't really touching the data on the drive.

---

### Post by QWERTY99 on 2009-10-21
> **CTRLurself said:**
> Sorry for bumping an otherwise dead topic, but I think I've found the root cause of the OP's error for the external drive. I've met quite a few people who work between OS's who have this problem.

Boot ubuntu, open up gParted, plug in the drive, force it to mount. it'll say it can't mount, hit ignore, it will mount anyways. Once mounted, just right click on the drive on your desktop now, and hit Unmount.

What it is, is actually pretty odd... On rare occasion when the OS (whichever it may be) shuts down, it doesn't always properly close the session on the drive (equivalent to an improper unmount, but it won't generate the same error). So simply forcing a mount (which Ubuntu is the most successful at) and then properly unmounting it fixes the session error.

NOTE: If the GParted method doesn't work, there is a terminal command for force mounting a drive that can be found from a quick google search... but personally, I've only had 1 drive out of about 20 that GParted wasn't able to force mount. And this has _practically_ no threat to your data's integrity just because this isn't really touching the data on the drive.

sorry for bringing up an old thread, but I also have this problem, but the solution with Gparted doesn't work for me.

I have a 1 TB WD External HDD
When I've unplugged it from ubuntu 9.04 [forgot to unmount] and plugged in my Windows7 [differnet PC] it says that 

W:\ is not accessible  The file or directory is corrupted and unreadable.

Then it asks to Format the drive, please help me...

---

