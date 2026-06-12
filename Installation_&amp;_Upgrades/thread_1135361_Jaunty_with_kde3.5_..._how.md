---
title: "Jaunty with kde3.5 ... how ?"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by michiedo on 2009-04-24
How can I install Kubuntu Jaunty Jack with KDE3.5  ?

From [www.kubuntu.com](www.kubuntu.com) I installed  the "alternate i386" and then I followed the directions in [http://apt.pearsoncomputing.net/](http://apt.pearsoncomputing.net/) (repository of KDE3.5).
then dpkg-reconfigure kdm ... -> kdm-kde3
rebooted	
All went ok, but I still have the "4" manager :-(

Is there some step that I'm missing ?

Thank you :-))

---

### Post by Phil Urich on 2009-06-28
No one seems to have replied to you :( and I just stumbled upon this here, so I shall try.

I've never had that issue myself, but I *do* know that apparently sometimes you have to dpkg-reconfigure ALL the display managers (since kdm-kde3 might still think kdm(4) is in charge, or something?).  Can't say I quite get why, but I've heard it in instructions elsewhere so it's worth a try (although by now you probably fixed things).

I did want to add a comment here just to mention that if you go over to [http://apt.pearsoncomputing.net](http://apt.pearsoncomputing.net) there's the unfortunate news that the servers got fried by EMP damage from nearby lightening strikes, one within 100 feet!  So if you've got a bit of spare cash around and feel like donating it to something Ubuntu+KDE related there's always that, erk!

---

### Post by calsaverini on 2009-09-18
I installed kile-kde3 from this instructions:
[https://wiki.kubuntu.org/Kubuntu/Kde3/Jaunty](https://wiki.kubuntu.org/Kubuntu/Kde3/Jaunty)

But can't find the binary to execute and open kile and no icon shows up. Anyone knows what happened? (I'm using jaunty ubuntu with gnome).

---

### Post by Phil Urich on 2009-10-11
> **calsaverini said:**
> I installed kile-kde3 from this instructions:
[https://wiki.kubuntu.org/Kubuntu/Kde3/Jaunty](https://wiki.kubuntu.org/Kubuntu/Kde3/Jaunty)

But can't find the binary to execute and open kile and no icon shows up. Anyone knows what happened? (I'm using jaunty ubuntu with gnome).

You'll have to make a new .desktop file with the full spiel, or run it from a terminal with all the environmental variables set.  Personally I've just duplicated existing .desktop files (ie. menu entries) and then changed them to add the environmental variables (I'm using KDE4, but the KDE3 versions of stuff like Amarok and K3b and etc, so I have "Amarok-KDE3" and "k3b-KDE3" and etc menu entries).

Here's an example of the command for k3b:

```
PATH=/opt/kde3/bin:/opt/kde3/games:/opt/kde3/bin:$PATH KDEDIRS=/usr/:/opt/kde3/ KDEHOME=$HOME/.kde3 XDG_DATA_DIRS=/opt/kde3/share/:/usr/share/ MANPATH=/opt/kde3/share/man k3b
```

So for Kile, I assume it'd just be:

```
PATH=/opt/kde3/bin:/opt/kde3/games:/opt/kde3/bin:$PATH KDEDIRS=/usr/:/opt/kde3/ KDEHOME=$HOME/.kde3 XDG_DATA_DIRS=/opt/kde3/share/:/usr/share/ MANPATH=/opt/kde3/share/man kile
```.

Sorry that I didn't see your post here for 3 weeks or so, my subscriptions page never seems to tell me when there's new posts, strangely (and I mainly lurk over at the Kubuntu forums, since to be blunt it seems more often that one gets answers over there).

Anyways, you've probably figured this stuff out on your own by now, but I figured just in case :)

---

