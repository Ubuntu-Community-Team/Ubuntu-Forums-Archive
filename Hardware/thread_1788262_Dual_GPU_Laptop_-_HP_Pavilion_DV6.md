---
title: "Dual GPU Laptop - HP Pavilion DV6"
date: 2011-06-22
forum: Hardware
---

### Post by SilentColour on 2011-06-22
Hi,
I'm very new to Ubuntu but I really want to replace Windows with it eventually. At the moment however, Ubuntu is only recognizing one of the GPU's in my laptop. :(

My laptop has a shared (integrated) one and a dedicated one, ATI Radeon HD 4250 (integrated) and the ATI Radeon HD 5470 (dedicated).

At the moment the 4250 is the only one that's registering with Ubuntu even with the proprietary drivers installed. Every time I try and switch to the high performance GPU in the ATI Control center, it stays on the integrated no matter what.:popcorn:

Any help is appreciated! Am I using the wrong drivers? :D

---

### Post by jerrrys on 2011-06-22
i can point you to a link that may help

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=2+two+gpu&sa=Search&cof=FORID:9#1031](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=2+two+gpu&sa=Search&cof=FORID:9#1031)

good luck

---

### Post by SilentColour on 2011-06-22
Ermm, that didn't really help sorry. Which link are you referring to? the URL takes me to a page of lodes of confusing links to stuff...

I'm still having trouble finding a thread that helps me with this, on any forum. I don't expect someone to have exactly the same problem or laptop, I just need something that tells me how to deal with 2 ATI GPU laptops...

Thanks anyway... :popcorn:

---

### Post by Blasphemist on 2011-06-22
AMD says switchable graphics of your config, 2 amd gpu's, is only available for win 7. [http://www.amd.com/us/products/technologies/switchable-graphics/Pages/switchable-graphics.aspx](http://www.amd.com/us/products/technologies/switchable-graphics/Pages/switchable-graphics.aspx)

There are projects such as bumblebee and debumblebee for dealing with switchable graphics but that project works for intel/nvidia. [http://www.martin-juhl.dk/](http://www.martin-juhl.dk/)
> Crazy Bumble-weeks
It has now been about 4 weeks since I sat in a small hotel room in Norway and implemented the first lines, of what was going to be the bumblebee project.

By now I have hit over 30.000 hits on the first blog page alone, have about 200 followers on twitter and about 200 issues have been created on github ( about 130 closed )…

z0rc has forked the project to debumblebee and is now supporting debian through that.

Joaquín is providing support for Arch Linux, and  backbone is handles Gentoo

arnauddupuis and paulvriens are helping me on bumblebee with Fedora and OpenSuSE support, and other people are also beginning to submit patches and suggestions (thanks!)..

This has really been some crazy weeks, and not looking to settle down right now.. 

Thanks to all for your support, suggestions and reports..

 

Arch Linux Support:

[http://aur.archlinux.org/packages.php?ID=49469](http://aur.archlinux.org/packages.php?ID=49469)

wiki:

[https://wiki.archlinux.org/index.php/Bumblebee](https://wiki.archlinux.org/index.php/Bumblebee)

Debian Linux Support:

[https://github.com/z0rc/debumblebee](https://github.com/z0rc/debumblebee)

Gentoo Linux Support:

[https://github.com/iegor/bumblebee-Gentoo-support](https://github.com/iegor/bumblebee-Gentoo-support)


I think you do have some fairly serious googling ahead. There are many different configurations for work on switchable graphics and yours is the first I've seen that uses the same driver for both cards. I think your best hope may be in the direction of wayland which for the time being would put you on the bleeding edge. That said, I don't think your config would be at the top of the list for wayland. 

This is the link for the x.org wiki on radeon. [http://wiki.x.org/wiki/radeon](http://wiki.x.org/wiki/radeon)
This is the link for wayland on freedesktop. [http://wayland.freedesktop.org/](http://wayland.freedesktop.org/)

---

### Post by SilentColour on 2011-06-22
*sad face* oh well, best get started with the googling then...
Thanks anyway, bieng a noob I have no idea what "Wayland" is nor Xorg although I have been Xorg before... "Xorg Server" right?

Thanks again.

---

### Post by DrWolfe on 2011-06-25
I have the HP DV6 6090us that has a Intel video card and a 6770m. Ubuntu does not even install for me. It uses the new Sandy Bridge CPUs.

How did you get it to install?

---

