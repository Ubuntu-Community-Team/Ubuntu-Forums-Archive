---
title: "What is the simplest way to get the newest compiz plugins?"
date: 2008-08-16
forum: General Help
---

### Post by Rukaru on 2008-08-16
I have the settings manager and all that stuff on my Hardy Heron, but the newest plugins (flying windows, desktop sphere, etc) can't be obtained from synaptic.  Now, I am quite new at this and I don't really understand all this "compiling" stuff. I went to this site:  [http://tombuntu.com/index.php/2008/07/25/upgrade-to-the-latest-compiz-fusion-release/](http://tombuntu.com/index.php/2008/07/25/upgrade-to-the-latest-compiz-fusion-release/)

it gives a very easy way to do it by simply going to the software sources.  My concern with this is that I don't know if I can trust this source that it gives. it's nothing about that particular source.  I just don't like to trust third party software.  What could it do?  What are the security risks?  Is there another simple but safer way to get the new compiz plugins?

[B]EDIT: Okay, I found out how to individually install specific plugins using the following guide:

[http://forum.compiz-fusion.org/showthread.php?p=56851](http://forum.compiz-fusion.org/showthread.php?p=56851)

I noticed this does not include a couple that I want.  I don't know how to get that sphere plugin; and I remember seeing on youtube some desktop snow plugin...different from the snowglobe plugin.  Are there any more new ones that are not featured in the guide I just linked to?[/B]

---

### Post by cdtech on 2008-08-16
I have a link in my signature for the plugins if you want to have a look there......

---

### Post by Rukaru on 2008-08-16
> **cdtech said:**
> I have a link in my signature for the plugins if you want to have a look there......

I don't like to click strange links.  Can someone just tell me?

---

### Post by cdtech on 2008-08-16
> **Rukaru said:**
> I don't like to click strange links.  Can someone just tell me?

Hovering will show the destination. :lolflag:

Strange Links......

---

### Post by nicedude on 2008-08-16
You can trust CD tech he is trying to help you, and I thought that is what you want. Plus your using Linux not Windows so strange links cant hurt you :-) . In general as an answer to your question if you want the newest compix-plugins or anything else then go to the source ( and then compile it :-) ).

---

### Post by hotrod6657 on 2008-08-16
yeah, not to worry about links, especially when you're running Linux and the links are in a forum member's signature :D  Good call on being cautions though

---

### Post by cdtech on 2008-08-16
> **hotrod6657 said:**
> yeah, not to worry about links, especially when you're running Linux and the links are in a forum member's signature :D  Good call on being cautions though

Yes, very good call..

---

### Post by hotrod6657 on 2008-08-16
Not sure if you're still trying to get this to happen but I'm in the process of trying this:

[http://forum.compiz-fusion.org/showthread.php?p=56851]("http://forum.compiz-fusion.org/showthread.php?p=56851")

It's from the people at compiz so i would assume it will work smoothly.

---

### Post by hotrod6657 on 2008-08-16
Alright, well i followed that guide and everything seemed successful, but when i try and enable any of the plugins the box stays checked for a few seconds and then unchecks itself.  Never enables the plugin.  I'm starting to reconsider just how badly i want fish on the inside of my cube...:confused:

Help is of course welcome because i would still love to get it working.

---

### Post by cdtech on 2008-08-16
> **hotrod6657 said:**
> I'm starting to reconsider just how badly i want fish on the inside of my cube...:confused:

:lolflag:

When it does that it means that the plugin is not installed. I'm not sure how you installed it. Don't give up we all needed the fish at one time, so you have to get it to work. :)

**P.S.**
did you restart your xsession? (ctrl alt + backspc).

---

### Post by hotrod6657 on 2008-08-16
yeah, tried restarting X, even resorted to rebooting the whole machine (old windows habit lol)  Same results...

---

### Post by hotrod6657 on 2008-08-16
what i did to install... lets say atlantis2 is this:

```
sudo apt-get install compiz-bcop compiz-dev compizconfig-settings-manager build-essential libtool libglu1-mesa-dev libxss-dev libcairo2-dev git-core
```

```
mkdir -p  ~/compiz/
```

```
cd ~/compiz
git clone git://anongit.compiz-fusion.org/users/wodor/anaglyph
git clone git://anongit.compiz-fusion.org/fusion/plugins/atlantis
git clone git://anongit.compiz-fusion.org/users/metastability/atlantis2
git clone git://anongit.compiz-fusion.org/users/metastability/cubemodel
git clone git://anongit.compiz-fusion.org/users/rcxdude/dialog
git clone git://anongit.compiz-fusion.org/users/warlock/freewins
git clone git://anongit.compiz-fusion.org/users/rcxdude/ghost
git clone git://anongit.compiz-fusion.org/users/b0le/photowheel
git clone git://anongit.compiz-fusion.org/users/pafy/screensaver
git clone git://anongit.compiz-fusion.org/users/metastability/snowglobe
git clone git://anongit.compiz-fusion.org/fusion/plugins/tile
git clone git://anongit.compiz-fusion.org/fusion/plugins/wallpaper
```

