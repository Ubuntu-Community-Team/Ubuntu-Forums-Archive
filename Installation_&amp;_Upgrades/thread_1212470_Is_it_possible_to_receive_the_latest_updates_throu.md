---
title: "Is it possible to receive the latest updates through Synaptic?"
date: 2009-07-13
forum: Installation &amp; Upgrades
---

### Post by svivian on 2009-07-13
There is an annoying bug in the version of Transmission (1.51) in Synaptic for Ubuntu 9.04. I can install the latest (1.72) manually, but I was wondering if it's possible to get the latest stable releases in the repo? It would be great for other software too, like Firefox 3.5.

Thanks in advance!

---

### Post by -=hazard=- on 2009-07-13
If they are not on the repo that means that they are not tested and released by ubuntu.

---

### Post by Fully216 on 2009-07-13
Once the software release is considered a stable release, the repos are updated. I do not think beta versions are usually included.

---

### Post by svivian on 2009-07-13
> **Fully216 said:**
> Once the software release is considered a stable release, the repos are updated. I do not think beta versions are usually included.

No, I'm talking about the stable versions. Firefox 3.5 and Transmission 1.72 are both stable releases but have not been updated. There are a few other apps that are 2-4 (minor) versions behind.

---

### Post by -=hazard=- on 2009-07-13
> **svivian said:**
> No, I'm talking about the stable versions. Firefox 3.5 and Transmission 1.72 are both stable releases but have not been updated. There are a few other apps that are 2-4 (minor) versions behind.

I repeat, they must be stable versions for the product developers but till they arent tested by ubuntu team, they wont be updated on repo.

Cheerz.

---

### Post by renbla on 2009-07-14
Well install from synaptic is just an option(the best :) ). If you really really need and want a newest version, you can always search for it on the internet for deb file or source to compile ;). I always don't bother if it is not in the synaptic.

---

### Post by mcduck on 2009-07-14
> **Fully216 said:**
> Once the software release is considered a stable release, the repos are updated. I do not think beta versions are usually included.

This isn't really true.

The general rule is that after Ubuntu version is released, it's packages are not updated any more (for other than security reasons and to fix serious bugs). If there's a new version of a program it will be added to *next* Ubuntu release, not any of the current ones.

The package versions available with the original release are the ones that were tested to work with everything else doing the development, and properly testing each new program version and their dependencies after release wouldn't be possible.

There are couple of way hows this basic rule can be extended to allow some new software, but these are very limited cases and you certainly shouldn't expect any software to update for any other than security reasons.

So, if you want latest program versions you need to look for other sources than Ubuntu's official repositories. Actually these days that's pretty easy, you'll quite likely to find a PPA repository that provides latest versions of the program you want. But if you are really obsessed about always having the latest program versions you should look into some rolling-release distribution, not Ubuntu.

edit: If you find a PPA or some other third-party repository for your program, you will of course be able to install & update that program through package manager just like any other software you have. It's just that the new program versions are not going to appear in Ubuntu's official repositories.

---

### Post by issih on 2009-07-14
If you want to use synaptic so you get updates pushed out to your machine, but want more bleeding edge versions of your software than are present in the ubuntu repos, you need to find another repository or ppa to add.

e.g.:

[http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html](http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html)

Hope that helps.

Be aware of what you are doing though..

---

### Post by -=hazard=- on 2009-07-14
For me, best thing to do is update only from ubuntu official repos, because some programs must be stable and tested from their developers but maybe it will mulfuction with any other software or library on your machine. It's just and adwice. Mozilla 3.0.11 works really fine so there is not any major need to update to the latest one.

Cheerz.

---

### Post by steveneddy on 2009-07-14
Once you go out of the Ubuntu repository for Synaptic and apt then the system will become or be in an "unstable" stste.

The software in the repos is tested and stable and should deliver acceptable performance for any given system.

Is is possible to add your own ppa's and sources for software that you feel that you need.

I did this with FF 3.5. I am using Hardy and I use the ppa for the development version so I get updated daily with new FF 3.5 packages.

But I'm on an LTS version of Ubuntu, so I keep it as stock as possible.

Just add the sources from the package web page to your sources.list and you will always have the newest version of that application. **Watch out for dependencies though. Sometimes they will tie you up.**

Here are the ppa's for you to add from the Transmission website:

[http://forum.transmissionbt.com/viewtopic.php?f=13&t=5604](http://forum.transmissionbt.com/viewtopic.php?f=13&t=5604)

Installing the ppa will automatically update the app when new software is available, just like if were installed stock.

---

