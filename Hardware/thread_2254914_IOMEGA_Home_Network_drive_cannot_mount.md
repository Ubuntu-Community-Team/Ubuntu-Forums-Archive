---
title: "IOMEGA Home Network drive cannot mount"
date: 2014-11-30
forum: Hardware
---

### Post by anastasios2 on 2014-11-30
Hi all

I have had issues with my IOMEGA Home Network drive. I have read that the way to recover your data is to hook it up as an external drive in an ubuntu machine. I have connected it using the sabrent SATA to usb cable and when I connect it to my computer, the ubuntu OS is trying to mount the volumes. It sees 2 volumes. It keeps trying and i get two messages:

[LIST]
[*]For the first volume, I get: Unable to mount 996GB Filesystem. Error mounting: mount: No data available (that is where my data is located)
[*]For the second volume in the drive, I get: Error mountin dev/sdb2 (I assume the one previously mentioned is sdb1)
[/LIST]

My problem is that once they fail, I cannot force them to mount so I can attempt a repair. Any thoughts how to approach this?  I am attaching a zip with 2 files, the output of dmesg and the output of sudo lsusb -v

I also found a forum a post that describes exactly my problem: [http://www.tomshardware.com/forum/266110-32-recovering-data-dead-iomega-networked-media-storage](http://www.tomshardware.com/forum/266110-32-recovering-data-dead-iomega-networked-media-storage) (see 2 before the last posting by Storage Anonymous ). That can provide additional context

thanks in advance for any help
-a

---

