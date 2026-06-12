---
title: "Can my harddisk be saved?"
date: 2012-04-28
forum: Hardware
---

### Post by Delodic on 2012-04-28
I have a 64 bit system with 3 harddisks. On this, I run a dual boot of ubuntu 11.10 and windows 7, each installed on their own drive. 

This morning I tried to boot windows, but after grub it told me:
[SIZE=2]
[/SIZE][INDENT][SIZE=2]A Disk Read Error Occured. Press CTRL+ALT+DEL to restart[/SIZE]

[/INDENT]So I booted ubuntu and tried to mount the disk on which windows is installed. However, it was unable to mount it and exited with code 2. 

Then I started the disk utility and noticed that the disk consisted of a large NTFS partition, but also had 22 gig free space (I believe the NTFS partition was the whole 1TB disk) Then I ran a short SMART self-test.  It says:

[INDENT] self assessment: passed
self-tests: FAILED (read)
power cycles 2160
bad sectors: 21 bad sectors
[/INDENT] 
And for the attributes of the tests many were good or N/A, but 3 turned out red:[INDENT]**1. Read Error Rate. **
Assessment: Failed in the past
normalized: 100, worst: 43, Threshold: 51, Value: 141

**5. Reallocated Sector Count**
Assessment:Warning
Normalized 100, worst 100, threshold 10, value: 13 sectors

**197. Current Pending Sector Count**
Assessment: warning
normalized 100, worst 99, threshold 0, 8 sectors
[/INDENT]I'm not sure where to go from here. What can I do to fix things (if that's even possible)?

---

### Post by Delodic on 2012-04-28
Oh, I forgot to say that I tried to Check Filesystem in the disk utility. It says 

[INDENT]**File system check on "1" (Partition 1 of ATA SAMSUNG HD103UJ) completed**
File system is **NOT** clean.
[/INDENT]

---

