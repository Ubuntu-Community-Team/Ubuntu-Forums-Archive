---
title: "Bluetooth &amp; uhci_hcd:usb* power usage on NC8000"
date: 2009-06-15
forum: Hardware
---

### Post by monikersupreme on 2009-06-15
I've noticed with powertop that my two powerhogs are:

43.8% (127.4) USB device 3-1 : Bluetooth by hp (ACTIONTEC)
36.7% (106.9) <interrupt> : uhci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3,

...respectively. However as I am using a Bluetooth mouse I'm not sure if this is necessary. I've noticed that even if I keep the mouse idle the Bluetooth usage remains high... again dunno if this is relevant. I'm puzzled by the second "uhci_hcd:usb*" but I think this may be the wifi unit in my NC8000?

Any advice/suggestions would be much appreciated!

---

### Post by shylingo on 2010-06-18
same with me. my logitech bluetooth mouse is always connected. when using it it seems to be kept away from sleeping (eg. powersave mode). 

also the battery usage has exploded: using windows i have to change batteries once every 7th week. and now, ubuntu, same mouse, same batteries are gone within 10 days.

how can i configure bluetooth - or better - the bluetooth sleep policy - in a way which allows devices to be put to sleep?

i'm running ubuntu 10.04 on a thinkpad t42.

thanks a lot - every hint is appreciated.

---

