---
title: "Epson ET-5850 printing problems"
date: 2020-12-29
forum: Hardware
---

### Post by menschmarcus on 2020-12-29
Hello hardware-friends,

I am using Ubuntu 20.04 LTS and the printer ET-5850. I have two poblems:

1) In "Settings &#8594; Printers" the printer appears once, but all settings are disabled. In "Printer Options" all options are disabled as well.
[IMG]https://media-cdn.ubuntu-de.org/forum/attachments/19/52/9214591-Epson_problem_1.png[/IMG]

2) If I want to print a document two almost identically names printers appear. If I choose the upper one, I cannot print as the option "Print" is disabled. Selecting the lower one (EPSON_ET_5850_Series) lets me click on "Print", but I can print only one copy. If I want to print e.g. 5 copies, the printer stops and "beeps" after the first copy. This is unfortunatesince I am a teacher and I need to print a document 20 times or so.
[IMG]https://media-cdn.ubuntu-de.org/forum/attachments/19/52/9214591-Epson_problem_2.png[/IMG]

I have completely removed (apt purge) cups, removed the folders /usr/share/cups and /etc/cups and the official Epson drivers and the Epson-printing-utility – and then reinstalled everything. Both problems are still there. The Epson support says they do not support Linux, sadly. Anybody here who can help me?


Happy Merry post-Christmas greetings from Germany
Marcus

---

### Post by brian_p on 2020-12-29
You should have a PPD in /etc/cups/ppd, probably named like the lower entry, EPSON_ET_5850_Series. This is YOUR_PPD. Give what you get for ```
sudo grep "*cupsManualCopies" /etc/cups/ppd/YOUR_PPD
``` ```
sudo grep "*PCFileName" /etc/cups/ppd/YOUR_PPD
```

Stop cups-browsed: ```
systemctl stop cups-browsed
``` Do any printers disappear from the list?

Are you using a USB or a wireless connection?

---

