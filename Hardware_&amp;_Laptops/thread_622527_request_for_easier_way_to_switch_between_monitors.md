---
title: "request for easier way to switch between monitors"
date: 2007-11-24
forum: Hardware &amp; Laptops
---

### Post by jmagick07 on 2007-11-24
Ubuntu doesn't seem to recognize the "monitor switch" button on my laptop. (which is a button almost all laptops have, so it's stupid it isn't recognized as a feature)

And "System -> Administration -> Screens & Graphics" requires a logout/login every time you make a change (this is not good when working on a project that may require switching monitor view from clone to dual displays often).

How about an easier way to switch between monitor displays, with changes made in real-time rather than this logout/login crap?

---

### Post by finer recliner on 2007-11-24
dual monitor support (which includes the VGA out on most laptops) is still in a very beta stage and undergoing development. this is a pitfall of probably all linux distributions. in fact, i think ubuntu is the first to even try offering a simple GUI interface to setup dual monitors. in prior releases, i had to manually edit my xorg.conf file and do a lot of trial and error to get my dual monitors to work correctly. 

be patient, better support will come with time.

---

### Post by jcsteele on 2007-11-24
Depending on your graphics card, you might try looking at the xrandr tool ([http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)) works fine for me most of the time when I try to clone my desktop to a network projector..maybe in time [https://answers.launchpad.net/ubuntu/+question/7162](https://answers.launchpad.net/ubuntu/+question/7162) will work again, which should provide you with more information (launchpad is down for maintenance right now).

//jcs

---

