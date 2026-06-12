---
title: "external monitor unrealized"
date: 2011-08-01
forum: Hardware
---

### Post by impreza112 on 2011-08-01
Hi,

I got a new Lenovo [ThinkPad T420s]("http://shop.lenovo.com/SEUILibrary/controller/e2/atind/LenovoPortal/en_AT/de_AT/catalog.workflow:item.detail?vt=5&GroupID=220&Code=NV8P4GE&hide_menu_area=true&current-category-id=45112BFFE92A442EA60C12769314D5C4") with a NVIDIA NVS 4200M and a [HP ZR24W]("http://www.amazon.com/HP-LP2475w-24-inch-Widescreen-Monitor/dp/B001FS1LLI/ref=sr_1_3?ie=UTF8&qid=1312224658&sr=8-3") (TFT).
When I connect my Laptop with my Monitor, it didn't receive any signal (DisplayPort, VGA or DVI).

However, when i connect the Laptop with my LG L225WS (VGA) i get a signal and the monitor is displayed in the systemsettings (monitor resolution settings).

there is no xorg.conf in /etc/X11

When i type "sudo nvidia-settings" i always get the following response:
"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."
"sudo nvidia-xconfig" create this xorg.conf: [http://pastebin.com/HPZVs88D](http://pastebin.com/HPZVs88D)
when i restart the xserver with "sudo restart gdm" i just get a black screen and i have to restart the system with ubuntu recovery in order to get back a working GUI (after that the xorg.conf is deleted)

I'm using ubuntu 11.04.

Does anyone know how to fix this issue?

Thank you!

br,
Greg

---

