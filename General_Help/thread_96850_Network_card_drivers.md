---
title: "Network card drivers"
date: 2005-11-29
forum: General Help
---

### Post by pabacon on 2005-11-29
Hi, i'm a complete novice with all this but am keen to move towards an open source environment so have installed Ubuntu 5.10.

I found the setup very straight-forward and the OS seems great.. the big problem i'm faced with is that i can't find a driver for my wireless network card.

I have looked at using a wrapper such as linuxant driverloader but don't really want to be shelling out a load of money unless i really have to.

Does anyone know if there is an easier way around this or somewhere i can find the driver i'm looking for? (US Robotics 5416)

Thanks loads in advance for any help.

Phil

---

### Post by Dr. Nick on 2005-11-29
ndiswrapper is free and similar to driver loader. You can look into that, It can be installed from synaptic. If you can find the chipset to the card you may be able to avoid wrappers and use a builtin driver.

EDIT
I believe your chipset to be TI ACX 111 by reading the ndiswrapper page here [http://ndiswrapper.sourceforge.net/forums/viewtopic.php?t=281]("http://ndiswrapper.sourceforge.net/forums/viewtopic.php?t=281")

Their are native drivers for it , but ndiswrapper may be a better choice. 
Run **lsmod | grep acx** in a terminal and see if anything is loaded. Post that output here if you need help.

---

### Post by pabacon on 2005-11-29
Thanks for the speedy reply!

I installed ndiswrapper from synaptic (it was called something like ndiswrapper-utils - is that the right one?) but i couldnt get the application to run, i didnt get any kind of error message, just a complete lack of any kind of response! (](*,) embarassing eh?)

Any idea what i might have done wrong there?
or if i were to 'avoid wrappers and use a builtin driver' how would i go about it?

Thanks again!
P

---

### Post by ruudiculus on 2006-02-04
I have a USR 5416 too and I managed to get it to work (once) with ndiswrapper, do I know it works. Now I have the problem that I don't remember how I did it before. I've posted my question in the thread ***[USR5416 odd problem ]("http://www.ubuntuforums.org/showthread.php?t=95228")***

So you can try and use ndiswrapper which is probably the most convenient (and costless) way and when you may experience the same problem I have, we'll find a solution for it together! Chances are that you won't have the problem I have now at all.

So, to help you try to use ndiswrapper do the following;

Keep your windows drivers at hand. These should consist of a *.inf file, a *.sys file and maybe a *.bin file. I've got mine from [www.linuxant.com](www.linuxant.com) (the site with the non-free solution, but with the free drivers).

Give your windows driver to the ndiswrapper program:
```
sudo ndiswrapper -i *windowsdriver*.inf
```

List the installed windows drivers:
```
sudo ndiswrapper -l
```

If you have given ndiswrapper the right windows driver the above comand will at least result in the message **driver present**. Hopefully it also says **hardware present**. If so ndiswrapper has linked the windows driver to the appropriate hardware (your wlan card). If the last thing is the case, then just proceed with the steps below. If it isn't, please report it and you'll get the second block of instructions :) .

Now, you have to link the ndiswrapper program to your wireless card (normally _wlan0_). Everytime you do things with wlan0, linux will know that you mean to use ndiswrapper.
```
sudo modprobe ndiswrapper
```

Now you would want to have wlan0 linked to ndiswrapper right from the moment of booting Ubuntu. Do this by typing:
```
sudo ndiswrapper -m
```

Now you should be set and ready to use your wireless network card (if you don't experience my problem):)  Check this by typing:
```
sudo iwlist wlan0 scanning
```

This should return a list with information for every accesspoint around. If you know for sure that you do have an accesspoint around to which you can connect, but the iwlist command returns "No scan results" THEN you have experienced the same problem I'm experiencing every time. The best thing to do then is to visit the thread I spoke about in the beginning [http://www.ubuntuforums.org/showthread.php?t=95228]("http://www.ubuntuforums.org/showthread.php?t=95228").

---

