---
title: "Inspiron E1705+nvidia: Can't switch video mode to CLI"
date: 2006-06-29
forum: Hardware &amp; Laptops
---

### Post by dmb on 2006-06-29
Hey, I just got a brand new E1705 from dell and everything is working correctly so far but one thing. For some reason, I can't switch from graphical xorg mode to normal  CLI mode. I have installed the nvidia drivers, but I think the problem was before as well.  When I press crtl-alt-F1, the screen would just be dark, without a backlight, and would just sit there until i press crtl-alt-F7 to get back into Xorg.  Anyone know why that happens? I need to switch between CLI and xorg often. Also, i think its related,  but when I suspend from ram and try to resume, the same thing happens except i can't get xorg to show again. Anyone know the problem? How about how to fix it?

---

### Post by tseliot on 2006-06-29
try point 13 of the problems section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

---

### Post by dmb on 2006-06-29
Boohoo, no more usplash. Is there any alternate than to getting rid of usplash?

---

### Post by tseliot on 2006-06-30
[QUOTE=dmb]Boohoo, no more usplash. Is there any alternate than to getting rid of usplash?[/QUOTE]
put "splash" back and add "vga=792"

---

### Post by m94mni on 2006-06-30
Wow, thanks, that actually worked on my Dell XPS M1710!

What other vga= lines would you think should work? Why exactly does 792 (=1024x768 @ 24bit) work??

---

### Post by dmb on 2006-07-01
Yay, you da man. Thanks, it worked.

---

