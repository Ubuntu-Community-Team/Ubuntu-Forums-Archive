---
title: "Yet another Ati card question.."
date: 2010-10-04
forum: Hardware
---

### Post by Martificiam on 2010-10-04
As most of us know, ATI has cut support for drivers since Ubuntu 8. That means that for Ubuntu 10 people like me need to use the open source drivers. Well, my pc starts freezing/langing terribly after some time of use and I need to restart the pc, soooo I was wondering if there's a way I could install Ubuntu 8 video drivers on my Ubuntu 10.04 system? Because when I was testing Ubuntu 8, it was working perfectly.

---

### Post by coffeecat on 2010-10-04
> **Martificiam said:**
> As most of us know, ATI has cut support for drivers since Ubuntu 8.

Eh! :-k

I think you mean that ATI has dropped support for some legacy chipsets from the later versions of their proprietary drivers. This is very similar to what nvidia has done with some of their legacy chipsets.

> **Martificiam said:**
> I was wondering if there's a way I could install Ubuntu 8 video drivers on my Ubuntu 10.04 system? Because when I was testing Ubuntu 8, it was working perfectly.

I don't believe that is possible because 10.04 uses a later version of the xserver and the proprietary drivers are made to be compatible with  specific versions of the xserver.

What ATI chipset do you have?

---

### Post by Martificiam on 2010-10-04
Ati radeon xpress 200M.

WHat should I do in order to get rid of the random freeze-ups?

---

### Post by coffeecat on 2010-10-04
I presume you get the freeze-ups with the proprietary fglrx driver. According to this page:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

... you should be able to get good 3D acceleration with your card and the open source driver. Your first post suggests that you don't like the open source driver. Is that true? And have you actually tried the open source driver in 10.04? It has improved very much since 8.04. If you haven't tried it in 10.04, you might find that it's better than you expected.

I use the open source driver in both 10.04 and 10.10 for both my Radeon Mobility HD4200 (laptop) and Radeon HD4350 (desktop) cards. I get 3D acceleration sufficient for the compiz effects I want. I am not a gamer, so I cannot say whether it's good enough for gaming.

---

### Post by Mark Phelps on 2010-10-05
I would be VERY SURPRISED if you were running the proprietary AMD/ATI driver with that video card in Ubuntu v10x.

To see, open a terminal and enter "sudo fglrxinfo".  You should get an error indicating that flgrxinfo can not be found.  IF you do, that means (as I suspect) that you are running the open-source drivers.

---

### Post by Martificiam on 2010-10-08
Yes, I've tried the open source drivers, but still, this is what's happening: [http://ubuntuforums.org/showthread.php?p=9940712#post9940712](http://ubuntuforums.org/showthread.php?p=9940712#post9940712)

---

