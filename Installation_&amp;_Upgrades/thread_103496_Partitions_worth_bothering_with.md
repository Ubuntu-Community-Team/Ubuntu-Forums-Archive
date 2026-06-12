---
title: "Partitions worth bothering with"
date: 2005-12-14
forum: Installation &amp; Upgrades
---

### Post by Quitch on 2005-12-14
Its been a while since I played with Linux, but I now have a second hard drive and re-built Windows, leaving enough space on both to have a Linux install of Ubuntu (after reading lots of good things about it, and since Linux is becoming less of a nightmare to use)

The thing is, I'm not sure what I should bother partitioning.  I used to have one for boot, root, usr, var and home.  I did it this way because I knew, later down the line, when securing the box I'd want to allocate certain flags to each partition... but I never got that far, I loved building the boxes too much :)

Is it worth using all those partitions?  Where does Ubuntu tend to put its various items (e.g. is a program from apt installed under /usr?).

---

### Post by Rinzwind on 2005-12-14
I don't think I can tell you how to use your partitions tho and only can tell you how I feel about my own setup.

To me(!!) as a single-user on a laptop I've not yet see any reason to go beyond a /, /swap and /home setup. And I can tell you I do use it as a database (mysql) and to play with Apache. So it's not like I just play gnome-games.

It makes it very simple too: once a setup is made and you got all your software installed, tweaked and working to your liking /home is ALL you are going to visit. 

Regarding the 2nd question: I should hope so :)

---

### Post by Topsiho on 2005-12-14
I agree with Rinzwind.

You only need a /, a /home and a swap partition.

Swap is usually set to twice the internal memory available, though if you have a lot of it then usually you need not have so much swap.

/ should be large enough for installing programs you want to use, say 4 GB or so, though Ubuntu installs in some 2 GB.

/home should be large enough for your own files and settings. Depends on what you are going to put into it, in my case I wamt to be able to download large .iso's before I burn them as images.

On a future upgrade or new install you must 1st. back up your /home and 2. NOT reformat /home, which keeps your precious files (sometimes (always?) the most precious thing in your computer system) and personal settings.

You can of course use separate partitions for /var, /usr and so on, but then you are always confronted with the problem you have to guess how large these partitions must be.

My two pennies ...

Elsewhere in this forum there are more opinions on this.

Topsiho

---

