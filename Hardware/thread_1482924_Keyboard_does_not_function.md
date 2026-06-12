---
title: "Keyboard does not function"
date: 2010-05-14
forum: Hardware
---

### Post by robfinley on 2010-05-14
I have an Acer Aspire 5517. AMD TF-36. 2 GB RAM.
I've already created a 50 GB Partition for Ubuntu as well as a 4 GB Swap partition
Ubuntu installs but the keyboard and touchpad don't work although the Microsoft USB Wireless Mobile Mouse does..
Any ideas? As far as I can tell, I'm the only one with this specific problem which scares me.

---

### Post by jazzgossen on 2010-05-14
Sounds like an odd problem indeed. Can you test the keyboard from another OS? Was Windows installed on the machine?

---

### Post by robfinley on 2010-05-14
Everything works fine in windows 7 as well as in the BIOS menu. I DO have a ghost in my machine.. Every once in a while my keyboard stops working after one keystroke when I boot up in windows. this is usually resolved by rebooting. The touch pad dosen't work in windows and I suspect it is the source of my problems. I don't need it though or even care about it.

---

### Post by jazzgossen on 2010-05-14
Just an idea:
You could boot Ubuntu in recovery mode (terminal only) and edit xorg.conf to remove all "synaptic" devices (that should be your touchpad).

---

### Post by robfinley on 2010-05-14
I'm down. How?

---

### Post by jazzgossen on 2010-05-15
In the GRUB boot menu that appears when the computer starts up, there should be an option to start Ubuntu in recovery mode. If your keyboard works there, you should be able to select that.

---

