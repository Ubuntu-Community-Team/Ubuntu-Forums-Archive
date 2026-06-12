---
title: "Nvidia 8700GT Sli"
date: 2009-05-13
forum: Hardware
---

### Post by amirage on 2009-05-13
Hello all

I have installed the latest ubuntu 9.04 with the latest Nvidia drivers 180.44. My system has an Nvidia SLI 8700GT card. The powermizer function in the driver shows that 1st card is running a max performance while the second is running at the lowest level. Is there anyway I can have both the cards running at top level - 650Mhz (GPU processor speed) and 300Mhz (GPU ram speed).

I tried installing coolbits but no use. My system is a DELL XPS 1730, with the card mentioned above, Intel T8300 2.10 Ghz processor, 2GB DDR2 ram, 200GB HDD.

Please let me know if there's a work around for this.

Regards

Amit

---

### Post by amirage on 2009-05-14
Wow!

18 views and no reply...must be a really tough issue..aye?

Someone...anyone...any help appreciated...

---

### Post by tuxwrench on 2009-05-14
I think most of the problems of these proprietary Nvidia cards is because the name being given by [COLOR="Blue"][FONT="Courier New"]lspci[/FONT][/COLOR] in the terminal doesn't match the one being stated on the proprietary driver.

[COLOR="Sienna"][FONT="Courier New"]system > administration > Hardware drivers[/FONT][/COLOR] recommend these drivers from nvidia but the names being listed on the [COLOR="SeaGreen"][nvidia driver]("http://packages.ubuntu.com/intrepid-updates/nvidia-glx-96")[/COLOR] do not match the name on [COLOR="Blue"][FONT="Courier New"]lspci[/FONT][/COLOR]

I had to edit the [COLOR="Blue"]xorg.conf[/COLOR] file
[[COLOR="RoyalBlue"]so here's how I did it[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1158597") [http://ubuntuforums.org/showthread.php?t=1158597](http://ubuntuforums.org/showthread.php?t=1158597)

I hope the same will work out for you

---

