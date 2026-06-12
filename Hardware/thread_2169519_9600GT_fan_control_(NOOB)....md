---
title: "9600GT fan control (NOOB)..."
date: 2013-08-22
forum: Hardware
---

### Post by dakos on 2013-08-22
Sorry for the noob Q, I spent more then 6 hours surching for a solution for this problem before asking for help so please be considerate... I just finished installing a dual boot win XP and Ubuntu 13.04, in ubuntu I have wireless and everything installed and working properly. The NVIDIA 9600GT fan was working at 100% before I updated the drivers to the propietery NVIDIA drives. Now it works at about 40% of full speed and still makes allot of noise, this is the number one noise making component of my PC (same as on the XP, I have an ssd, quiet cpu cooler and fanless PSU), GPU temp is 43-48C in ubuntu, I don't mind the GPU running at 70C just as long as the fan is more quiet. can anyone help me in quieting the evel fan?

Also /etc/X11/xorg.conf doesn't exist.

Thank you all for looking

---

### Post by dakos on 2013-08-22
Just saw that if I do in terminal:
```
sudo nvidia-xconfig
``` and not just ```
nvidia-xconfig
``` then a new xorg.conf file is created.

---

### Post by oldfred on 2013-08-22
I have a 9600GT and do not notice any noise, except when rebooting it seems to start at full speed. Sometimes entire system it gets full of dust/dirt and needs cleaning and then it is a bit louder.

---

### Post by dakos on 2013-08-22
Dear Fred,
After continuing a few more hours I figured out I was witing in terminal:
```
sudo gedit /etc/x11/xorg.conf
``` instead of ```
sudo gedit /etc/**X**11/xorg.conf
```
I edited the file like instructed here:
[http://www.overclock.net/t/1031846/how-to-control-fan-speed-in-ubuntu](http://www.overclock.net/t/1031846/how-to-control-fan-speed-in-ubuntu)
and enabled the GPU fan control, the problem now is that the minimum setting is 40% and it's still pretty loud.
I'll keep googling...
I hate NOOBs

---

### Post by dakos on 2013-08-22
Just went back to the XP install, set the fan to 20% using RivaTuner, GPU pinned at 47C and very quiet. Now there's gotta be a way to do this in ubuntu...

---

### Post by dakos on 2013-08-23
Found this:
[http://crunchbang.org/forums/viewtopic.php?pid=328585](http://crunchbang.org/forums/viewtopic.php?pid=328585)

it ncludes a little script to automaticlly change the fan speed according to the GPU temp.

Still no minimum fan speed less then 40% though...

---

### Post by oldfred on 2013-08-23
Which nVidia version are you running. Ubuntu offers current, updates & experimental, which are just the newer nVidia drivers. I am running 319.32 with 12.04 which I installed from command line or additional drivers.
System settings, Additional Drivers now shows it as nvidia_319_updates.

---

