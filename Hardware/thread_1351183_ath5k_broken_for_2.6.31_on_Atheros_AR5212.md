---
title: "ath5k broken for 2.6.31 on Atheros AR5212"
date: 2009-12-10
forum: Hardware
---

### Post by psycovic23 on 2009-12-10
Hi,

ath5k doesn't seem to work for my wireless card. NM-applet just sits there saying the wireless card isn't ready.  Dmesg activates just fine. iwlist says the device can't be used for scanning. In the meantime, I'm using madwifi, but I'd like to be able to use the module that's available without compiling the driver everytime for a new kernel.

---

### Post by drpjkurian on 2009-12-11
> **psycovic23 said:**
> Hi,

ath5k doesn't seem to work for my wireless card. NM-applet just sits there saying the wireless card isn't ready.  Dmesg activates just fine. iwlist says the device can't be used for scanning. In the meantime, I'm using madwifi, but I'd like to be able to use the module that's available without compiling the driver everytime for a new kernel.

Hi Psycovic

I feel that you have selected the robust driver for your wireless card. I have been using Madwifi from the period of Hardy. I went through all kernel updates as well as new release without any glitch to my wireless driver.

Please visit my thread [http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072) for the installation of drivers.

You mentioned that you would like to have a module which doesn't require any recompilation during kernel updates.
For that please note In my thread for step 4 Instead of typing the command```
sudo apt-get install linux-headers-`uname -r`
```

Type the command```
sudo apt-get install linux-headers-generic
``` 

This will take care of recompiling problems.

Thanks for my friend **kokopelli** who helped me to do this

All the best
Dr Kurian

---

### Post by psycovic23 on 2009-12-31
Unfortunately, I've been running into more and more kernel panics. This is a pretty well documented bug that has been very pervasive (blinking caps lock key at random). I had this problem once on .27 and upgraded to .30 (I think) with the ath5k driver and it went away. Now with .31, I get kernel panics that are much less frequent, but still there nonetheless, though I can't tell where they're coming from - maybe not from the network driver at all. Hence my desire to try out ath5k.

---

