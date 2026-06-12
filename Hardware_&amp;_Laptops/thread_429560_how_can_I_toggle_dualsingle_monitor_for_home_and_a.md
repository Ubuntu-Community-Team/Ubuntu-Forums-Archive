---
title: "how can I toggle dual/single monitor for home and away"
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by bakermiller on 2007-05-01
I used [this]("http://ubuntuforums.org/showthread.php?p=1773624") tutorial to set-up dual-monitors. It works fine. Only, when i'm away from home, i would like to use only the laptop LCD screen. Now, if i use the laptop without the extra monitor, some windows get lost in the non-existant window. How can i choose single or dual monitor session. I something about using a combination of keys (FN+F5??). But i don't know how to set-up the server layout in xorg.conf. can someone help?

---

### Post by pete on 2007-05-01
I'm not sure this is possible to do with a single xorg.conf file, although I'm not an expert by any means.

My setup isn't quite the same as yours, but it's similar.  The way I do it is to have two separate xorg.conf files, one for when I'm docked and have an external monitor, and one for when I'm undocked and using the internal LCD.

Then I have a script that checks at boot for the presence of the external monitor and loads the appropriate xorg.conf.  Been running this way for a week or so and it's working flawlessly.

[This thread (http://ubuntuforums.org/showthread.php?t=346483&highlight=script+docking+station)]("http://ubuntuforums.org/showthread.php?t=346483&highlight=script+docking+station")  got me pointed in the right direction as far as scripting the process.

---

### Post by bakermiller on 2007-05-01
nice. thanks. But would i be using LPL0000 as the monitors ID, or should i change it to something else according to my monitor?? How would i know my monitors ID or port or whatever LPL0000 is?? I tried lspci, but cant find the info.  hmmmm.

---

### Post by pete on 2007-05-01
You'll probably need to change "LPL0000" to some other identifier that's unique to your external display, as it's just something the guy in that thread came up with for his particular set-up.

For mine, i've got the following for my xorg.conf_switcher.sh:

```
#!/bin/sh
#/etc/init.d/xorg.conf_switcher.sh
#Determine if the external display is active.
#When local lcd is present "DELL 2007FP" is in ddcprobe.
if /usr/sbin/ddcprobe | grep "DELL 2007FP"; then
echo "External display is active."> /home/peteb/test.txt
#Copy docked xorg file to xorg.conf.
cp /etc/X11/xorg.conf.docked /etc/X11/xorg.conf
else
echo "Internal display is active." > /home/peteb/test.txt
#Copy undocked xorg file to xorg.conf.
cp /etc/X11/xorg.conf.undocked /etc/X11/xorg.conf
fi
```

To figure out what to use for yours, trying running "sudo ddcprobe" in Terminal while you're connected to the external display, then run it again while disconnected from the external display.  What you're looking for is *any* difference between the two that you can use as an indicator of what xorg.conf to pick.

---

### Post by bakermiller on 2007-05-01
Got it working!!
thanks!!
this is great!!

---

### Post by jjordan on 2007-05-04
There is a way to call the different layouts from a single xorg.conf file, can't remember it at the moment.  I think you just say

startx -layout-I-want

Take a look at this,

[http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/2003-November/013701.html](http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/2003-November/013701.html)

it looks way interesting to accomplish similar outcome.

-j

---

