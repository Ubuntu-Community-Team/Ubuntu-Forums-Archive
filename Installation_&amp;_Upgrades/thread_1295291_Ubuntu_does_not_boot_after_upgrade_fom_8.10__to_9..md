---
title: "Ubuntu does not boot after upgrade fom 8.10  to 9.X"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by anarchipur on 2009-10-19
Hi, 

I have a serous problem, please help:

In the gnome gui at the bottom to the right there comes up a red symbol showing that an upgrade is possible. So I clicked on it and an upgrade process started. My current system was 8.10 and the upgrade should have made it 9.04 I guess...

After more than an hour the upgrade was finished, and questions came  like
"do you want to retains the current menu.lst or replace it wth the new?" ... I choose to retain my current form ubuntu 8.10. After the system said, that it has to reboot, I said OK, so it restarted my computer but got stuck right after I selected ubuntu in the boot manager ( cause I have also WIndows vista). So it just does not come up.

I am new to ubuntu and have no clue where to start now

What should I do now, should I somehow replace menu.lst with the new one vo ubuntu 9 or or is it another problem that I have.  

Thank you !!!!

---

### Post by gabry79Italy on 2009-10-19
boot your pc with the live cd of ubuntu 9.04:
open a terminal and:
sudo grub
find /boot/grub/stage1
you will get an output like this :  (hdx,y) then:
root (hdx,y)
setup (hd0)
quit

---

### Post by mox386 on 2009-11-07
This was very bad advice, as it made my computer unresponsive.

---

