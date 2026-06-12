---
title: "Using gparted to clone a drive: errors"
date: 2016-04-10
forum: Hardware
---

### Post by jdkcarlson on 2016-04-10
I have an old MacBook that's stopped responding. Running Disk Utility in target mode asked me if I wanted to repair the disk, and then it stopped responding. I didn't repair as I was worried this could delete data I wanted to save. 

I've removed the hard drive, put in a case, and connected it to my Ubuntu computer. Files all seem to be visible in the GUI, though it has seems to problems opening both iPhone and Android photo uploads. With gparted, I've started copying this drive to a partition of an external HD. I got an error message at the beginning, but I pressed on. Now, I get warnings every 20 mb: "Input/output error during read on /dev/sdb" which I ignore because I don't want to abort and because retrying doesn't do anything. I'm at 440/476.6 GB progress now, but I don't know if it reflects things that will actually complete, and it's excruciating clicking away these error messages. Also, due to the error messages, it's not clear anything is being accomplished.

I'd really like not to lose my data; what are my options here?

---

### Post by weatherman2 on 2016-04-10
Sounds like your drive has serious issues and is probably failing.  You can verify this by installing GSmartControl in Ubuntu.

Gparted is not a good approach to try to recover files you care about most, because it doesn't copy files - it copies data in a partition.  It may copy pieces of files successfully but that's not going to help you.  If you have some specific files/folders you care about most, try to copy them first and hope some of them do copy.  Given the errors you are seeing, almost certainly the partition copy is not going to work - you'll wind up with a copy that is useless.

