---
title: "EEEPC 901 build-essential help"
date: 2008-07-17
forum: Hardware
---

### Post by nsegative on 2008-07-17
Hey guys I'm trying to install wireless on my eeepc. I installed the ubuntu release from here: [http://www.ubuntu-eee.com/index.php5?title=Main_Page](http://www.ubuntu-eee.com/index.php5?title=Main_Page)

I am following this guide:
[http://kunin.wordpress.com/2008/07/05/asus-eee-pc-901/](http://kunin.wordpress.com/2008/07/05/asus-eee-pc-901/)
However when I download the build essential and run it it tells me that "dependency is not satisfiable: libc6-dev|libc-dev. However those packages are already installed, and the last time I over wrote them it broke all my other packages and I had to format and reinstall ubuntu. I'm really lost and could use some help.

Ethernet does not work as well as it needs build-essentials to install. The only way I get files across is via USB.

---

### Post by nsegative on 2008-07-18
Anyone? I formatted winxp for this and have no way of going back XD

---

### Post by Askrates on 2008-07-19
Hello there buddy, I had the same problem, but found this solution on the net 

After the install process, you may be unable to use any of the ethernet devices. Two solutions are possibles:

    * Use a usb ethernet dongle
    * get a precompiled atl2.ko module here ( atl2.ko for Ubuntu Hardy ), and copy them into /lib/modules/2.6.24-16-generic/kernel/drivers/net/. Finally, type sudo depmod -a and you will have now a working ethernet device. Of course, d/l the module on a usb key 

Unfortunately, this doesn't work for me. I have a suspicion this is because the precompiled atl2.ko is compiled with a 2.6.24-16 kernel, and I am using a 2.6.24-19 kernel. 

So in conclusion: HEEELP!!

---

### Post by nsegative on 2008-07-19
I fixed it myself. Ok first make sure wireless is turned on in the bios (my big mistake as the hardware couldn't be seen). After boot up. Then go to goggle on a different pc, download ndiswrapper packages and transfer them to usb. Afterward go to google and get the ralink 2860 WINDOWS XP DRIVER (big step, vista driver does not work). Install it, go into the program files directory and copy the driver onto the usb. If you dont have a pc with windows xp I can send you the ralink xp driver (pm me for it). Then install ndiswrapper. Put the driver file onto the desktop, then open the terminal and cd into it (cd /home/<urusername>/Desktop/Driver. Then keep going until you get to the folder with RT2860 . inf file (it could be a diff name, but it must be .inf). Then type in console sudo ndiswrapper -i filename.inf . Then reboot and you should be good to go. Afterward I was able to simply update via the manager and build-essential was downloaded automatically.

---

### Post by Askrates on 2008-07-26
Thanks for the tip. However, for me to get it to work, I needed to do the following:
```

sudo ndiswrapper -m
sudo ndiswrapper -ma && sudo ndiswrapper -mi

```

And then it worked after reboot. Anyway, I am off to surf the net on my 901 :)

---

