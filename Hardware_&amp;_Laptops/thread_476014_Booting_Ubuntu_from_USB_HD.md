---
title: "Booting Ubuntu from USB HD"
date: 2007-06-16
forum: Hardware &amp; Laptops
---

### Post by Ant1cl0ckwise on 2007-06-16
I have been trying for 2 days to achieve the following.........

1/ Hijack the wifes laptop 
2/ Install Ubuntu 7.04 onto an external USB Hard drive (Freecom 60Gb Mobile drive - bus powered)
3/ Once installed the laptop boots into windows (keeping the wife happy), or will boot into Ubuntu if I select USB as first boot device. ( having a happier wife/life if the windows MBR remained untouched by the Ubuntu install!!)

I have searched forums, not just for Ubuntu, but Linux in general and probably installed Ubuntu about 18 times over the last two days.  ](*,)There are many different solutions out there, some a lot more complicated than others. I am reasonably new to Linux and some of the solutions are way above my current technical abilities.  So I have tried one last solutions and it works.......for me anyway!!! 

Remove your laptops internal hard drive, plug in your USB drive, boot into Ubuntu live CD, and install as normal. The grub cannot interfere with your windows partition if it isn't there!! Once the install is complete, replace your hard drive and test the install. Mine appears to be working ok so far. Booting into windows by default or into Ubuntu if I hit F12 and select USB in the boot process.\\:D/

Hope this helps anyone trying to achieve the same.

For further reference my wifes laptop is a Lenovo N100 3000, windows xp home.

---

### Post by logos34 on 2007-06-16
Yes, that's certainly one sure-fire way to get the grub install right...Not very elegant but it DOES work. 

Is Windows partition mounting in Ubuntu so you can read the files on it?  May have to add it to fstab.

---

### Post by Ant1cl0ckwise on 2007-06-17
The windows partition is available through Ubuntu. 

I do agree with the elegant comment. I decided to switch to Ubuntu so that I could learn how my system runs and have more control over it. 

However, after 2 days of frustration,  it was either elegance or the laptop going out the window..............

---

