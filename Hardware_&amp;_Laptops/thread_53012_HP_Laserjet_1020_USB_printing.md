---
title: "HP Laserjet 1020 USB printing"
date: 2005-07-29
forum: Hardware &amp; Laptops
---

### Post by balri on 2005-07-29
I have just installed Ubuntu on my computer for the first time and when I add a printer it detects my HP Laserjet 1020 on the USB port and suggests a Laserlet 1000 driver. After I add the printer I try to print a test page and although the job disappears from the queue nothing prints out.

Does anyone have any ideas what I am doing wrong?

---

### Post by alastair lewis on 2005-07-30
Have you got HPLIP from hpinkjet.sourceforge.net.

There is a fairly detailed debian installation HOWTO which works for ubuntu. However, you have to 'sudo apt-get install libjpeg62-dev' in addition to the other stuff they specify in the first section or configure will fail. Setting up is also well covered.

HPLIP is also available in the repositories (I can't remember which one, I think it was the backport, but it didn't work for me from there).

This should work.

---

