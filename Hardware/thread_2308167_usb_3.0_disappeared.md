---
title: "usb 3.0 disappeared"
date: 2015-12-31
forum: Hardware
---

### Post by dmtparker on 2015-12-31
I am running Ubuntu Studio 14.04.3. I just got an automatic update to kernal 3.13.0-74-lowlatency. When I rebooted after update, none of the usb ports recognize usb3 devices. They work fine with usb2 devices. I have an Intel NUC computer with 4 x usb3.0 ports mounted on motherboard. It was all working fine for over a year before update. This cannot be a problem unique to me. Is there an issue with the new kernal? How do I go back to 3.13.0-73? In this install grub is totally silent with no user input. I know in the past (Red Hat or Suse or??) that there was a menu and it was easy to just drop down to the old kernal until problems with the new one were cleared up. Is there an easy or at least SAFE way to edit grub to make it interactive? What about fixing the usb3 problem? Nearly all my data is on my 1T usb3 HDD.
Thanks!

---

### Post by weatherman2 on 2015-12-31
The change isn't really in Grub - it's in the Grub boot menu.  And unless you have purged it, 3.13.0-73 is still there; you can reboot and hold the Shift key to get a boot menu to be able to choose a previous kernel.  If you do that and USB 3.0 comes back, then you can remove the newer kernel and avoid doing kernel updates in the future.

---

### Post by dmtparker on 2016-01-01
> **weatherman2 said:**
> The change isn't really in Grub - it's in the Grub boot menu.  And unless you have purged it, 3.13.0-73 is still there; you can reboot and hold the Shift key to get a boot menu to be able to choose a previous kernel.  If you do that and USB 3.0 comes back, then you can remove the newer kernel and avoid doing kernel updates in the future.

Holding down shift key didn't work (tried both). Of course, my keyboard is a usb device, but it does work to get into bios, etc. at boot time so maybe my grub is set up differently?? I am somewhat hesitant to muck around inside grub without fairly explicit instructions, but any help appreciated.

---

### Post by dmtparker on 2016-01-02
I managed to get grub ineractive via help from another post, but it did not solve my problem re: usb 3.0. To keep things clearer, I am going to mark this SOLVED and start a new thread dealing ONLY with the usb 3.0 problem. Thanks for the help and sorry for the confusion.

---

