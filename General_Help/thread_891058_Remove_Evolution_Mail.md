---
title: "Remove Evolution Mail?"
date: 2008-08-15
forum: General Help
---

### Post by TrikeKid on 2008-08-15
So, I made the rookie mistake of removing evolution through synaptic, reinstalled evolution and ubuntu-desktop so everything is running as it should again. I have this glitch though, that makes having things on my system that I don't use bother me. I'd like to get rid of stuff like Evolution mail and Ekiga that I don't use/want to use, but I'd like to actually have my panels and clock etc stick around. Can I do this?

---

### Post by wilbbe01 on 2008-08-15
If you were sure whatever you didn't want you could probably just delete it or something.  I hate the fact I can't delete stuff I don't use as well.  I like things clean.  I however do not uninstall anything of those forced ubuntu apps, I remove them from the menu if anything, and forget about them.  I'm not sure, but if you were to just delete the program you would likely get it back when an update was released.  I'm just guessing, but I assume there would be a way to not install evolution.  Anyway, I would just leave it, unless you count your hard drive space in megabytes you probably don't need to worry about extra thigns like that, just hide the links and pretend they are gone.

---

### Post by tangibleorange on 2008-08-15
what's wrong with:
```
sudo apt-get purge evolution
```
to remove (for example) evolution?

---

### Post by memr1st0r on 2008-08-15
I removed Evolution but the package manager keeps wanting to send me Evolution file updates. Harmless probably but annoying.

I'm sure I removed it, because the apt-get purge command given in this thread reports that the Evolution package is not installed.

How do I tell my Ubuntu system that I don't want Evolution updates?

Thank you.

---

### Post by TrikeKid on 2008-08-16
> **tangibleorange said:**
> what's wrong with:
```
sudo apt-get purge evolution
```
to remove (for example) evolution?
I didn't know to try it. :mrgreen:

---

### Post by tangibleorange on 2008-08-16
> **memr1st0r said:**
> I removed Evolution but the package manager keeps wanting to send me Evolution file updates. Harmless probably but annoying.

I'm sure I removed it, because the apt-get purge command given in this thread reports that the Evolution package is not installed.

How do I tell my Ubuntu system that I don't want Evolution updates?

Thank you.

hmm. what happens if:

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

and then search for evolution in synaptic. what does it show by its box? (green or not green). also check the sections tab in the bottom left - if there is a not installed (residual config) tab, you can safely click on all the pakcages in that bit and right click, completely remove them.

---

### Post by steveydoteu on 2008-08-16
First and foremost it would be ***--purge*** rather than *purge*.

Moving on, you can more or less totally remove Evolution from the system, the only package that needs to be left to keep dependencies in line is *evolution-data-server-common* (See attached screenshot).

I have also managed to remove numerous other packages from a default install to slim it down quite considerably.

[http://www.stevey.eu/2008/08/diet-ubuntu-revisited/](http://www.stevey.eu/2008/08/diet-ubuntu-revisited/)

---

### Post by memr1st0r on 2008-08-16
After clean, update, upgrade, Synaptic shows these as green:

evolution-common
evolution-data-server
evolution-data-server-common
evolution-webcal

The installed and latest versions are the same.

I do not see any residual config or not installed tab in Sections.

Tangibleorange, is that Ubuntu tutorial site you linked to (psychocats) yours? It is great.

---

### Post by Tom--d on 2008-08-16
> **memr1st0r said:**
> After clean, update, upgrade, Synaptic shows these as green:

evolution-common
evolution-data-server
evolution-data-server-common
evolution-webcal

The installed and latest versions are the same.

I do not see any residual config or not installed tab in Sections.

Tangibleorange, is that Ubuntu tutorial site you linked to (psychocats) yours? It is great.

Remove all packages with evolution- APART from evolution-data-server-common It has to stay.
Then Evolution is removed.

---

### Post by Vivaldi Gloria on 2008-08-16
> **Tom--d said:**
> Remove all packages with evolution- APART from evolution-data-server-common It has to stay.
Then Evolution is removed.

Nope. This worked in a single computer but borked the other three I tried. 

Removing evolution is dangerous. Sometimes it works but most of the time it does NOT. Don't try it.

---

### Post by hotrod6657 on 2008-08-16
> **Tom--d said:**
> Remove all packages with evolution- APART from evolution-data-server-common It has to stay.
Then Evolution is removed.

that seemed to work for me, haven't rebooted yet but everything appears to be alright and i don't have evolution anymore.  

hotrod

---

### Post by patrickfromspain on 2008-08-16
As said, you just need to keep evolution-data-server-common. It's safe to remove the rest.

---

### Post by Vivaldi Gloria on 2008-08-16
> **patrickfromspain said:**
> As said, you just need to keep evolution-data-server-common. It's safe to remove the rest.

How can you say "it's safe" with confidence? Are you taking responsibility if it doesn't work?

I repeat, I removed evolution without removing data server and the next time I couldn't login because gdm said something of the sorts "no home folder found". This happened to me three times!

I admit that I tried it in the early days of hardy and may be an update fixed things but you should be more conservative when suggesting users something which could potentially harm their system.

---

### Post by hotrod6657 on 2008-08-16
upon reboot everything is still alright.  Not sure if i just got lucky or if the advice given is in fact correct but on my system it seems to have worked just fine.

---

### Post by steveydoteu on 2008-08-16
> **Vivaldi Gloria said:**
> Nope. This worked in a single computer but borked the other three I tried. 

Removing evolution is dangerous. Sometimes it works but most of the time it does NOT. Don't try it.

You must be doing something wrong, it has never caused issues with me on numerous systems. Provided evolution-data-server-common is left it causes no issues.

---

### Post by chinasteve2000 on 2008-08-25
Dear all,

I followed the advise of uninstalling all but evolution-data-server-common, and for the record, it worked fine with a week-old fresh install of Hardy (8.04 for those like me who need reminding). 

Also for the record, Synaptic had me upgrade evolution-common before I could uninstall it. So I just uninstalled it separately. :-)

I've rebooted to test and it looks good. The only thing that I'd like to get rid of still is the update for evolution-data-server-common. Do you know if that's possible?

THANKS!

Very glad to be only getting a 73KB update now,
Steve

---

### Post by Irihapeti on 2008-08-25
I removed Evolution from my system several days ago and everything is working well. And I've rebooted several times during that time.

To prevent evolution-data-server-common from updating, select it in synaptic, then go to Package -> lock version.

Irihapeti

---

### Post by chinasteve2000 on 2008-08-25
COOL...I like that. Thanks!

---

### Post by chinasteve2000 on 2008-08-30
It has all worked very smoothly. Thanks to all...I don't think I can thank more than one person in one thread, so Muchos Gracias to all!
-Steve

---

