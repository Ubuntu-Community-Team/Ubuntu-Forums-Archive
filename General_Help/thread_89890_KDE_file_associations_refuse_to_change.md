---
title: "KDE file associations refuse to change"
date: 2005-11-13
forum: General Help
---

### Post by pestie on 2005-11-13
I'm trying to add an application to the list of apps available for "Open with..." in KDE. I've tried two approaches - using kcontrol, and right-clicking the document on my desktop, choosing "Open with...", choosing the application (in this case I'm trying to associate Kate with HTML documents), checking "Remember application association for this type of file." In both cases, I see the "updating system configuration" dialog pop up briefly, everything looks like it works, but then the association is immediately forgotten. If I use kcontrol to re-order the existing list of apps (making, say, Firefox the preferred application for opening HTML documents), it *does* remember that, so I know settings are being properly saved. But I can't for the life of me force KDE to add Kate to that list and remember it. Anyone have any idea what's going on here?

---

### Post by daller on 2005-11-14
[QUOTE=pestie]I'm trying to add an application to the list of apps available for "Open with..." in KDE. I've tried two approaches - using kcontrol, and right-clicking the document on my desktop, choosing "Open with...", choosing the application (in this case I'm trying to associate Kate with HTML documents), checking "Remember application association for this type of file." In both cases, I see the "updating system configuration" dialog pop up briefly, everything looks like it works, but then the association is immediately forgotten. If I use kcontrol to re-order the existing list of apps (making, say, Firefox the preferred application for opening HTML documents), it *does* remember that, so I know settings are being properly saved. But I can't for the life of me force KDE to add Kate to that list and remember it. Anyone have any idea what's going on here?[/QUOTE]

It's a known problem, and it has been fixed i KDE3.5

(Find info on how to upgrade on [www.kubuntu.org](www.kubuntu.org))

---

### Post by pestie on 2005-11-14
KDE 3.5 is just a "beta 1" release according to what I'm seeing on kubuntu.org, so I'm a bit hesitant to install it. Is there some discussion of this bug somewhere else, maybe with a workaround?

---

### Post by daller on 2005-11-14
[QUOTE=pestie]KDE 3.5 is just a "beta 1" release according to what I'm seeing on kubuntu.org, so I'm a bit hesitant to install it. Is there some discussion of this bug somewhere else, maybe with a workaround?[/QUOTE]

It reached Release Candidate 1, some day ago!

---

### Post by daller on 2005-11-14
It's the newest annoncement!

---

### Post by gts on 2006-01-04
I've noticed this bug with the earlier versione of kde; now that I have Kde 3.5 nothing seems to be changed... I can't set my associations because kde forgets them: this is terribly annoying!! (but I must say that Kde 3.5 for me is perfect apart this bug)

am I the only one that's still in trouble with this?

---

### Post by ad noiseam on 2006-01-04
I am not in front of Kubuntu right now, but I know that, on my machine, I can go in the Konqueror preferences and set up the file associations I want, and it works perfectly. This is on KDE 3.5.

---

### Post by agostonbejo on 2008-05-27
Just another confirmation of the problem:

I have Kubuntu Feisty Fawn, KDE 3.5.6, and the file associations get forgotten when set from kcontrol as well as from Konqueror.

---

### Post by agostonbejo on 2008-05-27
And I've found the solution as well:
[https://bugs.launchpad.net/ubuntu/+source/kdelibs/+bug/157166](https://bugs.launchpad.net/ubuntu/+source/kdelibs/+bug/157166)

Quoting the important part:

"
File associations, I finally discovered, are stored in ~/.kde/share/config/profilerc. Somehow, that file had become owned by 'root'.
[...]
The work around is to do this in a terminal:
sudo chown yourusername ~/.kde/share/config/profilerc
(replacing 'yourusername' with your actual login name).
"

It works for me as well! (That was exactly the case on my system, which has recently been installed and I definitely haven't changed that file myself.)

---

