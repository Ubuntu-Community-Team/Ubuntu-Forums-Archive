---
title: "xpress200m?"
date: 2007-01-13
forum: Hardware &amp; Laptops
---

### Post by nj_chris on 2007-01-13
Anybody know how to drive xpress200m!Thank you!

---

### Post by locutus42 on 2007-01-13
> **nj_chris said:**
> Anybody know how to drive xpress200m!Thank you!

See the following thread for a script you can run to automatically install the new ATI driver:

[http://www.ubuntuforums.org/showthread.php?t=318889](http://www.ubuntuforums.org/showthread.php?t=318889)

FYI, when you download the "ati-8.32.5-builder.sh" script doing the following steps to get'er done:
1) log out of Ubuntu. Don't shutdown, just log out
2) enter: Ctl-Alt-F1 keys to switch from the login screen to command console #1
3) sign in as prompted using your userid and password
4) enter:  mv ~/Desktop/ati-8.32.5-builder.sh ~
       NOTE: by default, you probably downloaded the script to your Desktop
5) enter: chmod +x ~/ati-8.32.5-builder.sh
6) enter: sudo ~/ati-8.32.5-builder.sh
7) enter: sudo shutdown -r now

Your system should reboot and start running with the ATI fglrx v8.32.5 driver.

---

### Post by thx_1138 on 2007-01-13
would this help after a kernel update to help automate the upgrade process?

---

### Post by locutus42 on 2007-01-14
> **thx_1138 said:**
> would this help after a kernel update to help automate the upgrade process?

it would be best to update your system or kernel before running the ATI driver installation since it is based on your kernel and builds a proprietary module adjusted for your kernel version. What all that means is that if you change your kernel, you'll need to rerun the installation of the ATI driver so it can work with your new kernel.

---

