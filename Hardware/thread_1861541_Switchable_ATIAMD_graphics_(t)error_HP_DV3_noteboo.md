---
title: "Switchable ATI/AMD graphics (t)error HP DV3 notebook"
date: 2011-10-15
forum: Hardware
---

### Post by fantasm!c on 2011-10-15
I have installed the new 11.10 release on my notebook (64bit). It is a HP DV3 2350ed notebook with an ATI HD4350 and an intergrated intel graphic card.

After the installation everythings runs great but i can't switch the graphics card. I have read that the new ati catalyst drivers contain powerxpress for switching graphic cards.

However. When I install the AMD drivers using the jockey utility everything goes wrong. The 'post release' version doesn't work at all. It doesn't install. The normal version does work. 

After the reboot and the AMD driver is installed the 3d unity becomes 2d. That doesn't look good. When I try to open the AMD catalyst center I get an error 'unable to open CCC because there isn't a proper AMD driver installed'. So no way of switching the graphic card. And I loose the 3d when i install the AMD driver.

I can't recall the error messages exactly because i reinstalled the whole thing and now I am using the open source driver but that way I can't choose which grahpic card my laptop is using. The AMD card is eating all my battery :(

---

### Post by fantasm!c on 2011-10-16
I'v been trying some things.

I can install the fglrx-updates package from synaptic. After reboot the desktop is 2d. When i try to open ati catalyst i get this error: "There was a problem initialzing .... No AMD graphics driver is installed, or the AMD driver is nog functioning properly. Please intall the AMD driver appropiate for you AMD hardware, or configure using aticonfig"

When i try to run aticonfig --initial I get this error: "PowerXpress error: Cannot stat '/usr/lib64/fglrx': No such file or directory
Failed to initialize libglx for discrete GPU

When I reboot after this setup Unitiy doesn't even load, Only the nautilus bar loads. 

Somehow I get the idea that my notebook runs on the intel and the AMD driver is trying to initialize the intel card instead of its own.

Edit:

I made an installation in 32 bit and i have installed the fglrx-updates package. The desktop is 2d after the installation. 

I still can't open ATI catalyst but I can run sudo aticonfig --initial. However there are some strange errors and xserver is not working anymore.
When I try to switch to the igp (using sudo aticonfig --px-igpu i get this error:
aticonfig: error while loading shared libraries: ligGL.so.1: cannot open shared object file:  No such file or directory.

And the xserver won't start anymore.

---

### Post by fantasm!c on 2011-10-16
I'm giving this up. The AMD driver is nog working well with ubuntu 11.10. Maybe in a few months I try again.

Is there a way to disable the AMD graphic card in ubuntu. So it doesn't eat the battery and so I can use the onboard Intel only.

---

### Post by gnaag on 2011-12-06
You can probably disable switching graphics in bios. Disable discrete or switchable

---

