---
title: "CPU is very hot when idle"
date: 2006-10-28
forum: Hardware &amp; Laptops
---

### Post by Laterix on 2006-10-28
I have this problem with Edgy Eft that my CPU is very hot even when idle and the fan is active all the time, which makes annoying sound. I have a laptop with Pentium M 1.4GHz and I can't recall this problem with Dapper.

Here is a screenshot of my temperatures.
[IMG]http://personal.inet.fi/cool/laterix/hot.png[/IMG]

Any ideas?

---

### Post by DCDraco on 2006-10-28
Hi i am very new too ubuntu and I have installed it on my toshiba satellite P100. I have grave concern about overheating and I have want to find out how I can know if it is overheating. Could tell me how you managed to get the tempratures. As well at what temprature  is it dangerous for graphics card?

---

### Post by Laterix on 2006-10-28
> **DCDraco said:**
> Hi i am very new too ubuntu and I have installed it on my toshiba satellite P100. I have grave concern about overheating and I have want to find out how I can know if it is overheating. Could tell me how you managed to get the tempratures. As well at what temprature  is it dangerous for graphics card?
I don't know much about temperatures. I just know that my CPU idle temperature is way to high. You installed sensors-applet and hddtemp to see them on gnome panel. Just run
```

sudo apt-get install sensors-applet hddtemp

```
And then add the applet to your panel.

---

### Post by aidanr on 2006-11-16
i'm also seeing this on my pc, i'll walk away for ten minutes and when i come back the sensor is reading 50 degrees and i move the mouse around a little and it drops back down to 40 degrees in a few seconds:-k

---

### Post by neocookie on 2006-11-16
Have you installed laptop-mode and one of the CPU scaling apps (like cpufreqd)? My CPU was running 100% when I first installed both Dapper and Edgy and caused my fans to generate one hell of a racket, but that little tweak helped me out loads. 

Also, being a laptop, just make sure you're not actually using it on your lap! My laptop gets really hot when I don't give the vents enough clearance, and have now got myself a little wooden board for my laptop to sit on while I use it on the sofa.

---

