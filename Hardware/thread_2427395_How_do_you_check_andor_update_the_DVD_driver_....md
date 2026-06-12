---
title: "How do you check and/or update the DVD driver ..."
date: 2019-09-21
forum: Hardware
---

### Post by dagmann on 2019-09-21
I'm a Knoob.

I have a Plextor PX-891SAF. It works great in Kubuntu 18.04.
However I cannot find a way to display its current driver nor how to update it.

I would appreciate any help.

---

### Post by uRock on 2019-09-21
If I'm not mistaken, then it's built into the kernel. What are you looking to accomplish?

---

### Post by dagmann on 2019-09-21
I would like to make sure that it is current. But I suppose it really doesn't matter as long as it works.
It appears that Plextor does not have any software for Linux.

---

### Post by maglin2 on 2019-09-21
Does 
```
[FONT=monospace][COLOR=#000000]ubuntu-drivers devices[/COLOR][/FONT]
```
in terminal show anything?

---

### Post by SeijiSensei on 2019-09-21
Most DVD players nowadays have standard SATA interfaces. I don't think any of them use custom drivers. Is there some function that seems unsupported? I looked at the list of installed modules on two different machines using "lsmod" and don't see anything specific to their DVD players.

---

### Post by dagmann on 2019-09-21
thanks everyone

---

### Post by Yellow Pasque on 2019-09-23
Are you talking about the firmware version? IIRC, lshw shows it as well as maybe the cd-drive command.

```
sudo lshw -C storage
```

A lot of times, you'll need Windows to actually update the firmware though.

---

### Post by hk42 on 2019-09-25
> **Yellow Pasque said:**
> 

A lot of times, you'll need Windows to actually update the firmware though.

+1 
Same thing to update/ restore the BIOS of  a motherboard/mini PC
I had the very bad idea to unselect BIOS USB support on a mini PC that had only USB ports.
By chance I found a Window software to flash it one year later.
Now I can go again in the BIOS or run Linux from a USB dongle.

---

