---
title: "No audio, wifi, or cpu freq scaling in ubuntu 8.10"
date: 2008-11-24
forum: Hardware
---

### Post by crazy4laptops on 2008-11-24
I'm still relatively new to ubuntu so all how to's suggested need to be in step by step format

I installed ubuntu via wubi (which rocks btw) and am now dual booting vista and ubuntu on my hp dv5z-1000 laptop 

i'd use ubuntu more, i just have three problems that cause my laptop not to be quite as mobile as i'd like it to be 

prob #1-
wifi not working 
atheros AR5007 b/g wifi adapter (restricted driver installed)
i have no clue how to get the card active and connected to networks  

no audio-  
IDT hi-def audio 
tried alsa mixer, no sounds heard-
flash videos,  mp3s on hdd, only thing heard was silence

according to the cpu widget in the top panel,
cpu frequency scaling is not supported on a Turion 64 x2 rm-70

any fixes for anything above?

---

### Post by Ryan2009 on 2008-11-24
Just out of curiosity which widget are you using to see if cpu frequency scaling is supported?

---

### Post by cdtech on 2008-11-24
What do you see for your freq scaling with:
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
```

---

### Post by crazy4laptops on 2008-11-24
the one in 

right mouse on menu bar > add to panel > cpu frequency monitor 

but i also would like focus on the other two issues at hand also

---

### Post by cdtech on 2008-11-24
> **crazy4laptops said:**
> the one in 

right mouse on menu bar > add to panel > cpu frequency monitor 

but i also would like focus on the other two issues at hand also

Explain, you make no sense here.

---

### Post by crazy4laptops on 2008-11-25
follow that path and drag the cpu freq scaling monitor onto the panel. The message i get is that frequency scaling is not supported. 

Now, i'd like help resolving the audio and wifi issue also

---

