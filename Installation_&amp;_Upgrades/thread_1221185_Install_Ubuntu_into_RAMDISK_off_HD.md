---
title: "Install Ubuntu into RAMDISK off HD?"
date: 2009-07-23
forum: Installation &amp; Upgrades
---

### Post by jjpotter on 2009-07-23
**Goal:** Build a laptop that can be given to clients for temporary use, while they visit our facility. It would be able to connect to our public wireless and would really only need to be able to surf the internet. I would really like to be able to load into RAM everytime, that way once it is turned off/restarted, we are starting with a fresh desktop.
 
I would really like to be able to load the distro right off the HD into a RAMDISK. I wouldn't want them to be able to mount any drives or get to any terminal windows. Basically, purely a internet machine. (Maybe a calculator, paintprogram, notepad, etc...)
 
From what I have been looking at, Puppy Linux is pretty much designed for this. My only problem with it is, I feel like it is to bloated and that I would have to do a lof of modifications to it, (Remove all the fat, would rather use FireFox, etc...). If I have to go that root (pun intended) I will, but most of my linux work up to this point has been on Ubuntu and I feel more comfortable working with it. I also like the simple look and feel of the desktop (Puppy linux desktop is a mess!).
 
I guess some of the road blocks would be, could I get ubuntu slim enough to fit into 512mb - 1gb or RAM? Could it even be loaded into a RAMDISK off a HD and would it be worth the trouble? Could I prevent users from getting to a shell and installing apps and doing ports scans and all that great stuff we love linux for?
 
The journey begins...

---

### Post by TheNosh on 2009-07-23
ubuntu is to large for most PCs to load to ram, Puppy as you said is perfect for this purpose though (or maybe damn small linux, feather linux, or slax)

main point is, you want something small and Ubuntu is NOT it. not even with xfce, any of the box managers or lxde

but if you go with puppy you will need to modify it some if you want to restrict certain things, if i recall propperly (i haven't touched my Puppy installation in almost a year) puppy, by default, makes the user root. i think the rationalization for that was something about how it resets anyway with every boot, so you couldn't really screw things up permanently (though they ought to have changed that by default for save files and full installs)

as for damn small linux, feather linux, and slax; i'm not really fermiliar with them much, when i need something lightweight, i always go for puppy, or one of it's puplets (the puppy equivelent to remixes in ubuntu)

---

### Post by Omniman on 2009-09-05
Well i got 8 gig of ram, and would like the possibility to use 4gig for Ubuntu.

run OS from ramdisk and when PC is turned off, write changes to a image on hd that reloads back to ramdisk on bootup!

is this possible?

---

### Post by ethanep on 2010-07-09
I've been trying to do this for a while now. I have a 12gb of Ram.

My system would be for personal use only and I'm hoping to set up two boot options at grub, one for ramdisk and one for standard mode. If I boot standard, I can modify the os and install applications. If I boot into RAM, the / partition would be copied into a ramdisk and run from there. The /home partition would remain on the disk although I might later want to cache some of the settings from there into ram disk. This would allow me to use ubuntu from a ram disk and not worry about breaking it, it would be much faster, and I could still install updates easily.

I don't really know how to do this, but the closest i've come is with this tutorial [http://ubuntuforums.org/showthread.php?t=707230](http://ubuntuforums.org/showthread.php?t=707230)

This uses squashfs, which i'm not very familiar with but the concept is that it's squashed before loading into ram. This might be good if you don't have enough, but i've found that it's very glitchy because it's a read only filesystem and a lot of things don't work. Good luck! I'll let you know if I find any more resources.

---

