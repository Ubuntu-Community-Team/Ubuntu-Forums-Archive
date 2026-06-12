---
title: "Ubuntu 10.10 won't load X (desktop)"
date: 2011-02-07
forum: Hardware
---

### Post by MustangGT on 2011-02-07
Hello all,

I had Ubuntu 10.10 running fine on my netbook (Dell mini 10). I recently decided to install Compiz and so I used apt-get to obtain compiz and the ccsm as well.

Per the wiki I also did the following (since I have the dreaded GMA500 chipset):
```
sudo gedit /etc/X11/xorg.conf
and add the following option:
Option "ExaNoComposite" "true"
```

Anyway, I finished that and ran ```
compiz --replace
```

To my surprise, my screen flickered and compiz was up and running perfect! It ran beautiful and smoothe.

So I decided to reboot my laptop, and when I did, it begins to boot but at the Ubuntu splash screen it stops.  It just hangs.

If I hit ESC before it hangs, I get the terminal, I login and so I didn't notice any errors so I decided to try ```
startx
```

However, when I do  that I get a bunch of text and then it errors with the following message:
```
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (errno 3): Server error.
```

and it kicks me back to the terminal.  I would just reinstall Ubuntu but I have a TON of modifications to this install to get it to run my wireless card + gfx properly so it would kill me to do so.

Does anybody know how I can get this fixed?

---

### Post by MustangGT on 2011-02-07
Nevermind, I resolved my own problem.

Turns out that stupid line I added to the xorg conf file was useless and incorrect, no idea what I was thinking.

I simply used the following from the command prompt:
```
sudo nano /etc/X11/xorg.conf
```

and deleted that line.  Then saved it and ran startx.  All is fixed.

Thanks everyone! :-)

---

