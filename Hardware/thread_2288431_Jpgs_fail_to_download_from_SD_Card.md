---
title: "Jpgs fail to download from SD Card"
date: 2015-07-27
forum: Hardware
---

### Post by neigun on 2015-07-27
Hi Guys

The is the first post for a long time, which is always a good sign!

I have a SanDisk Extreme III 30 mb/s edition sd card, which refuses to play- in that all the jpg photos do not download from an internal card reader, either using Nautilus or Shotwell.  If I try only a few downloaded and the rest are corrupted- in that they partially download or not at all.

 The card works OK on a Windows 7 machine, but needless to say I would like to get it working in Gnome! I've tried various solutions and Ubuntu recognises the card reader.

Any help would be much appreciated.

Cheers 

Neil

Sytem Spec 15.04 Ubuntu Gnome, M5A99X EVO R2.0, AMD FX-8320, ATI 7750

---

### Post by sudodus on 2015-07-28
Before trying more from linux, I suggest that you ***backup*** all files on the card (copy them via Windows) to a safe place.

I think it could be a mismatch between the linux driver and the card reader.

Can you try reading the card, when it is in a camera (connect with Shotwell to the camera)?

If that does not work, there might be a problem with the file system on the card, and I suppose it is a Microsoft file system: FAT32, NTFS or exFAT. You could try to check and repair the file system. Boot into Windows and run

```
chkdsk /f X:
```

where X: is the drive letter in Windows, for example D: or E:

---

