---
title: "Problem installing ubuntu using onboard video"
date: 2008-05-05
forum: Hardware
---

### Post by Souljah on 2008-05-05
Hi,

Ubuntu used to work fine on my old desktop. However, when I bought my new PC it is not working.

My hardware specs:
AMD X2 Athlon BE-2350 2.1 GhZ
ASUS M2N-VM DVI [BIOS v0603]
Using the onboard graphics [Nvidia GeForce 7050pv/nvidia 630a]

I am trying to install ubuntu v7.10. However, it's not able to and wants to run in low graphics mode and then just enters a Unix based environment with 5 lines at the top. I think X is not able to load because it doesn't support the onboard graphics. I am using the Live install CD. 

What are my options? Shall I install 8.04 using the alternate cd or are there drivers for the onboard graphics? Thanks.

Ryan

---

### Post by teaker1s on 2008-05-05
it possibly needs nvidia binary drivers,
If you 
```
sudo dpkg-reconfigure xserver-xorg
```
try nv or vesa as driver. if you can get a desktop then use "envy" to install the correct binary driver

---

### Post by Souljah on 2008-05-05
> **teaker1s said:**
> it possibly needs nvidia binary drivers,
If you 
```
sudo dpkg-reconfigure xserver-xorg
```
try nv or vesa as driver. if you can get a desktop then use "envy" to install the correct binary driver
And this I can do at the command prompt? If so I'll try it. Let me see how it works.

Also, if I do get a desktop, how would I use envy to install the correct driver during installation?

---

### Post by teaker1s on 2008-05-06
yes 
```
sudo dpkg-reconfigure xserver-xorg
```

 also see link

[http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

---

### Post by Souljah on 2008-05-07
> **teaker1s said:**
> yes 
```
sudo dpkg-reconfigure xserver-xorg
```

 also see link

[http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")
It didn't work, what you said. However, when I downloaded the alternate cd for 8.04 and installed it, it worked, only in 800x600 graphics. So download the non open source nvidia graphics from the hardware manager and then got a 1024x768 resolution so I guess it's resolved now, but in a different way. :)

---

