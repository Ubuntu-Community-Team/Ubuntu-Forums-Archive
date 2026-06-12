---
title: "Firefox 3 in 7.04 (Feisty)?"
date: 2008-08-27
forum: General Help
---

### Post by diamond on 2008-08-27
I'm hoping someone can help me out with this.

I'm running 7.04 (Feisty) at work. I'd like to be able to update, but that's not an option right now; for the foreseeable future, I am stuck with Feisty. Which would be just fine with me (if it works, why change it?), except that the feisty repositories only have have FF2, and I'd like to upgrade to FF3.

I suppose I could download the source and try to manually build and install it, but I'd be more comfortable doing it with a .deb package.

Has anyone here done this? Is there a repository anywhere that has FF3 packages for Feisty? Or even a .deb file I can just download and install myself?

---

### Post by manoynmonic on 2008-08-28
I run feisty too.  I actually just loaded Feisty on the desktop upstairs.  Hardy is for the laptop.  You might try this(I remember doing it once a while back) in a terminal:

gksudo gedit /etc/apt/sources.list

Go through and edit all the lines that say "feisty" in your sources list to say "hardy".  Save, then 

sudo apt-get update

then

sudo apt-get install firefox

This should bump you up to ff3.  Now:

gksudo gedit /etc/apt/sources.list and change all of the "hardy" lines back to "feisty", so you don't end up upgrading your whole install.

Kind of a Rube Goldberg solution, but should work fine.

MN

edit: don't forget to sudo apt-get update after you change everything back to "feisty".

---

### Post by habtool on 2008-08-28
You could also add mozilla ppa?

deb [http://ppa.launchpad.net/mozillateam/ubuntu](http://ppa.launchpad.net/mozillateam/ubuntu) hardy main
# deb-src [http://ppa.launchpad.net/mozillateam/ubuntu](http://ppa.launchpad.net/mozillateam/ubuntu) hardy main

---

### Post by Coolcool on 2008-08-28
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by aysiu on 2008-08-28
This should help you:
[http://psychocats.net/ubuntu/firefox#terminal](http://psychocats.net/ubuntu/firefox#terminal)

And it won't require you to upgrade to Hardy or to add in Hardy repos (mixing and matching repositories is a no-no).

---

