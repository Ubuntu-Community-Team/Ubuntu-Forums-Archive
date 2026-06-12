---
title: "Lenovo 3000 N100: internal speakers, DRI, webcam"
date: 2006-06-29
forum: Hardware &amp; Laptops
---

### Post by haakon on 2006-06-29
I have gotten my new Lenovo 3000 N100 (the model with 1GB ram, core duo, NVIDIA GeForce Go 7300 TurboCache). I'm running dapper with the "2.6.15-25-686 #1 SMP PREEMPT" kernel on it. There are a couple of annoyances I would very much like to fix.

First, sound. I have fixed my /etc/modprobe.d/options like [https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100) says, so I do have sound. However, it is a known problem in Ubuntu that the internal speakers continue to produce sound after you plug headphones into the jack on this laptop. This should be easy to fix; just go into alsamixer and mute the external amplifier. This does indeed silence the internal speakers, but it also makes the sound sent to the headphones *really* broken. The sound becomes all bursty and thin, no matter how the alsamixer settings are. The moment I enable the internal speakers, the headphone sound becomes good again -- but then I have to endure the tinny internal speakers. Is anyone else seeing this or have any ideas?

I also wonder if there is any way to get DRI (direct rendering) in X with the nv drivers on this hardware. I currently have no direct rendering, so glxgears seems to get 3-5 fps and makes the fan spin up almost instantly. Also, the GUI programs feel sluggy; if I switch between windows, I have to sit and watch the GUI redraw itself for up to a second. Though a second is not an eternity, I switch between windows a lot and it becomes painful. My desktop PC has a poorer CPU (but direct rendering) and is way faster in this regards compared to this dual-core laptop. I know the unfree drivers would probably help, but I would rather not consider that.

Finally, there is a cute little webcam stuck into the top of the screen of this laptop. My googling so far suggests that there are no Linux drivers for it, but I would be interested any confirmation of this.

Thanks for any help!

---

### Post by Hellkeepa on 2006-06-29
HELLo!

For the sluggish performance during switching between windows and such, please read this thread:
[http://ubuntuforums.org/showthread.php?t=204100](http://ubuntuforums.org/showthread.php?t=204100)

Happy codin'!

---

### Post by haakon on 2006-07-01
Thanks. I tried to change /sys/module/processor/parameters/max_cstate to 1, but it didn't seem to do anything. Idle CPU load is at between 0.10 and 0.60, roughly. It very rarely goes below 0.10. Since I have dual core, I run the 686-smp kernel.

Regarding the slugginess, it's actually mostly noticable on Thunderbird. I can stand the other applications. Hopefully the nv driver will improve over time.

---

### Post by patrickfromspain on 2006-07-01
About the nv driver.. why not install the nvidia propietary drivers? Those are better for sure and will support you card 100%

---

### Post by Hellkeepa on 2006-07-01
HELLo!

The "max_cstate" doesn't fix the perfomance issues, it just circumvents the "CPU usage" bug from tricking the system into believing that the CPU is under constant load. In other words, the only thing you'll notice with that is that the temp goes down, and the CPU usage monitor applet shows less usage.
I had to install the -386 kernel to get something that was akin to "normal" performance, so you might want to try that as well. If that works for you, then I have no other suggestions than to try and compile the 2.17 kernel to get SMP support.

Happy codin'!

---

