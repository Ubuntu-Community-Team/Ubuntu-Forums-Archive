---
title: "No USB Printer Option"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by Greydog on 2007-02-02
Hello All,

I'm running Ubuntu 6.06 386-I.

While trying to install my Canon S500 printer via USB, there is no USB connection listed. The LPT & Parallel options are there, though.

I think I borked this at some time because, it worked before.

Is there any way to restore the USB option?

Any help is welcome. Thanks,

Greydog

---

### Post by neverett on 2007-02-02
Try opening a terminal and typing:

lsusb

Post the output here and I'll see if I can help you.

---

### Post by Greydog on 2007-02-02
> **neverett said:**
> Try opening a terminal and typing:

lsusb

Post the output here and I'll see if I can help you.

Bus 005 Device 002: ID 0781:9191 SanDisk Corp.
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 04b8:010a Seiko Epson Corp. Perfection 1640SU
Bus 002 Device 001: ID 0000:0000

I hope I did that right!

Thanks for your help.

Greydog

---

### Post by neverett on 2007-02-02
A few more questions...

Is the printer plugged in while you are booting?  Sometimes Ubuntu is weird.  I would recommend booting and logging in, then plugging it in.  See if that helps.

Another thing is: are you using a usb hub?  I doubt that would be an issue.  It's a long shot, but try plugging it directly into the computer.  And how many usb ports do you have on your computer?

Yes you did the command correctly.  That just lists (ls) the usb devices (usb) that Ubuntu is recognizing.  Let me know!

---

### Post by Greydog on 2007-02-02
Hey Neverett,

Thanks again for your help.

I tried what you suggested but, no dice.

After I get the "searching printer database" message, I get the options for:

LPT #1

Parallel port #1 (Epson)

Parellel port #2 (Canon) but, no "usb".

I'm trying to avoid a new install. I'd like to think that this one can be repaired. 

Any other ideas?

Greydog

---

### Post by neverett on 2007-02-02
Are you using the printer control center to set this up?  I'll see what I can figure out, but I'm not sure.  What version of Ubuntu are you using?

Nic

---

### Post by Greydog on 2007-02-03
Yes. I'm using the printer setup under System>Admin>Printers.

As I said, there just isn't the USB option in the drop down box.

I'm running 6.06 386i, no hub and 6USB ports (2 used).

Thanks again for your help,

Greydog

---

### Post by neverett on 2007-02-03
Have you considered using Edgy Eft (6.10) instead of Dapper?  There is a way you can upgrade from 6.06 to 6.10 in the terminal, but I'll need to look up the commands again.  From what I have read, 6.06 is slightly more stable than 6.10.  However, in all my experience, both have been very stable releases.  Let me know and I'll get those commands for you!

---

