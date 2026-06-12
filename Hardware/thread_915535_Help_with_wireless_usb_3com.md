---
title: "Help with wireless usb 3com"
date: 2008-09-09
forum: Hardware
---

### Post by javierg on 2008-09-09
Hi community... I'm using ubuntu hardy on my desktop and i have connected a 3com 3crwe254g72 usb wireless adapter. It recognized fine, i make install of ndiswrapper for the driver but it doesn't work.

I did:
1.- Installation of ndiswrapper
2.- # sudo ndiswrapper -i driver.inf
3.- # sudo ndiswrapper -l
    3c254g72 : driver installed.
           device (0506:0A11) present (alternate driver p54usb)
4.- # sudo depmod -a
5.- # sudo modprobe ndiswrapper
6.- # sudo gedit /etc/modules and add ndiswrapper to the end of the file.

But if I do # ifconfig or # iwconfig the adapter not appear.

Why ?, i dont now.

Please, some help?

Thanks and sorry for my english =)

---

### Post by HavarN on 2010-10-20
[Got it working without ndiswrapper from this guide]("http://plug.noloop.net/sheevaplug-hacks/installing-debian/prism54usb-3com-officeconnect-3CRWE254G72-wlan-wpa-without-nw").

Essentially this is it:
*Download [prism54 firmware]("http://daemonizer.de/prism54/prism54-fw/")*. For the 0506:0a11, the [2.13.1.0.lm86.arm]("http://daemonizer.de/prism54/prism54-fw/fw-usb/2.13.1.0.lm86.arm") worked. 

*Rename and move 2.13.1.0.lm86.arm to /lib/firmware/isl3886usb*
sudo mv 2.13.1.0.lm86.arm /lib/firmware/isl3886usb

*Load the driver*
sudo modprobe p54usb

Now it should be working.

---

### Post by bogyit on 2011-05-18
This would be great but the download link for 2.13.1.0.lm86.arm now is broken, can anyone help? I arrived here searching for an alternative donwload resource for that firmware. By the way here's explaind the same procedure:

[http://linuxwireless.org/en/users/Drivers/p54](http://linuxwireless.org/en/users/Drivers/p54)

---

