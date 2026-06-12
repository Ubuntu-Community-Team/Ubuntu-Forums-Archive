---
title: "Can't set GlyphCache using nvidia-settings"
date: 2008-08-16
forum: Hardware
---

### Post by Starlight on 2008-08-16
Hi! I have a GeForce 8400 card, and I'm trying to do what's described [here]("http://techbase.kde.org/User:Lemma/KDE4-NVIDIA") to make KDE 4.1 work faster. But I get an error about GlyphCache... here's what I get:
> 
$ nvidia-settings -a InitialPixmapPlacement=2 -a GlyphCache=1

  Attribute 'InitialPixmapPlacement' (Komputerek:0.0) assigned value 2.


ERROR: Error parsing assignment 'GlyphCache=1' (Unrecognized attribute name).


I have everything on my system updated to the latest version, including the nVidia drivers which are version 173 like they should be. Is there some way to set that GlyphCache option?

---

### Post by thread_au on 2008-11-25
Sorry it's a bit late and you probably sorted it by now, but I believe it's a setting from version 177 and up.

---

