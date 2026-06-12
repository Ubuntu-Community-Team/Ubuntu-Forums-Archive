---
title: "KWorld Plus TV Analog PCI Lite Not Working"
date: 2007-09-02
forum: Hardware &amp; Laptops
---

### Post by BloodyTails on 2007-09-02
I have a KWorld Plus TV Capture card, it's the Analog PCI Lite version and it's detected as UNKNOWN/GENERIC or Default in TVTime.

What on earth am I suppose to do in order to watch TV on this thing? I set it to NTSC-US/Cable and it still doesn't work.

I also found some MythTV garbage that just made things worse.

I just bought this computer, it came with Ubuntu and it came with this Card already in it.

---

### Post by Colbrac on 2007-10-10
I recently bought the same card. To use this card you have to:
- add the following line to the file /etc/modprobe.d/options (for example by issueing the command 'gksudo gedit /etc/modprobe.d/options')
```
options saa7134 card=63 tuner=56
```

- add the following line to the file /etc/modules
```
tuner
```

After a reboot you should be able to watch tv using for example the program 'tvtime'.

---

