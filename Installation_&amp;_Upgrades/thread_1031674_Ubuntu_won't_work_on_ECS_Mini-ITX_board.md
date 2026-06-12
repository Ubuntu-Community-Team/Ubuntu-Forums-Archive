---
title: "Ubuntu won't work on ECS Mini-ITX board"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by Z.K. on 2009-01-05
I was intending to use the ubuntu 8.10 server on a ECS Mini-ITX system that I just bought and I have been having some problems.  I get it to install including the XWindows, but then the whole system locks up and I can't move the mouse or press any keys on the keyboard.  This happens after using the system for about five minutes.  I was at first even unable to install it as I was getting errors about kernel features par and cx8 not present for my cpu so I installed the generic kernel and that seemed to work until I boot into XWindows and after five minutes, the system would lock up.  

I even tried the desktop version of Ubuntu 8.10 and 8.04 with the same result as to locking up.  I was thinking it might be a graphics issue, but then I tried a couple of different Linux distributions such as Fedora and they worked just fine.  Anyone have any ideas or suggestions.  I will probably use Fedora or Centos 5.2 at least for the time being.  

My newer machine works fine with Ubuntu.

---

### Post by tulchan on 2009-01-05
For info, I've just installed Ubuntu 8.10 on an EPIA-CN board - works fine

---

### Post by grognut on 2009-01-06
I've installed 6.06 on a mini-itx EPIA 500Mhz. It would not boot afterwards. I had to use the alternate install disc for it to work. I can't remember what the errors were or what was special about the alternate CD.

Hope it helps 

grognut

---

### Post by Z.K. on 2009-01-12
> **grognut said:**
> I've installed 6.06 on a mini-itx EPIA 500Mhz. It would not boot afterwards. I had to use the alternate install disc for it to work. I can't remember what the errors were or what was special about the alternate CD.

Hope it helps 

grognut

Well I tried it again with the alternate CD for 8.10 Server and I get the same message as before:

   This Kernel requires the following features not present on the cpu: pae, cx8

I can install the software, but when I reboot and select the kernel from grub, Ubuntu Server will not even boot and displays this message right away.  I know from before that it will kind of work if I install the generic kernel, but it causes intermittent problems such as lockups.  I suppose it might work if I go back to older version, but I would like to stay current.
I guess I will just have to use Fedora which is too bad as I really like Ubuntu and the support it offers.

---

### Post by grognut on 2009-01-12
Hi Z.K.

After reading your comments it reminds me that that was the same problem that I had with the standard CD but the alternate one cured it.
I don't know any more than that.

I know how you feel about having to change distribution, I'm trying to get apache, asp.net2, mono2 mysql-connector and php working together after doing a dist-upgrade from 6.06.1 to 8.04.
As much as I like ubuntu, if it doesnt work I'll install opensuse as mono is from the same house.

Cheers

grognut

---

