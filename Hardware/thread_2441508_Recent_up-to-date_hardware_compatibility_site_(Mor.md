---
title: "Recent up-to-date hardware compatibility site? (More specifically, USB/PCI Wifi card)"
date: 2020-04-24
forum: Hardware
---

### Post by Albert_Zeyer on 2020-04-24
Maybe this gets asked often here, so sorry if this is duplicated. (Maybe you can point me where to look.)
I'm specifically looking for a USB Wifi card now (maybe also PCI), but I guess the same question could come up for many other devices as well.

I searched via Google but I'm not really sure which of the resources are really up-to-date. Maybe Ubuntu should have a wiki for that? Or maybe it has?

E.g. some sites I found:

* [https://certification.ubuntu.com/](https://certification.ubuntu.com/): But this does not seem to list individual hardware? (E.g. USB wifi cards.)
* [https://community.linuxmint.com/hardware/](https://community.linuxmint.com/hardware/)
* [https://askubuntu.com/questions/389176/is-there-a-database-of-linux-compatible-hardware](https://askubuntu.com/questions/389176/is-there-a-database-of-linux-compatible-hardware)
* [https://wiki.debian.org/WiFi](https://wiki.debian.org/WiFi): Looks outdated? Also, there is only a single confirmed supported device, and that one does not work out-of-the-box with Linux, you would have to compile a driver yourself from some GitHub repo. Of course I would prefer sth which works out-of-the-box with a recent Linux installation. But from that wiki, it seems there is simply no USB wifi card which works out-of-the-box? Is that true?
* [http://www.tldp.org/HOWTO/Hardware-HOWTO/](http://www.tldp.org/HOWTO/Hardware-HOWTO/): From 2007, and not updated?
* [https://linux-hardware.org/](https://linux-hardware.org/): Looks good, but a bit hard to search. Where do I find a list of USB wifi cards?
* [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported): Also good? But it's just a huge list. I don't really now which of these to take. Just the first?

Some of these sites seem to be up-do-date mostly. But then they often just have such a huge list. I don't really see the (average/estimated) price, or the release date of this hardware, or maybe some ranking. So it's kind of hard to make a decision based on this list, what to buy now. Or how would you suggest to do that decision?

---

### Post by CelticWarrior on 2020-04-24
They're all hopelessly outdated and incomplete. The certification program depends on manufacturers submitting their products for certification therefore is necessarily limited. There's a lot more hardware that works and doesn't make the list.

---

### Post by Albert_Zeyer on 2020-04-24
So, how would you proceed when you want to buy a USB wifi stick? I'm a bit lost. Check Amazon, search for "usb wifi", go through the list, filter some good rated, and then double check if there are reports somewhere (Google?) that report this USB stick works? This seems like kind of complicated and annoying. Is that how everyone is doing it?

If there is really not a good solution yet, like e.g. a site for Linux-compatible-hardware, with ranking, prices, maybe comments, maybe we should create such a site? Or extend/update e.g. [https://linux-hardware.org/](https://linux-hardware.org/) or so?

---

### Post by CelticWarrior on 2020-04-24
Yes, for USB sticks it's not easy. OTOH, for PCI just choose one with an Intel chipset and you can't go wrong. Unless it's a brand new chip,you may have to wait a bit for native kernel support.

---

### Post by CatKiller on 2020-04-24
> **Albert_Zeyer said:**
> Is that how everyone is doing it?

There are loads that advertise their compatibility with Linux. Go with one of them. If you're buying hardware and the manufacturer *doesn't* support the operating system you're using then it's up to you to determine if it will work regardless, of course.

---

### Post by Yellow Pasque on 2020-04-24
> **Albert_Zeyer said:**
> So, how would you proceed when you want to buy a USB wifi stick? I'm a bit lost. Check Amazon, search for "usb wifi", go through the list, filter some good rated, and then double check if there are reports somewhere (Google?) that report this USB stick works? This seems like kind of complicated and annoying. Is that how everyone is doing it?

Yeah, that's basically how I'd do it. Rather than focusing on the adapter's brand/model, I'd focus on what chipset it uses. Unfortunately, manufacturers don't always make that info available or easy to find.
As for the hardware lists, they get outdated fairly quickly.

---

### Post by CelticWarrior on 2020-04-24
> **Yellow Pasque said:**
>  Rather than focusing on the adapter's brand/model, I'd focus on what chipset it uses. Unfortunately, manufacturers don't always make that info available or easy to find.

+100
Absolutely. The chipset is what matters and only that matters.

---

