---
title: "Firmware error on installation, but couldn't see message in time"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by CaseLogic on 2009-02-10
Right before the graphical install GUI came up, there was some text output to the screen talking about some firmware error and a site to visit.  However this message lasted for like 3 seconds and I didn't get a chance to write any of it down or remember it.  After 3 seconds the GUI came up and hid the message.

Is there a log file somewhere where I can find out what the error was?

---

### Post by CaseLogic on 2009-02-10
I want to say it told me to download some newer firmware at linuxwireless.org or something, but I wish I could find the exact error messages.

---

### Post by CaseLogic on 2009-02-10
no one has any idea how to see what those errors were? is it not logged anywhere? anyway to recreate them?

---

### Post by Threnners on 2009-02-10
[http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware)

---

### Post by CaseLogic on 2009-02-10
> **Threnners said:**
> [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware)
thanks!

I'm not entirely sure if that was the only error I got though.  I'm pretty sure that was one of them however.

Any ideas on how I can pull them up?

---

### Post by jimv on 2009-02-10
You *should* be able to see them by opening the terminal and typing 'dmesg'.

If that doesn't work, try pressing control+alt+f1.  That will drop you to a terminal where you might see those messages.  Press control+alt+f7 to get back to you regular screen.

---

### Post by CaseLogic on 2009-02-10
> **jimv said:**
> You *should* be able to see them by opening the terminal and typing 'dmesg'.

If that doesn't work, try pressing control+alt+f1.  That will drop you to a terminal where you might see those messages.  Press control+alt+f7 to get back to you regular screen.
and that'll work even though my laptop has been restarted since the installation?

---

### Post by jimv on 2009-02-10
Oh, no.  I thought you were getting it everytime you booted up.

---

