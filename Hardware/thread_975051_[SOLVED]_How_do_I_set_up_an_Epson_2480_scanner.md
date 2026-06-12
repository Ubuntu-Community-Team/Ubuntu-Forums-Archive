---
title: "[SOLVED] How do I set up an Epson 2480 scanner?"
date: 2008-11-08
forum: Hardware
---

### Post by bwallum on 2008-11-08
Hi

I have an Epsom scanner recognised as:-

Bus 001 Device 003: ID 04b8:0121 Seiko Epson Corp. Perfection 2480 Photo

I have checked and it is supported by xsane and I think the firmware is esfw41.bin. I have downloaded this file.

Can you help me with the next step please?

---

### Post by bwallum on 2008-11-08
Check that the scanner is plugged in with```
lsusb
```you should get something like this returned:-
Bus 001 Device 002: ID 04b8:0121 Seiko Epson Corp. Perfection 2480 Photo
If recognised then install the firmware:

1) ```
sudo apt-get install libsane-extras
```
2) Locate your firmware and download it to desktop e.g. my file for the Perfection 2480 Photo scanner is called esfw41.bin Note that you must have the precise firmware file for your scanner. Here's a good place to see if your scanner is supported [http://www.sane-project.org/sane-backends.html](http://www.sane-project.org/sane-backends.html) You can then determine the firmware file name and 'google' for it.

3) Open terminal and change directory to Desktop with```
cd Desktop
```
4) Copy file to sane.d e.g.```
sudo cp esfw41.bin /etc/sane.d
```
5) Edit snapscan.conf, first open the file  $ ```
gksudo gedit /etc/sane.d/snapscan.conf
``` then change the line starting with firmware to e.g. ```
firmware /etc/sane.d/esfw41.bin
``` Note that you must use your firmware file name if different to esfw41.bin

Fire up Applications>Graphics>Xsane Image Scanner

---

