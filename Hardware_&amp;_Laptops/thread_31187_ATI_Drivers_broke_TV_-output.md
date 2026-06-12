---
title: "ATI Drivers broke TV -output"
date: 2005-05-02
forum: Hardware &amp; Laptops
---

### Post by Laterix on 2005-05-02
I installed ATI drivers successfully by following instructions of this [HOWTO thread](http://www.ubuntuforums.org/showthread.php?t=24557). Everything went well, but now I can't see TV picture anymore. I have pretty old Hauppauge TV-tuner (BT878 analog) and I've been using Zapping program to watch TV. TV-audio is still working as well as Teletext. Only actual TV-picture is missing. Is there anyway to get ATI drivers work with my TV-card?

---

### Post by Laterix on 2005-05-02
Anyone? I'm sure that I'm not the only one with this problem.

---

### Post by sksbir on 2005-05-18
[QUOTE=Laterix]Anyone? I'm sure that I'm not the only one with this problem.[/QUOTE]

Perhaps this may help you : 

[http://forum.ubuntu-fr.org/viewtopic.php?id=2487&p=4](http://forum.ubuntu-fr.org/viewtopic.php?id=2487&p=4)

search "HOWTO" on the page.
In order to get totem and tvtime working again after installing fglrx driver, i had to put
```
Option      "VideoOverlay" "on"
```
in the driver section (same place where you replace "ati" wih "fglrx").

---

### Post by JurB on 2005-10-10
I was using Tvtime and had the same problem after installing the ati drivers....
This thread solved my problem, i just added "option      "VideoOverlay" "on""

---

