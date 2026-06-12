---
title: "Oops - I made a booboo an broke Ubuntu"
date: 2008-08-18
forum: General Help
---

### Post by b63craasx7aga4n on 2008-08-18
I'm running Hardy on an Acer Aspire 5630

For the past few weeks, I've been seeing errors when updating / upgrading using aptitude, due to a hal (service | daemon) not being able to restart.

This was not a problem until Xsane broke with an regular update (epson photo 3170 scanner), and I then needed to fix the hal dependency.

Cutting a long story, I removed hal, and everything else broke too

(I did manage dump the screen output, and found that gnome-mount, gnome-power-manager, gnome-session, gnome-volume-manager, hal, hal-cups-utils, hwdb-client-common, hwdb-client-gnome, network-manager, network-manager-gnome, pulseaudio-module-hal, sound-juicer, ubuntu-desktop, update-notifier had all been removed)

Using a USB key install, I have downloaded all of the relevant .deb files (using apt-get install --reinstall --download-only)

However, when I log into a failsafe terminal on my main pc, I cannot reinstall any of the deb packages to try and fix the previous balls up.

What other information would I need to provide so that someone can point me in the right direction?

---

### Post by itix on 2008-08-19
I think this might require some serious bash hacking (which I suck at). I think the problem here is that many of those packages require some of the missing packages as requirements.

Also, .deb's are best installed with *sudo dpkg-i file.deb*.

The esiest way to go on about this, I think, would be to nick somebodies external hard drive (or use your own) and back up valuable data and do a complete reinstall.

---

### Post by b63craasx7aga4n on 2008-08-20
Thanks foe the response.

I have managed to fix the issue, and I won't pretend for one second that it was optimal or pretty.

For a while I attempted to install the packages from the failsafe terminal, copying in deb files from various places, such as a USB install - this led to version problems.

I then found that hal doesn't really like to be installed with an xserver running at all (no idea why), and I began installing debs from different terms (tty1 etc) - then it was just a case of copying over different debs to get networking running, tracking down a network cable, as wireless didn't work (only 3 hours to figure that one out :(), and eventually running dpkg --configure -a, apt-get update, apt-get force, apt-get upgrade and I now have a correctly running machine.

And 115 deb files archived for future booboos.

---

