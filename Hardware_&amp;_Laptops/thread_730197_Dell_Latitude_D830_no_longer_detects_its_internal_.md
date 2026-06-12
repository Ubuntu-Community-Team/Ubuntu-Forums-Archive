---
title: "Dell Latitude D830 no longer detects its internal DVD Burner"
date: 2008-03-20
forum: Hardware &amp; Laptops
---

### Post by mdlueck on 2008-03-20
We loaded a Dell Latitude D830 w/ nVidia Quadro NVS140 chip and built-in DVD burner with Ubuntu 7.04 Feisty Fawn. Initially the internal CD drive was working properly as we were able to install from the alternate CD.

Now suddenly it does not have any device in the /dev directory that is for the internal CD drive.

More puzzling was the /etc/fstab had an entry for the CD as /dev/hda. No number, just "hda".

We connected a USB CD burner and it properly shows up in the /dev directory, various entries with "cdrom" as the group. I adjusted the /etc/fstab file and we are able to put CD's in the external drive, it automounts the drive, can access files.

So, what in the world happened to the internal drive? How do we diagnose this problem?

We tried putting in the Ubuntu alternate CD we installed from, and the computer does boot off of it. So it is not like the CD drive suddenly failed.

---

### Post by mdlueck on 2008-03-20
I am digging through /etc/messages in search of details about the internal CD drive. I came across the following lines, for which there is no corresponding entry in /dev:

scsi 2:0:0:0: Direct-Access     NEC      USB UF000x       1.50 PQ: 0 ANSI: 0 CCS
sd 2:0:0:0: Attached scsi removable disk sdb
sd 2:0:0:0: Attached scsi generic sg1 type 0

/dev$ ls -al sdb*
ls: sdb*: No such file or directory

/dev$ ls -al sg1
crw-rw---- 1 root cdrom 21, 1 2008-03-20 10:08 sg1

aaahhh, I will make some changes to /etc/fstab and report back the findings. What an odd device name for it to show up as, if it really is the internal drive.

---

### Post by mdlueck on 2008-03-20
(shrug) sg1 device is not something suitable to try to mount. sdb does not exist, yet I see it mentioned in messages. I think I am stuck.

---

