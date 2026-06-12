---
title: "usb midi controller suddenly not working BITWIG UBUNTU STUDIO"
date: 2018-05-22
forum: Hardware
---

### Post by thevmgas on 2018-05-22
hi all
so my korg nanokontrol suddenly stopped reliably functioning. i see it recognized in jack but when i try to map it in Bitwig there is no interaction between the device and software
on a random reboot it started to work and next few attempts i got the same results of no response
i tried to map in other software as well and was left with the same situation
the device is powered and recognized but Bitwig and a couple other programs seem to be incapable of connecting
any ideas?

---

### Post by kazakore on 2018-05-23
Does it show correctly is lsusb? What messages do you get in dmesg when you connect it?

Which MIDI Driver are you using? Seq or Raw (Alsa?)?? As you are using Bitwig I assume you are using Jack audio server?? If you use this via qjackctl there is an option to select this under Settings. I've found I need it set to Seq....

---

