---
title: "Any &quot;tricks&quot; for &quot;higer resolution&quot;?"
date: 2010-09-18
forum: Hardware
---

### Post by Cyclops_ on 2010-09-18
Hey, all,

Just purchased a 17.3" laptop.  With a screen this size, one would think it would come with 1920x1080 resolution options.  Unfortunately, no.  1600x900.  :(  ...

Is there anything that I can do to trick my eyes into thinking that I have a greater resolution.  I know that I can do things like make icons on the desktop and in Dolphin/Nautilus smaller.  Are there other things I can do (either at a much higher level or even as fine-grained as those things I'm already doing?)

Many many thanks for anyone who can answer this!  :)

---

### Post by Yellow Pasque on 2010-09-18
So is the screen supposed to run at 1920x1080 natively? If so, please post /var/log/Xorg.0.log (use [ code ] [ /code ] tags). WHat laptop do you have?

---

### Post by Cyclops_ on 2010-09-18
No.  It's "supposed" to run at 1600x900.  This is just painful for me! :(  ...

It's an ASUS G73J.

Thanks!

---

### Post by Zorael on 2010-09-19
Well, you can set;
[list][*]smaller icons (Fonts, obviously. DPI can also be set on a lower level when starting X)
[*]smaller fonts (Icons, Advanced tab)
[*]smaller Oxygen window borders (in 4.5: Workspace Appearance -> Window Decorations -> Configure Decoration, General tab, Border size)
[*]thinner scrollbars (in 4.5: Style -> Widget style Oxygen: Configure, Scrollbars tab)
[*]thinner panels (assuming plasma desktop)
[*]zoom out in web browsers
[/list]

I don't know if there's much else. KWin can't size down windows either (by a percentage), else that *might* have been a way to go, but they would end up fuzzy, ugly and hard to read from.

---

### Post by Cyclops_ on 2010-09-19
Huh.  I didn't think about scrollbars, panels and window borders.  Thank you, Zorael.... Those things should help!  :)

If you think of anything else, let me know, but this should be helpful (also helpful is that many programs allow you to "zoom" in and out:  pdf readers, dolphin, etc), but I did want things like you have mentioned, so thanks! :)

---

### Post by Cyclops_ on 2010-09-19
Oh, hey, I *am* using Plasma.  How do I get smaller panels?

Thanks!

---

### Post by Zorael on 2010-09-20
Unlock widgets, click the cashew on your panel to make its settings toolbar slide up, then click and drag the Height text to resize that panel.

(That's also where you move panels if you want them on a different edge of the screen; by clicking and dragging Screen Edge.)

---

