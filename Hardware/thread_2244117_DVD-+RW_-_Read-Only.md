---
title: "DVD-+RW - Read-Only"
date: 2014-09-13
forum: Hardware
---

### Post by tinman2 on 2014-09-13
I'm having problems writing to a DVD-+RW and have searched hundreds of messages on this forum without any luck.  It's not my DVD writer, it writes to DVD+RW's that were formatted with Nero under XP just like it was a hard drive.  My CD/DVD Dual Layer recorder is compatible with + or - media.

First, I formatted the 4.7 GB DVD with:

  dvd+rw-format /dev/sr0 .  (I have also tried formatting with Brasero and K3b with the same results.)

Then made it a UDF format:

  mkudffs /dev/sr0

Checked the permissions:  (I am the Administrator)

tinman@ASL:~$ ls -l /dev/cdrom
lrwxrwxrwx 1 root root 3 Sep 13 15:36 /dev/cdrom -> sr0
tinman@ASL:~$ 

  So far, so good, until I attempt to write a file or make any other changes on the DVD, then I get an error "Destination is read-only".  I can pull out this DVD media and insert the same exact media that was formatted under XP and write to it or make changes all day long just like a hard drive.

I ran the command:

  dvd+rw-mediainfo /dev/sr0 and got this:

tinman@ASL:~$ dvd+rw-mediainfo /dev/sr0
INQUIRY:                [ASUS    ][DRW-24B1ST   i  ][1.00]
GET [CURRENT] CONFIGURATION:
 Mounted Media:         1Ah, DVD+RW
 Media ID:              PHILIPS/041
 Current Write Speed:   4.0x1385=5540KB/s
 Write Speed #0:        4.0x1385=5540KB/s
 Speed Descriptor#0:    00/2295103 R@8.0x1385=11080KB/s W@4.0x1385=5540KB/s
READ DVD STRUCTURE[#0h]:
 Media Book Type:       00h, DVD-ROM book [revision 0]
 Legacy lead-out at:    2295104*2KB=4700372992
READ DISC INFORMATION:
 Disc status:           complete
 Number of Sessions:    1
 State of Last Session: complete
 Number of Tracks:      1
 BG Format Status:      suspended
READ FORMAT CAPACITIES:
 formatted:             2295104*2048=4700372992
 26h(0):                2295104*2048=4700372992
READ TRACK INFORMATION[#1]:
 Track State:           complete incremental
 Track Start Address:   0*2KB
 Free Blocks:           0*2KB
 Track Size:            2295104*2KB
FABRICATED TOC:
 Track#1  :             14@0
 Track#AA :             17@2295104
 Multi-session Info:    #1@0
READ CAPACITY:          2295104*2048=4700372992
tinman@ASL:~$ 


  I'm on Ubuntu 14.04 LTS on a custom ASL Workstation, Intel Core i7-4820K (Ivy Bridge E), 3.9GHz, X79 Express chipset and 20 GB of system memory.

  I don't have any problems with my other external devices like a 1 TB USB drive or an 8 GB thumb-drive.

  Any help will be much appreciated.

---

