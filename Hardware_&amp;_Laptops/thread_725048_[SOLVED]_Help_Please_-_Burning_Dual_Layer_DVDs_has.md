---
title: "[SOLVED] Help Please - Burning Dual Layer DVDs has stopped working"
date: 2008-03-15
forum: Hardware &amp; Laptops
---

### Post by stevo82 on 2008-03-15
I am relatively new to linux so apologies upfront if i am not quite on the ball.

I had been burning many dual layer dvds without a problem, but when i came to burn one last week it failed.  Thinking it was the new media i had bought i tried a few more and they all failed too.  Thinking this was just the new media i went and ordered the same discs as i had had success with.  These arrived last night and i tried them but keep getting the same failure.  I don't understand it as this had been working.

I don't think the problem is the media as they are the same brand of media that have worked before and they also work in my harddisc/dvd recorder.  All i can think of is that at some point since the last successfull burn i have had an upgrade that has changed something.

I have tried looking at other threads and while some are similar they seem to have never been able to get it to work whereas this did work for me.

ok. now some details...

Laptop is a dell inspiron 6400 with NEC DVD drive that def supports DL writing.
I am using kubuntu 7.10 with all the latest updates.
Also have dual boot with windows XP (although hardly ever use it) so no updates for a while.
Using datawrite DVD +R DL discs (that have worked before).

I have had success under both linux (using K3b) and windows (using both sonic and nero) but now neither works and they both seem to fail writing at startup as the discs are still totally blank after the fail.

Below is the trace when using K3b.

During K3b start up...

```

steve@default:~$ k3b
kdecore (KAction): WARNING: KActionCollection::KActionCollection( QObject *parent, const char *name, KInstance *instance )
(K3bDevice::HalConnection) initializing HAL >= 0.5
Mapping udi /org/freedesktop/Hal/devices/storage_model_DVD__RW_ND_6650A to device /dev/scd0
/dev/scd0 resolved to /dev/scd0
/dev/scd0 is block device (0)
/dev/scd0 seems to be cdrom
bus: 1, id: 0, lun: 0
(K3bDevice::Device) /dev/scd0: init()
(K3bDevice::Device) /dev/scd0 feature: CD Mastering
(K3bDevice::Device) /dev/scd0 feature: CD Track At Once
(K3bDevice::Device) /dev/scd0 feature: CD-RW Media Write Support
(K3bDevice::Device) /dev/scd0 feature: DVD+R
(K3bDevice::Device) /dev/scd0 feature: DVD+RW
(K3bDevice::Device) /dev/scd0 feature: DVD+R Double Layer
(K3bDevice::Device) /dev/scd0 feature: DVD-R/-RW Write
(K3bDevice::Device) /dev/scd0 feature: Rigid Restricted Overwrite
(K3bDevice::Device) /dev/scd0: dataLen: 60
(K3bDevice::Device) /dev/scd0: checking for TAO
(K3bDevice::Device) /dev/scd0: checking for SAO
(K3bDevice::Device) /dev/scd0: checking for SAO_R96P
(K3bDevice::Device) /dev/scd0: checking for SAO_R96R
(K3bDevice::Device) /dev/scd0: checking for RAW_R16
(K3bDevice::Device) /dev/scd0: checking for RAW_R96P
(K3bDevice::Device) /dev/scd0: checking for RAW_R96R
(K3bDevice::Device) /dev/scd0: GET PERFORMANCE dataLen = 8
(K3bDevice::Device) /dev/scd0: GET PERFORMANCE reports bogus dataLen: 8
(K3bDevice::Device) /dev/scd0:  Number of supported write speeds via 2A: 6
(K3bDevice::Device) /dev/scd0 : 4234 KB/s
(K3bDevice::Device) /dev/scd0 : 3528 KB/s
(K3bDevice::Device) /dev/scd0 : 2822 KB/s
(K3bDevice::Device) /dev/scd0 : 1764 KB/s
(K3bDevice::Device) /dev/scd0 : 1411 KB/s
(K3bDevice::Device) /dev/scd0 Invalid DVD speed: 706 KB/s
(K3bDevice::DeviceManager) setting current write speed of device /dev/scd0 to 0
/dev/scd0 resolved to /dev/scd0
(K3bDevice::DeviceManager) dev /dev/scd0 already found
(K3bDevice::DeviceManager) found config entry for devicetype: _NEC DVD+-RW ND-6650A
(K3bDevice::ScsiCommand) failed:
                           command:    READ DVD STRUCTURE (ad)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ DVD STRUCTURE length det failed
(K3bDevice::Device) Unable to read DVD structure for num of layers.
DiskInfo:
Mediatype:       DVD+R Dual Layer
Current Profile: DVD+R Dual Layer
Disk state:      empty
Empty:           1
Rewritable:      0
Appendable:      0
Sessions:        0
Tracks:          0
Layers:          2
Capacity:        927:30:74 (LBA 4173824) (8547991552 Bytes)
Remaining size:  Devices:
------------------------------
927:30:74 (LBA 4173824) (8547991552 Bytes)
Used Size:       Blockdevice:    /dev/scd0
Generic device:
Vendor:         _NEC
Description:    DVD+-RW ND-6650A
Version:        102C
Write speed:    4234
Profiles:       DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW
Read Cap:       DVD-ROM, DVD-R, DVD-R Sequential, DVD-RW, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW
Write Cap:      DVD-R, DVD-R Sequential, DVD-RW, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-R, CD-RW
Writing modes:  SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite
Reader aliases: /dev/scd0
------------------------------
00:00:00 (LBA 0) (0 Bytes)
kdecore (KAction): WARNING: KActionCollection::operator+=(): function is severely deprecated.
(K3bDevice::Device) /dev/scd0: GET PERFORMANCE dataLen = 8
(K3bDevice::Device) /dev/scd0: GET PERFORMANCE reports bogus dataLen: 8
(K3bDevice::Device) /dev/scd0:  Number of supported write speeds via 2A: 6
(K3bDevice::Device) /dev/scd0 : 4234 KB/s
(K3bDevice::Device) /dev/scd0 : 3528 KB/s
(K3bDevice::Device) /dev/scd0 : 2822 KB/s
(K3bDevice::Device) /dev/scd0 : 1764 KB/s
(K3bDevice::Device) /dev/scd0 : 1411 KB/s
(K3bDevice::Device) /dev/scd0 Invalid DVD speed: 706 KB/s

```

