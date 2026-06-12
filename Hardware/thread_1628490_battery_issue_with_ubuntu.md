---
title: "battery issue with ubuntu"
date: 2010-11-22
forum: Hardware
---

### Post by pternet on 2010-11-22
Hi all!
I have a Toshiba a300-22z laptop, and my problem is that under ubuntu, if its running on battery it only lasts for ~1 and a half hours, whereas if I run Windows 7 it can do 2 and a half hour. Is there some sort of trick with which I can extend the battery life? It would be really crucial, as I need at least 2 hours of battery time before I can charge it. I really like linux and ubuntu and I wouldn't like to go back to windows.

---

### Post by Fafler on 2010-11-23
Right click on the gnome panel, select add to panel and and the CPU frequency scaling monitor. Now you can force the CPU to either it's highest or lowest aviable frequency depending on what you need. Or let Ubuntu control it depending on CPU load.

It might also be possible to enable it for your graphics card, but i have no experience with ATI cards like yours. Are you using the default open source driver or the closed 3rd. party driver from ATI? You could maybe get an improvement just by changing. I know the open source driver have some issues with power saving on older Radeon chips and it might be the case with your hardware too.

---

### Post by pternet on 2010-11-23
Thank you, I will try the 3rd party Ati driver, i hope this helps, beacuse I've the CPU scaled down, I use ondemand policy for both cores. I have powertop installed and it disabled quite a lot of things and did some tweaks, the brightness on the minumum and the bluetooth turned off. Still my lapotop consumes 26 W, and it gives me and a half hour of battery power.

---

### Post by pternet on 2010-11-23
i have downloaded and installed graphic driver from ati site. it helped a bit but still my laptop, according to powertop, counsumes 23 to 26 W compared to windows which did around 17 W

---

### Post by Fafler on 2010-11-23
Can you adjust the GPU and memory speed from the ATI control panel? Thats possible with the Nvidia counterpart.

---

### Post by pternet on 2010-11-23
no, I can't adjust it

---

### Post by theSuperman on 2010-11-23
Install powertop to see your usage. Itll also show what programs are using the most CPU cycles. 
Install powertop:
```
sudo apt-get install powertop
```
run powertop from the terminal:
```
sudo powertop
```
After 15 seconds or so, it'll display your current power usage (must be running on battery - aka:disconnect power cable from your computer) and your wakeups-from-idle per second. Chrome has always been a large cause for wakeups. You can try lowering your brightness, disabling wireless, etc and see if that decreases your  power usage. 

Also, the program will display some helpful hints to try and maximize power usage.

---

### Post by theSuperman on 2010-11-23
> **theSuperman said:**
> Install powertop to see your usage. Itll also show what programs are using the most CPU cycles. 
Install powertop:
```
sudo apt-get install powertop
```
run powertop from the terminal:
```
sudo powertop
```
After 15 seconds or so, it'll display your current power usage (must be running on battery - aka:disconnect power cable from your computer) and your wakeups-from-idle per second. Chrome has always been a large cause for wakeups. You can try lowering your brightness, disabling wireless, etc and see if that decreases your  power usage. 

Also, the program will display some helpful hints to try and maximize power usage.

Oops, sorry, I didn't read that you tried powertop already. :(

---

