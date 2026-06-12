---
title: "[fglrx] System lockup when using OpenGL"
date: 2005-04-10
forum: Hardware &amp; Laptops
---

### Post by pagefault on 2005-04-10
Hi there, I am having a problem with the fglrx drivers on hoary. I have direct rendering reported as enabled with glxinfo but whenever I try to run an OpenGL application it works for about 2 seconds then locks up my entire system. Has anyone else has this issue or any idea how to fix it?

My system specs:

AMD Athlon XP 2400+
ASUS A7N8X Deluxe (nForce 2)
1 gb memory

---

### Post by zoso on 2005-04-10
It would most likely be good to know the exact sort of video card you're using. 

Other than that all I can do is chip in and say that I'm having a very similiar problem, and hope that somebody out there has an idea or can make a suggestion.

On my system fglrxinfo reports:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9000/9100 IGP Series DDR Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)

Trying to run fgl_glxgears (or glxgears) results in a black window and an unresponsive system. Only a hard reboot brings it back.

---

### Post by pagefault on 2005-04-10
Edit

Ok I found the problem, bad power supply. Who would have thought... Hmm.

---

