---
title: "Need help with multiple HDD/boot loader question"
date: 2008-08-28
forum: Hardware
---

### Post by stormtrooprdave on 2008-08-28
I currently have a SATA drive with XP and Ubuntu on with Grub as the boot loader.  I now have got an extra ATA drive with Vista on with the Vista boot loader.  

If I have them both connected at the same time what will happen?  Will it automatically default to Grub?  Will there be any conflict between Grub and the Vista BCR? 

If it does boot using Grub would it detect Vista on the OS selection screen?

---

### Post by caljohnsmith on 2008-08-28
> **stormtrooprdave said:**
> I currently have a SATA drive with XP and Ubuntu on with Grub as the boot loader.  I now have got an extra ATA drive with Vista on with the Vista boot loader.  

If I have them both connected at the same time what will happen?  Will it automatically default to Grub?  Will there be any conflict between Grub and the Vista BCR? 

If it does boot using Grub would it detect Vista on the OS selection screen?
Whether you get Grub or Vista on startup depends on which HDD is first in the BIOS boot order. IMHO I would put the Grub HDD first in the boot order, and then you can boot Vista by adding an entry for it in your Grub's /boot/grub/menu.lst. So unfortunately no, Grub won't automatically "detect" Vista on start up. :) But to add your Vista to Grub's menu.lst, just do the following:
```
gksudo gedit /boot/grub/menu.lst
```
Then at the very bottom of that file, add the following:
```
title   Windows Vista
root    (hd1,0)
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

```
That should be all you need. If you have any problems, then post the contents of your menu.lst and also the output of:
```
sudo fdisk -lu
```
Good luck and let me know how it goes. :)

---

### Post by stormtrooprdave on 2008-08-29
Plugged it all in and it booted with Grub. Added Vista to the Grub loader and was able to select it and boot into Vista no problem.

Unfortunately I had massive problems with Vista itself.  It would not recognise my graphics card (nVidia 7950GT) and gave a Code 35 error in device manager, saying I needed a BIOS update in order to make it work.  Its funny how it works in XP and Ubuntu!

So I have Vista with 800 x 600 analogue resolution with no aero effects, versus XP and Ubuntu with 1440 x 900 DVI resolution, don't think I'll be using it much lol

---