### Post by svennson on 2012-04-28
I have had a similar issue, and boot-repair (in ubuntu) solved it, seems grub broke my windows. (even windows cd din't recognized my hdd)

[http://ubuntuforums.org/showthread.php?t=1952550](http://ubuntuforums.org/showthread.php?t=1952550)

Might not be the solution, but worth giving a try.

---

### Post by Delodic on 2012-04-28
Hey Svennson, thanks for you reply! 

How did you start a boot-repair?

Unfortunately I think its a different problem since I'm not even able to mount it in ubuntu

---

### Post by svennson on 2012-04-28
Yes, but mine was on the same hdd, so it couldn't say my hdd din't react. Anyways here is the tutorial [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair
```

its a GUI tool :) goodluck :)

// edit

Anyways, it will generate a pastebin url, that might come in handy.

---

### Post by ahallubuntu on 2012-04-28
Sorry, boot repair can't fix failing sectors.  This is a hardware problem.

This drive probably can't be saved.  If you have just a few pending sectors, sometimes you can zearo out the entire drive (wipe it) and that will clear the pending sectors and you can use it again.  But in this case, you have 13 sectors that were already replaced (re-allocated) and 8 more that still can't be read...plus a "read error rate" in error.

If you're lucky you can save the contents of the Windows drive.  You could run the Windows chkdsk tool on this failing disk (try booting a Windows CD).  Or you might be able to copy the contents with ddrescue and perhaps run a file recover tool to extract files you  might wish to recover; most of them should be intact since you have still a relatively few failed sectors.  Once you have recovered everything, you can zero out the drive and check S.M.A.R.T. again; if there are still bad sectors, trash the drive and re-install Windows on a new drive.

---

### Post by Delodic on 2012-04-28
Thanks for your help man! 

I ran the windows dvd this afternoon and it couldn't access the drive either. It said it had no permissions to access it and the used space and total space on the drive were both 0 bytes. 

However, I could ask it to search for errors on the disk and automatically repair them. So I did this and after like 20 seconds it said it found errors and repaired them. Now I had to reboot. So I did and started the windows recovery again from the dvd. 

Now my drive had the proper size (970 gig) but it said there was nothing on the drive!? Like it was formatted. Again I ran the chkdsk and this time it took multiple hours. In ubuntu the disk still doesn't pass the self-tests though.

Anyway, is there any hope of recovering the data on my disk? There was *really* important date on it which was backed up too long ago. It seems like the disk is formatted, but I'm pretty sure I didn't get any warnings like: this may result in data loss. 

The attachment contains the two logfiles that chkdsk put on my drive. However, my operating system is Dutch, so the logfiles are Dutch too.

---

### Post by ahallubuntu on 2012-04-28
If you can actually mount the partition - even if it seems empty - that's probably good or better than unable to mount it, at least. Now you can try running a file recovery program.  In Windows, I have used one called Recuva (free - google for it), but of course you need to be running Windows to use it.  I am sure there are similar programs that will run in Linux but I'm unfamiliar with them.  Do some research.

Do you have another computer with Windows on it, that you could slave this failing disk to?  If so, I'd try running Recuva on it - and cross your fingers.  It may take a bit of trial and error and a lot of time to get the files you need off of here.

---

### Post by jmore9 on 2012-04-28
I had something similiar a couple of years ago running ubuntu.  It seemed to have screwed up my windows xp partition so nothing could access it ( they could see it but not access it).  An IT expert i know told me to bite the bullet and just reformat under windows all the affected drives with the drives manufacturs disk utilities , I had a seagate and 2 WDs at that time.

So thats what i did i reformated the one with windows and linux OS using the drives manufacturs disk utilities and put the same partition sizes back.  I then reinstalled both systems and was a happy camper again.  I always store my data on a seperate drive the one the OS's are on.

---

### Post by ahallubuntu on 2012-04-28
> **jmore9 said:**
> I had something similiar a couple of years ago running ubuntu.  It seemed to have screwed up my windows xp partition so nothing could access it ( they could see it but not access it).  An IT expert i know told me to bite the bullet and just reformat under windows all the affected drives with the drives manufacturs disk utilities , I had a seagate and 2 WDs at that time.

That's a different case from what the poster is seeing here: hardware problems.  Bad sectors.  Reformatting won't fix bad sectors that are caused by physical problems with the surface probably starting to fail.  And FYI, I've never had Ubuntu screw up any NTFS disk it's accessed - and I've used many of them over the last few years.  Never a reliability issue.


In your case, the "IT professional" should have told you to run chkdsk on your XP drive before the last resort of reformatting it and starting over...

---

### Post by oldfred on 2012-04-28
Does testdisk see the NTFS partition? With hardware failure it may not.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by Delodic on 2012-04-29
Yesterday I ran testdisk on the partition. Or actually, I ran photorec, which is in the same package but I read it was a little easier to use.   However, I might try testdisk as well, because photorec just puts all files it finds in folders without the original file name or map structure (not sure if testdisk is able to).    To give you guys some context: for my thesis I wrote some code that produced multiple gigs of experiment data. It took a lot of time to perform all these experiments. But the only way to distinguish between different experiments was by map structure and filename. So if i'm unable to recover that, I probably have to rerun the whole thing.     Anyway, many thanks for all the help and suggestions!

---

### Post by Delodic on 2012-04-29
Or I could recover the Matlab files that contain all the data processed data. But photorec didn't know these file extensions and even if it does, i think it's quite hard to identify them :(

---

### Post by oldfred on 2012-04-29
If testdisk can find files with the deeper search you may get your names & structures.

When my system had a crash I had a lot of text files. Photorec found all them, but it also found that I had saved them many times and found all the old versions and sometimes bits that were overwritten.

Photorec has scripts to recover from metadata in photos and music file names.

I now include a file name in my text files, python file names in python files I create and try to include names where possible. As  I had to grep to find a file and then run comparisons to see if I could tell the newest version. I might suggest including file names (and dates?) in files you create. Yes it is a little late to close the barn door now.

---

