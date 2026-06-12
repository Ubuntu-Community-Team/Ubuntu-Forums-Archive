---
title: "Activating Nvidia drivers"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by Dracona on 2009-10-10
Hello,
       I have been trying to activate the Nvidia driver version 180 (recommended) with no luck. everything goes good until i reboot. the system then hangs up at "checking battery state" i have read a few posts simular to this in the forums, but have had no luck so far. i have even tried downloading the driver from nvidia, but my Linux abilities are not good. i have tried it on ubuntu 32bit, kubuntu 32 and 64 bit ( all 9.04 ) every time i try, i start with a fresh install. 
system specs are,
Ubuntu 9.04 ( 32 Bit )
AMD Athlon 64 X2 6000+
Asus crosshair Mother board
4 gig corsair ram
2 geforce 8800 gts gpu
74gb WD raptor HD
I will not give up on this, but i do need some help. let me know what other info is needed
Thank you

---

### Post by SuperSonic4 on 2009-10-10
Hello.

---

### Post by wojox on 2009-10-10
**[size="3"]hello[/size]**

---

### Post by Dracona on 2009-10-10
If i was to install a earlier version of ubuntu, maybe 8.04,then activate the nvidia drivers, then upgraded to 9.04, would it break the nvidia driver?

---

### Post by Mark Phelps on 2009-10-10
Restricted video drivers are tied to the version of the kernel; thus, before a major kernel upgrade, you are recommended to uninstall restricted drivers.

Once you upgrade to the new kernel, you should then have access to the latest appropriate restricted drivers.

---

### Post by Meow27 on 2009-10-10
you should download the latest driver from nvidia
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

after you have that. follow this guide

[http://ubuntuforums.org/showthread.php?t=57368](http://ubuntuforums.org/showthread.php?t=57368)



though you may want to unisntall your current driver

---

### Post by presence1960 on 2009-10-11
from ubuntu open a terminal and run these commands:

```
sudo apt-get install envyng-core
```

&

```
sudo apt-get install envyng-qt
```

You can then find Envyng in your Applications menu or from terminal run ```
envyng -t
```
and follow the prompts to install Nvidia driver.

---

### Post by Meow27 on 2009-10-11
and CAN screw with your kernel, i reccomend you use my way before using envy

---

### Post by AllenGG on 2009-10-11
Hola Dracona !    look at what Meow27 has to say.  I've had problems recently with Envyng, seems to goof up, why ??
But, you are running a 32 bit version of Ubuntu on a 64 bit machine.
I have the 64 bit version installed on 2 machines, one is 6 years old. Both have NVidia chip video cards.
Honestly suggest you backup data and upgrade to the newest 64 bit version.

---

### Post by presence1960 on 2009-10-11
> **Meow27 said:**
> and CAN screw with your kernel, i reccomend you use my way before using envy

totally untrue! That is why it is in the repositories- it is tested to be safe with Ubuntu.

Personally it does not matter to me which way the OP gets his Nvidia driver working. Go ahead use **_HIS_** way.

Have used Envyng on 32 bit 8.04. 64 bit 8.04,8.10 & 9.04 and Mint 5 64 bit. have never had a problem.

---

### Post by Dracona on 2009-10-12
sorry for not getting back to this sooner, but thanks to everyone who responded.
I have tried envy with no luck.
i will give the 64bit a go, and then try what meow27 suggested.

thx again to everyone

---

### Post by Meow27 on 2009-10-12
@presence1960

then i stay corrected, but i remember when it wasn't available in the repos

does envy give the latest driver?

---

### Post by Dracona on 2009-10-18
Hello again, just came back to report, that i now have nvidia drivers installed.
i am running ubuntu 8.04 64bit. install was straight forward and very very easy. 
only thing, i dont think its the latest version. i am thinking it is 169.xxx or something close.

gonna dig around and see how to tell what version i have, and see about installing the latest drivers. 


man 64bit is faaaassst!

windows sucks

---

