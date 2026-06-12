---
title: "CD/DVD drive lost on HP laptop"
date: 2009-06-09
forum: Hardware
---

### Post by J-Morris on 2009-06-09
I have a long running problem: My CD/DVD drive doesn't work, and also my USB CD/DVD drive doesn't work. In my Disk & Filesystems panel in System Settings, it lists my CD/DVD drive as mount point: /media/cdrom0, type: auto, device: /dev/

It is also disabled. When I click "enable" I get the error message: 

"An error occured while enabling /media/cdrom0.

The system reported: mount: /dev is not a block device. 

What does this mean and how can I fix it? Thanks!

---

### Post by 2rB on 2009-11-03
Hi I had the same problem.
Not to experienced in Linux - but after some surfing on the net I kinda understood that this may be related to a scsi / sata issue.

I installed "scsiadd" from the repository, and after a reboot everything seem to be working.
(had done some other things before installing this so might not be the correct solution)

---

### Post by J-Morris on 2009-11-03
Actually, the problem turned out to be a hardware failure on the part of HP. A certain series of HP Pavilion lap-tops are prone to overheating and melting the insides of the computer resulting in CD drive failure, wireless failure, and eventually monitor failure. Check the serial number on your computer.

---

