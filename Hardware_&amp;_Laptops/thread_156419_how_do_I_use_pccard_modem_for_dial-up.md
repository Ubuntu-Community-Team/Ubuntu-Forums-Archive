---
title: "how do I use pccard modem for dial-up?"
date: 2006-04-07
forum: Hardware &amp; Laptops
---

### Post by whoa_551 on 2006-04-07
I am trying to use a AmbiCom56k PCCard modem in place of my internal modem (can't get driver installed on internal one). Ubuntu detects the pccard modem, and using the typical commands (lsmod, cardctl ident, etc.) everything seems okay with it, and the correct driver (serial_cs) is being used. So, my question is, how do I configure Ubuntu to use my PCCard modem for dial-up?  Specifically, how do I find out what device my pccard is assigned to (i.e. /dev/ttySL0, /dev/ttySL1, etc.)?

---

### Post by Matchless on 2006-04-08
Hi,
   This is the way I do it. Connect up serial modem, configure KPPP to use modem, go to Device tab in KPPP and select a device, under Modem tab use Query Modem button to test, if your modem lights start flickering and you get a positive result on the screen you have a go. Try them all that way. Mostly Com1 will be /dev/ttys0 and Com2 /dev/ttys1. A USB external modem needs drivers installed and compiled same as a PCCard modem. For full details on installing modems go to Wikki and Dialupmodemhowto.
Good luck.

---

