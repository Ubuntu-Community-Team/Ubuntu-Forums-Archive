---
title: "Bootloader problem"
date: 2008-11-28
forum: General Help
---

### Post by nevercroft on 2008-11-28
I just finished installing Intrepid Ibex on a separate 10 gig partition, but when I rebooted my computer the grub bootloader was not present and there is no Ubuntu entry in the windows one. 

Is is possible to add ubuntu to the present non-grub bootloader?

If not, how do I get the grub bootloader and how do add ubuntu to its startup list.

---

### Post by caljohnsmith on 2008-11-28
Since you have a new install, it would probably be easier to just reinstall Intrepid and let it install Grub. Did you click on the "advanced" button at the end of the installation setup to change the Grub settings? Do you have more than one HDD? How about opening a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -lu
```
So we can see your current setup. :)

---

### Post by nevercroft on 2008-11-28
I don't have a separate drive, and I did click the advanced button, I probably did click something do to with the bootloader. #-o. Anyway I'll reinstall Intrepid like you said and not touch the bootloader settings.

---

