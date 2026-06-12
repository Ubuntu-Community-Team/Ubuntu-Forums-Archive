---
title: "help me plez"
date: 2008-03-28
forum: Hardware &amp; Laptops
---

### Post by linden940 on 2008-03-28
ok it seems someone had all ready found a fit.....but i dont know how to use the fix...i am very new to ubuntu so if someone please give me a hand and tell me what they are meaning.....

of if you may know of a better fit plez let me know....my promble is that when i try 2 to do the visual effects in the appearance preferences *its stuck on none* but i get this pop up "The Composite extension is not available" so please help me under stand there fix or if u got one for me 2 try....but plez put it in very ez so i could follow..i am a child to ubuntu :lolflag:


 Originally Posted by maxxym  View Post
I just went through the same problem...

Do this:

First, run sudo gedit /etc/X11/xorg.conf

Put 1 instead of 0 in the last section so it looks like this:

EndSection
Section "Extensions"
Option "Composite" "1"
EndSection


Then try again.. if it doesn't work... then do:

sudo apt-get install xserver-xgl

Restart X by doing cntr-alt-backspace


I am assuming that you are using Proprietary drivers for your card...


thank you

---

### Post by bartcramer on 2008-03-29
This desktop appearance thing is called 'compiz', which you can find in Synaptics. Can you see whether it is installed? It is installed by default, normally... If it isn't, install it via Synaptics, and try again. 

Hope that helps, 

Bart.

---

