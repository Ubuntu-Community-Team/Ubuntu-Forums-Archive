---
title: "What is the keyboard device? (Feeling foolish)"
date: 2006-11-16
forum: Hardware &amp; Laptops
---

### Post by likwidoxigen on 2006-11-16
What is the actual device for the keyboard? /dev/<keyboard>/<device>


So I went into /dev/input/ and looked for kbd and it's not there. Then I grepped for it and it's not there, infact there's no kb anything in there. So waht is the keyboard called as as a device? Like a mouse is /dev/input/mouse0 (well for me anywhoo). I tried googling and it was one of those searches where I didn't quite know what to search for and kept getting nothing useful as results. All help is welcome and thanks in advance!

---

### Post by Peepsalot on 2006-11-16
> **likwidoxigen said:**
> What is the actual device for the keyboard? /dev/<keyboard>/<device>


So I went into /dev/input/ and looked for kbd and it's not there. Then I grepped for it and it's not there, infact there's no kb anything in there. So waht is the keyboard called as as a device? Like a mouse is /dev/input/mouse0 (well for me anywhoo). I tried googling and it was one of those searches where I didn't quite know what to search for and kept getting nothing useful as results. All help is welcome and thanks in advance!

The closest thing I would know is /dev/stdin
May I ask why you need to know though?  I've never come across a case where I needed to know that.  There may be a way to do what you want without knowing the device.

---

### Post by likwidoxigen on 2006-11-16
I'm trying to set up epsxe and I keeps trying to get input from the joystick device (which i don't have) so i was just going to switch it to the keyboard device and use that.

---

### Post by Peepsalot on 2006-11-16
ah I see.  So does /dev/stdin do the trick?

---

### Post by likwidoxigen on 2006-11-16
Just checked, yes it does, thank you so much! The help is greatly apprecciated!

---

