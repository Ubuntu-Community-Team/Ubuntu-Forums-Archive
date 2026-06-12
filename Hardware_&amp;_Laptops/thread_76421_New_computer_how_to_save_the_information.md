---
title: "New computer: how to save the information?"
date: 2005-10-15
forum: Hardware &amp; Laptops
---

### Post by Verzicht on 2005-10-15
hello!

My last computer was: 

Asus P3BF
Pentium III Tualatin
Geforce AGP FX5600

And there was UBUNTU LINUX installed. Then, after my AGP port on MB has been damaged, i changed my configuration to:

Asus P5ND2-Sli Delux (nForce)
Pentium D
Geforce PCI-E N6600GT

Now, question :D :
1) Can Ubunu Linux from old HARD DRIVE start on new harware configuration?
2) If yes, can i burn my information from Harddrive to CD-R, or send it by LAN.
3) If now, how can i save my information?

---

### Post by easterndodo on 2005-12-05
Well, I don't know if there is a way to save all your hardware configuration and automatically install Ubuntu using that configuration...

Basically, you would need to save all your /etc folder (by, for example, a [FONT="Courier New"]tar -zcf etc.tar.gz /etc[/FONT]), then install your new Ubuntu distribution on the new computer and, after all, opening the old /etc you saved and restoring the information on the new installation.

I would not suggest you to directly overwrite the new /etc/ with the old one you saved... that might bring problems if packages installed are not the same version... Well, if you install from the same cd, it might work, but you have to do "manual" work, by examining the fundamental files and placing the old settings on the new ones...

I don't know if this is of any help, but I usually do this when I want to bring my old settings on new installations of Linux...

---

