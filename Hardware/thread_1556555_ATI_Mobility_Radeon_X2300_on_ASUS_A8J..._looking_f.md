---
title: "ATI Mobility Radeon X2300 on ASUS A8J... looking for 3D while happy in 2D"
date: 2010-08-19
forum: Hardware
---

### Post by iknatius on 2010-08-19
To whom it may interest...

After surfing through the forums for some days with not much luck, I would like to share my personal howto reach the best possible from your ATI Mobility Radeon X2300.

Basically, everything started when I first installed Ubuntu 10.04 on my ASUS A8J and graphics where like the photo attached. Although some people seem to be working fine with default Ubuntu Open Source Drivers ([http://ubuntuforums.org/showthread.php?t=1553371&highlight=x2300](http://ubuntuforums.org/showthread.php?t=1553371&highlight=x2300)), you can see that it is not my case.
After trying ppa-edgers drivers ([http://ubuntuforums.org/showthread.php?t=1524945&highlight=x2300](http://ubuntuforums.org/showthread.php?t=1524945&highlight=x2300)) the result was the same crappy "magnetic fields affected computer".
I decided to sell my soul to the dark side and look for the proprietary ATI drivers... to find that ATI does not support Mobility Radeon X2300 since Catalyst 9.4 (they are currently in 10.4 version) and in several places is advised that to install these drivers is not recommended if your card is not in the supported list.
I was just looking to my bank account to see if I had enough money to buy a Mac and forget about Linux for ever; when something crossed my mind and installed fglrx drivers... and everything but 3D worked.
So, if you have ATI Mobility Radeon X2300 graphics card and open source drivers do not work for you... Just install fglrx and you will have everything but 3D and all that flashy things like transparency blahblabh that you can find in Compiz (at least this worked for me).

Howto do it:
> sudo apt-get install xorg-driver-fglrxPlease, do not blame me if it does not work for you, it worked in my laptop. You can go back with a clean Open Source Drivers installation following this instructions: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch")

Good luck and please, if you have found a way to have 3D with this card share it with me (with all)

--
iknatius

---

### Post by jotape99 on 2010-09-22
It has resulted fine for me too.

Thx.

---

### Post by ruicfc on 2010-10-02
Tenho um asus com uma A**TI Mobility Radeon X2300** a usar **Ubuntu 10.4 x64** e estava com o mesmo problema (imagem a tremer e com riscas tipo televisor dessintonizado , mas ao usar este driver "fglrx" ficou resolvido.

> sudo apt-get install xorg-driver-fglrx 			 		

Obrigado :)

_I'm Portuguese_

---

