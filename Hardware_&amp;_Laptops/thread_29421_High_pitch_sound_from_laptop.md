---
title: "High pitch sound from laptop"
date: 2005-04-24
forum: Hardware &amp; Laptops
---

### Post by Mackan on 2005-04-24
Hi, I just installed Ubuntu on my IBM Thinkpad X24 and everything seems to work nicely. But there is a big problem... I hear a high frequency noise coming from somewhere inside the laptop. It is not the harddrive, and I didn't have this in Win XP. The sound is not so high in magnitude, but it is audiable, and very annoying. 

It starts to appear pretty immediatly after loading the kernel, and its magnitude is sometimes higher, sometimes lower. It seems to be dependent on what's loading on the laptop. As an example, when I open a window on Ubuntu desktop, or the logout screen, the sound increases. It is very strange and annoying. 

Does anyone have a clue what it is? It doesn't matter if I run the laptop on battery or only AC. Thanks for any help to solve this problem.

---

### Post by Laurent Cazalet on 2005-04-24
I had something like this on my Dell C600. Only when running ACPI. 
You can try forcing APM (if your laptop supports it).

Maybe it's completely unrelated, because your hardware must be very different, but it can be worth a try. I solved it patching the kernel (now I'm using APM, so it's irrelevant). 

Look at this [thread](http://groups.google.be/groups?hl=nl&lr=&threadm=fa.dg37caq.1imot0c%40ifi.uio.no&rnum=1&prev=/groups%3Fq%3D%2Bc600%2Bnoise%2Bkernel%26hl%3Dnl%26lr%3D%26selm%3Dfa.dg37caq.1imot0c%2540ifi.uio.no%26rnum%3D) on google groups.

---

### Post by Gianni Exile on 2005-04-24
Hi,

I had exactly the same problem under Debian on my IBM laptop (i1410, i think).  Strangely enough, though I never did figure out what caused the problem, it went away when I ran KDE, so I left it at that.  Gnome and IceWM both made the sound louder, while KWin made it disappear.  No idea why, I have a decent understanding of Linux (I've written device drivers, etc), and I didn't figure out the problem -- nobody else reported the problem either.  This was about 4 years back.

---

### Post by Mackan on 2005-04-25
Hi again, and thanks for the repiles. On that google group, and here [http://www.thinkwiki.org/Problem_with_high_pitch_noises](http://www.thinkwiki.org/Problem_with_high_pitch_noises) , I have found some possible causes to the high pitch noise. Right now I don't have time to mess around in linux too much, but I will try to recompile kernel later with a patch to see if the noise goes away. *sigh*

---

