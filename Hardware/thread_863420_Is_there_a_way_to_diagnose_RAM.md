---
title: "Is there a way to diagnose RAM?"
date: 2008-07-18
forum: Hardware
---

### Post by sp0nge on 2008-07-18
Frustration has gotten the better of me! 

I have been working to resurrect an old Toshiba Sattelite laptop for months now. After several attempts to wipe the hard drive and start from scratch, I found no success. 

I popped a hard drive out of an old dell I own and with minor exceptions, it worked. I was able to access the files on the hard drive but the GUI wasn't working.  That led me to diagnose the issue to be a bad hard drive. I ordered a new one and upon installing I get: 

```
Intel(R) Boot Agent Version 3.0.03
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting Intel PXE ROM
Insert system disk in drive.
Press any key to continue.
```

The disk is in the drive and I'm positive it works. Now I'm wondering if the RAM may be bad thus the Live CD is not able to run? Is there some way I can diagnose this for certain?

---

### Post by damis648 on 2008-07-18
Run the RAM test from the LiveCD. It's in the menu when you boot up the CD.

---

### Post by sp0nge on 2008-07-18
Thats part of the problem. The Live CD wont start up. I get the TOSHIBA start up screen, but can't get the disk to load the Ubuntu Startup menu. The drive is spinning, trying to work, but I still get the error every time.

---

### Post by damis648 on 2008-07-18
> **sp0nge said:**
> Thats part of the problem. The Live CD wont start up. I get the TOSHIBA start up screen, but can't get the disk to load the Ubuntu Startup menu. The drive is spinning, trying to work, but I still get the error every time.

Sorry, I misread your post. According to your message, there is a problem with the boot media. Either the disc is bad or the CD drive is bad.

---

### Post by sp0nge on 2008-07-18
Thanks for the input! 

The disk is working. I have used it on several different machines and have had no issues. The CD Drive could be the problem. I don't even have Linux on a floppy anymore.. is it worth trying or should I scrap this machine? Is there a way to diagnose the CD Rom for sure?

---

### Post by damis648 on 2008-07-18
> **sp0nge said:**
> Thanks for the input! 

The disk is working. I have used it on several different machines and have had no issues. The CD Drive could be the problem. I don't even have Linux on a floppy anymore.. is it worth trying or should I scrap this machine? Is there a way to diagnose the CD Rom for sure?

If you can. try putting the drive in another machine and see if it works in that machine, or try putting another drive in the "broken" machine and see if it works then.

---

### Post by evets25 on 2008-07-18
you probably need to tell your computer to boot from the CD by setting this in the bios. This is slightly different with every computer, but usually you hit f12 or delete as the computer is starting, and then you will get into the BIOS. From there, figure out how to change the startup order so that it will try booting from the CD. This has nothing to do with your ram, 

About your error message, the first three lines are your computer trying to boot over the network, which it obviously fails to do. So next, it goes on to the next device, the hard drive. The last two lines are there because it tries to boot from the hard drive, but since it's a new hard drive there's no operating system to boot. (duh.)

You need to get it to actually boot from the CD, which can be set in the BIOS.(see above)

---

### Post by sp0nge on 2008-07-18
Thank you. 

The first thing I did when beginning the project was to change the boot order.

---

