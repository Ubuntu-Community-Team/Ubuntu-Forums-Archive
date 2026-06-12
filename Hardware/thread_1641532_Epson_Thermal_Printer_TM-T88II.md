---
title: "Epson Thermal Printer TM-T88II"
date: 2010-12-09
forum: Hardware
---

### Post by that_paper_tiger on 2010-12-09
Hallo, wonder if anyone might help. I'm writing a POS application and have got the Epson Thermal Receipt printer TM-T88ii to work ok, using Ubuntu 10.04.1, CUPS and the Epson Linux driver. It has to print from Firefox. It prints what its told to. However, it is rather slow and too slow for purpose. I've changed fonts and it seems to write Monotype quicker than anything else (i.e. 15 secs versus 21secs for other fonts, of the same text). 

However, when I was making it work there were times it spewed garbage at an incredible rate. So I know it can print fast, just how do I make it print what I want it to? Are there fonts I need to use? A raw text command I can send? 

Help!

---

### Post by moboticdes on 2011-03-30
> **that_paper_tiger said:**
> Hallo, wonder if anyone might help. I'm writing a POS application and have got the Epson Thermal Receipt printer TM-T88ii to work ok, using Ubuntu 10.04.1, CUPS and the Epson Linux driver. It has to print from Firefox. It prints what its told to. However, it is rather slow and too slow for purpose. I've changed fonts and it seems to write Monotype quicker than anything else (i.e. 15 secs versus 21secs for other fonts, of the same text). 

However, when I was making it work there were times it spewed garbage at an incredible rate. So I know it can print fast, just how do I make it print what I want it to? Are there fonts I need to use? A raw text command I can send? 

Help!

Hi could you explain how you got it to work?
I'm trying to make a similar printer work under GNU/linux to no avail..
thank you

---

### Post by aquarat on 2011-06-23
It's very very simple...

The device will either have a USB port, Parallel port, serial port or Ethernet port.

I've experimented with the parport version so far.

You can print to it from bash by entering this : (note you may need to set permissions on /dev/lp0)

```

sudo echo "This is a test" >> /dev/lp0

```

Epson has a document that describes the more complex commands for this printer, like font changes, cutting the paper etc. They're all executed by sending hex codes to the printer. The document is entitled "FAQ for ESC/POS".

You could use an application like gtkterm to send data to the printer via serial.

All of these printers have a port that looks like an ethernet port, but isn't. It's for powering the drawer on the till, connecting it to your hub could cause damage to the hub... so don't :P .

I've just written a small java application to act as a telnet server on my network for the printer.

I hope this helps.

---

### Post by sebastianberns on 2012-04-28
Hello— I’m still trying to get the TM-T88II to work.

My setup is as follows:
Epson TM-T88II  <>  PL2303 USB-Serial adapter  <>  MacBook Pro  <>  VM Ware  <>  Ubuntu 10.11

The adapter is recognized correctly and hooked up to /dev/ttyUSB0.
I didn’t have any luck with printer drivers, though, and probably did not find the one OP is talking about.
Direct serial communication trough minicom or gtkterm also was unsuccessful.

I initially managed to make it run on Win XP and was able to echo from CMD, but this also stopped working somehow.

Can anybody help me out here? Maybe there’s even a simple way to send stuff from Mac OS directly.
Thanks

---

