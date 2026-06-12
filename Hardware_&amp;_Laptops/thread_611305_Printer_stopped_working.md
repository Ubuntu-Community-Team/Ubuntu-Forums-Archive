---
title: "Printer stopped working"
date: 2007-11-12
forum: Hardware &amp; Laptops
---

### Post by IllegalCharacter on 2007-11-12
Hey everyone,

I was printing something the other night and the printer ran out of paper. I put some more paper in, but nothing happened (it automatically resumes when you put paper in). Now, I can't print anything. I've tried reinstalling the printer, and reinstalling CUPS.

The printer is an HP LaserJet 1000 and its using the foozjs or whatever it's called driver.

Thanks!

---

### Post by IllegalCharacter on 2007-11-20
Anybody?

---

### Post by stchman on 2007-11-27
So you are saying that the LaserJet 1000 was working fine on Gutsy and now nothing.  Running out of paper should not do anything.

Try cycling power to the printer and then rebooting the PC.  This should upload the firmware to the LJ1000.  If that does not work try my procedure for installing an updated foo2zjs driver.

[http://www.stchman.com/foo2zjs.html](http://www.stchman.com/foo2zjs.html)

---

### Post by IllegalCharacter on 2007-11-27
Thanks for your reply.
I thought this was kinda weird too.

I've restarted the computer and turned off the printer and everything (actually that was the first thing I did after it stopped working).

Unfortunately the script does not work. It installed the printer just fine, and when I restarted the printer flashed its lights and made some noise, but it still does not print.

I know that the printer works because ever since it stopped working in Ubuntu I've been restarting under Windows and printing, which works fine.

---

### Post by stchman on 2007-11-28
> **IllegalCharacter said:**
> Thanks for your reply.
I thought this was kinda weird too.

I've restarted the computer and turned off the printer and everything (actually that was the first thing I did after it stopped working).

Unfortunately the script does not work. It installed the printer just fine, and when I restarted the printer flashed its lights and made some noise, but it still does not print.

I know that the printer works because ever since it stopped working in Ubuntu I've been restarting under Windows and printing, which works fine.

My script does work.  I know, I used it to install my 1000 on Feisty.  The way you need to do it is to cycle power on the printer.  When the printer is on, turn the PC on.  This will upload the firmware to the printer.  Leave the printer plugged in.

---

### Post by IllegalCharacter on 2007-11-28
Hooray! It works. Looks like I don't need Windows anymore! Thank you.

---

