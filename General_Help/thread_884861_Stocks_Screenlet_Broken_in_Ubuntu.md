---
title: "Stocks Screenlet Broken in Ubuntu"
date: 2008-08-09
forum: General Help
---

### Post by I[AM]SMRT on 2008-08-09
My Stocks screenlet was working perfectly until yesterday, now it doesn't show up while all my other screenlets are working properly as widgets.

In the screenlets manager, it says that it's running and active yet there's nothing =/. I've tried restarting all my screenlets that I have running/restarting the computer but that doesn't help. Any ideas?

Also, I have a few screenlets that auto-start on startup but I have to restart some screenlets (MyIP, ClearWeather, WordoftheDay and Stocks before now) because I assume they need an internet connection to start properly and they start before my wireless connection kicks in. Is there a workaround for this?

-SMRT

---

### Post by SkonesMickLoud on 2008-08-09
> **'I[AM]SMRT said:**
> Also, I have a few screenlets that auto-start on startup but I have to restart some screenlets (MyIP, ClearWeather, WordoftheDay and Stocks before now) because I assume they need an internet connection to start properly and they start before my wireless connection kicks in. Is there a workaround for this?

In your "Startup Programs" in the Sessions menu, add:

```
sleep 10 && *start command*
```

Obviously you'll need to supply the command.  You may also be able to do this more efficiently by passing the "sleep" command to the main screenlets program.  I don't use any, so I don't know what's even available.

The "10" I used is seconds.  You can lengthen or shorten this variable to suit your needs.

---

### Post by I[AM]SMRT on 2008-08-09
> **SkonesMickLoud said:**
> In your "Startup Programs" in the Sessions menu, add:

```
sleep 10 && *start command*
```

Obviously you'll need to supply the command.  You may also be able to do this more efficiently by passing the "sleep" command to the main screenlets program.  I don't use any, so I don't know what's even available.

The "10" I used is seconds.  You can lengthen or shorten this variable to suit your needs.
Since each of my screenlets has its own entry in the session menu, do you know if I have to do it for each screenlet or just the screenlets daemon?

---

### Post by SkonesMickLoud on 2008-08-09
> **'I[AM]SMRT said:**
> Since each of my screenlets has its own entry in the session menu, do you know if I have to do it for each screenlet or just the screenlets daemon?

You could try the daemon, but you'll probably need to do it for every one.  Restarting X will let you check without doing a full reboot.

---

### Post by I[AM]SMRT on 2008-08-09
I just did it for the manager and it seems to have worked, thanks :).

Now the stocks screenlet...

---

### Post by SkonesMickLoud on 2008-08-09
Might try uninstalling/reinstalling it.  If you got it from Synaptic, mark it as "Completely remove", which will remove everything related to it.

---

