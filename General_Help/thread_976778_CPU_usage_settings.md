---
title: "CPU usage settings"
date: 2008-11-09
forum: General Help
---

### Post by wildman4god on 2008-11-09
I have a dell latitude d600 it has a 1.8GHz processor a gig of ram and a ati fire mobility 9000 graphics card, anywho the only first person shooter it can run is open arena and I wanted to try others but they would lag too much, untill I was messing around with the gnome panel applets and found the one that lets you set the usage settings, it was on "on demand" and it said only 600 MHz was currently being used so I kicked it up to proformance mode which caused the applet to read the full 1.8 GHz and imediatly everything ran quicker and I could play warsow untill I rebooted now it won't run as fast again, was this a one time fluk, if not how can i get it to run that fast again, if it could do it once surly it could do it agian, any ideas?

---

### Post by wildman4god on 2008-11-09
by the way does anyone know how much memory it has and how fast its cpu is. i looked on the website but its not saying.

---

### Post by wildman4god on 2008-11-09
update the graphics card is a Ati MobiityRaedon 9000 and I found a website that says it has 32 MB of dedicated gpu ram, I still would like to know the gpu speed and if there is a way to share the system memory with the gpu.

---

### Post by mdurham on 2008-11-09
It sounds like you adjusted the "CPU Freq scaling monitor". If it's not on a panel, just right-click on a panel and select "Add to panel" and select the "CPU Freq scaling monitor". This will allow you to set the CPU speed as you like.
You might also add a temperature sensor to watch your CPU temp when you jack the freq up.

---

### Post by wildman4god on 2008-11-09
> **mdurham said:**
> It sounds like you adjusted the "CPU Freq scaling monitor". If it's not on a panel, just right-click on a panel and select "Add to panel" and select the "CPU Freq scaling monitor". This will allow you to set the CPU speed as you like.
You might also add a temperature sensor to watch your CPU temp when you jack the freq up.

Thats what i am talking about, i did that to get it to play warsow but it won't do it anymore, i adjust the cpu freq like the first time but it still acts like I did nothing, it only affected proformance the first time.

Also is there any cpu overclocking tools for linux, i am thinking about bringing the cpu from 1.8 GHz (its factory made setting) to around 2 GHz, I don't need to over clock it much the games i try to play run just a little slow and choppy, I am thinking that just a little overclocking may do the trick.

---

### Post by mdurham on 2008-11-09
Check with System->Admin->Services that "CPU Freq Manager (powernowd) is enabled. At least, that's what I use on my system. I also had to enable Cool&quiet in my bios.

---

