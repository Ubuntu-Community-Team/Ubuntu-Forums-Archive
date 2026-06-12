---
title: "Using Multiple Monitors"
date: 2007-10-10
forum: Hardware &amp; Laptops
---

### Post by drisco on 2007-10-10
Hey everyone, I'm not a total noob...just half...I'm doing a project for school using 7 monitors, one Matrox dual head in the AGP slot and 5 monitors using 5 nvidia cards in the PCI slots.  I don't have a clue how to make the computer recognize the 5 nvidia cards and have it output in a sequential format.

Any help/push in the right direction would be greatly appreciated.

---

### Post by gibbsnich on 2007-10-11
Did you already check if the computer didn't recognize the graphic cards already? lshw can help here.
I'm not sure what you mean with "sequential format".. 
If they're recognized you'd have to edit /etc/X11/xorg.conf to include device sections for each of those graphic cards and monitor sections for each of those monitors. Then you'd have to add screen sections where each uses one of the graphic-devices and one of monitor-devices created earlier. I'd go for vim, but I heard that displayconfig-gtk edits xorg.conf graphically, never used it though.

HTH!

Michael

---

### Post by drisco on 2007-10-11
what i meant by sequential was this:
monitor 1, 2, 3, 4, 5, 6, 7 aranged in a circulary pattern, and a type of wave/snake like shape flowing to each one.

---

