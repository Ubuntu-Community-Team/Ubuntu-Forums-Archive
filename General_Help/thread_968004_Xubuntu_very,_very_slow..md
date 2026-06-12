---
title: "Xubuntu very, very slow."
date: 2008-11-02
forum: General Help
---

### Post by mwilley on 2008-11-02
First off, this is being done on a desktop computer with 256MB of RAM, an Intel Pentium 4 1300MHz processor with 7 GB of free HD space and Windows XP.

So, I installed Xubuntu 8.10 with Wubi a couple days ago (I gave it 5GB) with almost no problems.  When I boot into Xubuntu, everything loads fine, but when I try to open a program or install updates, everything slows down to a degree where it is unworkable.  Opening more than one program ends up freezing everything but the mouse cursor.  Even just using Firefox for a while, it will freeze.

I was able to activate a driver for my video card (it took me a few tries to get the whole thing installed without it freezing), but that didn't help either, and there are no other drivers available in that program.  I've tried installing updates, but Xubuntu will freeze when trying to do this.

Anyway, I don't think this is normal for my system.  Even though it is about five years old, it still runs XP quite well; I expected it to run Xubuntu the same, if not better.

Any ideas why it is running like this?  I've become very interested in Linux recently, and would rather have an Ubuntu distribution as opposed to one like DSL or Puppy.

---

### Post by mwilley on 2008-11-02
Okay, I think I know what the problem is.  When I installed Xubuntu through Wubi, I had to rename swap.disk to noswap.disk to get it to load (it got stuck at 'activating swapfile swap').  Now I have no swap file (the task manager said I have 0 MB), so Xubuntu is loading completely in my 256 MB of RAM (which Xubuntu seems to think is 240 or something, even though I have a 128 MB video card, and have installed the drivers to it).

So now my question is: how do I keep my swap file while still being able to load Xubuntu?

---

### Post by gjoellee on 2008-11-02
Xubuntu is very heavy, there are nearly no difference between Xubuntu and Ubuntu anymore. However you might want to try Linux Mint XFCE edition.

---

### Post by lifestream on 2008-11-02
+1 for Linux Mint Gnome or XFCE versions.
It is a child distro of Ubuntu, but compared to Ubuntu, it is fast fast fast.

Plus it comes with all sound and video working out of the box, comes with Wicd(!!!) so you shouldn't have any Internet issues. 

Only reason I am using Intrepid is because... let's see. I got this complex that I must have the newest applications :P

EDIT: For your computer I would also recommend installing a barebones Ubuntu:

Install Ubuntu minimal CD.
then login on the black screen, and type:
sudo apt-get install xubuntu-desktop --without-recommends
when that's done do:
sudo apt-get install gnome-app-install  software-properties-gtk ubuntu-restricted-extras epiphany  pidgin banshee wicd totem

(You might need wicd repository)
deb [http://apt.wicd.net](http://apt.wicd.net) intrepid extras
(add that line to Software Sources)

Then when you login to your XFCE, go to Add/Remove from your menu, and install whatever else you want :)
I promise, it doesn't take too long!


I did that on my Ubuntu Server Virtualbox playground and I couldn't be happier :D

---

