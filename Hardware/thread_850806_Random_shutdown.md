---
title: "Random shutdown"
date: 2008-07-06
forum: Hardware
---

### Post by oobe-feisty on 2008-07-06
Hi there i just bought a new pc its cheap deal nothing fancy 

m2n-mx se plus motherboard
5600+ AMD 
1 GB kingston value ram 
250 GB seagate 
cheap case with built in generic PSU 

it works fine in windows even with stress tests like sisoft and prime95 

but in kubuntu 8.04 it keeps shutting down randomly i cant find anything in the logs to indicate what it is doing i have checked /var/log/messages /var/log/syslog and dmesg 

I tried noapic and apci=off in grub to no avail  

I tried installing mythdora to test if its ubuntu specific problem and it shutdown during install which doesnt surprise me 
as i suspected it wasnt ubuntu however i will mention i used the 
text based alternate install the other install wouldnt work 

i am suspecting it is the PSU however i think it may be more to do with software issues as windows tests fine i dont want to fork out for a new PSU and install it just to find out it still happens.

does anyone have any suggestions of things i might try?

thanks in advance

P.S i will post back later with some logs close to times where it shutsdown

---

### Post by phaid on 2008-07-06
One thing to look at, just to rule it out as an issue. Is a quick and easy check to see what the bios are doing.

Restart the computer, go into the bios, and see if the bios are handling power management, temp control, etc.  It could be that the bios are turning the system off when it reaches a certain threashold like  heat/activity/something

  If that is the issue, then try to see what it was doing and then disable it.  You might need to be careful with something like a cpu temperature probe - your windows machine might have been doing management to keep it under range or something like that.

---

### Post by oobe-feisty on 2008-07-06
> **phaid said:**
> One thing to look at, just to rule it out as an issue. Is a quick and easy check to see what the bios are doing.

Restart the computer, go into the bios, and see if the bios are handling power management, temp control, etc.  It could be that the bios are turning the system off when it reaches a certain threashold like  heat/activity/something

  If that is the issue, then try to see what it was doing and then disable it.  You might need to be careful with something like a cpu temperature probe - your windows machine might have been doing management to keep it under range or something like that.

thanks for your reply your on the right track but i dont seem to be able to find threshold settings in the bios however im starting to think its the CPU temp as when i check its almost at maximum its 68 degrees on idle max is 70 it has a stock amd HSF
and no case fan im gonna buy a new HSF tommorow and try it out

---

### Post by oobe-feisty on 2008-07-06
just an update i was able to consistently get it to shutdown 2 mins into a kernel compile so i tried it with the case open and it shutdown 15 mins into it so i definately am going to get a new HSF tomorrow and maybe a case fan i only hope this works 100% as appose to making it just less frequent however my cpu temps are often close to max so I'm guessing if i can get it down to 40 degree's at load then it should be OK ( did i mention im not over clocking?).

---

### Post by ukripper on 2008-07-06
> **oobe-feisty said:**
> just an update i was able to consistently get it to shutdown 2 mins into a kernel compile so i tried it with the case open and it shutdown 15 mins into it so i definately am going to get a new HSF tomorrow and maybe a case fan i only hope this works 100% as appose to making it just less frequent however my cpu temps are often close to max so I'm guessing if i can get it down to 40 degree's at load then it should be OK ( did i mention im not over clocking?).

i personally think it is a fan but you can check when you are logged into kubuntu just install mbmon:
```
sudo apt-get install mbmon
```

and then run it in terminal:
```
sudo mbmon
```

see the output of cpu fan and temperature of MB and cpu will show up.

---

### Post by oobe-feisty on 2008-07-07
Problem solved I'm so glad i was able to reproduce the shutdowns consistently by compiling the kernel this took out a lot of the guess work 

it was the stock HSF i put on a zalman 9500-am2 i chose it cause it did not require a back plate and was pretty easy to install. 

However I would like to have a small rant about the AM2 stock HSF i do not OC and consider what I do on my PC to fall under ordinary use as far as cpu strain and the fact that the stock HSF was not suitable for ordinary use is unreasonable i was trying to figure it out for days before i posted and was not happy that the solution was replacing a component on a brand new PC with warranty. 

anyway enough of my rant thanks guys for your replies

---

### Post by ukripper on 2008-07-07
> **oobe-feisty said:**
> Problem solved I'm so glad i was able to reproduce the shutdowns consistently by compiling the kernel this took out a lot of the guess work 

it was the stock HSF i put on a zalman 9500-am2 i chose it cause it did not require a back plate and was pretty easy to install. 

However I would like to have a small rant about the AM2 stock HSF i do not OC and consider what I do on my PC to fall under ordinary use as far as cpu strain and the fact that the stock HSF was not suitable for ordinary use is unreasonable i was trying to figure it out for days before i posted and was not happy that the solution was replacing a component on a brand new PC with warranty. 

anyway enough of my rant thanks guys for your replies

i never rely on stock HSF, either for AMD or Intel. When assembling I always choose the zalman. Stock HSF are meant to be replaced are pretty tacky.

---

### Post by oobe-feisty on 2008-07-07
i agree but i still think they should atleast be usable

---

