---
title: "GPU fan not starting after hibernate"
date: 2011-08-29
forum: Hardware
---

### Post by trendal.toews on 2011-08-29
Ubuntu 10.04
Nvidia Quadro FX 570
19" Dell 
22" Acer
Asus P5Q3 non/wifi
Q9650

Power Management Preferences set to put computer and display to sleep when inactive for 30 minutes including spin down hard disks.

GPU temp runs around 70c or 72c during use and drops to around 48c at idle.  Works fine until after computer has been inactive for 30 minutes and shuts down/hibernates. On login (not rebooting) the GPU fan does not come on.  GPU heats up to around 90c+ and the fan never comes on. Reboot, fan comes on, cools back down to 70c for regular use.  Repeat. 

Where do I start?  Whats dieing on hibernate and not ever coming back until a reboot?

Trendal

---

### Post by trendal.toews on 2011-08-31
In case someone is wanting to monitor their nvidia card for a bit here is a script that logs the temp every 5 minutes.  Requires nvclock to be installed.

```
#! bin/bash
while true; do
`nvclock -T | grep "GPU\|Board" >> gpu_temp.txt`
sleep 300
done
```

---

### Post by trendal.toews on 2011-09-01
Well if no one will help me I'll do it myself...

Actually the jokes on me.  I was running the default drivers.  After I installed NVIDIA X Server Settings the fan now comes on after a hibernate session. I've got a sketchy connection at my house so I don't just download anything I want. The default drivers had seemed to be working well except for this.

Thanks to all those who read this anyway. Hope it helped someone.

---

### Post by trendal.toews on 2011-09-01
Edited:

Thanks to whoever removed his post.  :-)

---

