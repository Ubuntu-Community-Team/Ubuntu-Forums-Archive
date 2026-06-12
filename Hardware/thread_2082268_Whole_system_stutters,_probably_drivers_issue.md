---
title: "Whole system stutters, probably drivers issue"
date: 2012-11-08
forum: Hardware
---

### Post by prabab on 2012-11-08
Hi. I've just recently encountered this problem. Basically, whole system is stuttering.

Issues started to appear after going from Ubuntu 12.04 to 12.10. I work as a Java programmer, and I've noticed that as soon as I've updated the system, the Nouveau drivers returned errors every time when I was putting anything in GPU memory: [COLOR="Red"]"nouveau kernel rejected"[/COLOR].

So I've switched to proprietary drivers and everything was working flawless... Until few hours ago, then whole system started stuttering without any apparent reason. Everything freezes once in a few seconds in what appears to be fixed intervals.

Changing drivers back to Nouveau gets rid of this issue, but I still am not able to work, as my application doesn't run with them since the update.

The computer I speak of doesn't have the best GPU out there (onboard GeForce 6150SE) but it's enough for my work.

I've tried to run jockey-gtk too see if my drivers are running correctly, but I can't, system does not recognize this command and when I run sudo apt-get install jockey-gtk it clearly states, that it's already installed. So I guess the problem is much bigger than I thought.

I'm sitting ducks and I have no idea what to do. I am not in a position to reinstall the system. Already done a research on Google and forums, but I couldn't find anything I would be able to relate to. :frown:.

---

### Post by 2F4U on 2012-11-09
The application jockey has been removed and here is how to do it in 12.10:

[http://itsfoss.com/how-to-install-additional-drivers-in-ubuntu-12-10-quick-tip/](http://itsfoss.com/how-to-install-additional-drivers-in-ubuntu-12-10-quick-tip/)

---

### Post by prabab on 2012-11-09
> **2F4U said:**
> The application jockey has been removed and here is how to do it in 12.10:

[http://itsfoss.com/how-to-install-additional-drivers-in-ubuntu-12-10-quick-tip/](http://itsfoss.com/how-to-install-additional-drivers-in-ubuntu-12-10-quick-tip/)
I've already been using this method then, to switch between the drivers.

Still:
- When using open drivers, they starts flashing error[COLOR="Red"] "nouveau kernel rejected"[/COLOR] every time I try to put something in GPU memory, also the system freeze completely after few minutes.
- When using proprietary drivers, the system stutters in fixed intervals (1-2 seconds of freeze every ~5 seconds).

I have a feeling that the problem might be related to Compiz, as when I kill it the problem stops (but I can't really work without a window manager). Reinstalling Compiz didn't helped at all, though.

Edit: **When using XFCE problem does not occur.**

---

