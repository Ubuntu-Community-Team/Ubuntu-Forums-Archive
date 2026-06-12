---
title: "Upgraded to 9.10 - Ctrl-W no longer works? ; Installing Air Plasma theme"
date: 2009-05-26
forum: Installation &amp; Upgrades
---

### Post by victorhooi on 2009-05-26
heya,

This is rather strange, but I just upgraded to Kubuntu 9.10 (Karmic Koala).

Upon reboot, I had a nice play around with KDE 4.3, very nice *grins*. And it feels much swifter, as well, particularly the compositing features.

One weird quirk - Ctrl-W doesn't seem to work anymore in Firefox/Chromium etc.? It should normally close the tab, but seems to do nothing on this side. Ctrl-T, Ctrl-Pageup/Pagedown still work.

I could have sworn it worked before the upgrade. Is this a known issue or something, or is there something I should check on my end?

Also, I didn't notice the Air Plasma theme, which I'd heard so much about, so I downloaded a copy from SVN (svn checkout svn://anonsvn.kde.org/home/kde/trunk/playground/base/plasma/desktoptheme/air), and put it in the desktoptheme folder. It works, but it feels a bit hackish.

That all works fine - but is there a recommended way of getting the Air plasma theme?

Also, finally, when I start new apps, they get thrown to the left side of the taskbar - I assume that's the new behaviour, right? Is there a configuration option to change this, in case I want to? The KDE menu also seems to have moved to the right - I'm guessing there's some usability logic behind this?

Cheers,
Victor

---

### Post by victorhooi on 2009-05-26
heya,

Haha, whoops, I found the solution - it's a bug in KDE, meant to be fixed upstream in trunk. Details are here:

[http://michael-jansen.biz/blog/mike/2009-05-18/kde-common-problems-ctrlw-shortcut-doesnt-work-app-xyz](http://michael-jansen.biz/blog/mike/2009-05-18/kde-common-problems-ctrlw-shortcut-doesnt-work-app-xyz)

[https://bugs.kde.org/show_bug.cgi?id=190412](https://bugs.kde.org/show_bug.cgi?id=190412)

The workaround appears to be:
> 
> kcmshell4 keys

Got to the khotkeys component and remove ctrl-w from the "Remap CTRL+W to ..." 
shortcut. This is the result of me enabling the loading of the already present
examples without considering the implications.


I've also noticed that the nice scroll feature on my Synaptics Touchpad (as in, you can scroll by dragging up and down on the right side of the touchpad) doesn't seem to work now, as it did in 9.04. Going to have to do some googling to find out why - or anybody know off the top of their head?

(And of course, tablet pc functionality still doesn't work...ah well, that's a story for another thread...haha)

Cheers,
Victor

---

