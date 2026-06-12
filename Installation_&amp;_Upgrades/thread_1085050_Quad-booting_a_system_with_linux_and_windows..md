---
title: "Quad-booting a system with linux and windows."
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by jms1989 on 2009-03-02
Hello, I've got a question I need to run by ya'll.

Here's my setup, I've got Ubuntu, Windows XP, Windows 7 Beta, and I'm thinking on trying Fedora to learns some things on its side of linux.

I've got 3 hdds. One with Ubuntu and WinXP, the second with Win7, and the third for just storage.

/dev/sda{1,2} consists of a partition for windows and one for linux.
/dev/sdb{2,3,5} consists Ubuntu on #2, WinXP on #3, and possibly Fedora on #5
/dev/sdc1 is Win7

The setup works but I want to be able to boot both windows os from grub but the windows boot loader for 7 has taken over the XP boot loader. So my question is, how can I restore the xp boot loader and install the win7 boot loader on sdc1 so it will boot from grub without spitting an error out at me saying its boot loader is missing? Once that's fixed, I could then edit boot.ini for win7 to only boot itself.

The way it stands now is, I have ubuntu, xp, and 7 added to my grub menu. Once the computer gets to grub and I select Windows XP, it loads the Win7 bootloader with the option to boot either 7 or XP. There is another entry for 7 but it I select that it tells me the bootloader is missing.

I imagine its as simple as booting each setup disk and restoring the booloader for xp but what about 7? It just boots to a gui and not that lovely text-based setup menu xp has. Would I need to backup and copy the win7 bootloader from the xp partition and then restore its rightful boot loader?

Suggestions and help is welcome, jms1989.

Partition Info
```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e6777

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       39163   314576766    7  HPFS/NTFS
/dev/sda2           39164      121601   662183235   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x58455f47

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         261     2096451   82  Linux swap / Solaris
/dev/sdb2             262        5483    41945715   83  Linux
/dev/sdb3   *        5484       12010    52428127+   7  HPFS/NTFS
/dev/sdb4           12011       60801   391913707+   5  Extended
/dev/sdb5           12011       13315    10482381   83  Linux
/dev/sdb6           13316       21148    62918541   83  Linux
/dev/sdb7           21149       60801   318512691   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb398cd0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60802   488384512    7  HPFS/NTFS

```

---

### Post by jms1989 on 2009-03-06
Bump.

Does anybody have an answer?

---

### Post by Mark Phelps on 2009-03-07
Not being rude ... but the reason you're probably getting no response is you're asking questions about the MS Windows boot loader -- and this is the Ubuntu (Linux) forum, not MS Windows forum.

A really good source of MS Windows advice is the NeoSmart forums.  Suggest you check there.  you're likely to get a faster, and probably more correct, response.

---

### Post by jms1989 on 2009-03-08
Problem solved. The folks at NeoSmart Forums helped steer me into the right direction. I can now call xp and 7 from grub with no exra menus.

For future reference: [http://neosmart.net/forums/showthread.php?p=33940](http://neosmart.net/forums/showthread.php?p=33940)

Cheers!

---

