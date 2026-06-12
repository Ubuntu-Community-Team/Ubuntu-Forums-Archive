---
title: "Reinstall Xorg drivers at prompt"
date: 2009-10-01
forum: Installation &amp; Upgrades
---

### Post by dkknight593 on 2009-10-01
I have a problem.  While trying to boot Ubuntu in recovery mode I used the xfix option to try and fix video problems.  

Previously the computer worked fine.  I have Ubuntu 9.04 on dell insirion 530 with ATI radeon HD 3650.

I want to use the command prompt to reinstall a generic or default driver.

---

### Post by rreese6 on 2009-10-01
Look at these, they will help you reconfigure with dpkg-reconfigure xorg-xserver.

[http://www.freesoftwaremagazine.com/columns/how_to_fix_your_computers_graphics_with_dpkg-reconfigure]("http://www.freesoftwaremagazine.com/columns/how_to_fix_your_computers_graphics_with_dpkg-reconfigure")

Ubuntu help page about ATI:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

### Post by dkknight593 on 2009-10-03
Reconfiguring Xorg did not work for some reason it just gave me prompts for keyboard and stuff but no video stuff.

I resolved this issue using puppy linux and geany editor looking  for a backup copy of Xorg.conf.  I just cut and paste the settings and restarted.

---

