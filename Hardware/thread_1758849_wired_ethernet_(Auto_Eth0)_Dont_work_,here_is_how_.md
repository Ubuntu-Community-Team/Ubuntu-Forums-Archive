---
title: "wired ethernet (Auto Eth0) Dont work ,here is how i fixed it !!!"
date: 2011-05-15
forum: Hardware
---

### Post by dazndom on 2011-05-15
I hope this helps some one else who has lost their WIRED internet connection.

back in Feb 2011 i noticed that i had lost wired internet - previous post is here; [http://ubuntuforums.org/showthread.php?t=1700948](http://ubuntuforums.org/showthread.php?t=1700948)

so back in feb.. i had no wired connection in ubuntu or windows (nor the other 2 distros i was playing with)    and as you can see whilst in win7 i hit fn+f3 and browser opened and connection came back....
But for the last 2 weeks i have had the problem again , but this time i have no win7 as i replaced it with Ultimate Edition (Ubuntu on steroids)
But i seemed to fix it by rebooting over and over ( about 12 times) it just came back by itself again..
but it came back again

so i have spent 8 hrs reading forums of different solutions and here is what i have learned.

A COMPUTER is an ELECTRONIC device   !!!!!!!!

It's various components hold an electro magnetic charge    (for many days even when left OFF)


OHHH  BUGGER the technological explanations

differences in electrical charge currents can play havoc with your nic and wireless and graphics cards. i think auto eth0 config files mess things up and "LOCK" the nic


1st - Go to network manager / edit connections ....click on Auto Eth0 / Edit   - 
UNTICK  - connect automatically
click save

Now do the same for your wireless connection

2nd
UNPLUG your power supply and battery-(laptops),   disconnect everything..........
hold start button down for 60 seconds to drain all charge from ram, nic ,etc etc

go have a cup of tea for 10 min
power up computer 
when it has powered up you will have to click on your connection manager and click on  your connection either wired or wireless


I HAVE been testing this for 3 days, having rebooted 50 times across 3 different linuxes on my laptop and 4 linux and  vista on desktop.
both are working on wired connection again

I had to set this configuration in all linux  ( i have been thru many trial and errors)  did nothing in vista (it just came back -  i dont use it anymore, just for kids ipods/itunes store)


This works faultlessly and internet connection seems faster( both initial connection and opening webpages)

hope this helps,:D

have you discovered Oz Unity or Ultimate edition yet,  - ultimateeditionoz.com
good luck
Daz

---

