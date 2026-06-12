---
title: "Resolution problem driving me mad !"
date: 2007-08-02
forum: Hardware &amp; Laptops
---

### Post by lenx on 2007-08-02
First of all, thanks for reading this!

Now the problem is; i have a Samsung SyncMaster 913N. This worked very well in the past until i had to return it since it broke down. I still had waranty and got a new one. However he problem with this new screen i got back is that its internal firmware seems not 100% correct. It appears that it tells my PC that it cannot handle 1280x1024 resolution, although this is the native resolution of this screen !!

Now that's as clear as mountain water, here is the real problem: Since my PC is told that this screen can't have 1280x1024, it refuses to set the resolution to that value!! In Windows, i could go around this issue by forcing some values in the nvidia driver, but in ubunut, there is NO WAY to do that !!

I did everything i could, i changed all kinds of things in my xorg.conf including refresh rates and stuff like that, i used xorg reconfigure, i uninstalled and reinstalled nvidia drivers, ...
Still, i CAN NOT obtain a resolution of 1280x1024 !!! Now this drives me totally crazy! The only way to get the resolution is hook up another screen, set 1280x1024 (this gives no problems at all), remove that screen and reconnect my samsung. That gives me the correct resolution until i restart ubuntu ...

Why is it that people are programming all these fancy 3D desktops nowadays, while you still have to be a rocket scientist to do something simple as set up a screen !! For gods sake when will there be a graphical interface instead of all this fiddling in xorg.conf. Linux will never hit a broader market if they don't do something about that!

Anyway, my hope to a solution is completely lost, but if anyone knows, i'll be GLAD thank you !

---

### Post by dougfractal on 2007-08-02
I think for some reason ubuntu is not detecting you monitor model

spec from [http://prices.zdnet.co.uk/0,1000000838,23984273,00.htm](http://prices.zdnet.co.uk/0,1000000838,23984273,00.htm)

backup
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.`date +%Y%m%d`
```

so ```
sudo gedit /etc/X11/xorg.conf
```
```
Section "Monitor"
   Identifier   "SyncMaster 913N"
   HorizSync    30 - 81
   VertRefresh  56 - 75
   Option       "DPMS"
EndSection
```


also change in the Section "Screen"

   >  Monitor        "SyncMaster 913N"

restart X
```
sudo /etc/init.d/gdm restart
```


There is always a risk of X not starting if a setting is wrong.

**troubleshoot**
[ctrl+alt+f1] 
```
sudo cp /etc/X11/xorg.conf.`date +%Y%m`* /etc/X11/xorg.conf
```
sudo /etc/init.d/gdm restart[/CODE]

---

### Post by lenx on 2007-08-02
Hi dougfractal,

Thank you for replying. However the contents of my xorg.conf were already exactly the same as you told. I searched the forums and google in the past and this is indeed what could be the solution but weird enough it doesn't help :(

---

### Post by dougfractal on 2007-08-02
This might not work and may produce "out of range", this could break older CRT's but I think  you maybe alright.
 
my xorg.conf values are 
> HorizSync       30.0 - 83.0
VertRefresh     50.0 - 76.0
for a "HP vs17" and I get 1280x1024.

also check the logs
```

less /var/log/Xorg.0.log
```
and look for "validate mode"

---

### Post by chewearn on 2007-08-02
Just like to add in; I faced same issue with my LCD TV, which has resolution of 1280x768, but reported as 640x384 by the nVidia driver.  And no matter what I did to force the resolution, nvidia driver refused to budge.

I was going to try the new nvidia driver ver 100.14.11, but haven't the time to do so.

---

### Post by dougfractal on 2007-08-03
> also check the logs
Code:

less /var/log/Xorg.0.log

and look for "validate mode"

If the timings are out you wont get the resolution, A small tweek to the HorizSync and 
VertRefresh maybe all you need.

---

