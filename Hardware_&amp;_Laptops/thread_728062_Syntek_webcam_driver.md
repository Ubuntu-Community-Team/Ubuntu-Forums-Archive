---
title: "Syntek webcam driver"
date: 2008-03-18
forum: Hardware &amp; Laptops
---

### Post by CoffeeBreath on 2008-03-18
I have the driver and did the following:

$ make
$ sudo modprobe videodev
$ sudo modprobe v4l1-compat
$ sudo insmod stk11xx.ko
 
([COLOR="RoyalBlue"]the insmod line won't work unless I'm in the Stk... directory.) The others I can do from home.[/COLOR]

gksu gedit /etc/modules:
videodev
v4l1-compat
stk11xx.ko ([COLOR="RoyalBlue"]was it necessary to add this one?[/COLOR])

gksu gedit /etc/rc.local:
home/<my user name >/syntekdriver/trunk/driver/st k11xx.ko

As of now the syntek driver is located on my desktop so this line:"
gksu gedit /etc/rc.local:"
 is actually
/home/my name/Desktop/stk11xx-1.3.1/st k11xx.ko

After running all of these commands in order i can get the camera to turn on. But, how can I get it to turn itself on after reboot? Should I have untarred the module in another directory?

---

### Post by CoffeeBreath on 2008-03-18
Solved- slightly....
It loads on boot now.

**But**

1.But why was I able to use different directories for the insmod and modprobe commands initially?

2.Is there a more appropriate place to put this driver?

could someone also explain what these commands are doing?

---

