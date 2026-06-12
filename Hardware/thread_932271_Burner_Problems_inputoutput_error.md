---
title: "Burner Problems input/output error"
date: 2008-09-28
forum: Hardware
---

### Post by 426matt on 2008-09-28
Hello, I have a problem with burning of DVD's with my system. I have two burners, and neither of them will burn. I have had Hardy Heron installed for around 6 months now and have not had a problem until recently. Now, when I try to burn I just get error messages with the LG 4163B, or I get what appears to be a burn with the Pioneer DVR-212, but the disc is no good, has errors on it and wont work. Both drives will read just fine

I get input/output error with GnomeBaker, and with K3b I get a disc error and output of:

System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version: 3.3.8b
Kernel: 2.6.24-21-generic
Devices
-----------------------
HL-DT-ST DVDRAM GSA-4163B A106 (/dev/scd1, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite]

PIONEER DVD-RW DVR-212 1.24 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]
Burned media
-----------------------
DVD+R

K3bIsoImager
-----------------------
mkisofs print size result: 2250290 (4608593920 bytes)
Pipe throughput: 34738176 bytes read, 34733696 bytes written.

Used versions
-----------------------
mkisofs: 1.1.6
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd1 obs=32k seek=0'
/dev/scd1: "Current Write Speed" is 4.1x1352KBps.
1114112/4608593920 ( 0.0%) @0.0x, remaining 344:37 RBU 100.0% UBU 2.9%
1114112/4608593920 ( 0.0%) @0.0x, remaining 551:24 RBU 100.0% UBU 100.0%
1114112/4608593920 ( 0.0%) @0.0x, remaining 758:11 RBU 100.0% UBU 100.0%
1114112/4608593920 ( 0.0%) @0.0x, remaining 1033:53 RBU 100.0% UBU 100.0%
1114112/4608593920 ( 0.0%) @0.0x, remaining 1240:40 RBU 100.0% UBU 100.0%
1114112/4608593920 ( 0.0%) @0.0x, remaining 1447:26 RBU 100.0% UBU 100.0%
:-[ WRITE@LBA=220h failed with SK=3h/ASC=0Ch/ACQ=00h]: Input/output error
write failed: Input/output error
/dev/scd1: flushing cache
:-[ SYNCHRONOUS FLUSH CACHE failed with SK=3h/ASC=A0h/ACQ=80h]: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/scd1=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:2250290 -dvd-compat -speed=4 -use-the-force-luke=bufsize:32m

mkisofs
-----------------------
2250290
I: -input-charset not specified, using utf-8 (detected in locale settings)
0.02% done, estimate finish Sun Sep 28 21:42:15 2008
0.04% done, estimate finish Sun Sep 28 21:42:15 2008
0.07% done, estimate finish Sun Sep 28 21:42:15 2008
0.09% done, estimate finish Sun Sep 28 21:42:15 2008
0.11% done, estimate finish Sun Sep 28 21:42:15 2008
0.13% done, estimate finish Sun Sep 28 21:42:15 2008
0.16% done, estimate finish Sun Sep 28 21:42:15 2008
0.18% done, estimate finish Sun Sep 28 21:42:15 2008
0.20% done, estimate finish Sun Sep 28 21:42:15 2008
0.22% done, estimate finish Sun Sep 28 21:49:44 2008
0.25% done, estimate finish Sun Sep 28 21:49:03 2008
0.27% done, estimate finish Sun Sep 28 21:48:29 2008
0.29% done, estimate finish Sun Sep 28 21:48:00 2008
0.31% done, estimate finish Sun Sep 28 21:47:36 2008
0.33% done, estimate finish Sun Sep 28 21:47:14 2008
0.36% done, estimate finish Sun Sep 28 21:46:55 2008
0.38% done, estimate finish Sun Sep 28 21:46:39 2008
0.40% done, estimate finish Sun Sep 28 21:46:24 2008
0.42% done, estimate finish Sun Sep 28 21:46:11 2008
0.44% done, estimate finish Sun Sep 28 21:45:59 2008
0.47% done, estimate finish Sun Sep 28 21:45:49 2008
0.49% done, estimate finish Sun Sep 28 21:45:39 2008
0.51% done, estimate finish Sun Sep 28 21:45:30 2008
0.53% done, estimate finish Sun Sep 28 21:45:22 2008
0.56% done, estimate finish Sun Sep 28 21:45:14 2008
0.58% done, estimate finish Sun Sep 28 21:45:08 2008
0.60% done, estimate finish Sun Sep 28 21:45:01 2008
0.62% done, estimate finish Sun Sep 28 21:44:55 2008
0.64% done, estimate finish Sun Sep 28 21:44:50 2008
0.67% done, estimate finish Sun Sep 28 21:44:44 2008
0.69% done, estimate finish Sun Sep 28 21:44:40 2008
0.71% done, estimate finish Sun Sep 28 21:46:56 2008
0.73% done, estimate finish Sun Sep 28 21:46:47 2008

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid K3b data project -volset -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher -preparer -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-click/k3bBgUOnc.tmp -rational-rock -hide-list /tmp/kde-click/k3bCJQtEa.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-click/k3baOA8Ga.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-click/k3bzDtkib.tmp

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid K3b data project -volset -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher -preparer -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-click/k3bbJC6ca.tmp -rational-rock -hide-list /tmp/kde-click/k3bDkHrZb.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-click/k3bdxu4ja.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-click/k3bDGGJPb.tmp

