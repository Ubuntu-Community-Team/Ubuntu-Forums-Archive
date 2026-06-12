---
title: "HP Scanjet 4370 and XSane"
date: 2007-02-25
forum: Hardware &amp; Laptops
---

### Post by Aithnea on 2007-02-25
Hello everyone.  I've known for a while that this scanner wasn't supported by Sane but I recently found that the backend for the HP 3900 series might work for it.  Long story short I decided to install it and give it a try.  Now when I try to open Xsane I get this error:

> Failed to open device 'hp3900:libusb:003:004':
Access to resource has been denied.

To me it looks like XSane now realizes there is a scanner there but there appears to be a permission error.  Does anyone know how I might go about fixing that error?  Thank you in advance for your help.

---

### Post by MoebusNet on 2007-03-21
I've got the exact same situation. Anyone care to give me a direction to try next?

---

### Post by timcredible on 2007-03-21
the only suggestion i can give is make sure you're running the latest hplip (1.7.1).  if not, go to hp and install it.

---

### Post by lochball on 2008-02-04
Have a look on this thread, maybe it helps: [http://ubuntuforums.org/showthread.php?t=410398&highlight=4370+xsane]("http://ubuntuforums.org/showthread.php?t=410398&highlight=4370+xsane")

---

