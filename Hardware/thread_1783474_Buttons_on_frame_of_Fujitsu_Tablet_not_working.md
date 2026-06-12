---
title: "Buttons on frame of Fujitsu Tablet not working"
date: 2011-06-15
forum: Hardware
---

### Post by PlaceboMessiah on 2011-06-15
I have a Fujitsu Stylistic ST6012 running Natty

So far I haven't found any way to coax the buttons around the frame to actually register as buttons.

I'm not a total noob with linux, but I only use the terminal when instructed to do so

---

### Post by Favux on 2011-06-15
Most folks install the fjbtndrv.  It gives you the bezel buttons and automatic rotation.  They've been using Robert Grelach's PPA:  [https://launchpad.net/~khnz/+archive/ppa?](https://launchpad.net/~khnz/+archive/ppa?) but I'm not sure he has a Natty version out yet.

You could check the sourceforge site:  [http://sourceforge.net/projects/fjbtndrv/](http://sourceforge.net/projects/fjbtndrv/)

---

### Post by PlaceboMessiah on 2011-06-16
oh sweet!

now I just have to figure out how to install it

---

### Post by PlaceboMessiah on 2011-06-16
But seriously though

would anyone here be inclined to walk me through the installation process?

I installed the ppa in question, and I guess I expected the software to be searchable in Synaptic 

feeling pretty dumb right about now

---

### Post by PlaceboMessiah on 2011-06-17
anyone feeling especially nerdy on a friday night?

---

### Post by Favux on 2011-06-17
Does the PPA's Natty filter included fjbtndrv?  I don't think it did, so when you enabled it it wouldn't have pulled fjbtndrv, it would have pulled the other thing.  You could monitor the site for a Natty update or ask Robert.

That's why I mentioned the SourceForge site for the source code.  You may need to compile it or whatever yourself.  Plus it might need some changes to work in Natty.

I'm guessing it needs changes.  That's probably why it isn't available yet.  You could google and see if anyone has updated it for Natty's 2.6.38 kernel and 1.10 X server so it works.

---

### Post by PlaceboMessiah on 2011-06-17
i have the source too, but even that "dings" thing didnt show up in synaptic.

eta oh it has some build issue

---

