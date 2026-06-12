---
title: "External CDDVDW not working correctly"
date: 2013-05-24
forum: Hardware
---

### Post by asensio on 2013-05-24
Hi everyone,

I have an external Samsung SE-S204N DVD writer drive that I've been using since ever with Ubuntu. But now, since Precise (I'm on Ubuntu Precise Pangolin 64bits), the drive sometimes works sometimes it doesn't. When it doesn't work, it can't mount the media, there's no led blinking and even the eject button is useless.

On the desktop I also have an old internal Asus DVD drive that is working flawlessly. It mounts, with no problem, the media that the Samsung can't mount.

I've tried it on a machine with the OS *we do not speak of* and everything worked fine.

I've made some "tests" to see the output and find if the hardware is ok, here are the results: 

**asensio@Linux:~$ lsusb**
```
Bus 001 Device 002: ID 13fd:2040 Initio Corporation 
Bus 001 Device 003: ID 0cf3:7015 Atheros Communications, Inc. TP-Link TL-WN821N v3 802.11n [Atheros AR7010+AR9287]
Bus 004 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```


**asensio@Linux:~$ ls -l /media**
```
total 4
lrwxrwxrwx 1 root root    7 Mai 18 01:05 floppy -> floppy0
drwxr-xr-x 2 root root 4096 Mai 18 01:05 floppy0
```


**asensio@Linux:~$ sudo lshw -C disk     *[COLOR="#FF0000"]<---- started to spin[/COLOR]***
```
  *-disk                  
       descrição: ATA Disk
       produto: MAXTOR STM316021
       fabricante: Maxtor
       physical id: 0.0.0
       informações do barramento: scsi@0:0.0.0
       nome lógico: /dev/sda
       versão: 3.AA
       serial: 5RA98GF2
       tamanho: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuração: ansiversion=5 signature=f0c798a9
  *-cdrom
       descrição: DVD reader
       physical id: 0.1.0
       informações do barramento: scsi@0:0.1.0
       nome lógico: /dev/cdrom1
       nome lógico: /dev/dvd1
       nome lógico: /dev/sr0
       capabilities: audio dvd
       configuração: status=nodisc
  *-disk
       descrição: ATA Disk
       produto: WDC WD3200AAJS-5
       fabricante: Western Digital
       physical id: 0.0.0
       informações do barramento: scsi@2:0.0.0
       nome lógico: /dev/sdb
       versão: 01.0
       serial: WD-WCAV2CA14602
       tamanho: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuração: ansiversion=5 signature=15f75b9e
  *-cdrom
       descrição: DVD-RAM writer
       produto: CDDVDW SE-S204N
       fabricante: TSSTcorp
       physical id: 0.0.0
       informações do barramento: scsi@4:0.0.0
       nome lógico: /dev/cdrom
       nome lógico: /dev/sr1
       versão: TS00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuração: status=ready
     *-medium
          physical id: 0
          nome lógico: /dev/cdrom
```

**asensio@Linux:~$ ls -l /dev/cdrom**
```
lrwxrwxrwx 1 root root 3 Mai 24 21:43 /dev/cdrom -> sr1
```


**asensio@Linux:~$ dmesg | grep /dev/sr1     *[COLOR="#FF0000"]<---- no output[/COLOR]***


**asensio@Linux:~$ dmesg | grep /dev/cdrom     *[COLOR="#FF0000"]<---- no output[/COLOR]***


