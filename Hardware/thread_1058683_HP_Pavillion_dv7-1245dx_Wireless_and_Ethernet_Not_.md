---
title: "HP Pavillion dv7-1245dx Wireless and Ethernet Not working Ubuntu x64"
date: 2009-02-03
forum: Hardware
---

### Post by Herzchell on 2009-02-03
Good Morning!, As the tread's title states i have not been able to get this two things working, I currently have the Notebook Plugged to the Modem using the RJ-45 CAT5 cable, this model has a sort of touch pad or something with the volume power and wireless led on it, For some reason only the Wireless one stays red, I cannot connect to the internet even with te Laptop hardwired to the modem, Ive tried using Windows drivers also. Any help would be appreciated, Im using Ubuntu 8.10 x64 by the way

---

### Post by Herzchell on 2009-02-04
Bump

---

### Post by greaser_nc on 2009-02-19
Same problem here. Wired or wireless, no internet connection using 8.10. I've tried both the 64 bit and 32 bit versions to no avail.

---

### Post by Herzchell on 2009-02-20
Im still looking for a suitable 64 bit based ubuntu Distro for my model, any recommendations?

---

### Post by mredding on 2009-02-22
There's a possible solution found here:
[http://ubuntuforums.org/archive/index.php/t-977179.html](http://ubuntuforums.org/archive/index.php/t-977179.html)

(Summary: sudo aptitude install linux-backports-modules-intrepid-generic and activate this driver instead of the other one)

Seems to be a common problem though:
[http://kmandla.wordpress.com/2009/02/14/ubuntu-810-on-an-hp-pavilion-dv7/](http://kmandla.wordpress.com/2009/02/14/ubuntu-810-on-an-hp-pavilion-dv7/)

---

### Post by FoxIII on 2009-03-12
Just to keep some people informed, I have an HP Pavillion dv7 laptop, and using the above recommendations (and the thread that is linked above) I have wireless working perfectly.

Ethernet seemed to work 'out-of-the-box'. Thanks for that! :D

---

### Post by sixthcrow on 2009-06-28
Hi, I am running one of the HP DV7 laptops as well and have been having an issue getting the wireless working. I have tried following the instructions above but I keep getting errors regarding the command "apt-get install linux-backports-modules-intrepid-generic". 

~$ sudo apt-get install linux-backports-modules-intrepid-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-intrepid-generic

Would anyone be able to give me some assistance with this? It would be greatly appreciated. 

Thanks

---

### Post by timelord22 on 2009-06-30
Upgrade to 9.04 it works fine on mine other than some graphics problem that I can live with for now.  Just a dot scrolling up the screen...

---

### Post by mrjane on 2009-07-09
> **timelord22 said:**
> Upgrade to 9.04 it works fine on mine other than some graphics problem that I can live with for now.  Just a dot scrolling up the screen...
I had the same problem and fixed it with installing fglrx video driver for ATI (pressuming that you have ATI Radeon graphic card) works great with Compiz too :).
I followed these instructions [here]("http://ubuntuforums.org/showthread.php?t=1133950").

---

