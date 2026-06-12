---
title: "Breezy Upgrade Woes... (Synaptic seg fault and Language Selector)"
date: 2005-11-10
forum: General Help
---

### Post by vkkim on 2005-11-10
I just upgraded to Breezy using sudo apt-get dist-upgrade, and *almost* everything went perfectly well--except two things:

1-Whenever I try to run sudo synaptic, bash spits out "Segmentation Fault" and stops.  Yes, I've read the other threads, and I've tried purging synaptic and reinstalling from the [officially burned] Breezy CD.

2-I read the post-upgrade notes, which told me to do this "Language Selector" thing.  I tried, but nothing happens after I click "apply."  For a long time.  As in hours.

Please help me!

---

### Post by tseliot on 2005-11-10
A clean installation will solve your problem. Then you can use Automatix in order to make your life easier (it will install many useful things for you)

---

### Post by vkkim on 2005-11-10
[QUOTE=tseliot]A clean installation will solve your problem. Then you can use Automatix in order to make your life easier (it will install many useful things for you)[/QUOTE]

I am at school, and I do not have access to unlimited bandwidth.  Is there a version of Automatix that I could download once with all the .debs I need if I need to reinstall everything?  If I recall correctly, there was an "Ubuntu add-on CD" made by the guy who made ubuntuguide.org that did this.

---

### Post by tseliot on 2005-11-11
[QUOTE=vkkim]I am at school, and I do not have access to unlimited bandwidth.  Is there a version of Automatix that I could download once with all the .debs I need if I need to reinstall everything?  If I recall correctly, there was an "Ubuntu add-on CD" made by the guy who made ubuntuguide.org that did this.[/QUOTE]
Sorry but I don't think it exists yet. Nonetheless you can get the packages you need by doing the following things:

[QUOTE=]go under "/var/cache/apt/archives" (after you have used Automatix or have got the packages manually) and take all the .deb files you need and  burn them on a CD.[/QUOTE]

The next time you need to install them (e.g. on another PC or if you need to reinstall your system) you can install them by doing:

[QUOTE=]copy the debs to your harddisk (e.g. from the CD)[/QUOTE]

Then

[QUOTE=]cd directory_containing_the_debs
sudo dpkg -i *.deb (in this way it will install all the packages with only 1 command)[/QUOTE]

---

