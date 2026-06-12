---
title: "Cannot use Extra Desktop Effects!"
date: 2008-11-02
forum: General Help
---

### Post by Gismo235 on 2008-11-02
Hi,

I've just loaded Ubuntu 8.10 on to my computer which is a Packard Bell iMedia 5093, and i've been trying to load the extra desktop effects but it has been saying cannot load desktop effects everytime I have tryed it! :confused:

Any help? Thanks.

---

### Post by Gismo235 on 2008-11-03
Help please? :confused: :(

---

### Post by feng85jie on 2008-11-03
[Air Filter](http://www.chinafengjie.com/air-filter/)Ruian Fengjie Auto parts manufacture CO.,LTD is a company specilized in Filter and Filter components service.

---

### Post by zirun292 on 2008-11-03
Try to install your driver on

System > Administration > Hardware Drivers

Tick your driver and wait for the installation to finish and try the Extra Desktop Effects again.

It will work 100%

---

### Post by johnj33 on 2008-11-04
I'm having the same problem but when i press hardware drivers nothing appears in the box

---

### Post by DirkGently on 2008-11-04
The X.org version in Intrepid does not work with legacy video drivers (In Nvidia's Case 71 && 96). This causes no compatible drivers to be found in the Hardware Drivers page. Hardy Heron should work better.

Im having the same woes with an Nvidia Quadro 400 NVS...if someone finds a workaround. Id love to hear it :-)

---

### Post by kyme on 2008-11-04
Hey guys same in here. Everytime i click in desktop effects, a box appeared
and sez; Cannot enable desktop effects.
I have P4 3GHZ and 1GB ram

> 
 The X.org version in Intrepid does not work with legacy video drivers (In Nvidia's Case 71 && 96). This causes no compatible drivers to be found in the Hardware Drivers page. Hardy Heron should work better.


  hello sir, what do you mean by that?, you mean theres no other way? :(

---

### Post by zirun292 on 2008-11-12
> The X.org version in Intrepid does not work with legacy video drivers (In Nvidia's Case 71 && 96). This causes no compatible drivers to be found in the Hardware Drivers page. Hardy Heron should work better.

It means no compatible Nvidia video driver is found on the Intrepid Ibex version.

You should look at this one:-

**_[CENTER][http://sudan.ubuntuforums.com/showthread.php?t=970237](http://sudan.ubuntuforums.com/showthread.php?t=970237)[/CENTER]_**

and

I found the way how to make it worked!

1. Downloaded the beta driver from nvidia here the 96.43.09 legacy BETA [[COLOR="Blue"]here[/COLOR]]("http://www.nvnews.net/vbulletin/showthread.php?t=122139") ( I Used the Nvidia driver 0.run)

2. Downloaded from synaptic manager linux-headers-generic and linux-source-2.6.27

```

sudo apt-get install linux-headers-generic linux-source-2.6.27
```

3. CTRL + ALT F1

4.
Code:

```
sudo /etc/init.d/gdm stop
```

5.
Code:

```
sudo sh NVIDIA DRIVER that you downloaded from the url above
```

6
Code:

```

sudo /etc/init.d/gdm start
```

and done!

That worked for me
__________________________________________________________________________

i found this problem solving on this ubuntuforum site:-
[B][U]
[http://ubuntuforums.org/showthread.php?t=971103](http://ubuntuforums.org/showthread.php?t=971103)[/U][/B]

---

