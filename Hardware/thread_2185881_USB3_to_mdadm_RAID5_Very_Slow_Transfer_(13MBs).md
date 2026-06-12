---
title: "USB3 to mdadm RAID5 Very Slow Transfer (13MB/s)"
date: 2013-11-04
forum: Hardware
---

### Post by Casey_Friday on 2013-11-04
The title says it all - I just purchased a [PCI Express USB3 card]("http://www.amazon.com/gp/product/B008716XNM/ref=as_li_ss_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=B008716XNM&linkCode=as2&tag=cbte-20") and plugged it in to my Ubuntu 12.04 headless NAS box.  I wanted to pull some files off of an HFS+ USB3 Western Digital portable 1.5 TB drive.  Here are my system specs:

**Case**: Fractal Node 304
**Motherboard**: ECS H61H2-I3
**Processor**: Intel Celeron G1610 (2.6GHz Ivy Bridge)
**RAM**: 8GB DDR3 ADATA (2 x 4GB)
**HDD**: 4 x WD Red 2TB Drives (RAID5 - mdadm)
**PSU**: HEC 350TA-2RK
**PCI-e USB3 Card**: ORICO PVU3-5O2I

I plugged my USB2 boot flash drive into the PCIe card, and the system boots fine off of the PCIe card.  (Before, I was booting from the flash drive in a USB2 port).

I tried a transfer with the WD 1.5TB portable USB3 drive plugged into the front of the case (off the 20-pin header connector) and directly into one of the 5 ports on the back of the card.  Both transfers went lazily by at about 13MB/s.  The RAID5 array works great, with write speeds of about 269 MB/s, and the read speeds looked wrong in my tests, so I'm not sure what they are.

[IMG]https://lh4.googleusercontent.com/-nUDYZSs6D0k/Ungt2BsruII/AAAAAAAAF-Y/yW7FB9h_eVo/s800/speed%2520test%2520on%2520RAID%2520array.png[/IMG]

Using cp, pv, and rsync to move a file from the USB3 drive to the RAID5 array, though, was very slow.

[IMG]https://lh3.googleusercontent.com/-lVXznmyZeGg/Ungu4vsA41I/AAAAAAAAF-0/4ptQX8H-ROM/s800/moving%2520file%2520from%2520USB3%2520to%2520RAID.png[/IMG]
[IMG]https://lh5.googleusercontent.com/-XAKrkLG9AvA/UngvKo6ywII/AAAAAAAAF_M/NDbzQrLbFXk/s800/Screen%2520Shot%25202013-11-04%2520at%25205.34.52%2520PM.png[/IMG]

Those are two separate transfers that went between 12 and 13MB/s.  I also ran a test writing from /dev/zero to the USB2 OS boot drive:

[IMG]https://lh3.googleusercontent.com/-Xr7kj5kujoQ/Ungt5YclW9I/AAAAAAAAF-g/Kh6z-PlQI8g/s800/test%2520on%2520boot%2520usb.png[/IMG]

Pretty slow writing to the USB drive, which is to be expected.

Can anyone tell me though, why my reads from a USB3 drive are so incredibly slow?  Is the USB boot drive the bottleneck here?  Do transfers go from USB3 -> boot drive (USB2) -> RAID5 array?  Or do they go directly from USB3 -> RAID5 array?

Why is this going so slow?

---

### Post by TheFu on 2013-11-04
The USB protocol doesn't compare to SATA. It's good for bulk data transfers, but lacks stuff like native command queuing and DMA operations. Most features supported by the actual hard disk can't be used when you connect it though USB.

---

### Post by Casey_Friday on 2013-11-04
I know it doesn't compare to SATA, but this is just really slow. I only posted my SATA speeds to show that my system is not messed up. This is just as slow as USB2, so I'm curious if Linux even benefits from USB3... 

I was only copying one file at a time, as you previously told me that copying multiple files at a time could cause stability issues.

---

