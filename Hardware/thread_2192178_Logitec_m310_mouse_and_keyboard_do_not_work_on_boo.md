---
title: "Logitec m310 mouse and keyboard do not work on boot"
date: 2013-12-06
forum: Hardware
---

### Post by Subcomfreak on 2013-12-06
I have had this problem for quite a long time now, and finally the aggravation has got the best of me. I have a unified logitec keyboard and mouse combo. In GRUB and in windows the keyboard and mouse work fine together. When I boot into xubuntu (12.04) they are not recognized. I have to pull the usb dongle in and out several time before finally both will be recognized. After they are recognized they wrok perfectly for the rest of the session. Any hints?

---

### Post by Subcomfreak on 2013-12-10
I'm still having issues with this. Any log files that I need to provide I can.

---

### Post by Bashing-om on 2013-12-10
Subcomfreak; Hello.

Regret such a delay in a response.

Many times in a situation as you describe, it is a bios setting for usb devices not set properly. May I suggest that you check and make sure "legacy" settings are disabled, and PNP (plug and play) is enabled ?

[INDENT]just my thought
[/INDENT]

---

### Post by Subcomfreak on 2013-12-12
PNP is enable and legacy settings are disabled, but the problem still persists.

---

### Post by brisius101 on 2013-12-17
I have a similiar problem.

I'm a brand new user of Linux. Loaded Ubuntu 13.10 on a brand spanking new hdd without any other OS. I have a wired usb mouse and keyboard.

At first when I would boot the mouse wouldn't be recognized but the keyboard would. Replugging the mouse would fix the problem until I rebooted. I tried rebooting many times in different ports and with a different mouse and I got the same thing. Then on one of the reboots, the mouse worked but the keyboard didn't. Now the only the keyboard doesn't work on reboot and the mouse works. Legacy is disabled and pnp is enabled.

Seems like the Ubuntu boot up can only see one usb device at a time. I'm at a place were I don't have any other usb devices to plug in but a week I will be home were I have external hdd and other items I can plug in. Until then would any of you have any suggestions?

---

