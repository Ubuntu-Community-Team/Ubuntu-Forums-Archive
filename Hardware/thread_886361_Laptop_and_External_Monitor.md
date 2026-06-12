---
title: "Laptop and External Monitor"
date: 2008-08-11
forum: Hardware
---

### Post by Rainagul on 2008-08-11
Hi there,

I recently put Ubuntu onto my laptop and it works great. Im really loving it over vista :D 

My laptop has a 15.4 inch screen and i wanted to test my 22 inch external monitor on ubuntu. 
However when i plug it in, the resolution dosen't update and it stays at the 15.4inch resolution. When i go to resolution settings, i can't make it any bigger from there either.

So im a bit stuck. I would really like to use my 22inch but im just not sure how to make it work :S

If anyone could help, then i would appreciate it greatly. Also im still new to Ubuntu so if anyone awnsers then can it be in simple english >_< i probably won't understand if its all complicated.

Thanks in advance...:D

---

### Post by linux_tech on 2008-08-11
What is your system configuration- what graphics adapter 
are you using?
What method are you currently using for dual display?

---

### Post by overdrank on 2008-08-11
> **Rainagul said:**
> Hi there,

I recently put Ubuntu onto my laptop and it works great. Im really loving it over vista :D 

My laptop has a 15.4 inch screen and i wanted to test my 22 inch external monitor on ubuntu. 
However when i plug it in, the resolution dosen't update and it stays at the 15.4inch resolution. When i go to resolution settings, i can't make it any bigger from there either.

So im a bit stuck. I would really like to use my 22inch but im just not sure how to make it work :S

If anyone could help, then i would appreciate it greatly. Also im still new to Ubuntu so if anyone awnsers then can it be in simple english >_< i probably won't understand if its all complicated.

Thanks in advance...:D

Hi and welcome, You can use the command ```
lspci
``` 
In the terminal located under applications, accessories, terminal and this will identify your hardware, Look for VGA. Also you may use this command using the alt, F2 keys and enter ```
gksu displayconfig-gtk
``` There you can set your driver and resolution for you monitor.

---

### Post by Lusse on 2008-08-11
Try to restart with monitor plugged in, that worked for me!

---

### Post by Norman Grahams on 2008-08-11
Do you mean the external monitor wouldn't turn on? Or it turned on but only on a low resoulution - the native resolution of the laptop's 15.4"?

---

### Post by Rainagul on 2008-08-11
Sorry i probably didn't make myself very clear.
Ill Explain the situation.

1. I turn on my laptop, log into Ubuntu etc.
2. Then i plug in my 22 inch screen .
Note: im not using it for a dual monitor configuration, im using it for primary monitor use.
3. Then the image appears on my 22inch, but its not at the right resolution and i can't change it.

I have tried restarting with the monitor plugged in, but that dosent change anything.

As for my laptop specs:

Manufacturer: Hewlett-Packard 
Processor: Intel(R) Core(TM)2 Duo CPU T7300 @ 2.00GHz (2 CPUs), ~2.0GHz 
Memory: 2046MB RAM 
Hard Drive: 160 GB Total 
Video Card: NVIDIA GeForce 8400M GS  
Monitor: Generic PnP Monitor 
Sound Card: Speakers (Realtek High Definition Audio) 
Operating System: Windows Vista™ Home Premium and Ubuntu :)

And thank you overdrank, thats what i was looking for :) I can only try it on tuesday when i get back from holidays. But i will post my results/problems.

Thanks to everyone, got my replies quite quickly

---

