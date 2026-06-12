---
title: "Wireless problems - on a fujitsu amilo 2727 running Intrepid Ibex"
date: 2008-11-03
forum: Hardware
---

### Post by mattbrad on 2008-11-03
Evening,

I've just bought a Fujitsu Siemens Amilo 2727 which came pre installed with vista, and i am trying to get Ubuntu up and running on it. I had a live CD of Gutsy Gibbon so i installed that and then upgraded to hardy, then to ibex.

The install went fine, minus the wireless card not working. The reason being, is that wireless is disabled on start up, pressing a hotkey gets it working in windows, but not in ubuntu. 

I've followed these steps to no avail. [http://ubuntuforums.org/showthread.php?t=644899](http://ubuntuforums.org/showthread.php?t=644899) 

Although i did get a few errors when i was trying to make/make install the madwifi file?!? So i went to the madwifi site and used one of the other ones i found?! Could that be the problem?

If anyone has any ideas on how to get this working, id be gratefull. Im pretty new to all this ubuntu set up!!

---

### Post by iliaarpad on 2008-11-12
I seem to have the same problem. The button that should turn wireless on/off doesn't seem to do anything.

---

### Post by zcats on 2009-01-11
Think you need to swithch wireless on. open terminal and type
>sudo modprobe fsam7400 radio=1 
#Does it work now (should also see LED come on)
This is not permanent though&#8230; you have to do this every time you reboot. To make it permanent, do this: NB #are instructions, and > is what you enter in a enter in terminal:

>sudo gedit /etc/modules 
#insert on a new line
fsam7400
#Save the file
>sudo gedit /etc/modprob.d/options 
#insert on a new line
options fsam7400 radio=1
#Save the file
>sudo reboot

---

