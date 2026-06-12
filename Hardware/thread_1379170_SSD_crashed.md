---
title: "SSD crashed"
date: 2010-01-12
forum: Hardware
---

### Post by fitzefitzefatze on 2010-01-12
Hello,

my Solidata SSD crashed. It has a 64 GB capacity but now in *gparted* 128 GB are shown. I have no more partitions and no partition table. I also have no possibility to create a new one. I tried this with *sfdisk*, *fdisk*, ... Moreover the disk is not always recognized by the system (Jaunty Live CD). 
I tried to write nulls on the disk by
```

dd if=/dev/zero of=/dev/sdb bs=128k

```

which worked, but it wrote 128 GB although the disk actually only has 64 Gb. So I'm not sure if *dd* really "deleted" all/most sectors on the disk and I wrote /dev/sdb by *dd* again into a file, which I regarded with the *Bless* Hex-editor. The file consists of the code like (which is part of GRUB I guess: [http://ubuntuforums.org/showthread.php?t=1120321):](http://ubuntuforums.org/showthread.php?t=1120321):)

```

00000000  5a 0c ff 3f 37 c8 10 00  00 00 00 00 3f 00 00 00  |Z..?7.......?...|
00000010  00 00 00 00 31 30 33 32  35 34 37 36 39 38 62 61  |....1032547698ba|
00000020  66 63 30 63 34 35 36 39  00 00 00 08 00 30 30 30  |fc0c4569.....000|
00000030  50 2e 30 38 20 20 41 59  41 54 44 50 4e 4f 20 47  |P.08  AYATDPNO G|
00000040  41 42 45 52 4f 46 54 4f  52 2d 4d 4f 20 20 20 20  |ABEROFTOR-MO    |
00000050  20 20 20 20 20 20 20 20  20 20 20 20 20 20 10 80  |              ..|
00000060  00 00 00 2f 00 40 00 02  00 02 07 00 ff 3f 10 00  |.../.@.......?..|
00000070  3f 00 10 fc fb 00 10 01  00 00 00 10 00 00 07 00  |?...............|
00000080  03 00 78 00 78 00 78 00  78 00 00 00 00 00 00 00  |..x.x.x.x.......|
00000090  00 00 00 00 00 00 01 00  06 07 00 00 00 00 00 00  |................|
000000a0  e0 00 00 00 20 40 00 44  00 40 20 40 00 04 00 40  |.... @.D.@ @...@|
000000b0  3f 40 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |?@..............|
000000c0  00 00 00 00 00 00 00 00  00 00 00 10 00 00 00 00  |................|
000000d0  00 00 00 00 00 40 00 00  00 00 00 00 00 00 00 00  |.....@..........|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 a5 45  |...............E|
00000200

```

which repeats constantly every 512 characters. Why is that? I know that the first 512 byte of every disk are the MBR but not 2^32/512 times? Is it possible that dd ran into a loop so that it only wrote the MBR again and again? Or can I be sure that this file is really an image of my disk. The whole file has 128 GB but only 2^32 can be shown in *Bless*.

I just want the disk to be empty/unreadable because I can get a new one by warranty. But the files on the disk are business data which should not travel around the world. How can I be sure that the data is destroyed? 

Thanks for any help.

---

