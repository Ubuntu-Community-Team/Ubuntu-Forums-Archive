---
title: "scanner under parallel-usb cable, Ubuntu 9.04"
date: 2010-10-21
forum: Hardware
---

### Post by sfp100 on 2010-10-21
Hi,
I've got Plustek OpticPro 9636T scanner with has parallel port and an laptop with Ubuntu 9.04 and no parallel port - only USB. I've tried two cables to connect one to each other and it's hasn't work. One cable is usb-serial and serial-parallel converter (two parts I can disconnect) with is visible in sane-find-scanner and reported as
```
found USB scanner (vendor=0x067b [Prolific Technology Inc.], product=0x2303 [USB-Serial Controller]) at libusb:004:017
``` (note that it is cable name, not scanner)
Second cable is direct usb-parallel, but in properties has part:
 ```
Interface Descriptor:
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      2 Bidirectional

```and  sane-find-scanner don't see it.
In both cases scaneimage -L and xsane reports no scanner found. 
The line plustek_pp in dll.conf is uncommented, I've tried some device names in plustek_pp.conf such as:
 ```
parallel:libusb:005:014
```, or
```
parallel:/dev/serial/by-id/usb-Prolific_Technology_Inc._USB-Serial_Controller-if00-port0
``````
  0x2305
``````
  /dev/usb/lp0
```but it doesn't help.
What else I can try? How to set up this scanner?

---

### Post by P4man on 2010-10-21
You didnt actually expect that to work, did you?

laptop -> usb -> serial to usb -> parallel to serial -> scanner ?

Something like this :D

[IMG]http://www.dansdata.com/images/blog/adapter_chain.jpg[/IMG]

Seriously, I very much doubt it CAN work in theory, Id never expect it to work in reality. I would not even bet on a USB to parallel converter to work with a parallel scanner, but at least that could be worth trying.

---

### Post by sfp100 on 2010-10-21
No, I have 2 cables and I've tried connect scanner to laptop with cable 1 (left on foto) or cable 2. 
[IMG]http://lh5.ggpht.com/_Vvdnej4TGV4/TMCv1L31PfE/AAAAAAAAABI/Hfl46y-2Dx4/s144-c/Cables.jpg[/IMG]
Scanner have two ports: to host computer (with "gender changer") and to printer. May by I should use some thing to finish the line (in place of printer) but I haven't one. 
I want any of this cables to work, not both ;)
For me it looks quite simpler than on Your photo ;)
I've read some articles on google, try all ideas from this (most about connecting printers via parallel-USB or some other scanners connected to parallel - there are problems too, since sane-find-scanner -p is developed only for one manufacturer (according to man)).  Then I've went to state "no more idea" and ask...

---

### Post by P4man on 2010-10-21
Okay sorry, I misunderstood.

I did some googling for you and found this:
[http://manpages.ubuntu.com/manpages/maverick/man5/sane-plustek_pp.5.html](http://manpages.ubuntu.com/manpages/maverick/man5/sane-plustek_pp.5.html)

It appears even if you have a "real" parallel port, it may require some tinkering. I would suggest if possible, you try to get it working on ubuntu on a different PC that has a parallel port. Once you are confident that works, go ahead and experiment with the USB to parallel adapters again. But right now its hard to say if the problem is the sane drivers or the adapter.

---

### Post by sfp100 on 2010-10-22
OK. You're right - I should divide problem to two parts, althouhg it's not so easy to find computer with parallel port ;)
EDIT:
Another one journey on web about "USB to parallel converter" and at [http://ubuntuforums.org/archive/index.php/t-981770.html](http://ubuntuforums.org/archive/index.php/t-981770.html) I found that:
> I don't know about the serial-to-parallel converter, but the USB-parallel port interface is likely not to work, mainly because these special cables do not emulate a full parallel port, just enough that printers which do not need some "back-channel" (unlike the HP scanner/printer combination) work.
So, it may be simpler to buy one old computer with old ports and set up a "scan-server" or buy new scanner, whatever will be cheaper :(
Of course buy new scanner is very not ecological solution, but maybe the most economical one.
Any way I will try my old scanner under old computer and both Windows XP and Ubuntu 9.04. Thanks for this suggestion.

---

