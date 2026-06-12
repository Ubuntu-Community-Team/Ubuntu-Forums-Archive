---
title: "New project: Jim's First Time Script"
date: 2008-11-11
forum: General Help
---

### Post by thephotoman on 2008-11-11
I'm sure that by now, you've heard about Ultamatix and [its problems]("http://mjg59.livejournal.com/99905.html").  Admittedly, this is not the first time someone has tried to automate the process of installing codecs and potentially illegal packages on Ubuntu systems.  However, most solutions I've seen over the past 4 years have sucked in equally horrible ways.  Aside from Ultamatix, these other projects have come and gone, trying to solve the same problem:

***Automatix**: A once popular option for adding proprietary codecs, but it did so by adding third party repositories without getting their GPG signatures, amongst other grave sins.

***EasyUbuntu**: This one was a relatively safe alternative to Automatix, but instead of using APT to fetch packages, it just used wget and dpkg.  As such, if you didn't have Universe/Multiverse/some third party repositories in use, you didn't get security updates.

***The New Users Script**: This was actually a great bash script in the day, but it hasn't been updated since the Breezy Badger days as its maintainer died around that time, and nobody picked up the slack.

Now, the dev team has done a great job of creating metapackages that contain all the needed codecs (ubuntu-restricted-extras alone fetches some 30 packages that I once had to select by hand), but most new users don't know about that package.  Furthermore, advanced users generally have a list of packages that they install on their first boot (build-essential, for example, which should be in the default install but isn't).

What I've done with [Jim's First Time Script]("http://www.launchpad.net/firsttimescript") is simplified the process of adding useful and secure repositories as well as fetching patented codecs and potentially illegal packages (depending upon your location).  It's a simple Python script that adds Universe, Multiverse, and Medibuntu to your repository lists, then fetches a (currently) small list of packages using aptitude.

Try it out (instructions are on Launchpad) and tell me what you think.  Play around with it, and tell me what needs added.

---

### Post by jpeddicord on 2008-11-13
Moved to General Help; offsite programs do not count as tutorials. :)

---

### Post by bodhi.zazen on 2008-11-13
I have one of these scripts too. Installs my extra apps, configures fstab for my networks shares, etc, .zshrc, etc, etc.

I am sure my list is different from your :twisted:

Seriously though, IMO the "standard tools" are not really *that* difficult that we need tools like Ax and otherwise.

To all: No trolling please ;)

---

