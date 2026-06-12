---
title: "Ubuntu 8.10 - Wacom Bamboo Fun"
date: 2009-03-23
forum: Hardware
---

### Post by mishathegoat on 2009-03-23
Hey everyone,

I was curious if anyone knew how to get the eraser working with the Wacom Bamboo Fun. Everything seems to work fine all except the eraser. I've installed all the updates.

EDIT: And, yes, I've installed wacom-tools. The tablet wasn't visible in the wacomcpl window.

Thanks,
Misha

EeePC 900HA
Ubuntu Desktop 8.10
CPU 1.6Ghz
RAM 1G

---

### Post by mishathegoat on 2009-03-24
Anyone?

---

### Post by Favux on 2009-03-24
Hi mishathegoat,

Have you looked at the other threads on the Wacom Bamboo?  Have you checked out Loic2's Wacom wiki and associated thread?  It's here:

[https://help.ubuntu.com/community/Wacom]("https://help.ubuntu.com/community/Wacom")

Not having stylus and eraser in wacomcpl or seeing them in extended input devices in Gimp or Inkscape suggests that you are not correctly configured through your xorg.conf.  Instead HAL (hardware abstraction layer) and the 10-wacom.fdi may be handling your stylus.  And I don't think that will give you eraser.

Or possibly linuxwacom isn't correctly installed.

---

### Post by Favux on 2009-04-03
Hi mishathegoat,

Gemnoc says he got the buttons working here on post #7.

[http://ubuntuforums.org/showthread.php?t=1098822]("http://ubuntuforums.org/showthread.php?t=1098822")

He also says he has the eraser working.  So maybe you could ask him?

---

