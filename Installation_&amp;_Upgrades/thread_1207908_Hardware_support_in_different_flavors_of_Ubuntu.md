---
title: "Hardware support in different flavors of Ubuntu"
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by Buce on 2009-07-08
This question is for a Dell E1505 laptop, and I have Hardy in mind because I prefer LTS, but I'm open to suggestions.

The short question: Does a base install (the installation that doesn't come with a GUI) of Ubuntu from the alternate CD have the same hardware detection as a normal installation?

The long explanation: I started out my Linux experience using Ubuntu, switched to Arch Linux some time ago in order to learn more, and am now finding that I don't have the time to hassle with a distribution that uses rolling upgrades.

I'm gonna make the switch back to Ubuntu, but the only GUI apps I need are firefox, thunderbird, pidgin, skype, pulseaudio volume control, and occasionally thunar and deluge. Basically, I want a lightweight, fluxbox-based desktop without all the bells and whistles that come with GNOME or KDE. What I very much *don't* want, though, is to struggle for hours just to get my hardware to work. I'm okay with configuring xorg, and really, wouldn't mind setting up any other hardware if I knew I only had to do it once, but I'm generally annoyed with driver configuration and maintenance and wish there was a rolling-release-based distro that didn't make that so hard.

In sum, I fight and compete with the computers at work, and I just want my computer at home to play with me and be my friend. I think Ubuntu is the best distro for that, but I'm not sure how to go about installing. When I first used Ubuntu (and this was Hardy), I did the standard GNOME-based install, and the only thing I had to do out of the box for things to just work was update everything and accept a single proprietary driver for something (don't remember what the 'something' was). If I started with the slimmed-down, GUI-less installation off the alternate CD, would it be that simple, or am I better off starting with a default install and removing the stuff I don't need (essentially removing GNOME and adding fluxbox)?

To restate and reiterate:
Dell E1505 Laptop
Ubuntu Hardy
Fluxbox
Firefox
Thunderbird
Skype
Handful of other GUIs
Not too much hardware fuss
Which Ubuntu should I install?
Thanks in advance!

---

### Post by earthpigg on 2009-07-08
this how-to certainly makes it look like the answer is yes:

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

but i myself have never done an ubuntu minimal install.

---

### Post by Buce on 2009-07-09
Okay, so I accidentally installed the default installation instead of the base one. What packages do I need to remove to have just the bare essentials, including the ubuntu-standard package? Would 'sudo apt-get remove ubuntu-desktop' followed by a 'sudo apt-get autoremove' do the trick?

---

### Post by b.a.w on 2009-07-09
ubuntu-desktop is just a meta package that installs a group. Uninstalling it doesn't break any dependencies so autoremove won't find anything to remove. It may be easier to just reinstall if you don't have to much on the install already. Finding all the unnecessary packages may prove to be a huge pain.

---

### Post by Buce on 2009-07-09
Okay, I think I was confused before. I thought the Alternate CD had an option to install a minimal ubuntu system, but it looks like that functionality is only provided in the Minimal CD. Problem is, that CD downloads packages during the install, and I have only a wireless connection -- no ethernet. Is there any way to get a minimal install without ethernet?

EDIT: Woops, nevermind. F4 -> Install command line system on the Alternate CD main menu will hopefully do the trick. Am trying this now.

---

### Post by Buce on 2009-07-09
> EDIT: Woops, nevermind. F4 -> Install command line system on the Alternate CD main menu will hopefully do the trick. Am trying this now.

This worked, but now I've got a minimal install with no wireless. Hopefully I can install the needed packages from a CD. I'm looking around for how to do that now, but if someone has some helpful info or links, it'd be much appreciated. Seems like every howto assumes access to an ethernet connection.

---

### Post by Buce on 2009-07-10
Well, I'm still trying to get wireless working, but since this is a network problem now and not an installation question, I'm opening a new thread.

EDIT: And after dinking around with this for a few days, the answer to my original question is yes, but getting the hardware to work sometimes requires configuration that's difficult to get info on. Lots of tutorials will tell you to go to the Administration menu to configure hardware, and finding the command-line equivalents is difficult. I think the solution here is to not use 'ubuntu' as a keyword when searching for solutions to various problems, substituting 'debian' or 'linux' instead, but YMMV.

---

