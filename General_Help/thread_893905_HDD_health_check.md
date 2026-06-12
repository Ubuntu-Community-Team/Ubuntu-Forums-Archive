---
title: "HDD health check?"
date: 2008-08-18
forum: General Help
---

### Post by devman on 2008-08-18
I'm looking for a way to check the health of my hard drive before I put an SVN server on it. Is there an easy way to do that that in a way that will generate a log file? (I'm running a headless Ubuntu server.)

I'd just like to check the disk sectors and see if everything is good to go.

---

### Post by az on 2008-08-18
[https://help.ubuntu.com/community/FaultyHardware](https://help.ubuntu.com/community/FaultyHardware)

Self-Monitoring, Analysis and Reporting Technology System (S.M.A.R.T.) is built into most modern ATA and SCSI hard disks. To use SMART to check your disk, install the smartmontools package.

To all information provided by SMART on /dev/sda, run

sudo smartctl -a /dev/sda

To run a selftest on /dev/sda, run

sudo smartctl -t long /dev/sda

To view the results of the test, display all information (see above) or simply run

sudo smartctl -l selftest /dev/sda

An alternative way to check your disk is to use badblocks. To perform a non-destructive scan of the disk surface, boot the live cd and run badblocks from the command-line

sudo badblocks -nvs /dev/sda (where sda is the disk to examine)

---

### Post by raashell on 2011-04-28
Just a quick note, I did an install of Natty today on an older disk and it looked like there were some bad blocks.

I'm sure you sysadmin people already know this, but running the live cd in rescue mode would not allow a read-write check by badblocks (because the disk was mounted and couldn't be un-mounted).

Launching just the plain old shell from the live disk didn't mount the disk and *did* allow me to run the command.

---

### Post by arcosaf on 2011-11-02
The problem not exist, in the Disk Utility application select the hard disk to verify, and then click in SMART Data.

Alejandro

---

### Post by dFlyer on 2011-11-02
If disk utility says you have bad blocks/sectors, backup what ever data you want to keep and replace the drive.

---

