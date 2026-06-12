---
title: "Karmic: Skype lists pulseaudio but not ALSA"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by scotty64 on 2009-11-06
I have installed Skype 2.1.0.47 on a new Karmic install. I notice that when I open the audio device preferences only "pulseaudio (local)" is listed. I am missing the ALSA devices - they usually showed up in Hardy - even with pulseaudio running.
What do I have to install to allow Skype to use ALSA on Karmic ?

---

### Post by scotty64 on 2009-11-08
I solved the problem by going back to Skype version 2.0.0.72.

It is a shame that Skype forces linux users to use a buggy beta by removing all download options for 2.0.0.x. But Medibuntu is the answer:
[http://packages.medibuntu.org/jaunty/skype.html](http://packages.medibuntu.org/jaunty/skype.html)
[http://packages.medibuntu.org/jaunty/skype-common.html](http://packages.medibuntu.org/jaunty/skype-common.html)

**I do not recommend installing the .debs** as the system will start holding back upgrades because of Jaunty / Karmic version conflicts!
Download the source package called skype_2.0.0.72.orig.tar.gz instead and proceed in this way:
- completely uninstall any existing Skype 2.1 installation (regardless if Medibuntu repo or .deb from Skype website was used).
- extract skype-2.0.0.72.tar.bz2 from skype_2.0.0.72.orig.tar.gz
- tar -xjf skype-2.0.0.72.tar.bz2  (or use your favourite archiver program to extract the contents of this file)
- put the resulting skype-2.0.0.72 folder in a location you like (/usr/local or home folder).
- start "skype" within this folder - or create an Icon / Launcher in your Desktop (KDE / Gnome) menu by using the icon files in the skype-2.0.0.72 folder.
- within Skype go to the "Options" and then "Notifications" to set the proper path to the sound files.

---

### Post by olivier.crespo on 2009-12-01
downgrading to previous version was indeed the only solution I found to solve my sound issues. There is however an easier way to do it through the Synaptic Package Manager:
- add "http://packages.medibuntu.org/ jaunty free non-free" to your repositories (in Settings-Repositories-Other Software)
- look for skype
- and Force version 2.0.0.72 (jaunty) (in Package-Force Version)

good luck

---

### Post by Savicava on 2011-08-08
> **scotty64 said:**
> I solved the problem by going back to Skype version 2.0.0.72.

It is a shame that Skype forces linux users to use a buggy beta by removing all download options for 2.0.0.x. But Medibuntu is the answer:
[http://packages.medibuntu.org/jaunty/skype.html](http://packages.medibuntu.org/jaunty/skype.html)
[http://packages.medibuntu.org/jaunty/skype-common.html](http://packages.medibuntu.org/jaunty/skype-common.html)

**I do not recommend installing the .debs** as the system will start holding back upgrades because of Jaunty / Karmic version conflicts!
Download the source package called skype_2.0.0.72.orig.tar.gz instead and proceed in this way:
- completely uninstall any existing Skype 2.1 installation (regardless if Medibuntu repo or .deb from Skype website was used).
- extract skype-2.0.0.72.tar.bz2 from skype_2.0.0.72.orig.tar.gz
- tar -xjf skype-2.0.0.72.tar.bz2  (or use your favourite archiver program to extract the contents of this file)
- put the resulting skype-2.0.0.72 folder in a location you like (/usr/local or home folder).
- start "skype" within this folder - or create an Icon / Launcher in your Desktop (KDE / Gnome) menu by using the icon files in the skype-2.0.0.72 folder.
- within Skype go to the "Options" and then "Notifications" to set the proper path to the sound files.
Thanks a lot for this post that helped me on my issue described in the question on the link below:
[http://ubuntuforums.org/showthread.php?t=1810427](http://ubuntuforums.org/showthread.php?t=1810427)

---

