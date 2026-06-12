---
title: "I want to repport that I can't use Ubuntu based distros on G3 3590"
date: 2021-02-14
forum: Hardware
---

### Post by yandiro on 2021-02-14
I have tried several Ubuntu based distros, including Ubuntu itself, but I always get the same errors.

Computer freezes on the same stages after booting:
before asking for user and login info
after asking for user and login info
right before desktop environment loads

So I have to force shutdown (by holding the power button) 3 times to be able to use the computer.

This happens quiet often.

Sometimes computer simply freezes for no reason as well, but I can't really say much about it.

Please don't mind me sending the system info using Fedora!
[https://imgur.com/a/B008sDg](https://imgur.com/a/B008sDg)
[IMG]https://imgur.com/a/B008sDg[/IMG]
[IMG]http://imgur.com/a/B008sDg[/IMG]
[IMG]https://imgur.com/a/B008sDg[/IMG]
[IMG]https://imgur.com/a/B008sDg[/IMG]

---

### Post by CelticWarrior on 2021-02-14
Welcome.

The situation is very simple, actually.

First of all make sure that the motherboard's firmware (UEFI) is updated and also SSD's.
Then you need to understand that you have Nvidia Graphics and those often require Nvidia proprietary drivers. With any current Ubuntu the drivers can be automatically installed if you select "install third-party drivers, codecs, etc". If you don't then you need to use 'nomodeset' to boot and then install the required drivers.

---

