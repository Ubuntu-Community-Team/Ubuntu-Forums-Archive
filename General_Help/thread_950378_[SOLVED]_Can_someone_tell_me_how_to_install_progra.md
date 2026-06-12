---
title: "[SOLVED] Can someone tell me how to install programs on Linux?"
date: 2008-10-17
forum: General Help
---

### Post by princerameses on 2008-10-17
This can get very stressful. I am trying to install Firefox and flash, but I don't know how to do that. I click download, save file (does it matter where I save it?) When it's finished downloading I right-click open, extract (all). Now this is where problems start. Where do I extract it to? Does it matter? I created a new file called "FF" and extracted it there. It then listed a bunch of files and images and such; but none of the files would open (I click on them and nothing).

I'm using opera currently.

Thanks.

---

### Post by oldsoundguy on 2008-10-17
System> Administration>  sign in .. synaptic package manager.  All kinds of programs in there

OR

Applications> add/remove programs.. sign in


Spend some time opening up those three drop down menus at the top.  You will find what has ALREADY been installed in there and the means to install more.

Later you can learn the use of terminal, but to get started, not needed.

---

### Post by hyper_ch on 2008-10-17
you should have a read here: [http://www.psychocats.net](http://www.psychocats.net)

---

### Post by jespdj on 2008-10-17
Firefox is installed by default on Ubuntu. You don't need to install it separately. Are you trying to install a special version of Firefox other than the default one that you get with Ubuntu?

Anyway, you can install Firefox and Adobe Flash with one simple command:
```
sudo apt-get install firefox flashplugin-nonfree
```
Or you can do it via Add/Remove Programs or Synaptic ofcourse.

---

### Post by mrowth on 2008-10-17
As has been said, the easiest way to install anything on Ubuntu is through the package management system. Read  [http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware) for an introduction.

About your downloads, though: When I download and extract firefox-3.0.3.tar.gz, clicking on the "firefox" script inside the archive actually runs Firefox. I'd then move the whole unpacked "firefox" directory to /opt, which seems to be a sensible location for manually installed stand-alone applications (at least it's where I've put Open Office 3, Second Life, Google Earth, Nexuiz, and Netscape Navigator 9. Yes, I use Netscape Navigator, don't look at me like that...).

---

### Post by niteshifter on 2008-10-17
> **mrowth said:**
> .... and Netscape Navigator 9. Yes, I use Netscape Navigator, don't look at me like that...).

:lolflag: Here, I'll take the heat off ya: I still use lynx. Frequently.

---

### Post by princerameses on 2008-10-17
I couldn't figure it out, but I found it in synaptic; I had to reload the repositories. (I'm on tinyme, not ubuntu)

But anyways, firefox and flash are now installed. =)

---

### Post by mrowth on 2008-10-17
> **niteshifter said:**
> :lolflag: Here, I'll take the heat off ya: I still use lynx. Frequently.
To be honest, Navigator 9 is based on Firefox 2 so it's not quite *that*... archaeological. It's got the steering wheel, though, so it's better. :)

---