I have a dual boot system with Windows XP, and burners work fine there.

Is anybody able to help, as I am at my wits end at the moment. I want to use Linux, but am on my 3rd distro, all with different problems. Ubuntu was looking like the one I was going to stay with.

Thanks in advance for any help

---

### Post by Steve H on 2008-09-28
I'm getting a similar problem, just started today while trying to burn an .iso image to a TDK DVD....

The debugging output shows this:

```
System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.24-19-generic
Devices
-----------------------
LITE-ON DVDRW LH-20A1P KL0G (/dev/scd0, /dev/sg2) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

Burned media
-----------------------
DVD-R Sequential

Used versions
-----------------------
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
/dev/scd0: "Current Write Speed" is 16.4x1352KBps.
     950272/1440417792 ( 0.1%) @0.0x, remaining 151:28 RBU 100.0% UBU   9.7%
     950272/1440417792 ( 0.1%) @0.0x, remaining 227:13 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 302:57 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 403:56 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 479:41 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 555:25 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 656:24 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 732:09 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 807:53 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 908:52 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 984:37 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 1060:21 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 1161:20 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 1237:04 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 1312:49 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 1413:48 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 1489:32 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 1565:17 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 1666:16 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 1742:00 RBU 100.0% UBU 100.0%
:-[ WRITE@LBA=1d0h failed with SK=0h/ASC=00h/ACQ=02h]: Input/output error
:-( write failed: Input/output error
/dev/scd0: flushing cache
/dev/scd0: updating RMA
/dev/scd0: closing disc

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/scd0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:703329 -dvd-compat -speed=16 -use-the-force-luke=bufsize:32m 
```

I did recently enable "backports" on the Update Manager the other day and keep seeing a k3b update on there but it's always greyed out, could this be connected?

---

### Post by Steve H on 2008-09-29
I've chased this problem a little further. It would seem to be a bit more co-operative at burning at lower speeds (4x and below). Also I have tried burning in Brasero as well, but that produced EXACTLY the same error when it failed to burn.
```
:-[ WRITE@LBA=220h failed with SK=3h/ASC=0Ch/ACQ=00h]: Input/output error
write failed: Input/output error
/dev/scd1: flushing cache
:-[ SYNCHRONOUS FLUSH CACHE failed with SK=3h/ASC=A0h/ACQ=80h]: Input/output error
```

Because of the low burn speeds and the reproducable failure in other software I'm starting to think this may be something other than ropey apps.

Does anyone know anything about DMA settings on the Ubuntu IDE driver? Could this affect the ability to burn properly?

