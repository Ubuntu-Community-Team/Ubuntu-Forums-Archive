---
title: "[SOLVED] leaner install"
date: 2008-11-07
forum: General Help
---

### Post by labud on 2008-11-07
Asus P5KC core2duo 3.6  3.0 g ram Gnome/KDE 8.04.1
BioStar P4M80-M4  2.4gHz  2.0g ram  KDE/XFCE 7.10


I have been using Ubuntu [ Ubuntu, Kubuntu, Xubuntu 7.10 & 8.04.1] for abount 6 months. which I realize is a very short time and still feel I have megatonnes to learn.  IMHO 7.10 in some ways is the better[more stable]  One thing I am not happy with is the amount of software [unneeded to me] that is installed with CD.s.  I understand why it is done that way [I think], but I would like to know if there is a way to install K/X/Ubuntu with only the software that I want [I am going to call Myself a minimalist.]  To install a base system with internet connection, a base KDE desktop, and then just the software that I want. [Some [software]Gnome based, some KDE]
I like the KDE desktop but as long as We can have drag and drop it isn't necessary.
Anyway, I am enjoying this new [to me] OS and hopefully with suggestions, I can get it working to my liking.

---

### Post by Idefix82 on 2008-11-07
Maybe this is what you are looking for: [https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")

---

### Post by labud on 2008-11-10
From: [COLOR="Navy"]https://help.ubuntu.com/community/Installation/MinimalCD[/COLOR]

"[COLOR="Gray"]The Minimal CD downloads packages from online archives at installation time instead of providing them on the install CD itself. Downloading packages at install time reduces the size of the install CD to approximately 5 to 20MB depending on architecture (see below),[/COLOR] 
[COLOR="Red"]**_as well as providing only the packages needed for installation_**[/COLOR]"

The line in red, I believe, is the one I want to know about.  I certainly don't need download pkgs at install time.  Where would I find out what "[COLOR="Green"]only the packages needed for install[/COLOR]" are?

---

### Post by Yashiro on 2008-11-10
[Installation using the Alternate CD](https://help.ubuntu.com/community/Installation/#Installation%20using%20the%20Alternate%20CD)
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

then

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by labud on 2008-11-16
i have gone ahead and done this minimal install after reading about it, but something seems to have gone awry.  Things are up and running but i have done something wrong in my partitioning the hard drives.

I have 3 hard drives: 
1] sda  has 3 partitions  root, swap, home
2] sdb  has 1 partition  music storage
3] sdc  [B][COLOR="Blue"]was supposed to be extra storage, but it has some essential [I    think] files in it that are supposed to be in my /home? directory.
the files are named:bin, games, include, lib, local, lost&found, sbin, share, src, X11R6[/COLOR][/B]      

Is there any way to change this and put these files where they are supposed to be?

---

