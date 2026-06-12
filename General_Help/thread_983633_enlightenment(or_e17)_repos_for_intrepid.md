---
title: "enlightenment(or e17) repos for intrepid"
date: 2008-11-15
forum: General Help
---

### Post by christoforever on 2008-11-15
anyone know of any e17 repos for intrepid. I've looking and cant seem to find any.

---

### Post by christoforever on 2008-11-20
So i've been looking everywhere for enlightenment DR 17 repos for intrepid and cant seem to find them. The only thing I did come across was these guys putting out a version of ubuntu with e17 as the default. They put out their own distro and build all the e17 source themselves and include it in their version... but no repos. Anyway here is the link in case anyone wants to try it out or use it.... [http://opengeu.intilinux.com/Home.html](http://opengeu.intilinux.com/Home.html)

---

### Post by christoforever on 2008-11-20
Found an e17 repo .... sort of. I've tried the directions in this link, and though they are outdated they do work for intrepid...[http://ubuntuforums.org/showthread.php?t=916690&highlight=how+to%3A+e17](http://ubuntuforums.org/showthread.php?t=916690&highlight=how+to%3A+e17)

it basically does download of source code and building and installing of e17 for you ... its actually great. The only thing is my wifi no longer works when running enlightenment desktop.. but im sure i will find a fix.

---

### Post by cunnilinux on 2008-11-23
i still use e17 from e17.dunnewind.net repo.
the latest available build is for hardy, but everything (except for entrance) installs & works just fine.
entrance does not work even though i have required libs that are no longer available in intrepid.
hope this helps.

---

### Post by cunnilinux on 2008-11-23
/* double post. sorry. */

---

### Post by tjwoosta on 2008-11-26
i have been running Elive for a while now as my main OS because i love enlightenment


im just curious, how is it working out for you in Ubuntu?

are there any issues that you have run into?

can you easily switch back and forth between GNOME and E17?


the reason i ask is because if its not too much trouble i would like to re-install Ubuntu, this time with E17 and GNOME, (so i can switch if i want to)

---

### Post by Tux Aubrey on 2008-11-26
There are several methods to get an e17 desktop on Ubuntu.

1. The latest .deb packages (which say they are at 16.999.05, the same as the latest eLive version) are available by following the instructions at [http://xsm.alphagemini.org/E17/repository/](http://xsm.alphagemini.org/E17/repository/)

I have done this on Ubuntu Hardy Heron but it wasn't as straightforward as it looks - quite a bit of tweaking of particular Ubuntu packages was required to make it work.  Once it did, it was fine.  This is as up to date as you will get with .deb packages and (I think) both OpenGeu and Maryan use the same build.  I'm pretty sure that OpenGeu has a number of alternative desktops installed, but can't remember if Gnome is one of them.

If the past is any guide to the future, the next build should be available for debian-based distros around the end of President Obama's first term in office.

2. Build it yourself from source code.  This is actually a lot easier than it sounds (and, in my experience, easier than 1. above).  Check out this thread: [Rui Pais Amazing Guide to Building e17 from Source]("http://ubuntuforums.org/showthread.php?t=916690&highlight=how+to%3A+e17").  If you have heard of the "Morlenxus Script" (that's how a lot of e-developers get their code and keep it updated, Rui's script (e17_svn) is like that but for users who don't want all the old and redundant stuff - or the highly experimental, highly breakable stuff either.  It also has some "failsafe" devices to stop bad code from being compiled.  

Since Rui made the post linked above, several people have got together and expanded the offerings related specifically to e17 done that way.  We call it "[OzOS]("http://cafelinux.org/OzOs/")" - and the packages are available individually (for debian/ubuntu systems) or as a prepacked e17 version of Xubuntu (but lighter).

If you want the gnome desktop as well as e17, it would be best to install Ubuntu (8.04.1 or 8.10) first and then use Rui's post or my How-To ([from here]("http://cafelinux.org/OzOs/content/how-install-ozos-desktop-existing-os")).

The e17_svn and oz-desktop scripts and packages (like e17 code) are "rolling releases" but once installed updates are manual - ie. you don't have to do them at all.

(Rui has also packaged a "cut-down" version of the Gnome desktop that can be installed over OzOS.  It is in the OzOS (cafelinux) repos)

As you are already using e17, I don't think you would find the jump to using the svn version a big problem. (But I'm incredibly biased!) I don't recommend it for absolute linux newbies because coming to grips with e17 can be hard enough without simultaneously being challenged by a different method of installing and updating your system.

3.) The positively worst way to install enlightenment onto Ubuntu is from the Ubuntu repos.  That version dates to December 2004 and does not work with anything (themes, modules etc) built in the last two years. (Unless someone has changed it for Intrepid.)

