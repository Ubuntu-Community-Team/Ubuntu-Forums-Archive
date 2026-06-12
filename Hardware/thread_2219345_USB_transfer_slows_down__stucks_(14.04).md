---
title: "USB transfer slows down / stucks (14.04)"
date: 2014-04-23
forum: Hardware
---

### Post by LuigiMazzini on 2014-04-23
Hello,
I'm having problems with copying stuff on usb in Ubuntu 14.04. I think there's already a bug report but I'm not sure if that's exactly the problem I have ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/500069](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/500069)). When copying for example 1.4GB file from disk (ntfs partition, ext4 partition) to USB stick (Kingston DT101, 8GB, fat32) after app. 600MB speed starts gradually slowing from over 30MB/s to 6MB/s. It usually stucks right before end and sometimes the process finishes after 5 minutes or so. Sometimes the progress window even doesn't appear (but the nautilus icon shows that something is being copied). Any ideas?

---

### Post by sudodus on 2014-04-24
Maybe the simple truth is that the transfer of data seems fast as long as it is buffered, but the flash hardware in the pendrive is slow, maybe only 6MB/s (the speed you noticed after a while). The important thing is to have patience and let the process finish before you unplug the pendrive.

1. You can run the command

```
sync
```

from a terminal window. When sync returns to prompt, the buffered data is flushed to the target drive.

2. And remember to unmount (or eject) all partitions on the pendrive before unplugging it.

See these links about the speed of USB pendrives

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

[Link to USB 3.0 Flash Drive Speed Tests]("http://usb.userbenchmark.com/")

[Link to USB 2 and USB 3 speed tests for installers]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")

---

### Post by LuigiMazzini on 2014-04-24
Thanks for your reply.
Seems the speed is really so slow. Testing write speed (following [http://kernelreloaded.blog385.com/index.php/archives/benchmark-flash-memory-on-linux/](http://kernelreloaded.blog385.com/index.php/archives/benchmark-flash-memory-on-linux/) instructions) shows it's even slower than 6MB/s:
```
luigi@PC:~$ sudo dd if=/dev/zero of=/dev/sdb1 bs=1M count=400 skip=1000 oflag=direct[sudo] password for luigi: 
400+0 records in
400+0 records out
419430400 bytes (419 MB) copied, 86.2638 s, 4.9 MB/s
```
I'll check how fast it is in Windows to compare.
Obviously I'll have to think about new faster USB. :)

---

