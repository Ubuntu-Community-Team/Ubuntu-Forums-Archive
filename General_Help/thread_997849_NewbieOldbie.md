---
title: "Newbie/Oldbie"
date: 2008-11-30
forum: General Help
---

### Post by jalor@yousee.dk on 2008-11-30
Hi.

I am new to ubuntu and the package systems used in linux in general, coming from a freebsd background. Is there anyone can point me in the direction of how to download and compile sources for various packages used in ubuntu? 

I have installed ubuntu 8.10 (32 bit and 64 bit), there are a couple of things nagging me (wvdial for one), so I thought I would grab the source and start fixing som of the small problems I stumble upon.

However, downloading sources seem to be somewhat more difficult---how/where do I find the sources for the packages that come with ubuntu? How do I make them compile?

Thanks in advance,
Jacob.

---

### Post by aheckler on 2008-11-30
[http://packages.ubuntu.com/intrepid/wvdial](http://packages.ubuntu.com/intrepid/wvdial)

Source code is over there on the right. You can search for any package and get its code as well.

---

### Post by CatKiller on 2008-11-30
Welcome to the Ubuntu community.

Linux is different from BSD in that all of the source trees for each of the packages is completely independent. That is, the kernel source is kept in the Linux git tree. The Firefox source is in the Mozilla's Mercurial repository. wvdial will be somewhere else.

So although you can get the source for the packages you are using simply enough - aheckler's method for a Web interface, ```
sudo apt-get source wvdial
``` if you want to use the package management system (and you have the appropriate source (deb-src) repository enabled) - the method to get your changes upstream varies quite wildly for each project.

---

### Post by jalor@yousee.dk on 2008-11-30
Yeah - I found the source and some dependency libraries to download, thanks for your help everybody. It just took me by surprise that even if I could run the program, I could not compile it without installing additional libraries (which I thought I had but needed in developers' version).

Very impressed with ubuntu distribution, the package system and all the automated installations. I even have my old Windows XP partition running in a vmware window for those few programs I absolutely need in windows still...

> **CatKiller said:**
> Welcome to the Ubuntu community.

Linux is different from BSD in that all of the source trees for each of the packages is completely independent.



---

### Post by CatKiller on 2008-11-30
> **jalor@yousee.dk said:**
> It just took me by surprise that even if I could run the program, I could not compile it without installing additional libraries (which I thought I had but needed in developers' version).

It's the old binary/source thing. If you're only installing binary packages, you don't need the header files. So they get put in a separate package so that only the people that need them get them.

Glad you're enjoying Ubuntu :)

---

