---
title: "Adept problem"
date: 2005-12-01
forum: General Help
---

### Post by Optiker on 2005-12-01
Someplace along the line in trying to install a gstreamer package to accommodate mp3 files, I must have glitched my adept installation. I am running Kubuntu 5.10.

When I run adept, I get an error dialog box with a title bar...

"Could not open cache-Adept"

The dialog box content says...

"The APT Database could not be opened! This may be caused by incorrect APT configuration or something similar. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem."

When I run sudo apt-setup, I get a Ubuntu configuration utility.

First screen: method to access archive, default is http - ACCEPT
Second screen: Country, default is United States - ACCEPT

This runs some stuff and gives the following output to the console...
-----------------
Testing apt sources...
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Fetched 1B in 0s (1B/s)
Reading package lists... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources [232kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Fetched 232kB in 1s (197kB/s)
Reading package lists... Done

[blank lines deleted]

     release v=5.10,o=Ubuntu,a=breezy,l=Ubuntu,c=restricted
     release v=5.10,o=Ubuntu,a=breezy,l=Ubuntu,c=main
-----------------------
Running Adept at this tme gets the same error dialog.

Running sudo apt-get gets me a screenfull of help lines for apt-get, but I don't know how to use it, so don't know what to do with it.

How do I fix it so I can get back to the GUI Adept for package management? Should I just clear the partitioon and start over with a fresh installation and hope it works?

Thanks!
Optiker

---

### Post by starfire1983 on 2005-12-04
I've been getting the same problem recently and I've tried reinstalling apt and dpkg but with no luck.

---

### Post by axel_2078 on 2005-12-05
If adept is your only problem, I would just dump it in favor of a different package manager such as synaptic or Kpackage.  sudo apt-get install synaptic

---

### Post by Optiker on 2005-12-05
Axel...call me stubborn!  :)

I was just getting accustomed to Adept, and liking it. I'm a relative novice to Linux, and one of my concerns was how to install new apps - I guess I'm a freeware junkie, so enjoy trying new apps. Adept was easy to learn, and easy to use for me, so I hesitate throwing it out and starting with something new.

In any case, it was working great prior to that one oincident - and still is working just fine on my home computer - so it's a little hard to believe that it's something intrinsic.

I guess I'll hold out for a better solution for now.

Thanks!
Optiker

---

### Post by veloct on 2005-12-05
I may give Kpackage a try.  Synaptic runs better under Gnome and Adept is not mature enough for use (IMO). :)

---

