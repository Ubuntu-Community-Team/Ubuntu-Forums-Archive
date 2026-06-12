---
title: "Detecting partitions/other drives"
date: 2005-05-06
forum: Hardware &amp; Laptops
---

### Post by m3jsh on 2005-05-06
I just moved to Ubuntu from Windows. I have two hard drives. One is 200gb and the other is 40gb. I had a 20gb partition on the 200gb drive for linux. Now the other partition and the other harddrive do not show up in linux. Is it because they're formatted in NTFS? I'm not quite sure what the deal is. Thanks for your help.

---

### Post by nad on 2005-05-06
Where have you looked? What type of drives and what is the physical setup? Is this a new problem that they 'disappeared' or have you never been able to see them with ubuntu? The type of filesystem is not an issue.

---

### Post by m3jsh on 2005-05-06
The last time i used ubuntu was on my laptop, and since that wasn't partitioned there was no problem.

I'm not using ubuntu on my desktop (first day.) They are both Maxtor Drives. I believe you see your other harddrives through /dev/hda1 2 3 etc. Am I wrong in this?

The physical setup? I'm not exactly sure what you mean by this, but I'm going to guess you mean which drive is master? The 200gb is Master and that is the drive that I partitioned.

---

### Post by mohaham on 2005-05-06
i'm assuming  hda1 is the ntfs partition, so u need to manually mount this partition..
this link might help u ..
[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

---

### Post by nad on 2005-05-06
A little bit more slowly, from the begining.

"I'm not using ubuntu on my desktop (first day.)". I don't understand this.

Your ide drives are designated /dev/hda, /dev/hdb, etc. The partitions on the drives are designated /dev/hda1, /dev/hda2, etc. Sata, scsi, and raid drives are noted with other /dev designations.

By physical setup, it would be helpful to know the order of the drives, what file systems (partitions) are installed and where, and your drive controller chipset.

What is the output of the terminal window commands: df -hl  , parted /dev/hda print , lspci .

---

### Post by m3jsh on 2005-05-06
Sorry, I meant "I am now using ubuntu on my desktop."

As you requested, the results to those commands in the terminal:

> 
root@ANJIN:/home/m3jsh # sudo fdisk -l

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2442    19615333+  83  Linux
/dev/hda2            2551       24792   178658865    7  HPFS/NTFS
/dev/hda3            2443        2550      867510    5  Extended
/dev/hda5            2443        2550      867478+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 36.5 GB, 36529274880 bytes
255 heads, 63 sectors/track, 4441 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4440    35664268+   7  HPFS/NTFS


root@ANJIN:/home/m3jsh # df -hl
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              19G  1.9G   16G  11% /
tmpfs                 253M     0  253M   0% /dev/shm
/dev                   19G  1.9G   16G  11% /.dev
none                  5.0M  2.9M  2.2M  57% /dev


root@ANJIN:/home/m3jsh # parted /dev/hda print
Disk geometry for /dev/hda: 0.000-194481.000 megabytes
Disk label type: msdos
Minor    Start       End     Type      Filesystem  Flags
1          0.031  19155.629  primary   ext3        boot
3      19155.630  20002.807  extended
5      19155.661  20002.807  logical   linux-swap
2      20002.808 194474.355  primary   ntfs
Information: Don't forget to update /etc/fstab, if necessary.


root@ANJIN:/home/m3jsh # lspci
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
0000:00:05.0 Multimedia audio controller: nVidia Corporation nForce MultiMedia audio [Via VT82C686B] (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
0000:00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
0000:01:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
0000:01:09.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (rev 04)
0000:01:09.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
0000:01:0b.0 RAID bus controller: Silicon Image, Inc. (formerly CMD Technology Inc) SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
0000:02:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
0000:02:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)
 i

---

### Post by m3jsh on 2005-05-06
[QUOTE=mohaham]i'm assuming  hda1 is the ntfs partition, so u need to manually mount this partition..
this link might help u ..
[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)[/QUOTE]

Awesome, that worked, just one question though:

How can I make it read/write, because it's currently read only and i cannot change it by right-clicking.

---

### Post by m3jsh on 2005-05-06
Ignore this thread now, thanks.

---

