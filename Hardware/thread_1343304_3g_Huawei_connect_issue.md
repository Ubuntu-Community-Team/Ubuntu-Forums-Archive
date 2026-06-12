---
title: "3g Huawei connect issue"
date: 2009-12-01
forum: Hardware
---

### Post by Shikos on 2009-12-01
I've just got my brand new Acer One d250, on which I installed Ubuntu Netbook Remix, and I've also got some 3G internet. I have to connect it via a dongle named Huawei and the model is E1752. Unfortunately this doesn't work.

I followed this [article]("http://www.blogcatalog.com/blog/iwrite-2/dbbfb38ae5ef9ccef8540aad7f9edbd6"). This told me to download and install usb_modeswitch, which I did. Afterwards I should run *sudo usb_modeswitch* while the dongle was plugged in

It just gave me this response

```
 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 0.9.7 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

No default vendor/product ID given. Aborting.
```I looked for updates and found one. When i ran *sudo usb_modeswitch *again*, *it just gave me the same response. Then I looked up, if I've got the libusb 0.1.12, and I found out I've got the latest version.

Finally I can tell that I works on my other computer, in which Linux Mint has been installed.

I'm pretty lost at this point. I'm hoping some off you guys are way smarter than me. what should I do?

---

### Post by Shikos on 2009-12-02
I just found out. i had to paste the code into the config  file again once it was updated. Silly me :oops:

---

