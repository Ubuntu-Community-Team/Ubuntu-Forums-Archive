---
title: "How to send windows-printer file to parallel port?"
date: 2012-04-30
forum: Hardware
---

### Post by zelena on 2012-04-30
I have an old LPT-printer (Epson LQ-100, year: 1996), and it is unlikely that Ubuntu can use it. Instead, I want to do this: use Windows (in virtual machine) and print to file, then in Ubuntu send that file to LPT-port. What command should I use for the last step?

My LPT-controller is Gembird LPC-1. It is a PCI-daughterboard. In documentation they write:
To install the parallel port use the following command:
/sbin/modprobe parport_pc io=0x3f8,a400 irq=4,18
The above command indicates onboard parallel port at 0x3f8 with IRQ 4 and MCS9835 parallel port at a400 with IRQ18. 

So, what command should I use to send a file to the port? Something like
cp myfile.prn /???/lpt???

Thank you.

---

