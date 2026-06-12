---
title: "Driver for an old ATI."
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by ErusGuleilmus on 2007-04-25
Where can I find a driver for ATI's old Rage Pro 128? It would also be convenient if you could provide some tips on installing drivers. I'm a Linux n00b and am not very savy with this OS. From the instructions for installing other ATI cards so far, it seems rather complicated. Thanks!

---

### Post by BoneKracker on 2007-04-25
It's called r128

---

### Post by ErusGuleilmus on 2007-04-25
Thanks, but that doesn't help any.

---

### Post by BoneKracker on 2007-04-25
Did you try searching the software repository for r128?  Or the forums?  Or ATI's site?  Or google?

---

### Post by ErusGuleilmus on 2007-04-25
Yes, I did try Google, but all I got was a bunch of really old websites that confused me to no end. And I'm not sure how to access the software depository.

---

### Post by BoneKracker on 2007-04-25
Oh, sorry.

You probably should read some of the ubuntu documentation about how to do some basic stuff before you start trying to optimize your system.

First, I'm assuming it's up and running.  And I'm assuming your using Ubuntu (not Kubuntu or Xubuntu, etc.).

There are some good links under the menus that lead to some basic documentation that describe, among other things how to install software.  It's much easier in Linux. All the software you will probably ever need is waiting for you in one place, ready to install by clicking on it.  You can also probably find a few good posts in these forums that are labelled "Sticky" that give good tips for new users.  You're in a different world here with Linux and it's worth reading a bit to avoid some frustration.  It's not Windows.  Not worse, just different, and in many ways better.

You should read up a bit first, but there are several ways to access the software:

1. There is an add/remove menu under the main menu.  That's for basic applications and it's pretty self-explanatory.

2. There is a more advanced tool called Synaptic Package Manager under the system menu, under adminstration I believe.  This gives you more power and it also lets you look for packages that are not official ubuntu packages (like drivers produced by a graphics card company).  First, you will have to set an option in there that lets you look at the optional software repositories.  This is described in the material about installing software.

3.  You can also use commands at the terminal, but you can do most things you'll need in 1 or 2.

Also, if you are on ubuntu 7.04 (the new version), there is now the "Non-Free Drivers Manager" or whatever it's called, also under the menus.  This will install some of these special drivers that come directly from the companies, but I have no idea if the ATI r128 driver is one of them.  You should probably check that first.
After you read up that is.  :) 

Also, the open source driver that should be installed automatically will work just fine with the Rage128 Pro.  That driver is called "ati".  It won't give you 3-d acceleration though.

You can check which driver is currently installed by looking at the file /etc/X11/xorg.conf.  It should be in a section titled "Section Device".

---

### Post by ErusGuleilmus on 2007-04-25
Ok, thanks. I was asking because I cant get Beryl to work.

---

### Post by ErusGuleilmus on 2007-04-25
I tried Synaptic, and was told the driver for the r128 was already installed. It did note that it can use Direct 3D and suggested the "fglrx" driver. Searched synaptic and found it. Didn't list the r128 but downloaded it anyway. I still dont have direct 3d.

---

### Post by BoneKracker on 2007-04-25
Beryl's still a bit buggy in Feisty.  It's great eye candy, but I would suggest to explore the system and read to get powerful with it  -- there's lots of fun stuff to learn.  Then you'll feel more comfortable modifying the settings and when you get some ugly error message while trying to upgrade your video driver or when Beryl makes your window borders and close box disappear.

---

