---
title: "Advice on robust filesystem"
date: 2017-04-01
forum: Hardware
---

### Post by alechemi on 2017-04-01
Hi all.
I have a removable disk that is frequently moved between two computers. It has two partitions on it: an ext4 and a ntfs.
Due to the physical geometry of the desktop, and maybe a loosy usb port, from time to time the disk gets disconnected for a few ms. Note that for most of the time the fs is mounted, but rarely written to.

Apparentely ext4 fs is extremely vulnerable to this problem, and needs a lot of time (2+h) to restore access to the disk. I already had to fsck -b twice in a week!
Can anyone give me (informed) advice on which FS is the most robust against random disconnect during idle time?
Thank you.

---

### Post by ajgreeny on 2017-04-01
Where did you see the information that ext4 is very vulnerable to this problem?
I do not believe that it is any worse than any other filesystems, and I am amazed to hear that it takes 2h+ to restore access to a disk after such a happening.

Not the same sort of problem I accept, but when I have suffered the occasional power-outage here and my desktop system has simply shut off through no power it normally reboots when power returns without even needing to run fsck.  I think you should check the disk using the Disks application in your Ubuntu OS; it may be that you have a disk problem and it is beginning to fail.

I assume this is the same disk you asked about in your first thread at [https://ubuntuforums.org/showthread.php?t=2329611&p=13512887#post13512887](https://ubuntuforums.org/showthread.php?t=2329611&p=13512887#post13512887) which would also lead me to suspect something is wrong somewhere.

---

