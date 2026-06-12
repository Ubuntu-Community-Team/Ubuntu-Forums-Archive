---
title: "External USB HD's unmount at unexpected times"
date: 2009-03-01
forum: Hardware
---

### Post by pilpi on 2009-03-01
Hi,

Running Ubuntu 8.04 Hardy on an IBM Thinkpad T41 Type 2373-4FG. I have a faint memory that there were updates this weekend, which I promptly installed. This evening my USB2 hard drives - two of them - started getting unmounted at unexpected times. 

That is, after 20 minutes or so after being mounted, while running an rsync-based backup script, I start getting errors like: 
rsync: writefd_unbuffered failed to write 4 bytes [sender]: Broken pipe (32)
rsync: write failed on "/media/[...]/p1160244.jpg": Read-only file system (30)
rsync error: error in file IO (code 11) at receiver.c(259) [receiver=2.6.9]
rsync: connection unexpectedly closed (69968 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(454) [sender=2.6.9]
 

After this, subsequent mounting commands state that the device is not found. As this happens with two different external USB HD's, either the hardware related to the USB ports just broke today, or Ubuntu did. I have no other OS to test this on.

I would like my backups back as soon as possible, so any ideas? Thanks
Olli

---

### Post by pilpi on 2009-03-03
There are also other issues with 8.04 Hardy LTS, and I would like to upgrade. Maybe I will wait for 9.04, but I will not be capable of doing that, either, unless I get this fixed, since I have no way to do my backups.

Any thoughts, anyone?

---

### Post by Cybie257 on 2009-03-03
Try using the Live CD as 'another OS to test with'. If it was working before updates, I would make the assumption that the Live CD version would give you a good indication of where the problem might be occuring.

-Cybie

---

### Post by pilpi on 2009-03-03
Thanks, I'll try that as soon as I find my/a liveCD. 

Pauli Borodulin replied to this on facebook, answering his questions here.

The drives are connected directly to the PC, no USB hub. One of the hard drives is a previous version of iomega ego ( [http://go.iomega.com/section?SID=fed72e3568e27aa5bb18686b38eca14bda2:4760&secid=76813](http://go.iomega.com/section?SID=fed72e3568e27aa5bb18686b38eca14bda2:4760&secid=76813) ) and gets its power from USB , the other one is a standard 3,5" drive with a casing and requires a separate power cord.

It seems that if I just let the HD be, it tries to remount again and then again fails, causing the HD to be mounted multiple times.

dmesg output when this happens: [http://rafb.net/p/WO1cjG11.html]("http://rafb.net/p/WO1cjG11.html")
further output, continuing from previous (mounts, falls, mounts, falls, without me doing anything): 
[http://rafb.net/p/iXKbdy29.html](http://rafb.net/p/iXKbdy29.html)

---

### Post by pilpi on 2009-03-03
Trying 2.6.24-19-generic kernel, still broken, though it doesn't happen that often now (maybe coincidence) ... [http://rafb.net/p/ekRqqg63.html](http://rafb.net/p/ekRqqg63.html)

---

### Post by pilpi on 2009-03-04
Tried liveCD for kubuntu 7.04. The problem is still there, so I guess the USB controller is broken. Hm, wonder if I could get a cheap PCMCIA usb controller somewhere, cos I really would not want to buy a new laptop... thanks for the help!

---

