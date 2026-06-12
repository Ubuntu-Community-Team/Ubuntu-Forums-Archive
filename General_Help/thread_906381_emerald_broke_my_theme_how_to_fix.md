---
title: "emerald broke my theme how to fix?"
date: 2008-08-31
forum: General Help
---

### Post by Garratt on 2008-08-31
Hello

A few weeks ago I decided to reformat due to a strange bug i had not being able to install any themes that would work 100% (that and a number of other issues)

so i reformatted and everything worked fine, I didn't install emerald theme on my pc, which i thought was the problem last time.

today i reformatted my g/f's computer and installed beuce's  icon theme,
but i was just following how-to multimedia, and custom effects posts, so was just copying and pasting everything....

I completely forgot that emerald kills the ability to install themes properly, and accidently installed it, needly to say my icon theme set broke instantly, and now i cannot reinstall it.

So i tried:
```
sudo apt-get remove emerald
```
but the icon themes don't work still is there anything else i need to do to fix this?

---

### Post by rune0077 on 2008-08-31
Emerald really should not be destroying your icon-theme. Emerald is only responsible for the windows decoration, and has nothing to do with the icons. I think your problem may lie elsewhere.

---

### Post by Garratt on 2008-09-01
nope it was emerald, after i rebooted i was able to drag the package back on to themes and it installed.
I had tried 20+ times to install it prior to that and it would not.

Probably would have helped if i done that before posting but what the heck... 

I know emerald is great and lots of people love it.

 I think what the problem is that once you install it you got to install themes via emerald or they don't work 100%. personally i prefer to just use the gnome version, at least it works.

if you are using emerald at the moment try this for a test.

download and install [BuuF-Deuce-iconset]("http://gnome-look.org/content/show.php/BuuF-Deuce-iconset?content=46201")

and install it via: right click desktop > themes, drag and drop.

that icon set should replace almost every single icon on your desktop/awn/cario/applications settings/etc/etc/etc/.

but when i have emerald installed it does not. i only see 3-4 icons that change(and 90% of the time icon sets fail to install), like folders in places, and 1 or 2 differences in the applications, but apart from that 97% of the rest are the default human icons.


So... I got lucky finding and comming to that conclusion and since that has been a situation now on 2 different computers of mine, thats enough not to ever want to touch it again.

If you test and find that I am right, you may want to send in a bug report.

Thats probably why the extras got taken out of repos, shame they didn't take it all out.

---

### Post by rune0077 on 2008-09-01
> **Garratt said:**
> nope it was emerald, after i rebooted i was able to drag the package back on to themes and it installed.
I had tried 20+ times to install it prior to that and it would not.

Probably would have helped if i done that before posting but what the heck... 

I know emerald is great and lots of people love it.

 I think what the problem is that once you install it you got to install themes via emerald or they don't work 100%. personally i prefer to just use the gnome version, at least it works.

if you are using emerald at the moment try this for a test.

download and install [BuuF-Deuce-iconset]("http://gnome-look.org/content/show.php/BuuF-Deuce-iconset?content=46201")

and install it via: right click desktop > themes, drag and drop.

that icon set should replace almost every single icon on your desktop/awn/cario/applications settings/etc/etc/etc/.

but when i have emerald installed it does not. i only see 3-4 icons that change(and 90% of the time icon sets fail to install), like folders in places, and 1 or 2 differences in the applications, but apart from that 97% of the rest are the default human icons.


So... I got lucky finding and comming to that conclusion and since that has been a situation now on 2 different computers of mine, thats enough not to ever want to touch it again.

If you test and find that I am right, you may want to send in a bug report.

I already have that theme installed :) (I love it, though not using it at the moment). I installed it while Emerald was installed, and it works fine. What version of Ubuntu are you using?

I don't have a "themes" when I right-click my desktop. Here's how I install it: System > Preferences > Apperances, then click "Install" and point the browser to the theme packages (a tar.gz file). That's it. Then I can click "Customize", go to the "Icons" tab and select my theme from there.

---

### Post by Garratt on 2008-09-01
ubuntu 8.04, and the emerald version downloaded was the link from the sticky'd post "great desktop effects faq".

yea well when i was experiencing the problem only 20-30% of "ICON themes" downloaded from gnome-look.org would work.

I guess it's a bit hard for you to test if you already have it... so maybe someone else could test.

I dont see what else it could be tho, because i didn't install anything else after emerald, and removing it....

my vlc player is broken as well, and i have no idea why, i hear a extremely loud static noise. which worked fine up until I started following the FAQ post and installing desktop effects.

---

### Post by Garratt on 2008-09-01
bump!

---

