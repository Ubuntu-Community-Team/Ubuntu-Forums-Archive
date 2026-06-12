---
title: "Ubuntu for Dummies"
date: 2006-01-18
forum: Installation &amp; Upgrades
---

### Post by marmaduke14 on 2006-01-18
Hi all,  Just signed on.  Just got done downloading Ubuntu(permanent version). I am totally new to Linux and right now I want to take a shot at Ubuntu.  I have three old computers at home I can use to set up Ubuntu on.  One has a 3DfX Voodoo 3000 video card, another has a Phoenix card, and the third has a Mx4000(Nvidia)  Will Ubuntu recognize these cards?
My biggest concern is I have no idea what to do.  I want to install to a blank hard drive.  When I boot from the CD will Ubuntu be able to format and install to the hard drive?  From other web sites, I've noticed command line parameters are used for Linux.  Where would I find info on these commands?
Are there any web sites that hold your hand and help you through installing, setting up and running Ubuntu?  I've noticed some web sites that mention having to change things (?) right after installing Ubuntu.  I haven't a clue.
Wish me luck.8-[ [-o<

---

### Post by jsmidt on 2006-01-18
The Ubuntu CD does a really good job at detecting hardware.  It probably will.  You shouldn't have to feed it command line info, it should just detect it.  Just boot up with the install cd.  Follow the instructions, they really aren't too hard.  If you can afford for your harddrive to be erased on the computer you are using Let Ubuntu do it.  

Here are some websites:

[http://archive.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/](http://archive.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/)

[https://wiki.ubuntu.com/Installation?highlight=%28install%29](https://wiki.ubuntu.com/Installation?highlight=%28install%29)

---

### Post by canadianwriterman on 2006-01-18
Welcome to Ubuntu Marmaduke. I think you will find installing Ubuntu fairly friendly. The installation is not graphical, but the options are pretty clear.

When you mentioned installing to a blank disc, do you mean that you're installing to a second hard drive and that you'll be dual booting with another operating system on the first hard disc (like Windows)? If so, when you get to the partitioning screen, just select the option that let's you take over a drive completely and select hdb, which should be your second (slave) drive. The installation will then automatically detect your other operating system and install a file called GRUB in the master boot record of your primary hard drive. When you boot your system, you'll then get a menu that allows you to choose which operating system to boot into.

As for tweaks, you MAY need to do some after the installation, when you find out what Ubuntu is detecting and what it isn't, etc. When that happens, just post here and you'll get all the help you need.

Good luck on your install!

---

### Post by marmaduke14 on 2006-01-18
When you mentioned installing to a blank disc, do you mean that you're installing to a second hard drive and that you'll be dual booting with another operating system on the first hard disc (like Windows)? 

No.  I have several hard drives laying around. I was going to erase one and boot the Ubuntu CD and hopefully install from the CD to the hard drive(Like Windows does on an initial install)  I was going to use the whole computer for Ubuntu.  No other operating system on it.

---

### Post by 504harry on 2006-01-19
[QUOTE=marmaduke14]When you mentioned installing to a blank disc, do you mean that you're installing to a second hard drive and that you'll be dual booting with another operating system on the first hard disc (like Windows)? 

No.  I have several hard drives laying around. I was going to erase one and boot the Ubuntu CD and hopefully install from the CD to the hard drive(Like Windows does on an initial install)  I was going to use the whole computer for Ubuntu.  No other operating system on it.[/QUOTE]
HI,
I think this "clean install" is a good idea (but most appear to want Windows also), I had similar needs and it isn't really 100% yet.
The first problem is making the CDdrive work, I've managed it with a FDD booter but that only worked once, recently I've tried the CD writing onto an existing Ubuntu system (I found that you need the web connected, otherwise it can't link-up....see other posters here, similar problem in small number of cases).
I tried a Gnome "Live" CD and that managed to connect to the internet, so I suspect that it needs to be there and then Ubuntu just makes the necessary files. I hace read that using the Live Distro (Ubuntu presumably) may allow the HDD to be prepared. It may be possible to make a booting disc that will recognise your CDrom and Linux.... My PC is a few years old and the CDrom does need booting.
Partitioning is a nightmare - but if you follow the words, a couple of times, you may get the basic set-up ie a small swap file of 750MB and the rest.
What is difficult to do is to split three-ways - so your "work" files are separate - I read this is a good idea - but maybe regret attempting it.
Things like USB just work, but 5.10 hasn't printed anything; 5.04 did until I updated it...perhaps I got carried away. Printing is still a nightmare. I don't use the soundcard, yet.


I'm trawling here for updates to Firefox - three will do:- RealPlayer,  Java and .PDF plug-ins.........seems very difficult, yet something that most Windows Users have done for them, with one click.
Good luck.....let us know how you get on.
Cheers. H

---

### Post by christhemonkey on 2006-01-19
For installing:
Ubuntu = great
Windoze = not quite so great
(in my experience anyway!)

---

