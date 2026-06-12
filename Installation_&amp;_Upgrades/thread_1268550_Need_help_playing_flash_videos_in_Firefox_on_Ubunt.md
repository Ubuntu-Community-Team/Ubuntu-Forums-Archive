---
title: "Need help playing flash videos in Firefox on Ubuntu"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by spiritofcat on 2009-09-17
I recently bought a [PC from Zazz with Ubuntu installed on it.]("http://www.zazz.com.au/pastproducts.php?past=1353") 
For the most part it is going very well. 
Got most of the applications I need up and running, but I'm having some trouble with flash videos in Firefox. 
 
This is my first time using Linux as my primary OS, so although I do know some stuff, I'm far from an expert. 
 
The PC came with Firefox already installed, but when trying to watch videos on [www.escapistmagazine.com]("http://www.escapistmagazine.com/") I ran into some problems. 
 
First of all it told me I was missing a plugin, so I clicked the button to find and install the appropriate plugin. 
It gave me a choice of a few different ones and I chose the first in the list. It wasn't Adobe's one. 
 
After installing the plugin, I still wasn't having much luck getting the videos to play. 
I decided to try YouTube instead, and when I tried to play a video there, it asked me to install another plugin for Mpeg-4 ACC audio or something. I did that, and now YouTube sort of works, but The Escapist is still just giving me a big white space. 
 
I tried uninstalling Firefox in the hope of re-installing it fresh and clean to try again, but the add/remove utility told me it couldn't remove it, and that I should use Synaptic Package Manager. 
I found Synaptic Package Manager, and managed to uninstall firefox and all its related packages, then re-installed it with the add/remove utility, but the problem persists. 
 
I'd be really greatful if anyone could walk me through the process of finding out what plugins I have installed, checking if they are the ones I need, and uninstalling them and putting on the right ones if they aren't. 
Or even just how to completely remove firefox and all the plugins related to it and start again from scratch, this time installing the correct plugins and getting it all working. 
 
 
Edit: 
On a related note, this PC seems to struggle a little bit in general every-day display tasks such as switching tabs in Firefox, or displaying a window that was minimised. 
It has 2GB of RAM and a Celeron 2.8GHz processor. My previous PC had only 1GB of RAM and an AMD XP3200+ processor. 
It was running Windows 2000 and could switch between tabs instantly and open minimized windows without delay. 
It did have a 512MB 3D accellerated video card though, but I thought that only really helped for the high powered games, not regular browsing and workstation activity. 
That video card was AGP though, and this PC only has PCI-Express so I can't transplant it. I think I do have a slightly less good PCI-Express one in another unused PC though, so maybe I'll try installing that and see if it improves matters.

---

### Post by hal10000 on 2009-09-17
The easiest way to get rid of the wrong plugins is to open a terminal window and do this:
[COLOR="Red"]sudo apt-get remove gnash swfdec-mozilla[/COLOR]
gnash and swfdec are both flash-plugins and were supposedly installed when you were asked to.
when uninstalled, then do
[COLOR="Red"]sudo apt-get install flashplugin-nonfree[/COLOR]
then restart your firefox and be happy.

---

### Post by spiritofcat on 2009-09-17
Thanks for the reply.

Apparently gnash was not installed, but swfdec-mozilla was, so that's gone now.

Installing flashplugin-nonfree now. Hopefully that will solve it all for me.


Edit: Yes! Flash videos now play perfectly. Thank you again for your help!

---

### Post by happy mom on 2011-02-03
Thanks so much for this post! My son couldn't watch any videos on disney. It worked!!!!

---

