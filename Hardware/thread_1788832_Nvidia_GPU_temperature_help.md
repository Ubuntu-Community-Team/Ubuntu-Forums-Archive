---
title: "Nvidia GPU temperature help?"
date: 2011-06-23
forum: Hardware
---

### Post by deskman on 2011-06-23
I have Gigabite Nvidia GTX460 1G graphics card with the 270... Nvidia driver that is the latest in ubunru repos. In the nvidia control center there is 2 power options, one is adaptive and the second is - prefer high performance. The second option runs the gpu at its full speed. But! it makes the gpu temperature jump to 50c at idle, and when compiz effects used it may jump higher.
I noticed that the fan speed stays always at 40% and there is no option to change it. the adapive power mode keeps the gpu cool about 38c but usually sets the clock speed of the gpu very low so compiz really lags. I guess that the fan speed is just not changing tegards the power mode so this is what keeps my gpu not cooled enough. Is there any option to fix it? Change the fan speed or whatever?


i5 2500k, ASUS p8p67 m3 pro, Gigabyte nvidia gtx460 1G, 2x4 ddr3 ram

---

### Post by DanneStrat on 2011-06-23
> **deskman said:**
> But! it makes the gpu temperature jump to 50c at idle, and when compiz effects used it may jump higher.
I noticed that the fan speed stays always at 40% and there is no option to change it. the adapive power mode keeps the gpu cool about 38c but usually sets the clock speed of the gpu very low so compiz really lags.

Don't worry too much about it. You're using the nvidia driver v.195, right?

The temperatures are incorrectly reported in this driver version. I remember when I first installed lucid, I noticed the reported temperature so I looked it up and found out it was a bug. So if everything works properly you don't have to worry about it. If you do need accurate temperature reporting you can get newer nvidia drivers by adding the x-swat ppa to your software sources. Note however that these drivers have not been as thoroughly tested as the one in the ubuntu repository so it may not work for you.

If you're still interested, here's how you add the ppa:

Open terminal and do:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates && sudo apt-get update
```

Now you can get the new driver from "hardware drivers" or synaptic.

I don't know if it's really needed, but you can always uninstall the old driver version before installing the new one to keep it clean.

Good luck.

---

### Post by deskman on 2011-06-23
mate, i don't use lucid lynx anymore, i'm on natty and it has the 270 driver, not 195. help!!!!!!!!!!!!!

---

### Post by DanneStrat on 2011-06-23
> **deskman said:**
> mate, i don't use lucid lynx anymore, i'm on natty and it has the 270 driver, not 195. help!!!!!!!!!!!!!

Sorry I misinterpreted your post. I was not sure if natty used the 195 driver.

Sometimes values reported may be inaccurate so you have to keep that in mind.

> But! it makes the gpu temperature jump to 50c at idle, and when compiz effects used it may jump higher

How high does the temperature rise if you push the card?

And when you do push it, do you hear the fan speeding up?

I had a look around and found this post in the nvidia forums:

[http://forums.nvidia.com/index.php?showtopic=183957](http://forums.nvidia.com/index.php?showtopic=183957)

It is a possibility that some batches of 460 cards run hotter than others as you can see from that thread (manufacturing fault maybe?).

---

