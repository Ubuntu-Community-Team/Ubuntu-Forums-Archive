---
title: "Inspiron fail to resume from suspend"
date: 2009-04-21
forum: Hardware
---

### Post by bayonetblaha on 2009-04-21
I really don't want to reformat *again*, so I hope someone knows what this is.  

After upgrading to the Jaunty beta, I could hibernate and suspend successfully.  At some point my Inspiron 1520 lost the ability to resume, though hibernation and suspend still work.  When the lid is opened, the hard drive starts up and everything works as normal, except that the screen remains blank and no unlock dialog is displayed.

---

### Post by bayonetblaha on 2009-04-27
I just found the solution.

I reenabled Nvidia accelerated graphics driver ver. 180 in the "Hardware Drivers" section of system menu, and everything's back to normal, with good suspend and resume.

---

