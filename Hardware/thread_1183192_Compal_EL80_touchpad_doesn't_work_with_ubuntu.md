---
title: "Compal EL80 touchpad doesn't work with ubuntu"
date: 2009-06-09
forum: Hardware
---

### Post by citm on 2009-06-09
Hey everyone!

I've just tried out Ubuntu today and I spent all day long trying to get to know it a bit and also trying to install the drivers.  I was able to succeed in installing the Nvidia and Realtek drivers but unfortunately the touchpad doesn't work.  The two buttons used to work though until I did something that I found on google and now they don't even work anymore.

I also did something to download the Touchpad application but everytime I choose it, an error message appears saying GSynaptics couldn't initialize, you gotta set SHMConfig true in xorg.conf.  But I already did this (maybe not correctly though...) and still not working.

I hope you could could help me.

Cheers,
Mark

p.s. if you could help me install other hardwares as well, like my computer's mic, webcam, the buttons on the side and on the top of my keyboard and what not...

---

### Post by Aeromousikos on 2009-06-15
I found where the solution is! 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/315882](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/315882)

and toward the bottom the magic fix:

            [Ricardo Faria]("https://bugs.launchpad.net/%7Ericardomiguelfaria")          wrote     on 2009-03-31:     [              (permalink)     ]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/315882/comments/33")   
                   i solved my non working touchpad by doing in terminal:
       modprobe -r psmouse
      modprobe psmouse proto=imps
 

at this time the touchpad should be working
 and add:  options psmouse proto=imps
to:  gedit /etc/modprobe.d/options

-------------
I had to super-use in order to get modprobe to work. At your dos prompt type: su then enter your super-user password which you set up when you initially configured ubuntu on your machine. If you didn't do that or don't remember, go to your system->administration->users&Groups and add user root   .   

~David

---

