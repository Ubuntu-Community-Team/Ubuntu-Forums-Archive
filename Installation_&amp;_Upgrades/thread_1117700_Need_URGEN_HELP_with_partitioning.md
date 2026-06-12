---
title: "Need URGEN HELP with partitioning"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by Qana on 2009-04-06
Hey..... I am really newby here... from 3 days I have installed Ubuntu... first 7.04 and now 8.10

It is much for me to learn, so I need in the meanwhile to make (without deleting) a new ntfs partition for windows...:(

I have read that I can use partman for that, but I cannot find it anywhere.... 

So any suggestion? (about partman or some other software)

---

### Post by Mark Phelps on 2009-04-06
Boot from the Ubuntu LiveCD, run the partition editor (System --> Administration --> Partition Editor) and create a new NTFS partition using that.

Reboot from the Vista DVD and install to that partition.  If given the option to reformat that partition by Vista, choose to do so.

---

### Post by Qana on 2009-04-06
ok, did that, just right now when I start the computer I cannot start Ubuntu, it starts automaticallz windows

Anz suggestion on that?

---

### Post by Mark Phelps on 2009-04-06
All MS Windows installations automatically overwrite the MBR which forces booting to the MS Windows partition.

You will have to reinstall GRUB and manually add an entry for MS Windows, as follows:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

