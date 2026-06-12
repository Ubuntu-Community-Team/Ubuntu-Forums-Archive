---
title: "Fedora messed up my comp.... I need ubuntu back!"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by Jedwinjim on 2009-03-17
Hi, just made the switch over to linux from windows, started with ubuntu which was all good, but wanted to mess around and see others and how they compare. SO I moved on to Fedora 10, it installed fine, but after a few days I decided I wanted to go back to ubuntu. So I insert my xp disc to wipe the partition clean, only my screen now goes blank after the "setup is inspecting your hardware configuration" screen.... I've also tried reinstalling ubuntu on the same partition as fedora only to be now met with a "ubuntu failed to install due to hardware configuration failure" message....


I need to wipe fedora and start all over with ubuntu, anyone now how this is going to be possible?? any help MUCH appreciated!!

---

### Post by taurus on 2009-03-17
You do not need to wipe off Fedora before you install Ubuntu.  Just tell the installer either to use the same partitions or to use the whole disk.  That sure will wipe out any previous OS on the drive.

---

### Post by Jedwinjim on 2009-03-17
yeah but ubuntu won't install because of what ever changes fedora has made. I've installed ubuntu before with no issues - but since I installed fedora ubuntu gives me a hardware configuration failure and ceases to install.

---

### Post by taurus on 2009-03-17
Does it say what hardware?

Can you run it Live?  If you can, open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