You can try an advanced rescue program called ddrescue.  It will copy partitions and record the failed sectors automatically and just move on to copy the good.  It has the ability to keep re-reading bad sectors over and over again to try to read them, but keep in mind this is a tedious, uncertain approach.  I would run GSmartControl first and check the Attributes for bad sectors and see how many you are dealing with.  (I'd guess hundreds from what you describe - but who knows?)  Running S.M.A.R.T. tests probably won't do much besides fail so look at the Attributes.

Do some web searching on ddrescue if you want to explore it.  Start here:

[https://wiki.gentoo.org/wiki/Ddrescue](https://wiki.gentoo.org/wiki/Ddrescue)

---

### Post by Bucky Ball on 2016-04-10
There is also [Clonezilla]("http://clonezilla.org/") and [fsarchiver]("http://www.fsarchiver.org/Main_Page"). Clonezilla is my tool of choice. 

If the hard drive is failing badly, though, all may be lost as it won't cope with the reading of data from it.

---

### Post by jdkcarlson on 2016-04-10
This is what I was worried might be happening. The copying has stalled at 446.91 of 464.76 and isn't throwing errors anymore, just chilling there. I take it I should just cancel this process in order to follow the other steps? I know enough to know trying to mount and read the disk right now would be a major mistake.

---

### Post by Bucky Ball on 2016-04-10
Yes. You can clone the partition then work on the cloned partition to get the files off from a decent hard drive.

---

### Post by jdkcarlson on 2016-04-10
It's asking me if I want to force-cancel and warning this could cause MASSIVE damage. There's nothing I have to lose on the target drive but I'm worried about the source drive. Will force cancelling a copy also put that data at further risk?

New error!: "Error fsyncing/closing /dev/sdc: Input/output error"
Options are retry or ignore

Edit!: Okay, it cancelled finally. I'm trying to manually copy folders that are important but I get an error: permission denied. How can I grant myself permission to copy things before they're lost?

---

### Post by Bucky Ball on 2016-04-10
How are you trying to copy things? You should NOT be running an install directly from that drive. Boot to a live session using install media ('Try Ubuntu') and copy the files/folders to an external drive that way is the safest for what you're attempting. Cloning the partition and working on that from a live session is also an option, as mentioned.

Either way, think of getting those files off as if you've got one shot at it. We can't assume the partition/drive will last over multiple attempts. Live session and copy/paste to external drive or clone partition then see if they're retrievable.

---

### Post by jdkcarlson on 2016-04-10
Not sure I understand what you mean by "live session." I have the following: 

1. Ubuntu machine in no danger
2. Mac internal hard drive mounted as external through USB, with problems
3. external HD to back stuff up onto, which shows up as healthy under smartcheck.

I've logged in as root in Nautilus and am manually copying folders off failing Mac internal HD as fast as I can; this fixed most of the permission issues I was having with copying, but permission to write all image files seems to be denied.

> sudo chown ME /dev/sdb

does not give me control of drive 2, the Mac Drive, and now that I've repartitioned the external (blank) HD in gparted to hfs+, I don't have permission to write on it either.

**What can I put in the terminal to get all permissions on these two drives?**

I'm trying to figure out what SMART tests to do and will post them if that would help.

I don't know how to modify permissions to write to the external hard drive partition. I have been trying to follow this

[http://askubuntu.com/questions/332315/how-to-read-and-write-hfs-journaled-external-hdd-in-ubuntu-without-access-to-os](http://askubuntu.com/questions/332315/how-to-read-and-write-hfs-journaled-external-hdd-in-ubuntu-without-access-to-os)

but get this error:

> mount: mount point /media/mntpoint does not exist

Other note: The logo next to the hfs+ partition from the Mac HD I've been trying to save has changed from a red exclamation point to a key in gparted. Here are the errors I get in gparted every time devices are refreshed:

> "end of file while reading No such file or directory"

"The backup GPT table is corrupt, but the primary appears OK, so that will be used."

"The journal is not empty.  Parted must replay the transactions before opening the file system.  This will modify the file system."

I've been responding to these respectively with Ignore, OK, and Cancel. I was worried Fixing the journaling would destroy data.
Thank you for your help.

---

### Post by weatherman2 on 2016-04-10
Don't bother running any S.M.A.R.T. tests now - just check the stored Attributes to see what the current state of the drive is.   GSmartControl will highlight Attributes it thinks are problems in red or pink.  If you aren't running the graphical version, you can use the terminal version, the command "smartctl," like this:

```

sudo smartctl -a /dev/sdb

```

(Replace "/dev/sdb" with the device ID of your drive, whatever it is.)

Or to filter out sector attributes:

```

sudo smartctl -a /dev/sdb | grep -i sector

```

(Sometimes you must add extra arguments to this command to get S.M.A.R.T. info from USB.  You can try adding the options "-T permissive" and/or "-d sat" if smartctl itself returns nothing.)

The other poster wasn't sure whether you were running FROM this drive, but it seems to me you are not.  A "live" session is just one booted from a CD or USB stick that completely goes away once you power off.  An Ubuntu installation on a hard drive keeps state like any other installed operating system after you boot up again.

---

### Post by jdkcarlson on 2016-04-10
Yes, it seemed like the other poster thought I was booting off the damaged disk.

Your code wanted a -d option as predicted; I put "-d sat".

[http://pastebin.ubuntu.com/15748180/](http://pastebin.ubuntu.com/15748180/)

Your other code yielded this (when I added "-d sat"; before, it just gave me a new prompt):

[http://pastebin.ubuntu.com/15748231/](http://pastebin.ubuntu.com/15748231/)

I don't think this looks good. I'd like to copy all my important stuff manually and then clone the drive, but 1. I don't seem to be able to get permissions to do so on either external HD and 2. I didn't understand the Clonezilla instructions, which I **think** assume I'm booting off the same drive I'm trying to clone. 3. Is it **safer to disconnect** this drive after every step of the process so it doesn't get worn out, **or leave it running** so it doesn't have to start and stop as much**?**

Thank you again.

---

### Post by weatherman2 on 2016-04-10
Clonezilla is something you would boot off of a live disc (CD or USB).  But I probably wouldn't even think about cloning the partition at this point and trying to boot from it (cloned to a new drive) again.  Getting most of your files off may be your best hope.  I'd plan on not being able to clone it and needing to replace the hard drive and re-install Mac OS (or Linux) from scratch on the new drive.

The other suggestion was to use ddrescue to make a copy of the partition in question as an image to another disk; it will log the error sectors that cannot be read on the first pass, so it's really a better tool than Clonezilla for this.  I think you can tell ddrescue to go back and try to re-read the missing sectors over and over again and hope they can eventually be read, once it has already copied off the "good" sectors.  I have heard of cases where a few days later it managed to copy the bad sectors.  You do have 152 bad ("pending") sectors at this point, which is pretty bad though I've seen worse.  They may not all be in files or in files you care about.  It could be only a few files will be lost.

I'd probably do it all at once shot not just keep stopping and starting.  Some people claim success with the "freezer" trick (put your drive in a freezer for a while, in a plastic bag that keeps the moisture out) because a cooler drive is more likely to work better, but I've never had success with that personally.  Do some web searching on "hard drive freezer" and you should get a bunch of results, if you are so inclined.

---

### Post by jdkcarlson on 2016-04-10
The freezer option doesn't appeal. I would like to copy a bunch of files, then use ddrescue, but I can't get permissions working. It says the drive, an hfs+ partition, is opened as read-only, and I haven't been able to get it to open otherwise. Moving files, even as root in Nautilus, results in claims of inadequate permission. The files are visibly right there but I can't I'd really rather do that first, as I understand ddrescue can take days and I don't know that my drive has days of life left in it.

I've attempted to follow this advice

[http://askubuntu.com/questions/175739/how-do-i-remount-a-filesystem-as-read-write](http://askubuntu.com/questions/175739/how-do-i-remount-a-filesystem-as-read-write)

but when i do

> sudo mount -t hfsplus -o rw,remount -force /dev/sdb3 /media/untitled

the data doesn't reappear. It doesn't give an error but neither does it mount. Mounting from the GUI, on the other hand, is easy, but I can't access the files. **What can I do to get at my files? Would it be worth asking in a new thread?**

Would ddrescue result in something "as good" I could write to a nondefective drive and try to boot if I so chose?

P.S.: I've started ddrescuing. Here's what it looks like so far:

```
GNU ddrescue 1.17
Press Ctrl-C to interrupt
rescued:   347258 kB,  errsize:    336 MB,  current rate:        0 B/s
   ipos:   683335 kB,   errors:      37,    average rate:    1102 kB/s
   opos:   683335 kB,    time since last successful read:      14 s
Copying non-tried blocks...
```

Other questions: what do you think of gparted's persistent request I fix the journaling? Will that destroy things?

---

### Post by weatherman2 on 2016-04-10
OK - I should ask: what are you trying to copy TO?  Another Mac HFS+ disk?  Yes, in that case, you will have trouble mounting the destination as write-able in Ubuntu.  I suspect it is possible but I have never gotten it to work.  (One issue: with each new version of Ubuntu, some tutorial that was written a year or two ago for an older version of Ubuntu may no longer work.)

(And to clarify terminology: you should be "copying" files not trying to "move" them.  There is a difference.  "Move" means erase from the source after you are done, and that involves write privileges.  But if you are just dragging folders in Nautilus you'd be copying.)

My suggestion: if you want to read your files later onto another Mac, create a new Linux ext2 (yes, ext2, not ext3 or ext4) partition on some other disk.  Mount that, then copy your files to it from this failing Mac disk.  My understanding is that Mac OS can read ext2 partitions (with some sort of add-on) but has trouble with ext4.  Anyway, as long as you can copy them off now, at least you have a copy of them SOMEWHERE.

I wouldn't mess with disabling the journaling of your HFS+ volume.  Leave it alone.  You should be able to read files off of it without write privileges.

You can google around for tutorials on ddrescue.  I suspect you will have other issues later due to HFS+ though. I would personally try to get the file copy working first.  ddrescue involves a whole lot more work and may not necessarily get you any further in saving your files.

---

### Post by jdkcarlson on 2016-04-11
I was trying to copy them to an external HD formatted in HFS+ as well because I thought that would be easier somehow, but I can stop. The same problems, however, happen when I try to copy some files to the desktop of my Ubuntu machine; it says they're read-only. This only happens for some files and not others; I was able to copy a block of files but with important exceptions that I had to skip, including my archived email.

You're right that I'm trying to copy files but that dragging them has seemed to have the effect of copying them, when it was successful. It wasn't successful for a number of files I cared about, including almost all downloaded pictures from a phone I no longer have. That is to say, **I am not currently able to copy these files**. I was dragging them from within Nautilus on Ubuntu 14.04, if that makes this any more sensible. I was repeatedly told the drive was read-only even though I thought I was only reading.

Below is my current ddrescue status. I did want to rescue my files first manually but didn't know how, and I'm hesitant to stop this process. Do you think the image will be readable or are there too many errors?

```
Press Ctrl-C to interrupt
rescued:   146122 MB,  errsize:   2245 MB,  current rate:   80281 kB/s
   ipos:   148367 MB,   errors:    1010,    average rate:   12864 kB/s
   opos:   148367 MB,    time since last successful read:       0 s
Copying non-tried blocks...
```

---

### Post by weatherman2 on 2016-04-11
I'm sorry, I have very limited experience with HFS+ disks in Linux.  I have accessed them (read-only) but not on a failing disk.  The drag-and-drop with Nautilus sounds like the right approach.  I don't know why you would get errors about the original being read-only.

You might see what happens if you copy via the command line in a terminal.  Something like this:

```
rsync -av  /media/USERNAME/MACPartition/Users/YourName/Pictures /SOME/DESTINATION/FOLDER | tee /tmp/errorlog
```

I think rsync will continue on if it can't copy a bad file.  The error log would give you a record of which files couldn't be copied.  And if you have to quit and restart, it will skip files already copied.

---

### Post by jdkcarlson on 2016-04-11
Thanks, will try. Still waiting for ddrescue though. Report is now thus:

```
GNU ddrescue 1.17
Press Ctrl-C to interrupt
rescued:   498037 MB,  errsize:   1076 MB,  current rate:     1024 B/s
   ipos:     3694 MB,   errors:    1783,    average rate:   12543 kB/s
   opos:     3694 MB,    time since last successful read:       0 s
Splitting failed blocks... 

```

Progress has gotten much slower now. Do you know if ddrescue is itself damaging the disk further at this point? I've read there's a way to resume the process if halted, but doubt it's possible to do that if I mount the drive in between, right?

---

### Post by jdkcarlson on 2016-04-11
Things have gotten much slower. Should I be worried?

```
rescued:   498042 MB,  errsize:   1071 MB,  current rate:        0 B/s
   ipos:    23962 MB,   errors:    3748,    average rate:    5725 kB/s
   opos:    23962 MB,    time since last successful read:    10.6 m
Splitting failed blocks...
```

**Update**: Crap.

```
rescued:   498043 MB,  errsize:   1070 MB,  current rate:        0 B/s
   ipos:    29096 MB,   errors:    3863,    average rate:    5088 kB/s
   opos:    29096 MB,    time since last successful read:      24 s
Splitting failed blocks... ^[[D^[[D^[[D^[[D^[[D^[[D^[[D^[[D^[[D^[[D^[[D^[[D^[[D^[[D^[[D^[[D
ddrescue: input file disappeared: No such file or directory
```

**What should I do now?** I think the computer moved slightly, but the drive is still plugged in as far as it goes. The drive is still legible; it just mounted when I clicked the disk in the dock to see if it was okay (if that word isn't too generous for my situation ...).

**Update update**: rsync report:

```
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1183) [sender=3.1.0]
sent 67 bytes  received 20 bytes  174.00 bytes/sec
total size is 0  speedup is 0.00

```

**Update update update**: I'm having some success hunting in the terminal and doing sudo cp! It's getting most but not all files. What should I do to try to get the damaged ones back? In particular, nothing from Thunderbird seems to be recoverable, although I might have it backed up somewhere else.

---

### Post by jdkcarlson on 2016-04-12
Okay, so here are my questions:

1. What should I do with regard to the ddparted backup? It stopped claiming the media had disappeared. I have a logfile but don't know how to use it.

2. What can I do about specific important-to-me folders that wouldn't copy, e.g., all of Thunderbird.

3. There are a number of image files that won't open despite showing no input/output error in the terminal during copy (many show such errors, too). I get "Could not open image. Failed to open input stream for file." What can I do about getting these open?

---

### Post by weatherman2 on 2016-04-12
You're going to have to start to accept that you won't get some of your files back - unless you want to send your failed drive off to a forensics company that specializes in data recovery and pay a bit of money.  For most of us, it would not be worth it.

This is why it's crucial to make backups.  Unfortunately, sometimes we have to learn this the hard way: hard drives fail, and when they do, you lose files.  I had to learn the lesson that way, having lost files more than once after hard drive failures.  That's why I not only make backups, I have backups of my backups.  The last few times I bought 4TB archive or backup drives, I bought two of each and make one a copy of the other that is offline most of the time but occasionally synced.  (Some people choose to RAID them to protect against hard drive failure - two drives always synced up - but hard drive failure isn't the only threat to your data, and there are benefits to having one drive unplugged most of the time.)

At least you are getting SOME of your files back, right?  The first time I experienced hard drive failure, I lost EVERYTHING.

---

### Post by jdkcarlson on 2016-04-12
I've accepted this and got most of what I wanted, which is a relief, but not all, so I'm going to keep trying to get the most possible. Is trying ddrescue again my best option here to try and save Thunderbird? Various things offer to repair partition tables or remove journaling; should I take them up on this offer?

I'd been making Time Machine backups but the last was in January and apparently they never saved Thunderbird; when I navigate it in Ubuntu, these are files named Thunderbird where these folders should be but they're of size 0 B. I don't know if that has something to do with the "layered snapshot" system and an initial backup being missing. I installed Thunderbird in September to download mail from an account that was being deleted. 

The images that won't open and didn't give errors during transfer also won't open on an earlier Mac Time Machine backup on a disk that seems to check out fine, so I think that must not be a damage issue and I might ask it somewhere else if Google doesn't help.

---

### Post by weatherman2 on 2016-04-13
I don't know if your best bet is to try to repair the partition table or remove journaling - I doubt it will matter, honestly.  You might try an Apple forum.  I really don't know much about HFS+ volumes.

If your Time Machine versions are also corrupt, it's possible that disk had been messed up for a while...

---

### Post by jdkcarlson on 2016-04-15
I guess I'll never know how long the disk had been messed up.

New problem: I've been ddrescuing more every once in a while, but I have to disconnect and move the computer often. Last time I did this, I put the drives back in, checked what was what with gparted, resumed with the same img and logfile, and noticed it was getting a LOT more data than usual. Then it stopped because it said the partition was full. This was strange, because I'd calculated how large that partition needed to be, but I resolved to resize my partition. Then gparted refreshed the device list, which it had not done before, apparently, and it turned out the reason departed had been so unexpectedly successful was because it had been copying not from my sad old Mac drive, but from the same partition it was writing the img file in.

Is there a way to rewind this complete idiocy somehow or have I just made this backup completely worthless?

---

