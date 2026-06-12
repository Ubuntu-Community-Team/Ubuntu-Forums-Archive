---
title: "Laptop ATI 9700 Dual Monitor"
date: 2005-03-23
forum: Hardware &amp; Laptops
---

### Post by hou5ton on 2005-03-23
I would like to use Hoary on my main laptop, but really need that external monitor in addition to the one of the laptop, and not as a clone, but as an extended desktop.  However, looking through all the forums and asking on irc, I'm not having much luck or I'm just not looking in the right places.

This laptop has an ATI mobility radeon 9700. Is what I'm wanting even possible with this laptop? (Some have said it isn't.) But if it is, is there a clear how-to posted somewhere to walk me through it?

---

### Post by Strider on 2005-03-23
Here's an Howto guide for the ATI Radeon drivers.  Haven't tried the dual display but give it a shot...

[http://www.rage3d.com/content/articles/atilinuxhowto/](http://www.rage3d.com/content/articles/atilinuxhowto/)

---

### Post by Leszek Tarkowski on 2005-03-24
[QUOTE=Strider]Here's an Howto guide for the ATI Radeon drivers.  Haven't tried the dual display but give it a shot...

[http://www.rage3d.com/content/articles/atilinuxhowto/](http://www.rage3d.com/content/articles/atilinuxhowto/)[/QUOTE]
 to run dual-head is rather simple - i'v followed the instructions on [http://gentoo-wiki.com/HOWTO_Separate_x-screens_on_Monitor_and_TV](http://gentoo-wiki.com/HOWTO_Separate_x-screens_on_Monitor_and_TV) and it is working on my laptop (Radeon 9600, fglrx). Only troubles i have now is to choose (maybe at level of gmd) to use single or dual-head config, and to enable some light windowmanager (fvwm) on second display (not second gnome with is default)

---

### Post by jonny on 2005-03-24
[QUOTE=Leszek Tarkowski]to run dual-head is rather simple - i'v followed the instructions on [http://gentoo-wiki.com/HOWTO_Separate_x-screens_on_Monitor_and_TV](http://gentoo-wiki.com/HOWTO_Separate_x-screens_on_Monitor_and_TV) and it is working on my laptop (Radeon 9600, fglrx). Only troubles i have now is to choose (maybe at level of gmd) to use single or dual-head config, and to enable some light windowmanager (fvwm) on second display (not second gnome with is default)[/QUOTE]
 The how-tos that I've found for my laptop are horrific and I haven't dared tackle this problem yet.  it's a real shame that it doesn't work out of the box - Beatrix (an excellent live CD based on a cut-down version of Warty) works perfectly for me with no fiddling, so I don't understand why its parent distro doesn't work.

---

