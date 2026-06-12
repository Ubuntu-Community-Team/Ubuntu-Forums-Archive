---
title: "X Server error in installation."
date: 2006-01-19
forum: Installation &amp; Upgrades
---

### Post by kevinc on 2006-01-19
Hi there,
I am trying to install Ubuntu x64 on my AMD 64 3000+ system, however, when the X server attempts to start, it fails due to "No Screens Found". 

Should I fiddle around with my resolution?

Any help would be appreciated...

Kevin

---

### Post by stinedvd on 2006-01-19
I'm having the same problem.  I am using a ATI Radeon X800 PCIE.  I tried to run gdmconfig and it fails with the same error.  I looked at the logs and it seems like it has the right display driver.  Any ideas?

---

### Post by kevinc on 2006-02-05
Yes, I do have that same card, and I just used the vesa driver.

sudo nano /etc/X11/xorg.conf

Change the device driver to vesa.

Worked for me.

---

