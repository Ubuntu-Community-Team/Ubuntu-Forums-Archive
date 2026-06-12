---
title: "[SOLVED] Dual boot (Want to Resize Ubuntu to Have More Space)"
date: 2008-11-12
forum: General Help
---

### Post by linuxology on 2008-11-12
Here's the Scenario; Keeping XP dual boot around just in case I blow up ubuntu since I'm a noob.  I want to reduce the size of the XP partition since I never get into it.  I have partition magic, but am scared of resizing and I won't be able to get into Ubuntu after making ext3 bigger?  Is this a valid concern or should I go for it?  Is this recommended or should I do it with the Ubuntu installation disk??  I want to make Ubuntu's partition way larger, but don't want to lose my precious Ubuntu install.  I do not want to go back to windows.  So Please help.

---

### Post by blackened on 2008-11-12
As long as you're just resizing you should be fine. I would use gparted from the livecd, but partitionmagic will do just as well (been years and years since I've used it). Just make sure you don't format any of the partitions if asked (obviously).

---

### Post by linuxology on 2008-11-13
[IMG]http://i2.photobucket.com/albums/y49/xaeniac/ubuntupartition.png[/IMG]

This is a screenshot of my partition when I tried to change it in gparted.  I was able to resize the Windows partition, but I could not resize the ubuntu partition to overtake the newly allocated space.  I had to create a new partition.  Is there anyway I can have the Ubuntu partition resize into it?  It looks like Ubuntu will only let me resize the partition on the right side and not the left.  SDA5 is my ubuntu install

---

### Post by blackened on 2008-11-13
You need to move the linux partition to the left, and then resize it to the right. I would apply each operation individually to lessen your chances of something going awry. So move it to the left, apply, resize parition, apply.

---

