---
title: "Can't mount CD with Marvell SATA Controller"
date: 2024-05-29
forum: Hardware
---

### Post by hakelm on 2024-05-29
I increased the number of disks and therefore installed an Marvell SATA Controller (see below) and connected it to the CD-drive.
I am however not able to mount the CD-drive, and when I try the computer hangs. Interestingly the drive appears automatically in a Windows 10 when I run it as a VM-player guest on my Ubuntu 22.04 host.
What should I do?
Thanks in advance for any tip
H


Device Information
Name Marvell Technology Group Ltd. 88SE9215 PCle 2.0 X1 4-port SATA 6 Gb/s Controller (rev 11) (prog-f 01 [AHCI 1.0])
class SATA controller

root@x22:/home/he# ls -l /dev/cdrom 
lrwxrwxrwx 1 root root 3 maj 29 09:05 /dev/cdrom -> sr0
root@x22:/home/he# ls -l /dev/sr0 
brw-rw----+ 1 root cdrom 11, 0 maj 29 09:05 /dev/sr0
root@x22:/home/he# mount /dev/sr0 /mnt/cdrom
..
(here it hangs)
..
^C

---

