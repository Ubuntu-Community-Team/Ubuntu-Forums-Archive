---
title: "unable to detect file system gparted"
date: 2012-06-27
forum: Hardware
---

### Post by anbydare on 2012-06-27
I'm new to Linux. So I have absolutely no idea on what to do with this. I just got a new laptop computer, an ASUS N53SM-ES72 which came with Windows 7.  I decided it was time to learn Linux, and naturally I chose Ubuntu 12.04 lts.  
So I installed it as a dual boot with windows 7.  Everything appears to be working just fine, and I can switch back and forth between Ubuntu and Windows. But some feeling was telling me to make sure everything was alright and I installed Gparted to make sure. Attached is a screenshot of what I found.
 It appears that the, roughly 45gb, partition I created for Ubuntu has been partially corrupted. I right clicked /dev/sda6 to properties and it says Warning unable to detect file system! and it lists a few vague possible reasons why.  Like I said, everything is working, but there seems to be corrupted partition of 16 gb that I would like to heal.

Again, I am completely new to the Linux community and I'm not the most tech savy, but I'd appreciate any ideas or suggestions. I hope you guys don't treat me like I'm stupid.

---

### Post by oldfred on 2012-06-27
Did you create a large swap? And did you encrypt /home? If so that is normal. Swap is also encrypted so nothing including gparted can see it.

---

### Post by anbydare on 2012-06-28
> **oldfred said:**
> Did you create a large swap? And did you encrypt /home? If so that is normal. Swap is also encrypted so nothing including gparted can see it.

Thank you very much for responding. 
yes I chose to encrypt /home during the ubuntu installation. If i recall correctly I created a partition about 45 gb for all of ubuntu.  But for the swap, I don't remember choosing it's size.

So i guess that /home is in the partition /dev/sda6.  So that is relieving. But now i'm led to a few more questions.

how can I figure out how much space is left in /home if it's encrypted?
Is it safe to allocate more space for /home in the future? and how?
and how do i know the size of my swap? and what are the preferable sizes?

thanks again. i was scared for a little while.

-andy

---

### Post by oldfred on 2012-06-28
You can see sizes of used mounted partitions with this:

df -H

I do not use encryption, but once you have given password on booting, it should show just like without encryption.

Swap used to be 2X RAM when RAM was 256K or 512K. When RAM got to 2GB then it was 1X RAM so you could hibernate. Actually math should be in GiB not GB so you have enough if you want to hibernate. If you have lots of RAM you may not need much or any swap but supposedly systems run better with at least some swap so I often suggest 2GB as a minimum or RAM size.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Some also use swap files:
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

Resizing your encrypted file system can not be done directly as of yet with Gparted as Gparted sees the encrypted partitions as unformatted space.
How to: Resize an Encrypted Partition (LUKS)
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)
How to Resize a LUKS Encrypted File System.
[http://ubuntuforums.org/showthread.php?t=726724](http://ubuntuforums.org/showthread.php?t=726724)

Since there is no way to recover data from encrypted systems, you do need a very good backup plan.

discussion of alternatives/strategy:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