It also seems to "hang" at the "Updating RMA.." bit of the burn process (when it does actually burn that is). Does anyone know what this is doing as I cannot find anything about what the app is doing when it is "Updating RMA"?!?!?

---

### Post by Steve H on 2008-09-29
Have a look [here]("http://ubuntuforums.org/showthread.php?t=933114")

I seem to have stumbled on a way through the probs..

---

### Post by 426matt on 2008-10-01
Thanks for putting in the extra effort. I will have a go with that and see what happens

---

### Post by 426matt on 2008-10-03
Different speeds, different drives, different discs, +R, -R, +RW, new codecs. Nothing works. I have had enough. I have really tried. I wanted to use Linux so badly. The thing is, Windows is so loudly put into poor regard, but I never had this many problems with it. Every distro I have tried has had a huge problem that nobody seems to know how to fix. I could fix Windows myself.  I will try Linux again at a later date.

---

### Post by markbuntu on 2008-10-03
Are you using memorex dvd disks?
They seem to not work but other disks like from TDK, SONY and Verbatim do. I thought my dvd burner was toasted but it would burn cds, just not memorex dvds of any kind. Got some TDK and they worked!
Others have reported that Verbatim and Sony also work.

---

### Post by Pete7 on 2008-10-04
EXACTLY the same problem in Denver that started when I upgraded to Hardy three weeks ago. The Plextor PX-800A works fine on the Windows side it just won't burn and has trouble playing. I've tried every thread I can find on the internet and nothing is able to change it. Hardy does think it's a SCSI device, but that shouldn't be it.
For now I'm burning with K3B to a "portable" burner on a usb port.
I'm ready to try anything my skill level can handle:confused:

---

### Post by Steve H on 2008-10-10
My problems still aren't quite all ironed out. I'm getting a hit-rate of about one successful disk burn in about every five attempts. It's a pain in the **** TBH. I'm wasting loads of disks as it does appear to write just enough data on the disk to make a beautiful coaster!!

I was experiencing problems when growisofs wouldn't release the drive after a failed burn. Now I just kill the process and I can at least get the coaster out of the drive. 

It does seem strange that this is happening under Heron, my burner works fine in Windows and worked fine in Gibbon.

Is this a glitch with growisofs?

Has anyone tried burning files to disk? I'm attempting to burn .iso files to the disk and having these problems, I just wonder if it is DVDs in general that are the problem. I'm just trying to narrow down the possibilites of the problems we are all experiencing.

---

### Post by taecha on 2008-10-10
Steve H, same problem here with ISOs as well as files. Neither Brasero nor Nautilus direct burn work most of the time. I followed one idea in another thread I decreased burning speed. I have just finished burning an ISO this way but can't tell whether it was successful because of the speed decrease or just by pure luck. :confused:

Problem emerged - as with many others - only recently. I have been burning DVDs for the last few months. The problem emerged about 3 weeks ago.

Running Hardy, GNOME brasero 0.7.1, and GNOME nautilus 2.22.5.1.

---

### Post by bongoMaster on 2008-12-19
exactly the same problem here on Hardy i386 with k3b. I tried 2 DVD recorders (both LG) and already lost a few discs. I only have Memorex DVDs here, somebody tried it with another brand?

It's bad publicity for ubuntu, imagine what a newby would think about an OS that isn't able to burn DVDs... Very poor... Nobody here with an idea of what the problem could be?

---

### Post by bongoMaster on 2008-12-19
The problem was solved by installing the latest firmware of my DVD-recorder.

Here the details of my working configuration:

# distro: Kubuntu Hardy Heron i386
# recorder: LG HL-DT-ST DVDRAM GSA-4160B
# firmware: updated from A302 to A306

```
$ k3b -version
Qt: 3.3.8b
KDE: 3.5.10
K3b: 1.0.5

```

```
$ growisofs -version
* growisofs by <appro@fy.chalmers.se>, version 7.0.1,
  front-ending to genisoimage: genisoimage 1.1.6 (Linux)

```

I tested it again with Memorex DVDs and it works.

---

