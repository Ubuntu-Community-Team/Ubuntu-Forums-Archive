---
title: "Which Epiphany should I use?"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by Luxx on 2009-11-07
The choices are epiphany-webkit, epiphany-gecko, epiphany-browser. 

When I first upgraded from Jaunty to Karmic I found Epiphany-gecko in Applications > Internet with no icon. I pointed it to an icon, dragged it to the panel at top of desktop and it seemed to be working both from Applications menu and from panel, but then suddenly nothing opened when I tried the icon later. In trying to get information on getting epiphany working I came across several webpages that said epiphany-browser should be used instead of the gecko or webkit options in Karmic. So I switched to epiphany-browser as suggested. I feel I have been mislead as nothing seems to work right in this version.

I've heard good things about Epiphany. Tabbing is so efficient, VLC with noflash greasemonkey scripts work great much better than flash or better than bulky FF, easy to use any Firefox addons... but I can't get it to do anything I have heard it does so well. Was any of it true? There are no tabs, The fonts are almost unreadable and extensions are almost non-existent. Yet, for just a few minutes after upgrade and reboot epiphany-gecko seemed to work, looked good and had the recognizable extensions menu with the icons just like FF, until I closed the browser. I can't duplicate that now.

Over the last 2+ years using Ubuntu I have managed to get just about anything I had problems with working with enough searching, trying again, and sometimes having to ask questions. This one seems to have me stumped. 

What I am trying to do is minimize the load on my CPU by using a browser lighter than Firefox and bypass that nasty flash to view video in (or out of) the browser. I tried The new Shiretoko and it was great for the first few minutes and then got so bogged down over time that there was no response to input on webpages and it took more than 2 minutes to get it to close. I've read all kinds of threads on both subjects, getting video to work and specifically which Epiphany to use in Karmic and now I'm just confused.

Any advice much appreciated. Sorry for the long post.

---

### Post by nortexoid on 2009-11-07
epiphany-gecko uses the same backend as Firefox and development for it has stopped. It's good though. The latest Epiphany has moved to webkit, and 2.28.x is actually quite good barring a few annoyances that, from what I can tell, can be blamed mostly on webkit rather than Epiphany. I would go for epiphany-webkit. You need both the webkit ppa and the epiphany one as well.

---

### Post by Luxx on 2009-11-07
Thank you for your reply. I wasn't aware development for epiphany-gecko came to a halt. Why on earth? I thought it was the gecko engine and continuing development that brought Ephipany into the Karmic release of Ubuntu in the first place -- since it was working so well in Jaunty. And it was. I tried it for a bit.

It seems development for other browsers with the FF backend have also gone astray in the last year. I don't get it.

A slimmer browser that uses the FF extensions with the Greasemonkey addon seemed to be a simple solution to my problems with flash and high CPU usage when viewing video in a browser. 


At least now I know what went wrong with Epiphany on my computer and will give webkit a try and see what it can do.

---

### Post by julianb on 2009-11-07
Webkit based browsers are typically really quick and work fine on slow machines.

My favorite webkit based browser is Chrome. Chrome for linux has extensions, Java, and Flash support. (you need the flash plugin package). It is fast.

You can download the .deb package for ubuntu/debian machines here:
[http://dev.chromium.org/getting-involved/dev-channel](http://dev.chromium.org/getting-involved/dev-channel)

you may need to use
```
sudo apt-get -f
```
after installing chrome from the .deb package. After install chrome will automatically ask you if you want it to download updates (the same way other programs do, using repositories).

---

### Post by Luxx on 2009-11-08
Thanks for your input. I'll look into that as well.

I've decided to install and compare Firefox's Namaroka, Epiphany and Chromium. Comparisons will probably take a while since I want to try different video viewing options and see what each one can do. 

This isn't just for myself and my old computer, but my daughter now has a newer computer that seems to be overwhelmed by it's oversized proprietary OS. Well, I found the solution to that a few years ago! It's time to check out Distro Watch and fire up the ISO burner. 

She uses her computer differently, so she may want an OS and a browser that does different things than what I want. This will be fun. ;)

---

