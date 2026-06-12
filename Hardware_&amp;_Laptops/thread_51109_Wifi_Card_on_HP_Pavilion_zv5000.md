---
title: "Wifi Card on HP Pavilion zv5000"
date: 2005-07-22
forum: Hardware &amp; Laptops
---

### Post by kmramki on 2005-07-22
In HP Pavilion zv5000us, there is this button to turn the built-in wifi card on/off. When I boot in Windoze, I am able to use it. But when I run Ubuntu, it is always off, which means I cannot use wireless. So, I have to retain Windoze just so I could access the net at some hotspot, in some contingency arises. 

There are further problems too. My laptop is amd64. So, ndiswrapper does not work. The card is atmel-based Broadcom. Ubuntu has the drivers, which I have installed. But I dunno if it will work, coz I cannot turn it on in the first place! 

Is there any one out there who has got this working?

---

### Post by md4life on 2005-08-17
hey kmramki,  i just bought a pavillion 64bit laptop and i sounds almost the same as yours.  i was wondering how i could check out the details on all the hardware on my notebook.  a while back, i had this program that displayed all the info and configuration for you hardware, but can't seem to remember the name of the prog.  also, what ubuntu distro are you using?

---

### Post by nocturn on 2005-08-17
I have a zv5474 which is working fine with 32 bit Hoary.
There are 64 bit broadcom drivers, I believe someone ripped them from an Acer 64-bit install CD.

---

### Post by zackman2002 on 2005-08-24
I use Everest to see all of my computers specs.  It's helpful when working on someone elses computer so you don't have to open it up to see what parts are inside when replacing them.  But it is a win32 application which kind of sucks.

---

### Post by duffman25 on 2005-08-24
[QUOTE=zackman2002]I use Everest to see all of my computers specs.  It's helpful when working on someone elses computer so you don't have to open it up to see what parts are inside when replacing them.  But it is a win32 application which kind of sucks.[/QUOTE]


There are similar programs to everst:
Hardware Lister : [http://ezix.sourceforge.net/software/lshw.html](http://ezix.sourceforge.net/software/lshw.html)
gnome hardware browser: [http://www.xline.fr/index2.php?rub=dl#](http://www.xline.fr/index2.php?rub=dl#)

---

### Post by asimon623 on 2005-09-07
I have a zv5240 us I installed ndiswrapper ndiswrapped the driver bcmwl5.inf ndiswrapper -m ndiswrapper -l says driver installed hardware found or whatever it's supposed to say, and that modprobe command doesn't work...but wlan isn't listed under networking

any ideas?

---

### Post by oceanside on 2006-03-06
I have the same machine, just installed ubuntu, and still cannot get the internal wifi to work.  I would love to know how.  I installed ndiswrapper from Synaptic...I have an idea how to use it to install the drivers but the only drivers I have were dled from hp and are an exe file!  Any instructions for how to get this to work are much appreciated I really like this distro and don't want to install another!

---

### Post by pbransford on 2006-03-06
The button (i have a ze5730us) does not send a proper keyboard code, linux won't be able to recognize the button without extreme coaxing. I know that in windows it doesn't work either without special software.

That switch is only a light and button, whether that light is on or not has nothing to do with your radio working or not.


I might suggest spending ~ $50 on a WG511T ([http://www.netgear.com/products/details/WG511T.php](http://www.netgear.com/products/details/WG511T.php))

It works out of the box on Breezy 5.10. No ndiswrapper needed :D

---