DURING BURNING
```

(K3bDevice::Device) /dev/scd0: GET PERFORMANCE dataLen = 8
(K3bDevice::Device) /dev/scd0: GET PERFORMANCE reports bogus dataLen: 8
(K3bDevice::Device) /dev/scd0:  Number of supported write speeds via 2A: 6
(K3bDevice::Device) /dev/scd0 : 4234 KB/s
(K3bDevice::Device) /dev/scd0 : 3528 KB/s
(K3bDevice::Device) /dev/scd0 : 2822 KB/s
(K3bDevice::Device) /dev/scd0 : 1764 KB/s
(K3bDevice::Device) /dev/scd0 : 1411 KB/s
(K3bDevice::Device) /dev/scd0 Invalid DVD speed: 706 KB/s
(K3bDevice::HalConnection) lock queued for /org/freedesktop/Hal/devices/storage_model_DVD__RW_ND_6650A
(K3bDevice::HalConnection) unlock queued for /org/freedesktop/Hal/devices/storage_model_DVD__RW_ND_6650A
(K3bDevice::ScsiCommand) failed:
                           command:    READ DVD STRUCTURE (ad)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ DVD STRUCTURE length det failed
(K3bDevice::Device) Unable to read DVD structure for num of layers.
DiskInfo:
Mediatype:       DVD+R Dual Layer
Current Profile: DVD+R Dual Layer
Disk state:      empty
Empty:           1
Rewritable:      0
Appendable:      0
Sessions:        0
Tracks:          0
Layers:          2
Capacity:        913:05:21 (LBA 4108896) (8415019008 Bytes)
Remaining size:  913:05:21 (LBA 4108896) (8415019008 Bytes)
Used Size:       00:00:00 (LBA 0) (0 Bytes)
(K3bDevice::Device) /dev/scd0: GET PERFORMANCE dataLen = 8
(K3bDevice::Device) /dev/scd0: GET PERFORMANCE reports bogus dataLen: 8
(K3bDevice::Device) /dev/scd0:  Number of supported write speeds via 2A: 6
(K3bDevice::Device) /dev/scd0 : 4234 KB/s
(K3bDevice::Device) /dev/scd0 : 3528 KB/s
(K3bDevice::Device) /dev/scd0 : 2822 KB/s
(K3bDevice::Device) /dev/scd0 : 1764 KB/s
(K3bDevice::Device) /dev/scd0 : 1411 KB/s
(K3bDevice::Device) /dev/scd0 Invalid DVD speed: 706 KB/s

```

