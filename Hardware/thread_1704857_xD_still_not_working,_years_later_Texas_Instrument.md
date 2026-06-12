---
title: "xD still not working, years later: Texas Instruments 5-in-1 Multimedia Card Reader"
date: 2011-03-11
forum: Hardware
---

### Post by sisyphus1978 on 2011-03-11
I use a usb card-reader that includes xD and it works fine. However my internal netbook SD slot does not read xD although with windoze it does.

My solution: purchase a cheap card reader and hope that sometime in the future this functionality is improved.

There may be alternative solutions. Good luck.

---

### Post by dionyself on 2012-07-11
go to /etc/default/grub
uncomment:
#GRUB_TERMINAL=console
[COLOR=Red]GRUB_TERMINAL=console[/COLOR]

go to  /etc/rc.local
before:    [COLOR=Red]exit 0[/COLOR]
add:
[COLOR=Red]modprobe acpiphp[/COLOR]

run:
[COLOR=Red]update-grub[/COLOR]

restart and you are done!

---

### Post by suaf on 2012-12-25
> **dionyself said:**
> go to /etc/default/grub
uncomment:
#GRUB_TERMINAL=console
[COLOR=Red]GRUB_TERMINAL=console[/COLOR]

go to  /etc/rc.local
before:    [COLOR=Red]exit 0[/COLOR]
add:
[COLOR=Red]modprobe acpiphp[/COLOR]

run:
[COLOR=Red]update-grub[/COLOR]

restart and you are done!

Did not work for me at all. Moreover, I now get an error-message on startup: "No Graphic Control selected" or something similar.

---

