---
title: "Still can't get MP600 to actually print under 9.10"
date: 2009-11-04
forum: Hardware
---

### Post by rmp73 on 2009-11-04
Hi,

After following suggestions on other forums about downloading drivers from Canon Asia and then converting them from rpm to deb etc. I've got to the stage of installing my MP600 only to find it won't print on either configuration (usb or cnij_usb:/dev/usb/lp0) despite my best efforts at editing printers.conf etc.

Anyone have any better luck?

Here's a snapshot of [https://localhost:631/printers/](https://localhost:631/printers/)
[http://ubuntuforums.org/attachment.php?attachmentid=134673&stc=1&d=1257340283](http://ubuntuforums.org/attachment.php?attachmentid=134673&stc=1&d=1257340283)

Here's the transcription of /etc/cups/printers.conf
# Printer configuration file for CUPS v1.4.1
# Written by cupsd on 2009-11-04 12:31
<DefaultPrinter MP600>
Info Canon MP600
Location ryan-vaio
MakeModel Canon MP600 Ver.2.70
DeviceURI usb://Canon/MP600
State Idle
StateTime 1257337852
Type 8425500
Filter application/vnd.cups-raw 0 -
Filter application/vnd.cups-postscript 0 pstocanonij
Filter application/vnd.cups-command 0 commandtops
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>
<Printer VaioMP600>
Info Canon MP600
MakeModel Canon MP600 Ver.2.70
DeviceURI cnij_usb:/dev/usb/lp0
State Idle
StateTime 1257336569
Type 8388612
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>

---

### Post by mjcritchie on 2009-11-06
Don't know if this helps, but I have an MP600 too and have always had problems getting it to work when I upgrade Ubuntu.

This time (9.10) I just selected the driver for the MP610, obviously the MP600 wasn't listed, from the dialogue box that came up when Ubuntu told me it couldn't find the right driver for my printer.

I haven't printed a lot of things yet, but so far it works fine.

~ Mike

---

### Post by rmp73 on 2009-11-07
Brilliant, thanks - it seems to work a treat!

---

### Post by mjcritchie on 2009-11-10
Scratch that.

I've just tried printing .xls and .pdf documents and they look awful!

Back to the drawing board :(

---

### Post by mjcritchie on 2009-11-10
Have tried using the MP500 driver instead.

That seems to be OK for printing .xls docs.

---

