---
title: "Getting KDE for Ubuntu"
date: 2005-12-18
forum: Installation &amp; Upgrades
---

### Post by serratemplar on 2005-12-18
Rather than reinstall with Kubuntu (as I've just settled in on my Ubuntu system), I wanted to go the manual route about switching from gnome over to KDE.  I've made a sad guess that my menus will not port over to KDE.  If this is true, I'd like any advice or information people might have on perhaps manually packing and porting over my menus, or perhaps an organized way to note all of the programs I'll have to manually write to my new KDE menu.

Thanks for your time.

---

### Post by Vorian on 2005-12-18
you can #sudo apt-get install kubuntu-desktop

You will have all your files +all kde apps.

---

### Post by varunus on 2005-12-18
Actually, its probably better to use synaptic and install the "kubuntu-desktop" package.  Then, follow aysiu's howto in the "Customization tips and tricks" section of the forum on how to remove GNOME, if you want, or you can leave it.

Believe it or not, KDE and GNOME use the same menu system.  All of your stuff will stay.

---

### Post by Vorian on 2005-12-18
[QUOTE=varunus]Actually, its probably better to use synaptic and install the "kubuntu-desktop" package.  Then, follow aysiu's howto in the "Customization tips and tricks" section of the forum on how to remove GNOME, if you want, or you can leave it.

Believe it or not, KDE and GNOME use the same menu system.  All of your stuff will stay.[/QUOTE]


My bad, i meant ....install kubuntu-desktop :oops:

---

### Post by Topsiho on 2005-12-18
I did this both ways on two different computers, and both methods worked great.

The first method, with synaptic, is a bit tedious, marking the many kde packages to install, but is the most flexible in that you can choose what you want and what not.

The second, using sudo apt-get install kubuntu-desktop, is the easiest, and you are sure that the necessary packages are installed. After that you still can use synaptic to see what is not yet installed that you want installed, and mark that to install.

You do not need to throw out Gnome, of course, when booting, or after logging out, you can choose what session (KDE or Gnome) you want (next) and what kind of session you want to be the standard one.

The menus in both KDE and Gnome are similar, each with the applications of the other desktop included.
(it is even possible to install single KDE applications (and their dependencies) in just Gnome, as I did for a while with kstars, a KDE application that I really want in any Linux install).

For some actions Gnome is easier to use, for others it is KDE. Nice thing is you can play with both and discover this for yourself.

Topsiho

---

### Post by Masteroc on 2005-12-18
is there any disavantage to just using kubuntu instead of using ubuntu then downloading the kde packages. Will you get the same thing either way?

---

### Post by Vorian on 2005-12-20
[QUOTE=Masteroc]is there any disavantage to just using kubuntu instead of using ubuntu then downloading the kde packages. Will you get the same thing either way?[/QUOTE]

If you install the kde packages, you keep gnome and gain kde.  You have the choice when you log in which desk top environment you want to use.  Another advantage to installing kde is you get access to kde programs in gnome and vice versa.  I like to go back and forth...  but to each their own:KS

---

### Post by varunus on 2005-12-21
The only disadvantage to installing KDE from GNOME is that you have to download KDE.

Some people with slower internet connections who have already decided that they want KDE don't want to have to download GNOME (the CD) and then KDE (inside GNOME), so they can get the Kubuntu CD to start with KDE.  Similarly, people who want to start with GNOME can get the Ubuntu CD.

There is no disadvantage to installing the desktop environment(s) later.

---

### Post by rcrcomputing on 2005-12-21
I just d/l the 5.10.  I'd like to add kde. 
The wikie stuff say's add the "hoary" repository to do this. Is this still true with 5.10?

Umm,, I was going to post the link, but just noticed gnome doesn't seem to have my trusty little clipboard manager.  :(

BTW, I let the cd re-size the drive etc..   Seems to have worked out wonderfully!!!

---

### Post by rlsuth on 2005-12-22
Message deleted, please ignore

---

### Post by Sutekh on 2005-12-22
[QUOTE=rcrcomputing]I just d/l the 5.10.  I'd like to add kde. 
The wikie stuff say's add the "hoary" repository to do this. Is this still true with 5.10?
[/QUOTE]
No.  If you are using 5.10 the Breezy Badger, then if you ever see 'hoary' in a sources list replace it with 'breezy'.

---

### Post by varunus on 2005-12-23
To add KDE in breezy:

Open up the Ubuntu Help from your GNOME panel, click "starter guide", and go to "installing applications" on the left.  Then, follow the instructions to add universe, multiverse, and backports.  This is not necessary, but its a good idea to do so that you'll get the newest versions of everything you need.

Then, install the package "kubuntu-desktop" from Synaptic.

That's all there is to it; you can then choose KDE from the login manager.

Also, if you just want klipper, the KDE clipboard manager, you can install it separately from synaptic.  It works just fine in GNOME (though it'll look a little weird, since it'll use a KDE theme and GNOME will use a GNOME theme).  There's a howto on these forums somewhere on how to make QT and KDE applications look good in GNOME...you may want to check it out.

---

