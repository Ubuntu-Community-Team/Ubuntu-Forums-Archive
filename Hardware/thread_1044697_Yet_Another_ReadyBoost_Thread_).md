---
title: "Yet Another ReadyBoost Thread :)"
date: 2009-01-19
forum: Hardware
---

### Post by mwsealey on 2009-01-19
Hi,

I was just thinking (and reading a bunch of threads) on the possibility of Vista ReadyBoost-like functionality on Linux.

As far as I can see this technology or something like it may actually come in handy with the latest trend in low-end Netbook devices and with the average memory consumption of the desktops (GNOME/KDE), web browsers (Firefox, maybe Chrome soon) and office applications etc.

So I was just wondering if anyone with technical knowledge thinks it could actually be implemented. [Performance tests on Vista have shown that in a limited memory environment, it does make some difference](http://www.anandtech.com/systems/showdoc.aspx?i=2917&p=6), however the cost compared to just buying new RAM makes it more prudent to go and buy more RAM. With some laptops, memory is actually pretty darn expensive compared to an affordable SD card, so the balance may go the other way here.

In essence, ReadyBoost acts as a flash-based backup for the disk cache used in the memory management layer. On Linux, memory Linux usually marks as "cached" - check 'free -m' output to see the number, or use 'top' - and this contains disk blocks most recently used from filesystem access, swap access, and so on, so that the disk isn't hammered as much. When lots of apps are loaded, the "cached" value will drop to compensate, loading and keeping less data in the cache to give real memory up for the applications. Of course the data can always be pulled back from disk but seek times and schedulers may mean that this data is not always forthcoming as fast as it could be. It also means discarding data which may still be needed, which also has to be pulled back in at that time.

A disk seek time of 20ms can be compared to a flash seek time of less than 1ms (effectively reducing latency 20x). Of course, most flash media is far, far slower than a SATA disk, but these are also limited in portable devices to 4200 or 5400rpm drives, with low amounts of onboard disk cache compared to desktop systems. ReadyBoost on Vista also performance-tests the flash drive in question to make sure it meets a certain minimum specification, in order to actually provide a boost and not a penalty. Most high-end SDHC or ["high performance"](http://www.supermediastore.com/apacer-ht203-4gb-usb2-flashdrive.html) [or "dual channel"](http://www.ocztechnology.com/products/flash_drives/ocz_rally2_turbo_usb_2_0_flash_drive) USB 2.0 flash controllers work really well.

So imagine you have a 512MB EeePC, with a 4GB SSD or a notebook-class hard drive. Dedicating 1GB of this SSD to swap space is probably a bad idea, plus it only leaves you with 3/4 of the available storage space to store the OS and applications. You would probably be better off not using swap at all given the lifetime of these flash modules with heavy write access. In the SATA disk case, having the disk churn is probably a bad idea as the latencies are much higher on low-spindle-speed disks. 

It's also not an easy module to replace on some systems (if it's soldered to the main PCB, then definitely, but even the PCI Express module in most Netbooks would be hard to find after-market. Maybe RAM is not affordable or you simply do not feel like accidentally voiding your warranty or making a mistake. In this case, grabbing a nice fast SHDC card is a much more friendly solution.

The idea; a kernel module (or built-in) which effectively takes each entry to the space Linux calls "cached" and write it to a fixed-size file on a flash media drive. When Linux reduces the cached size to allow more programs in real memory, rather than simply discarding it, it marks it as "on the flash drive" (much the same thinking as taking a page fault and working out that it's in swap) - if that data is accessed again, it can be pulled from the flash drive back into cached, and other blocks can be swapped out (perhaps this can be done periodically like a journal flush performed by ext3 jdb).

It would also require a couple of support applications; udev rules to find this special file and use it on insertion of a USB key or SD card, and of course something that pops up (like ReadyBoost) and generally allows users to select a flash medium to use as "cache" backup.

It would not give people a ridiculously large performance boost, but it would be appreciable on systems which cannot take more than 512MB and have a reasonable speed flash controller on board (SHDC would do). What I want to know is; is this technically feasible, or is the Linux cache subsystem or VFS subsystem not ready for this kind of intrusive change?

Would it be prudent to poke around in the buffering part of the VFS to cache/buffers to Flash and see if it makes any difference at all at that point?

---

