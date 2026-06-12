---
title: "amd catalyst control center administrative"
date: 2011-10-29
forum: Hardware
---

### Post by minipot on 2011-10-29
[SIZE=3][COLOR=Black]dear people pleez help I have a 2 monitor setup an ati raedon hd 3200 graphics as catalyst control calls it and an IBM t55d and am trying to setup with ubuntu 11.10 however when using amd catalyst control center it mirrors the displays and when I try to set from cloned displays to multi displays and i apply it it just closes and nothing happens.[/COLOR][/SIZE] [SIZE=3]same with normal display control when I turn of mirror it says the selected configuration can not be applied:
requested position/size for CRTC 148 is outside the allowed limit: position=(800, 0), size=(1024, 768), maximum=(1600, 1600) 

what does this mean and what do I do?[/SIZE]

---

### Post by Mark Phelps on 2011-10-29
Catalyst has lots of problems with 11.10 as the Hardware Drivers options installs a version that is incompatible with the Gnome version in Ubuntu.

You would do better removing the Catalyst drivers and going with the default open-source drivers.  I'm using them with an ATI HD 4290, dual screens, and it works just fine.

---

### Post by minipot on 2011-10-29
OK where do I get these drivers ?

---

