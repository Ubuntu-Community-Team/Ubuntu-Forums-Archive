---
title: "package ubuntu-desktop broken after upgrade"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by troelskn on 2009-05-22
Hi.

I just upgraded from Intrepid to Jaunty, and during the process it said something about package "ubuntu-desktop" and asked me to report it as a bug. I proceeded with the install and everything went sort-of well, although it said something about doing ```
sudo dpkg --configure -a
``` somewhere near the end. After restart, there's now a warning-sign in my taskbar with the message:

> An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: ' Error: BrokenCount > 0'This usually means that your installed packages have unmet dependencies.

Doing so, shows "ubuntu-desktop" as a broken package. I tried selecting the menu option "Fix Broken Packages", but I'm afraid to go through with it, since it appears that Synaptic is trying to uninstall "ubuntu-desktop", which supposedly would take down my desktop?

What should I do?

PS. Not sure if this is related, but I have two instances of pidgin in my taskbar at the moment, and they have different icons. I remember having installed something for using msn a few months back. Could this be the root of the problem?

---

### Post by dustman on 2009-05-22
> **troelskn said:**
> 

What should I do?



You could proceed with the uninstall of "ubuntu-desktop". You can always install it later: 
```
sudo apt-get install ubuntu-desktop
```
I uninstalled -> installed it just now, with no problem (or so it seems). From what I know, you will lose your GUI (and have only command line Ubuntu) if you uninstall the packages "gnome-desktop*" -> that is if you use Gnome as a desktop environment.

But do what you think it suits you best, I'm just telling some things that I would do if I were you.

Cheers,
Radu

---

### Post by troelskn on 2009-05-22
Thanks, but that is not entirely helpful, since I obviously don't know what I should do. Are you saying that "ubuntu-desktop" is not the actual GUI, whereas "gnome-desktop" is?

---

### Post by dustman on 2009-05-22
> **troelskn said:**
> Thanks, but that is not entirely helpful, since I obviously don't know what I should do. Are you saying that "ubuntu-desktop" is not the actual GUI, whereas "gnome-desktop" is?

When I uninstalled the "ubuntu-desktop" package, it said:
```
After unpacking 45.1kB disk space will be freed.
``` whereas when I tried uninstalling the "gnome-desktop[COLOR="Blue"]*[/COLOR]" (please note the [COLOR="Blue"]*[/COLOR] at the end of "gnome-desktop") I got the message:
```
After unpacking 53.8MB disk space will be freed.
```
If you take into account the huge difference in size between these 2 uninstalls, you can say that "ubuntu-desktop" is just a small part of your whole GNOME environment. As I said, you can always install it later, even if for example you lose your Graphical User Interface, by using the command line: 
```
sudo apt-get install ubuntu-desktop
```

As I said, that is what I would do...I am only human and could be wrong though...

Cheers,
Radu

---

### Post by troelskn on 2009-05-25
OK. I finally got it working, by typing the following magical incantations into my shell. I have no idea which of those commands actually solved my problem, but it worked afterwards. In case anybody else has the same problem, you could try this (I think it's safe to run them in any case):

```
sudo apt-get update
sudo apt-get install -f
sudo apt-get autoremove
sudo apt-get dist-upgrade
sudo dpkg --configure -a
sudo apt-get update --fix-missing

```

---

### Post by mcduck on 2009-05-25
> **troelskn said:**
> Thanks, but that is not entirely helpful, since I obviously don't know what I should do. Are you saying that "ubuntu-desktop" is not the actual GUI, whereas "gnome-desktop" is?

Yes. Ubuntu-desktop is not actual package, but just a metapackage that is used to get all the stuff that belongs to Ubuntu's default desktop.

In other words, it's empty package that has all the default stuff marked as it's dependencies. On the other hand, none of the actual programs depend on the ubuntu-desktop package so installing it will install the default setup, and removing it only removes the metapackage itself.

---

