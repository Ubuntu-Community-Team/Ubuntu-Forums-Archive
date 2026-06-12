---
title: "I don't know how to install a program through the terminal window"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by juanicotolengo on 2009-01-19
Hi there!!! I'm new, and I downloaded LMMS from the sourceforge page, because the aplication wasn't on the synaptic, now I got the tar.bz2 file, and I don't know where should I put the file, and how to install it from the terminal, any idea??? Thank you very much!!!!
Best Regards!!

Juan!

---

### Post by Coreigh on 2009-01-19
to install the Ubuntu lmms package:
```
sudo apt-get update
```
then
```
sudo apt-get install lmms
```
You'll need to enter a password after the first command, use your normal login password.

lmms is in the repositories so you shouldn't have to use the Sourceforge version.

---

### Post by boof1988 on 2009-01-20
Also... I think it is easier to remove the applications when they have been installed using Synaptic.

If you still want to learn how to install from tar.bz2, [here's a link](http://ubuntuforums.org/showthread.php?t=530017) to get you started.  I haven't done that sort of operation yet.

---

### Post by oldos2er on 2009-01-20
lmms is in the universe repository. Check your Software Sources (System, Administration) to enable it.

---

