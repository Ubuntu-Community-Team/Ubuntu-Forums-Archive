---
title: "Ubuntu 7.04, mouse problems"
date: 2007-07-16
forum: Hardware &amp; Laptops
---

### Post by akiratheoni on 2007-07-16
I used to use Ubuntu 6.10 and everything worked fine even when I upgraded to Ubuntu 7.04. After reinstalling it one more time due to some problems, the mouse stopped working. It's optical and the light isn't even on. It's a USB mouse.

After trying to find the problem through Google, I read that the problem was with the kernel or something and downloaded a *.deb which is supposed to update the kernel, I dunno really. I ran it and nothing happened.

Oh and I also have Vista, Fedora 7, and Mandriva on this computer... Fedora 7 suffers from the same problem, Vista and Mandriva work fine.

I've tried editing the grub.conf file to change which kernel it boots but I don't think I did it correctly because it didn't boot. Mandriva's /boot/grub/menu.lst file currently is booting Fedora and Ubuntu using the vmlinuz-2.6.17-13mdvlegacy which I think is older than the one that Ubuntu's /boot/grub/menu.lst had, which was vmlinuz-2.6.20-15-generic.

So I copied Ubuntu's kernel over to Mandriva's /boot and changed the menu.lst so it booted from ubuntu's kernel... but it didn't work. Yeah I'm a complete noob at linux so this was probably the wrong move so go ahead and flame me.

Also my internet isn't working on that computer, but that's not a problem until I can get this problem solved first.

Tell me if you need any more details.

---

### Post by Antimatter27 on 2007-07-17
i have had, unfortunately, the exact same problem with a usb optical mouse (my light also does not come on). curiously though when i boot ubuntu 7.04, or kubuntu, my usb optical mouse resonds on both versions up until they have fully loaded. at that point it dies.

on kubuntu forums i was basically told i'm screwed. perhaps somebody here knows a fix, if not we might have to end up with one of these:

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1220387&CatId=469](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1220387&CatId=469)

---

