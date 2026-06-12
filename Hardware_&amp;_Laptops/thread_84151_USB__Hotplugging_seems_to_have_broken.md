---
title: "USB / Hotplugging seems to have broken"
date: 2005-10-30
forum: Hardware &amp; Laptops
---

### Post by stewarto on 2005-10-30
Hi

Something seems to have broken over the last 2-3 days re USB and/or Hotplugging.
Everything was working fine up to 2-3 days ago.
There were some software updates over the weekend .. I wonder if that is where the probem may have occured?
The first problem emerged after having to disconnect and reconnect the usb printer.
It stopped working properly so I decided to re install it ( hp970cxi ).
During the re installation the printer wasn't auto detected although I could see it via lsusb, so I had to manually enter the manufacturer name etc.

Also, my card reader which was being detected and automounting  is now no longer being detected or automounting.

Also. lsusb sometimwe just hangs.

I never had any of these problems 2-3 days ago so maybe something has gone wrong with the recent software updates.

I am only using the Ubuntu Repositories including Universe and Multiverse.

I see there are some others who appear to be experiencing automounting problems just recently.

Has anyone any ideas where the problem may lie?


Cheers

Stewart

---

### Post by Samuel on 2005-10-30
im having usb problems too, only with my little ram drive though, the ipod and printer work fine.

from what i have gathered, the kernel upgrade via update manager is to blame, someone said they fixed it by downgrading the kernel but didnt say how to do it. i guess we will just have to hold on and see, im sure the developers are aware and working on it :)

---

### Post by stewarto on 2005-10-30
Samuel

If that is the cause of the problem then you can always boot the previous kernel from the grub menu.

If you check cat /boot/grub/menu.lst you should see the previous version still listed ( and the actual kernel in /boot.

I guess it needs to be fixed properly though

Stewart

---

