---
title: "usb printer detection"
date: 2012-02-07
forum: Hardware
---

### Post by benDavisNC on 2012-02-07
hi all,
i've gotten stuck trying to use an old lexmark (z22) printer with ubuntu 11.10 directly via usb. it worked fine back when i had ubuntu 11.4, but now nothing is detected no matter which method (cups browser or system settings), and lsusb doesn't even show anything. the closest i've gotten is when i followed this advice - [https://wiki.ubuntu.com/DebuggingPrintingProblems-](https://wiki.ubuntu.com/DebuggingPrintingProblems-) and ran this command - tail -f /var/log/syslog. i recieved this message at the end "Feb  7 17:30:10 ben-1215T udev-configure-printer: Device vendor/product is 1309:F002
Feb  7 17:30:10 ben-1215T udev-configure-printer: MFG:Lexmark MDL:Lexmark Z22-Z32 SERN:- serial:-
Feb  7 17:30:11 ben-1215T kernel: [ 1988.120143] usb 3-2: usbfs: process 3297 (usb) did not claim interface 1 before use
Feb  7 17:30:12 ben-1215T udev-configure-printer: no corresponding CUPS device found
"  

i guess my question is what can i do to have CUPS recognize my connected local printer, or is there a different route i need to take? thanks to anyone that can help with this headache.

ps. i'm running gnome 3 and not unity and my laptop is 64 bit.

---

### Post by wolfen69 on 2012-02-07
I believe cups no longer supports this model, being that it is 12 yrs old. But you can get the PPD file [here]("http://www.openprinting.org/ppd-o-matic.php?driver=lxm3200-tweaked&printer=Lexmark-Z22&show=0"). More info can be found [here]("http://www.openprinting.org/printer/Lexmark/Lexmark-Z22").

---

