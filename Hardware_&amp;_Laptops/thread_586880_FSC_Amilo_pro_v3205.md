---
title: "FSC Amilo pro v3205"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by mmalygin on 2007-10-22
Hi folks,

actually it is known bug - i have googled a bit for possible solution - at the moment i could not find anything which helps. It looks like because of the buggy BIOS (1.20) kernel does not recongnize a touchpad after suspending the ram and does not create a corresponding input class.

People suggesting to force Siemens to fix a BIOS - most probably the worst idea, because they don`t support LINUX on that laptop. I found here similar issues with FSC Si 1520 which has the same BIOS, considered to be a "Wishlist" priority. I understand that there are much more important things to do for the team but anyway... I wanted to investigate myself is it possible to force a kernel to initialize this crappy touchpad, because for me that is the most annoying issue forcing me to use XP on the road :)

Any suggestion will be useful

---

### Post by pbvascon on 2007-10-22
I have recently bought the same laptop for using exclusively with Linux. Yes, I have experienced the lost touchpad after resume from suspend. Here are some things I have tried:

1) use an external usb mouse after resume (cumbersome for some, but can be reasonable if the laptop is on a desk)
2) use hybernate rather than suspend (slower, but touchpad works fine)
3) revert to the older bios 1.10 (I tried this but other things like wifi and booting while connected to external usb disks worked less well)

BTW, I don't think it is a buggy bios that is causing the problem (otherwise it should show it in windows too) so there is hope that this issue will be fixed in a future kernel.
In the mean time I use hybernate or the external mouse.

---

