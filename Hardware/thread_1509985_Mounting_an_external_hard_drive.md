---
title: "Mounting an external hard drive"
date: 2010-06-14
forum: Hardware
---

### Post by astay13 on 2010-06-14
I have an external hard drive which I store my backed up data on.  I have just started to move to Linux, so I am dual booting Windows XP Professional and Kubuntu 10.04.  My external hard drive is set up to be accessed under Windows as follows:  First it sets up a "cd drive" and you run a password utility which then sets up the main hard drive so you can copy files to it, etc.  When I try to mount it in ubuntu, all I see from ls /dev or fdisk -l are the following drives/partitions:
sda (My main internal hard drive)
sda1 (Windows)
sda2
sda5 (Kubuntu)
sda6 (Kubuntu swap)
sdb (The external hard drive)
Also, I can find the following when I run ls /dev
sr1 (The "cd drive")
I cannot mount sdb since I cannot find a partition number.
I can mount sr1 and view the contents but this does not help me mount sdb since I cannot run the (windows) password utility under linux.  How would I go about mounting sdb?

Thanks alot!

---

### Post by IcarusR on 2010-06-15
Is the drive encrypted ?
Is the drive visible to windows system before running the cd program. ie to windows equivalent of fdisk -l ??

Plug the drive in then type this in terminal & see if it says anything relevant.

```
dmesg | tail
```

If you have to run a separate password program in windows before drive is visible how are you going to enter password under Ubuntu ??

---

### Post by astay13 on 2010-06-15
I do not believe the drive is encrypted.
It is not visible to Windows before running the password utility.
Since I can't run the password utility under Ubuntu, I am looking for a workaround so I can access my data from Ubuntu and not Windows only.

dmesg says the following about my external drive:
```
[    6.064842] scsi 2:0:0:0: CD-ROM            BUFFALO  USB-ATA Bridge   1.20 PQ: 0 ANSI: 0
[    6.066823] scsi 2:0:0:1: Direct-Access     BUFFALO  Disk Drive       1.20 PQ: 0 ANSI: 0
[    6.085563] sr1: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[    6.085752] sr 2:0:0:0: Attached scsi CD-ROM sr1
[    6.085873] sr 2:0:0:0: Attached scsi generic sg2 type 5
[    6.086109] sd 2:0:0:1: Attached scsi generic sg3 type 0
[    6.088191] sd 2:0:0:1: [sdb] Attached SCSI disk

```

I have tried mounting sg3 but it says it can't do that because it is a character file not a block file.

---

