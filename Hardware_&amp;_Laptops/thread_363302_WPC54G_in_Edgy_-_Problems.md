---
title: "WPC54G in Edgy - Problems"
date: 2007-02-16
forum: Hardware &amp; Laptops
---

### Post by VeganZombie on 2007-02-16
Hey guys. After alot of reading I'm unable to get my wireless card up. I'm using Ubuntu 6.10 and the WPC54G v1.2.

I've used ndiswrapper to apply the latest Linksys patch. However there are a few issues that I've run into. According to a few of the guides I've read, I'm supposed to run

"echo ndiswrapper >> /etc/modules"

But I get a permission denied error. And when I try to scan using 

"iwlist eth1 scan"

I get "no scan results" or something similar.

dmesg always replies with an error : "bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed"

Perhaps there's a certain driver I'm supposed to use? I don't know. I got wireless running perfectly in 6.06 but after the upgrade I did, wireless seems to be a pain to configure.

Any ideas?

---

### Post by nachotronics on 2007-02-18
> **VeganZombie said:**
> I'm supposed to run

"echo ndiswrapper >> /etc/modules"

But I get a permission denied error.

Did you try
```
sudo echo ndiswrapper >> /etc/modules
```

or instead of that you could try
```
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```

And then do the scanning:
```
sudo iwlist scanning
```

Also, i don't know your wireless card, but i had to install mine with ndiswrapper also, in my case i had to blacklist the "bcm43xx" module because it didn't support my card, which has a broadcom 4311 chipset. Perhaps if the above doesn't solve your problem you could blacklist "bcm43xx" so it doesn't get loaded and after that install the windows driver with ndiswrapper...
If you want to block bcm43xx from loading:
```
sudo echo blacklist bcm43xx >> /etc/modprobe.d/blacklist
```

Good luck!

---

### Post by VeganZombie on 2007-02-18
> **nachotronics said:**
> Did you try
```
sudo echo ndiswrapper >> /etc/modules
```

or instead of that you could try
```
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```

And then do the scanning:
```
sudo iwlist scanning
```

Also, i don't know your wireless card, but i had to install mine with ndiswrapper also, in my case i had to blacklist the "bcm43xx" module because it didn't support my card, which has a broadcom 4311 chipset. Perhaps if the above doesn't solve your problem you could blacklist "bcm43xx" so it doesn't get loaded and after that install the windows driver with ndiswrapper...
If you want to block bcm43xx from loading:
```
sudo echo blacklist bcm43xx >> /etc/modprobe.d/blacklist
```

Good luck!

I have tried ```
sudo echo ndiswrapper >> /etc/modules
``` but I wasn't aware it did the same thing as ```
 sudo modprobe ndiswrapper
``` because it returns 0 errors.

I'll try blacklisting the module ASAP and I'll tell you how things go.

Thanks for your help.
-VeganZombie:biggrin:

---

### Post by fallasteeni on 2007-02-18
> **VeganZombie said:**
> I have tried ```
sudo echo ndiswrapper >> /etc/modules
``` but I wasn't aware it did the same thing as ```
 sudo modprobe ndiswrapper
``` because it returns 0 errors.

I'll try blacklisting the module ASAP and I'll tell you how things go.

Thanks for your help.
-VeganZombie:biggrin:

It doesn't do the same thing. 

echo ndiswrapper >> /etc/modules

adds the word "ndiswrapper" (without quotes) to the end of the file /etc/modules

modprobe ndiswrapper attempts to load the ndiswrapper driver (module) into the kernel


In my case I did both, but still can't get neither eth1 nor wlan0 to show up, let alone to pass an ifup :(

---

### Post by VeganZombie on 2007-02-18
Finally got it working using this guide:
[http://ubuntuforums.org/showthread.php?t=340689&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=340689&highlight=BCM4306)

Blacklisting 43xx definitely was a part of the process. :biggrin:

To above: Use lspci to find exactly what chipset you're using (in my case - bcm4306) and do a forum search.. perhaps the above link will help.

-VeganZombie :biggrin:

---

