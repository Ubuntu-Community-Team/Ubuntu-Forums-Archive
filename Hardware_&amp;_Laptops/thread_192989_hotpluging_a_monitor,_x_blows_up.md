---
title: "hotpluging a monitor, x blows up"
date: 2006-06-09
forum: Hardware &amp; Laptops
---

### Post by giants_fan on 2006-06-09
Hi,

Hopefully someone can help me here...

I have a IBM T42 with the proprietary ATI drivers installed and two monitors--not one big desktop, but two X windows.  One main monitor (the laptop) runs at 1024x768 and the other (external LCD) runs at 1280x1024.  I'm using the VGA port on the laptop itself.  Works great when I startup with the external monitor plugged in.

Anyway, I'd like to be able to run my laptop by itself (say, when I'm at home) and then when I get to work, plug in my external monitor and have it be recognized.  When I plug in the external monitor, nothing happens...which I guess is fine.  I restart X with a Ctrl+Alt+Backspace and that's when the displays goes crazy.  Nothing is on my laptop screen and the external monitor displays some goofy remnants of what was on my laptop screen.  I'm forced to do a hard reboot at that time.  Not great.

This also happens when I Ctrl+F1, sudo /etc/init.d/gdm stop, startx.

Any ideas or suggestions?

Thanks in advance.

---

### Post by carlo.nicora on 2006-06-19
Hello!
I am facing the exact same problem.
My laptop is a t42p with a screen resolution of 1600x1200 and an external monitor of 1280x1024.
If I start the computer with the external monitor plugged everything works fine, but if the laptop is already turned on and I want to plug the external monitor the only solution is a reboot...

Anyone has any news on this?

I have configured everything with the ati configuration!

Cheers

Carlo

---

