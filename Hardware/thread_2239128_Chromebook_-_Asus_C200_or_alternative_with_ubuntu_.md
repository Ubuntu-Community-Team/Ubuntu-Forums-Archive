---
title: "Chromebook - Asus C200 or alternative with ubuntu + windows possibility"
date: 2014-08-12
forum: Hardware
---

### Post by kaktux on 2014-08-12
hi there,

i am currently looking for a netbook like pc for my work. So far i like the specifications (espacially the no-fan and battery time) of the Asus C200 (with 2 or 4gb ram).
A minus is that its a chromebook - but as far as i can see ubuntu can be installed without a problem.
But also i need some programs for work that only work on windows - which i am not quite sure if this can be done on a chromebook.

So - the specs are: 249$ 2gb version, 16gb hd 329$ for 4gb, 32gb hd - about 10-12 hours battery, no fan, Celeron N2830, 2x2,16ghz.

So my questions are:
Do you know if Ubuntu (+windows) can be easily installed on a chromebook (easy means : i know the console - but i don't use it very often - so an average experienced linux user)??

Or:
Can you recommend a alternative netbook-like pc that will suit me and comes with linux (or blank) as it is??

---

### Post by tista on 2014-08-20
Hi kaktux ;)

I've been working with Utopic Gnome on my ASUS C200 chromebook (4GB-RAM&32G-SSD model) via crouton.
Maybe I could give some answers for you about it.

**1. Chromebook can't run Win**
Basically, C200's hardware (and most of chromebook as well) only works on LinuxOS/ChromeOS, and drivers for win didn't appeared today, so it would be damned useless even if you could install it on your chromebook (no wifi, bluetooth, touchpad, keyboard, and any other ports).

**2. C200 can't accept for Chrubuntu today I suppose**
Compared with Acer C720 series, in contrast, it might be so hard to install chrubuntu on our C200 today. On my some install tests, C200 won't accept for any UEFI/legacy install medias, like rufus, unetbootin, and so. It only can run Chrome's recovery media, I suppose. And chrubuntu seemed to be installed fine, but it could not be kicked via C200 firmware (maybe UEFI).

**3. crouton has a couple of degradation to run**
Crouton devs work so great, but it still has some issues on our chromebooks.
[LIST=1]
[*]802.11AC dual-band wireless INTEL-AC7260 would need to disable power-saving feature with commands.
[*]systemd leads some unexpected results on crouton.
[*]Wifi/Bluetooth can be controlled only from ChromeOS init services.
[*]some more...
[/LIST]

Anyway I think you'd better to buy a windows notebook/ultrabook/netbook and to run dual-booted ubuntu... ;)

Best regards,
Tista

---

