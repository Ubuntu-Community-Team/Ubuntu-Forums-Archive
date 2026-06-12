---
title: "How to Undo CD assisted Boot"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by Stheman on 2009-05-02
Hello,

while I was trying to install Ubuntu 9.04 on my laptop through the CD, I chose the option to install the CD Boot so that I can choose to either boot the CD or Windows.  Now that I have successfully installed Ubuntu and the GRUB loader is working, I would like to undo this so that when I choose Windows from GRUB it just loads windows.  Thanks, please advise.

---

### Post by saidinesh5 on 2009-05-02
did you mean to 
1) set windows as the default boot option in the grub menu / hide the grub at all?
                    or
2)uninstall ubuntu so that there when you turn on your pc, it directly boot into windows?

---

### Post by stretch427 on 2009-05-02
Edit your grub boot loader to specify Windows as the default.

```
sudo nano -w /boot/grub/menu.lst
```and lets say that windows is your 4th boot option

Change the default from 0 to 4

```
default     4
```exit and save and that should do the trick.


Cheers!

---

### Post by Stheman on 2009-05-02
Ummm actually it isn't that, the Grub loader does what I want it to.  It lists Ubuntu and Windows XP OS, and I can choose from either of them, but when I choose Windows XP, it takes me to a second boot menu that is due to intalling the assisted boot option from the CD, which is not the GRUB loader, but more like if I held the F8 key for windows Safe mode.  In this menu I can choose to boot either Windows or Ubuntu, but choosing Ubuntu here, it will try looking for the CD.  It is the later boot menu that I would like to get rid of.

---

### Post by stretch427 on 2009-05-05
[http://www.vistax64.com/general-discussion/151517-disable-boot-manager-popping-up.html](http://www.vistax64.com/general-discussion/151517-disable-boot-manager-popping-up.html)

This is a link to fixing the problem. And I would use EasyBCD to try and reinstall the bootloader and then just set it to the standard default 0. But that seems like a Windows Problem not really a Ubuntu problem.

Best of luck!

Edit: that is if you want to keep GRUB as default bootloader, which I highly recommend. Just easier to configure according to your preferences.

---

