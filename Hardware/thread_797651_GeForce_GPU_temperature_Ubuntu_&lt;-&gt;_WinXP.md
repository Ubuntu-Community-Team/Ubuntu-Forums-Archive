---
title: "GeForce GPU temperature Ubuntu &lt;-&gt; WinXP"
date: 2008-05-17
forum: Hardware
---

### Post by tomdirac on 2008-05-17
Hello,

I'm running Ubuntu 8.04 on my Dell Latitude D800 Laptop using the proprietary 'nvidia' driver that came with ubuntu for my "GeForce FX Go5200" video card.

I noticed that the GPU temperature is always around 75°C with the system idling (empty desktop). In WinXP the temperature usually is only 40°C.

What could be the reason for this? What's the temperature range where the hardware can be permanently damaged?

"nvidia-settings" has a section called "PowerMizer" wich says that adaptive clocking is enabled... is there a way to change the performance level from 2 (390MHz) to a lower value? Quite frankly, I would guess that "adaptive clocking" does not really work... but thats just a guess.


I would be happy to get some ideas how to fix this.


greetings,
thomas

---

### Post by teaker1s on 2008-05-17
if you haven´t already:-using ¨envy" installer for nvidia binary driver normally gives better results than ubuntu repository offerings

---

### Post by tomdirac on 2008-05-17
I just installed the nvidia driver using the envy script. It seems that graphics performance has increased a bit compared to teh repository-driver. The GPU temperature however did not change.

I don't know wether temperatures between 70-80°C  can permanently damage the graphics card ot other devices of the Laptop.

---

### Post by motin on 2008-06-27
My GPU is always around 60, which seems to much for idling even though compiz is activated. I too would like to see idling temperatures of around 40 in Ubuntu...

There is always the possibility to [underclock the nvidia GPU]("http://aldeby.org/blog/index.php/enable-nvidia-coolbits-frequency-tuner.html"), but it would be great if there existed a more decent solution to this heat problem...

---

### Post by jimv on 2008-06-27
I think Nvidia gpus are rated for something like 140 degrees C.

---

### Post by starcannon on 2008-06-27
You can play with underclocking and overclocking if you enable coolbits.

I wrote a post on this just a bit ago, you can see it here:
[http://ubuntuforums.org/showpost.php?p=5274719&postcount=3](http://ubuntuforums.org/showpost.php?p=5274719&postcount=3)

GL

---

### Post by tgeer43 on 2009-06-28
Just FYI - I'm using the latest driver from Nvidia's website under Ubuntu 9.04 with adaptive clocking enabled and it does indeed work. Try leaving the Nvidia settings applet open then fire up a 3D game or benchmark and you should see it ramp up the frequencies and then scale them back down when you exit back to an idling desktop. At least then you'll know whether adaptive clocking is actually working for you.

My Geforce 8600M GS run at about 40°C when idling and no more than 60°C under full load. That's in a notebook which, theoretically should run hotter than a desktop.

Worst case you could add some cooling to the case or directly to the GPU.

tgeer

---

### Post by buntu_hugenewbie11 on 2009-12-19
My GPU is consistently over 90 Celsius when watching flash video?
PEriorically it overheats and shuts down.
GeForce 770 
Kubuntu 64 bit hardy.
Please any help would be so useful.

---

### Post by abdusamed on 2010-04-13
> **tgeer43 said:**
> Just FYI - I'm using the latest driver from Nvidia's website under Ubuntu 9.04 with adaptive clocking enabled and it does indeed work. Try leaving the Nvidia settings applet open then fire up a 3D game or benchmark and you should see it ramp up the frequencies and then scale them back down when you exit back to an idling desktop. At least then you'll know whether adaptive clocking is actually working for you.

My Geforce 8600M GS run at about 40°C when idling and no more than 60°C under full load. That's in a notebook which, theoretically should run hotter than a desktop.

Worst case you could add some cooling to the case or directly to the GPU.

tgeer


how did you enable adaptive clocking? i have 9700m gts

---

