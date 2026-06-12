---
title: "[SOLVED] Games freezing after 5 minutes"
date: 2007-06-24
forum: Hardware &amp; Laptops
---

### Post by greg_g on 2007-06-24
So, I am having issues with my system completely freezing when playing most games for more than 5 minutes.

Symptoms: My system runs fine, completely fine, until I want to play a game.  I had my system up for 4 days doing basic stuff (non-game).  Once I play a game it crashes in around 5 minutes.

Hardware: Intel Core2 Duo E6400 2.13 GHz
2 gig memory
nVidia 7100GS 128
ASUS P5VD2 VM motherboard

and I'm running Fiesty.

Yes, it isn't a gaming rig spec wise, but the games that make it freeze are Planet Penguin Racer and Nexuiz, not the most advanced games in the world.

What things should I look at for diagnosing the issue?

Thanks in advance,

greg

---

### Post by yabbadabbadont on 2007-06-24
Install some temperature monitoring software and see if it might be overheating.

---

### Post by greg_g on 2007-06-24
Here are two logs of my sensors output using a cron job for every minute.

I'm not sure about temperatures so if you could take a look at them for me that would be great.  Search for "CRASH" to find the points where I labeled when it froze.

Thanks,

greg

---

### Post by yabbadabbadont on 2007-06-24
Well, it claims that the temperature of your motherboard got up to 52°C...  That would be bad if true.  CPU getting that hot is not unusual, at least not for an AMD processor.  I don't know what the valid range is for Intel.  Either way it appears that there is a temp problem of some sort.

---

### Post by greg_g on 2007-06-24
Thanks for the help yabbadabbadont,

I'm going to reboot and try to manually set the fan speed.  I have noticed (during the many restarts) a message on boot up about "Fan Setting: Auto" or some such.  I'll take a look at that and report back.

Thanks again,

greg

---

### Post by Super TWiT on 2007-06-24
My motherboard has reached that temperature before. Is that temperature too high? Maybe I need to buy some more fans.  My airflow is pretty bad.

---

### Post by Super TWiT on 2007-06-24
> **yabbadabbadont said:**
> Well, it claims that the temperature of your motherboard got up to 52°C...  That would be bad if true.  CPU getting that hot is not unusual, at least not for an AMD processor.  I don't know what the valid range is for Intel.  Either way it appears that there is a temp problem of some sort.


My motherboard has reached that temperature before. Is that temperature too high?  Maybe I need to buy more fans.  My airflow is pretty bad.

---

### Post by Super TWiT on 2007-06-24
Sorry for posting the same thing twice.  I admit I don't know how to delete my posts.:D

---

### Post by greg_g on 2007-06-24
Well, I took a look at the BIOS settings, and the only thing related to the fan I could set was the fan speed warning (set at 600, options for 1000 and 1300 I believe, or around there).  Nothing about setting fan speed.

Btw, the last crash has happened with the side of the case off, in a room about 72 degrees F, which is 20/21 C I believe.

So do we think this is a heat thing?  Or is it possibly a video card thing?  Maybe video card heat thing because the card is one of those fanless models.

thanks,

greg

---

### Post by Super TWiT on 2007-06-24
I have heard that running with the side off actually makes the computer run warmer because it disrupts the airflow.

---

### Post by greg_g on 2007-06-24
Yeah, I was just testing all configurations, trying everything.

Side is back on now though :)

---

### Post by Super TWiT on 2007-06-24
Okay, just thought I should let you know about that.;)  It doesn't seem like the computer should freeze up like that though.

---

### Post by greg_g on 2007-06-25
Anymore ideas to help diagnose what is causing this problem?

---

### Post by Super TWiT on 2007-06-25
You couId try putting in more fans I guess.

---

### Post by greg_g on 2007-06-29
Turns out it was overheating.

Thanks for all the help community.


greg

---

