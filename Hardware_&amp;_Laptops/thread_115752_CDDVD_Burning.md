---
title: "CD/DVD Burning"
date: 2006-01-11
forum: Hardware &amp; Laptops
---

### Post by willhurt on 2006-01-11
HI im having problems CD/DVD burning, I can read and play both DVD's and CD's but when i go to burn something onto either of these using nautilis all i can do is write a file image to my hard disk. When i try with Serpentine i get the startup error -  No recording Drive Found.

Im running Ubuntu 5.10 on an Fujitsu-Siemens Amilo-D 1840W, the DVD+RW drive a Ricoh DVD+RW RW8160. Ive looked around a few threads and found some info to post here, i dont really know what it means as im new to Linux but it should be helpful.


the cd-rom specific line in /etc/fstab:

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

this is the DVD related bit when running dmesg in the terminal:

[4294672.630000] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
[4294672.630000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb: DMA
[4294672.630000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd: DMA
[4294672.630000] Probing IDE interface ide0...
[4294672.894000] hda: FUJITSU MHT2080AT, ATA DISK drive
[4294673.202000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294673.202000] Probing IDE interface ide1...
[4294673.874000] hdc: DVD+RW RW8160, ATAPI CD/DVD-ROM drive
[4294674.180000] ide1 at 0x170-0x177,0x376 on irq 15
[4294674.180000] Probing IDE interface ide2...
[4294674.693000] Probing IDE interface ide3...
[4294675.205000] Probing IDE interface ide4...
[4294675.717000] Probing IDE interface ide5...
[4294676.232000] hda: max request size: 128KiB
[4294676.295000] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16 /63, UDMA(33)
[4294676.298000] hda: cache flushes supported
[4294676.298000]  /dev/ide/host0/bus0/target0/lun0: p1 p3 p4 < p5 >
[4294676.329000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 8192kB Cache
[4294676.329000] Uniform CD-ROM driver Revision: 3.20

Its using the Uniforn CD-ROM driver, is there a Uniform DVDRW Driver, and can i install that.

Any help would be ace.
Will

---

### Post by s_p_a_r_k_y on 2006-01-11
I remember back in the day fiddling with ide-scsi, but I believe that has been taken out and things should just work. I would try typing in the model number of your cdrom drive into google with Linux and see what other people have had problems/solutions with it.

---

