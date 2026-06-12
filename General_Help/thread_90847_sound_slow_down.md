---
title: "sound slow down"
date: 2005-11-15
forum: General Help
---

### Post by iamsobored056 on 2005-11-15
everytime there is an instant message sound on gaim, my music playing on rythmnbox slows down.  Does anyone know how to fix this?  I just upgraded to Breezy, and Hoary didn't have this problem.

---

### Post by iamsobored056 on 2005-11-17
no one wants to help me?  aww...

---

### Post by slux on 2005-11-17
Probably not so much that nobody wants to but nobody knows how to. :P

It's either a change in the config between the two Ubuntu versions or a driver regression I guess. How are you sounds set up? Do your sounds get played thru esd or straight without a separate sound daemon? You could be able to do something for the problem by not using esd and letting alsa do the mixing (or I suppose the other way around as well). Some settings like buffer sizes might have an effect too...

---

### Post by ColinG on 2005-11-17
I've had problems with sound reproduction on Breezy as well. I actually prefer the Gnome desktop and for that reason moved from Kubuntu. I'm a reasonably regular user of KIno (video editor) and whilst sound, when playing back video clips, was ok in Kubuntu it was terrible in Ubuntu. Disabling system sounds helped and routing the sound through Alsa helped more, but the quality in Gnome was not as good as KDE.

I'm now back with Kubuntu but why should two desktops show such different results? Any ideas and is there a way around the problem?

Thanks

PS I should mention I did not so much experience sound slow down as just jerky/fuzzy sound.

---

