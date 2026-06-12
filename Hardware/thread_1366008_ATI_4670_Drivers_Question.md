---
title: "ATI 4670 Drivers Question"
date: 2009-12-27
forum: Hardware
---

### Post by MeanEYE on 2009-12-27
I was just wondering: is ATI going to start making decent drivers anytime soon. 

It's not that just us, linux users, are suffering. To my experience ATI never made good drivers for any OS. Yes, sure, windows drivers work A LOT better than Linux ones but still, they never seemed to work like they should.

I've just spent 6 (or more) hours trying to make this damn card to work with no luck.

After the "white ubuntu logo" screen just freezes, keyboard stops responding and that's it. I end up with black screen and no control over my machine.

I've really tried EVERYTHING. Even tried stupid things I knew they could never work. Read almost every article online that I was able to find and still nothing.

Anyone had similar issues?

---

### Post by spigy11 on 2009-12-28
Hi

I have an ati 4770 so think similiar cards, I installed 9.12 and the drivers are working just fine - with the new drivers is comming also the support for Cairo-dock OpenGL :)

I have installed my drivers with the following command

sudo sh ./ati-driver-installer-9-12-x86.x86_64.run --buildpkg Ubuntu/karmic 

I have Ubuntu 9.10 Karmic Koala ;)

---

### Post by Piscicani on 2009-12-28
Hi, 
I'm an ATI user my first Radeon was a 9550, then i've used an HD 4550 a HD 4650 and now two HD 4870 , well IMHO ATi drivers on Win are just fine the Fglrx one are terrible, but are emproving day by day.  I suggest you to be carefull, the installation procedure need a complete disinstallation of the present fglrx components and sometimes X server restart.

---

### Post by MeanEYE on 2009-12-28
> **Piscicani said:**
> Hi, 
I'm an ATI user my first Radeon was a 9550, then i've used an HD 4550 a HD 4650 and now two HD 4870 , well IMHO ATi drivers on Win are just fine the Fglrx one are terrible, but are emproving day by day.  I suggest you to be carefull, the installation procedure need a complete disinstallation of the present fglrx components and sometimes X server restart.

Thank you for your concern :). I am a long time linux user but it seems expirience and logic has little to do with these drivers.

---

### Post by MeanEYE on 2009-12-28
Really? Those I downloaded from AMD site could build packages only for redhat and suse. Where did you download yours?

---

### Post by M20554443 on 2010-02-02
Just want to say that I have the same problem since installing karmic last year: HIS Radeon HD 4670, Dell Optiplex 740 (with onboard graphics). When enabling/installing the fglrx drivers (I tried various driver versions) the system doesn't respond anymore after a reboot (black screen when I expect gdm to be started). 

I couldn't find a solution. There are some bug reports at launchpad that may be related to this issue though. For now I gave up hoping this will be fixed in the next ubuntu or ati driver versions. Or maybe the radeonhd driver will come to aid by supporting 3D for these cards ...

---

### Post by MeanEYE on 2010-02-03
> **M20554443 said:**
> Just want to say that I have the same problem since installing karmic last year: HIS Radeon HD 4670, Dell Optiplex 740 (with onboard graphics). When enabling/installing the fglrx drivers (I tried various driver versions) the system doesn't respond anymore after a reboot (black screen when I expect gdm to be started). 

I couldn't find a solution. There are some bug reports at launchpad that may be related to this issue though. For now I gave up hoping this will be fixed in the next ubuntu or ati driver versions. Or maybe the radeonhd driver will come to aid by supporting 3D for these cards ...

I'll try once more to fix it. There's some indication that drivers might just work if they are installed before updating system... But, let's wait and see :)

---

