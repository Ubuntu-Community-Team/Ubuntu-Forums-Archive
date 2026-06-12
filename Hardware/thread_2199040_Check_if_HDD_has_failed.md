---
title: "Check if HDD has failed"
date: 2014-01-11
forum: Hardware
---

### Post by Shadius on 2014-01-11
Hey everyone! 

I need to know if an HDD has failed.  This HDD has Windows on it, but whenever I try to boot from it, I get a BSoD error.  What can I use from Linux to test the HDD?  The BSoD error I get is 0x0000007B (0xBA4C3524, 0x0000034, 0x00000000, 0x00000000).  I've Googled the error, but haven't found any solutions.  Any help is appreciated!

---

### Post by Shadius on 2014-01-11
Hellllllllllllp please!!

---

### Post by QIII on 2014-01-11
Please wait 24 hours before bumping a thread.

---

### Post by Shadius on 2014-01-11
> **QIII said:**
> Please wait 24 hours before bumping a thread.

Oh, sorry. :( You can delete this and the previous post I made.

---

### Post by tgalati4 on 2014-01-11
You can check the SMART parameters of the disk.  Create an Ubuntu Live USB and boot from it.  Use the Disk Utility and check the hard drive status.  Search the web for any error codes that you find.  There are so many things that can cause a BSoD, that it's hard to troubleshoot.  The fact that you couldn't find any codes through google tells you that you probably have some random failure that could either be software or hardware related, though more likely hardware, since software errors tend to show up more consistently.

---

### Post by Shadius on 2014-01-11
> **tgalati4 said:**
> You can check the SMART parameters of the disk.  Create an Ubuntu Live USB and boot from it.  Use the Disk Utility and check the hard drive status.  Search the web for any error codes that you find.  There are so many things that can cause a BSoD, that it's hard to troubleshoot.  The fact that you couldn't find any codes through google tells you that you probably have some random failure that could either be software or hardware related, though more likely hardware, since software errors tend to show up more consistently.

Thank you for replying. So I used Disk Utility to check the hard disk drive's status and it says the drive passed and is healthy, but that can't be true because I can't boot from it. I get the BSoD error. I can mount the drive in Linux and view the files. The error also told me to run CHKDSK /f from Windows. Is there a way I can use Linux to do that or is there a Linux equivalent?

---

### Post by houstonbofh on 2014-01-12
The disk may be fine, but files on it may be corrupt.  This can be caused by mallware, or a hard reboot while writing.  However, it could also be bad ram in the computer.  Start with running memtest to make sure the ram is good.  Then do a repair install of Windows, or just reinstall it.

---

### Post by Shadius on 2014-01-12
> **houstonbofh said:**
> The disk may be fine, but files on it may be corrupt.  This can be caused by mallware, or a hard reboot while writing.  However, it could also be bad ram in the computer.  Start with running memtest to make sure the ram is good.  Then do a repair install of Windows, or just reinstall it.

I had tried to use the Windows CD to do a repair, but when I inserted the CD the setup started and just stopped and gave me the BSoD again. I'll try running the memtest. Oh, I forgot, I'm also not getting any video signal from the computer's VGA port. That's why I decided to plug the hard disk drive on my Linux computer and check it out there. So I wouldn't be able to run the memtest on that PC. I don't really know what I can do now.

---

### Post by Shadius on 2014-01-12
I was wondering if I could use this HDD as an HDD to just drop files on? Like music, pictures, etc. Is this a possible? Bad idea, good idea?

---

### Post by houstonbofh on 2014-01-13
Yes.  You can use it for whatever you want.  Sounds like your computer died, and this part is fine.

---

### Post by Shadius on 2014-01-25
**Update**

I've fixed the problem! I went into my UEFI and changed my SATA mode to IDE mode. That allowed the drive to load without the BSoD. The HDD is fine and I'm able to log into Windows. 

Another problem I'm facing is that I can't tell if my VGA port is working on the original computer the HDD came from. I don't get any video signal. I've checked the cable with another computer and it works fine so the cable isn't in question. I have no idea what could be the problem except maybe the VGA port on the motherboard is bad, but how do I find out for sure? Some guidance would be appreciated with this issue.

---

