---
title: "Ubuntu lost all my data when it locked up during a file move"
date: 2008-11-29
forum: General Help
---

### Post by KyferEz on 2008-11-29
I was moving over 7GB of data from one USB drive to another. The PC froze - not sure why, it's been doing it lately and I haven't had time to troubleshoot it.

In any event, it lost over half of my data. This was NOT a hard disk failure, but rather a failure of Ubuntu in some way in writing data. Both of the USB drives are NTFS, and they work fine and I've never had any trouble with them. 

Ubuntu was about half-way into the copy when the computer froze. Everything that should have been moved was gone from BOTH drives. ALL of the data that was supposedly moved to the USB drive does not appear. AND SINCE THIS WAS A MOVE OPERATION, UBUNTU, as expected, removed the data from the source drive, so all my work, DAYS of work, is gone! Poof! This should NOT have happened. At the most, the file that was in the process of copying should have been corrupted, but there should have been a copy on the source drive cause it shouldn't be removed until the move of that file is completed.

I love the Linux ideal, and really appreciate the work that goes into Ubuntu, but this is the sort of thing is intolerable, and is something that will make me quite using linux in a heartbeat. If it happens again, I don't think I will be able to recommend or use Linux again. It's simply a fundamental thing to NOT loose data on file operations. This is not an isolated case - I've done some searching and found others with the same sort of issue.

I am extremely patient with computers... But this about made me throw the ****ing monitor and has ruined my day. I just about removed Ubuntu on the spot, and I've been happily using it for over a year, until now.

---

### Post by jrharvey on 2008-11-29
That is weird that the USB card is corrupted. Ubuntu doesnt really like fixing NTFS drives when they mess up. Try opening the drive in windows if you can so it can repair the drive. Hope this helps.

---

### Post by KyferEz on 2008-11-29
WOW, I can't believe you just recommended I use Windows to fix something Linux caused. That is just wrong in every way. Linux is supposed to be more stable and secure. Well, I don't call losing my data either secure or stable. I've never, ever had data lose like this in Windows. This is a particularly large failure of Linux (or is it Ubuntu specific?) IMO.

I used windows to check the disk. It found it, but it's corrupted beyond use. D**n Ubuntu. That's a failure I will NOT put up with. I'm not using Ubuntu again until this is fixed.

---

### Post by adult swim on 2008-11-29
all may not be lost
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by KyferEz on 2008-11-29
No, it's pretty pointless. This freeze when moving happened thrice before I realized that I was actually loosing data, so I don't expect to recover much of anything. The second and third times surely overwrote large amounts of data from the first time.

It's unacceptable. Period. What's worse is that I've lost all confidence in Linux because of this. My reason for trying to move to linux was the increased productivity due to not having to worry about viruses and security holes. But that's _Worthless_ to me if the OS can't protect my files from itself. It simply wasn't worth the countless hours I devoted to learning to use and configure it when I can't trust it to successfully accomplish basic file IO operations.

*Sigh* I can understand loss due to hardware failure, but it's infuriating when it's from bugs. I really WANT to be able to get away from MS OS crap but I keep getting forced back to it :(

---

### Post by jrharvey on 2008-11-30
> **adult swim said:**
> all may not be lost
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

I think this sounds like a good idea to me. The problem is your computer crashed durring a file MOVE not COPY. In the future always copy over and then delete the un needed one when its done. Im pretty sure windows has corrupted many more disk than linux for me. Of course, I have never been in your exact situation before.

---

### Post by ajcham on 2008-11-30
I'm having the same problem with complete system freezes during large file operations - they have occurred when copying large files, installing software and while playing FM2009 in Wine.

This has only started happening in the past day or two and I suspect that it may be connected to the latest kernel update (2.6.27.9.13).  This was the most recent major change, and the problems begun soon after. Can anyone confirm this?

---

### Post by jrharvey on 2008-11-30
> *Sigh* I can understand loss due to hardware failure, but it's infuriating when it's from bugs. I really WANT to be able to get away from MS OS crap but I keep getting forced back to it 

I know it may not sound like it now but linux really is much more secure and stable than windows. I personally dont know why it would erase and corrupt your files on the source drive since all its suppose to do is read them first but oh well. I really hope someone can give a solution here. I would not reformat the drive until you know for sure its truly corrupted.

---

### Post by akudewan on 2008-11-30
> **KyferEz said:**
> WOW, I can't believe you just recommended I use Windows to fix something Linux caused.

Thats because your USB Drive is formatted in NTFS.
Read:
[http://en.wikipedia.org/wiki/NTFS#Linux](http://en.wikipedia.org/wiki/NTFS#Linux)
> 
The file system specification is a trade secret, although it can be licensed commercially from Microsoft through their Intellectual Property licensing program


ext3 would be a better option if you permanently want to move away from Windows. Unfortunately, it wouldn't work on other people's Windows machines without installing a driver.

About the topic of "linux" messing up with the file transfer - I have faced the very same problem with Windows XP and Windows Vista. I've learnt the hard way that a copy-and-then-delete operation is a lot safer than a move operation - on any OS.

This may be a bug in Linux, or maybe a hardware fault. If something like this happens, it may be a good idea to look at some log files:
/var/log/messages
/var/log/syslog
dmesg

---

### Post by jrharvey on 2008-12-02
> **akudewan said:**
> Thats because your USB Drive is formatted in NTFS.
Read:
[http://en.wikipedia.org/wiki/NTFS#Linux](http://en.wikipedia.org/wiki/NTFS#Linux)


ext3 would be a better option if you permanently want to move away from Windows. Unfortunately, it wouldn't work on other people's Windows machines without installing a driver.

About the topic of "linux" messing up with the file transfer - I have faced the very same problem with Windows XP and Windows Vista. I've learnt the hard way that a copy-and-then-delete operation is a lot safer than a move operation - on any OS.

This may be a bug in Linux, or maybe a hardware fault. If something like this happens, it may be a good idea to look at some log files:
/var/log/messages
/var/log/syslog
dmesg

I agree that this could easily have happened in windows as well. I think in the future copy and delete would be the way to go, especially knowing that your computer crashes regularly.

---

### Post by KyferEz on 2008-12-02
Thank you all for your comments. I've had some nice discussion with Szabolcs Szakacsits at bugs.launchpad.com/ubuntu/

Ubuntu doesn't use anywhere near the latest NTFS driver, so that could have contributed to the issue. I'll upgrade and see if that helps. For now, I'm not going to give up on Ubuntu yet... I will use copy operations from now on though.

Hopefully we will see some improvements soon. 

I'd also like to see an user enable-able software crc32 check option for copy and move operations where for moves the source file is not deleted until the check passes, and for copy operations the copy creates & shows a log file of any file(s) that did not pass with an option to retry those files. I'd want it always on ;)

ajcham: you may be onto something with the latest kernel causing the trouble. My lockups have started recently during vigorous HDD activity too.

I would use ext3 or fat32, but I have to have Win support of >2gb files.

Thanks all!

---

### Post by ajcham on 2008-12-03
> **KyferEz said:**
> 

ajcham: you may be onto something with the latest kernel causing the trouble. My lockups have started recently during vigorous HDD activity too.


Actually, the timing proved to be nothing more than a coincidence in my case. In another thread someone suggested running a memtest in the event of complete system freezes.  Lo and behold, it showed I had a bad memory module and since removing it I've not had any further trouble.

---

