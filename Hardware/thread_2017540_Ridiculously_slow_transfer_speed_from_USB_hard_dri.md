---
title: "Ridiculously slow transfer speed from USB hard drive"
date: 2012-07-05
forum: Hardware
---

### Post by BavidDowman on 2012-07-05
Hi,
I have a Western Digital MyPassport hard drive which I was using with Ubuntu  Lucid for several months. The drive is formatted with ext3/ext4. I have to transfer the data on this drive (around 700 Gigs of it) to my new computer (running Ubuntu Precise). The problems is that since the past 3-4 days I am getting transfer speeds  around 200-500 KB/s.
The port is usb-2.0 and he disk has usb-3.0 capability.

The problem is definitely with the HDD since changing the target machine and/or the usb port does not improve these rates. In fact, a different ntfs USB HDD gives a very healthy 30 MBps on the same system. 

Since I had reformatted the disk in question to ext4, I doubt if the manufacturer will help me. Is there a way to check what might be wrong with the disk? The data on this is very important and I will not like to lose it.

---

### Post by ahallubuntu on 2012-07-05
In Ubuntu, you can use SmartMonTools or the graphic interface called GSmartControl to check the S.M.A.R.T. status of a hard drive.  Unfortuantely, sometimes S.M.A.R.T. doesn't automatically work with external USB drives.  You may have to add an option like -d sat or -T permissive to the smartctl command (the command used by GSmartControl to get S.M.A.R.T. status).

Here is some more info about smartctl options.

[http://sourceforge.net/apps/trac/smartmontools/wiki/Supported_USB-Devices](http://sourceforge.net/apps/trac/smartmontools/wiki/Supported_USB-Devices)

Still, if I were you, I would backup my files off this drive ASAP to some other device, no matter how long it takes. Hard drives fail all the time sometimes gradually, sometimes without warning.  It's very reckless to keep only one copy of important data on one hard drive; people lose everything on their drives all the time when drives fail.  If data is important, you need at least two hard drives for reliable backup.  (Online is possible but challenging for such a large amount of data.)

---

### Post by BavidDowman on 2012-07-05
@ahallubuntu: Thanks, I am looking into it... It might be quicker to generate the data again than wait for the 600 hours it will take for the transfer :D

Meanwhile, I also found that writing to the HDD still occurs at normal speeds (several MB/s). it is only the reading  and copying that is slow. 
Another thing that might be relevant: a few days ago I accidentally  deleted a really large directory on the disk (thankfully, I restored it immediately from the trash). While I have access to all data on the disk, could this have led to fragmentation of any kind? I am not too familiar with the ext filesystem to know any better.

---

### Post by ahallubuntu on 2012-07-05
I did have a weird case recently with Ubuntu 10.04 on one particular computer where an external USB drive would read really slowly (5MBps which I know is a lot faster than what you see) but write much faster, like 20Mbps.  It turned out to be something to do with the USB driver in the kernel for the USB controller on the motherboard; every drive did the same thing but on another computer it worked fine.

But you said you've tried this drive on different computers and it is slow to read on all of them - right?

---

### Post by BavidDowman on 2012-07-05
Yeah, it is the disk that is slow. 

I have attached the report from the SMARTctl program. Indeed there is  a read failure on this disk, although I am not sure how serious. I am moving data as fast as I can, while it is still accessible. However, the transfer rate, miraculously,  has increased to 30 MBps in the last few minutes :shock:.
I think smartctl has given me the much-needed scare. I'll dump this disk anyway.

---

### Post by kurt18947 on 2012-07-05
I have write speed issue with an enclosure.  It starts out gangbusters but rather quickly drops to 1.2 Mb./sec. -- USB 1.1 speed :frown:.  The enclosure is a $4.99 wonder from Amazon with a 60 GB. SATA drive so maybe I got what I paid for.  I do have an Accomdata PATA/SATA  3.5" enclosure with a PATA drive which will write 28-30 Mb./sec all day long.

---

### Post by ahallubuntu on 2012-07-05
There are no bad sectors showing in that report, which is good.  The read failure occurred a long time ago - at lifetime 2049 hours.  The Conveyance offline test failed 90% of the way through.  But you're now at 6376 hours powered on, probably some months ago since the test failed.

Perhaps some other tool ran that test - or did you buy this drive used?

There could still be an issue, of course.  Maybe you were getting slow read due to part of the surface in better shape than the rest and some files were hard to read correctly.  Or...as you said, maybe just a fragmentation issue with the filesystem or something.  Better safe than sorry.

Even if you get a new disk, you'd be very wise to have two copies of anything important, on separate disks.  I always buy shadow disks for all my backup drives now.

> **BavidDowman said:**
> Yeah, it is the disk that is slow. 

I have attached the report from the SMARTctl program. Indeed there is  a read failure on this disk, although I am not sure how serious. I am moving data as fast as I can, while it is still accessible. However, the transfer rate, miraculously,  has increased to 30 MBps in the last few minutes :shock:.
I think smartctl has given me the much-needed scare. I'll dump this disk anyway.

---

### Post by stateroom on 2012-07-14
I had slow 10MB transfer speeds to a USB drive (and sata to sata) on a newer 3 core Athlon system with an AMD SB710 6 port sata/ide/usb controller chip.  The problem was slow sata reading speed.  I was able to get consistently 30MB or greater speeds by disabling the onboard IDE controller which had an ATAPI dvd attached.  I have no idea whether it is a linux or firmware problem.

---

