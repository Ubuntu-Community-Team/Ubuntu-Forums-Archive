---
title: "CPU maxes out on Dell E1505 when plugged into car inverter"
date: 2008-03-13
forum: Hardware &amp; Laptops
---

### Post by landman 1560 on 2008-03-13
I'm fairly well a noob as 7.10 is my first real try at learning a Linux environment so I will try to keep up.

This is a really weird problem that I have not found on any forum yet.  I work out of my car a lot and spend a good bit of time on the road during the day so I tend to have my laptop running most of the day.  I use an inverter to plug it into to keep the charge up on the battery while I'm driving.

On longer drives I use an RF broadcaster to listen to streaming radio or my collection of music through my stereo.  I have started having a problem in that sometimes the CPU maxes out and everything locks up.  If I unplug the charge cable the CPU calms back down.  Plug it in and it maxes out again.  This doesn't happen unless it's in the car.

Is there something odd about inverters or some setting that I don't have set right?  Firefox has been using a lot more CPU lately (13% as I sit here) but today it pulled this stunt with only Amarok open.

My system:
Dell E1505
Intell Core 2 Duo T5600 (1.83 GHz)
1 Gig Ram
X1400 Radion Mobility
Broadcom Wireless Card

I'll supply whatever info you need if you  tell me.  Thanks for the help in advance.

---

### Post by |{urse on 2008-03-13
when that laptop is plugged into the inverter, open a terminal and type

top

that will let you know the cpu/mem/swap usage for each process, when youve tracked down which one is using up all your cpu, press ctrl + c to exit top and type

sudo killall foo

replace foo with the actual processes name

---

### Post by landman 1560 on 2008-03-23
This condition has not repeated itself yet.  Once it has I'll post what showed.

Any ideas as to why this would happen in the first place?  It used to happen more when I was driving a mid 80's Camaro but I just bought an '03 Infiniti G35 and it has only happened once.  Something about the electrical systems that are different, maybe?

---

