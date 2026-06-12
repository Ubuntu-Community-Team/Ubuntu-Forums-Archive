---
title: "acer timeline 1810tz: run Ubuntu in ACPI mode?"
date: 2010-07-29
forum: Hardware
---

### Post by kilauea on 2010-07-29
I have an acer timeline 1810tz and tried both openSUSE 11.2 and Ubuntu  10.04 (64bit). The only way however to run linux on this notebook is to change  in the BIOS the ACPI to IDE mode. 

That's ok but the battery time is however "worse" than it should be. In  the example its maybe 4 hours, when it makes 6 hours in win7 and ACPI  mode. How is it possible to run this kind of laptop on ACPI mode?
I saw few suggestions on the net to update the bios (but I do not have windows installed on the laptop...).

By the way Ubuntu works great on the acer timeline but I had some bugs using openSUSE.

thanks for comments.[IMG]http://c0491962.cdn.cloudfiles.rackspacecloud.com/images/questions/images/smilies/smile.gif[/IMG]

---

### Post by kilauea on 2010-07-31
For those interested, I found a way to run ubuntu 10.04 in the AHCI mode  (sorry not ACPI)instead of IDE on the ACER timeline 1810TZ. That might  save some battery power, I have to check it out.

You just have to update your bios. You can do it without windows using a USB stick and UNetbootin, its all described [http://www.netbooktech.com/tag/acer-...-instructions/]("http://www.netbooktech.com/tag/acer-aspire-one-bios-update-instructions/")

I used the BIOS 3310 from the acer homepage. The file that you have to  execute is not a bat file as described in the link above, but  ZH7_3310.exe (that I would just copy in the directory of the USB drive,  here called C[IMG]http://c0491962.cdn.cloudfiles.rackspacecloud.com/images/questions/images/smilies/smile.gif[/IMG]

However, be careful handling around with BIOS, that can have bad consequences (backup your files).

by the way, if you have problems with the internal mic and skype this link helped me: contractattorneys.wordpress.com/2010/05/17/fixing-low-or-no-microphone-volume-on-skype-in-ubuntu-10-04-and-why-im-leaving-mac/

---

