---
title: "UK Dell 6400 Inspiron system speaker too LOUD!"
date: 2007-09-09
forum: Hardware &amp; Laptops
---

### Post by Linicks on 2007-09-09
I have noticed this on all Dell laptops at work too - the system speaker volume is so LOUD it almost gives you a heart attack when it beeps.

I called the Ubuntu Dell helpline to see if the guy knew how to turn the volume down, but I couldn't get him to understand it wasn't the sound system speaker[s] volume but the pc speaker - he just couldn't get that and kept trying to get me to adjust soundcard mixer levels...

So, does anybody know how to turn down the system speaker volume (I don't want it off, just quieter)?

Nick

---

### Post by phrawzty on 2007-09-17
I have the same problem on my Dell 6400 (France) as well.  For now, i've disabled the system beep - replacing it instead with the screen flash.  It's less heart-attack inducing, but now i'm worried about seizures. :P

In any case, *bump*, because i'd really like to have a solution on this one as well!

---

### Post by Linicks on 2007-09-17
I should have replied.  I finally got through to a Dell techy, and he confirmed that you cannot turn the volume down on this - he said it was designed to tell you an error occurred (but then I lost him explaining that *nix uses this as console 'bell', so it is way too loud).

Oh well.  I have done the same and turned it off in Gnome consoles.

Nick

---

### Post by axm on 2007-10-23
You modify the speaker with xset, but there is a lower limit to the least annoying sound produced. This seems to be system/speaker dependent and is quite high with the 6400. I like

> xset b 10 13500 20

best here. Still too loud, just a little better. Loudness and length depend on eachother to still play a sound. When you go below a certain point, no sound at all. You can play with your preferred pitch, here I find a pitch at the upper end of the scale less annoying, usually I would go to the lower end:

>xset b 40 100 5

.. works like a charm on the systems I was annoyed by too loud beeps before.

PS: Add it to bashrc and the gnome autostart, should be always active then. (Better way to have both in one?)

---

### Post by Linicks on 2007-10-23
Yes, I have messed around with xset b a bit.

The trouble is on the Inspiron 6400 all it seems to be able to adjust is the freq and duration... the damn thing is still too loud, especially as I work in a console a lot, and it soon gets on your nerves the constant beeping.

Thanks anyway.

Nick

---

