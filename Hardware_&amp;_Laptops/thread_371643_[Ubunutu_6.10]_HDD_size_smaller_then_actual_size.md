---
title: "[Ubunutu 6.10] HDD size smaller then actual size"
date: 2007-02-27
forum: Hardware &amp; Laptops
---

### Post by Glitch0r on 2007-02-27
Hello people,

My first post here, so go easy on me aight.

I recently converted my Windows desktop to a completely Ubuntu desktop. As I am mainly using the desktop as FTP server I have a couple of large HDD's in there which I also converted from NTFS to EXT3 with gparted doing it one by one to avoid data loss.

This all went pretty well except for the fact that the same amount of data does not fit on the same HDD anymore. I have 4 HDD's in my desktop and only one of the which is used for '/', '/home' and SWAP shows the correct size (80GB). The other three are disks from 200GB that have been mounted. When I look at the available space it only shows 177GB on space.

I'm wondering where the rest went and how I could get the space back ... :confused: \

Below is an overview (in dutch):
```

Schijf /dev/sda: 203.9 GB, 203928109056 bytes
255 koppen, 63 sectoren/spoor, 24792 cylinders
Eenheden = cylinders van 16065 * 512 = 8225280 bytes

 Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/sda1               1       24792   199141708+  83  Linux

Schijf /dev/sdb: 203.9 GB, 203928109056 bytes
255 koppen, 63 sectoren/spoor, 24792 cylinders
Eenheden = cylinders van 16065 * 512 = 8225280 bytes

 Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/sdb1               1       24792   199141708+  83  Linux

Schijf /dev/hda: 81.9 GB, 81964302336 bytes
255 koppen, 63 sectoren/spoor, 9964 cylinders
Eenheden = cylinders van 16065 * 512 = 8225280 bytes

 Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/hda1   *           1        1275    10241406   83  Linux
/dev/hda2            1276        1530     2048287+  82  Linux-swap / Solaris
/dev/hda3            1531        9964    67746105   83  Linux

Schijf /dev/hdb: 203.9 GB, 203928109056 bytes
255 koppen, 63 sectoren/spoor, 24792 cylinders
Eenheden = cylinders van 16065 * 512 = 8225280 bytes

 Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/hdb1               1       24792   199141708+  83  Linux
```

---

### Post by an.echte.trilingue on 2007-02-27
EXT3 keeps a journal to prevent data loss.  It takes up +/- 10% of your free disk space.  It will shrink as your free disk space shrinks, approaching zero as your free disk space approaches zero.  I think that if you actually try to put 200GB of data on the disk, it should work just fine, or have you tried that already?

Also, have you taken the differences in the two definitions of GB into account (1,000,000,000 bytes vs 2^30 bytes)?  Using the second definition (which Nautilus does in the free disk space dialog , IIRC), your disks are only 189GB.

Take care,
-mat

---

### Post by Glitch0r on 2007-02-28
Thanx for your answer Mat, explains a lot.

I had indeed not tried to exceed the 177Gb that is reported by Nautilus as total HDD space. Although I'm aware of the difference in definition of space, I thought the difference between 189 and 177 was too big.

The journaling could very well be the explanation for this. Gonna try and pump some more data on the disks ... ;) 

Is there actually a config file where this journaling can be cancelled for certain disks for instance?

---

### Post by an.echte.trilingue on 2007-02-28
You can do different things with the journal, and I believe that is one of them, but I do not know how to do it, unless you just reformat your drive EXT2 (which is not a journaling filesystem).  I am sure there is somebody here who knows how if you start a new thread asking that question.

However, there is no reason to do this that I can think of.  The journal is IMMENSELY useful in preventing data loss if you should have a power outage or hard crash, and it does not take up any actual space, even if it appears to do so in the dialogs.  Its size is a percentage of free space, so it disappears as you fill up your drive.  Is is completely transparent to you; just remember that it is there when you look at how much free space you have.

The first thing I would recommend you do though is try to fill a drive up.  If you can put 189GB on the drive without issues, you really needn't bother with this any more.

Also, there is a command line utility called diskfree that will give you a better idea of your disk space.  Try:

```
df -h
```

Take care
-mat

---

### Post by Glitch0r on 2007-03-01
Thanx for the answer again. 

It's just that I'm a control freak and feel the need to know exact numbers but I guess you are right and I shouldnt worry about it ... ;)

I'm at work right now so I cant test filling up the drive or try out that command line utility at this moment. It will be the first thing for me to do when I get home.

---

