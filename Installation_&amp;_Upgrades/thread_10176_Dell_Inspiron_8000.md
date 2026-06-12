---
title: "Dell Inspiron 8000"
date: 2005-01-05
forum: Installation &amp; Upgrades
---

### Post by jahn on 2005-01-05
Installation went fine on my home laptop, an Inspiron 8000, but the display is very messed up now.  The screen image is cut in half vertically, and blurred out in the middle.  Does anyone have any clues as to how to remedy this?  Thanks!

I'll post my hardware specs when I get home (browsing Ubuntu Forums at work, shhh).

---

### Post by F Cocquyt on 2005-01-06
I've got a Dell inpiron8000 too, but I can't get ubuntu installed. It always freezes at the language selection. (can't even select a language) :-( 

PC:
Dell inspiron 8000
Intell PIII 512 Mb ram
currently dual boot WinXP and Fedora Core 3 (but I am still just a linux newbie, trying to decide which distro I like the most)

---

### Post by jahn on 2005-01-10
[QUOTE=jahn]Installation went fine on my home laptop, an Inspiron 8000, but the display is very messed up now.  The screen image is cut in half vertically, and blurred out in the middle.  Does anyone have any clues as to how to remedy this?  Thanks!

I'll post my hardware specs when I get home (browsing Ubuntu Forums at work, shhh).[/QUOTE]
 Finally figured this one out!

I have an ATI Mobility graphics card... so...
- I had to reboot into recovery mode
- "ran dpkg-reconfigure -plow xserver-xfree86" and changed my video settings to 16-bit, with Vertical Refresh rate between 58-62, and all seems fine.

Hope that helps someone!

---

### Post by Danilo on 2005-01-11
Jahn, if you don't want to resort to lower quality video modes, you might want to try increasing HorizSync values in your /etc/X11/XF86Config-4 file: I've so far never had much luck in those being detected automatically (that should be VESA DDC giving a hand, right?). It's best if you've got a manual for the computer, but on my Inspiron 1100 I use something like "HorizSync 28-60" to get full resolution in full depth :)

---

### Post by macbeth on 2005-01-21
I had the same problem as the original poster, and I fixed it by going to 

/etc/X11/XF86Config-4

and setting my color depth to 16, as well as modifying the three resolutions in the options associated with the color depth to "1400x1500".

Anyway, my gnome now launches with 640x480 resolution, and there's only one option in the Screen Resolution Preferences menu: "640x480". How do I change the resolution to my laptop's native resolution of 1400x1050?

Edit: Disregard Most of my information is lame. Don't listen to me, go here: [http://www.ubuntuforums.org/showthread.php?t=5651&highlight=HorizSync](http://www.ubuntuforums.org/showthread.php?t=5651&highlight=HorizSync)

---

