---
title: "Multiple desktops on same machine"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by nosmadar on 2009-05-07
I'm relatively new to the Ubuntu world and I got started with Kubuntu actually, but now that I've got the wireless working, I'd like to evaluate all 3 desktops (Xbuntu, Unbuntu and Kubuntu ) by installing the same build (Intrepid) of all 3 on one machine.  

1) Is there a preferred order that makes this work better?

---

### Post by HyRax on 2009-05-07
Simply go into Synaptic or the terminal and install the following packages:

ubuntu-desktop for the GNOME environment
xubuntu-desktop for the XFCE environment
kubuntu-desktop for the KDE environment

Or install all three.

When you login, you simply choose which environment you want for this session.

---

### Post by xebian on 2009-05-07
Or you can have 3 separate install exclusively for gnome, kde, xfce in 3 separate partitions in the same machine.

---

### Post by HyRax on 2009-05-07
> **xebian said:**
> Or you can have 3 separate install exclusively for gnome, kde, xfce in 3 separate partitions in the same machine.

...but... why?

---

### Post by Kareeser on 2009-05-07
Why?

In my experience, KDE and GNOME don't play well together. Qt applications default to KDE settings, even when running in GNOME, VLC being the prime example.

I'm too scared to try GNOME and XFCE :)

---

### Post by HyRax on 2009-05-07
> **Kareeser said:**
> Why?

In my experience, KDE and GNOME don't play well together. Qt applications default to KDE settings, even when running in GNOME, VLC being the prime example.

I'm too scared to try GNOME and XFCE :)

Hehehe... well in that case, I'd create three separate test users each utilising one of the three environments. Creating three separate partitions is over the top for such testing.

---

### Post by nosmadar on 2009-05-13
> **HyRax said:**
> ...but... why?

Because I really don't know which desk top I want to use on a permanent basis.  I've started with Kubuntu, which looks great but I hate Adept  - it keeps getting dumber and harder to use with each version of KDE IMHO.
Also most, if not all of the books all seem to be written from a Ubuntu point of view for GNOME and since I'm still learning,  it doesn't make sense to run on a UI that the resources aren't written for.  Xubuntu might have enough stuff in it to make me happy...but I'll never know if I don't try it.

Plus I want to demo Linus for some friends and lure them away from the MS "Evil Empire".  So this way I can show them a variety of UI choices.

---

### Post by HyRax on 2009-05-14
> **nosmadar said:**
> Because I really don't know which desk top I want to use on a permanent basis.  I've started with Kubuntu, which looks great but I hate Adept  - it keeps getting dumber and harder to use with each version of KDE IMHO.
Also most, if not all of the books all seem to be written from a Ubuntu point of view for GNOME and since I'm still learning,  it doesn't make sense to run on a UI that the resources aren't written for.  Xubuntu might have enough stuff in it to make me happy...but I'll never know if I don't try it.

Yeah, that's cool, but you don't need to do three physically separate installs to achieve that - You can login with whatever desktop you want using the Session menu on the login screen, ie: today I'll login with Gnome, tomorrow KDE and on the weekend, XFCE. One install, one machine, three desktop environments. :)

> **nosmadar said:**
> 
Plus I want to demo Linus for some friends and lure them away from the MS "Evil Empire".  So this way I can show them a variety of UI choices.

Oh that's easy - just show startup/shutdown time and a bit of Compiz - that gets people every time. Then point out that they don't really need MS Office, that Firefox and many other apps they use are available on all platforms, and that Windows itself doesn't actually offer them anything special (and Solitaire doesn't count because the Gnome one is actually better if you compare them!). Then if they ask about games, show them a bit of Teeworlds, Alien Arena, Sauerbraten, Battle Tanks, Pingus, I Have No Tomatoes and Savage 2 for non-commercial entertainment.

---

