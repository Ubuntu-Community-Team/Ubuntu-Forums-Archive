---
title: "sony DVD-ROM DDU 1611 not playing dvd's"
date: 2010-07-03
forum: Hardware
---

### Post by anthonyu on 2010-07-03
Hi Guys,

I am getting started with ubuntu, so excuse my my newbi questions.

I have recently installed ubuntu 10.04 in an old PC, with dual boot win2000, and the DVD drive will not play DVD's. It is a SONY DVD-ROM DDU 1611. 
I have already installed the restricted formats, listed at the link.
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

This is working, as I have a USB DVD player, a LG GP08, which can play DVD's in the system. However, the DVD's will not play with the installed DVD player. It will however recognise Audio CD's though.

I ran the command SUDO lshw a few times with different media, and I've listed the results below. There is also a CD drive as well, which is working so far

1) sudo lshw with no disk in the dvd drive

           *-cdrom:0
                description: DVD reader
                physical id: 0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio dvd
                configuration: status=nodisc
           *-cdrom:1
                description: CD-R/CD-RW writer
                product: CD-RW  CRX225E
                vendor: SONY
                physical id: 1
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: QYB1
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=nodisc

2) sudo lshw with Audio CD in the dvd drive

           *-cdrom:0
                description: DVD reader
                physical id: 0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio dvd
                configuration: status=ready
           *-cdrom:1
                description: CD-R/CD-RW writer
                product: CD-RW  CRX225E
                vendor: SONY
                physical id: 1
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: QYB1
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=nodisc

3) sudo lshw with DVD in the dvd drive

          *-cdrom:0
                description: DVD reader
                physical id: 0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio dvd
                configuration: status=ready
           *-cdrom:1
                description: CD-R/CD-RW writer
                product: CD-RW  CRX225E
                vendor: SONY
                physical id: 1
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: QYB1
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=nodisc

It'll be great if anyone could give me some insights to this.

Thanks,
Anthony

---

### Post by anthonyu on 2010-07-06
Hi Guys,

I just tried the command dmesg | tail

1) This was with a DVD that had data on it

samantha@ubuntu:~$ dmesg | tail
[  515.624769] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 23 12 7c 00 00 02 00
[  515.624788] end_request: I/O error, dev sr0, sector 9193968
[  515.624795] Buffer I/O error on device sr0, logical block 1149246
[  522.951471] sr 0:0:1:0: [sr0] Unhandled sense code
[  522.951477] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  522.951483] sr 0:0:1:0: [sr0] Sense Key : Medium Error [current] 
[  522.951490] sr 0:0:1:0: [sr0] Add. Sense: No seek complete
[  522.951497] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 23 12 7c 00 00 02 00
[  522.951515] end_request: I/O error, dev sr0, sector 9193968
[  522.951522] Buffer I/O error on device sr0, logical block 1149246

2) This was with a movie DVD

samantha@ubuntu:~$ dmesg | tail
[  522.951471] sr 0:0:1:0: [sr0] Unhandled sense code
[  522.951477] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  522.951483] sr 0:0:1:0: [sr0] Sense Key : Medium Error [current] 
[  522.951490] sr 0:0:1:0: [sr0] Add. Sense: No seek complete
[  522.951497] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 23 12 7c 00 00 02 00
[  522.951515] end_request: I/O error, dev sr0, sector 9193968
[  522.951522] Buffer I/O error on device sr0, logical block 1149246
[  601.721039] sr0: CDROM (ioctl) error, command: Xdread, Read track info 52 01 00 00 00 01 00 00 08 00
[  601.721062] sr: Sense Key : Medium Error [current] 
[  601.721069] sr: Add. Sense: L-EC uncorrectable error
samantha@ubuntu:~$

---

### Post by anthonyu on 2010-07-11
Hi Guys,

I am leaving this as unresolved. I was planning to try and convince some other users to change over to Ubuntu. I had a high spec older PC that I wanted people to still use, so I thought to give them a robust solution, where they could use the latest version of Ubuntu and replace their windows requirements.

At the moment they are using the DVD's on the windows 2000 operating system. It is a dual boot win2000 /ubuntu 10.04

A shame, I would have liked to resolve this one. I have searched through, but I haven't found a solution.

Thanks anyway.

---

