---
title: "Xorg on a HP DV1000 series"
date: 2005-05-24
forum: Hardware &amp; Laptops
---

### Post by gabriello on 2005-05-24
Hi everyone,

I have a question for you ubuntu experts...
Since two weeks I'm using Ubuntu Hoary on a HP dv1131ea (DV1000 series), and something curious happens everytime xorg starts: the screen begins to flicker for about one second and shows some colors/lines, then becomes black and after a while (some seconds) I see the Ubuntu login screen... 
Is it OK, does it happen also to you or should I worry for my laptop screen?? 
BTW, the graphic card is an Intel Extreme Graphics 2 and the chipset is a Intel i810 (as far as I understood...)

Thank you all!

---

### Post by michux on 2005-05-29
I'm also using Ubuntu Hoary on my dv1074ea laptop. All works great as well.
The flickering thing s probably due to poor ati supoprt in Linux. I don't think you should wory about it. It behaves randomly on my laptop as well (some blinking during Xorg startup) but then works great.

I have one question for ya. Can you do 3d accelleration and DVD watching at the same time? When I have 3d modules on, DVD produces blue screen withing xine or mplayer. When I turn 3d off, DVD works fine.

---

### Post by Silwenae on 2005-05-29
[QUOTE=gabriello]Hi everyone,

I have a question for you ubuntu experts...
Since two weeks I'm using Ubuntu Hoary on a HP dv1131ea (DV1000 series), and something curious happens everytime xorg starts: the screen begins to flicker for about one second and shows some colors/lines, then becomes black and after a while (some seconds) I see the Ubuntu login screen... 
Is it OK, does it happen also to you or should I worry for my laptop screen?? 
BTW, the graphic card is an Intel Extreme Graphics 2 and the chipset is a Intel i810 (as far as I understood...)

Thank you all![/QUOTE]
 I have a dv1000 series notebook as well, and right before the the login screen comes up, I get the same flickering.  I wouldn't worry about it, it's just trying to set up the correct resolution and refresh rates.

---

### Post by gabriello on 2005-05-30
First of all thank you all for your attention.
Maybe I understood why the flickering happens: if I change the framebuffer resolution with vga=791 in the grub boot parameters I don't get the same flickering anymore, but only something "smaller", so the problem is only related with resolution changing when Xorg starts, and maybe it is not worth worrying about that.

[QUOTE=michux]The flickering thing s probably due to poor ati supoprt in Linux. I don't think you should wory about it.[/QUOTE]
ATI support? My graphic chipset is an Intel Extreme Graphics 2, maybe yours is different.

[QUOTE=michux]
I have one question for ya. Can you do 3d accelleration and DVD watching at the same time? When I have 3d modules on, DVD produces blue screen withing xine or mplayer. When I turn 3d off, DVD works fine.[/QUOTE]
I never tried, but I'll let you know if have similar issues.

[QUOTE=Silwenae]
I get the same flickering. I wouldn't worry about it, it's just trying to set up the correct resolution and refresh rates.[/QUOTE]
Yes, the problem for me is what resolution and what refresh rate  ;-).
And, by the way, is there a way to change color depth? It seems to me that the same things look different in Ubuntu than in WindowsXP....(maybe I'm only wrong!)

Ciao,
G.

---

