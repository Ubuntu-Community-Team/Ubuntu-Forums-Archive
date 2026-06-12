---
title: "mounting floppy drive bump"
date: 2012-04-10
forum: Hardware
---

### Post by edcompsci on 2012-04-10
Can I bump this old thread?
[http://ubuntuforums.org/archive/index.php/t-1050192.html](http://ubuntuforums.org/archive/index.php/t-1050192.html)

My dmesg output is a bit different:

```

progave@Lifebook-S6210:~$ dmesg | grep -e floppy -e fd
[    0.000000] Move RAMDISK from 00000000378a6000 - 0000000037fefefd to 00881000 - 00fcaefd
[    0.521514] PCI: PCI BIOS revision 2.10 entry at 0xfd972, last bus=3
[    0.545121] system 00:01: ioport range 0xfd00-0xfd6f has been reserved
progave@Lifebook-S6210:~$

```Also, trying to mount from pcmanfm:
```

Given device "/org/freedesktop/Hal/devices/storage_serial_MITSUMI2_MITSUMI2" is not a volume or drive

```I tried making a directory of the above:
```

progave@Lifebook-S6210:~$ sudo mkdir /org
progave@Lifebook-S6210:~$ sudo mkdir /org/freedesktop
progave@Lifebook-S6210:~$ sudo mkdir /org/freedesktop/Hal
progave@Lifebook-S6210:~$ sudo mkdir /org/freedesktop/Hal/devices
progave@Lifebook-S6210:~$ cd /org/freedesktop/Hal/devices
progave@Lifebook-S6210:/org/freedesktop/Hal/devices$ sudo mkdir /org/freedesktop/Hal/devices/storage_serial_MITSUMI2_MITSUMI2
progave@Lifebook-S6210:/org/freedesktop/Hal/devices$ sudo mount -t msdos /dev/fd /org/freedesktop/Hal/devices/storage_serial_MITSUMI2_MITSUMI2
mount: /proc/7320/fd is not a block device

```Then I tried making a directory called 7320, thinking maybe I could use the ln command to put either a hard link or symbolic link (I wouldn't know which this early), but got this:
```

progave@Lifebook-S6210:/org/freedesktop/Hal/devices$ ls /proc/7320
ls: cannot access /proc/7320: No such file or directory
progave@Lifebook-S6210:/org/freedesktop/Hal/devices$ cd /proc
progave@Lifebook-S6210:/proc$ cd 7320
bash: cd: 7320: No such file or directory
progave@Lifebook-S6210:/proc$ sudo mkdir 7320
mkdir: cannot create directory `7320': No such file or directory
progave@Lifebook-S6210:/proc$ 

```Can anyone help? This is onn Masonux, a distro of Lubuntu., using Lucid repositories.

---

### Post by edcompsci on 2012-04-10
I retried it but with a blank floppy in it, and it tried to mount the first way again first, then failed then tried again and now I have an accessibe floppy.

---

### Post by edcompsci on 2012-04-11
Now I can't seem to mount it on my desktop machine, running Ubuntu Lucid (not Lubuntu, with Gnome)

```

edward@selfmade-desktop:~$ ls /dev | grep fd
fd
fd0
fd0u1040
fd0u1120
fd0u1440
fd0u1600
fd0u1680
fd0u1722
fd0u1743
fd0u1760
fd0u1840
fd0u1920
fd0u360
fd0u720
fd0u800
fd0u820
fd0u830
edward@selfmade-desktop:~$ sudo umount /dev/fd*
[sudo] password for edward: 
umount: /dev/fd: not mounted
umount: /dev/fd0: not mounted
umount: /dev/fd0u1040: not mounted
umount: /dev/fd0u1120: not mounted
umount: /dev/fd0u1440: not mounted
umount: /dev/fd0u1600: not mounted
umount: /dev/fd0u1680: not mounted
umount: /dev/fd0u1722: not mounted
umount: /dev/fd0u1743: not mounted
umount: /dev/fd0u1760: not mounted
umount: /dev/fd0u1840: not mounted
umount: /dev/fd0u1920: not mounted
umount: /dev/fd0u360: not mounted
umount: /dev/fd0u720: not mounted
umount: /dev/fd0u800: not mounted
umount: /dev/fd0u820: not mounted
umount: /dev/fd0u830: not mounted


```and I can't umount any of them.

Trying dmesg

```

edward@selfmade-desktop:~$ dmesg | grep -e floppy -e fd
[    0.887222] Floppy drive(s): fd0 is 1.44M
[26098.838644] end_request: I/O error, dev fd0, sector 0
[26110.919097] end_request: I/O error, dev fd0, sector 0
[26110.919108] Buffer I/O error on device fd0, logical block 0
[26122.999141] end_request: I/O error, dev fd0, sector 0
[26122.999152] Buffer I/O error on device fd0, logical block 0
[26135.078717] end_request: I/O error, dev fd0, sector 0
[26135.078729] Buffer I/O error on device fd0, logical block 0
[26147.158440] end_request: I/O error, dev fd0, sector 0
[26147.158451] Buffer I/O error on device fd0, logical block 0
[26159.239071] end_request: I/O error, dev fd0, sector 0
[26159.239083] Buffer I/O error on device fd0, logical block 0
[26171.318616] end_request: I/O error, dev fd0, sector 0
[26171.318628] Buffer I/O error on device fd0, logical block 0
[26183.399158] end_request: I/O error, dev fd0, sector 0
[26183.399170] Buffer I/O error on device fd0, logical block 0
[26195.478721] end_request: I/O error, dev fd0, sector 0
[26195.478732] Buffer I/O error on device fd0, logical block 0
[26207.559186] end_request: I/O error, dev fd0, sector 0
[26207.559198] Buffer I/O error on device fd0, logical block 0
[26219.638680] end_request: I/O error, dev fd0, sector 0
[26219.638691] Buffer I/O error on device fd0, logical block 0
[26231.718409] end_request: I/O error, dev fd0, sector 0
[26231.718421] Buffer I/O error on device fd0, logical block 0
[26243.798579] end_request: I/O error, dev fd0, sector 0
[26243.798591] Buffer I/O error on device fd0, logical block 0
[26255.879178] end_request: I/O error, dev fd0, sector 0
[26255.879190] Buffer I/O error on device fd0, logical block 0
[26267.958788] end_request: I/O error, dev fd0, sector 0
[26267.958799] Buffer I/O error on device fd0, logical block 0
[26280.038386] end_request: I/O error, dev fd0, sector 0
[26280.038398] Buffer I/O error on device fd0, logical block 0
[26292.118764] end_request: I/O error, dev fd0, sector 0
[26292.118775] Buffer I/O error on device fd0, logical block 0
[26304.198398] end_request: I/O error, dev fd0, sector 0
[26304.198410] Buffer I/O error on device fd0, logical block 0
[26316.278960] end_request: I/O error, dev fd0, sector 0
[26316.278972] Buffer I/O error on device fd0, logical block 0
[26328.358544] end_request: I/O error, dev fd0, sector 0
[26328.358556] Buffer I/O error on device fd0, logical block 0
[26340.439149] end_request: I/O error, dev fd0, sector 0
[26340.439161] Buffer I/O error on device fd0, logical block 0
[26352.518914] end_request: I/O error, dev fd0, sector 0
[26352.518926] Buffer I/O error on device fd0, logical block 0
[26364.598599] end_request: I/O error, dev fd0, sector 0
[26364.598611] Buffer I/O error on device fd0, logical block 0
[26376.678919] end_request: I/O error, dev fd0, sector 0
[26376.678929] Buffer I/O error on device fd0, logical block 0
[26388.758394] end_request: I/O error, dev fd0, sector 0
[26388.758404] Buffer I/O error on device fd0, logical block 0
[26400.838981] end_request: I/O error, dev fd0, sector 0
[26400.838992] Buffer I/O error on device fd0, logical block 0
[26412.919319] end_request: I/O error, dev fd0, sector 0
[26412.919331] Buffer I/O error on device fd0, logical block 0
[26424.998937] end_request: I/O error, dev fd0, sector 0
[26424.998950] Buffer I/O error on device fd0, logical block 0
[26437.078724] end_request: I/O error, dev fd0, sector 0
[26437.078735] Buffer I/O error on device fd0, logical block 0
[26449.159306] end_request: I/O error, dev fd0, sector 0
[26449.159318] Buffer I/O error on device fd0, logical block 0
[26461.238460] end_request: I/O error, dev fd0, sector 0
[26461.238472] Buffer I/O error on device fd0, logical block 0
[26473.319148] end_request: I/O error, dev fd0, sector 0
[26473.319160] Buffer I/O error on device fd0, logical block 0
[26485.399311] end_request: I/O error, dev fd0, sector 0
[26485.399324] Buffer I/O error on device fd0, logical block 0
[26497.479047] end_request: I/O error, dev fd0, sector 0
[26497.479059] Buffer I/O error on device fd0, logical block 0
[26509.558665] end_request: I/O error, dev fd0, sector 0
[26509.558677] Buffer I/O error on device fd0, logical block 0
[26521.638950] end_request: I/O error, dev fd0, sector 0
[26521.638962] Buffer I/O error on device fd0, logical block 0
[26533.718494] end_request: I/O error, dev fd0, sector 0
[26533.718506] Buffer I/O error on device fd0, logical block 0
[26545.799135] end_request: I/O error, dev fd0, sector 0
[26545.799147] Buffer I/O error on device fd0, logical block 0
[26557.879267] end_request: I/O error, dev fd0, sector 0
[26557.879279] Buffer I/O error on device fd0, logical block 0
[26569.958453] end_request: I/O error, dev fd0, sector 0
[26569.958466] Buffer I/O error on device fd0, logical block 0
[26582.039066] end_request: I/O error, dev fd0, sector 0
[26582.039077] Buffer I/O error on device fd0, logical block 0
[26594.118468] end_request: I/O error, dev fd0, sector 0
[26606.199327] end_request: I/O error, dev fd0, sector 0
[26618.288701] end_request: I/O error, dev fd0, sector 0
[26630.369260] end_request: I/O error, dev fd0, sector 0
[26642.448740] end_request: I/O error, dev fd0, sector 0
[26642.448751] Buffer I/O error on device fd0, logical block 0
[26654.528589] end_request: I/O error, dev fd0, sector 0
[26654.528601] Buffer I/O error on device fd0, logical block 0
[26666.608513] end_request: I/O error, dev fd0, sector 0
[26666.608525] Buffer I/O error on device fd0, logical block 0
[26678.688339] end_request: I/O error, dev fd0, sector 0
[26678.688351] Buffer I/O error on device fd0, logical block 0
[26690.769340] end_request: I/O error, dev fd0, sector 0
[26690.769352] Buffer I/O error on device fd0, logical block 0
[26702.848967] end_request: I/O error, dev fd0, sector 0
[26702.848979] Buffer I/O error on device fd0, logical block 0
[26714.928533] end_request: I/O error, dev fd0, sector 0
[26714.928546] Buffer I/O error on device fd0, logical block 0
[26727.009259] end_request: I/O error, dev fd0, sector 0
[26727.009270] Buffer I/O error on device fd0, logical block 0
[26739.088966] end_request: I/O error, dev fd0, sector 0
[26739.088978] Buffer I/O error on device fd0, logical block 0
[26751.168608] end_request: I/O error, dev fd0, sector 0
[26751.168619] Buffer I/O error on device fd0, logical block 0
[26760.460109]  ffff8800a9f93198 ffff880093003fd8 0000000000015c00 ffff8800a9f92de0
[26760.460114]  0000000000015c00 ffff880093003fd8 0000000000015c00 ffff8800a9f93198
[26760.460200]  [<ffffffff8115eb2a>] ? alloc_fd+0x10a/0x150
[26763.248570] end_request: I/O error, dev fd0, sector 0
[26763.248582] Buffer I/O error on device fd0, logical block 0
[26775.328426] end_request: I/O error, dev fd0, sector 0
[26775.328439] Buffer I/O error on device fd0, logical block 0
[26787.409155] end_request: I/O error, dev fd0, sector 0
[26787.409167] Buffer I/O error on device fd0, logical block 0
[26799.488353] end_request: I/O error, dev fd0, sector 0
[26799.488366] Buffer I/O error on device fd0, logical block 0
[26811.568852] end_request: I/O error, dev fd0, sector 0
[26811.568864] Buffer I/O error on device fd0, logical block 0
[26823.650173] end_request: I/O error, dev fd0, sector 0
[26823.650185] Buffer I/O error on device fd0, logical block 0
[26835.728945] end_request: I/O error, dev fd0, sector 0
[26835.728957] Buffer I/O error on device fd0, logical block 0
[26847.808570] end_request: I/O error, dev fd0, sector 0
[26847.808582] Buffer I/O error on device fd0, logical block 0
[26859.889129] end_request: I/O error, dev fd0, sector 0
[26859.889141] Buffer I/O error on device fd0, logical block 0
[26871.969348] end_request: I/O error, dev fd0, sector 0
[26871.969360] Buffer I/O error on device fd0, logical block 0
[26880.460119]  ffff8800a9f93198 ffff880093003fd8 0000000000015c00 ffff8800a9f92de0
[26880.460123]  0000000000015c00 ffff880093003fd8 0000000000015c00 ffff8800a9f93198
[26880.460210]  [<ffffffff8115eb2a>] ? alloc_fd+0x10a/0x150
[26880.460240]  ffff880006f983b8 ffff88004065bfd8 0000000000015c00 ffff880006f98000
[26880.460244]  0000000000015c00 ffff88004065bfd8 0000000000015c00 ffff880006f983b8
[26880.460298]  [<ffffffffa0001fa1>] floppy_open+0x41/0x3c0 [floppy]
[26880.460334]  [<ffffffff8115eb2a>] ? alloc_fd+0x10a/0x150
[26884.048565] end_request: I/O error, dev fd0, sector 0
[26884.048577] Buffer I/O error on device fd0, logical block 0
[26896.129253] end_request: I/O error, dev fd0, sector 0
[26896.129264] Buffer I/O error on device fd0, logical block 0
[26908.209055] end_request: I/O error, dev fd0, sector 0
[26908.209067] Buffer I/O error on device fd0, logical block 0
[26920.288730] end_request: I/O error, dev fd0, sector 0
[26920.288742] Buffer I/O error on device fd0, logical block 0
[26932.368727] end_request: I/O error, dev fd0, sector 0
[26932.368739] Buffer I/O error on device fd0, logical block 0
[26944.454070] end_request: I/O error, dev fd0, sector 0
[26944.454081] Buffer I/O error on device fd0, logical block 0
[26956.539196] end_request: I/O error, dev fd0, sector 0
[26956.539206] Buffer I/O error on device fd0, logical block 0
[26968.643909] end_request: I/O error, dev fd0, sector 0
[26968.643922] Buffer I/O error on device fd0, logical block 0
[26980.730413] end_request: I/O error, dev fd0, sector 0
[26980.730423] Buffer I/O error on device fd0, logical block 0
[26992.809388] end_request: I/O error, dev fd0, sector 0
[26992.809401] Buffer I/O error on device fd0, logical block 0
[27000.460403]  ffff8800a9f93198 ffff880093003fd8 0000000000015c00 ffff8800a9f92de0
[27000.460407]  0000000000015c00 ffff880093003fd8 0000000000015c00 ffff8800a9f93198
[27000.460501]  [<ffffffff8115eb2a>] ? alloc_fd+0x10a/0x150
[27000.460532]  ffff880006f983b8 ffff88004065bfd8 0000000000015c00 ffff880006f98000
[27000.460536]  0000000000015c00 ffff88004065bfd8 0000000000015c00 ffff880006f983b8
[27000.460597]  [<ffffffffa0001fa1>] floppy_open+0x41/0x3c0 [floppy]
[27000.460633]  [<ffffffff8115eb2a>] ? alloc_fd+0x10a/0x150
[27004.888675] end_request: I/O error, dev fd0, sector 0
[27004.888685] Buffer I/O error on device fd0, logical block 0
[27016.968481] end_request: I/O error, dev fd0, sector 0
[27016.968491] Buffer I/O error on device fd0, logical block 0
[27029.049162] end_request: I/O error, dev fd0, sector 0
[27029.049172] Buffer I/O error on device fd0, logical block 0
[27041.129099] end_request: I/O error, dev fd0, sector 0
[27041.129109] Buffer I/O error on device fd0, logical block 0
[27053.208472] end_request: I/O error, dev fd0, sector 0
[27053.208487] Buffer I/O error on device fd0, logical block 0
[27065.288659] end_request: I/O error, dev fd0, sector 0
[27065.288671] Buffer I/O error on device fd0, logical block 0
[27077.369185] end_request: I/O error, dev fd0, sector 0
[27077.369197] Buffer I/O error on device fd0, logical block 0
[27089.448523] end_request: I/O error, dev fd0, sector 0
[27089.448536] Buffer I/O error on device fd0, logical block 0
[27101.538593] end_request: I/O error, dev fd0, sector 0
[27101.538606] Buffer I/O error on device fd0, logical block 0
[27113.618752] end_request: I/O error, dev fd0, sector 0
[27113.618765] Buffer I/O error on device fd0, logical block 0
[27120.460157]  ffff8800a9f93198 ffff880093003fd8 0000000000015c00 ffff8800a9f92de0
[27120.460161]  0000000000015c00 ffff880093003fd8 0000000000015c00 ffff8800a9f93198
[27120.460248]  [<ffffffff8115eb2a>] ? alloc_fd+0x10a/0x150
[27120.460278]  ffff880006f983b8 ffff88004065bfd8 0000000000015c00 ffff880006f98000
[27120.460282]  0000000000015c00 ffff88004065bfd8 0000000000015c00 ffff880006f983b8
[27120.460334]  [<ffffffffa0001fa1>] floppy_open+0x41/0x3c0 [floppy]
[27120.460370]  [<ffffffff8115eb2a>] ? alloc_fd+0x10a/0x150
[27120.460398]  ffff88001c004888 ffff8800a86bdfd8 0000000000015c00 ffff88001c0044d0
[27120.460402]  0000000000015c00 ffff8800a86bdfd8 0000000000015c00 ffff88001c004888
[27120.460465]  [<ffffffff8115eb2a>] ? alloc_fd+0x10a/0x150
[27125.709306] end_request: I/O error, dev fd0, sector 0
[27137.789164] end_request: I/O error, dev fd0, sector 0
[27149.888864] end_request: I/O error, dev fd0, sector 0
[27162.298836] end_request: I/O error, dev fd0, sector 0
[27180.708898] end_request: I/O error, dev fd0, sector 0
[27231.948543] end_request: I/O error, dev fd0, sector 0
edward@selfmade-desktop:~$ 

```Trying to mount from Nautilus:
```

Unable to mount location

No media in the drive


```Interesting that with the write protect slid on or off, trying to mount from terminal still says write-protect is on:
```

edward@selfmade-desktop:~$ sudo mount -t msdos /dev/fd0 /media/floppy 
mount: block device /dev/fd0 is write-protected, mounting read-only
mount: /dev/fd0: can't read superblock
edward@selfmade-desktop:~$ sudo mount -t msdos /dev/fd0 /media/floppy
mount: block device /dev/fd0 is write-protected, mounting read-only
mount: /dev/fd0: can't read superblock
edward@selfmade-desktop:~$ 

```

Trying with parted:
```

edward@selfmade-desktop:~$ sudo parted /dev/fd0
Warning: Unable to open /dev/fd0 read-write (Read-only file system).  /dev/fd0
has been opened read-only.
Warning: Unable to open /dev/fd0 read-write (Read-only file system).  /dev/fd0
has been opened read-only.
GNU Parted 2.2
Using /dev/fd0
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) mktable fat16                                                    
parted: invalid token: fat16
New disk label type? help                                                 
parted: invalid token: help
New disk label type? msdos                                                
Error: Input/output error during read on /dev/fd0                         
Retry/Ignore/Cancel? r                                                    
Error: Input/output error during read on /dev/fd0      (after sliding write-protect)                   
Retry/Ignore/Cancel?    

```

---

