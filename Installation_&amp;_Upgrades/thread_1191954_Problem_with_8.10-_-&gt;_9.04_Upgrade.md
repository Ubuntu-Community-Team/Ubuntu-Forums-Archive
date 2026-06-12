---
title: "Problem with 8.10- -&gt; 9.04 Upgrade"
date: 2009-06-19
forum: Installation &amp; Upgrades
---

### Post by smsvends on 2009-06-19
I didn't finish installing all of the updates in 8.10 before I installed 9.04. Now when I boot 9.04 I just get my normal desktop background and my mouse arrow, no menu, files or anything. I have no idea how to fix this problem.

---

### Post by dstew on 2009-06-19
Boot into recovery mode. From the command line, try **xfix**. If the command works OK, enter **startx** and see if you can get a working desktop.

---

### Post by smsvends on 2009-06-19
I ran it in recovery mode and then selected xfix from the recovery menu. Then there was a warning about overwriting and then it sent me back to the recovery menu and I selected resume normal boot and nothing changed. I still just get the desktop background and mouse arrow. Did I do something wrong?

---

### Post by dstew on 2009-06-22
I think you have to proceed through the warning. It is telling you that xfix  will overwrite your xorg.conf file, which is what you want it to do, since your display is not working.

---

