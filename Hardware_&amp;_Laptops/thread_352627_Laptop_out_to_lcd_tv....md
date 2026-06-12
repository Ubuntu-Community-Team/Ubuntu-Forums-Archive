---
title: "Laptop out to lcd tv..."
date: 2007-02-03
forum: Hardware &amp; Laptops
---

### Post by styven on 2007-02-03
Hi all,

I have a new tv and thought i would see what ubuntu looks on a big monitor.

TV says "no pc input" when i connect up my laptop.

The laptop is a HPnx6318 with intel graphics chipset.
The TV is a Hitachi 32" lcd.

What do i need to do to see it on the lcd tv?


Steve

---

### Post by RandomJoe on 2007-02-03
Are you starting X (by rebooting, or hitting Ctrl-Alt-Bkspc at the login prompt) with the TV connected?  I haven't tried in a very long time, but I seem to recall not having much success under Linux with the special function keys on my Dells that would switch between the panel and external display.

What resolutions does the TV support?  It's possible if it only has some oddly-sized ones you will have to use the 915resolution program to add a supported mode.  It may be falling back to the internal display if it can't find a "valid" resolution for the TV.  You can search through /var/log/Xorg.0.log to see if it even sees the TV.  (I'm assuming you are connecting with a VGA or DVI cable.)

---

### Post by styven on 2007-02-04
Hi there and thank you,

As far as i can see the resolution is not an issue, the laptop defaults to 1024 x 768 in both ubuntu and XP. It goes without saying that all works fine in XP.

I am connecting via a vga cable.

Steve

---

### Post by styven on 2007-02-04
Don't know if this is worth knowing, I am only wanting to replicate what is on the laptop monitor at this stage.

Steve.

---

### Post by styven on 2007-02-04
Sussed it, fn+f4, on this laptop and it's there:) 

Cheers steve.

---

