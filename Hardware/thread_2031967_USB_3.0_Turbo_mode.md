---
title: "USB 3.0 Turbo mode"
date: 2012-07-22
forum: Hardware
---

### Post by vishnumrao on 2012-07-22
I read an interesting [article]("http://www.tomshardware.com/reviews/usb-3-uas-turbo,3215.html") at tomshardware regarding USB 3.0 performance.


I myself had been wondering why I could not get more than the 120-140 MB/s speed on my [TR4UTBPN]("http://www.sansdigital.com/towerraid-plus/tr4utbpn.html"), which has 4x2TB drives in a RAID5.

Sansdigital provides a Windows only utility called USB 3.0 Turbo boost, which I belive does the same thing that this article talks about: 

"The maximum transaction size for bulk-only transfers (BOT) at the operating system level is 64 KB. However, sequential data is typically moved in 128 KB blocks, requiring two BOT transactions. What's being referred to as "Turbo mode" overcomes that limitation by increasing the maximum transfer size to 1 MB or larger, allowing the USB driver to pack several 128 KB sequential requests into one larger transaction. Fewer small transactions means less wait, ready, and acknowledge USB commands, in turn reducing the amount of bandwidth consumed by signal overhead"

The article also talks about UASP, something I don't think my hardware is capable of. But I am very interested in enabling Turbo Mode. 

Three reasons I am interested. I am thinking of getting a USB 3.0 external case and putting in an SSD to use as an external storage. Two, the article says there is about 25%$ increase in speeds on USB 2.0 standard drives. Three, I could use some speed increase on the TR4UTBPN. A RAID5 of mechanical drives should definitely be possible of transfers greater than 120MB/s.

So question is: How do I enable USB 3.0 Turbo mode in Ubuntu. I looked up on the web. Did not get too many answers for enabling on Linux.

---

### Post by neoalex on 2012-12-14
I have the exact same enclosure connected to an Ubuntu server.
Based on the article you mentioned Turbo mode is achieved by "increasing the maximum transfer size to 1 MB or larger, allowing the USB driver to pack several 128 KB sequential requests into one larger transaction". I did a little bit more research and found this can easily be achieved in linux without any 3rd party tools. See the blog below (while he doesn't talk about USB 3.0 the concept is the same).

[http://marc-abramowitz.com/archives/2007/02/17/getting-good-performance-out-of-usb-hard-drives-in-linux/](http://marc-abramowitz.com/archives/2007/02/17/getting-good-performance-out-of-usb-hard-drives-in-linux/)

I set my block size to 2048 which according to the link below is 1 MB

[http://www.linux-usb.org/FAQ.html#i5](http://www.linux-usb.org/FAQ.html#i5)

I tried higher values but haven't seen any better performance. See the before and after test results below:

root@HomeServer:~# echo 240 > /sys/block/sda/device/max_sectors
root@HomeServer:~# hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   15562 MB in  2.00 seconds = 7789.54 MB/sec
 Timing buffered disk reads: 384 MB in  3.00 seconds = 127.84 MB/sec
root@HomeServer:~# echo 2048 > /sys/block/sda/device/max_sectors
root@HomeServer:~# hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   15676 MB in  2.00 seconds = 7846.82 MB/sec
 Timing buffered disk reads: 460 MB in  3.01 seconds = 152.77 MB/sec
root@HomeServer:~#

---

