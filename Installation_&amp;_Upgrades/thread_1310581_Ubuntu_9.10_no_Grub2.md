---
title: "Ubuntu 9.10 no Grub2"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by Darth Trix on 2009-11-01
I have two partitions in my PC, one with kubuntu 8.04 and the other with Win XP, I decided to get rid of Win and make a fresh install of Ubuntu 9.10
The install works fine (i think) but when a reboot i get the old Kubuntu 8.04 grub menu that has no idea that Ubuntu 9.10 is installed in the system (It still thinks Win XP is there).
I' tried some of the solutions of the forum but the problem persists, the old grub it's still there.

Any solutions?

---

### Post by Rumpty on 2009-11-01
Sounds like your grub2 bootloader from 9.10 didn't get installed to the MBR?

---

### Post by Darth Trix on 2009-11-02
Yeah I'm pretty sure that's what happened.
Any idea how to install it?

---

### Post by presence1960 on 2009-11-02
> **Darth Trix said:**
> Yeah I'm pretty sure that's what happened.
Any idea how to install it?

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Darth Trix on 2009-11-02
Grub 2 wasn't installed
This tutorial solved: 
[https://wiki.ubuntu.com/Grub2#Error%2015%20-%20File%20not%20found]("https://wiki.ubuntu.com/Grub2#Error%2015%20-%20File%20not%20found")

---

### Post by F_C on 2009-11-02
[[IMG]http://brainstorm.ubuntu.com/idea/22223/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/22223/)

---

