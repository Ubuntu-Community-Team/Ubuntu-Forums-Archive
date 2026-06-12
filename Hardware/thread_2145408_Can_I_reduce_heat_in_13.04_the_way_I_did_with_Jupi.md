---
title: "Can I reduce heat in 13.04 the way I did with Jupiter"
date: 2013-05-15
forum: Hardware
---

### Post by spaceshipguy on 2013-05-15
I have strange amd switchable hybrid graphics

[Mobility Radeon HD 4225/4250] vendor: Advanced Micro Devices [AMD] nee ATI   --- and---[Mobility Radeon HD 5430/5450/5470] vendor: Advanced Micro Devices [AMD] nee ATI
      
on the same machine
Ubuntu has never played nice with this hardware, but it wasn't a problem because I could use Jupiter to bring heat down to a level where my machine didn't get cooked. (Ubuntu switches both integrated and graphics chips on at the same time and runs them on full power even when cpu usage is at single digits = things get hot)

I could really use e.g tricks for removing unused modules, or for setting all PCI buses to drop into idle mode quicker...
tmpfs'ing the firefox temp folder because it fsyncs() to  the hard-drive everytime you browse a page causing no end of hard-drive  activity...apparently.

Any links with walkthroughs would be appreciated.
I can't fix my graphics driver, but maybe I can get the heat down some other way?

---

### Post by dankojoffrey on 2013-05-15
Hi, I'm not sure about your GPU... you probably need proprietary drivers to turn off one of your graphics... or some open source tool to do that (something like Bumblebee for nVidia or maybe Ironhide), but I don't know any for ATI cards...

As a Jupiter replacement try TLP```
sudo add-apt-repository ppa:linrunner/tlpsudo apt-get update
sudo apt-get install tlp tlp-rdw
sudo tlp start
```

and install Powertop and change tunables:```
sudo apt-get install powertop
```

for tmpfs I use this in /etc/fstab :```
tmpfs   /tmp       tmpfs   defaults,noatime,mode=1777   0  0
tmpfs   /var/spool tmpfs   defaults,noatime,mode=1777   0  0
tmpfs   /var/tmp   tmpfs   defaults,noatime,mode=1777   0  0
tmpfs   /var/log   tmpfs   defaults,noatime,mode=0755   0  0
```

replace /tmp with firefox sync folder...

you can disable startup apps... to show hidden startup apps:```
sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop
```

---

### Post by spaceshipguy on 2013-05-15
Found a solution!!
[http://askubuntu.com/questions/96983/how-to-completely-shutdown-ati-card](http://askubuntu.com/questions/96983/how-to-completely-shutdown-ati-card)
put this command in a terminal
echo OFF | sudo tee /sys/kernel/debug/vgaswitcheroo/switch
and my temperature dropped from 80 to 60
happy happy

It's not persistant so it would be great if I could add it to some registry, but I'm happy to type it every time if I have to.

---

### Post by dankojoffrey on 2013-05-16
if you want to make it persitant, try add this echo command to /etc/rc.local

---

