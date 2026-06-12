---
title: "Kaffeine resume playback function gone"
date: 2005-11-23
forum: General Help
---

### Post by poekie on 2005-11-23
Hi

I've been using kaffeine for my movie-watching (on kubuntu breezy), but there used to be a 'resume playback' function in one of the menu's (I think it was in the settings menu) and it's gone. It was quite handy so I'm curious why it has disappeared. Did it go somewhere where I haven't seen it yet, or is this a bug? It's disappearance is not in any of the changelogs, so that's why I'm asking.
Bit of a noob btw, so take easy steps please :)

[edit] Forgot to mention, I've been having this 'problem' since I upgraded from hoary to breezy [/edit]

---

### Post by poekie on 2005-12-19
Absolutely no one else having this problem? It's weird. It seems as if the latest hoary-kaffeine with working screencaps function and so on has been replaced with a buggy earlier version for breezy. Things that had been fixed again are broken in this release.

---

### Post by noigeaR on 2005-12-19
the kaffeine version in breezy is indeed a little buggy. it crashes quite frequently. it's a newer version than the one in hoary though. hoary has version 0.6.0 and breezy has 0.7.0
i don't know about the resume playback function. haven't seen anything like this in kaffeine, but i haven't used kaffeine in hoary, so i don't know if any functions were removed between the two versions. what does this option actually do in hoary?
i'm not sure if i remember correctly, but i think (k)ubuntu switched to the gstreamer engine between hoary and breezy. try installing the xine engine for kaffeine. it has lots more options than the standard gstreamer engine. maybe your resume playback function is in there somewhere.
the install xine engine, use synaptic/adept to install the package kaffeine-xine or from a terminal run ```
sudo apt-get install kaffeine-xine
``` then open kaffeine and choose the xine playback engine in the "settings/playback engine" option. for me the xine playback engine is just named kaffeine (not kaffeine xine) in the menu and the gstreamer engine is named kaffeine gstreamer.

---

### Post by poekie on 2005-12-28
[QUOTE=noigeaR]the kaffeine version in breezy is indeed a little buggy. it crashes quite frequently. it's a newer version than the one in hoary though. hoary has version 0.6.0 and breezy has 0.7.0[/quote]
Yes, I've seen it. But the latest version I had in hoary had all those crashes fixed, that's the weird part.
> i don't know about the resume playback function. what does this option actually do in hoary?
Exactly what it says 'on the box': it resumes playback:  when you pause a film, shut down kaffeine, restart it, it remembers where you were and resumes playback on that spot. I was rather pleased with this function as I could  watch films spread over a couple of days like this.
> i'm not sure if i remember correctly, but i think (k)ubuntu switched to the gstreamer engine between hoary and breezy. try installing the xine engine for kaffeine. it has lots more options than the standard gstreamer engine. maybe your resume playback function is in there somewhere.
Hmm, maybe I should've mentioned that. I already have the xine-engine as I had trouble playing videofiles (not the right codecs etc) in gstreamer.

Thanks anyway :) 
It's just really weird that such a cool feature disappeared overnight and took some stability with it, as it seems :)

---

