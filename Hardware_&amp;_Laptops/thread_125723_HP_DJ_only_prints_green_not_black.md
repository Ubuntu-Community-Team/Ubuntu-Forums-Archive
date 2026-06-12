---
title: "HP DJ only prints green not black"
date: 2006-02-04
forum: Hardware &amp; Laptops
---

### Post by GrayMagiker on 2006-02-04
I am having trouble printing on my HP Deskjet 3650.  

Ubuntu detected the printer fine, and was able to install it with the "hpijs" driver.  When I go to print from any application it will not print black, instead it prints green.  Everything seems to be printed green, or with color messed up.  The printer worked fine when I was in Hoary, but now in Breezy I get this problem.

I have changed the black ink cartridge, I have tried two different black cartridges that are full.  I have installed the hpijs, hplip, hplip-base, hplip-data, hplip-ppds, and hpoj packages.   I have re-installed all of those packages, as well as cups and all related packages.  I have also tried restarting cupsys at various stages.  I have uninstalled the printer and re-added it to no effect.  I have also changed settings in the properties > advanced tab to no effect.  

When I remove the color cartridge, nothing is printed at all.  

I know this is not an issue with the printer because I have a laptop with XP on it, when I install the printer on the laptop and hook it up, it prints how it is supposed to and black text on the XP test page is black.  

Anyone have any ideas on how to solve this problem?

---

### Post by GrayMagiker on 2006-02-06
I have had no luck getting it to print, however on a fresh install of Ubuntu Hoary I observed the same phenomena as described with Breezy.  This leads me to believe that there is an issue with the current version of hpijs driver.  

Is there anyway to roll back, and use a previous version of the driver?

When I had Hoary on the machine that now has breezy the exact same printer worked fine, so I think there is a earlier version of hpijs that works with it.  

Thanks to anyone who can help with this.

---

