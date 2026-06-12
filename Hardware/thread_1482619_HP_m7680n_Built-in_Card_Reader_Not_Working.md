---
title: "HP m7680n Built-in Card Reader Not Working"
date: 2010-05-13
forum: Hardware
---

### Post by iknowcss on 2010-05-13
I have an HP Media Center PC m7680n with a "built in" card reader on the front of the case. This card reader is attached to the motherboard by a wire, and I'm not exactly sure how. According to the HP page, it supports the following cards:

[LIST]
[*]Compact Flash ICompact Flash IISmartMediaMemory StickMemory Stick ProMultiMediaCardSecure Digital (SD)Micro DriveXD Picture Card (xd = extreme digital)
[/LIST]
Specifically, I am trying to read an SD card using this reader on Karmic. The little green LED light lights up when I put the card in, but the card doesn't automount. I can't find it with fdisk -l either. Any ideas how I can get this working? Maybe a file I can tail -f to see what happens when I actually put the card in the reader? I've done quite a bit of searching and I can't seem to figure this one out.

Link to the HP Support Page for the :

[LIST]
[*][http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c00739902&product=3230688](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c00739902&product=3230688)
[/LIST]

---

### Post by Syke on 2010-05-14
After you insert a card, try "lsusb" and post the output.

---

### Post by crustyBarnacle on 2010-05-14
```
lsusb
``` does not change after inserting the card.

I have an HP Pavilion Slimline 

```
lsb_release -idrc
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04 LTS
Release:	10.04
Codename:	lucid
```


```
lspci | grep USB
``` returns the following:

```
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i USB (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP73 [nForce 630i] USB 2.0 Controller (EHCI) (rev a1)
``` and the most recent lines from ```
dmesg
``` show:

```
[67048.389140] sd 6:0:0:2: [sdd] 3920896 512-byte logical blocks: (2.00 GB/1.86 GiB)
[67048.392258] sd 6:0:0:2: [sdd] Assuming drive cache: write through
[67048.396257] sd 6:0:0:2: [sdd] Assuming drive cache: write through
[67048.396261]  sdd: unknown partition table
```

---

