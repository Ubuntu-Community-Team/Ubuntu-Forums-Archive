---
title: "Harddisk fails. /dev/hda4 cannot be mounted"
date: 2005-10-08
forum: Hardware &amp; Laptops
---

### Post by bladehaze on 2005-10-08
My computer is running ubuntu 5.04, with 2 hard disks. and my /dev/hda4 is mounted as /home

I was uploading some stuff to another computer, and then the system freezed, with the habit given by Microsoft, I rebooted the system and then the nightmare begain. When it tried to check the file-system, it gave the following error

-------------------------------------------------------------------
e2fsck 1.35 (28-Feb-2004)
e2fsck: Bad magic number in super-block while trying to open /dev/hda4
The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains an ext2 filesystem (and not ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>
------------------------------------------------------------------
Then I tried "e2fsck -b 8193 /dev/hda4", it still give me the same error message above.
Then I found this paragraph
-------------------------------------------------------------
A filesystem can be corrupted so it can't be mounted, the result of damage to
the filesystem's superblock. Any attempt to mount it will fail.
The filesystem keeps backups of the superblock.
THere are backup copies of the superblock at block offsets 8193, 16385 (8192 x
2 + 1), 24577 (8192 x 3 +1)

you can check for the size of superblocks with dumpe2fs <device> | more
if the size is different use that in the formula above.
mine is Blocks per group: 32768

you can run e2fsck using a copy of the superblock

e2fsck -f -b <offset> <device>

eg. e2fsck -f -b 16385 /dev/hda1

(taken from 'running linux' by Matt Welsh and Lar Kaufmann)
---------------------------------------------------------------
I first tried 16385 and 24577 to substitute 8193, it didn't work, and I wondered maybe because I was use ext3 and the error message is meant for ext2, they might have different size of superblocks, so I try to use

"dumpe2fs /dev/hda4 | more"

It give me the following error message

--------------------------
dumpe2fs 1.35 (28-Feb-2004)
dumpe2fs: Filesystem revision too high while trying to open /dev/hda4
Couldn't find valid filesystem superblock
--------------------------
And then I have no idea how to continue.


maybe I need some tools for ext3, or any other good tools to rescue my data? Thanks a lot for an help.

---

### Post by mlomker on 2005-10-08
> "dumpe2fs /dev/hda4 | more"


This command only works against my main partition (/) and not swap or any of my other paritions.  

I think the command has to be run against the first partition of the physical drive that the partition is on.

---

### Post by bladehaze on 2005-10-08
My # of  block per group is 8192, which means the command for e2fsck should work but it didn't, Hmmm... Any way to save my data? Thanks for the reply

---

### Post by mlomker on 2005-10-08
> My # of  block per group is 8192, which means the command for e2fsck should work but it didn't, Hmmm... Any way to save my data? Thanks for the reply

I don't see how you could if you can't mount it, but I've never had a drive failure like that.

When you said that the system froze do you mean just gnome or could you not switch to another console using Ctrl-Alt-F2?

---

### Post by bladehaze on 2005-10-08
I didn't try Ctrl-Alt-F2, but I tried Ctrl-Alt-Backspace. There are chances Ctrl-Alt-F2 works but Ctrl-Alt-Backspace does not?


Since I can still access root /. is there anyway I can check what happened at the time when the system is freezed? This is not the first time it freeze and I want to find out why.

---

### Post by mlomker on 2005-10-08
> There are chances Ctrl-Alt-F2 works but Ctrl-Alt-Backspace does not?

Yes.  Ctrl-Alt-Back is just a command to gnome or kde...if that's hung it won't respond.  

Ctrl-Alt-F2 brings you to another terminal and is listened for by another process.

> Since I can still access root /. is there anyway I can check what happened at the time when the system is freezed? This is not the first time it freeze and I want to find out why.

If root is your only partition then that's also where your logs are.  You can do a manual paritioning at setup to have separate partitions for things but it gets to be a pain guessing how much disk space you need for each.  I do that on all of my servers just for this reason...we can't afford to lose the logs.

---

### Post by bladehaze on 2005-10-08
Thanks for clearing this up. 

The disk that missed is the one with my /home folder, my / is on another disk.  

I was using ncftpput uploading some big files to another computer(an xbox) at the time when it freezed. Which log should I check to capture the behavior, how can it cause the freeze?

---

### Post by mlomker on 2005-10-08
> Which log should I check to capture the behavior, how can it cause the freeze?

The logs are in /var/log.  Look at: messages, kern.log, and syslog.  Kern.log is the first that I'd check.

---

### Post by bladehaze on 2005-10-08
I formated my /dev/hda4 and mount it again, and everything back to normal. I check the log files and it seems nothing really suspecious to me.

I uploaded some files to my xbox again and it freezed again. (not immediately, but after several Gigbytes..), and I made sure that Ctrl-Alt-F2 doesn't work. 

But This time I made the copy of the syslog, kern.log, messages before the freeze and after the freeze and reset. In the attachment is my log file that gives the difference of the 2 version of my log files. So, I guess that it is possible the reason of the freeze will be shown in these files.

could you kindly went over it and see if there is something abnormal going on? Thanks a lot.

---

### Post by mlomker on 2005-10-08
What time was the crash at?  The logs appear to be of a normal system boot-up. 

If it is crashing during a hard workout then my first thought would be heat and/or a hardware component that can't take the beating.

---

### Post by bladehaze on 2005-10-08
Mmm.. then the reason for the freeze is not there, the freeze happened like 60 mins ago? What I did is that I first tar syslog, messages, and kern.log into one file. Then I upload several gig to my xbox, and then It freeze, I reboot, and compare the log with the log I saved before. What's in the attachment is the different of these 2 files.

well, the crash happens whenever I upload some files to my xbox, it happens everytime when I upload 4-5 gig, and it happens randomly, but definitely will happen. It seems like it does not happen with the windows machine. 

What else I can do to figure out what happened?

---

### Post by mlomker on 2005-10-08
> different of these 2 files.

A difference won't help...those files are unique...errors and status info gets logged there.

> What else I can do to figure out what happened?

Hard lock-ups are almost always hardware problems.  Bad memory, CPU, network card, or simply heat.

---

