---
title: "Hard drive failure"
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by kay0d on 2009-02-08
I recently migrated from Windows to Ubuntu - unintentionally, I must confess. All I wanted to do was try out Ubuntu. I burned the ISO to a flash disk, and ran Ubuntu. I was very pleased with all the eye-candy, so, I decided to install it. At first, the partition manager, GPartEd, didn't detect my Windows partitions at all. I rebooted. It recognized the partitions this time. I had a total of five partitions: C, D, E, F, G. I decided to format G, whose size was 12 GB, and install Ubuntu there. I deleted the "G", marked it, and continued to the next step, but before proceeding, it said that I haven't chosen or created any swap area and I may encounter problems during install. I went back to the previous step, broke that 12 GB into two parts: 10 GB and 2 GB, and I marked that 2 GB as the swap space. A few "Forwards" later, my system froze during the installation process at around 37% and I got the error message that either my drive needs replacement or I should move my system to a cooler area. Now my drive isn't that old. I bought this laptop just six months ago and I didn't do much with it, defragmented it regularly, etc. Anyway, I tried to click here and there, but the computer didn't respond, and after a while, even the mouse didn't move. That's when I knew something is terribly wrong. I waited for almost 20 minutes for my system to recover, but it did not. I cut the power and restarted the system... and behold! 

NO OPERATING SYSTEM FOUND.

No Windows, no Ubuntu.. Nothing. All gone to hell.

I tried to boot from Flash Disk again, but right before that bar is supposed to become all full of orange color and Ubuntu should start, I'd get an error. The terrible black screen and some error message would continue to repeat after an interval of around 1.5 seconds. Alright, maybe 2 seconds. Anyway, I had loads of important data in my drive (and of course I didn't have a backup) so I rushed to get some recovery tools.
I tried to install Windows again, hoping that I might be able to repair it, but windows installer didn't detect any windows at all. There was just this one big free space of 160 GB. All C, D, E, F & G were gone. I booted using a Windows 98 CD and tried "fdisk", but it didn't detect anything. I consulted a geek friend of mine, and he said that my "Zero sector has gone bad". Now I have no idea what that means. I tried using SpinRite or something like that, but nothing worked. I tried using Hard Drive Regenerator, some software I found in that recovery CD, and it kept finding bad sectors.. It seemed as if every sector on my hard drive is bad. The process would have taken years, because it fixed only 400 bad sectors in an hour.

I took the hard disk to some stupid computer shop, and the guy tried using "fdisk" with Windows 98 CD, and he told me the same thing that my zero sector has freaked out and the drive is 'probably' irreparable. He said he can try and the process will take 7 - 8 hours, and if the drive works, he still cannot guarantee that for how long the drive will work in future. Hopeless! I had important work to do, so I bought a new hard drive and installed Ubuntu.

I was wondering if anything can be done about all the data in that hard drive. It's like... ALL MY LIFE'S WORK! I feel like committing suicide. Just kidding! :( 

Oh, and by the way, my Ubuntu is now running very slow. I just have one big 160 GB partition and that's all. I was so afraid to click any other option while partitioning this time, so I just clicked "Forward... Forward... Forward". Might this be due to one large single partition?

I have:
Acer 5570z
1.73 GHZ Dual Core
1 GB of RAM
160 GB HDD

Thank you.

---

### Post by Pumalite on 2009-02-08
Boot your Live CD and post from the Terminal:
```
sudo fdisk -lu
```

---

### Post by kay0d on 2009-03-10
Well, the problem is: I **cannot** boot from the Live CD. When I try to boot from it, it gives an error message which keeps on repeating after short intervals. I cannot say what the message is, because I'm not using that hard drive any more.

---

### Post by Ericyzfr1 on 2009-03-10
You could try to get an adaptor case for HD laptop and plug it as a USB drive to see if it is recognized.

---

