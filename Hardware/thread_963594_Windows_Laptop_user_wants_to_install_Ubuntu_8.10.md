---
title: "Windows Laptop user wants to install Ubuntu 8.10"
date: 2008-10-30
forum: Hardware
---

### Post by 333halfevil on 2008-10-30
Well I have been a window user most of my life.  I tried Ubuntu 7.10 with Wubi.  It ran pretty well.  I want to upgrade to 8.10.
I only have 384 MB of ram.  What items can i turn off (remove) So that I can make it run fast on my laptop I dont mind losing eye candy. and being able to run firefox with alot of tabs open is important.

---

### Post by nullspace on 2008-10-30
If you want to run a light system then I suggest you try xubuntu. 
[http://www.xubuntu.org/](http://www.xubuntu.org/)

It's still a newbie friendly interface.

---

### Post by 333halfevil on 2008-10-30
I want to keep gnome if possible.  I like the app interfacess

---

### Post by Idefix82 on 2008-10-30
The first thing you will probably want to do is replace compiz by metacity. Both are Window managers but metacity is much lighter than compiz (and consequently less eye candy). A generously sized SWAP partition might also help.

---

### Post by snowpine on 2008-10-30
One service I like to turn off for a small but noticeable performance boost is Tracker. And obviously you should not be using compiz visual effects if speed is a concern.

RAM upgrades are very inexpensive these days, and that's the best solution if you want to open lots of Firefox tabs at the same time.

---

### Post by nullspace on 2008-10-30
Well you did say trim off the eye candy, gnome is eye candy . So using a lighter WM is a quick easy way to reduce strain on the system. You can install the xubuntu WM with out a full reinstall but I am not sure your are comfortable with a terminal. 

 I am pretty sure by default the eye candy like compiz is disabled. If not you can go to System >> Preferences >> Appearance and click on the tab "Visual Effect" and make sure non is selected.

Now running firefox with a lot of tabs is a huge resource hog. Easily can hit 200MB.

your going to have to give on some things here.

---

### Post by bytor4232 on 2008-10-30
> **333halfevil said:**
> Well I have been a window user most of my life.  I tried Ubuntu 7.10 with Wubi.  It ran pretty well.  I want to upgrade to 8.10.
I only have 384 MB of ram.  What items can i turn off (remove) So that I can make it run fast on my laptop I dont mind losing eye candy. and being able to run firefox with alot of tabs open is important.

Open a terminal, and run:

sudo aptitude install xubuntu-desktop

Log out, then when you log back in at gdm select Xfce as the session.  I enjoy the desktop, its fast, responsive, and still Ubuntu.

> **333halfevil said:**
> I want to keep gnome if possible.  I like the app interfacess

Xubuntu has a gnome-like look and feel, so you'll be right at home with the interface.  Its based off alot of the same libraries and toolkits used to build gnome, so you won't be giving much, if anything, up.

---

### Post by 333halfevil on 2008-10-31
Thanks Im currenty downloading 8.10 by bittorrent. (having cheap dsl its going to take anouther 9 hours)  I will try boith solutions and pick the one that works best.  Thanks for every thing.

---

