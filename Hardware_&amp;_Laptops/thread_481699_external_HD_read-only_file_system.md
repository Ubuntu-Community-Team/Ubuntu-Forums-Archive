---
title: "external HD: read-only file system"
date: 2007-06-22
forum: Hardware &amp; Laptops
---

### Post by xinelo on 2007-06-22
Hi!

I'm having a problem with an external hard drive. I recently upgraded to Feist (I don't think this is related) and my system crashed while I was copying some files from the laptop's hard drive to the external HD. I think this is what might have caused the problem: something was left half copied when the system shut down.

The thing is now I can't write anymore to the external HD. It says "read-only file system". I've searched the forums and the Internet and did all the things other users suggested to had a similar problem. However, nothing seemed to work.

I noticed something else. Before, my external HD used to be /dev/sda1 and mounted to /media/SDA1. Now it keeps mouting to the same volume but it seems to be /dev/sdb1, whereas /dev/sda1 is now what used to be /dev/hda1, that is /. Weird.

We can see below the output of the commands df -h, fdisk -l, lsusb, mount, fsck and the file fstab. If you need to see another file or output of a command, please let me know. The output of fsck includes some questions: I'm not sure my replies were the good ones (you can see them below) because I didn't really understand the questions.

Any suggestion would be very appreciated.

souto@micho:~$ df -h
S. fitxers            Tamany En ús Lliure %Ús Muntat a
/dev/sda1              36G   22G   13G  64% /
varrun                252M  100K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb            252M  140K  252M   1% /proc/bus/usb
udev                  252M  140K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   33M  219M  14% /lib/modules/2.6.20-16-generic/volatile
/dev/sdb1             154G  148G  6,1G  97% /media/SDA1

souto@micho:~$ sudo umount /dev/sdb1

souto@micho:~$ lsof | grep /dev/sda1

souto@micho:~$ fdisk -l

Disc /dev/sdb: 164.6 GiB, 164696556032 octets
255 capçals, 63 sectors/pista, 20023 cilindres
Unitats = cilindres de 16065 * 512 = 8225280 octets
Dispositiu Arrenc.   Comença       Acaba    Blocs    Id  Sistema
/dev/sdb1   *           1       20023   160834716    6  FAT16

souto@micho:~$ sudo lsusb
Password:
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 046d:c01b Logitech, Inc. MX310 Optical Mouse
Bus 002 Device 004: ID 059b:0177 Iomega Corp.
Bus 002 Device 003: ID 04a9:1056 Canon, Inc. BJC-2110 Color Printer
Bus 002 Device 002: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

souto@micho:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=81c1baa6-b377-4c2e-ba0a-b9caf551e27d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=2cddca4f-8ff5-4ad3-bee8-32270e59ffe9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

souto@micho:~$ mount
/dev/sda1 on / type ext3 (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb1 on /media/SDA1 type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)

In next post I'll include the output of fsck.

Thanks a lot, xinelo

---

### Post by xinelo on 2007-06-22
I've modified some characters (such as colon + parenthesis) in order not to get smilies.

souto@micho:~$ fsck /dev/sdb1
fsck 1.40-WIP (14-Nov-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset: original/backup)
  65:01/00
1) Copy original to backup
2) Copy backup to original
3) No action
? 2
FATs differ but appear to be intact. Use which FAT ?
1) Use first FAT
2) Use second FAT
? 1
/dell2mac/Palast Orchester (Max Raabe Gecoverte Moderne Hits) Full Album + Cover.rar_FILES
  Contains a free cluster (1364884). Assuming EOF.
Orphaned long file name part "ison.mp3"
1: Delete.
2: Leave it.
? 1
/dell2mac/Nouvelle Vague - Versions originales - Joy Division, Depeche Mode, Clash, PIL, Killing Joke, etc.rar_FILES/13 - The Specials - Friday Night, Saturday Morning.mp3  and
/dell2mac/Nouvelle Vague - Versions originales - Joy Division, Depeche Mode, Clash, PIL, Killing Joke, etc.rar_FILES/13 - The Specials - Friday Night, Saturday Morning (reaggae).mp3
  share clusters.
