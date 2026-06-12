---
title: "Error message - need to disable bluetooth"
date: 2012-09-29
forum: Hardware
---

### Post by naviehuynh on 2012-09-29
Hi guys,
its my first post here and im also a newbie in Ubuntu. I recently got an error message like this:
[IMG]http://i.imgbox.com/abktu5iv.png[/IMG]
I guess the problem is related to my bluetooth modemn. I don't really use it in Ubuntu so it's ok to disable the modemn anyway. How can I do this?

---

### Post by jerrrys on 2012-09-29
Hi naviehuynh, welcome to the forums :)

When [posting screenshots]("http://ubuntuforums.org/showthread.php?p=4527031#post4527031") use the paperclip option.

For Bluetooth, uncheck it from your [autostart list]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=disable+bluetooth+12.04&as_qdr=all&sa=Google+Search&lang=en").

---

### Post by 2F4U on 2012-09-29
It may also be necessary to disable the kernel modules associated with bluetooth. On my machine, these are the relevant kernel modules:
- bnep
- rfcomm
- btusb
- bluetooth

It should be sufficient, to create a file in /etc/modprobe.d, for example /etc/modprobe.d/bluetooth.conf and put all the modules in there with the term blacklist in front of the module:

blacklist bnep
blacklist rfcomm
blacklist btusb
blacklist bluetooth

---

