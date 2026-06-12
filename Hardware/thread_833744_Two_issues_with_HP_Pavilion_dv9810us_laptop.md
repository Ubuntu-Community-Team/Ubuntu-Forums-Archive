---
title: "Two issues with HP Pavilion dv9810us laptop"
date: 2008-06-18
forum: Hardware
---

### Post by Brian Hogan on 2008-06-18
I just installed Ubuntu Studio on my HP Pavilion dv9810us laptop, and I have two show-stopping hardware issues:

First, my ethernet device, which is an Atheros chip (I'm not sure what; lspci says it's an AR242x, but I've read elsewhere that Hardy misdetects this chip), is unable to configured. wlan0 is not even listed as a device, and when I add it to /etc/network/interfaces and do sudo /etc/init.d/networking restart, it says that such a device doesn't exist.

Second, my video, which is an nVidia GeForce 7150M, will not go higher than 800x600 resolution on a 17" laptop whose native resolution is 1440x900! Quite unpleasant. I tried setting the mode manually in xorg.conf, and this does nothing. I tried setting the driver to nv, at which point Xorg fails to even load.

Any help toward rectifying either of these issues would be very greatly appreciated!

---

### Post by sergiom99 on 2008-06-19
I have the same video card and just enabling the restricted drivers worked fine for me in HH. (In GG I had to install drivers using envy)
My screen is 15.4" so my resolution is 1280x800 or something like that.

About the wifi I have a Broadcom, cant tell you much about your chip.

---

### Post by ravl on 2008-06-19
Hello. I had the same "problems" when installing Ubuntu on my HP dv6810, but all it takes is some configuration.

For the wifi card:
[http://blog.linuxoss.com/2008/05/08/ubuntu-804-enabling-atheros-ar5007-based-wireless/](http://blog.linuxoss.com/2008/05/08/ubuntu-804-enabling-atheros-ar5007-based-wireless/)
The madwifi drivers don't work on 64-bit platforms.

For the Nvidia card (mine is the same):
```
sudo aptitude install envyng-core
sudo envyng
```
It will download all the packages required for the card and install them.

---

### Post by Brian Hogan on 2008-06-20
Thanks, I tried doing an iwconfig, and it says I have no wireless connections. Also my wireless led is still red. Any suggestions?

---

### Post by Dv6704 on 2008-06-20
> **Brian Hogan said:**
> Thanks, I tried doing an iwconfig, and it says I have no wireless connections. Also my wireless led is still red. Any suggestions?
]Hi!, I have a Hp Dv6704 laptop, I also am having the same problems. cant connect wirelessly, (also the little LED that is blue when the wireless is in use(on), and red when it is off) and also same the same with the 800 by 600. 

Windows Vista Premium SP
2048 MB ram
AMD 
Nvidia

---

### Post by sergiom99 on 2008-06-20
> **Dv6704 said:**
> ]Hi!, I have a Hp Dv6704 laptop, I also am having the same problems.

Not sure your laptop's specs, but you might want to drop by this excellent howto I used to configure mine.
[http://ubuntuforums.org/showthread.php?t=575750](http://ubuntuforums.org/showthread.php?t=575750)

good luck.

---

### Post by JB_1980 on 2008-08-14
I have the same laptop (hp dv9810us) that had the same issues. I found quick solutions though. To solve the display problem I just went to system>administration>hardware_drivers, and then enabled the nvidia driver, after restart the screen is great.
To solve the wireless I found an excellent how to:

[http://ubuntuforums.org/showthread.php?t=792158&highlight=atheros](http://ubuntuforums.org/showthread.php?t=792158&highlight=atheros)

I just copied and pasted the code line by line into the terminal, and now my hp is running ubuntu great. Hope it works for everyone else with the HP dv9810us and similar laptops.

---

### Post by BrianElliott0218 on 2008-11-16
> **JB_1980 said:**
> 

I just copied and pasted the code line by line into the terminal, and now my hp is running ubuntu great. Hope it works for everyone else with the HP dv9810us and similar laptops.

Need some sound help on the dv9810us as well.  I resolved the Atheros Wireless issue, and the NVidia driver issues right away after installation, and all else worked fine, until a couple of weeks ago (when I upgraded to II from HH), and my sound buttons just stopped working.

On first installation and after fixing wireless and video, everything was great.  I did the upgrade to 8.10 from 8.04, and the sound doesn't react to the buttons at all.  The sound slider window pops up and everything, but the sound doesn't change, not even mute.  Any suggestions?

I've tried several of the sound fixes, but none of them have worked, and besides, the sound does come up when I play a video, or listen to Pandora, it's just that the sound has to be changed on each applications control panel instead of with the "master controls"  which do nothing but change visibly.

If nothing else, is there a way to revert back to 8.04?  It was working great!

Thanks for any help you can provide,
~BE

---

