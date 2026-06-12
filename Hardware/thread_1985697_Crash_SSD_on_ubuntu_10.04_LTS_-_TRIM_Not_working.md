---
title: "Crash SSD on ubuntu 10.04 LTS - TRIM Not working"
date: 2012-05-23
forum: Hardware
---

### Post by themaxxx on 2012-05-23
Hi guys,

i have a disk SSD  Kingston ssdNow 50 S in ubuntu 10.04 LTS.

I am experiencing crash problems in the file system and then I passed the partition to read only. To retrieve this requires a reboot. I was reading a bit and I find that better performance is needed TRIM.


i try install the kernel  2.6.35 on 10.04 lts with this commands:

sudo apt-get update && sudo apt-get install linux-image-generic-lts-backport-maverick linux-headers-generic-lts-backport-maverick

The installation was accomplished successfully, I set the "discard" in fstab and I used hdparm to check if realiemente TRIM is activated, but unfortunately the results I get is that I have not activated.

i followed these instruccion to set TRIM:

[https://sites.google.com/site/lightrush/random-1/howtoconfigureext4toenabletrimforssdsonubuntu](https://sites.google.com/site/lightrush/random-1/howtoconfigureext4toenabletrimforssdsonubuntu)

[https://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking](https://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking)


[B]here the results:
[/B]
1+0 records in
1+0 records out
52428800 bytes (52 MB) copied, 13.0756 s, 4.0 MB/s

tempfile: underlying filesystem: blocksize 4096, begins at LBA 2048; assuming 512 byte sectors
 byte_offset  begin_LBA    end_LBA    sectors
           0    7702528    7718911      16384
     8388608    7768064    7854079      86016

/dev/sda:
reading sector 7768064: succeeded
bbfd 0687 a4b2 1dae 765b 0c37 2290 6e3d
7f55 eb68 9f7d 090d 9b04 d62f b47a 775e
d66a 63d4 6fc2 2e38 be3d c52e e0f8 4424
937a 30a7 0fe0 dbba 56d6 1e81 ae79 64ff
f835 d1b7 9c3b 3bcc 2cc1 844e 6fc6 40db
199d 70be 3027 b3a2 5031 3668 6e1d 3539
a8ab 24a5 dd95 c79f 1a6a 7ee4 8dbb b5d7
0da8 bb5a 3400 a5cc 7477 1459 ea56 93ea
7963 16dd 9e27 4982 7048 f838 6913 698f
b123 e98f ea83 f3f8 6da4 9486 2cc0 ca1e
6a76 f5dd 10b2 983f b4bd ea02 7318 22df
eef8 5a08 e6be bf3c 5f18 e7ad 1eeb 20b4
1a00 0c03 f207 6696 9341 ddc8 f344 6658
dc7b b8a8 b323 4d67 60a2 72ad 8360 83da
35a0 ee8f ea74 9030 72f9 dcdc 561a 1b81
54e2 e0e7 d8e8 4659 b1ae f788 b126 5d06
f945 67d6 33ff 544c c8c6 683d 4aff faed
f625 2d1d 7c00 c394 7598 4731 200f 234a
2a85 65a7 bcc1 e07a 2c32 2ec0 58f2 1917
a9c0 2ed0 1ed3 16b9 36f8 d2e5 b188 cca8
3a4e 1906 bd68 3da1 c9aa 0b31 8fd3 a091
42b6 d8fb 2c0c 175a e620 24d3 fb7e 36a3
97ae b93f 8bad 2534 d361 8c2f 996f c113
ad4a 8869 1d6d ac00 6de2 df8c 059d ba2b
c698 3167 0bdf 282d 2beb 1d9b a6ac a3a1
9b58 8f10 b101 9c10 c95f 0e69 7695 da79
9e19 0cb4 75d2 2a81 9f2b d1c1 efff 92c9
e495 6e71 e9c8 5170 fdb9 1fcb 8210 a4a6
e632 af30 2287 9254 829a d2ce ffda df6a
db12 6341 4ad9 6798 d8d5 3531 f63f 89c5
26ff c5a7 163d 6847 5c84 c191 9254 36ea
9ff2 fe2c b704 29ae 1e0a 3037 835a 5c27

This is a sector of the file. It should have been successfully read
and show a bunch of random data.

Press any key to continue...

File deleted. Sleeping for 120 seconds before re-reading the sector.
If TRIM is working, you should see all 0s now.


/dev/sda:
reading sector 7768064: succeeded
bbfd 0687 a4b2 1dae 765b 0c37 2290 6e3d
7f55 eb68 9f7d 090d 9b04 d62f b47a 775e
d66a 63d4 6fc2 2e38 be3d c52e e0f8 4424
937a 30a7 0fe0 dbba 56d6 1e81 ae79 64ff
f835 d1b7 9c3b 3bcc 2cc1 844e 6fc6 40db
199d 70be 3027 b3a2 5031 3668 6e1d 3539
a8ab 24a5 dd95 c79f 1a6a 7ee4 8dbb b5d7
0da8 bb5a 3400 a5cc 7477 1459 ea56 93ea
7963 16dd 9e27 4982 7048 f838 6913 698f
b123 e98f ea83 f3f8 6da4 9486 2cc0 ca1e
6a76 f5dd 10b2 983f b4bd ea02 7318 22df
eef8 5a08 e6be bf3c 5f18 e7ad 1eeb 20b4
1a00 0c03 f207 6696 9341 ddc8 f344 6658
dc7b b8a8 b323 4d67 60a2 72ad 8360 83da
35a0 ee8f ea74 9030 72f9 dcdc 561a 1b81
54e2 e0e7 d8e8 4659 b1ae f788 b126 5d06
f945 67d6 33ff 544c c8c6 683d 4aff faed
f625 2d1d 7c00 c394 7598 4731 200f 234a
2a85 65a7 bcc1 e07a 2c32 2ec0 58f2 1917
a9c0 2ed0 1ed3 16b9 36f8 d2e5 b188 cca8
3a4e 1906 bd68 3da1 c9aa 0b31 8fd3 a091
42b6 d8fb 2c0c 175a e620 24d3 fb7e 36a3
97ae b93f 8bad 2534 d361 8c2f 996f c113
ad4a 8869 1d6d ac00 6de2 df8c 059d ba2b
c698 3167 0bdf 282d 2beb 1d9b a6ac a3a1
9b58 8f10 b101 9c10 c95f 0e69 7695 da79
9e19 0cb4 75d2 2a81 9f2b d1c1 efff 92c9
e495 6e71 e9c8 5170 fdb9 1fcb 8210 a4a6
e632 af30 2287 9254 829a d2ce ffda df6a
db12 6341 4ad9 6798 d8d5 3531 f63f 89c5
26ff c5a7 163d 6847 5c84 c191 9254 36ea
9ff2 fe2c b704 29ae 1e0a 3037 835a 5c27

If the sector isn't filled with 0s, something is wrong with your
configuration. Try googling for "TRIM SSD Linux".

---

### Post by themaxxx on 2012-06-21
no idea? :;(

---

### Post by Redblade20XX on 2012-06-21
Try this test: [http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2](http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2)

And post the results.

-Red

---

