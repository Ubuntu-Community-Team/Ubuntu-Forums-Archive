---
title: "Grub Error 15: file not found"
date: 2008-07-31
forum: General Help
---

### Post by Zabil on 2008-07-31
Hello,

I'm using a laptop with a 2.20 GHz CPU, and I'm interested in installing Wubi because it doesn't require taking up partitions. I downloaded the latest Ubuntu iso file along with it's corresponding Wubi file (i.e. both are v 8.04.1). After installing and booting I'm getting this message:

Find --set-root -ignore-floppies /ubuntu/install/boot/vmlinuz

Error 15: file not found</code>

How can I resolve this problem?

Thanks in advance. :)

---

### Post by ago on 2008-07-31
did you install over a raid or a USB drive?

---

### Post by Zabil on 2008-08-01
Nope.

---

### Post by ago on 2008-08-01
It might be that your HD is not visible at boot
Check that you have either /ununtu/install/boot/.. folder or /ubuntu/disks/boot/.. folder
See bean123 message here [http://ubuntuforums.org/showthread.php?t=876466](http://ubuntuforums.org/showthread.php?t=876466)

---

### Post by Zabil on 2008-08-01
> **ago said:**
> It might be that your HD is not visible at boot
Check that you have either /ununtu/install/boot/.. folder or /ubuntu/disks/boot/.. folder
It seems I have both folders, both contain a grub folder. 

> See bean123 message here [http://ubuntuforums.org/showthread.php?t=876466](http://ubuntuforums.org/showthread.php?t=876466)

Okay, here are all the outputs:

fstest info E:\ output:
```
version: 1.0 build 3
part_base: 0x30D3CF2 (24999M)
part_leng: 0x6446412 (51340M)

blocksize: 512
spc: 8
mft_size: 2
idx_size: 8
mft_start: 0x600000
```

fstest list E:\ output:
```
000036D1             0  [DB]
000036CD             0  [2df158223ea93659049b01108b40]
000036CD             0  [2DF158~1]
000000D5             0  [953b61b912dcf9903f1dbe84a298]
000000D5             0  [953B61~1]
00000021             0  [MSOCache]
00003844             0  [My Dump]
000000AF             0  [My E-Books]
000000C6             0  [My Junk]
0000032D             0  [My other junk]
000000B2             0  [My Videos]
00003844             0  [MYDUMP~1]
000000AF             0  [MYE-BO~1]
000000C6             0  [MYJUNK~1]
0000032D             0  [MYOTHE~1]
000000B2             0  [MYVIDE~1]
00003052             0  [Program Files]
00003052             0  [PROGRA~1]
00002D86             0  [Qur'an]
000000A6             0  [RECYCLER]
0000001B             0  [System Volume Information]
0000001B             0  [SYSTEM~1]
0000A7C1             0  [ubuntu]
0000A7EF             0  [ubuntu-backup]
0000A7EF             0  [UBUNTU~1]
00000356             0  [Vampire - Bloodlines]
00000356             0  [VAMPIR~1]
0000A7E3        188547  wubildr
0000A7E4          8192  wubildr.mbr
00009439             0  [Yusuf Estes]
00009439             0  [YUSUFE~1]
```

fstest inode E:\$MFT output:
```
Type: File
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $FILENAME (0x30) (r,sz=74)
    $MFT
  $DATA (0x80) (nr,sz=54116352)
    6291456+105696
  $BITMAP (0xB0) (nr,sz=6608)
    6291448+8,57257744+8
```

fstest inode E:\. output:
```
Type: Directory
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=48)
  $FILENAME (0x30) (r,sz=68)
    .
  $OBJECT_ID (0x40) (r,sz=16)
  $SECURITY_DESCRIPTOR (0x50) (nr,sz=4172)
    52572768+16
  $INDEX_ROOT (0x90) (r,nm=$I30,sz=152)
  $INDEX_ALLOCATION (0xA0) (nr,nm=$I30,sz=8192)
    29328+8,48298304+8
  $BITMAP (0xB0) (r,nm=$I30,sz=8)
```

Edit: I'm assuming that you wanted the outputs for the partition that contains Ubuntu, which is why I'm using E:\ .

---

### Post by Zabil on 2008-08-05
Could anyone give me some feedback on my situation? Please? 

*cough*Bump*cough*.

---

### Post by bean123 on 2008-08-05
> **Zabil said:**
> Could anyone give me some feedback on my situation? Please? 

*cough*Bump*cough*.

Perhaps you can try grub2:

[http://ubuntuforums.org/showthread.php?t=877750](http://ubuntuforums.org/showthread.php?t=877750)

---

### Post by Zabil on 2008-08-07
Phew, I finally have Ubuntu on my computer.

---

### Post by bean123 on 2008-08-07
> **Zabil said:**
> Phew, I finally have Ubuntu on my computer.

How do you solve it ? Perhaps you can share the story.

---

