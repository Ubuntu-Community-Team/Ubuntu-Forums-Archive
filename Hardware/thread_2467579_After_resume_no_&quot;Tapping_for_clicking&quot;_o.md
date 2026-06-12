---
title: "After resume no &quot;Tapping for clicking&quot; on Touchpad"
date: 2021-10-01
forum: Hardware
---

### Post by jonnycache2 on 2021-10-01
Hello Ubuntuusers,

i have an Surface 3 Pro and i'm using KDENeon 20.04. After starting my Surface i can tap on my touchpad and it is like clicking on it.
When i close the Surface (suspend i think) and open it then again, i have to klick by the edges of the touchpad, tapping is disabled.
So i tried to different ways to reactivate tapping on the touchpad after suspend.
1. 
This is described in the post here:
[https://forum.manjaro.org/t/automatically-enable-touchpad-after-suspend/5812/16](https://forum.manjaro.org/t/automatically-enable-touchpad-after-suspend/5812/16)
I made a service (i tried to locate the service like it is explained in the forum above an on another way in /etc/systemd/system) but after waking the surface the following command
```
systemctl status tip_restart.service
``` 
I get this 
```
Warning: The unit file, source configuration file or drop-ins of tip_restart.service changed on disk. Run 'systemctl daemon-reload>
&#9679; tip_restart.service - Restart Touchpad 
     Loaded: loaded (/etc/systemd/system/tip_restart.service; bad; vendor preset: enabled) 
     Active: failed (Result: exit-code) since Fri 2021-10-01 09:07:20 CEST; 14min ago 
   Main PID: 5835 (code=exited, status=1/FAILURE) 

Okt 01 09:07:20 hondosf systemd[1]: Starting Restart Touchpad... 
Okt 01 09:07:20 hondosf tip_restart.sh[5835]: Restarting Tipping just in case 
Okt 01 09:07:20 hondosf tip_restart.sh[5836]: unable to find device Microsoft Surface Type Cover Touchpad 
Okt 01 09:07:20 hondosf tip_restart.sh[5837]: unable to find device Microsoft Surface Type Cover Touchpad 
Okt 01 09:07:20 hondosf systemd[1]: tip_restart.service: Main process exited, code=exited, status=1/FAILURE
Okt 01 09:07:20 hondosf systemd[1]: tip_restart.service: Failed with result 'exit-code'.
Okt 01 09:07:20 hondosf systemd[1]: Failed to start Restart Touchpad.

```
So he cant find the device, but i figured the device name with 
```
xinput --list
```
The script for renable the tapping is like that: 
```
#!/bin/bash
echo"Restarting Tipping just in case"
declare -x DISPLAY=":0.0"
declare -x XAUTHORITY="/home/hondo/.Xauthority"
xinput set-prop 'Microsoft Surface Type Cover Touchpad' 329 1

```

So the first question is, why he cant find the device, when i get this with xinput?
```
xinput --list 
&#9121; Virtual core pointer                          id=2    [master pointer  (3)] 
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)] 
&#9116;   &#8627; NTRG0001:01 1B96:1B05 stylus              id=14   [slave  pointer  (2)] 
&#9116;   &#8627; NTRG0001:01 1B96:1B05 touch               id=15   [slave  pointer  (2)] 
&#9116;   &#8627; NTRG0001:01 1B96:1B05 eraser              id=17   [slave  pointer  (2)] 
&#9116;   &#8627; Microsoft Surface Type Cover Consumer Control     id=9    [slave  pointer  (2)] 
&#9116;   &#8627; Microsoft Surface Type Cover Mouse        id=11   [slave  pointer  (2)] 
&#9116;   &#8627; Microsoft Surface Type Cover Touchpad     id=16   [slave  pointer  (2)] 
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)] 
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)] 
    &#8627; Video Bus                                 id=6    [slave  keyboard (3)] 
    &#8627; Surface Pro 3/4 Buttons                   id=7    [slave  keyboard (3)] 
    &#8627; Microsoft LifeCam Front: Micros           id=12   [slave  keyboard (3)] 
    &#8627; Microsoft LifeCam Rear: Microso           id=13   [slave  keyboard (3)] 
    &#8627; Microsoft Surface Type Cover Keyboard     id=8    [slave  keyboard (3)] 
    &#8627; Microsoft Surface Type Cover Consumer Control     id=10   [slave  keyboard (3)]

```



2. 
I tried to make a suspend-script in 
```
/lib/systemd/system-sleep
```
The script contains this:
```
#!/bin/bash
if["${1}"=="pre"];then
  # Do the thing you want before suspend here, e.g.:
fusermount -u /home/hondo/fuse/ 
elif["${1}"=="post"];then
  # Do the thing you want after resume here, e.g.:
xinput set-prop 'Microsoft Surface Type Cover Touchpad' 329 1
fi
```

But it dont works. I get with 
```
journalctl | grep system-sleep
```

this 

```
[5189]: /lib/systemd/system-sleep/tipklick failed with exit status 1.
```



Wich is the right way to renable the tapping after suspend, where is my mistake? 

Jonny

---

