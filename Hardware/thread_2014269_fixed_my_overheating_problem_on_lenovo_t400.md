---
title: "fixed my overheating problem on lenovo t400"
date: 2012-07-01
forum: Hardware
---

### Post by tsardine on 2012-07-01
Hey All,


Im pretty new to Ubuntu, but did find a resolution to a problem i was  having with my Lenovo t400 laptop in Ubuntu 11.10 and 12.04.  I searched  for an answer to my overheating problem on many forums and tried lots  of things, but this seemed to solve my problem for good, so I thought i  would post it.  The problem was that t400, which ran at normal laptop  temperatures in Windows 7, would become exceedingly hot when running  ubuntu.  This happened even when the machine was sitting idle.

The problem appears to be related to the BIOS, and to the t400's OS  switchable graphics adapters.  (I would venture a guess that the t400 is  not the only laptop out there with switchable graphics adapters .)  The  T400 has an integrated graphics device and a discreet AMD Mobility  Radeon HD 3400 series.

Ubuntu and the fglrx driver do not seem to know what to do with this hardware configuration.

The solution is to disable the integrated graphics adapter in the BIOS of the laptop.  In my t400 i would enter setup and then:

--->Config----->Displays----->
--Default Display Device = *PCI Express*
--Boot Display Device = *Thinkpad LCD*
--Graphics Device = *Discreet Graphics*
--OS Detection for Switchable Graphics = *Disabled*

After committing these changes and booting into Ubuntu, Run *lspci  *to confirm that you indeed only one show one active Graphics Card.  Like this:

~$ lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV620 [Mobility Radeon HD 3400 Series]

This may be optional---Now you may want to purge and install a fresh  fglrx driver for the AMD/ATI graphics adapter.  (Skip this if you're  laptop does not have a discreet AMD/ATI graphics adapter.)

~$ sudo apt-get purge fglrx

~$ sudo apt-get install fglrx

restart Ubuntu and now you should finally be able to use your Ubuntu laptop ON your lap!!

Thanks!

---

### Post by jakobb on 2012-08-18
Having heat problems like the ones you describe on my Ubuntu 12.04 @ Lenovo T430

It didn't really seem to turn on when using discrete graphics, but managed to turn on with Integrated. 

Now much more silent and not as warm.

[Edit: I was not able to ad a tag called "lenovo t430"]

---

### Post by twipley on 2012-08-24
I am using integrated graphics (basic T430) -- am I affected by this issue? Also note that I am never firing up video games at all on this laptop.

---

### Post by jakobb on 2012-08-24
> **twipley said:**
> I am using integrated graphics (basic T430) -- am I affected by this issue? Also note that I am never firing up video games at all on this laptop.

If you
* dont have a graphincs card
* dont have a noisy and warm laptop

then I think the problem is caused by the default graphics drivers in ubuntu

---

### Post by twipley on 2012-09-14
> **jakobb said:**
> If you
* dont have a graphics card
* dont have a noisy and warm laptop

then I think the problem is caused by the default graphics drivers in ubuntu

Well, having no point of reference, relating to either noise or temperature, I cannot tell.

---

