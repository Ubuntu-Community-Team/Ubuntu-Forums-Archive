---
title: "Scanned stopped working (works fine under XP/Knoppix)"
date: 2006-02-27
forum: Hardware &amp; Laptops
---

### Post by artik on 2006-02-27
Hello,
I have a problem with HP PSC 1315 Printer/Scanner all in one.
It used to work fine all the time untill it just scanner **had stopped working** without any reason:

xsane starts and then closes immediatly not giving any message.
scanimage/scanimage -L gives nothing to output
(Even not a message that scanner not found)
sane-find-scanner gives
```
found USB scanner (vendor=0x03f0, product=0x3f11) at libusb:001:002
```
I've tryed to restart hplip, scan file system for errors, reinstalled hplip* libsane, xsane*. Nothing had changes the situation.

The scanner works under WinXP, and it also works under Knoppix 4.0.2.
dmesg output related to scanner is
```
[4295386.790000] usb 1-1: USB disconnect, address 4
[4295386.792000] drivers/usb/class/usblp.c: usblp0: removed
[4295390.971000] usb 1-1: new full speed USB device using ohci_hcd and address 5
[4295391.098000] drivers/usb/class/usblp.c: usblp0:
USB Bidirectional printer dev 5 if 1 alt 0 proto 2 vid 0x03F0 pid 0x3F11
```

Can someone give me a direction what had messed up? I didn't any upgrates... it just stopped working. I have no ideas what can I do.

Thanks!!!
Artik

P.S.: System Ubuntu Breezy, kernel 2.6.12-9-k7, Working with KDE

---

### Post by artik on 2006-02-27
Some additional information:

the output of grep -i xsane /var/log/messages | tail
is
```
Feb 27 19:28:03 artyomtnk xsane: unable to open /var/run/hplip/hpssd.port: No such file or directory: prnt/hpijs/hplip_api.c 84
Feb 27 19:28:03 artyomtnk xsane: unable to connect hpssd socket 50002: Connection refused: prnt/hpijs/hplip_api.c 710
```


The scanimage on another computer in network (Debian Sarge, that is connected to Ubuntu ) gives segfault

Any ideas

---

### Post by artik on 2006-02-28
up

---

### Post by artik on 2006-03-02
Just in case someone is interested in the solution - I've found it there:
[http://sourceforge.net/forum/message.php?msg_id=3342335](http://sourceforge.net/forum/message.php?msg_id=3342335)

I've removed accidently definition of localhost as 127.0.0.1
After I added it in Networking dialog all works fine...

---

