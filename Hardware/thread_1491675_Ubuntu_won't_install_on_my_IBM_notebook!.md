---
title: "Ubuntu won't install on my IBM notebook!"
date: 2010-05-23
forum: Hardware
---

### Post by ch91woo on 2010-05-23
Hello fellow forum members, I've been having problems with installing Ubuntu on my IBM laptop. The problem is that I cannot boot into the Ubuntu live CD, although it does show the menu with the following selections; "Install ubuntu now" "Try Ubuntu without installing it" etc. After I choose either the option "install ubuntu now" or "try ubuntu without installing" it wouldn't boot into it! My laptop was bought way back in the year 2000 and has Windows 2000 installed on it right now. What can possibly be the problem? 

The laptop's series by the way, is the "i series."
thank you all in advance for the input.

---

### Post by tgalati4 on 2010-05-24
How much RAM?  You need a minimum of 256 MB.  Also you can set "safe graphics mode" by hitting one of the function keys.

---

### Post by ch91woo on 2010-05-24
> **tgalati4 said:**
> How much RAM?  You need a minimum of 256 MB.  Also you can set "safe graphics mode" by hitting one of the function keys.

The laptop definitely has over 256 mb of ram. Also to clarify, the laptop is the Thinkpad i series 1200. I hope this made things easier. And I tried the safe graphics mode too. That doesn't work either. I also tried Kubuntu and Xubuntu, but they all don't work ): I don't know what's going on! :confused:

---

### Post by dino99 on 2010-05-24
you need to boot by adding [COLOR="Blue"]acpi=force irqpoll[/COLOR] on the boot line

then when installation is done, you make this permanent:

sudo gedit /etc/default/grub

on the line ended by "quiet splash", change this by "acpi=force irqpoll quiet splash"

a little guide for installation:
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by ch91woo on 2010-05-24
> **dino99 said:**
> you need to boot by adding [COLOR=Blue]acpi=force irqpoll[/COLOR] on the boot line

but how do I add the line when I am trying to boot from the Live CD?

---

### Post by tgalati4 on 2010-05-24
There should be an function button that allows you to pass kernel parameters before booting into the Live CD.  Look through the FN help pages when the Live CD selection window comes up.

---

