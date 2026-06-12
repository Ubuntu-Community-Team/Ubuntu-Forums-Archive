---
title: "Change display to 1280x1024 no xorg.conf??"
date: 2010-01-25
forum: Hardware
---

### Post by gannggstaz on 2010-01-25
I have successfully run ubuntu for about a year, until I updated to 10.04 which ruined my display resolution and wireless usb card. I decided to try some other distros, but ended up returning to ubuntu, only I made the switch to kubuntu because I prefer the KDE desktop. 
I tried with both kubuntu and ubuntu to get my display to the proper resolution, but the last time I fixed this I had an xorg.conf file located in /etc/X11. My xorg.conf file is missing, and xrandr seems to just plain not work. The only thing that has worked was setting up my wifi, then updating my driver for my video card, however this forces me to boot in safe graphics mode and doesn't allow me to use the internet anymore. I experienced this previously, but I had an xorg.conf file and edited it which fixed the problem.

I just need to add the option of 1280x1024 @ 60.0
I tried using the xrandr tool but it has done literally nothing.

---

### Post by Chicanob12 on 2010-01-26
> **gannggstaz said:**
> I have successfully run ubuntu for about a year, until I updated to 10.04 which ruined my display resolution and wireless usb card. I decided to try some other distros, but ended up returning to ubuntu, only I made the switch to kubuntu because I prefer the KDE desktop. 
I tried with both kubuntu and ubuntu to get my display to the proper resolution, but the last time I fixed this I had an xorg.conf file located in /etc/X11. My xorg.conf file is missing, and xrandr seems to just plain not work. The only thing that has worked was setting up my wifi, then updating my driver for my video card, however this forces me to boot in safe graphics mode and doesn't allow me to use the internet anymore. I experienced this previously, but I had an xorg.conf file and edited it which fixed the problem.

I just need to add the option of 1280x1024 @ 60.0
I tried using the xrandr tool but it has done literally nothing.

Try "sudo apt-get install xresprobe" and see if that does the trick, you might need to restart after. i had a similiar problem and that worked for me!

---

### Post by Chicanob12 on 2010-02-11
sorry if "sudo apt-get install xresprobe" doesn't work just look for it in the synaptics package manager it will be there.  I used to have a similiar problem and this worked perfectly for me.

---

