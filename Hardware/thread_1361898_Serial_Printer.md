---
title: "Serial Printer"
date: 2009-12-22
forum: Hardware
---

### Post by Leberyo on 2009-12-22
I have a problem with our company's barcode printer (Citizen CLP-6001) that's serial port only that we have to have for our business software. I can't get it  to work for the life of me. I added the printer via Cups as a serial printer and as a generic text only printer. 
When I "dmesg | grep ttyS" the printer shows up;
[    1.676104] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.676308] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

and typing "sudo stty" I get 
speed 38400 baud; line = 0;
eol = M-^?; eol2 = M-^?; swtch = M-^?;
ixany iutf8

The printer is there but it won't respond to any commands, when I type "sudo echo "test" > /dev/ttyS0" I don't get any response. When I use gtkterm and send a break line, it doesn't respond. When I'm using my business software, (based on java) and print to /dev/ttyS0, I get a really quick printer icon in my notification area but the printer doesn't do anything. Does anybody have a clue how to fix this???

Thx

Solved, ubuntu doesn't provide generic text cups driver by default, had to add it.

---

### Post by serkanhamarat on 2010-04-05
> **Leberyo said:**
> Solved, ubuntu doesn't provide generic text cups driver by default, had to add it.

Add how? how did you do?

-------------------------

---

