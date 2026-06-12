---
title: "Help with upgrade"
date: 2010-12-20
forum: Hardware
---

### Post by medphys on 2010-12-20
Hi all,

Just updated my computer from 9.1 to 10.04.1.  Everything went well with the exception of expanding the programs to fit the whole screen.  I cannot get my programs, open office, Thunderbird  etc to fill the screen.  I also cannot center them on the screen.  they will not move and reside on the left of the screen.  

What is the secret to expanding the programs to fill the screen?

Thank you and have a great holiday.

---

### Post by oldfred on 2010-12-20
Is this more a case of your video card outputting the wrong size to the monitor. What video card do you have?

To see video:
sudo lshw | grep -A 11 display
or
sudo lspci -nn|grep VGA

this might work:
#If able to boot to recovery mode & netroot
#list of recommended drivers:
jockey-text -l
#Install a driver:
sudo jockey-text -e <driver>

You may also have a proprietary driver listed under System, Administration, Hardware Drivers

eidt:

See this also:
[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

---

### Post by medphys on 2010-12-28
Oldfred,

Thanks for the help.  Been gone for a while and now have the time to fix the problem, I think.

My configuration is as follows:
MSI P55-GD80 1156 RT
INTEL |CORE I7 860 2.8 G
SEAGATE 7K ST3100052
4 GIG CORSAIR CMX4GX3M2
MSI N94GT MD512 9400 GT
Ubuntu 10.04 64 bit

I have tried all of my programs and some I can expand, but most of them I cannot expand or move.  I do not have the minimize, Maximize or quit icons on the upper right of the screen as in previous editions of the software.  I wonder what is going on with this upgrade.  Everything seems to be working fine and can access all of my programs.  

I also am running the nvidia kernal from ubuntu and can modify my screen resolution but to no avail.

Thanks for the help.

---

