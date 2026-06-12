---
title: "screen garbage returning from suspend"
date: 2005-05-05
forum: Hardware &amp; Laptops
---

### Post by kabanta on 2005-05-05
When I restore my laptop (an IBM x40) from suspend, the display shifts down about 2 centimeters -- with video garbage along the top of the screen.

Aside from the fact that this is annoying, it also create problems. The mouse, for example, is still reading position information of (now invisible) menu bars according to where they *should* be.  It is possible to refresh it back to normal by logging out and back in.  But, since I run my main menu bar along the *bottom* of the screen I have to "guess" where  the logout button is.

So:

- anyone have a proposal for preventing the video problem
- if not, how about some way to quickly refresh/restore the screen
- if not, anyone know what command-line equivalent Ubuntu uses for "logout" (ie, to the graphical login screen) :-)

thanks. k

---

### Post by luca_linux on 2005-05-05
What's your video card? If it's an ATI one and you're using their proprietary driver fglrx, it's normal.
There's just a way reported to work...

---

### Post by kabanta on 2005-05-05
> What's your video card? 
Ah! good question. How do I detect it? 

> There's just a way reported to work... 
yes?

---

### Post by luca_linux on 2005-05-05
Ok, I made a little research for you notebook's devices and it just uses the Intel graphic controller of the chipset. So I can't be helpful to you, since I was referring to ATI video cards.

---

