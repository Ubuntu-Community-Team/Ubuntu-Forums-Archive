---
title: "Wonky Graphics (Intel 945gm express)"
date: 2009-01-18
forum: Hardware
---

### Post by Rinaru on 2009-01-18
Hello Ubuntu users! First of all I'd like to say that I really love Ubuntu, been using it for about three weeks now after giving up on Vista.

I'm pretty much a newbie with Ubuntu so please spare me! I came here for help because the community seems very nice.

Now I know there are a ton of topics around the Intel 945gm chip, I've searched through and through and I couldn't find an answer or a fix for my specific problem.

I'm running Intrepid Ibex. The problem isn't that I can't run Compiz or anything, I get full desktop effects. The problem is every time I try to run something graphic intensive, like games.

I tried running Tales of Pirates through Wine for example, using the latest dev release (and before that I tried with the latest stable). The game loaded, I could hear music. But the graphics would sort of corrupt after two seconds. Colors were thrown everywhere, a lot of black. Like the graphics were eaten or something, I don't know how to describe it.

This also happened with Tibia, a 2d game I tried to play. The top part of the game was nothing but green and white lines and the rest was black.

If you need a screenshot, let me know. I'll have to download something to test it on, since I've removed anything that displays like that. Even Regnum seems to load but it flickers and the graphics get corrupted.

If you need any terminal information, I'll gladly provide it. Just need to know how to do that since I'm new to all this.

---

### Post by densou on 2009-01-20
> **Rinaru said:**
> I'm pretty much a newbie with Ubuntu so please spare me!

ok, I'll handle it.

> Now I know there are a ton of topics around the Intel 945gm chip, I've searched through and through and I couldn't find an answer or a fix for my specific problem.

*faster way* check out my previous posts ;)

> I'm running Intrepid Ibex. The problem isn't that I can't run Compiz or anything, I get full desktop effects. The problem is every time I try to run something graphic intensive, like games.

I'd recommend to turn Compiz off; -try Metacity instead- it doesn't love non-Ati/nVidia cards :p

> If you need any terminal information, I'll gladly provide it. Just need to know how to do that since I'm new to all this.

probably you're using the 'vesa' driver (generic one, as 'Standard VGA' in Windows), I need your xorg.conf (paste it here)

Open a terminal window:
write *sudo gedit /etc/X11/xorg.conf* press enter
digit your password then press enter (note: invisible chars, don't worry)
copy & paste
DON'T EDIT IT !! Unless you read my past advices etc, although I don't recommend to do it yet.

---

