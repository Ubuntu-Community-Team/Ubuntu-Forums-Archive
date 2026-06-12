---
title: "USB Printing problems"
date: 2009-01-23
forum: Hardware
---

### Post by NFN Smith on 2009-01-23
I'm having difficulties getting a USB printer to work.  My situation:

The machine is a no-name desktop that runs an AMD64 version of Hardy.  This box was originally configured with Gutsy, and has been upgraded, rather than having been built with Hardy.

The printer is a Canon Pixma IP-3000.

For the moment, I don't believe drivers are the issue.  When this printer is attached to a Windows machine, I can print to it from the Ubuntu box using a Samba connection, without difficulty.  However, when I connect the printer directly to a USB port on the Ubuntu box, then I'm having problems.

As far as I can tell, the printer is configured correctly.  In fact, when I plug in the USB cable, the printer is automatically detected, and the necessary printer definition is created, and includes the correct driver.  However, when I send test jobs to the printer, they stall in the print queue.

One interesting I did find is that two of the jobs disappeared from the queue without printing, but when I unplugged the USB connection from the Ubuntu box, and reattached to the Windows box, the two jobs started printing on the printer.  Thus, I'm assuming that what happened is that the jobs got all the way to the printer's memory (and thus, deleted from the queue), but I don't see why they would have started printing when I reconnected the printer to the Windows box.

Any idea of how to get this one resolved?  As soon as I can get printing working reliably, it's my intent to move the functions of the Windows box to the Ubuntu box (including acting as a print server), and I'd really like to get the Windows box (a really old one) decommissioned.

Thanks in advance.

Smith

---

