---
title: "have wireless working at startup without password"
date: 2008-08-17
forum: General Help
---

### Post by Woody1987 on 2008-08-17
Every time i boot my laptop i have to type in my root password in order for the wireless to connect. I am not sure why this is or even if its normal, but i would like not to have to. How do i go about this if its possible?

---

### Post by eggdeng on 2008-08-17
You're right, it shouldn't happen. A quick & dirty workaround would be to run
```
gksudo gedit /etc/rc.local
```
and add the line
```
ifup wlan0
```
just above
```
exit 0
```
Save, exit and reboot.
This is assuming that your wireless interface is wlan0. If you aren't sure, you can check by running the command ```
ifconfig
``` in a terminal.

---

### Post by Woody1987 on 2008-08-17
Doesnt seem to work, i ran ifconfig and it said i was using eth1 so i used that, that didnt work so i used wlan0. that didnt work either. Thanks for helping anyway

---

### Post by eggdeng on 2008-08-17
Sorry, typo in my post. It should read
```
gksudo gedit /etc/rc.local
```
The line to insert is
```
ifup wlan0
```
as you supposed.

---

### Post by Woody1987 on 2008-08-17
yea, i realised that when i tried it, still, the method isnt working unfortunately

---

### Post by Woody1987 on 2008-08-19
bump

---

### Post by cottonfox on 2010-08-07
This worked for me in lucid. 
Right click on your networking icon, select edit connections. 
Choose your wireless server that you use. Click Edit. 
At the bottom of the window select "Available to all uses."

I am no longer required to enter my root password on start-up to connect to the LAN. 

(Screenshot included)

---