```
wget -O /tmp/elements.tar 'http://oreaus.googlepages.com/elements.tar'
wget -O /tmp/fireflies.tar 'http://oreaus.googlepages.com/fireflies.tar'
wget -O /tmp/snow.tar 'http://oreaus.googlepages.com/snow.tar'
wget -O /tmp/stars.tar 'http://oreaus.googlepages.com/stars.tar'
wget -O /tmp/wizard.tar 'http://oreaus.googlepages.com/wizard.tar'

tar -xf '/tmp/elements.tar' -C ~/compiz/
tar -xf '/tmp/fireflies.tar' -C ~/compiz/
tar -xf '/tmp/snow.tar' -C ~/compiz/
tar -xf '/tmp/stars.tar' -C ~/compiz/
tar -xf '/tmp/wizard.tar' -C ~/compiz/
```
Compiling these did give some errors, but only the .tar files, not any of the others from the get clone lines.

```
cd ~/compiz/atlantis2
```

```
make
```

```
make install
```

That all seemed to work but no go in ccsm.  Maybe that howto is no good.
(how to from here:  [http://forum.compiz-fusion.org/showthread.php?t=8214]("http://forum.compiz-fusion.org/showthread.php?t=8214")

---

### Post by hotrod6657 on 2008-08-16
hmm... here's a cruel trick.  I noticed under system tools that i now have a fusion icon that i didn't have before.  So, i clicked on it and lost all of my desktops (the cube) and my dock, but gained the fusion icon in the upper right corner of the menu bar.  Clicked it and opened the settings manager.

Didn't do much, just closed it, and then couldn't get my dock back so i opened the fusion icon again and bingo, it works!  Got all my settings back, and my dock :D  And the one effect i tried selecting (atlantis) worked!  I have fish :guitar:  Fish in need of configuring :D

That was goofy, I'm surprised there wasn't a section about that in the how-to.

Oh yeah, i also lost emerald (no top bar on the windows), just noticed that and when i opened it up again i had a bunch of extra themes (the ones that used to be installed in gusty) and all of my old ones still... Sweet!

hotrod

**EDIT:**

got emerald back, had to change the window decorator back to emerald --replace

Also, i was following a different how-to for a while and hadn't noticed any changes so i'm thinking that might be where some of this was coming from.  I don't know that it's all because of the tutorial i linked to.

Now it's almost like i have two different versions of Compiz going at the same time.  If i just reboot I get my old one, which won't let me select any of the new plugins.  But if i launch the fusion icon from application i can use the other effects.  Should I be disabling or uninstalling something to get this to work?  I really don't want to end up having more stuff running in the background than i should.

Maybe it wouldn't hurt for me to uninstall compiz all together and start fresh.  I just don't know what all i should uninstall to avoid really messing anything up.

---

### Post by Rukaru on 2008-08-16
> **hotrod6657 said:**
> Not sure if you're still trying to get this to happen but I'm in the process of trying this:

[http://forum.compiz-fusion.org/showthread.php?p=56851]("http://forum.compiz-fusion.org/showthread.php?p=56851")

It's from the people at compiz so i would assume it will work smoothly.

I tried this guide.  I did everything (and yes I already had version 0.7.4) and it didn't work even after restarting ubuntu.  It says to restart compiz, but I don't know how to do that other than restarting the computer or just closing the window.

---

### Post by durand on 2008-08-16
Did you do ***sudo** make install *instead of just *make install*?

If you want bleeding edge compiz plugins, try this script: [http://forum.compiz-fusion.org/showthread.php?t=7744](http://forum.compiz-fusion.org/showthread.php?t=7744)

---

### Post by steveneddy on 2008-08-16
Here

[http://forum.compiz-fusion.org/showthread.php?t=8214](http://forum.compiz-fusion.org/showthread.php?t=8214)

---

### Post by hotrod6657 on 2008-08-16
> **steveneddy said:**
> Here

[http://forum.compiz-fusion.org/showthread.php?t=8214](http://forum.compiz-fusion.org/showthread.php?t=8214)

I think that's the same link as I posted.  

I tried everything again on a fresh install and it works just fine.  I only did the first list of items on that how-to and did both
```
sudo make
```
```
sudo make install
```

I think the other tutorial I tried beforehand is what messed me up this last time.

hotrod

---

### Post by MattBD on 2008-08-16
Try using Ubuntu Tweak - it includes the facility to manage several third-party repositories, including Compiz. You can get it at [http://www.getdeb.net/app/Ubuntu+Tweak](http://www.getdeb.net/app/Ubuntu+Tweak)
I've used it for a while and can vouch for it being safe and easy to use. It can also get you the latest Gnome Do or Avant Window Navigator, among others.

---

### Post by Rukaru on 2008-08-16
> **hotrod6657 said:**
> I think that's the same link as I posted.  

I tried everything again on a fresh install and it works just fine.  I only did the first list of items on that how-to and did both
```
sudo make
```
```
sudo make install
```

I think the other tutorial I tried beforehand is what messed me up this last time.

hotrod

I didn't have to do that.  Right now, I'm just trying to find out about the plugins that weren't in that guide.

---

### Post by hotrod6657 on 2008-08-16
oh?  I wasn't aware there were other, i might need to do some more research myself.

---

### Post by overdrank on 2008-08-16
Moved :)

---

