---
title: "Desktop won't load on a fresh install"
date: 2008-11-14
forum: General Help
---

### Post by xer0kill on 2008-11-14
Trying to get 8.10 up and running on a friend's machine. Pentium 2.0 single core, 1GB RAM. (HP Pavilion a518x)

I get the same results whether running the Live CD or running the copy installed on the HDD. It boots up fine to the login screen, but after logging in it does nothing. It just shows the standard background color and the mouse pointer and nothing loads. The only error I've seen is ACPI: Failed to load System Description Tables. or something of that nature. I've disabled the acpi and gotten rid of that message, but it still won't load the desktop. Anybody have an idea of how to proceed with this?

I should also add that I have already run the disk check program and it says the disk is fine.

Also, the mouse pointer moves fine, but I can't get a terminal with ALT+F1 etc.

---

### Post by dcstar on 2008-11-14
> **xer0kill said:**
> Trying to get 8.10 up and running on a friend's machine. Pentium 2.0 single core, 1GB RAM. (HP Pavilion a518x)
........

8.10 no longer supports old Nvidia video chipsets (which I suspect may be used), I would recommend trying 8.04 (which is a LTS release).

---

### Post by xer0kill on 2008-11-15
> **dcstar said:**
> 8.10 no longer supports old Nvidia video chipsets (which I suspect may be used), I would recommend trying 8.04 (which is a LTS release).

Ah hah. Okay, I'll give that a shot today. Thanks!

---

### Post by CatKiller on 2008-11-15
Actually, unless your friend has put a graphics card in there, it probably has integrated Intel graphics, which don't need proprietary drivers.

Also, it's Ctrl-Alt-F1 to get to a virtual console.

---

### Post by xer0kill on 2008-11-15
> **CatKiller said:**
> Actually, unless your friend has put a graphics card in there, it probably has integrated Intel graphics, which don't need proprietary drivers.

Also, it's Ctrl-Alt-F1 to get to a virtual console.

Ah. Yeah, that's what I meant (ctrl+alt+f1). doesn't work... :( I'll try to boot up a live CD of 8.04 because I really don't know what else to do at the moment.

And yea, it's just integrated graphics.

---

### Post by xer0kill on 2008-11-15
8.04 doesn't want to work either. I think I may have figured out the issue though. I checked the xorg.conf and it's got no Device section. Seems that maybe it has had some issues figuring out the settings for this ancient LCD monitor. Looks like I've got some more research to do!

---

### Post by TMaC750 on 2008-11-15
I too have the same issues.....

IntelD845GVSR MB 80gig WD hard drive 512megs RAM

I had 8.04 installed and then went to Mandriva and wiped HD clean and tried to install either 8.04 or 8.10 with the same results.:popcorn:

I have a year old ViewSonic monitor.

---

