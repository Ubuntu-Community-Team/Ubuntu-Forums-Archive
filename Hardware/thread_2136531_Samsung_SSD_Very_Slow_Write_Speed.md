---
title: "Samsung SSD Very Slow Write Speed"
date: 2013-04-17
forum: Hardware
---

### Post by jephthai on 2013-04-17
I did a bunch of Googling, and couldn't find anything -- my apologies if this is answered somewhere else.  

I just did a fresh install (12.04 LTS) on a new box with a Samsung SSD.  I do have AHCI enabled, etc. -- all of the tips I can find anywhere else.  My read speed is great.  But my write speed is unbearably slow.  Here's an example:

```
# dd count=30 bs=1M if=/dev/zero of=/root/foo.img
30+0 records in
30+0 records out
31457280 bytes (31 MB) copied, 26.9415 s, 1.2 MB/s

```

I've set up my fstab according to the various guides:

```
UUID=XX-YY-ZZ-AA     /               ext4    discard,noatime,nodiratime,errors=remount-ro 0       1
```

One megabyte per second is killing me!  Updates take forever.  I want to install a regular hard drive so it will be FASTER.

---

### Post by pqwoerituytrueiwoq on 2013-04-17
try running this, this is the command for manual trim
[FONT=courier new]sudo fstrim -v /[/FONT]
is the ssd used? how old it is? firmware update?
try increasing the over provisioning (can be done my leaved part of the drive unformated, but requires a secure erase or untouched drive, some samung firmware allows you to alter the over provisioning)
edit could you post your fstab file

---

### Post by jephthai on 2013-04-17
It is a new drive, right out of the box.  I did an fstrim -v, and there was no change in performance.  Based on what I'm reading online, this isn't just a few-percent issue.  I am 10s or 100s of times slower than I should be.  It takes almost 10 minutes just to finish "reading package lists" to install a new package.

---

### Post by pqwoerituytrueiwoq on 2013-04-17
check for a firmware update
gsmartcontrol can show you the firmware version
what about your fstab file?
there was a [FONT=courier new]**/**[/FONT] at the end of that command

which IO scheduler are you using? i dont think 12.04 uses deadline out of the box

did it takes ages to install the OS? if not try it without using discard and using fstrim
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

---

### Post by jephthai on 2013-04-18
I did include the "/" at the end of the command.  It did take a long time to install the OS -- I was thinking it was a slow source flash drive, but evidently that is not the case.  I have already tried without discard (that was the default).  

I've tried everything I've seen on the various "how to improve performance of your SSD" pages.  I really believe this is not about tuning -- it is an error somewhere.  I'm concerned that there may be a driver problem, etc.  I was hoping that I could get information from the forum that would be something I couldn't find with Google.

Do you really think that the IO scheduler could make a difference of 100x?

---

### Post by jephthai on 2013-04-18
For completeness, I just tested all three available schedulers.  Right now, I'm hoping it's a kernel thing, so I'm updating to 12.10.  If that doesn't work, I'll move to Gentoo so I can mess with kernel stuff more easily.

---

### Post by pqwoerituytrueiwoq on 2013-04-18
defiantly not that much, i would suggest secure erasing the ssd and leaving 7-21% unformatted (for maximum performance) when you setup your partitions
if your Over Provisioning is literally near 0 that would cause write speeds to the horrible, if that does not work I would RMA that drive
i do know that on at least some Samsung SSDs they give you software to adjust the Over Provisioning, Over Provisioning trades capacity for write speed

I am using 13.04 on my SSD, it is a boot drive meaning it also works with a mechanical HDD, i recored my installation process
[https://www.youtube.com/watch?v=2sPGEwqoXA0](https://www.youtube.com/watch?v=2sPGEwqoXA0)

---

### Post by jephthai on 2013-04-18
Thanks for your input.  I have completed a long upgrade to 12.10, and that has not made any improvement.  I did some more research on my motherboard -- it's a Gigabyte 970A-UD3.  There is a "beta" BIOS update with a newer AHCI implementation.  Unfortunately, I have no windows from which to install the update.  I thought maybe I will try to disable AHCI and see if my performance changes at all.  It won't be as fast as it could, theoretically be, but could still be much faster than it is now.  We'll see.

---

### Post by jephthai on 2013-04-18
I installed a BIOS update, and there is no change.  Now it's off to Gentoo, hoping that a newer kernel may work better.

---

### Post by pqwoerituytrueiwoq on 2013-04-18
you could try a mainline kernel
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-rc6-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-rc6-raring/)
you need 4 files
the one ending in all.deb
and the 3 for your architecture (i386=32bit and amd64=64bit)

most likely the ssd is defective
have you checked the smart data using [gsmartcontrol](apt:gsmartcontrol)?

---

### Post by jephthai on 2013-04-18
The Gentoo liveCD didn't work either.  I tested a standard SATA hard drive, and the spindle drive was just as slow.  I spoke with Gigabyte, and they think it's a driver problem.  I will be refunding the motherboard.  I am now looking for one that is known to be compatible with Linux drivers

---

### Post by pqwoerituytrueiwoq on 2013-04-18
what CPU socket, form factor, and budget
you did have the drive connected to one of the 1st stats ports right and not on a second controller
my board has a couple JMicron ports that are not as fast as my other ports

---

### Post by jephthai on 2013-04-18
I tried several ports for the only controller on the board.  I need an AM3+ to work with the FX-8350.  I was looking at the ASUS Sabertooth 990FX.  I have two coworkers who have this board, and they have been successful.

---

