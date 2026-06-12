---
title: "Laptop Battery"
date: 2011-07-26
forum: Hardware
---

### Post by dwally89 on 2011-07-26
Hi,

On my old laptop, I ruined the battery by keeping it plugged in whenever I was using it, meaning that if I was to actually unplug it, I'd only have about 20 minutes of battery life.
I've just got myself a new laptop, and I don't want to make the same mistake again, so I was wondering what is the best way to treat a laptop battery.
Should I run my laptop on battery mode all the time, and whenever it runs out of charge, charge it?
Should I take the battery out of my laptop and just plug it in all the time?
Or something else?

Thanks

---

### Post by haqking on 2011-07-26
> **dwally89 said:**
> Hi,

On my old laptop, I ruined the battery by keeping it plugged in whenever I was using it, meaning that if I was to actually unplug it, I'd only have about 20 minutes of battery life.
I've just got myself a new laptop, and I don't want to make the same mistake again, so I was wondering what is the best way to treat a laptop battery.
Should I run my laptop on battery mode all the time, and whenever it runs out of charge, charge it?
Should I take the battery out of my laptop and just plug it in all the time?
Or something else?

Thanks


I am guessing your older laptop was really an older laptop ? 

Newer batteries dont really suffer from that problem though some would argue it.

I personally keep my laptop plugged in all the time and if i do unplug it i still get the same life from battery that i did when latop was new.

I have a thinkpad so is good quality which i think makes a difference also though the batteries are all usually made from similar manufacturers.

---

### Post by dwally89 on 2011-07-26
> **haqking said:**
> I am guessing your older laptop was really an older laptop ? 

Newer batteries dont really suffer from that problem though some would argue it.

I personally keep my laptop plugged in all the time and if i do unplug it i still get the same life from battery that i did when latop was new.

I have a thinkpad so is good quality which i think makes a difference also though the batteries are all usually made from similar manufacturers.

My old laptop was an approximately 4 year old Dell Inspiron 6400 (got it round about when Vista was new, unfortunately...) and my new laptop is an HP Pavilion dv6.

So are you saying that it's ok for me to keep my laptop plugged in whenever I used it without worrying about the battery life being affected?

---

### Post by haqking on 2011-07-26
> **dwally89 said:**
> My old laptop was an approximately 4 year old Dell Inspiron 6400 (got it round about when Vista was new, unfortunately...) and my new laptop is an HP Pavilion dv6.

So are you saying that it's ok for me to keep my laptop plugged in whenever I used it without worrying about the battery life being affected?

oh right well not that old then.

the thing is there are lots of schools of though on the subject, you can find as many sites dedicated to battery care that say remove it, as well as many that say it is fine to leave in.

There is a difference between nicad and nickel metal hydride and lithium ion and lithium polymer etc etc.

I think to be honest it is personal preference really, like i said mine is plugged in all the time but that doesnt mean it is the best thing for it, conversely it happens to be fine when i unplug it and it is a 2007 Thinkpad.

Basically it wont harm it to remove battery thats for sure so if plugged in all the time then by all means remove it and pop it in once and a while to charge it.

I dont think it is possible to say one way or other these days as everyone seems to have different experiences and schools of thought, what works for one doesnt for another, also alot depends on quality of battery and manufacturer etc

---

### Post by pjd99 on 2011-08-03
If you really want to get the most life out of the battery then  discharge it to 40% and store in a cool, dry place. Li-ion batteries  lose capacity over time. Temperature and charge affect the rate of loss  of capacity. At 100% charge and 25 degrees C, you'll lose ~20% per year.  Same temperature and 40% charge, it'll be about 4%.

The battery  in my Vostro 1710 is at 57% of its original capacity after 2.5 years. I  keep it plugged in nearly all of the time, and now it struggles to get  through a 2 hour lecture on battery alone.
```

cat /proc/acpi/battery/BAT1/info

present:                 yes
design capacity:         57720 mWh
last full capacity:      33050 mWh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 1652 mWh
design capacity low:     991 mWh
cycle count:          0
capacity granularity 1:  264 mWh
capacity granularity 2:  3780 mWh
model number:            
serial number:           11
battery type:            Lion
OEM info:                Dell

```Of course, if it's not plugged in, your laptop wont be able to sustain itself through a power dip.

