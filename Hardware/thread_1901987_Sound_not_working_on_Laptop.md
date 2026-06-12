---
title: "Sound not working on Laptop"
date: 2011-12-29
forum: Hardware
---

### Post by haxifix on 2011-12-29
Hello, for some reason I have no sound on my computer.  I had sound before but then I installed the package that installs Flash and Java.  I forgot what it is called but after I installed that, I have no sound anymore.  Can someone please tell me how to enable sound?

---

### Post by lidex on 2011-12-31
Did you try a suspend-resume cycle? Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