The output From the debug window.
```

System
-----------------------
K3b Version: 1.0.3

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
_NEC DVD+-RW ND-6650A 102C (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite]

Burned media
-----------------------
DVD+R Dual Layer

Used versions
-----------------------
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
/dev/scd0: splitting layers at 2054448 blocks
:-[ SEND DVD+R DOUBLE LAYER RECORDING INFORMATION failed with SK=3h/ASC=02h/ACQ=00h]: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/scd0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:4108868 -dvd-compat -speed=3.1 -overburn -use-the-force-luke=bufsize:32m 

```


Like i said i don't have a lot of tech know how but the line in the trace where it says 
>  (K3bDevice::Device) /dev/scd0 Invalid DVD speed: 706 KB/s
(K3bDevice::DeviceManager) setting current write speed of device /dev/scd0 to 0 
seems suspicious to me. 

Can anyone help or shed some light on this???

 I hope i have given enough info, if not please just say so.

Many thanks in advance.

steve

---

### Post by Phantom Power on 2008-03-20
I appear to be having exactly the same issue as Stevo. I can burn a single layer DVD fine, but my dual layers don't work. I get the same sort of errors as his in the K3b debug window. I've tried Brasero and growisofs with similar results. The discs stay blank, so nothing is getting written at all.

Here's the output of the trace and debug.
[Starting up K3b trace]("http://members.shaw.ca/Project2501/ubuntu/k3b_startup_trace.txt")
[Attempting to burn trace]("http://members.shaw.ca/Project2501/ubuntu/k3b_burn_trace.txt")
[K3B Debug Output]("http://members.shaw.ca/Project2501/ubuntu/k3b_debug_output.txt")

I'm doing this on an HP dv9617nr Laptop. Any help would be greatly appreciated.

---

### Post by stevo82 on 2008-03-24
I have not solved this yet, but after some more digging it may be down to the media after all.  From what i have found there are media codes or MIDs for a dvd and apparently certain drives will only support certain media codes.  And it looks like manufacturers change media codes from time to time, so discs from the same brand may have diff media codes.

I checked the media code of the old working discs and the new ones that don't, using nero drive speed info tool (don't know how to do this under linux), and found that the old ones were in the supported list (RICOHJPND001) and the new ones were not (CMC MAG D02).

I am now going to have to buy some more blank dvds which have a media code that is supported ([http://bigmaggot.co.uk](http://bigmaggot.co.uk) shows the media code of some of the blank dvds) and see if they work.  I'll let you know the result.

for my drive NEC 6650A it looks like only the following MIDs are supported.
MKM 001
RICOHJPNR001
RICOHJPND001
RITEK   D01
PHILIPS CD2 
PRODISC D01

Phantom power i suggest you try search for your dvd drive name and media codes or MIDs and see which ones are supported for your current firmware version ([http://club.cdfreaks.com](http://club.cdfreaks.com) - is where i found my info).

---

### Post by stevo82 on 2008-04-12
It turns out it was the problem with the unsupported media codes as i described in my previous post.  

I have found a fix for this...

I used a tool called MediaCodeSpeedEdit (from [http://ala42.cdfreaks.com/MCSE/]("http://ala42.cdfreaks.com/MCSE/")) and followed the instructions for teaching the firmware a new media code  which replaced one of the existing media codes with the media code of the discs i have.  I then flashed the firmware and hey presto it appears to work.  I have just burnt a disc and it works fine, it even burnt at a higher speed than it is meant to.

The media code that i replaced was MKM - 001-000 with CMC MAG D02.

Just as a note, i used the MSCE tool and flashed the firmware under windows XP (not sure if the tool works under linux).

---

