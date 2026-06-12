---
title: "GNOME Power Management"
date: 2005-12-19
forum: Hardware &amp; Laptops
---

### Post by .t. on 2005-12-19
In KUbuntu, there is a KDE applet that controls the system's resources depending on the power source; I forget what it is called, as I have now switched to GNOME. I like it because I can tell the system what to do when I close the lid, press the power button, or what SpeedStep setting to use depending on the source. This makes it much easier and quicker to change the settings to preserve battery - is that not important for us laptop users? Since I think it is, is there a similar applet for GNOME?

---

### Post by dys4ic on 2005-12-19
I think gnome-power-manager is what your looking for. Try the latest version, although you will need some very specific deps. Have a look at the homepage ([http://www.gnome.org/projects/gnome-power-manager/]("http://www.gnome.org/projects/gnome-power-manager/")).
You can find the latest version here [http://mirrors.dk.telia.net/ubuntu/pool/universe/g/gnome-power-manager/]("http://mirrors.dk.telia.net/ubuntu/pool/universe/g/gnome-power-manager/")

I've tried the current version g-p-m-0.2.8 in synaptic but It doesn't work very well for me and it doesn't have all the features that the latest one have.

And the g-p-m-0.3.1 I cant even install because of the deps, not sure what to do next...

---

### Post by .t. on 2005-12-20
Cheers, I'll have a look

---

### Post by taseal on 2005-12-21
how do i install that latest 3 version? I dont even know what debs are :(

---

### Post by JLB on 2005-12-22
debs are the packaged files that a debian (and ubuntu) system uses. you can manually install a packagename.deb file like so...

open a terminal

sudo dpkg -i packagename.deb

enter your password when prompted. Just take notes of the required dependencies :)

---

### Post by GoodPanos on 2005-12-22
What's the results...

---

### Post by emenny81 on 2005-12-22
[QUOTE=JLB]debs are the packaged files that a debian (and ubuntu) system uses. you can manually install a packagename.deb file like so...

open a terminal

sudo dpkg -i packagename.deb

enter your password when prompted. Just take notes of the required dependencies :)[/QUOTE]


but for the new version de dependencies are in tar format, I've tried to install them but I am unable to do it, is there a way someone can post a step by step instructions on how to get this power management program working, thanks

---

### Post by dys4ic on 2005-12-24
[QUOTE=emenny81]but for the new version de dependencies are in tar format, I've tried to install them but I am unable to do it, is there a way someone can post a step by step instructions on how to get this power management program working, thanks[/QUOTE]

I gave it a try to install deps manually too, but this is exactly why I installed ubuntu in the first place, so that I wouldn't have to spend time doing that. I know that the latest version is in Dapper though, so I suppose I'll just have to wait till that is released... 
In the meantime I wrote a little shellscript that will take care of at least shutting down my laptop if I would fall asleep reading or something :)    

```
#!/bin/bash

SLEEPCOMMAND="/sbin/poweroff"
# Get the battery's low and current capacity value
LOW=`cat /proc/acpi/battery/*/info | grep "capacity low" | grep -o -E +[0-9]+`
CURRENT=`cat /proc/acpi/battery/*/state | grep "remaining" | grep -o -E +[0-9]+`
ON_BATTERY=`cat /proc/acpi/ac_adapter/*/state | grep off-line`
if [ -z $LOW ] || [ -z $CURRENT ] || [ -z $ON_BATTERY]
then
        exit 0  # Exit if no values are found or on AC
elif [ $CURRENT -lt $LOW ]
then
        $SLEEPCOMMAND
fi
```

I just put this in a file called checkBattery.sh and then run it as a root cronjob every 2min. It will then shutdown when the battery power becomes critical (around 4-5%). I tried to get it to hibernate instead of shutting down, but for some reason it seems like it can't do a complete hibernation when run as cronjob...

---

