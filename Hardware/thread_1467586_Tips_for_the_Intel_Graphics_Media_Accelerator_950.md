---
title: "Tips for the Intel Graphics Media Accelerator 950?"
date: 2010-04-30
forum: Hardware
---

### Post by Espionage724 on 2010-04-30
I really like Ubuntu 10.04, I would even use it as my main OS, if it wasn't for my graphics chip...

This chip has given me issues on every copy of Linux I tried, mainly with it just being slow.

I heard that it is because it's using Mesa, which means its software rendered?

---

### Post by Espionage724 on 2010-05-01
bump

---

### Post by andrewabc on 2010-05-01
What exactly do you find slow about it?

I presume you have 10.04 installed?

What are your hardware specs?

I have atom 1.6ghz gma950 nettop and 10.04 performs as expected.

Make sure you turn off compiz
system->preferences-> appearance->visual effects tab->none

GMA950 card itself is slow, but I don't know of any serious problems with ubuntu.

---

### Post by Espionage724 on 2010-05-01
I can't do Runescape HD, and WoW in OpenGL mode under Wine doesn't work, Cedega doesn't detect that the 950GMA runs in Hardware, and I've only seen cards that wern't properly set up having the Mesa thing.

But the one thing that gets me is RuneScape HD. (Runescape is a Java based browser game. It uses OpenGL to render in HD mode) I can't even use Standard Detail (idk what the difference is)

---

### Post by Espionage724 on 2010-05-01
Wasn't trying to be mean or anything (I reread my msg and it sounded a bit mean lol)

---

### Post by andrewabc on 2010-05-01
So these programs were working properly under other OS using same hardware?
I presume windows (winxp)?

I do find games work better under my winxp than ubuntu OS.

When running one of these games, open terminal and type in 'top' and see what processes use up your CPU. My guess is that xorg will be the main culprit. I don't know of any way to get games etc to run faster under ubuntu. That's why I dual boot with winxp.

---

### Post by Espionage724 on 2010-05-01
Yep they work fine in any other OS (xp, vista, 7, os x). Runescape HD worked fine in ubuntu in the past I believe though....

---

### Post by andrewabc on 2010-05-01
If you're willing to break, possible screw up your ubuntu install you could always try latest kernel, and/or xserver

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

[ HOWTO: Jaunty Intel Graphics Performance Guide](http://ubuntuforums.org/showthread.php?t=1130582)
outdated but might have newer version somewheres or give you some tips.

---

### Post by Espionage724 on 2010-05-02
Is there an easy way to try a newer kernel? Like is there a PPA thing for kernels that works?

---

### Post by andrewabc on 2010-05-02
[https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa)

So trying newer kernel and newer intel drivers might help. Or could screw up your install. Make sure you have 10.04 on cd or liveusb in case you need to reinstall.

Also you state runescape runs in web browser. I'd also try running it in Opera or Chrome as they may run faster than firefox.

---

### Post by Espionage724 on 2010-05-02
Yea I tried firefox and chrome and it did the same thing, as soon as I clicked Standard Detail, it would black out and come back saying it can't use that render. When I clicked High Detail, it would just go to a gray box and that would be it.

---

