---
title: "Warning / Head's Up RE: Synaptics Driver"
date: 2008-03-08
forum: Hardware &amp; Laptops
---

### Post by Arthur Archnix on 2008-03-08
Hi, I was using powertop to try and extend my battery life. One easy tip is simply to turn off your wireless when on batter, or else tweak it. I turned mine off and found that my system was pretty lean, about 150 wakeups per second with two or three processes causing me problems. It turns out that it was the synaptic touchpad driver that comes installed with Gutsy: xserver-xorg-input-synaptics

After uninstalling it I am down to <25 wakeups per second.

You can check this out yourself. Install powertop:
```
sudo apt-get install powertop
```Then, run it
```
sudo powertop
```It will give you a baseline. Now turn off your wireless with the switch if you can. Physically turn it off I mean. Wait about 15 seconds and get the new baseline. Now temporarily remove the synclient by finding and killing its process id. I use
```
ps ax
```search for synclient, say its PID is 8001 then
```
kill 8001
```Wait another 30 seconds and get the new baseline.

Anyone else affected? I'd like to try the x86free one, but I can't find it in the repos.

---

