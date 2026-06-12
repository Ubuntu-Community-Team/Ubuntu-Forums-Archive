---
title: "how to get the gutsy kernel??"
date: 2007-06-14
forum: Hardware &amp; Laptops
---

### Post by ali4949 on 2007-06-14
Does anyone know if it would be possible to take the gutsy gibbon tribe 1 kernel and use it on a feisty system, and if so how would one go about doing that. I am mostly interested in seeing how the 2.6.22 kernel improves on the battery life and the usb support on my laptop. 
thanks

---

### Post by angryfirelord on 2007-06-14
Add gusty's sources to your sources.list file. Install the linux-image package and remove gusty's sources.

However, you run the risk of breaking your system.

---

### Post by Rui Pais on 2007-06-15
yes, 
besides add gutsy to sources.list will lead you to move to all ubuntu unstable or end up with a mixed system.

A better choice would be download just linux-image and linux-header packages [from here]("http://packages.ubuntu.com/").

But even better, in terms of _security and stability_, compile your own kernel from the sources you want:
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

---

