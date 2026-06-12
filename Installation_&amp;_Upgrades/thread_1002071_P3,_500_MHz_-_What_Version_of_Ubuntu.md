---
title: "P3, 500 MHz - What Version of Ubuntu?"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by jbzeigler on 2008-12-04
I recently obtained an old PIII 500MHz machine.  It is completely formatted with no OS.  I want to install Ubuntu but don't know what version would even run on something this old.  Any ideas?

---

### Post by Pumalite on 2008-12-04
This might help:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by snowpine on 2008-12-04
> **jbzeigler said:**
> I recently obtained an old PIII 500MHz machine.  It is completely formatted with no OS.  I want to install Ubuntu but don't know what version would even run on something this old.  Any ideas?

Hi and welcome to the forums! I have a Dell laptop that is PIII, 500mhz. I've tried out a whole bunch of linux flavors or "distros" and here is some advice.

First, install as much ram as you can. Computers of that era typically max out at 512mb, which I would consider a comfortable minimum for Ubuntu. If you have less than 256mb, your options are severely limited. 

Second, many distros (including Ubuntu) have a choice to install from a Live CD or an Alternate CD. You definitely want the Alternate CD; it uses a text-based installer that seems to work better with older hardware.

The first distro I tried on my laptop was Ubuntu 7.10 (the most recent version at the time). It ran just fine, though kind of slow. Very user friendly. 

As I learned more about Linux, I started experimenting to find a faster option. "Distro hopping" like this is very addictive! :)

Xubuntu is a well-supported, "official" version of Ubuntu that uses a lighter desktop environment (Xfce) for a boost in performance. Other non-official Ubuntu variants are even faster (such as Fluxbuntu and my personal favorite, Crunchbang) but the downside is a smaller user community and no corporate backing. The fastest distros I've tried were not related to Ubuntu at all: SliTaz and Sidux. Not sure I would recommend those two to a beginner though. :) Puppy Linux is a popular choice for beginners with old hardware, though I've never been able to get it up and running on my hardware.

Hope that helps you out somewhat. I guess what I'm saying is it might take you a little while to find the perfect distro for you. Xubuntu is probably as good a place to start as any. You can try the 8.04 Hardy Heron release, which is a more stable, long-term support release, or the newer 8.10 Intrepid Ibex. 

Good luck, please ask lots of questions!

---

### Post by abn91c on 2008-12-04
> **jbzeigler said:**
> I recently obtained an old PIII 500MHz machine.  It is completely formatted with no OS.  I want to install Ubuntu but don't know what version would even run on something this old.  Any ideas?

i have a generic intel celerom 400mhz with 448mb ram, pc100 motherboard and a nvidia gforce mx400 video. Ubuntu 8.10 runs fine, a bit slow but very usable since I have a wireless belkin USB adapter for broadband internet. It also had an old ISA sound card wich i got to work using the guide available here in the forums. So the pIII 500 will probably be Ok, jus run he live CD and see what happens, Mandriva 2009 also likes older PC's I used kde4.1 on this same pc also

---

### Post by tgalati4 on 2008-12-04
I've got 768 MB (3 DIMM slots) in my Dell GX1 Optiplex (500 Mhz, PIII).  I run Linux Mint Darnya XFCE (based on Gutsy) on mine.  It's OK.  OpenSUSE11.1RC-KDE4.1 and Fedora10 are slow on it.  

SliTaz runs quite well.

---

### Post by binbash on 2008-12-04
linux mint fluxbox edition or xfce

---

### Post by inobe on 2008-12-04
> **jbzeigler said:**
> I recently obtained an old PIII 500MHz machine.  It is completely formatted with no OS.  I want to install Ubuntu but don't know what version would even run on something this old.  Any ideas?

what is the make and model ?

---

### Post by peterthewolf on 2008-12-04
Depends what you want but I would recommend

Debris Linux - uses ubuntu repos

Zenwalk

Both quick on old kit

---

### Post by jerrykenny on 2008-12-04
xubuntu   definitely :-)

Also keep the partitioning to a minimum, and use the older ext2 file system


And keep a knoppix disk handy for emergencies.

Bump the comments re more ram

---

### Post by Mark Phelps on 2008-12-05
I have an "old" laptop with the same CPU and I had been running Xubuntu 7.04 on it, a bit slow, but useable.  I was unable to upgrade beyond that because I could not get better than 800x600 screen res on the newer versions.

I installed PC Linux OS 2007 and it worked fine.  Able to find all the hardware, including default screen res of 1024x768.  Again, a bit slow but useable.

Replaced that with the Zen-Mini version, also from PC Linux OS, which was written and configured for slower, less-powerful machines.  Worked great!

Suggest you check out the Zen-Mini version.  The link below is to the PCLOS Gnome 2008 forums: 

[http://linuxgator.org/forums/viewtopic.php?f=1&t=1341]("http://linuxgator.org/forums/viewtopic.php?f=1&t=1341")

---

