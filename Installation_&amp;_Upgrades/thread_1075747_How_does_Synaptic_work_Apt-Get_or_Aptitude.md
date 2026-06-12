---
title: "How does Synaptic work? Apt-Get or Aptitude?"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by CraigPaleo on 2009-02-20
I've been reading about the differences between *apt-get install* and *aptitude install*. I'm curious as to which method is used by Synaptic to install and uninstall programs. If I choose to uninstall xubuntu-desktop through Synaptic, which is how I installed it, will everything that came with it be removed as well?

Thanks,
Craig

---

### Post by glotz on 2009-02-20
I don't know what it's based on but if you remove the xubuntu-desktop, only the meta-package itself will be removed.

---

### Post by lukjad on 2009-02-20
Synaptic runs on apt. Link: [http://www.nongnu.org/synaptic/](http://www.nongnu.org/synaptic/)

---

### Post by CraigPaleo on 2009-02-20
Thanks!

So, will I have to run the commands here to remove all of xubuntu-desktop and its associations?: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome) . 

I just want to be sure that nothing I use in k/ubuntu will be affected. If it's recommended that I use these commands, is it necessary to include the last one: ```
sudo apt-get install ubuntu-desktop
``` since I already have it?

---

### Post by SunnyRabbiera on 2009-02-20
Synaptic and aptitude are both front ends for apt.

---

### Post by glotz on 2009-02-20
> **CraigPaleo said:**
> Thanks!

So, will I have to run the commands here to remove all of xubuntu-desktop and its associations?: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome) . 

I just want to be sure that nothing I use in k/ubuntu will be affected. If it's recommended that I use these commands, is it necessary to include the last one: ```
sudo apt-get install ubuntu-desktop
``` since I already have it?

Yes, however, all the 3 metapackages (ubu,kubu,xubu) overlap, so you will have to not only use that last command but since you also want kubuntu, you'll also have to install kubuntu-desktop. So some packages will first get removed and then reinstalled. It's not going to be a problem unless you have installed manually newer versions of some packages or removed many packages. It's an unofficial guide so there's no guarantees. :-?

---

### Post by CraigPaleo on 2009-02-20
> **SunnyRabbiera said:**
> Synaptic and aptitude are both front ends for apt.

This is confusing. Everything I'd read was about differences in the commands, not front ends. I was wondering which back-end Synaptic used. Now you tell me that Aptitude is a front end to apt????

---

### Post by CraigPaleo on 2009-02-20
> **glotz said:**
> Yes, however, all the 3 metapackages (ubu,kubu,xubu) overlap, so you will have to not only use that last command but since you also want kubuntu, you'll also have to install kubuntu-desktop. So some packages will first get removed and then reinstalled. It's not going to be a problem unless you have installed manually newer versions of some packages or removed many packages. It's an unofficial guide so there's no guarantees. :-?

Ahhh! Thank you!

---

### Post by snova on 2009-02-20
> **CraigPaleo said:**
> This is confusing. Everything I'd read was about differences in the commands, not front ends. I was wondering which back-end Synaptic used. Now you tell me that Aptitude is a front end to apt????

Everything is built on top of dpkg (to the best of my knowledge). dpkg deals with .debs and not much else.

apt-get adds repositories to the mix, automatically downloaded packages from the Internet, before installing them with dpkg.

aptitude brings some more to the system. If you run it without arguments it's a complete ncurses package managar. Then you can also use it to do some higher-level operations, like automatically removing unused packages, the 'reinstall' command, etc.

Synaptic is just a graphical front-end.

---

### Post by CraigPaleo on 2009-02-20
> **SunnyRabbiera said:**
> Synaptic and aptitude are both front ends for apt.

It just dawned on me that you might be thinking of Adept, which is used as a front end by Kubuntu.

---

### Post by CraigPaleo on 2009-02-20
> **snova said:**
> Everything is built on top of dpkg (to the best of my knowledge). dpkg deals with .debs and not much else.

apt-get adds repositories to the mix, automatically downloaded packages from the Internet, before installing them with dpkg.

aptitude brings some more to the system. If you run it without arguments it's a complete ncurses package managar. Then you can also use it to do some higher-level operations, like automatically removing unused packages, the 'reinstall' command, etc.

Synaptic is just a graphical front-end.

Thanks, that helps quite a bit. I actually understand about 94.2% of it too. :D

---

