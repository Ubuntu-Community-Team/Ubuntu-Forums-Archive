---
title: "Generic Gentoo a possibility?"
date: 2008-12-02
forum: Gentoo and derivatives
---

### Post by insane_alien on 2008-12-02
Now, I know this would likely be shot down in flames by gentooers but this may be a good way to encourage more people to use gentoo.

If perhaps there is a 'generic' install media where it sets up an unoptimized gentoo on your PC with a GUI (similar to what you get when you install ubuntu) and a wizard to help newbies go through the process of optimizing their system if they want.

I for one would love it. I get the concept of USE flags but I still don't understand what ones I should use. Not to mention all the other settings. 

Basically, this is to put an end to the arduous task of the initial install.

PS. Yes, I have RTFM. 

PPS. If anyone knows of a USE flag generator site/script where it asks you about your system and preferences and then generates your use flags for you i would be grateful.

---

### Post by canistra on 2008-12-02
well, there is sabayon linux ... so there is no need for a generic gentoo, that will only ruin the image of gentoo ...

---

### Post by kk0sse54 on 2008-12-03
> **insane_alien said:**
> Now, I know this would likely be shot down in flames by gentooers but this may be a good way to encourage more people to use gentoo.

If perhaps there is a 'generic' install media where it sets up an unoptimized gentoo on your PC with a GUI (similar to what you get when you install ubuntu) and a wizard to help newbies go through the process of optimizing their system if they want.

I for one would love it. I get the concept of USE flags but I still don't understand what ones I should use. Not to mention all the other settings. 

Basically, this is to put an end to the arduous task of the initial install.

PS. Yes, I have RTFM. 

PPS. If anyone knows of a USE flag generator site/script where it asks you about your system and preferences and then generates your use flags for you i would be grateful.

The closest thing to a generic Gentoo would be using the generic kernel other than that like mentioned before you might want to try Sabayon since an unoptimized generic install of Gentoo would defeat the very purpose of using Gentoo. 

As for USE flags check out [http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=2&chap=2](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=2&chap=2) and here's a list of all the USE flags [http://www.gentoo.org/dyn/use-index.xml](http://www.gentoo.org/dyn/use-index.xml). Basically USE flags adds support for particular packages for example if I was installing elinks and wanted support for bittorrent I would either add it to my make.conf or use it as a local variable so it's used for only elinks which in that case the command would be  USE=bittorrent emerge elinks. 

Alternatively they can also be used to indicate you don't want support for that particular package for example I run a gnome only system so in my make.conf I have -qt3 -qt4 -kde because I don't want KDE support for any of my packages. You don't need to go crazy picking out as many USE flags as possible but add those that you want your system to be optimized for, you can always add a global USE flag later on in your make.conf and rebuild the affected packages (can take some time depending on how many packages are affected.)

---

### Post by RedSquirrel on 2008-12-13
> **insane_alien said:**
> If perhaps there is a 'generic' install media where it sets up an unoptimized gentoo on your PC with a GUI (similar to what you get when you install ubuntu) and a wizard to help newbies go through the process of optimizing their system if they want.

Actually, the latest plans for Gentoo are to focus on the minimal CD and weekly stage3 tarballs.


> **insane_alien said:**
> I for one would love it. I get the concept of USE flags but I still don't understand what ones I should use. Not to mention all the other settings. 

That's not a big deal. You will learn it as you go along. If you are new to Gentoo and you are setting up a desktop system, I recommend you use the **desktop** profile. That should have most of the USE flags you need. It is no problem to modify your USE flags later on; you just have to rebuild the affected packages.


> **insane_alien said:**
> Basically, this is to put an end to the arduous task of the initial install.

The manual installation described in the Gentoo Handbook is a way to learn something about Gentoo while you're installing it. You will need to know all this stuff to maintain the system anyway.

---

### Post by RedSquirrel on 2008-12-13
> **C!oud said:**
> Basically USE flags adds support for particular packages for example if I was installing elinks and wanted support for bittorrent I would either add it to my make.conf or use it as a local variable so it's used for only elinks which in that case the command would be  USE=bittorrent emerge elinks.

Note that if you set USE flags like that, your settings will be dropped the next time the package is emerged. ;)

If you add your per-package USE flags to /etc/portage/package.use instead, the settings will be remembered the next time the package is emerged.

Setting USE flags on the command line is useful for testing (with emerge --pretend <...>) or for certain rare cases where you want to set a USE flag to achieve a particular purpose.

---