### Post by Casey_Friday on 2013-11-04
From the reading around I've done, it appears the problem may be that the drive is formatted HFS+. I'd love to format it ext4, but then my Mac wouldn't be able to read or write to it without paid software, and I couldn't plug it into the Roku for easy playback...

---

### Post by TheFu on 2013-11-04
> **Casey_Friday said:**
> I know it doesn't compare to SATA, but this is just really slow. I only posted my SATA speeds to show that my system is not messed up. This is just as slow as USB2, so I'm curious if Linux even benefits from USB3... 

I was only copying one file at a time, as you previously told me that copying multiple files at a time could cause stability issues.

I'm positive that I never said anything about "stability issues" related to USB3.  I've had a system stop responding for about 20 seconds, but then it came back and behaved perfectly for months. It did not lockup forever and definitely did not crash.

I have multiple USB3 drives, and for bulk copies, they work as fast as expected  - limited by the disk media. My spinning disks over USB3 see 65-85MBps on write. Are you certain your drives are connected to a USB3 port on the system? I see a blue port for USB3. USB3 devices ARE backward compatible, but will be limited to USB2 speeds if connected to a USB2 port.  I don't mean to talk down, but sometimes the simple things get all of us, plus lurkers might see this later.

I haven't any clue about HFS stuff or performance. Sorry.

---

### Post by Casey_Friday on 2013-11-05
Yes, it's USB3. I still have no idea why my speeds are so slow. Is there a line of troubleshooting I can perform to find out what's causing these slow speeds?

---

### Post by TheFu on 2013-11-05
Simplify and test. Keep clear records, clear scenarios.  

