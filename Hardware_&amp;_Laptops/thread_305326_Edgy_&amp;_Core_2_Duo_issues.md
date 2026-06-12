---
title: "Edgy &amp; Core 2 Duo issues"
date: 2006-11-23
forum: Hardware &amp; Laptops
---

### Post by sergestusx on 2006-11-23
Hello there!

I own a Dell Inspiron 6400 Core 2 Duo T5500 /ATi X1400 laptop. I installed Edgy yesterday in its 64bit version, but it didn't seem to want to boot up in Live-CD mode. So I tried i386 version, and it installed OK. Is there any problem with Edgy & the Core 2 Duo processor? :-k 

My question is about a pair of issues. One is how do I configure my graphics card? I'm newbie with linux, so I'm not familiar with installing packages and stuff. Secondly, how do I make it to detect the dual core? I've read out there that I have to get a compatible kernel, but don't know where nor how to do it. And third, how do I make it detect my wifi card correctly? It's an Intel Proset Wireless for Core 2 Duo.

Thanx for any help!  :-k :-k :-k

---

### Post by Levander on 2006-11-23
There are no problems with Edgy and Core 2 Duo.  The problems are with Linux and 64 bit installs.  I don't know of a distro that has a really smooth 64 bit install.  32 bit is just as fast for the vast majority of applications.  In the future (years), it will be a compatibility issue where if you don't have a 64 bit processor, a lot of software won't run.  We're not there yet.

You're graphics card will be configured during the Ubuntu install.  It also should have been configured during the LiveCD boot process (although with the LiveCD, it will have to be configured every time you boot off it - system configuration isn't written down when using the LiveCD, so it can be run off a read-only filesystem, like a read-only CD ROM).  If it wasn't post back and try to get more help.  After install, you can reconfigure it with 'dpkg-reconfigure xserver-xorg'.  This is configuring X-windows to know about your graphics card, because X-windows is what talks to your graphics card in "GUI mode" in Linux.

What I've heard is that the default kernels now support SMP (SMP is dual CPU's).  It used to be that Ubuntu named packages that had an SMP kernel with the string 'smp' in the name of the package.  But, SMP is more common now, and they are just putting it in the default kernels.

Wifi cards are commonly difficult to get configured in Linux.  I've never done it.  Maybe someone else can help?

---

