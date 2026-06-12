---
title: "No dual boot option for XP on reboot- all else groovy!"
date: 2006-01-08
forum: Installation &amp; Upgrades
---

### Post by jonant on 2006-01-08
Hello:
I have AMD64 version of Ubuntu installed and operating fine- printer, sound, video, browser, email.
On reboot there is no option to boot to Windows XP, it boots straight into Ubuntu.
My system: (2) SATA WD 36.7GB Raptors in RAID 0 ( Windows XP), (1) IDE Seagate 80GB Barrcuda (Ubuntu), ASUS K8V SE
Now if I reboot and change the boot order to the RAID drives it will boot and reboot into XP. I have to change the boot order to the 80GB Seagate drive to get Ubuntu and then it reboots only to Ubuntu.
In System/Admin/Disk it shows-
HD 74.53GB   Partitions 1, 2, and swap         /dev/hda1, /dev/hda2, dev/hda5
HD 34.48       Partition 1 68.94GB                 /dev/sda1
HD 34.48       (no partitions)                         /dev/sdb
I am a total noob with this, so speak slowly and in simple English:rolleyes:

---

### Post by TikkiRo on 2006-01-08
[COLOR="Purple"]Sorry can't really help with this, other than to say that I remember when installing Ubuntu on my double drive XP system it did mention something about RAID and so it's possible you either selected or deselected something to do with that option although in all honesty (since I've zilch idea what RAID even is!) I have no idea either if that's the problem.  All I know is that mine set up the dual boot menu straight off without any issues, BUT I equally couldn't tell you what settings I used in the installation other than probably using the defaults for things like RAID and LVM of which I'd no ideas about.  Hopefully someone else with a tad more knowledge will be able to provide a bit more in-depth info on this one.[/COLOR]

---

### Post by jonant on 2006-01-08
So I have tried reinstalling several times with the same result.
I'm installing everything to the IDE 80GB drive. There are only Ubuntu options when booting up, no XP, so I'm guessing something needs to be installed into the Windows XP/ SATA Raid drive(s)?
Thanks

---