More info: [http://batteryuniversity.com/learn/article/how_to_prolong_lithium_based_batteries](http://batteryuniversity.com/learn/article/how_to_prolong_lithium_based_batteries)

---

### Post by dwally89 on 2011-08-07
In the end, I have decided to run my laptop off the mains, without the battery being in, and then about once a month, to go through a full charge cycle of the battery, and of course, to use the battery if I need to take my laptop somewhere during the month where I won't have access to a plug socket.

Now I'm not sure if this is related or not, but I think it might be.
Over the past few days, I have noticed the clock on my laptop reset itself about 3 times.
I am using Windows 7 as my primary operating system, and have it set up to synchronise it's clock over the internet.
Could it be possibly that when the laptop is off, and doesn't have the battery plugged into it, that it's not able to keep the clock running?
I thought that computers are meant to have a small battery on the motherboard for this purpose?

Thanks

---

### Post by pjd99 on 2011-08-08
I remember having clock problems years ago. They were related to the different way linux and windows use the system clock. Windows uses (or at least used) local time, whereas linux uses UTC, the local time you see on the clock is based on your location (which will use the correct GMT/UTC offset).


Either edit the windows registry to use UTC, or modify the linux clock to not use UTC.
Fixes:
[http://answers.microsoft.com/en-us/windows/forum/windows_7-performance/does-windows-7-use-utc/e722ad92-a65b-4c0a-8c05-b8a84fb155d1](http://answers.microsoft.com/en-us/windows/forum/windows_7-performance/does-windows-7-use-utc/e722ad92-a65b-4c0a-8c05-b8a84fb155d1)
[http://lifehacker.com/5742148/fix-windows-clock-issues-when-dual+booting-with-os-x](http://lifehacker.com/5742148/fix-windows-clock-issues-when-dual+booting-with-os-x)

---

### Post by dwally89 on 2011-08-08
> **pjd99 said:**
> I remember having clock problems years ago. They were related to the different way linux and windows use the system clock. Windows uses (or at least used) local time, whereas linux uses UTC, the local time you see on the clock is based on your location (which will use the correct GMT/UTC offset).


Either edit the windows registry to use UTC, or modify the linux clock to not use UTC.
Fixes:
[http://answers.microsoft.com/en-us/windows/forum/windows_7-performance/does-windows-7-use-utc/e722ad92-a65b-4c0a-8c05-b8a84fb155d1](http://answers.microsoft.com/en-us/windows/forum/windows_7-performance/does-windows-7-use-utc/e722ad92-a65b-4c0a-8c05-b8a84fb155d1)
[http://lifehacker.com/5742148/fix-windows-clock-issues-when-dual+booting-with-os-x](http://lifehacker.com/5742148/fix-windows-clock-issues-when-dual+booting-with-os-x)

I don't think it's to do with that, because I'm using a new computer and haven't install Ubuntu yet.

---

### Post by pjd99 on 2011-08-11
> **dwally89 said:**
> I don't think it's to do with that, because I'm using a new computer and haven't install Ubuntu yet.

Ah. You said Win 7 was your **primary OS** on that machine, so I thought you were dual-booting.

When you say reset, does it always reset to the same or similar time and date? That to me would indicate that the CMOS battery (or whatever the laptop equivalent is called) is bad or not making a good connnection. Or it may simply not have one, and rely on a capacitor to keep the clock running if the system loses all of its power sources.

---

### Post by mmsmc on 2011-08-11
in previous experiences, i have been able to extend my battle life by keeping it plugged in until it is fully charged, then keeping unplugged until it is about to shut off :D

---

### Post by imortalninja161 on 2011-08-11
This is a good thread and i have been wondering about this stuff as well  good info and yer batterys just die over the  years lol. i don't know much about battery but i know there are 6 cell and 12 cell batterys when ya by ya laptop try and by it with a 12 apossed to a 6cell they are meant to hold charge longer i think.

 	Code:
 	cat /proc/acpi/battery/BAT1/info  present:                 yes design capacity:         57720 mWh last full capacity:      33050 mWh battery technology:      rechargeable design voltage:          11100 mV design capacity warning: 1652 mWh design capacity low:     991 mWh cycle count:          0 capacity granularity 1:  264 mWh capacity granularity 2:  3780 mWh model number:             serial number:           11 battery type:            Lion OEM info:                Dell 
and whats the syntax for the command you used 


thanks 
imortalninja61

---

### Post by pjd99 on 2011-08-11
> **imortalninja161 said:**
> This is a good thread and i have been wondering about this stuff as well  good info and yer batterys just die over the  years lol. i don't know much about battery but i know there are 6 cell and 12 cell batterys when ya by ya laptop try and by it with a 12 apossed to a 6cell they are meant to hold charge longer i think.

and whats the syntax for the command you used 


thanks 
imortalninja61
The number of cells is related to the cell voltage and capacity. Li-ion cells are about 3.7V each. A 4 cell battery will usually have a voltage of about 14.8V, a 6 cell would be 11.1V (3*3.7V, in 2 sets) or 22.2V (6*3.7). Arrange the cells in a serial fashion and you get the voltages adding, in a parallel arrangement the capacity will increase (i.e. It will be able to deliver the same current for about twice as long).

```
[FONT=monospace]
[/FONT]cat /proc/acpi/battery/BAT1/info

```This works on my laptop, yours might be slightly different. Once you get it to "cat /proc/acpi/battery", hit TAB a few times and you should see the options available. A lot of the information is available via the battery monitor panel app if you don't want to use the terminal.

---

### Post by dwally89 on 2011-08-11
> **pjd99 said:**
> Ah. You said Win 7 was your **primary OS** on that machine, so I thought you were dual-booting.

When you say reset, does it always reset to the same or similar time and date? That to me would indicate that the CMOS battery (or whatever the laptop equivalent is called) is bad or not making a good connnection. Or it may simply not have one, and rely on a capacitor to keep the clock running if the system loses all of its power sources.

From what I can see, it resets to whatever time I shut the computer down at.
The clock seems to have been fine over the past few days though.

---

### Post by seicean on 2011-08-11
Same issue here, but I talked to an expert and got a few things cleared up...

1. modern li-ion batteries have about 600-700 charge cycles (~1 - 1.5 years)

2. NEVER let the battery drain to 0%, or you will kill it softly (I'd recommend plug it in again at 20-25%)

3. Make sure that it never boils (ex: OS install, game playing, etc... will make the computer a bit warm - therefore the battery can catch a bit)

4. it doesn't hurt the battery if you leave it plugged in for a long period of time (up to multiple weeks). it is recommended to plug it out once in a while and have a go on the discharge.

5. as far as my experience goes with mobile computing, SONY and SAMSUNG batteries have the most overall life

hope this helps...

---

### Post by pjd99 on 2011-08-11
> **seicean said:**
> 
2. NEVER let the battery drain to 0%, or you will kill it softly (I'd recommend plug it in again at 20-25%)


This shouldn't be an issue. The control electronics in modern Li-ion batteries make "0%" well above the minimum safe level. The only way to get it to completely discharge is if you drain it, then let it self discharge, which will take some months.

See it all the time with Li-ion power tools. They just hammer along then suddenly stop, whereas Ni-Cd and Ni-MH fade.

---

### Post by seicean on 2011-10-01
Running Ubuntu 11.04 and W7 for a while now and the scenario is the same... 

still the same battery: (1-3 months scenario)

ubuntu: 1:45
W7    : 2.50

the heat problem can be resolved by some simple vacuum. 

drivers are getting crazy. others have some more info. sorry.

---

### Post by diasf on 2011-10-01
Just a random info.

I have a 6400 as well, and I think the fact you left it always plugged had nothing to do with the problem. I do (and i know at least 2 other ppl with the same laptop/behaviour) leave it plugged and never got any problems with it. My battery did die a while ago, when i hooked it to a friends' car sound system. But it went from normal to dead in a week or so.

---

### Post by parth.s on 2011-10-01
Got a new laptop 20 days ago. And I had the same concern about the battery. But from what I have gathered, 
Laptops do switch off (internally) the power supply to the battery once it is charged: in my case, the charger becomes comparatively hotter when im running my laptop from the A/c mains while the battery is charging, than directly from the A/c mains sans the battery (in which case its slightly warm). That said it cools down after the battery is charged, because it no longer has to power both the battery and the laptop.
And its a bad idea to fully charge the battery and store it.

---

### Post by Abhinav Kumar on 2011-10-01
Earlier  i was keeping my battery plugged in without caring for power getting on/off. But after 11 months the battery backup was about 10 min. Ultimately i had to change the battery . Now i make battery complete a cycle of full charge and then run without AC mains to about 30 % discharge. Backup is now 2 hrs even after 10 months :)

---

### Post by diasf on 2011-10-02
To always cycle the battery is a bad, bad idea.

Each battery has a finite number of power cycles. If you keep using it, it will die sooner.

Further, most of the logic here is flawed. You can't possibly say that plugged/unplugged is the *only* factor contributing to battery health. This ignores the quality of the battery for starters. Even from the same "brand", the cells can be provided by different suppliers with different qualities.

And as counter-example, I have 3 laptops, one from 2007, 2 from 2009. Always kept them plugged on table, unplugged on other places (basically I don't care for the battery). All 3 of them still have the capacity they had when new.

One of the things that ppl usually forget is that what you are running matters. If you keep playing hardcore games (or something else that uses a lot of power, like DVD burning, etc) while on battery, it will wear the battery sooner. So a valid tip is to plug it to run heavy stuff.

And never, never hook up the audio output to a car's sound system input. Never :)

---

