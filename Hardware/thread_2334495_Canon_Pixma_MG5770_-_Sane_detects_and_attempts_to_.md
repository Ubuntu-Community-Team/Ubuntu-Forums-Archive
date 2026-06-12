---
title: "Canon Pixma MG5770 - Sane detects and attempts to use it but I/O error"
date: 2016-08-19
forum: Hardware
---

### Post by timonoj on 2016-08-19
Hi, 

I just purchased this multifunction scanner/printer because of its wifi connectivity and Linux drivers, but I'm having a bit of trouble to make it work. 
After installing the sane ppa, I finally got it detected by skanlite and simple-scan. But whenever I try to scan something, I get an error pop up that says "Error during device I/O" after some seconds. The scanning progress bar moves actually, reaching mostly anywhere between 3% and 15%. In Simple scan I can even see the portion of the image that it successfully scanned. 
After this error, the scanner (usually) gets completely stuck for good. It stays in the scanning task, having a prompt in the LCD saying "Scanning". If I try to hit the cancel panel button it says "Processing, please wait momentarily", but it's still stuck. The only thing that works is hitting the power button, after 30 seconds or so it will go down.

This is the problem of using the sane library, but I'd really like to use it, as it's way more decent/standarized and more software is compatible with it. Canon's official app is a super laconic scangearmp2 runtime which barely has any interface at all. No preview, not allowing to change any of the scanner settings, no nothing. You hit save, it will save whatever it is on the scanner in the folder you say, and that's about all it does. But it does work, though, and no crashes.
I'd like to try and see if I can get sane working with my scanner, as the experience would be so much better...what should I check?

Thanks a lot!

EDIT: A few more details: Running Kubuntu 16.04. After running scanlite from the console, I can see the following error:
> 
$ skanlite                                                                                                                   
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)                                                                         
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
KDE Daemon (kded) already running.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
kbuildsycoca4 running...
[bjnp] bjnp_recv_data: ERROR - could not read response payload (select timed out)!

This error shows on the console the exact moment the communication interrupts.

---