1) Truncate first to 0 bytes
2) Truncate second to 0 bytes
? 2
/dell2mac/Nouvelle Vague - Versions originales - Joy Division, Depeche Mode, Clash, PIL, Killing Joke, etc.rar_FILES/13 - The Specials - Friday Night, Saturday Morning (reaggae).mp3
  File size is 3433248 bytes, cluster chain length is 0 bytes.
  Truncating file to 0 bytes.
Reserved field in VFAT long filename slot is not 0 (but 0x08 ).
1: Fix.
2: Leave it.
? 1
Start cluster field in VFAT long filename slot is not 0 (but 0xe24c).
1: Fix.
2: Leave it.
? 1
Unfinished long file name ":6rO: DqC:302:6gl:ARD:4MD:6Qo:04b:9Nb:ERV:0D1:9+s:31s".
  (Start may have been overwritten by `xx3x.+/.x(
1: Delete LFN
2: Leave it as it is.
3: Fix numbering (truncates long name and attaches it to short name `xx3x.+/.x(
? 3
Wrong checksum for long file name ":6rO: DqC:302:6gl:ARD:4MD:6Qo:04b:9Nb:ERV:0D1:9+s:31s".
  (Short name `xx3x.+/.x(x may have changed without updating the long name)
1: Delete LFN
2: Leave it as it is.
3: Fix checksum (attaches to short name `xx3x.+/.x(
? 3
Long filename fragment ":CA+:9q7:AwQ:Bg5:41q:46x: DUH:4WN:103:30x" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
1: Delete fragment
2: Leave it as it is.
3: Set start bit
? 3
Reserved field in VFAT long filename slot is not 0 (but 0x1a).
1: Fix.
2: Leave it.
? 1
Start cluster field in VFAT long filename slot is not 0 (but 0x2639).
1: Fix.
2: Leave it.
? 1
Unfinished long file name ":CA+:9q7:AwQ:Bg5:41q:46x: DUH:4WN:103:30x".
  (Start may have been overwritten by $xq\025xhx\005.\226n\002)
1: Delete LFN
2: Leave it as it is.
3: Fix numbering (truncates long name and attaches it to short name $xq\025xhx\005.\226n\002)
? 3
Wrong checksum for long file name ":CA+:9q7:AwQ:Bg5:41q:46x: DUH:4WN:103:30x".
  (Short name $xq\025xhx\005.\226n\002 may have changed without updating the long name)
1: Delete LFN
2: Leave it as it is.
3: Fix checksum (attaches to short name $xq\025xhx\005.\226n\002)
?
3
Invalid input.
? 3
Long filename fragment ":Bh9:1YF: DQq:6Cc:3F2:4Ge:67H:9E9:99b:C4T:FQe:9Qe:0yF" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
1: Delete fragment
2: Leave it as it is.
3: Set start bit
? 3
Reserved field in VFAT long filename slot is not 0 (but 0x11).
1: Fix.
2: Leave it.
? 1
Start cluster field in VFAT long filename slot is not 0 (but 0x0e13).
1: Fix.
2: Leave it.
? 1
Unfinished long file name ":Bh9:1YF: DQq:6Cc:3F2:4Ge:67H:9E9:99b:C4T:FQe:9Qe:0yF".
  (Start may have been overwritten by '\201xxxx|\177.\0271\217)
1: Delete LFN
2: Leave it as it is.
3: Fix numbering (truncates long name and attaches it to short name '\201xxxx|\177.\0271\217)
? 3
Wrong checksum for long file name ":Bh9:1YF: DQq:6Cc:3F2:4Ge:67H:9E9:99b:C4T:FQe:9Qe:0yF".
  (Short name '\201xxxx|\177.\0271\217 may have changed without updating the long name)
1: Delete LFN
2: Leave it as it is.
3: Fix checksum (attaches to short name '\201xxxx|\177.\0271\217)
? 3
/dell2mac/Pet_Shop_Boys-Fundamental-(Special_Edition)-2CD-2006-VOiCE
  Has a large number of bad entries. (937/1004)
Drop directory ? (y/n) y
Long filename fragment ":0bi:Cdf:5ep:1MM: DCT:AcI:8+G:2Gt:AJX:EMH:745:Fa1:A0F" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
1: Delete fragment
2: Leave it as it is.
3: Set start bit
? 3
Reserved field in VFAT long filename slot is not 0 (but 0x0c).
1: Fix.
2: Leave it.
? 1
Start cluster field in VFAT long filename slot is not 0 (but 0x944f).
1: Fix.
2: Leave it.
? 1
Unfinished long file name ":0bi:Cdf:5ep:1MM: DCT:AcI:8+G:2Gt:AJX:EMH:745:Fa1:A0F".
  (Start may have been overwritten by \221U\236\236\215x)x.\027J])
1: Delete LFN
2: Leave it as it is.
3: Fix numbering (truncates long name and attaches it to short name \221U\236\236\215x)x.\027J])
? 3
Wrong checksum for long file name ":0bi:Cdf:5ep:1MM: DCT:AcI:8+G:2Gt:AJX:EMH:745:Fa1:A0F".
  (Short name \221U\236\236\215x)x.\027J] may have changed without updating the long name)
1: Delete LFN
2: Leave it as it is.
3: Fix checksum (attaches to short name \221U\236\236\215x)x.\027J])
? 3
Long filename fragment ":3FQ:A8Z:100:9gA:8ZG:6i1:A50:1HL:3e9:Eo9:1KD:8Ws:BnI" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
1: Delete fragment
2: Leave it as it is.
3: Set start bit
? 3
Reserved field in VFAT long filename slot is not 0 (but 0x09).
1: Fix.
2: Leave it.
? 1
Start cluster field in VFAT long filename slot is not 0 (but 0x860b).
1: Fix.
2: Leave it.
? 1
Unfinished long file name ":3FQ:A8Z:100:9gA:8ZG:6i1:A50:1HL:3e9:Eo9:1KD:8Ws:BnI".
  (Start may have been overwritten by \225bxxAx\237x.0u\010)
