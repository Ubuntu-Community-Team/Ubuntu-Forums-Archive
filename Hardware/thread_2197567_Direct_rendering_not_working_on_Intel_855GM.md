---
title: "Direct rendering not working on Intel 855GM"
date: 2014-01-04
forum: Hardware
---

### Post by neural_adapter on 2014-01-04
Hello,
I am unable to get direct rendering to work on an old Dell Latitude D505 with the Intel G855GM VGA. I use Lubuntu 13.10 with fake PAE.

[ATTACH]249210[/ATTACH]
[ATTACH]249211[/ATTACH]

Xorg.0.log: [http://pastebin.com/NsuQJDTx](http://pastebin.com/NsuQJDTx)

---

### Post by neural_adapter on 2014-01-04
I was able to get it to work with the following workaround.
> 
User reported a work-around:

Edit (or create) /etc/X11/xorg.conf as follows: (ugh, can't format, should be a tab before each line except the first and the last).

Section "Device"
Identifier "Intel Graphics"
Driver "intel"
Option "AccelMethod" "uxa"
EndSection

Restart X (reboot, restart your display manager, whatever). Colors are back to the way they used to be and flash works.


---

