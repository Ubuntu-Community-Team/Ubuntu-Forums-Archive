---
title: "Just started using Ubuntu and need some help"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by IaReSlyFoX on 2008-12-12
Hey,

I just installed Ubuntu (First time i've ever used another OS besides windows) and for the most part I'm lost.  I was trying to download some app's from [http://www.getdeb.net/](http://www.getdeb.net/) but when I download them and the package installer comes up it says "ERROR: Dependency is not satisfiable:libboost-date-time 1.34.1" and I searched a but on google and i found a thread and the guy told the OP to go to the Synaptic Package Manager and install whatever the error message was (his was something like libdev or devc) so I looked for libboost but couldn't find it.

So pretty much I am loving Ubuntu but I really don't know what I need to do - along the lines of downloading apps - so if anyone could help me I would appreciate it.

So for example what do I need to do to get the error to go away.

Thanks

---

### Post by fubbleskag on 2008-12-12
```
sudo apt-get install libboost-date-time1.34.1
```

---

### Post by IaReSlyFoX on 2008-12-12
Ha ha.  Sorry.  Where do I put that?  In the Synaptic.

---

### Post by doctorbighands on 2008-12-12
You type that into a terminal. Whenever you see a command like that, it'll go into the terminal.

You can find that by clicking Applications > Accessories > Terminal.

---

### Post by IaReSlyFoX on 2008-12-12
Alright thank you.  I was messing around in there to see what it was about.

EDIT: It says [Sudo] password:  but it wont let me type.

---

### Post by doctorbighands on 2008-12-12
I should've thought of that!

Your "sudo" password is the same one you use to log in to Ubuntu when you boot up. "Sudo" gives you temporary root privileges in order to perform certain functions. As you go farther along in Ubuntu, you'll find you use sudo quite a lot.

When you enter your sudo password into the terminal, it's going to look like you're not typing anything, but you actually are. It doesn't give you asterisks or anything - you just have to trust your fingers! :)

EDIT: This ([https://help.ubuntu.com/8.10/index.html](https://help.ubuntu.com/8.10/index.html)) is some excellent reading for anyone who's new to Ubuntu. It's written for version 8.10, but I believe the information applies fairly universally to all releases. It's a gentle introduction, and there's lots of info in there for folks switching over from Windows. If you Google, you can find LOTS more (and I mean LOTS) introductory information. Feel free to come back here to the forums as much as you need to, also!

---

### Post by IaReSlyFoX on 2008-12-12
Ha ha thanks.  Yea I was trying to figure that out ha ha.

It's saying it couldn't find the package.  

But I pretty much just need to replace the "sudo apt-get install **libboost-date-time1.34.1**" with whatever the error is?

---

### Post by doctorbighands on 2008-12-12
Sometimes that'll work. It could also be that the name of the package you're trying to install isn't typed in precisely, and that's important. A period or dash misplaced means the terminal won't be able to find what you want.

An alternative would be to open Synaptic Package Manager (System > Administration > Synaptic), search for "libboost" (without the quotes), and see if you can find the package you need. It might be easier that way than trying to guess what the package manager wants from you.

---

### Post by IaReSlyFoX on 2008-12-13
> **doctorbighands said:**
> Sometimes that'll work. It could also be that the name of the package you're trying to install isn't typed in precisely, and that's important. A period or dash misplaced means the terminal won't be able to find what you want.

An alternative would be to open Synaptic Package Manager (System > Administration > Synaptic), search for "libboost" (without the quotes), and see if you can find the package you need. It might be easier that way than trying to guess what the package manager wants from you.

Alright thanks for your help.

Alright so I downloaded the package for the time and date.  Then it gave me another filesystem error so I downloaded that and it still gives me the error even though in the terminal it says it's up to date. And neither one are in the Synaptic Package Manager.  

This is fun though. ha ha.

---

