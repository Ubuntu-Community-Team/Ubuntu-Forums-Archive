---
title: "Only every second boots are success"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by LightningW on 2009-04-24
I don't know how but I did it...
At the first install unfortunately there stayed a Vista loader on a disk and it appeared in GRUB's list at boot. There is another mistake too what I did: I didn't watched which disk to be the GRUB installed so it installed elsewhere than the Ubuntu. Unhidden boot files on a data disk beacuse it was hd0? I hated it. :D
By the way, already only every second boots were success this time too.

I realized this is suck and I deleted every boot files what I found and reinstalled the Ubuntu and here comes the more intresting part. :D
In theory there weren't any boot files anywhere but after the second install the boot is failed with "Error 17". I switched off that disk what contained the older boot files and finally it booted up. But still only every second times. Later I switched back that disk what I talked about and by now it doesn't cause problems.

I'm using ext4 if it matters on Ubuntu's disk and NTFS on the old date disk.

Is this one of that things which only can happen with me? :D

---

