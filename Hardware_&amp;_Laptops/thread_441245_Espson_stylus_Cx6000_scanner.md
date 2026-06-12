---
title: "Espson stylus Cx6000 scanner"
date: 2007-05-12
forum: Hardware &amp; Laptops
---

### Post by doctor bangali on 2007-05-12
I can get my EPSON STYLUS CX6000 all in one to work as a scanner ( it prints though). xsane does not detect it.
Any ideas?

---

### Post by dk0r on 2007-08-01
Same thing here. Once opened, xsane 'scans for devices' but produces the following error: 
"Failed to open device 'gt68xx:libusb:003:002': Invalid Argument."
googling the error seems to be of no use either. 
Anyone?

---

### Post by dk0r on 2007-08-01
> **doctor bangali]  
Tanker Bob, Any ideas on how to get the scanner working. xsane does not detect it.[/quote]

[QUOTE=Tanker Bob said:**
> No, and Feisty in its current kernel release will not recognize it.  The kernel team introduced a USB suspend feature for laptops in Feisty that breaks support for all scanners.  Older scanners have a workaround with something called Scanbuttond in the repositories, but it won't work with newer scanners.  You can read the whole sad story [here](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/85488).  According to that thread, the Linux kernel team just fixed the problem, but the ubuntu team hasn't updated our kernel with the fix yet.  I remains to be seen if they ever will.  All of which means that I have to fix my WinXP dual-boot setup today.
.

---

### Post by ventrec on 2007-08-06
This worked for me.  [http://ubuntuforums.org/showthread.php?t=358774](http://ubuntuforums.org/showthread.php?t=358774)

---

