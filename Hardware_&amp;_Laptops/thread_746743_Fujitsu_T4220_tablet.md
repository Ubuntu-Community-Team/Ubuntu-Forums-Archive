---
title: "Fujitsu T4220 tablet"
date: 2008-04-05
forum: Hardware &amp; Laptops
---

### Post by Alterac on 2008-04-05
Hi, I'm new to Linux and I need help to get my digitizer working for my tablet.
> 
Now we need to enter the /dev/ttyS0 (COM0) settings in /etc/serial.conf. Add this to the file:

/dev/ttyS0 port 0x220 irq 4 autoconfig

I found this from here: [https://help.ubuntu.com/community/T4220](https://help.ubuntu.com/community/T4220)

But I don't understand what it means by entering the /dev/ttys0 (COM0) settings in /etc/serial.conf. How do I go about this? Could anyone guide me step by step?

*Sorry for being so noob, but there is something I don't understand. I cannot do any copying or pasting outside /home. Why is this? And how do I go about enabling this?

---

### Post by Alterac on 2008-04-05
Okay, I've managed to get my digitizer working.

How do I calibrate it now?

Also, the noob question from before... I realised that I can do copying, pasting and modification of files via the Terminal with the "sudo" command but is there anyway i can do without the terminal? It tends to get tedious.

---

