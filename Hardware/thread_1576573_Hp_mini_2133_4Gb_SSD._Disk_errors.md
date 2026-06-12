---
title: "Hp mini 2133 4Gb SSD. Disk errors?"
date: 2010-09-17
forum: Hardware
---

### Post by matthekc on 2010-09-17
Sorry in advance for the small essay.

A little backstory...
I've got a customer in our PC repair shop that has an Hp mini 2133 with Suse 10.1.
When she came in the machine would not boot to GUI it was full and could not start a GDM session. I cleared out her /tmp and the machine booted fine.  I looked at her Suse 10.1 which was 2 years out of support and filling the tiny SSD and suggested a change to something smaller.

The current problem.
I'm have put Linux Mint Xfce on it twice and twice I have eventually had the following start-up problem.
The error says:
errors found while checking the disk for /

I have used Disk Utility to check for smart errors but it says the drive is healthy.
I'd like to fsck from a live usb, but I can't get /dev/sdb1 to umount.

If the disk is bad and I can prove it then I will suggest a new disk or maybe an SD card install as a workaround.  If the disk isn't bad then what is my issue?

What tests should I run, is there a good live usb diagnostic I could use?

---

### Post by dougalkerr on 2010-09-17
TheeMahn over at Ultimate Edition Linux has been playing with writing operating system to SSD for a while now and says he wouldn't go back to the old mechanical drives. maybe he or one of his good buddies could point you in the right direction.

Look into the Ultimate Edition forums here;
[http://forumubuntusoftware.info/index.php?sid=559377a9cc41fd3e18c91635442d54c3](http://forumubuntusoftware.info/index.php?sid=559377a9cc41fd3e18c91635442d54c3)

---

### Post by matthekc on 2010-09-17
All right I will try that if I don't get an answer here soon.

---

### Post by matthekc on 2010-09-17
Okay I made a thread over at Ultimate Edition here is a link.

[http://forumubuntusoftware.info/viewtopic.php?f=18&t=5133](http://forumubuntusoftware.info/viewtopic.php?f=18&t=5133)

---

### Post by matthekc on 2010-09-17
Does it look like a hardware failure?

---

### Post by matthekc on 2010-09-17
Could it be a file system choice issue maybe Ext2 will work better?
I'm going to try Ext2 because I've got nothing to lose and everything to gain.

I've got to get going soon I will pick this up on Monday.

---

### Post by matthekc on 2010-09-20
I read somewhere to try EXT2 on this SSD drive. So I did that at the end of the day on Friday now that seems to be working for me. Any ideas why?

---

