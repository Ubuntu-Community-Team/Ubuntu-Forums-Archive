---
title: "AVM Fritz!Card with feisty"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by Matl on 2007-04-25
Hello,

I use the AVM Fritz!Card USB. I used it with edgy without problems. After the upgrade to feisty it doesn't work anymore. 
I compiled the driver with the avm-kernel-source packet.

With modprobe fcusb I can load the driver but feisty does not recognize tthe card. When I plug it in dmesg shows
[  690.648288] usb 1-1: new full speed USB device using ohci_hcd and address 3
[  690.874057] usb 1-1: configuration #1 chosen from 2 choices

And lsusb says
Bus 001 Device 003: ID 057c:1000 AVM GmbH 

But it doesn't load the firmware and the Fritz!Cards USB-led is still blinking.

Any hints?

Martin

---

### Post by maitarco on 2007-05-05
Hi,
i have the same problem, i used ndiswrapper in ubuntu edgy then i tried de source of avm, but it doesn't work. did you find a solution?

---

### Post by jakob42 on 2007-05-23
Hey everyone.

I've got a very similar problem, I wanna describe further:
I've got an AVM Fritz!Box USB 2.0 and I want to use it as a viocebox. As far as I unterstand I'll need capi for that.

So I got the (2 year old!) linux-driver from the AVM-site and tried to compile it (after installing the essentials, linux-header, buidl-essentials etc.). It failed several times. I managed to adapt it to compile on my system (it seems that at least the USB-system changed...) The module loads now all right, but capiinfo doesn't finds any cards. What I installed:

[LIST]
[*]build-essential
[*]isdnutils
[*]isdnutils-base
[*]capiutils
[*]pppdcapiplugin
[*]isdnactivecards
[*]libcapi20-3
[*]libcapi20-dev
[*]linux-headers
[/LIST]
Some info:
```
root@waxford:~# lsmod|egrep capi\|fxusb\|isdn
capi                   17344  0 
capifs                  5896  2 capi
fxusb                 657880  0 
kernelcapi             39924  2 capi,fxusb
usbcore               131480  4 fxusb,ehci_hcd,uhci_hcd
```
```
root@waxford:~# lsusb |grep AVM
Bus 001 Device 004: ID 057c:1000 AVM GmbH 
```
```
root@waxford:~# capiinfo 
capi not installed - No such device or address (6)
```
```
root@waxford:~# egrep -v ^# /etc/isdn/capi.conf
fxusb           /usr/share/isdn/2.6.20-15/fus2base.frm DSS1    -       -       -       -
root@waxford:~# file /usr/share/isdn/2.6.20-15/fus2base.frm
/usr/share/isdn/2.6.20-15/fus2base.frm: data
```
I copied fus2base.frm from the windows driver, since I couldn't find such a file in the linux-driver and according to my howto I need this.

So thats all I've done:
[LIST]
[*]install the packages
[*]edit and compile AVM-driver
[*]edit /etc/isdn/capi.conf
[*]copy the firmware from windows
[/LIST]

Any ideas at all why its not working and suggestions what I could try are greatly appreciated. :-)
TIA, Jakob

---

### Post by jakob42 on 2007-06-06
> **jakob42 said:**
> Hey everyone.
I've got an AVM Fritz!Box USB 2.0 and I want to use it as a viocebox. As far as I unterstand I'll need capi for that.

Hi again.

I found some patches that made the sources compile *and* work (:-)), but my system crashed from time to time (often at boot up). I changed to an old Fritz!Card PCI for now (which works easy and great, but I only got one PCI slot), but I wanted to post the link to the patches: [LIST]
[*][The patches]("http://www.linkpool.de/fcpatches.html")
[*][A german howto]("http://www.linkpool.de/fcusb2.html")
[/LIST]

Regards, Jakob

---

