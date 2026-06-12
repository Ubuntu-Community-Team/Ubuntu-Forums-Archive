---
title: "Could someone make a .deb of this???"
date: 2005-11-21
forum: General Help
---

### Post by uberlinux on 2005-11-21
[http://ubuntuforums.org/showthread.php?t=93222](http://ubuntuforums.org/showthread.php?t=93222)
It's the best interactive firewall I've seen to date.
Towards the bottom of the page are the links to the RPMS and source

---

### Post by taurus on 2005-11-21
If you want to convert RPM to deb, use "alien" then!!!

---

### Post by uberlinux on 2005-11-21
[QUOTE=taurus]If you want to convert RPM to deb, use "alien" then!!![/QUOTE]
is that clean?  What I'm worried about is that things won't transition smoothly.

---

### Post by mhancoc7 on 2005-11-21
You can open a terminal window and change the directory to the one that has the rpm. Then run this command.

sudo alien -i NAME OF RPM.rpm

That should convert the rpm to a deb and install it. I have done this successfully with a few apps.

You can also run the following command to creat a deb.

sudo alien -d NAME OF RPM.rpm

Hope that helps. I know how frustrating it can be when you ask a question and you get an answer like, "Use alien!", with no explanation.

God Bless, Jereme:smile:

---

### Post by bored2k on 2005-11-21
[QUOTE=uberlinux]is that clean?  What I'm worried about is that things won't transition smoothly.[/QUOTE]
It's a hit or miss roulette. If it works, it works. If it doesn't, it doesn't. Try it, at most the deb won't work.

---

### Post by uberlinux on 2005-11-21
OK, so I got it in with alien, and when trying to run the daemon, I got this
```

pest@blustation:~/ifw$ mandi &
mandi: error while loading shared libraries: libdbus-1.so.0: cannot open shared object file: No such file or directory
[1] 12611
[1]   Exit 127                mandi

```
so I went and got the RPM for that and aliened it, still no dice.

---

### Post by towsonu2003 on 2005-11-21
looks nice, why not put it in the repositories? 

posted request here:
[http://www.ubuntuforums.org/showthread.php?p=510385#post510385](http://www.ubuntuforums.org/showthread.php?p=510385#post510385) , but I'm not hoping much.

also, this post (quoted below) was very disturbing as I'm hoping we won't become one of those distro where people curse at you when you ask a newbie question:

> 
If you want to convert RPM to deb, use "alien" then!!!


just giving a wiki / howto link to alien would be much more constructive...

[http://www.ubuntuforums.org/showthread.php?t=64557&page=6](http://www.ubuntuforums.org/showthread.php?t=64557&page=6) post #56 looks nice and it took me 2 minutes to find... Wouldn't take longer for other helpers (who tend to be extremely more experienced than me) either...

---

### Post by aysiu on 2005-11-21
[QUOTE=towsonu2003]
just giving a wiki / howto link to alien would be much more constructive...[/QUOTE] I wrote a whole page about every way to install software in Ubuntu:

[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

---

### Post by uberlinux on 2005-11-21
[QUOTE=towsonu2003]looks nice, why not put it in the repositories? 

posted request here:
[http://www.ubuntuforums.org/showthread.php?p=510385#post510385](http://www.ubuntuforums.org/showthread.php?p=510385#post510385) , but I'm not hoping much.
[/QUOTE]
well, I hope someone gets it working under Debian, and thanks for requesting it.

---

