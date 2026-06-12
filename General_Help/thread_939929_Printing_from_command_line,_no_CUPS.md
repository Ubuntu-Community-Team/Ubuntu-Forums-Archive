---
title: "Printing from command line, no CUPS"
date: 2008-10-06
forum: General Help
---

### Post by dejan.b on 2008-10-06
I have installed Ubuntu Server 8.04 (no GUI) for some admin work and I would like to be able to print a few text file directly to my LaserJet 1300 printer. I don't need printer server and network printing. Ubuntu recognizes the printer with lsusb, but when I send something to >/dev/usb/lp0 the printer just prints the first line or gives the blank page.

Is there a way to have LaserJet family of printers work from command line without GUI-CUPS?

I found a few howto's but they are about setting up a cups server from command line. 

What is missing in Ubuntu as the system recognizes the USB device and makes usblp0?

Thanks

Dejan

---

### Post by wyliecoyoteuk on 2008-10-06
You need to use the lp command, just redirecting stdio to the port will not word wrap (which is why you get one line).

example: to print the /etc/fstab configuration file, you would type lp /etc/fstab. The formatting of the printed page is rough (no margins, and non-proportional font used), but it’s OK for quick hard copy viewing.

---

### Post by dejan.b on 2008-10-06
Thanks for your reply, but when I give a command like that using lp I get 

```
lp: Error - no default destination available.
```

So, lp does not see usblp0 as destination?

Dejan

---

