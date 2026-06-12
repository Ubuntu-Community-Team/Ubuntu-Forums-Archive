---
title: "[SOLVED] Dual boot wiped out hard drive.  HELP!!"
date: 2007-10-23
forum: Hardware &amp; Laptops
---

### Post by stitcher06 on 2007-10-23
I recently installed ubuntu 7.10 on a laptop that had vista.  I was hoping for the dual boot configuration so highly talked about.  I made a wrong choice somewhere and allowed ubuntu to wipe the hard drive and install itself as the sole operating system.  I have tried to re-boot vista using my recovery cd's without success.  My computer company states that since I changed operating systems the warranty is void.  Is there any way to wipe ubuntu off and get back to vista to try again?  Thanks.:(

---

### Post by jualin on 2007-10-23
I am sorry to hear that!, You could format your partition so that you have a blank hard drive, but to install vista again you will need a Vista Installation Disc. If you deleted the partition containing Vista I think that there is no way of recovering. During the Ubuntu Installation you should have select the option of "Install Ubuntu in the free space", probably you selected the option of use entire disk or something similar. About the computer warranty, I do not think that changing operating systems will make the warranty void. The warranty is not for the Operating System, is for the hardware of your computer. Try to get a Vista Installation Disc, and then after installing Vista try to install Ubuntu again.

---

### Post by rogirwin on 2007-10-23
Boot Ubuntu and log into a terminal.
Type this: cat /proc/partitions

The result will look like this:

major minor  #blocks  name

   8     0  117220824 sda
   8     1  114214086 sda1
   8     2          1 sda2
   8     5    3004123 sda5

As you can see 100% of my drive is linux (sda1)

If your vista system has survived then it will be on another partition. You should be able to mount this partition and see files that belong to vista.

sudo mount /dev/sdxx /mnt 
ls -l /mnt

What do you see when doing this?

---

### Post by stitcher06 on 2007-10-24
Thank you both for your help.  Forgive me, but I'm as green as they come in ubuntu/linux.  I do remember choosing the option to allow ubuntu to use the whole drive when installing, a grave error on my part.  Thankfully it's a backup computer, but I really need the windows side of things for our business.  What I see when I tried your suggestions rogirwin is this:

8  0  78150744 sda
8  1  75521533 sda1
8  2                1 sda2
8  5   2626596  sda5

I didn't go any further than this.  To my green eyes, it looks as though I completely wiped out vista's partition (correct me if I'm wrong.)  This isn't a big deal as I had everything backed up on our main system, but I really need to get vista back on.  I do have the dvd's I burned as recovery discs and all apps & drivers, but it won't re-install vista when re-booted at this point.  Do I need to format the hard drive and start over at this point?  Will the vista recovery discs boot without any operating system on the computer at all?  I welcome all suggestions.  I'd love to get to the place where I can utilize the dual-boot configuration I've heard so much about, but I really need the vista back in place ahead of everything.  Thank you!!!!!

---

### Post by Ryangarve on 2007-10-24
Unforutuanlly your recovery cd's lose their purpose if you format your entire hard drive.  The way a recovery cd works is it activates a recovery partition on your hard drive and if you partition is wiped than it won't come back.  Also, while reading a condensed eula you did void your warranty, so you really only have the choice of buying a new copy of vista.

---

