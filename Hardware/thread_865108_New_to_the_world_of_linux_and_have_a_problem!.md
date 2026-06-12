---
title: "New to the world of linux and have a problem!"
date: 2008-07-20
forum: Hardware
---

### Post by dub268 on 2008-07-20
Hi guys ive made the leap across to Linux after been a slave to windows.
Ive just installed the Ubuntu 8.04 onto my Amilo M7400 laptop and i have one or two slight problems, i cant get my hot keys to work and i cant get my wireless to switch on so at the min im hard wired into my router,is there anything that help me on my way please, thanks

---

### Post by sanhome on 2008-07-21
Same for me dude :(
I've tried to follow steps provided here:
[http://ubuntuforums.org/showthread.php?t=189540]("http://ubuntuforums.org/showthread.php?t=189540")
However I'm still far away from success, heh !
But I hope to solve it. 
Please pay attention on message from page 8 in this thread, cause there is important info re compilation of fsam4700 driver.

Hope we can solve this small issue.

---

### Post by DanubeRS on 2008-07-21
If theres one thing ive learn't with the transition from windows to Ubuntu. Drivers are a pain in the backside!

So i reccomend using NDISWrapper to fix your Wifi connection. As long as you still have  copy of your Wifi drivers (usually on a cd that cam ewith your pc. Can probably also be downloaded from the interwebs)

The installation is simple if you already have an internet connection active.

Simply follow these instructions:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

as for the hotkeys, sorry I cant be of any help

Hope it gets fixed

---

### Post by dub268 on 2008-07-21
I hope so to mate, ive spent all morning now trying different ways to solve this problem but getting now where im really need my laptop to be wireless as hard wired is just not good for me, everything else is spot on with linux just wireless :(

---

### Post by sanhome on 2008-07-21
> **dub268 said:**
> I hope so to mate, ive spent all morning now trying different ways to solve this problem but getting now where im really need my laptop to be wireless as hard wired is just not good for me, everything else is spot on with linux just wireless :(
You know, its actually so simple as one - two - three... :)
I've realized that fsam4700 SW RF kill switch as well as ipw2200 driver already provided and in place with this release of ubuntu.
Thus we just needed to use it :)
Try the following:
1. open up console
2. type **sudo modprobe fsam7400**
3. check if driver is running by typing 
cat /proc/driver/wireless/radio

you should see something like that:
SW RF kill switch for Fujitsu Siemens Amilo M 7400, v0.4.0
  auto-off is ON, auto-load is OFF
  radio state is ON

if it is up and running then you can easily connect to your wireless network by using network icon in tray.

now you can add couple of lines in two files:
1. in console type **sudo nano /etc/modules** and add line in that file:
fsam4700 autoload=0 radio=1
2. create new file /etc/modprobe.d/ipw2200
and add one line there :
options ipw2200 led=1

now you can restart your laptop and see that wifi led is switched on and you can connect to your wireless network.

Hope this can help you.

Good luck.

---

