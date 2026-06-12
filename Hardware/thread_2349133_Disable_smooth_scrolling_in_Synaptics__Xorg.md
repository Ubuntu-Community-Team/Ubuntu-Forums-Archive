---
title: "Disable smooth scrolling in Synaptics / Xorg"
date: 2017-01-11
forum: Hardware
---

### Post by Maximus559 on 2017-01-11
I have a recurring problem in Xubuntu 16.04 where smooth scrolling causes poor performance in Google Chrome (still relevant as of Chrome 55). The problem only affects notebooks with touchpads.

I started [another thread]("https://ubuntuforums.org/showthread.php?t=2330283&p=13515595#post13515595") discussing this symptom, but after some more research, I'm getting the impression that Chrome's behavior is by design and not a bug per se. What I would like to do at this point is disable smooth scrolling in the Synaptics driver and/or Xorg itself.

There appear to have been some changes recently to the way Synaptics and Xorg handle scrolling:

[http://who-t.blogspot.com/2011/09/whats-new-in-xi-21-smooth-scrolling.html](http://who-t.blogspot.com/2011/09/whats-new-in-xi-21-smooth-scrolling.html)
[http://who-t.blogspot.fr/2012/05/whats-new-in-synaptics-160.html](http://who-t.blogspot.fr/2012/05/whats-new-in-synaptics-160.html)

According to the second link, the smooth scrolling I'm seeing in Chrome is a result of the Synaptics driver generating scrolling valuators instead of scroll events. Apparently only some applications know how to handle the valuators, which explains why scrolling is smooth in Chrome but not in LibreOffice or the Xubuntu settings manager, for example.

It would be nice if I could change Chrome's scrolling behavior, but I wouldn't mind turning off smooth scrolling globally. The problem is, I can't find any settings that would allow me to do this. The [Synaptics manual]("https://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html") doesn't offer any help here.

Any ideas?

---

