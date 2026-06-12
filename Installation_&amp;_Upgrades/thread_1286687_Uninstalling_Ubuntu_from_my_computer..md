---
title: "Uninstalling Ubuntu from my computer."
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by macka7887 on 2009-10-09
Hello Ubuntu Forum.
I installed Ubuntu tonight but unfortunately at the moment it is not what I am looking for.

Previously before I installed this, I was running Microsoft Windows 7 Release Candidate Build 7100.

I would like to go back to this but when I go to install Windows 7 and I chose where I would like to install it I get a message telling me that I can not install Windows 7 to Disk 0  Partition 1 because it is an unrecognized type.

There is also a second option that is Disk 0 Partition 2. but that is only 2.9GB.

How can I fix this problem so I can resume my work on Windows 7.

Thanks for the help in advance,

Mackenzie.  :)

---

### Post by pmlxuser on 2009-10-09
reinstall windows mbr i think it FIXMRB command in windows disk repair prompt

---

### Post by jeremyswalker on 2009-10-09
If you are *re-installing* Windows, there should be an option to format the partition. It will have to be formatted. You cannot install Windows on a Linux-native filesystem.

---

### Post by keplerspeed on 2009-10-09
The Win7 installer cannot recognise the ubuntu partiton, either ext3 or ext4 format probably.

So what you will need to do, to install win7 back over the top of ubuntu, is in the win7 installer when it says it cant install, unrecognised type, there should be an option to delete/edit/format partition. Win7 installer will then format the partition to the required format, however this will mean loosing you ubuntu install. Is this what you want to do?

Have you considered a dual boot setup?

---

### Post by macka7887 on 2009-10-09
> **pmlxuser said:**
> reinstall windows mbr i think it FIXMRB command in windows disk repair prompt

This line did not work.

> **keplerspeed said:**
> The Win7 installer cannot recognise the ubuntu partiton, either ext3 or ext4 format probably.

So what you will need to do, to install win7 back over the top of ubuntu, is in the win7 installer when it says it cant install, unrecognised type, there should be an option to delete/edit/format partition. Win7 installer will then format the partition to the required format, however this will mean loosing you ubuntu install. Is this what you want to do?

Have you considered a dual boot setup?

When choosing where to install, underneath the difference 'Disk Partitions' it has, Refresh, Delete and Load Driver.  It also Has Format, New and Extend but these are all frozen/unactivated out.

Dual boot is great.  I have 2 500GB drives on my desktop comptuer that I use most of the time.  I just wanted to try out Ubuntu on my laptop first as I do not use it as much witch unfortunately only has a 100GB drive or something.

Thanks for trying to help so far,
Anything else would be great.

---

### Post by jeremyswalker on 2009-10-09
Well, if you are completely getting rid of Ubuntu, delete the Ubuntu partition and create a new partition. You said that the 'Delete' option was available.

---

### Post by macka7887 on 2009-10-09
> **jeremyswalker said:**
> Well, if you are completely getting rid of Ubuntu, delete the Ubuntu partition and create a new partition. You said that the 'Delete' option was available.

I don't know why I did not try this in the first place.
Thanks :)

I will try Ubuntu again, Just at the moment I rather have only Windows on this laptop.

---

### Post by pmlxuser on 2009-10-09
sorry i thought you had dual boot. ... you sentence seemed to say you had ubuntu and windows 7 and you want to go back to windowsd 7 completely..

---

