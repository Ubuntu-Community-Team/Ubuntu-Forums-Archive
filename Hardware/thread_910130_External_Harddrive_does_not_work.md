---
title: "External Harddrive does not work"
date: 2008-09-04
forum: Hardware
---

### Post by lusion on 2008-09-04
I have a seagate 500gb external harddrive and it use to work for my windows but i just switched to ubuntu yesterday and it will not open, i always get the error "Unable to mount the volume FreeAgent Drive":confused:

---

### Post by secretspicy15 on 2008-09-06
I'm working on the same problem. I have had it working in the past, I just have to figure out what I'm doing wrong. I'll be sure to let you know what I find :-)

---

### Post by secretspicy15 on 2008-09-06
Alrighty! I found a solution that worked for me, so hopefully it will work for you too!
Allow me to quote from [http://ubuntuforums.org/showthread.php?t=900682]("http://ubuntuforums.org/showthread.php?t=900682") post number 5 (thanks eggdeng!):
> 
First, just make sure the device is identified as /dev/sdb1 using
Code:

sudo fdisk -l

Copy and paste to avoid typos.
Now run
Code:

sudo apt-get install ntfsprogs

which will install a program which includes a repair utility. Run the utility (assuming the drive is sdb1)
Code:

sudo ntfsfix /dev/sdb1

With luck, this will repair and mount the drive.

Then restart your computer and your FreeAgent Drive should be mounted, and easily accessible from your desktop.

Hope it works for you like it did for me!!

TJ

---

### Post by geoffpl on 2008-09-10
This worked great for me - thanks!!!

---

