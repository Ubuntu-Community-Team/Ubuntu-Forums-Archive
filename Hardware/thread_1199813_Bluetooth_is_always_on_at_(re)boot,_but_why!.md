---
title: "Bluetooth is always on at (re)boot, but why?!"
date: 2009-06-29
forum: Hardware
---

### Post by neocortex on 2009-06-29
Hello!
Every time I (re)boot, bloetooth is on. I would like to make it off, by default, with the possibility to turn it on if needed. I tried (according to the [http://ubuntuforums.org/showthread.php?t=1198338](http://ubuntuforums.org/showthread.php?t=1198338)):
> Go to Preferences > Startup Apps > Uncheck the blue tooth manager.

System > Administration > Services > Uncheck bluetooth.
But no luck.

I even tried to play with /etc/default/bluetooth. No luck whatsoever.

Please, help me: how to make bluetooth off by default?

Thanks!
PM

---

### Post by neocortex on 2009-06-30
Nothing?!? No idea at all?!?

---

### Post by ashen on 2009-07-01
I am currently having pretty much the same problem as you.

I can stop bluetooth being on at boot by disabling it in services:

```

System > Administration > Services > Uncheck bluetooth

```

but then I can't enable it by pressing Fn+F8.  I can toggle it off using the Fn+F8 commands, but initially it turns both bluetooth and wifi off, and I don't really want to lose my wifi connection (although toggling again will bring wifi back up).

Like the previous poster I'd like bluetooth to start off but be able to toggle it on using Fn+F8.

I have recently installed Jaunty, but did not have this problem under Intrepid.  Under Intrepid bluetooth was off on boot but could be toggled on using the Fn+F8 command.

Does anybody have any suggestions?

Thanks,

ashen

---

### Post by neocortex on 2009-07-04
Hello,
With the help from nice people of ThinkPad helping list, I managed to (re)boot with the bluetooth disabled, but with possibility to turn it on. In brief, only thing that needs to be done is to add the following line at the end of "/etc/init.d/rc.local":
> echo disable > /proc/acpi/ibm/bluetooth

[COLOR="DarkRed"]All acknowledgements goes to Richard Neill![/COLOR]

Best,
PM

---

### Post by jmduncan on 2009-07-04
Hi I am also having this problem running  			       Ubuntu 9.04 Jaunty Jackalope but I have the Sony VAIO. I tried the post of adding the line but when I try to save it says I do not have permissions to do so. Does anyone have any other thoughts on this or can neocortex post more details, maybe a copy of the file or screen shot of the end of the file. Thanks for the help.

---

### Post by neocortex on 2009-07-05
Naturally, you need to be a root!
In console, do either:
- su
- enter root password
- pico /etc/init.d/rc.local
Or:
sudo pico /etc/init.d/rc.local

Then, add the line at the end.

Best,
PM

---

### Post by randomguy1 on 2009-07-20
Hello
I had the same problem, but dont have the path /proc/acpi/ibm/bluetooth
Im running ubuntu 9.04 on an acer laptop.
Furthermore the killswitches are assigned a random number from 0-2 (rfkill0; rfkill1; rfkill2) on each startup.
Here's the solution:
As always, edit the rc.local and paste
```
if [ `cat /sys/devices/platform/acer-wmi/rfkill/rfkill2/type | grep -c bluetooth` = "1" ]
then sudo bash -c "echo 0 > /sys/devices/platform/acer-wmi/rfkill/rfkill2/state"
fi

if [ `cat /sys/devices/platform/acer-wmi/rfkill/rfkill1/type | grep -c bluetooth` = "1" ]
then sudo bash -c "echo 0 > /sys/devices/platform/acer-wmi/rfkill/rfkill1/state"
fi

if [ `cat /sys/devices/platform/acer-wmi/rfkill/rfkill0/type | grep -c bluetooth` = "1" ]
then sudo bash -c "echo 0 > /sys/devices/platform/acer-wmi/rfkill/rfkill0/state"
fi
```

before the exit line.

---

### Post by ashen on 2009-08-04
To fix this on a Toshiba laptop (I have a Tecra R10) you can make use of the command

```

toshset -bluetooth off

```

and add it to /etc/rc.local (before the exit 0 flag).

This results in bluetooth being off initially, but can be turned on using the bluetooth hot key.

Cheers,

ashen

---

### Post by Numer0bis on 2009-08-06
> **jmduncan said:**
> Hi I am also having this problem running  			       Ubuntu 9.04 Jaunty Jackalope but I have the Sony VAIO. I tried the post of adding the line but when I try to save it says I do not have permissions to do so. Does anyone have any other thoughts on this or can neocortex post more details, maybe a copy of the file or screen shot of the end of the file. Thanks for the help.


to tun off bluetooth on startup on a sony vaio you need to use spicctrl (Sony Programmable I/O Control Device Driver)

basically: 
spicctrl -l0
turns off bluetooth

so edit your /etc/rc.local and put spicctrl -l0 before the exit line and bluetooth will be turned off on bootup

however to re enable bluetooth just type spicctrl -l1 in a console and it will turn it on again

---

