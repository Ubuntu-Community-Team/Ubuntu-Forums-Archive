---
title: "Ubuntu and Plug&amp;Play, From Feisty to Hardy"
date: 2008-02-18
forum: Hardware &amp; Laptops
---

### Post by xerman on 2008-02-18
Hello there:

Just for the settlement of the issue about plugging new devices to an already configured system:

1- Add a new graphic card needs reconfiguration of XORG. In fact, restarting the computer with the new hardware produces a GDM/XORG failure and going back to console mode. "sudo dpkg-reconfigure xserver-xorg" does not check for the new graphic card. No good.

2- Changing Keyboard+Mouse(both ps2) can be irritating depending on the product. From a Desktop Microsoft (Keyboard+Mouse Wireless Natural Multimedia Keyboard) to a Desktop Microsoft (Keyboard+Mouse Wireless Comfort Keyboard) produces unnatural behavior of mouse. Clean install of system with Wireless Comfort Keyboard works fine.

3- Adding an internal Multicard reader just works.

4- Adding bluetooth dongle works after much touching files in Feisty. Have not tried yet in Hardy.

5- I still haven't found a way to change name to Pendrives or SD cards the "easyway".

There is still a long way to go to be Plug&Play, but on the other hand, there is so many different hardware that it is hard to check them all.

Regards
Xermán

---

