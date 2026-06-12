---
title: "ThinkPad T420, DVD-tray keeps on openning"
date: 2018-08-29
forum: Hardware
---

### Post by ereus on 2018-08-29
[COLOR=#242729][FONT=Arial]Hello there, I'm having an issue with my ThinkPad T420. I'm currently dual-booting with Ubuntu latest LTS and Windows 10 and the problem persists only on Ubuntu. Sometimes, when even the slightest pressure applied to the computer, the DVD-tray just keeps on opening, even typing on the machine cause the hardware inside spin and the DVD-tray to open. I cannot reproduce such problem on Windows, only a Ubuntu thing. I could always just remove the DVD tray out but for now it's not a feasible solution.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Any clues? Thanks in advance![/FONT][/COLOR]

---

### Post by Yellow Pasque on 2018-08-30
Maybe this would help: [https://superuser.com/questions/524945/disable-the-dvd-eject-button-on-a-thinkpad-running-linux/687231#687231](https://superuser.com/questions/524945/disable-the-dvd-eject-button-on-a-thinkpad-running-linux/687231#687231)
Note the path is different, probably /lib/udev/rules.d/60-cdrom_id.rules if Ubuntu is the same as Debian sid.

---

