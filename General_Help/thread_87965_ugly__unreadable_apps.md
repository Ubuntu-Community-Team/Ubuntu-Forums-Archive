---
title: "ugly / unreadable apps"
date: 2005-11-09
forum: General Help
---

### Post by tedddee on 2005-11-09
how do i go about fixing this?

im using the default human theme

[IMG]http://members.cox.net/tedddee/ugly.png[/IMG]

[IMG]http://members.cox.net/tedddee/ugly2.png[/IMG]

---

### Post by KingBahamut on 2005-11-09
Adjust your fonts. 

Administration > Preferences > Fonts

---

### Post by tedddee on 2005-11-09
only seems to change for certain programs  :(

[IMG]http://members.cox.net/tedddee/some.png[/IMG]

---

### Post by Who on 2005-11-09
I don't know which apps have the wrong fonts, but:

I have seen simlar problems when there are badly configured GTK1 engines/thems and OK GTK2 ones - so the apps based on GTK1 will look bad and the ones based on GTK2 will be ok.
One way to test this would be to download some GTK theme engines (not gtk2) from synaptic and instal them - this may fix it.
BUT - I don't think that is the problem...
As you may know, Linux has a number of different toolkits that are commonly used to create applications. If you have configured fonts using Gnome's app it will only fix the fonts for GTK(2, perhaps 1) apps.
If the problem is with QT apps then the following will help:
Install the qt3-qtconfig package, then run the qtconfig utility to change the font size...
Also, if you install Kcontrol you will be able to apply themes to QT apps (Kcontrol is the KDE control centre, and actually is part of ubuntu). You may also have to install some QT artwork, but atleast KControl will allow you to change the fonts. 
Though the thread remained unresolved, [http://www.ubuntuforums.org/showthread.php?t=51749](http://www.ubuntuforums.org/showthread.php?t=51749) discusses a similar, maybe identical problem...

HTH
Who

Edit: I just looked at the VLC media player website, and it _would appear_ ([http://www.videolan.org/vlc/screenshots.html](http://www.videolan.org/vlc/screenshots.html)) that the app uses GTK widgets through WxWidgets. I don't know whether this is GTK 1 or2, but it probably means the QT stuff will be of no use - sorry....
BitTornado uses wxPython, so it suggests some wx weirdness, perhaps you could check synaptic to see if there are any packages with a wx in their name that look related to this problem...

---

### Post by tedddee on 2005-11-09
installed wx-common and all the wx2.6-* packages listed in synaptic

didnt change anything :(

---

