---
title: "Ubuntu detecting slower AMD clock speed?"
date: 2008-01-07
forum: Hardware &amp; Laptops
---

### Post by Tadock on 2008-01-07
First, off I have an AMD 64 X2 3800+ (2.0Ghz) Today I did a cat /proc/cpuinfo and it said I have 2x1Ghz rather then a 2x2Ghz. I am not sure what to think of this any ideas on how to correct this or is there nothing to correct?

---

### Post by ryanVickers on 2008-01-07
yes this is correct - i have the same ship it scales like a laptop between 1 and 2Ghz - major power and heat saver!! :D

If you want to see what each ocre is running at (they are usually synced up though), add "CPU Frequency Scaling Monitor" to the panel ;)

---

### Post by Tadock on 2008-01-07
So, because of AMD Cool N' Quite technology it shows it is a slower clock speed. But in reality it isn't? I still get my full 2.0Ghz?

---

### Post by ryanVickers on 2008-01-07
No, when it says 1Ghz, your getting 1 Ghz, but as soon as it needs more, aka as soon as you do practically anything more intensive than move the mouse, it will turn up to 2 Ghz

all in all, don't worry - it knows what it's doing ;)

---

### Post by Tadock on 2008-01-07
So, when it needs more horse power it goes and gets more from the idle processing power? If so, that sense.

---

### Post by ryanVickers on 2008-01-07
OK, imagine an old horse buggy car thing ;)

lets say its moving at a top speed of 50 km/h.  say adding more horses won't help, it will just waste energy

now imagine your climbing a hill. your slowing down to only 49km/h - magically another horse appears out of no where and starts pulling - you now continue your 50km/h

points I'm trying to highlight:
-it can speed up and slow down instantly - its not like a disk that needs to spin
-it only runs faster when need be, but if it needs more power, even a little bit, it will use all its power

---

### Post by Tadock on 2008-01-07
> **ryanVickers said:**
> OK, imagine an old horse buggy car thing ;)

lets say its moving at a top speed of 50 km/h.  say adding more horses won't help, it will just waste energy

now imagine your climbing a hill. your slowing down to only 49km/h - magically another horse appears out of no where and starts pulling - you now continue your 50km/h

points I'm trying to highlight:
-it can speed up and slow down instantly - its not like a disk that needs to spin
-it only runs faster when need be, but if it needs more power, even a little bit, it will use all its power
Gotcha thxs again BTW the magic horse part was pretty funny.

---

### Post by TheMixtureMedia on 2008-02-07
Hi there I have the same problem but I would like to have my full cpu power I am running Boinc and what the full speed. I am spose to have 1.6 GHZ but it tells me I am running 800MHZ. I want the more speed because Bionc will run faster.

---

### Post by Yellow Pasque on 2008-02-07
> **TheMixtureMedia said:**
> Hi there I have the same problem but I would like to have my full cpu power I am running Boinc and what the full speed. I am spose to have 1.6 GHZ but it tells me I am running 800MHZ. I want the more speed because Bionc will run faster.
When your processor is under load, it will go to 1.6GHz. It doesn't need to run at 1.6GHz when it isn't doing anything. All that does is waste power and generate heat/fan noise.

---

### Post by ryanVickers on 2008-02-07
Exactly, while running that, it *is* using the 1.6Ghz... using that all the time would just be a waste of electricity and produce extra heat.  People don't seem to realize this no matter how much you tell them, and its not a problem, it's a feature.

---

### Post by NightwishFan on 2008-02-07
I have the AMD 64 X2 3800+ and Ubuntu is such a low load normally it camps on 1ghz even when im doing normal stuff. It can also scale to other freqs I have seen it on 1500, 1800. It seems like a useful feature for overclockers.

---

### Post by ryanVickers on 2008-02-07
Only problem with that is the cooling is so good that it will heat up really quick at the higher speeds of overclocking, and then cool down really quick, which is very bad for the chip, especially if done frequently.

It would almost be better to let the chip over heat and stay there than make it fluctuate between 25 and 55 every 20 seconds :p

---

### Post by robert shearer on 2008-06-22
Does this apply to desktops as well or just laptops ??  'cause my desktop with AMD64 3000+ should report 2Ghz but only reports 1Ghz.

---

### Post by Yellow Pasque on 2008-06-22
> **robert shearer said:**
> Does this apply to desktops as well or just laptops ??  'cause my desktop with AMD64 3000+ should report 2Ghz but only reports 1Ghz.
Yes, it works on desktops too. When idle, your CPU should drop to 1.1V and 1GHz.

---

