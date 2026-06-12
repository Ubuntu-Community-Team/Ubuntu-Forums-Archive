---
title: "Intall Printer Lexmark X1150 on Lubuntu 16.04"
date: 2017-07-30
forum: Hardware
---

### Post by sed_faster on 2017-07-30
Hello,

I am trying install this printer ([http://support.lexmark.com/index?segment=SUPPORT&userlocale=EN_UK&locale=en&productCode=LEXMARK_X1150&page=product&frompage=null#1](http://support.lexmark.com/index?segment=SUPPORT&userlocale=EN_UK&locale=en&productCode=LEXMARK_X1150&page=product&frompage=null#1)) on Lubuntu 16.04. How can I do this?
I try following this topic ([https://ubuntuforums.org/showthread.php?t=1439074&page=3](https://ubuntuforums.org/showthread.php?t=1439074&page=3)) but before try anything I want know which best option/path to do/following!

Thanks

---

### Post by DuckHook on 2017-07-30
The instructions in your linked thread are ancient and obsolete. They are highly unlikely to work and may lead you badly astray. The Lexmark site that you link to has drivers and printer utilities for Debian systems. Ubuntu is derived from Debian and should install the .deb packages easily. While I have never used Lexmark printers, the download and installation appear to be straightforward. Just make sure you download the proper architecture (32-bit) or 64-bit), install using the Ubuntu Software Centre and you should be good to go.

If you prefer, you can wait for more detailed advice from a forum member who has a Lexmark printer.

Make sure you back up all important data before attempting a driver install.

---

### Post by pdc on 2017-07-31
Hi Edgar; honestly; there don't seem to be any drivers; I do remember there being a debian one; ages ago; but you had to edit it; and that was a bit tricky; I don't think you will get this to work on ubuntu; sorry

it doesn't get a mention on OpenPrinting [http://www.openprinting.org/printers/manufacturer/Lexmark](http://www.openprinting.org/printers/manufacturer/Lexmark)

---

### Post by sed_faster on 2017-07-31
Hello,

I can't find drivers to debian on this link: [http://support.lexmark.com/index?segment=SUPPORT&userlocale=EN_UK&locale=en&productCode=LEXMARK_X1150&page=product&frompage=null#1](http://support.lexmark.com/index?segment=SUPPORT&userlocale=EN_UK&locale=en&productCode=LEXMARK_X1150&page=product&frompage=null#1)

On my lubuntu 16.04 I try handle this task through "System Tools" -> "Printer" and I see this screens: [http://imgur.com/a/aqW3h](http://imgur.com/a/aqW3h) and [http://imgur.com/a/gfMHn](http://imgur.com/a/gfMHn)
But the system, this programs, freezing and I can't install any drivers to this printer. The highlight the printer lexmark X1150 plug in through usb on my desktop.

My main OS is Lubuntu but fist of all I try install this printer on windows 7. I can't handle this task on windows because I can't find drivers to 64 bits windows 7 :/ 
On this site ([http://support.lexmark.com/index?segment=SUPPORT&userlocale=EN_UK&locale=en&productCode=LEXMARK_X1150&page=product&frompage=null#1](http://support.lexmark.com/index?segment=SUPPORT&userlocale=EN_UK&locale=en&productCode=LEXMARK_X1150&page=product&frompage=null#1)) I have drivers to windows vista 64 bits but I can't put them work on windows 7!

---

### Post by DuckHook on 2017-07-31
> **Edgar_Oliveira said:**
> Hello,

I can't find drivers to debian on this link: [http://support.lexmark.com/index?segment=SUPPORT&userlocale=EN_UK&locale=en&productCode=LEXMARK_X1150&page=product&frompage=null#1](http://support.lexmark.com/index?segment=SUPPORT&userlocale=EN_UK&locale=en&productCode=LEXMARK_X1150&page=product&frompage=null#1)
I used [this]("http://support.lexmark.com/index?page=driversdownloads&linkSelected=node2%5Esubnode2&locale=en&userlocale=EN_US") link. However, be prepared for disappointment. As *pdc* states:
> **pdc said:**
> …there don't seem to be any drivers; I do remember there being a debian one; ages ago; but you had to edit it; and that was a bit tricky; I don't think you will get this to work on ubuntu…
Moreover:
> …it doesn't get a mention on OpenPrinting [http://www.openprinting.org/printers/manufacturer/Lexmark](http://www.openprinting.org/printers/manufacturer/Lexmark)
…is bad news. This means that no one else with this model of printer has reported success.

The drivers I linked to are for other models of printers. Sometimes, it is possible to get one for a newer model working with your old one (or vice versa). However, this involves trial & error, and is a long, drawn out process. Your success will depend on your patience, hacking chops and luck.
> My main OS is Lubuntu but fist of all I try install this printer on windows 7. I can't handle this task on windows because I can't find drivers to 64 bits windows 7 :/ 
On this site ([http://support.lexmark.com/index?segment=SUPPORT&userlocale=EN_UK&locale=en&productCode=LEXMARK_X1150&page=product&frompage=null#1](http://support.lexmark.com/index?segment=SUPPORT&userlocale=EN_UK&locale=en&productCode=LEXMARK_X1150&page=product&frompage=null#1)) I have drivers to windows vista 64 bits but I can't put them work on windows 7!…I can't help you with Windows. Haven't used it in years. Perhaps someone on the Windows forums can help. Or contact Lexmark support.

---

