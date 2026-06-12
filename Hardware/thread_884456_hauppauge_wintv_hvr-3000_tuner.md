---
title: "hauppauge wintv hvr-3000 tuner"
date: 2008-08-09
forum: Hardware
---

### Post by Dopan on 2008-08-09
trying to get this card working a bit lost in the whole install process..

Ive downloaded both mythbuntu and ubuntu 8.04 (with the idea of installing mythtv on top) (tried separately of course) but having issues with the tuner. have search forum and net a couple times but coming up blank:confused:. 

is there any where thats says what this card requires to get up and running.. there is something there that the install process detected but when trying to test with dvbtune its sorta like its trying to use dvb-t instead of dvb-s?

appreciated any help.. 

thanks

---

### Post by rxstephen on 2008-08-11
Gidday,

I'm afraid I don't have a direct answer because I have only just ordered my hardware, but I plan on using the HVR3000 and have found the following links that look to be very informative.

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-3000](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-3000)
[http://dev.kewl.org/hauppauge/](http://dev.kewl.org/hauppauge/)
[http://www.mythtvtalk.com/forum/viewtopic.php?t=4460](http://www.mythtvtalk.com/forum/viewtopic.php?t=4460)

It appears to me that you are not seeing both the DVB-S and DVB-T because mythtv does not recognise the hybrid devices as being separate (although you can only run one at a time).  The above links will help recognise the devices.

An important part is to create the /dev/adapter links so that you end up with two devices that mythtv can use.  But these links are lost every time you boot so make sure you write an rc script to create the links at boot up.  Have a look at the 4th page on the mythtvtalk forum link above.

Cheers
Stephen

---

### Post by Dopan on 2008-08-12
> **rxstephen said:**
> Gidday,

I'm afraid I don't have a direct answer because I have only just ordered my hardware, but I plan on using the HVR3000 and have found the following links that look to be very informative.

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-3000](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-3000)
[http://dev.kewl.org/hauppauge/](http://dev.kewl.org/hauppauge/)
[http://www.mythtvtalk.com/forum/viewtopic.php?t=4460](http://www.mythtvtalk.com/forum/viewtopic.php?t=4460)

It appears to me that you are not seeing both the DVB-S and DVB-T because mythtv does not recognise the hybrid devices as being separate (although you can only run one at a time).  The above links will help recognise the devices.

An important part is to create the /dev/adapter links so that you end up with two devices that mythtv can use.  But these links are lost every time you boot so make sure you write an rc script to create the links at boot up.  Have a look at the 4th page on the mythtvtalk forum link above.

Cheers
Stephen

thanks for the info:) yeah i think your right its only seeing the dvb-t head at this stage and i need to somehow add the others. i only want to use the dvb-s side of it. ill check your links out and see what i can see. let me know when you hardware arrives and how you get on. 

many thanks
scott

---

### Post by rxstephen on 2008-08-13
I got hold of just the HVR3000 yesterday and tried it out in my PC, still waiting for the HTPC hardware.
Also found this [http://wiki.linux.net.nz/FreeViewMythTvSetup](http://wiki.linux.net.nz/FreeViewMythTvSetup) which is pretty spot on for getting the DVB-S working.

I went through the steps on linuxtv.org and then added the rc script as mentioned in the mythtvtalk forum with one exception.  To get the rc script to run at boot up you need to put it in /etc/rc2.d, so the last step I did:
ln -s /etc/init.d/add_dvb_links /etc/rc2.d/S20add_dvb_links

All works brilliantly... can't wait to get my actual HTPC installed!

Cheers

---