**asensio@Linux:~$ wodim --prcap dev=/dev/sr1**
```
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'TSSTcorp'
Identification : 'CDDVDW SE-S204N '
Revision       : 'TS00'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.

Drive capabilities, per MMC-3 page 2A:

  Does read CD-R media
  Does write CD-R media
  Does read CD-RW media
  Does write CD-RW media
  Does read DVD-ROM media
  Does read DVD-R media
  Does write DVD-R media
  Does read DVD-RAM media
  Does write DVD-RAM media
  Does support test writing

  Does read Mode 2 Form 1 blocks
  Does read Mode 2 Form 2 blocks
  Does read digital audio blocks
  Does restart non-streamed digital audio reads accurately
  Does support Buffer-Underrun-Free recording
  Does read multi-session CDs
  Does read fixed-packet CD media using Method 2
  Does not read CD bar code
  Does read R-W subcode information
  Does return R-W subcode de-interleaved and error-corrected
  Does read raw P-W subcode data from lead in
  Does return CD media catalog number
  Does return CD ISRC information
  Does support C2 error pointers
  Does not deliver composite A/V data

  Does play audio CDs
  Number of volume control levels: 256
  Does support individual volume control setting for each channel
  Does support independent mute setting for each channel
  Does not support digital output on port 1
  Does not support digital output on port 2

  Loading mechanism type: tray
  Does support ejection of CD via START/STOP command
  Does not lock media on power up via prevent jumper
  Does allow media to be locked in the drive via PREVENT/ALLOW command
  Is currently in a media-locked state
  Does not support changing side of disk
  Does not have load-empty-slot-in-changer feature
  Does not support Individual Disk Present feature

  Maximum read  speed:  7056 kB/s (CD  40x, DVD  5x)
  Current read  speed:  7056 kB/s (CD  40x, DVD  5x)
  Maximum write speed:  8468 kB/s (CD  48x, DVD  6x)
  Current write speed:  8468 kB/s (CD  48x, DVD  6x)
  Rotational control selected: CLV/PCAV
  Buffer size in KB: 2048
  Copy management revision supported: 1
  Number of supported write speeds: 5
  Write speed # 0:  8468 kB/s CLV/PCAV (CD  48x, DVD  6x)
  Write speed # 1:  7056 kB/s CLV/PCAV (CD  40x, DVD  5x)
  Write speed # 2:  5645 kB/s CLV/PCAV (CD  32x, DVD  4x)
  Write speed # 3:  4234 kB/s CLV/PCAV (CD  24x, DVD  3x)
  Write speed # 4:  2823 kB/s CLV/PCAV (CD  16x, DVD  2x)
```


**asensio@Linux:~$ wodim --devices**
```
wodim: Overview of accessible drives (2 found) :
-------------------------------------------------------------------------
 0  dev='/dev/sg1'	rwrw-- : 'ASUS' 'DVD-ROM E616'
 1  dev='/dev/sg3'	rwrw-- : 'TSSTcorp' 'CDDVDW SE-S204N'
-------------------------------------------------------------------------
```


**asensio@Linux:~$ wodim -scanbus**
```
scsibus0:
	0,0,0	  0) *
	0,1,0	  1) 'ASUS    ' 'DVD-ROM E616    ' '2.0 ' Removable CD-ROM
	0,2,0	  2) *
	0,3,0	  3) *
	0,4,0	  4) *
	0,5,0	  5) *
	0,6,0	  6) *
	0,7,0	  7) *
scsibus4:
	4,0,0	400) 'TSSTcorp' 'CDDVDW SE-S204N ' 'TS00' Removable CD-ROM
	4,1,0	401) *
	4,2,0	402) *
	4,3,0	403) *
	4,4,0	404) *
	4,5,0	405) *
	4,6,0	406) *
	4,7,0	407) *

```

**asensio@Linux:~$ sudo mount /dev/sr1 /media/floppy     *[COLOR="#FF0000"]<---- started to spin[/COLOR]***
```
mount: block device /dev/sr1 is protected; mounting in read only mode
```

**asensio@Linux:~$ sudo umount /dev/sr1**
```
umount: /dev/sr1: not mounted
```

**asensio@Linux:~$ sudo mount /dev/cdrom /media/floppy0     *[COLOR="#FF0000"]<---- started to spin[/COLOR]***
```
mount: block device /dev/sr1 is protected; mounting in read only mode
```

**asensio@Linux:~$ sudo umount /dev/cdrom**
```
umount: /dev/cdrom: not mounted
```

It's everything ok? If so could it be a software problem? Hope that someone can help
Thanks
Cheers
**asensio**

---

### Post by asensio on 2013-05-26
I tried with a Precise LiveCD in the old Asus to see if the External Drive would mount a CD. It didn't work...
Again, if someone could tell me if the outputs in the first post are ok, I would appreciate.
Thanks,
Cheers
**asensio**

---

### Post by asensio on 2013-05-29
anyone? someone?
:(
**asensio**

---

