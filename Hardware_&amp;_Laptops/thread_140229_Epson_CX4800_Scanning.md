---
title: "Epson CX4800 Scanning"
date: 2006-03-05
forum: Hardware &amp; Laptops
---

### Post by Red Ghost on 2006-03-05
I recently bought an Epson CX4800. I plugged it in and it detected it and printed just fine. Now I need to scan. How do I go about doing this, everything I've read and tried doesn't work.
**Edit**: nevermind, I wasn't running xsane as root. FIXED

---

### Post by zubrug on 2006-03-06
[QUOTE=Red Ghost]I recently bought an Epson CX4800. I plugged it in and it detected it and printed just fine. Now I need to scan. How do I go about doing this, everything I've read and tried doesn't work.
**Edit**: nevermind, I wasn't running xsane as root. FIXED[/QUOTE]
Have the same printer, with the same problem. It does work with a trail version of Vuescan but I don't want to fork out $90!:cry:

---

### Post by Red Ghost on 2006-03-06
I have it working flawlessly now with sane. Install sane and xsane if they aren't already installed. Do a "sudo gedit /etc/sane.d/epson.conf" and make sure **everything** is commented out except "usb 0x04b8 0x0819". Then make sure you run xsane as root and it should work.

---

### Post by zubrug on 2006-03-06
[QUOTE=Red Ghost]I have it working flawlessly now with sane. Install sane and xsane if they aren't already installed. Do a "sudo gedit /etc/sane.d/epson.conf" and make sure **everything** is commented out except "usb 0x04b8 0x0819". Then make sure you run xsane as root and it should work.[/QUOTE]
Finally, thanks for that, it worked! \\:D/

---

### Post by z_diver on 2006-03-31
Adding usb 0x04b8 0x0819 to /etc/sane.d/epson.conf worked for me as well.  I'm not too fond of running xsane as root but i guess for the amount of scanning I do...it's unlikely to hurt.

For people on Breezy that are still using the gimp-print driver(for printing), I'd heartily recommend trying guttenprint 5.0.0 rc2 or better(available on sourceforge).  Not only is the quality better, and the color improved, but it's much faster too.

[COLOR="DarkRed"]Edit: These instructions worked on my Breezy install as well as Dapper flight 6.[/COLOR]

---

### Post by JulienPDX on 2006-07-26
OK

I am glad I found this thread because I followed those directions.

The XSANE UI is quite clunky and a little user-unfriendly.  For some reason, it seems to only want to scan in black and white.  What gives?

---

