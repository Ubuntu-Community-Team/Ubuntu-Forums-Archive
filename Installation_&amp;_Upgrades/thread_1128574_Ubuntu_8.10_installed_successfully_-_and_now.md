---
title: "Ubuntu 8.10 installed successfully - and now?"
date: 2009-04-17
forum: Installation &amp; Upgrades
---

### Post by mac-christian on 2009-04-17
Hi all

I have now successfully installed Ubuntu on an old Powerbook G3 (old-world Mac). I have used the "PPC Alternate" ISO download, as well as [these instructions]("http://gonz.wordpress.com/2006/03/22/installing-ubuntu-510-breezy-badger-on-an-old-world-powerbook-g3-wallstreet/"). All went smoothly, and now I am able to start up in Ubuntu. 

But: My Ubuntu has a command line interface only. What are my possibilities to add a graphical desktop (like KDE) to my installation, and where can I find all the software downloads which I would eventually need?

Thanks, Mac-Christian

---

### Post by Mercury_Alpha on 2009-04-17
The "alternate install" does not come with a GUI, so you'll need to install one from the command line. Depending on which particular [flavor of G3 Powerbook]("http://en.wikipedia.org/wiki/PowerBook_G3") you have, you may be able to squeeze Gnome onto it, but you're probably better of with [Xubuntu]("http://www.xubuntu.org/"), which uses a much lighter-weight GUI.

---

### Post by mac-christian on 2009-04-18
> **Mercury_Alpha said:**
> The "alternate install" does not come with a GUI, so you'll need to install one from the command line. 
So I'd need to find a place from where to download a suitable version of KDE, X, or GNOME... didn't find one so far.

> **Mercury_Alpha said:**
> Depending on which particular [flavor of G3 Powerbook]("http://en.wikipedia.org/wiki/PowerBook_G3") you have, 
It's the "Wallstreet" model (called "Wallstreet II" in the page you referenced) with the bigger screen, a 300 MHz processor and 192 MB RAM (I think this was the maximum RAM for this model).

> **Mercury_Alpha said:**
> you may be able to squeeze Gnome onto it, but you're probably better of with [Xubuntu]("http://www.xubuntu.org/"), which uses a much lighter-weight GUI.
I visited the Xubuntu page, but all I saw there were specialised downloads for i386 and AMD 64bit processors. I am not afraid to download some source code and compile it on my machine as long as I get some instructions on how to do it, or I am also prepared to install again using a different distribution (Xubuntu, Kubuntu, ...) If there is a possibility to do so.

Mac-Christian

---

### Post by sandy8925 on 2009-04-18
Yeah you should most probably get Xubuntu. Although since you have a 300 Mhz processor I seriously don't know how well it will run. Better see the minimum reqts and then decide. The minimum RAM required is 192 MB so that's OK.

---

### Post by mac-christian on 2009-04-18
> **sandy8925 said:**
> Yeah you should most probably get Xubuntu. 
And **where** do I find a version that can be installed on a PPC G3?

> **sandy8925 said:**
> Although since you have a 300 Mhz processor I seriously don't know how well it will run. Better see the minimum reqts and then decide. The minimum RAM required is 192 MB so that's OK.
Is there a previous release which is less demanding on the hardware?

Mac-Christian.

---

### Post by Elegia on 2009-04-18
Can't you use apt-get to install whatever you need? Something like 'sudo apt-get install xfce4' would install the xubuntu desktop environment.

---

### Post by mac-christian on 2009-04-18
> **Elegia said:**
> Can't you use apt-get to install whatever you need? Something like 'sudo apt-get install xfce4' would install the xubuntu desktop environment.
Yes, that did the trick - Thank you!

Mac-Christian

---

