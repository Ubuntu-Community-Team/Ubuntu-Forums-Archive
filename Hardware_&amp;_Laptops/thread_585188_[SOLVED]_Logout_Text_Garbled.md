---
title: "[SOLVED] Logout Text Garbled"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by steveneddy on 2007-10-21
I have noticed that when I logout from Gnome, the text is garbled and unreadable. It looks like a lot or horizontal lines. X works perfectly whenever I'm logged in.

I recently tried to install the artwiz fonts for my Fluxbox DE and I think that may have messed something up.

I just deleted the artwiz fonts pack and I'm backtracking what I may have done to cause this problem.

The only other thing I have done is install Firefox 3.0a in a desktop folder for testing purposes, but I don't remember if I had the problem before or after that. 

This has happened in the last 24 hours and these are the only two things I have installed that I can think of (Firefox 3.0a and Artwiz fonts).

Anybody have an idea where I can go to repair this?

EDIT:

I also noticed that i can't go to a tty terminal session (ctrl+alt+F1) because the text there is garbled also.

---

### Post by steveneddy on 2007-10-21
I figured it out.

I noticed that some of the font references for the artwiz fonts were unscaled, and when I was poking around in the /xorg.cong file, I noticed those font references in the file near the top. 

After the font listing, it had "unscaled" listed. I just commented these out and the problem went away.

Thanks to everyone who read this and thought about the answer.

:popcorn:

---

### Post by steveneddy on 2007-10-21
```
Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
#	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
#	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection
```

---

