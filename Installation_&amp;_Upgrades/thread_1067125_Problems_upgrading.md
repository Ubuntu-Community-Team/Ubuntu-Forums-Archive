---
title: "Problems upgrading"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by elchato on 2009-02-11
So, I've been using Hardy for several months now and never made any of the upgrades it asked me to do... till today (250 all in all). And now I'm having all sorts of problems, like when I start the computer there's some sort of problem with gnome where I cant see or use the network manager, battery status or brightness control for like 5 minutes. Only then it goes back to normal. It also takes some 5 to 10 minutes to turn off the computer.

What the hell happened? Is there anyway to go back in time before this happened?

Also, I've been having problems with flash videos and sound drivers... like, If I'm using amarok, flash videos won't play. If I've seen a flash video during my session, amarok or any other video won't work. I guess it has something to do with JACK not working (?)

Thanks in advance!

---

### Post by cariboo on 2009-02-11
From the sounds of it your upgrade didn't complete. When upgrading to the next version make sure any ppa's you have enabled are diabled.

Open a Applications-->Accessories-->Terminal and type:

```
sudo apt-get install -f
```

that should install any missing dependencies, then in the same terinal type:

```
sudo apt-get update && sudo apt-get upgrade
```

Jim

---

