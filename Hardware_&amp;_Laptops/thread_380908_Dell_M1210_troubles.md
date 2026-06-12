---
title: "Dell M1210 troubles"
date: 2007-03-10
forum: Hardware &amp; Laptops
---

### Post by thypeacefrog on 2007-03-10
I installed ubuntu edgy on my new dell m1210 and everything that I would want to use is working flawlessly except the brightness keys.

When I hold Fn and the brightness key (up arrow) the screen goes black and it takes me to some sort of command line (not terminal) and then restarts. I can live without it but it would be nice to be able to change brightness.

Anyone been able to fix this or have any ideas? thanks in advance

---

### Post by dimeotane on 2007-03-10
I'm also on ubuntu edgy on the m1210  (I have the intel graphics card and bcm wifi card version though)
have you tried putting a mic into the line in/mic in jack yet to record your voice ?  I don't think anyone has gotten that to work yet.  If you get that to work then pm me please.

Brightness keys work for me during booting, but not after. 

I also have some trouble with getting the thing to stand by, and that's probably related to a problem with beryl.  Avoid beryl and you might not have that problem. 

Other than that.. this laptop rocks with Ubuntu :guitar:

---

### Post by medley on 2007-03-10
> **thypeacefrog said:**
> I installed ubuntu edgy on my new dell m1210 and everything that I would want to use is working flawlessly except the brightness keys.

When I hold Fn and the brightness key (up arrow) the screen goes black and it takes me to some sort of command line (not terminal) and then restarts. I can live without it but it would be nice to be able to change brightness.

Anyone been able to fix this or have any ideas? thanks in advance

The brightness up key seems to have the same effect as ctrl-alt-backspace is supposed to have (which incidently doesn't work on this laptop), which restarts the X server. When I first installed kubuntu on my M1210, the forward slash key did not work properly in the terminal (I forget what keystroke I got instead). Obviously this is a problem in the console, where you are always use that key. The solution was to change the keyboard layout to 'basic' from whatever I had specified in the install. 

But, that experience leads me to believe that at least on this laptop, the keystrokes are not all mapped the same as a standard 104 key keyboard. This would explain why the brightness keys and the X restart combination don't work; they are probably mapped differently than they are in Windows, for example.

A major concern I do have about Linux (or at least ubuntu) on this laptop is that I am wondering if thermal control is working properly. That is, it seems the cpu fan is not being regulated by the OS. The reason I think this is that if I reboot my system to Windows XP (I have dual boot) after running ubuntu for a while, the fan comes on almost immediately and blows a significant amount of hot air, then slows down as the temperature falls.

If my observation is correct, this is a fairly serious problem in my view. One thing Dell does extremely well is design systems with outstanding thermal regulation in their hardware design.

I'd be curious to know if other laptop users of different brands have noticed the same thing.

---

### Post by thypeacefrog on 2007-03-10
Well feeling my fan, I can feel cool air trickling out. The only time it really used to pump out with vista was when I was playing games. So once I get wow working on this I'll update as to what goes on.

---

