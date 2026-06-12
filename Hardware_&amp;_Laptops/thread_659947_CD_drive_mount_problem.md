---
title: "CD drive mount problem"
date: 2008-01-06
forum: Hardware &amp; Laptops
---

### Post by bramberg on 2008-01-06
I am running Ubuntu 7.10 Gutsy Gibbon on a Sony Vaio Laptop. Under Computer my CD / DVD drive shows up as a CD-RW/DVD+-RW Drive and under properties the model is recognized correctly as model DVD RW DW-U50A. The problem is that when I insert any CD or DVD into the drive I get the following message: Unable to mount media. There is probably no media in the drive. Any idea what to look for or how to fix this problem?

---

### Post by Travisher on 2008-01-06
I'm seeing the same problem on two machines that were both able to play and burn DVDs and CDs when I set them up. Some automatic update has broken them both. Any help with this would be gratefully received.

 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux
Gutsy Gibbon 7.10
lshw gives;
              *-cdrom
                   description: DVD-RAM writer
                   product: ATAPI DVD A DH20A3P
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   version: XP5T
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: mode=udma4 status=nodisc
but there is a disk in there,  It worked until some time in the last few weeks, sorry can't be more precise than that as these machines are used by other people.

---

### Post by bramberg on 2008-01-07
I can confirm that I had the same situation; the CD / DVD drive was working after installation of  Ubuntu, but then stoped to work. Possibly some update has imposed this problem.

---

### Post by Bigdeath on 2008-01-22
Same here. I had Ubuntu Studio Fiesty and now under gutsy something has broken it somewhere along the road.

---

### Post by Bigdeath on 2008-02-14
anyone?

---

### Post by wirawan0 on 2008-02-15
Why don't you report this problem to Ubuntu bug report system? I think that is a better place to receive response, since apparently more people are having problem.

Now I also am having problem with playing DVD with my Sony VAIO laptop under Ubuntu 7.10. I have been keeping the OS up-to-date, so whatever you suffered because of Ubuntu update might have been the cause of this problem, too. When it played DVD, suddenly (at a random moment which I cannot pinpoint) it stopped. The computer is still working, but with dmesg messages like these show up:

> 
[ 6393.512000] UDF-fs: Partition marked readonly; forcing readonly mount
[ 6393.580000] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'W07 PJT 07', timestamp 2007/12/27 23:53 (1ed4)
[ 8133.332000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[ 8133.332000] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[ 8133.332000] ide: failed opcode was: unknown
[ 8140.156000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[ 8140.156000] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[ 8140.156000] ide: failed opcode was: unknown
[ 8146.980000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[ 8146.980000] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[ 8146.980000] ide: failed opcode was: unknown
[ 8153.804000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[ 8153.804000] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[ 8153.804000] ide: failed opcode was: unknown
[ 8153.804000] hdc: DMA disabled
[ 8153.808000] hdc: ide_intr: huh? expected NULL handler on exit
[ 8154.428000] hdc: ATAPI reset complete


The first two lines are from the detection of the DVD; they are fine. Lines 3 onward (starting at time marker 8133.332) shows the problem. The DVD was OK if it is read with another laptop (which runs Ubuntu 7.04, by the way). 

The dmesg output from lines 3 onward is repeated many, many times until I killed the DVD player (either vlc or totem) and ejected the DVD.

I don't have the VAIO laptop with me right now--but it is a Sony PCG-FXA53, a model from year 2002.

The reason I did not submit a bug report yet is because under Windows XP this problem seems to also be there. I was suspecting whether there is a bug with the DVD drive firmware. It is recognized by Linux as:

   UJDA720 DVD/CDRW, ATAPI CD/DVD-ROM drive

Anyway...I don't have the answer, but just to add more to the questions. Maybe we could figure out the problem if it is given sufficient repetition.

Wirawan

---

