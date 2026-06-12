---
title: "Kubuntu being very slow."
date: 2009-07-08
forum: Hardware
---

### Post by kutagh on 2009-07-08
Well, let me start off with the specs.

I got a Toshiba Satellite A10 as my laptop (which I want to use for MSN and while I'm gaming, use it to browse the internet). Obvisiously, I got a desktop as well.

The Toshiba Satellite A10 has 256MB RAM, an integrated Intel GMA chipset, and if memory serves me correctly, an intel Celeron 2.4GHz processor. It got a 40GB IDE hard disk.

It used to come with windows XP, running that reasonably well (but not optimally). I decided to switch to Kubuntu, only to find out now that Kubuntu is actually performing worse.

Since I got an issue with the network drivers as well (I got a Sitecom wireless card slotted in, which isn't being recognised so I'd need a driver for that as well) it is a tad hard to get everything correctly as I'm running Windows 7 RC on my desktop (I'm an avid gamer, and I can't be bothered finding native Linux versions or trying to get them run in Linux.... I play too many current games for that, Overlord 2, GTA4, Velvet Assassin, Prototype, FUEL, etc etc), getting the packages isn't as easy as I'd hope it'd be.

The main issue is that the desktop (KDE4 desktop if I'm right) is responding a tad slow, and in some instances screens won't listen properly. Kubuntu states that there are no drivers available for the chipset either.


I'd like to speed up Kubuntu while keeping the KDE desktop. So I'm wondering, is it the configuration that I need to work on, or should I actually get a less demanding desktop?


Thank you in advance for reading this wall of text and trying to help me.

---

### Post by shatterblast on 2009-07-09
KDE has possibly one of the highest resource usages out of the GUIs available for the X Window server.  Also, it has some of the best software designed for its interface.  As an advantage, you can use some of your KDE programs in other environments.  Quadra Plus stands as an exception in my thoughts, but if you don't develop web pages, it shouldn't become an issue.

Gnome, the standard desktop, has potentially the most compatibility and comparable behavior.  XFCE, or the Xubuntu version, would probably suit your system the best because of its performance advantage.  I suggest making a LiveCD of Xubuntu and then access Synaptic to try a few software applications of whatever keeps you to KDE.  Clonezilla can help with back-ups of your system once you have something chosen that aids your comfortability.

---

### Post by kutagh on 2009-07-09
Thought so. 

Why I want to use KDE? For the looks. I don't need the widgets though, would I get a reasonable performance gain when disabled? The programs aren't any issue for me.

My main curiosity is why the KDE desktop is responding slower then the standard XP installation desktop (Toshiba OEM installation)...

The main usage of the laptop is just MSN (pidgin is preferred for that) and browsing websites. So if I'd install Xubuntu and use "apt-get install kubuntu-desktop" would that give me the KDE GUI while having just a minor impact on the GPU (perhaps with Widgets disabled)?

---

### Post by shatterblast on 2009-07-09
Linux tends to come more compact while the Windows OS no matter what version has many sections to it.  This is true even down to the original versions of both operating systems.  While Linux tends to set everything for your computer in a single yet smaller space, Windows will load its core while its other sections wait to jump up on demand.  This causes Linux to run efficiently, yet Windows will appear to run faster.  However if you have a lot of "start-up" items for Windows, you can notice how that efficiency compares at times.

KDE in my understanding has the closest Windows-like GUI for the X Window server when unchanged.  If you have an open mind towards trying a different GUI, settings and themes exist that can allow your computer to mimic the feel and look of other operating systems you may prefer.

Ubuntu's download system will get the dependencies necessary to run programs you may want.  It will store parts of KDE in an XFCE environment so that your program will run.  I recommend testing a favorite software before making the jump over.  Even though a software may mostly run, parts of it may refuse to work.  You should notice in a few minutes if that becomes the case since an error message usually will let you know.  Also, KDE things are easier to pick out since the majority of them begin with the letter "K".

---