1: Delete LFN
2: Leave it as it is.
3: Fix numbering (truncates long name and attaches it to short name \225bxxAx\237x.0u\010)
? 3
Wrong checksum for long file name ":3FQ:A8Z:100:9gA:8ZG:6i1:A50:1HL:3e9:Eo9:1KD:8Ws:BnI".
  (Short name \225bxxAx\237x.0u\010 may have changed without updating the long name)
1: Delete LFN
2: Leave it as it is.
3: Fix checksum (attaches to short name \225bxxAx\237x.0u\010)
? 3
Reserved field in VFAT long filename slot is not 0 (but 0x20).
1: Fix.
2: Leave it.
? 1
Start cluster field in VFAT long filename slot is not 0 (but 0x6af6).
1: Fix.
2: Leave it.
? 1
Unfinished long file name ":045: DEB:9sB:9UF:2kT:BHk:0sB:Fk0:5eo:A00: Dz2:4Dg:0o0".
  (Start may have been overwritten by xhxx|\225<\177.(bx)
1: Delete LFN
2: Leave it as it is.
3: Fix numbering (truncates long name and attaches it to short name xhxx|\225<\177.(bx)
? 3
Wrong checksum for long file name ":045: DEB:9sB:9UF:2kT:BHk:0sB:Fk0:5eo:A00: Dz2:4Dg:0o0".
  (Short name xhxx|\225<\177.(bx may have changed without updating the long name)
1: Delete LFN
2: Leave it as it is.
3: Fix checksum (attaches to short name xhxx|\225<\177.(bx)
? 3
Reserved field in VFAT long filename slot is not 0 (but 0xc3).
1: Fix.
2: Leave it.
? 1
Start cluster field in VFAT long filename slot is not 0 (but 0x7bb8 ).
1: Fix.
2: Leave it.
? 1
Unfinished long file name ": D4o:AQp:0Pr:18a:1MH:9tC:7pN:CpU:0sb:8ti:1AL:CVy:4uY".
  (Start may have been overwritten by xN'JB\204~g.\021&#1983;)
1: Delete LFN
2: Leave it as it is.
3: Fix numbering (truncates long name and attaches it to short name xN'JB\204~g.\021)
? 3
Wrong checksum for long file name ": D4o:AQp:0Pr:18a:1MH:9tC:7pN:CpU:0sb:8ti:1AL:CVy:4uY".
  (Short name xN'JB\204~g.\021 may have changed without updating the long name)
1: Delete LFN
2: Leave it as it is.
3: Fix checksum (attaches to short name xN'JB\204~g.\021&#1983;)
? 3
Reserved field in VFAT long filename slot is not 0 (but 0xef).
1: Fix.
2: Leave it.
? 1
Start cluster field in VFAT long filename slot is not 0 (but 0x152e).
1: Fix.
2: Leave it.
? 1
Unfinished long file name ":9sH:27rx:4ck:6wk:EUu:5Qg:8eM:8RD:8IM:9OY:5kT:Boy".
  (Start may have been overwritten by xU<\213F\213xx.xU))
1: Delete LFN
2: Leave it as it is.
3: Fix numbering (truncates long name and attaches it to short name xU<\213F\213xx.xU))
? 3
Wrong checksum for long file name ":9sH:27rx:4ck:6wk:EUu:5Qg:8eM:8RD:8IM:9OY:5kT:Boy".
  (Short name xU<\213F\213xx.xU) may have changed without updating the long name)
1: Delete LFN
2: Leave it as it is.
3: Fix checksum (attaches to short name xU<\213F\213xx.xU))
? 3
Reserved field in VFAT long filename slot is not 0 (but 0xf7).
1: Fix.
2: Leave it.
? 1
Start cluster field in VFAT long filename slot is not 0 (but 0x740b).
1: Fix.
2: Leave it.
? 1
/dell2mac/Peret-Rumba Catalana.rar_FILES
  Has a large number of bad entries. (937/1007)
Drop directory ? (y/n) y
*** glibc detected *** fsck.vfat: double free or corruption (out): 0x080dc648 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7e967cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7e99e30]
fsck.vfat[0x804ee34]
[0x4000]
======= Memory map: ========
08048000-08053000 r-xp 00000000 08:01 851993     /sbin/dosfsck
08053000-08054000 rw-p 0000a000 08:01 851993     /sbin/dosfsck
08054000-080fb000 rw-p 08054000 00:00 0          [heap]
af7fd000-b57d6000 rw-p af7fd000 00:00 0
b7d00000-b7d21000 rw-p b7d00000 00:00 0
b7d21000-b7e00000 ---p b7d21000 00:00 0
b7e16000-b7e21000 r-xp 00000000 08:01 3342400    /lib/libgcc_s.so.1
b7e21000-b7e22000 rw-p 0000a000 08:01 3342400    /lib/libgcc_s.so.1
b7e2e000-b7e2f000 rw-p b7e2e000 00:00 0
b7e2f000-b7f6a000 r-xp 00000000 08:01 3376386    /lib/tls/i686/cmov/libc-2.5.so
b7f6a000-b7f6b000 r--p 0013b000 08:01 3376386    /lib/tls/i686/cmov/libc- 2.5.so
b7f6b000-b7f6d000 rw-p 0013c000 08:01 3376386    /lib/tls/i686/cmov/libc-2.5.so
b7f6d000-b7f70000 rw-p b7f6d000 00:00 0
b7f7a000-b7f7e000 rw-p b7f7a000 00:00 0
b7f7e000-b7f97000 r-xp 00000000 08:01 3342357    /lib/ld-2.5.so
b7f97000-b7f99000 rw-p 00019000 08:01 3342357    /lib/ld-2.5.so
bffcc000-bffe2000 rw-p bffcc000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Warning... fsck.vfat for device /dev/sdb1 exited with signal 6.

---

### Post by markoloka on 2007-07-05
I have been  in problems w/ read-only file system...
I used command fsck -f -y  and it fixed it.

---

### Post by xinelo on 2007-07-06
Thanks, Markoloka. 

I solved it with fsck + some options. And it did work, but first I had to delete some of the files which did not get copied correctly. 

Thanks again, xinelo

---

