---
title: "ubuntu drivers for clevo x8100?"
date: 2010-10-25
forum: Hardware
---

### Post by Sagacious on 2010-10-25
does anyone have or know where i can get ubuntu drivers for my clevo x8100 laptop? Drivers such as Bluetooth, touch panel controls, fingerprint biometic device and gaming hot keys?

---

### Post by Sagacious on 2010-10-26
*bump*

---

### Post by Sagacious on 2010-11-01
*bumpety bumpety* ...no one? surely everyone is familiar with the clevo x8100? fastest laptop you can get...?

---

### Post by IcarusR on 2010-11-01
Drivers in linux ( which Ubuntu is a variation of) are built into the kernel.
The main exceptions to this are proprietary & non free open source drivers.

You need to tell us what version of Ubuntu you are using. Would also be helpful to add it to your profile, then we can all see.

Also we need more info on the exact make & model of the hardware you are having difficulties with. Along with an explanation of what you have tried so far.

Of course you could always search the forum for the hardware model # & id #. And I guess you have also heard of google. That is where I get a lot of my info from !

> surely everyone is familiar with the clevo x8100? fastest laptop

Nope never heard of it & would certainly never buy either !

> gaming hot keys

I guess you mean 'special keys', they are unlikely to work. Could test with xev (yes google it) & see if they send a key code that is read by ubuntu. (is in the repositories)

> fingerprint biometic device

I know nothing about these, do not have one, heard mixed reports as to support in ubuntu.

> touch panel controls

Generally touchpads are well supported in ubuntu. Explain more of what you want to be able to do.

> Bluetooth

Need to install a load of bluetooth software from repositories.

Lot of info on ubuntu, specifically Lucid here

[http://ubuntuguide.org/wiki/Ubuntu:Lucid]("http://ubuntuguide.org/wiki/Ubuntu:Lucid")


To find out details of your system hardware from a terminal run the following 

USB
```
lsusb
```

pci
```
lspci
```

---

### Post by Sagacious on 2010-11-01
> **IcarusR said:**
> Drivers in linux ( which Ubuntu is a variation of) are built into the kernel.
The main exceptions to this are proprietary & non free open source drivers.

You need to tell us what version of Ubuntu you are using. Would also be helpful to add it to your profile, then we can all see.

Also we need more info on the exact make & model of the hardware you are having difficulties with. Along with an explanation of what you have tried so far.

Of course you could always search the forum for the hardware model # & id #. And I guess you have also heard of google. That is where I get a lot of my info from !



Nope never heard of it & would certainly never buy either !



I guess you mean 'special keys', they are unlikely to work. Could test with xev (yes google it) & see if they send a key code that is read by ubuntu. (is in the repositories)



I know nothing about these, do not have one, heard mixed reports as to support in ubuntu.



Generally touchpads are well supported in ubuntu. Explain more of what you want to be able to do.



Need to install a load of bluetooth software from repositories.

Lot of info on ubuntu, specifically Lucid here

[http://ubuntuguide.org/wiki/Ubuntu:Lucid]("http://ubuntuguide.org/wiki/Ubuntu:Lucid")


To find out details of your system hardware from a terminal run the following 

USB
```
lsusb
```

pci
```
lspci
```


would never buy? why not?! core i7 $ 5870 crossfire!

im running ubuntu 10.04 with gnome.
laptop : [http://www.gizmag.com/clevo-x8100-fastest-gaming-laptop/14421/picture/111850/](http://www.gizmag.com/clevo-x8100-fastest-gaming-laptop/14421/picture/111850/)


the touch panel has volume level, camera, music player, webcam, blueooth and fan control hotkeys.

the fingerprint reader is by upek
the camera is a bison cam nb PRO 2.0mp
theres also a tm6200 HDMI input capture device 

i havent been able to find any drivers through google...

---

### Post by IcarusR on 2010-11-01
> i havent been able to find any drivers through google..

You've missed my point.

The drivers sre mostly already there. You need to search the forum & / or google to find other people who had the same difficulty with your hard ware & then try to fix like they did.

Or pay my flight over & I'll do it all for you. I need a holiday !!

> the touch panel

They are known as resistive buttons. Don't think you'll get them to work. But no harm in trying my earlier suggestion.

> bison cam nb PRO 2.0mp

As far as I know there is no driver.
But install cheese & try it.

The rest I can not comment or spend more time doing your research.

---

