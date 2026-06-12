---
title: "Asus G75VW Ubuntu 12.04 question"
date: 2012-06-13
forum: Hardware
---

### Post by c0rrupts3ct0r on 2012-06-13
I have the following laptop. Asus G75VW. I installed ubuntu, but the only thing not working is the Nvidia Geforce 660GTX Mobile. I tried using "additional drivers" but it says no drivers are in use, I have run the update and everything. Does anyone have any Insight on how to get this working with ubuntu ? Nvidia's site does not have any drivers for my specific card,

Is there something i could do to make it fully supported?

Thanks

---

### Post by oakstair on 2012-06-13
I have just bought an G75vW as well and plan to install Ubuntu.

Should I ?

I tried the wubi.exe but that did not work!

Next attempt will be to burn a CD.

---

### Post by c0rrupts3ct0r on 2012-06-13
> **oakstair said:**
> I have just bought an G75vW as well and plan to install Ubuntu.

Should I ?

well, everything works as far as I can tell, EXCEPT the 660GTXm, i cannot for the life of me find drivers for it. the Wifi card (Atheros) i know works well with linux ( i use it with backtrack ). You will be stuck without the native res for your 660GTXm until there is drivers for it.

---

### Post by oakstair on 2012-06-15
I failed installing from the setup DVD I created.

I can se Ubuntu install screen (the purple one with just some tiny graphics at the bottom) but it hangs when reading the dvd.

The dvd seems ok to me.

So right now I dont know which will be my next try.

---

### Post by oakstair on 2012-06-16
I also tried it fron an USB stick and then Ubuntu install process started up with a conosole but after some lines (20-40) it hanged.

I wonder if it's my new G75VW that is broken or if it is something with the ubunti installers.

---

### Post by Elias Barroso on 2012-07-04
additional driver dont work, but you can search for Nvidia Driver on Ubuntu software center and you wil find the driver, just install this and have fun!

---

### Post by Yellow Pasque on 2012-07-04
> **Elias Barroso said:**
> additional driver dont work, but you can search for Nvidia Driver on Ubuntu software center and you wil find the driver, just install this and have fun!
NO, do not directly install the nvidia driver on an Optimus (hybrid graphics) laptop. There's a reason that "additional drivers" does not offer the nvidia driver on Optimus systems (it will break 3D or even make X fail).

Bumblebee works for Optimus, but people with recent nvidia GPU's (6xxM) were having issues with optirun. See: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by number5 on 2012-07-21
> **Temüjin said:**
> NO, do not directly install the nvidia driver on an Optimus (hybrid graphics) laptop. There's a reason that "additional drivers" does not offer the nvidia driver on Optimus systems (it will break 3D or even make X fail).

Bumblebee works for Optimus, but people with recent nvidia GPU's (6xxM) were having issues with optirun. See: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

G75VW only has one Nvidia card (660M or 670M), it has nothing to do with Optimus.

To install Ubuntu 12.04 on a new NVidia card you need to use the text mode, try follow the instructions here [http://askubuntu.com/a/129729/1867](http://askubuntu.com/a/129729/1867)
And yes, use the proprietary nvidia driver nvidia-current, that will gave you more performance and save you from lots of trouble

-- sent from my G75VW-T1013v Ubuntu 12.04

---

### Post by JD82 on 2012-09-23
> **number5 said:**
> G75VW only **has one Nvidia card** (660M or 670M), it has **nothing to do with Optimus**.

Hi,
do you know if this also applies to models without 3D display?

I want to buy one G75VW-9Z198V, but I am afraid of finding the Optimus to bother.

---

### Post by HrKristian on 2012-10-07
Neither G75 or G55 laptops uses Nvidia Optimus, not sure about the other models in the gaming series are the same, but I believe they are.

3D or no is solely a matter of the screen being used, all Nvidia cards are "3D Ready"...

---

