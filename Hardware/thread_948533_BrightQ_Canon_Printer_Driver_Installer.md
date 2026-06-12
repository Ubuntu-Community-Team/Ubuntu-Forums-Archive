---
title: "BrightQ Canon Printer Driver Installer"
date: 2008-10-15
forum: Hardware
---

### Post by vgrisham on 2008-10-15
At my school, I need to be able to print to a Canon Image Runner C6800, which is a networked multifunction printer and copier. I got it working in Ubuntu by using the PPD file provided at Linux printing's website. The capabilities are pretty limited (single sided, black and white printing only; the printer is capable of color, duplexing, stapling, hole punching, etc). I stumbled across canon's installer for Linux which is called brightq. I'm hoping it will allow me to access at least some of the features that I can use via Windows.

I've downloaded the brightq binary for linux and I'm attempting to run it. The file is called brightq-se-2.4.1-linux-2007-07-13.run. The instructions tell me to open a terminal and code:

> sh brightq-se-2.4.1-linux-2007-07-13.runI tried that (also tried adding sudo) and it fails with the message, "sh: Can't open brightq-se-2.4.1-operating_system-2007-07-13.run".

Simply double clicking the file seems to work better, but the terminal closes after it begins executing and I can't figure out why it's crashing. 

Anybody out there have any experience with this program? I'd appreciate your help.

---

### Post by markginter24 on 2008-10-15
make sure you use sh ./xxxxxxxx.run  otherwise it won't give you any meaningful feedback

---

