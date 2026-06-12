---
title: "UUIDs in /etc/fstab"
date: 2007-02-12
forum: Hardware &amp; Laptops
---

### Post by ariszlo on 2007-02-12
Ubuntu used to boot without problems back in the good old days when hard disk partitions were listed with /dev/hda* ids but it seems some people decided to fix what was not broken.

I have three Linux distributions on my machine, one on /dev/hda6, Ubuntu on /dev/hda7, and a third distribution on /dev/hda8, and I could boot into each until yesterday when I replaced the Linux distribution on /dev/hda8 with another one. The installer reformated /dev/hda8, as installers normally do, and it would have caused no problem to Ubuntu if it still used the good old /dev/hda* ids in /etc/fstab but it is using UUIDs instead. Unfortunately, reformatting changes the UUID.

The installer of the new distribution did not touch Ubuntu's fstab. Why should it have done so? Consequently, Ubuntu greeted me with the following message:

Failed to open the device 'UUID=35e9bd0a-12f7-44d2-b1f0-0bb09260d63c': No such file or directory :(

Should this happen to you, this is how to fix it:

First, get the UUID of /dev/hda8 with the following command:
sudo vol_id -u /dev/hda8
Then edit /etc/fstab and replace the old UUID of /dev/hda8 with the new one.

Now I know what's wrong with UUIDs in /etc/fstab. What I don't know is what was wrong with the good old /dev/hda* ids?

---

