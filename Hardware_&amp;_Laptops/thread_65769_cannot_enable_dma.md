---
title: "cannot enable dma"
date: 2005-09-15
forum: Hardware &amp; Laptops
---

### Post by gus6464 on 2005-09-15
I have been searching the the faqs and done all the things that they say but i still cannot get dma turned on on my acer travelmate 4400. I keep getting an action not permitted error. I have taken out the ide-* lines in my modules file and have also added the following lines for my cpu as one user said which works:

amd74xx

above

ide-cd 

My other question is if there is a line at the install prompt that i can put in to enable dma when i install ubuntu as it takes forever to install if dma is not enabled. Ubuntu recognizes everything on my laptop except the dma.

---

### Post by WillCooke on 2005-09-15
Silly question, but you are using 'sudo' to turn DMA on?

i.e.

prompt>  sudo hdparm -d 1 /dev/hda

here hda is the device you want to use dma on (could be hda, hdb, hdc etc etc)

---

### Post by gus6464 on 2005-09-15
yes i did do sudo before using the hdparm command. I have also added all the ide-* to my etc/modules like other threads have said and nothing. System is crawling right now without dma turned on.

---

### Post by casainho on 2005-09-15
Hi!!

I also had that problem in one other PC..

I remember that I tried amd74xx and others modules for ide cd.. I think that there is a right sequence for load that modules.. and maybe you have some other ide module in memory, already loaded that interferes with the amd74xx..

Try to load by hand one at a time.. and in sequence..

Good luck. You will put that DMA working ;)




[QUOTE=gus6464]yes i did do sudo before using the hdparm command. I have also added all the ide-* to my etc/modules like other threads have said and nothing. System is crawling right now without dma turned on.[/QUOTE]

---

