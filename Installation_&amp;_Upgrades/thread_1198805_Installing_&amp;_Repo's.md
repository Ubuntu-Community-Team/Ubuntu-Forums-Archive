---
title: "Installing &amp; Repo's"
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by Doman on 2009-06-27
Okay, so I'm reading on practically every installation guide I can find that almost everything I need will be in a repo.  Well, I'm new to Ubuntu & am looking for a way to install the following:  [http://code.google.com/p/pidgin-facebookchat/](http://code.google.com/p/pidgin-facebookchat/)  I've heard of incompatabilites beteween Linux versions & installing the wrong package type or whatever might screw up my install, which is not something I really want to deal with risking.  & Is there a list of other safe repo's that I might be able to access as well?

I've used Ubuntu briefly in the past and broke my OS so many times trying to figure out theming that I gave up after two weeks.  I have modest Unix experience, having had a mac for the last 4 years.  It's been a while since I've linux'd & I'm hoping I was just an idiot when I tried this a few years back, but I'm hesitanty to play with metacity/emerald/whatever, not that I, to be honest, even remember anything significant about them.  The mere potential to customize the look of my UI is too much to pass up, so can anyone throw me a bone?

Anyway, thanks & I hope to hear from you soon.
-Doman

---

### Post by bobbob1016 on 2009-06-27
If you install with the .deb listed on that site, you should be fine.  It will make sure you have the right version of Pidgin, and everything.

If it does mess something up, it is highly highly unlikely it'll be anything vital since Pidgin isn't vital.  The worst you'd have to do would be purge "sudo aptitude purge pidgin" and "rm ~/.pidgin/*" to remove pidgin and all it's settings, then "sudo apt-get install pidgin" to bring it back again.

---

