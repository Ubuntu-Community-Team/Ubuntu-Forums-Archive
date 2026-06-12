---
title: "Unable to configure screen resolution"
date: 2008-05-26
forum: Hardware
---

### Post by Mpkstroff on 2008-05-26
Hello everyone, im new to the forum and i have a big problem. 
I have used Ubuntu for 2 years now, i had my problems but i was always able to  solve them. A few days ago i decided to do 2 things: 1. Get me an LCD 17` Viewsonic 1703wb wide monitor. 2. Do a fresh install of Ubuntu 8.04. The big problem is that i cant configure the screen resolution to 1440x900 as the monitor supports. 
The funny thing is that when i run x with the default video drivers gets me an 800x600 resolution (max). Now when i run x with the Nvidia  propietary drivers 640x480 is the highest my screen goes. 
I tryed to edit manually xorg.conf, but had no results. Also i tryed to reinstall by several ways (synaptic, envy, etc) the Nvidia drivers, but always the same. 
What would you advice me to do? Is there anyone that could fix this? If anyone is up to give me a hand, i can provide with my xorg.conf file so we can get somewhere.

Tanks in advance to this wonderful comunity, and again, i'd really apreciate if someone can give me a hand with this.

Cheers, from Argentina!

---

### Post by dpaint4 on 2008-05-28
This is the same issue that I'm experiencing exactly. I'd also like an answer to this.

---

### Post by housam on 2008-05-28
try this way it may help


```
sudo nano /etc/usplash.conf
```
 you will got something like that 



> # Usplash configuration file
# These parameters will only apply after running update-initramfs.  



add the required resolution 


> # Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=[COLOR="red"]1440[/COLOR]
yres=[COLOR="red"]900[/COLOR]
  



OR put the settings you want for [COLOR="Red"]x & y[/COLOR] then reboot and type :



```
sudo dpkg-reconfigure usplash
```

then check for the new settings -- System > Preferences > Screen Resolution and select the new one.
__________________

---

