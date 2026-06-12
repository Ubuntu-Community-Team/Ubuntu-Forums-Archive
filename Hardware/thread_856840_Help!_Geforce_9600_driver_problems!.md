---
title: "Help! Geforce 9600 driver problems!"
date: 2008-07-11
forum: Hardware
---

### Post by Paladiamors on 2008-07-11
Hi guys, I'm having a real tough time getting the video card working well on the computer. Some help would be nice.

Specs:

OS: Ubuntu 8.04.1
Motherboard: GF8200A
Video Card: MSI Geforce N9600GT 512 MB
RAM: 4 GB
CPU: AMD 5200+ dual-core

1. Cannot use restricted drivers

System -> Administration -> Hardware Drivers

No check box listed to use restricted nvidia driver
I looked up this [page]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Ubuntu%208.04%20Hardy%20Heron") at help.ubuntu.com but it wasn't helpful with my problem

2. Low resolution only from downloaded nvidia drivers from nvidia's site

Went [here]("http://www.nvidia.com/object/linux_display_amd64_173.14.09.html") next to get drivers from nvidia. Downloaded them and did the install. 

Ie:

ctrl+alt+F1
/etc/init.d/gdm stop
sh NVIDIA.... (name of driver file)
/etc/init.d/gdm start

screen flickers 3 times, fails to run the driver and goes into low resolution mode. I try to choose the "NV" driver and set the screen resolution to 1280x1024. The screen gets some garbage for the top 1/3 of the screen and the rest of the screen is jumbled up. I am forced to use the preinstalled "nvidia" on the computer instead.

3. Cannot use dual-monitors

I have an additional LCD monitor, both are capable of DVI input. Plugging both monitors into the Geforce 9600 yields a blank screen *after* ubuntu boots up. BIOS and POST screen comes up fine. 

I am new to ubuntu and been with Windows to try out something new... Been working at this problem for the past 2 days, looking up webpages and trying to install the drivers. Any good leads or a solution would be greatly appreciated.

Thanks

---

### Post by Paladiamors on 2008-07-12
bump

---

### Post by w116tjb on 2008-07-21
Try this out: [http://ubuntuforums.org/showthread.php?t=863205](http://ubuntuforums.org/showthread.php?t=863205)

Can't confirm if it works or not though.

---

### Post by johnnybg00de on 2008-07-28
I finally got my card workin with NVIDIA's drivers using the manual installation described [[COLOR="Sienna"]here[/COLOR]]("https://help.ubuntu.com/community/NvidiaManual").

The only missing step in that process is getting the driver to load on startup. The process is described in [[COLOR="Sienna"]this[/COLOR]]("http://wiki.debian.org/NvidiaGraphicsDrivers#Libraries") how-to, or you can simply follow these quick steps:
1) force the driver to load on startup:
```
$ grep -q ^nvidia /etc/modules || echo nvidia >> /etc/modules
```
you'll probably get an error like /etc/modules permission denied, so just do
```
$ sudo gedit /etc/modules and add a line containing nvidia
```
2) load the driver:
```
$ modprobe nvidia
```
3) restart the X server:
```
$ invoke-rc.d gdm restart
```
if X server doesn't come back up right away you can run
```
$ sudo /etc/init.d/gdm start
```

Hope this helps

---

### Post by R0bbie on 2008-11-18
hi, I really need ur help here... i recently bought N9600gt T2D512 n ever since I have problems playing games. every game I install is showing same problem, my monitor n computer went to hibernation or stand by and only I can do is to restart my computer:(.
btw I'm using windows XP n latest drivers for this card, however people already suggested me to use Windows vista with this card, but I dont like that solution, I would stay at XP as long as possible:).
so, if any1 can help me and already solved this problem please let me know asap, thnx in advance

---

### Post by Rocket2DMn on 2008-11-18
Thread closed for necroposting/hijacking.  R0bbie, please start a new thread in the [Windows Discussions]("http://ubuntuforums.org/forumdisplay.php?f=170") area of [Other OS Talk]("http://ubuntuforums.org/forumdisplay.php?f=147").

---

