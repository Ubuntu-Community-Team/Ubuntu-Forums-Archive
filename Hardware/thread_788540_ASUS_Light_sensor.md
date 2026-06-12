---
title: "ASUS Light sensor"
date: 2008-05-09
forum: Hardware
---

### Post by triptych03 on 2008-05-09
Hey all, well the problem is with the stupid ASUS light sensor. I have an M50SV. I can turn it off by 

echo 0 > /sys/devices/platform/asus-laptop/ls_switch

however when rebooting the settings go back. !@#$%

Does anyone know of a perm fix?

Using Hardy

Cheers.

---

### Post by Whiffle on 2008-05-09
Install sysfsutils, and then I think in the file /etc/sysfs.conf (might double  check that), put

devices/platform/asus-laptop/ls_switch=0

---

### Post by triptych03 on 2008-05-09
cheers I'll give it a try

---

### Post by triptych03 on 2008-05-09
> **Whiffle said:**
> Install sysfsutils, and then I think in the file /etc/sysfs.conf (might double  check that), put

devices/platform/asus-laptop/ls_switch=0


Works perfectly thanx heaps... great little util

---

### Post by barney66 on 2008-06-19
Hi there, I would like to be able to do this... however every time I go to save the sysfs.conf file I get an error saying I don't have permission to save the file... can someone provide a solution for a newbie please.... :)

regards,
barney

---

### Post by Soaa- on 2008-07-09
You have to edit it as root.

In Ubuntu: ```
sudo gedit /etc/sysfs.conf
```
In Kubuntu: ```
sudo kate /etc/sysfs.conf
```
In Xubuntu: ```
sudo mousepad /etc/sysfs.conf
```

---

### Post by Flying caveman on 2008-12-29
Thanks Whiffle.  :)  Hey there's no thank button ???

For the record mine is a ASUS Z71v / Z7100 running Ubuntu 8.04

Just upgraded from 7.04 and I can't remember if it never worked or just stayed bright all the time.  I didn't really care until all of a sudden that feature was working now, but not how I wanted it to.  It would dim down way too much when it was dark.  Fine for watching a movie but too hard on the eyes for reading any text.

Its not really a power saving feature when I have to turn on a desk lamp so my laptop doesn't get too dim.

---

### Post by An6oon on 2009-01-11
Hey guys, 
I am a new Ubuntu user and I have an asus m50sa laptop. I am also having problems with the light sensor. I did try to do whatever you guys wrote but nothing seemed to work. I don't know if it is me who's doing something wrong or I may have a different system. I'll appreciate it if someone would put down what should I do step by step to get it to work. Thanx.

Asus m50sa
Ubuntu 8.10

---

### Post by hotweiss on 2009-01-11
**A)** Open Terminal (Menu->Accessories), and type the following:
> sudo nano brightness

**B)** Now paste the following in the Terminal window:
> #!/bin/sh
echo 0 > /sys/devices/platform/asus-laptop/ls_switch

**C)** Hit Ctrl-O to save and then Ctrl-X to exit.

**D)** Now we will copy our new shell script to the appropriate directory, make it executable and add the following links by typing the following in Terminal:
> sudo mv brightness /etc/init.d
and then
> sudo chmod 755 /etc/init.d/brightness
and then
> sudo update-rc.d brightness defaults 90

**E)** Reboot, and you will have regained control of your brightness level.

---

### Post by An6oon on 2009-01-12
Thanx a lot. Works perfectly.

---

### Post by AnthonyDuncan on 2009-10-07
> **hotweiss said:**
> **A)** Open Terminal (Menu->Accessories), and type the following:


**B)** Now paste the following in the Terminal window:


**C)** Hit Ctrl-O to save and then Ctrl-X to exit.

**D)** Now we will copy our new shell script to the appropriate directory, make it executable and add the following links by typing the following in Terminal:

and then

and then


**E)** Reboot, and you will have regained control of your brightness level.
 
Not sure how many of you guys tried upgrading to Karmic 9.10 from Jaunty 9.04; and while I had this patch working in Jaunty, it stopped working after the upgrade to Karmic until I noticed a small difference.

echo 0 > /sys/devices/platform/asus-laptop/ls_switch
should be
echo 0 > /sys/devices/platform/asus**_**laptop/ls_switch

take note of the underscore between asus and laptops. eg. "asus**_**laptop" instead of "asus-laptop".

I hope this helps someone who needs it.

---

### Post by Stapo on 2009-10-16
I've got problem with creating the script. 

update-rc.d: warning: /etc/init.d/brightness missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>

pls help

---

