---
title: "Never have successfully installed Gentoo"
date: 2008-10-01
forum: Gentoo and derivatives
---

### Post by dodle on 2008-10-01
Every time that I try to install Gentoo, at the end of the installation, it tells me that the installation has failed.  I think I have tried on at least three different systems.  I had wanted to try out Gentoo for a while.  Does anybody else have similar experiences with Gentoo?

---

### Post by trimeta on 2008-10-01
Are you using the graphical installer? It's generally recommended that you not use that, and instead go through the command-line install method. You can still use the graphical LiveCD, of course, but instead of clicking on the Install link, just launch a terminal window and go forward with the instructions in the Install Handbook.

---

### Post by dodle on 2008-10-01
Yes I have only tried using the graphical installer.  The next time I get the opportunity to install it, I will try the command line.  I assume this is something that the Gentoo team has been working on fixing.  Do I assume wrong?

---

### Post by Bachstelze on 2008-10-01
> **dodle said:**
> I assume this is something that the Gentoo team has been working on fixing.  Do I assume wrong?

The GUI installer? I wouldn't be so sure about that, since it has always been like that. I think its only use is for networkless instllations.

---

### Post by RedSquirrel on 2008-10-03
> **dodle said:**
> Yes I have only tried using the graphical installer.  The next time I get the opportunity to install it, I will try the command line.  I assume this is something that the Gentoo team has been working on fixing.  Do I assume wrong?

The emphasis for the future will be on the Minimal CD and up to date stage3 tarballs. See the second News item [here]("http://www.gentoo.org/").

You will have a better chance of a successful Gentoo installation if you follow the Handbook as suggested above by trimeta.

---

### Post by crimesaucer on 2008-10-04
I gave it one real try (2 real attempts.... one of the times was with the installer where I screwed it up and knew that I had done it wrong.... the other was with the stage3 tarball where I'm pretty sure I followed every direction correctly so I don't know why it failed?)..... I basically spent 2.5 days, and about a week of pre-install studying..... and in the end it failed at the grub menu.


I gave up for now, I will give it another serious try when I get a permanent residence where I can spend the proper time with it to keep installing it until I get things correct.

---

### Post by ippokratis on 2008-10-11
> **dodle said:**
> Every time that I try to install Gentoo, at the end of the installation, it tells me that the installation has failed.  I think I have tried on at least three different systems.  I had wanted to try out Gentoo for a while.  Does anybody else have similar experiences with Gentoo?

I had the same problem, both for 2007 and 2008 versions!  I used the graphical installer.  But I can't understand the existence of the installer if it doesn't works!  Anyway, after 10-12 failures (!), I have now installed the 2007 version in my PC and I'm proud of it!  :popcorn:

---

### Post by trimeta on 2008-10-11
> **ippokratis said:**
> But I can't understand the existence of the installer if it doesn't works!

I think some people complained that Gentoo couldn't be a "real" distro if it didn't have an installer. But since all the major Gentoo devs think the manual install is the "proper" way to install Gentoo, the installer has never really gotten much work on it. Anyway, if I understand their new release strategy, they're basically going to stop development on the installer. So yea, I highly advise against using it, and instead recommend using the manual install (from whatever LiveCD you want, you can still use the graphical LiveCD as long as you open up a terminal and do the manual install).

---

### Post by regomodo on 2008-10-17
If you are using the 2008.0 Graphical installer change to the 2008.1. There's a bug in either compiling the kernel or extracting something iirc.

I'm glad they dropped the development for this exercise of development time-wasting. I've noticed a lot of stable ebuilds coming through portage of late.

---

### Post by Crooksey on 2008-10-19
I used it when it was first released as a test exercise, took ages!

Where as a minimal install and a kernel build, takes me about an hour.

---

### Post by Ender305 on 2008-11-08
I've done two successful installs, on both I used Sysrescd([http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)) and a funtoo stage3 tarball(the funtoo.org tarballs are compiled for more architectures.) 
It takes a long time to get a fully operational system, but you're proud when you're done. :-)

---

### Post by bwhite82 on 2008-11-09
I am currently installing a Gentoo system in Virtualbox. I have no doubt that I'll be successful. I'm using a miminal CD and stage3 tarball. I am cheating though and using a default kernel (made with genkernel). I've NEVER been successful at compiling my own kernel without borrowing an existing kernel config.

---

### Post by regomodo on 2008-11-10
> **Soldierboy said:**
> I am currently installing a Gentoo system in Virtualbox. I have no doubt that I'll be successful. I'm using a miminal CD and stage3 tarball. I am cheating though and using a default kernel (made with genkernel). I've NEVER been successful at compiling my own kernel without borrowing an existing kernel config.

Good idea. It is what I did initially and for my laptop and PC. Unfortunately, they boot considerably slower using genkernel(initrd) instead of using a single image/file. Additionally, i cannot get dmraid to work using the non-genkernel method.

---

