---
title: "My Ubuntu turned into Xubuntu after upgrade to 9.10 WTF"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by razorlives on 2009-10-31
OMG what has happened here....  I clicked the upgrade button to upgrade to 9.10 via the net install and all was going well until I was asked to restart the PC. I did that and I was all of a sudden greeted with a Xubuntu splash screen and desktop.  What has happened to my precious GNOME and all my settings?  All my files appear to be intact thank god, but I'm bad at navigating Xfce.  GNOME has to still be here on the PC.  Is there a way I can get this nasty Xfce off my PC and get back to GNOME?  Would all my gnome settings still be there?  Forgive my ignorance but I don't understand how this could've happened.

---

### Post by razorlives on 2009-10-31
Ok, I've figured out how to get GNOME back and I must say it really looks stunning, especially the new Human theme.  And the fonts, wow.  They're even sharper than before, really comfortable on the eyes.  But I still want to get rid of Xfce.  Can I just mark all the packages that say Xubuntu and Xfce in Synaptic to be uninstalled and be done with it?

---

### Post by ad_267 on 2009-10-31
Yeah that should do the trick. Did you have any xfce packages installed on Ubuntu before? Kind of a weird thing to happen, but it usually works out better doing a clean install rather than an upgrade. 

Any kind of package operation shouldn't touch any files under /home so you can always retrieve your files then do a clean install if things turn to custard.

I find having a separate /home partition helps so you can just do a clean install onto your root partition and keep all your files and settings intact.

---

### Post by alienclone on 2009-10-31
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