Some stuff that Ive done.
* [http://blog.jdpfu.com/2011/10/17/hdd-performance-tuning-and-results](http://blog.jdpfu.com/2011/10/17/hdd-performance-tuning-and-results)
* [http://blog.jdpfu.com/2011/07/28/disk-performance-comparison-laptop-vs-desktop](http://blog.jdpfu.com/2011/07/28/disk-performance-comparison-laptop-vs-desktop)

Look at connection type, different ports, different cables, different file systems, different tuning parameters - the mdadm tuning is an art, not a science.

I find that drawing a picture helps to ensure I look at all the pieces, not just what comes to mind.

---

### Post by Casey_Friday on 2013-11-06
I'm talking about USB3 transfers, not mdadm performance. My RAID array performs fine. USB is the slow performer here. 13MB/s is WAY too slow for a USB hard drive. It should be closer to 80-90MB/s.

Any other reason I'd be getting USB2 speeds on a USB3 drive?

---

### Post by TheFu on 2013-11-07
USB2 is about 20MBps tops. That is my only guess. Somewhere in the path is a USB2 component or software with USB2 settings.

Simplify and test.

Have you tried a different USB port?  Same results?

Verified that a USB3 cable is being used?

Tried different USB devices?  Both USB2 and USB3?  Same results?

Are you certain the drivers are working at USB3?  Don't know how to check for this, but **lsusb** would be a start with an **lsmod** next. Perhaps some options are needed for the specific drivers?  Perhaps the USB3 hub only has USB2 support for Linux?  Lots of things are possible.  I know that USB3 is supported by Linux - have a few HDDs running now with great performance ... er ... for backups.

Cheap USB3 flash drives of 16-32G are relatively cheap and handy for all sorts of things. OTOH, you've probably just spent a little on USB3 for your backups, so I can understand not wanting to drop $20 more. It is an option.

Remove any USB hubs from the path too.  Have a USB3 hub here that only works at USB2 speeds for some storage ... external HDDs, of course. The device materials claim usb3 support for Linux. That machine runs 10.04, so I hope when it gets upgraded to 12.04 is gets solved.

Simplify and test.

Have you looked up the specific devices involved for Linux support? MB, USB controller, HDD enclosure, ...

Nothing specific, but hopefully this helps with some ideas.

---

### Post by Casey_Friday on 2013-11-11
I got a new Micro-B to USB3 cable; a bit heartier than the one that came with the WD drive.  Here's my output from lspci:

```
caseyfriday@fridaynode:~$ lspci | grep "USB 3"
01:00.0 USB controller: VIA Technologies, Inc. VL80x xHCI USB 3.0 Controller (rev 03)
```

Here's the result of a batch file copy of a bunch of backup files I conveniently named after a TV show:

```
caseyfriday@fridaynode:/media/usbhdd$ sudo rsync -r Weeds\ Season\ 1/ /media/raidmount/TV\ Shows
/Weeds/ --progress
sending incremental file list
Weeds S01E01.mkv
  3098315279 100%   19.04MB/s    0:02:35 (xfer#1, to-check=9/11)
Weeds S01E02.mkv
  3849810726 100%   19.15MB/s    0:03:11 (xfer#2, to-check=8/11)
Weeds S01E03.mkv
  2202549821 100%   19.26MB/s    0:01:49 (xfer#3, to-check=7/11)
Weeds S01E04.mkv
  2160051467 100%   19.05MB/s    0:01:48 (xfer#4, to-check=6/11)
Weeds S01E05.mkv
  1933675937 100%   19.06MB/s    0:01:36 (xfer#5, to-check=5/11)
Weeds S01E06.mkv
  2298626830 100%   18.59MB/s    0:01:57 (xfer#6, to-check=4/11)
Weeds S01E07.mkv
  2312976246 100%   19.08MB/s    0:01:55 (xfer#7, to-check=3/11)
Weeds S01E08.mkv
  2218166559 100%   19.24MB/s    0:01:49 (xfer#8, to-check=2/11)
Weeds S01E09.mkv
  2468883771 100%   19.14MB/s    0:02:02 (xfer#9, to-check=1/11)
Weeds S01E10.mkv
  2768097505 100%   19.13MB/s    0:02:17 (xfer#10, to-check=0/11)
```

That looks like USB2 speed to me, even though the machine knows it has a superspeed card in it.  It's faster than before by about 6MB/s, which tells me the old cable actually was a bottleneck of sorts, but it's still only maxing out at USB2 speeds.  At this point, it might be worth it for me to just upgrade my 10/100 router to a gigabit model, and get the 125MB/s max speed of that for loading content on the server.

I'm now searching for some xHCI USB 3.0 drivers that could possibly fix my problem...  I'm really at a loss here.

---

### Post by Casey_Friday on 2013-12-11
Well, I solved the problem.  It seems the PCI x1 card I got initially was not very compatible with Ubuntu.  I returned it and got [a card that comes with the NEC drivers]("http://www.amazon.com/gp/product/B00F920IYW/ref=as_li_ss_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=B00F920IYW&linkCode=as2&tag=cbte-20") (D720201), and it worked out of the box, once I plugged it in.

[IMG]https://lh4.googleusercontent.com/-YtObS4B0oiA/UqiUmnYtHjI/AAAAAAAAGNc/Xr6z91FfATw/s800/USB%2520super%2520speedy.png[/IMG]
You can see that my speeds have skyrocketed above what they were previously.  After getting the ~19 MB/s speeds, I tried hooking the drive up to a USB2 port (on the mobo), and I was getting 30 MB/s.  Much faster than the USB3 speeds, so I knew something was wrong with the card (or the drivers).  I ran an hdparm test with the new card, and I got about 110 MB/s read from a WD 1.5TB USB3 drive, which is about the max an internal SATA hard drive would get, so since my above *transfer* speeds are around 60 MB/s, I'm figuring it's my RAID array that is the limiting factor in transfer (writing) speeds.

As an added bonus, the card has 2 USB3 ports, a 20-pin USB3 header connection for my Fractal Node 304, an eSATA port, and an internal SATA port, so if I want to boot off of a small SSD in the future (versus the USB drive I'm currently booting from), I can add it in easily.

**TL;DR** - The NEC chipset works wonderfully with Ubuntu 12.04.3 LTS Server - out of the box, with no additional driver install needed.

---

