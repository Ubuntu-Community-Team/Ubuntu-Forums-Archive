---
title: "cpu temperature"
date: 2010-08-16
forum: Hardware
---

### Post by yashar on 2010-08-16
i hava a msi laptop , turion-x2 64 bit , i use both win 7 and ubuntu 10.04 32 bit, my cpu temperature is about 4-5 'C cooler in win 7, and it is important for me, although i use ubuntu more.

how about you? same experiment?

---

### Post by TBABill on 2010-08-16
Yes, Ubuntu does run hotter than Windows. Depending on your configuration it could run significantly hotter because open source drivers are just not good at scaling your GPU and managing power well. And Adobe Flash does not use hardware acceleration so your CPU does much more of the work in any Linux distro than it does in Windows or Mac. Other power management settings also come into play and could need to be tweaked on your machine. I use frequency scaling on my CPU to keep it at its slowest speed until demand increases to kick it up higher.
 
If you search for heat, CPU and laptop I am sure you'll find many threads on this.

---

### Post by gradinaruvasile on 2010-08-16
Also there are reports that The 10.04's kernel has a bug that makes it consume CPU power when in idle mode.
And the fact that the series 1 (dont know about the new II series) turions and mobile athlons are overheating (even under Windows) dont help...

Edit: The newer kernels (2.6.3x) already have built-in CPU frequency scaling and the default governor is ondemand meaning that the CPU stays at its lowest frequency level when at idle (or under 40-50% load). Also the cores are throttled independently.

And as others said, be careful what pages are opened in the browser - the flash plugin can easily use 100% CPU if some demanding pages are open even when in the background. I suggest using flashblock or something to similar effect to prevent unneeded flash applets from loading.

The AMD platform uses Ati cards, if you have a 2000 series or newer (the 1xxx series are only supported by the built-in driver), using the proprietary fglrx drivers because those will lower the video cards working frequency in idle mode and help with the cooling - the laptops usually dont have separate fans for CPU and GPU, instead they use shared fan(s) that pushes the air through cooling tunnels - both the CPU and GPU are in this path, so one overheating will influence the other.

Dont leave the laptop running on the bed or similar soft surfaces because it cannot cool efficiently there - put it on a flat or at least hard surface that lets air flowing underneath.

---

### Post by utnubuuser on 2010-08-16
I'm thinking it's flash too.  On my ThinkPad it's as though something were running in the background that's not shown in TOP. My laptop will inexplicably get warmer and warmer even though TOP shows only 1.2% or 2% activity.

It must be something at a deeper level, ie in the kernel or one of the drivers...

It's probably a good idea to add the CPU frequency monitor to the panel so you can see what's going on.

On my machine, the hottest point seems to be the mini-pci, the wireless card.
It might be what one of the other posters suggested, an actual site that's causing not CPU usage, but excessive network traffic.

What's really annoying about it is that the behaviour isn't consistent.  It's bad in that you can't trust the OS to behave while unattended - a key requirement for my  main OS.

---

### Post by yashar on 2010-08-17
yes, i can see when i use adobe files or browse them the cpu temp increase fast, as much as i know turion x2 could handle up to 100 'C and i never let it get higher than 77 'C till now;)

about system frequency, win 7 offers power vs long life battery by reducing cpu speed, as you said in 2.6.3x it is built inside,so is there a way to configure that for speed or battery life?

---

### Post by yashar on 2010-08-17
CPU Frequency Scaling Monitor is the answer, it is inside gnome applets, install it!!

---

