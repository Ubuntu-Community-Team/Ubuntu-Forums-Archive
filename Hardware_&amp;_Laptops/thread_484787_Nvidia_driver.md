---
title: "Nvidia driver"
date: 2007-06-26
forum: Hardware &amp; Laptops
---

### Post by Microlife on 2007-06-26
Hi,

I'm a new user in linux world and i have a new pc and this is the pc info:

Motherboard : ASUS m2nbp-vm CSM
Processor : AMD 64 Athlon X2 3200+
Ram : Kingston 1024Mb x2
HDD : Maxtor 160GIG Sata

Ubuntu 7.04 installed perfectly, but some problem in graphic card.

I can't run any program by openGL and i don't have many resolutions.

The graphic card info:
Nvidia Quadro NVS210S / nvidia Geforce 6150le

This card on board.

Please.............. i need the driver.

Thanks

---

### Post by sargeras on 2007-06-26
Have you tried installing the "linux-restricted modules" for your kernel version?  I have installed all my nVIDIA cards this way. 

 ```
$ uname -r 
$ sudo apt-get install linux-restricted-modules-'uname-r'
```

If you want to use the GUI, open adept_manager and search for the correct linux restricted modules.

That should install the restricted modules.

then do the following (if you don't like vi, then use another editor)

```
$ sudo vi /etc/X11/xorg.conf
```

find the section about graphics driver and change it from 'MESA' to nv.  

this should give you openGL.

hope this helps

---

### Post by BobLand on 2007-06-26
My card is a bit older, GeForce 7300.  I tried the driver from the nVidia site but it didn't work.  Reading a few posts advised to search thru synaptic for nvidia and try those drivers, which I did.

Don't remember which one I used.  I believe there are 3.  I'd say try the legacy one first.  If it works, it will do the whole shebang for you.  I think if you install the other drivers, synaptic will remove the prior ones.

In the Device section of your xorg.conf you can also try using
```
Driver   "nvidia"
```
but there are a lot of other factors that need addressing.  That's why trying the synaptic drivers may resolve your problem...maybe not.

The xorg.conf that I use employs all defaults.  The only changes are screen modes which are unique to my monitor, my monitor type and changes I made for my MX510 mouse.

Be careful about changing xorg.conf.  Make sure you have a backup that is as close to the original as possible.  If you screw up (which you will someday) and are thrown into the command line, first thing is to restore your xorg.conf with the original.  That usually fixes 90% of interface problems.

bobland

---

