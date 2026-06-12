---
title: "Resolution help?"
date: 2008-10-10
forum: General Help
---

### Post by Krupski on 2008-10-10
I'm not sure if this is a Linux question or a Windows question, so please bear with me.

I know that if I have a monitor connected to my Linux box and use "VGA=775" as a boot parameter, I get sharp, tiny characters and a huge screen... something like 150 by 60 characters.

But, if I SSH into the Linux box with a Windows SSH client (Bitvise Tunnelier), and I switch the screen from a window to full screen mode, the best I can get is 80 x 50 resolution.

Obviously, the video card and monitor are capable of hi-res operation (Linux can use it), but in Windows console mode all I get is the lousy 80 x 50 mode.

Anyone know how I can get the "super resolution" type mode that I can get in Linux?

Thanks!

-- Roger

---

### Post by schauerlich on 2008-10-10
cmd.exe is rather fussy about what size its window is. Try using PuTTY. It comes with a terminal emulator, so it should act just like if you were using ssh through gnome-terminal or something similar.

---

### Post by Krupski on 2008-10-10
> **EDavidBurg said:**
> cmd.exe is rather fussy about what size its window is. Try using PuTTY. It comes with a terminal emulator, so it should act just like if you were using ssh through gnome-terminal or something similar.

Thanks. Bitvise Tunnelier starts a console WINDOW with any font and any resolution I wish... that's no problem.

What I was hoping to do is get the hi-res Linux-style modes in FULL SCREEN (i.e. the mode you get with alt-enter).


Here's a typical window that I can get with Tunnelier (it's 110x40 and the characters are 10x18 pixels):



[center][IMG]http://home.roadrunner.com/~krupski/images/screen.jpg[/IMG][/center]



What I want is to be able to get this in full screen mode.


-- Roger

---

### Post by Ptero-4 on 2008-10-10
Also your wintendo could have a fussy videocard.

---