Which ever way you go - enjoy!

---

### Post by amrlima on 2008-12-11
> **Tux Aubrey said:**
> There are several methods to get an e17 desktop on Ubuntu.

1. The latest .deb packages (which say they are at 16.999.05, the same as the latest eLive version) are available by following the instructions at [http://xsm.alphagemini.org/E17/repository/](http://xsm.alphagemini.org/E17/repository/)

I have done this on Ubuntu Hardy Heron but it wasn't as straightforward as it looks - quite a bit of tweaking of particular Ubuntu packages was required to make it work.  Once it did, it was fine.

I tryed to install E17 from this repository but I always get an SEGV crash at startup and get all modules unloaded. I removed it all and tried Rui Pais script but i get the same crash. What did you do to make it work? did it also crashed for you? I'm running intrepid.

Thanks!!

---

### Post by Tux Aubrey on 2008-12-11
> I tryed to install E17 from this repository but I always get an SEGV crash at startup and get all modules unloaded. I removed it all and tried Rui Pais script but i get the same crash. What did you do to make it work? did it also crashed for you? I'm running intrepid.

Thanks!! 

Installing the whole thing from the Debian Experimental repos is not possible - you have to do it without any modules first (resolving conflicting packages along the way) and then install the modules one by one (but not all of them - just the essentials.  IMO, it is more trouble than it is worth!

I'm surprised you got a Seg Fault doing it Rui's way - I only get that when I REALLY mess with something fundamental!  The problem could be that some config or other files got left behind from the Debian version (in particular, you should delete any ~/.e directory before you try again).  One of the good things about Rui's way is that unstable or unsupported modules are not installed.

Because the svn version gets installed in /opt (rather than /usr/share) it needs different config files.  But in my experience it is by far the most stable e17 around - particularly if you get familiar with the backup and restore tools. 
:p

BTW, the past couple of days have been very bad at the e17 svn - I haven't had a workable update since about Tuesday.  You can check the svn alerts thread at [http://www.cafelinux.org/forum/](http://www.cafelinux.org/forum/) to see when it is possible to install from svn. (Rui's update script now polls that thread before getting an update and warns you if breakage is likely).

---

### Post by amrlima on 2008-12-12
> **Tux Aubrey said:**
> 
I'm surprised you got a Seg Fault doing it Rui's way - I only get that when I REALLY mess with something fundamental!  The problem could be that some config or other files got left behind from the Debian version (in particular, you should delete any ~/.e directory before you try again).  One of the good things about Rui's way is that unstable or unsupported modules are not installed.


I've removed ~/.e directory but still get the same seg fault. I've tryed to reinstall from debian unstable and then purge all the libs and installed with the script again... and still he same problem. 

I realy can't figure it out. I guess if some day I want e17 on this laptop I'll have to reinstall Ubuntu, and that I really wanted to skip :)

---

### Post by Rui Pais on 2009-01-04
> **amrlima said:**
> I've removed ~/.e directory but still get the same seg fault. I've tryed to reinstall from debian unstable and then purge all the libs and installed with the script again... and still he same problem. 

I realy can't figure it out. I guess if some day I want e17 on this laptop I'll have to reinstall Ubuntu, and that I really wanted to skip :)

Sorry amrlima, i've been pretty occupied lately, and this thread completely failed my attention :(

Have you solved your issues by now? Do you still want help?
Rui

---

