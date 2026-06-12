---
title: "anything easier to use than unbuntu"
date: 2006-01-31
forum: Installation &amp; Upgrades
---

### Post by dude of wonders on 2006-01-31
unbuntu installs all this extra stuff on the computer that i dont need and it won't play all my video files i got it to play avi. but no wmv. The graphical interface is nice tho, just a bunch of junk on the system and nothing that i really need. so i was wondering if there was anything else like unbuntu, that doesnt install all the junk and plays the video files, and is easier to pick up on. ;) i'm probably asking for to much though lol

---

### Post by Elvish Legion on 2006-01-31
Nothing will play wmv out of the box.

You can select what you want to install with any distro

Try automatix to get wmv/dvd etc working

---

### Post by aysiu on 2006-01-31
No distribution will do what you want. I'm sorry.

There are distributions that play multimedia out of the box, but they have far more "junk" than Ubuntu has. Ubuntu, in fact, is quite slimmed down. Can you explain what you find as unnecessary in Ubuntu exactly?

If you don't mind more junk but also more immediate multimedia support, try Mepis, Linspire, or PCLinuxOS... or Blag.

---

### Post by dude of wonders on 2006-01-31
all the extra games and i'm not sure what all these other folders are but it takes about 3 gigabytes away from my hard drive and i have a small 9 gig lol, i tried going to the add and remove programs but cant seem to delete the games unless i go to advance and then it sends me to a device manager to download stuff.

where do i download automatix? 

sorry for being a newb, just dont have much harddrive space so trying to get rid of what i dont use.

---

### Post by aysiu on 2006-01-31
Again, you're at odds with yourself.
Automatix will add more crap to your installation, but you're trying to slim things down.

You can go to advanced without all those updates. Just go to System > Administration > Synaptic Package Manager. Click **Reload**. Go to **Sections** (at the bottom) and the **Games and Amusement** and mark all those packages for uninstallation.

If you really know *exactly* what packages you want, do a server install and then install only the packages you want. Then do Automatix for multimedia codecs.

---

### Post by dude of wonders on 2006-01-31
thanks i'll try doing the server install see how it goes mainly i just want to surf the web and watch videos on this system. The rest is just taking up space.

---

### Post by az on 2006-01-31
You should be able to remove as much of the junk as you want.  all the games, all the office stuff.  You are probably being told that you need updates (which you should get)  Once you remove all the stuff you don't want, you will be able to update your system and it will only update installed package.

Don't worry if it tells you it will remove the ubuntu-desktop-package.  It is there to insatll the whole enchilada and contains nothing in of itself.

As for disk space, a default basic install takes up 1.8 gigs of hard drive space plus swap.  You can make you swap smaller, if you want.  Removing a lot of stuff will bring you down a bit.  REmoving gnome and installing a smaller desktop environment (or starting over with a server install) will be more dramatic.

---

### Post by mishranurag on 2006-01-31
I have always been scared to remove the extra stuff I didn't like as Synaptic always said it will remove UBUNTU-Desktop or KUBUNTU-Desktop. What  default applications can we actually remove from UBUNTU and KUBUNTU without screwing up the system. :)

Thanks for the insight
Anurag

---

### Post by az on 2006-01-31
[QUOTE=mishranurag]I have always been scared to remove the extra stuff I didn't like as Synaptic always said it will remove UBUNTU-Desktop or KUBUNTU-Desktop. What  default applications can we actually remove from UBUNTU and KUBUNTU without screwing up the system. :)

Thanks for the insight
Anurag[/QUOTE]
Pretty much any package installed by default will take ubuntu-desktop along with it if you remove it.

Don't panic!

Really, the only use for the ubuntu-desktop metapackage is to (A) install the ubuntu desktop packages that it depends on onto a base system and (B) bring along extra packages from one release to the next.

For example, Hoary used Xpdf, but Breezy now uses Evince to read pdf files.  Had you just done a dist-upgrade from Hoary to breezy without there being an ubuntu-desktop package, nothing would have brought evince onto your system.  (I am oversimplifying because I think some other packages depend on it)

But the point is that if Ubuntu ships with some new exciting functinoalitites in the next release, you can get earlier releases to install them when upgrading by adding them to the dependancies.  Ubuntu-desktop is a metapackage that will depend on all of the other componenets of the basic ubuntu desktop.

Remove it today and forget about it until you want to upgrade to another release.

When Dapper comes out, either change your sources.list to point to Dapper and install the ubuntu-desktop package - that should be almost equivalent to a dist-upgrade.  You may need to fetch a few packages after that - you should do the dist-upgrade, too.  ut that wil ensure that you get everything.

You can also just update, and mark the ubuntu-desktop package for installation.  You will then see whan new interesting things are offered and install them only if you want to.

It is also completely fine to just dist-upgrade and not bother to see if there is anything new you want.  That should work fine, too.

---

### Post by aysiu on 2006-01-31
Just to add to Azz's already thorough explanation, this is the description from Synaptic of the ubuntu-desktop metapackage (emphasis added): > This package depends on all of the packages in the Ubuntu desktop system

[b]It is safe to remove this package if some of the desktop system
packages are not desired.[/b]  However, it is recommended that you keep
it installed, because it is used to carry out certain upgrade
transitions (such as adding new packages to the system).

---

### Post by mishranurag on 2006-02-01
Hmm!

Thanks for the explanation. I will at least remove the useless small games and rhythmbox from my system. The Amarok gives me lot more than I expected.

Anurag

---

