---
title: "Firefox prints, Ev, OO, Abiword don't!"
date: 2006-05-05
forum: Hardware &amp; Laptops
---

### Post by lancest on 2006-05-05
Breezy, HP Laserjet 1020, to Windows XP box (Samba). [COLOR="SeaGreen"]NO PROBLEM [/COLOR]printing from Firefox/Ubuntu box at all! [COLOR="Red"]Why can't I print properly from Evolution, or any other program?[/COLOR]  Just get paper with fuzzy printed lines. Gnome print file to edit?

---

### Post by megabyte405 on 2006-05-26
It does sound like you have an issue in Gnome Print, since the only apps you list as working are ones that talk right to cups.  From your use of the term Samba when referring to the windows share, I'm guessing you know what you're doing, and possibly even configured the cups printer manually - port 631 or some config file I don't know where.  That's all well and good in most cases, but as often happens in Ubuntu, there's an "Ubuntu Way" - actually the Gnome Way.  Make sure you've added the printer to System, Administration, Printing - and possibly reverse any changes you've made in a config file manually.  Gnome will auto-configure CUPS for you, but not the other way around.

Good luck!

-- Ryan, AbiWord Dev and Win32 Maintainer

---

