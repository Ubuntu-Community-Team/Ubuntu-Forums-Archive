---
title: "Overheating Desktop"
date: 2013-01-09
forum: Hardware
---

### Post by ivotkl on 2013-01-09
Ok, so I have my desktop with overheating issues.

Outside temperature was around 30ºC the last few days and computer's CPU and integrated graphics went up to critical temps a few times (between 50 and 70), causing system sudden shutdown. I have changed silicone compound less than a month ago and I've cleaned fans 3 days ago.

Additional fans are only one on the rear, outtake. I had to leave case open with a 60 cm diameter fan at a distance between 1.5 and 3 metres. Current temperature, 2 browsers with 4 tabs opened in total and music streaming.

I would like a permanent solution that does not involve this current settings or water-cooling. None of the components is overclocked.

Current sensors outputs are:
```
temp1:        +21.0°C  (high = +85.0°C, hyst = +81.0°C)
                       (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor
temp2:          FAULT  (high = +85.0°C, hyst = +81.0°C)
                       (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor
temp3:        +36.0°C  (high = +70.0°C, hyst = +68.0°C)
                       (crit = +85.0°C, hyst = +83.0°C)  sensor = transistor

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:   +30.0°C  
Core0 Temp:   +31.0°C  
Core1 Temp:   +36.0°C  
Core1 Temp:   +32.0°C
```

Thank you.

---

### Post by TenPlus1 on 2013-01-09
Some information on your system would be handy like Ubuntu version, your processor, graphics card ?

---

### Post by gordintoronto on 2013-01-09
70 should not be a critical temperature. 95 C is a critical temperature.

If I play videos, my laptop can get up to 80, and that's OK.

---

### Post by Yellow Pasque on 2013-01-10
If the overheating started happening after you reinstalled the heatsink, you may not have done it correctly..

> **gordintoronto said:**
> 70 should not be a critical temperature.
70C is at the high end for desktop CPU's. Most desktop chips are rated for 60-70C max.

---

### Post by ivotkl on 2013-01-10
Let's hope [this](http://pastebin.com/kjVJGFwj) answers your question. =)

I've even opened PSU to clean it and I've seen some brownish thing coming out of some capacitors. I've asked an IT employee at work and he told me malfunctioning PSU could be giving wrong voltage to MoBo and/or components, which causes overheating.

---

### Post by whatthefunk on 2013-01-10
Your case only has one fan?  Maybe you should get a new one that has at least two.  What kind of CPU cooler do you have?   I hope youre not using the one that came with your CPU...those are typically junk.

The outside temperature gets above 40 here in the summer and Ive never seen my CPU temp go above 55.  My case has two fans and I have a nicer after-market CPU cooler.

---

### Post by tlhIngan on 2013-01-10
> **Temüjin said:**
>  70C is at the high end for desktop CPU's. Most desktop chips are rated for 60-70C max.

> **whatthefunk said:**
> The outside temperature gets above 40 here in the summer and Ive never seen my CPU temp go above 55.

Intel CPU's run much cooler than AMD CPUs and have a different threshold temperature. Until we know what CPU he's running, although I suspect it's an AMD, we should keep these opinions to ourselves.

Like the man said, if this overheating started after you cleaned the CPU cooler, you may have reinstalled it incorrectly or not have put enough silicone compound on it.

Mine is tricky to keep cool, and I've found positioning a fan to blow air on the GPU side of the graphics card towards the back of the case (with all slots opened up) helped keep the case temperatures  about 5C cooler, and that in turn helped keep the CPU temps 2-3C cooler.
That being said, mine still idles at 50C on a warm day and can reach 60C under load.

---

### Post by Yellow Pasque on 2013-01-10
> **tlhIngan said:**
> Intel CPU's run much cooler than AMD CPUs 
This is only true for the current generation of AMD CPU's (FX/Bulldozer). AMD had some very efficient chips in the K8 days and even the Phenom/II series wasn't bad. Personally, I have a 45W TDP Brisbane-based 5050e in our living room PC and it runs really cool especially since it runs stable even with further undervolting. ;) 

>  (Intel and AMD) have a different threshold temperature.
Yeah, every chip's a bit different, but most desktop chips I've seen have max temps in the 60-70C range. The OP looks to have a dual-core K8 so something like this might be a good reference for max temp (68C): [http://products.amd.com/pages/desktopcpudetail.aspx?id=40&AspxAutoDetectCookieSupport=1](http://products.amd.com/pages/desktopcpudetail.aspx?id=40&AspxAutoDetectCookieSupport=1)

> Until we know what CPU he's running, we should keep these opinions to ourselves.
(EDUCATED) OPINION: 70C is cause for worry on a K8 chip, epecially if you're reaching that temp without having both cores loaded. I did have an AMD X2 5000 that I burned out by trying to run it passively (I'm a silence freak) as it was near/a bit over max temp under full load. Doing a Fedora install killed it one day.
Unrelated note: a cheap 120mm Yate Loon fan running off 5V makes a world of difference in tenmps and it hardly makes any noise.

---

### Post by ivotkl on 2013-01-10
CPU Cooler is the factory one, I'm planning on changing whole computer once I'm able to get the money. But I would like to save as much as possible with current one as I find it hard to get it.
 
It also has a rear 8mm fan which I bought a few weeks ago.
 
CPU is AMD64 X2 4800+.
 
Full box specs are [here]("http://pastebin.com/s87GdBXd").
 
**How do I go about undervolting to guarantee lower temperatures?** (It's pure electric physics, so less voltage would mean less watts consumed = less heat produced).
 
**Edit: **I have cleaned it and reapplied compund after overheating started. Is there any how-to on applying compound? I can try again.

---

### Post by whatthefunk on 2013-01-10
How much compound are you putting on?  I put a small dot on each surface and spread a very thin layer over them with a credit card.  You dont want a lot...just enough to fill in any imperfections in the metal surfaces.  Keep in mind that most compunds take a week or two to set so if youve applied it correctly, you should see a drop in temperature in ten days or so.

---

### Post by ivotkl on 2013-01-10
That's what I did. I was adviced to place a tiny dot and spread on small surfaces and like a dice's 5 figure on larger ones. I applied it a long time ago (let's say a month maybe) and even cleaned surface to remove trace of previous compound.

Should I re-apply it? How do I know if PSU is faulty?

---

### Post by Yellow Pasque on 2013-01-10
> and even cleaned surface to remove trace of previous compound.
How did you do this? I generally use 90% rubbing alcohol.

---

### Post by ivotkl on 2013-01-10
If by "rubbing alcohol" you mean rubbing a piece of cloth / gauze / cotton / etc. soaked in alcohol, then I did the same with 97% v/v alcohol (the one usually sold here at the chemist's). Then waited until it went fully dry and reattached everything back.

**Edit/update:** I believe factory settings fan was intake. Should I change it to outtake?

---

### Post by ivotkl on 2013-01-12
Shameless bump. =(

---

### Post by Yellow Pasque on 2013-01-12
Okay, since the overheating started before you (re)applied the heatsink, then I would think that the thermal compound is not the problem.

The next thing to check is whether your CPU fan runs at full speed. I would go into the BIOS and disable the "SmartFan" function so that the fan runs at full speed all of the time. If that solves the overheating, then the BIOS fan control is not working properly (note that there's a BIOS update with a fan fix: [http://www.msi.com/product/mb/K9AGM4.html#/?div=BIOS](http://www.msi.com/product/mb/K9AGM4.html#/?div=BIOS) )

If having the CPU run at full speed is not working, then perhaps your case needs more ventilation (run more case fans and/or run them at higher speed). I had an MSI  mobo very similar to yours with the 690G chipset and that northbridge/GPU got HOT. (Personal note: MSI also did a shoddy job with the northbridge heatsink and used really cheap thermal compund. That was the last MSI mobo I ever bought).

---

### Post by ivotkl on 2013-01-12
Temûjin: Thank you for your reply on both threads. I have done that, but it is merely running at 990 - 1k RPM. I definitely need a better fan. If by northbridge you refer to the one that is near PCI slots, then yes it is hotter than the other one and has a lower quality heatsink (by that I mean smaller).
 
I already changed thermal paste as explained before. Current settings are open case, 1 extra fan and one 50cm diameter fan at full speed (unsure about RPMs on that one as it is meant for humans, haha) pointing at the mainboard.
 
By the way, I'm currently using sound converter (bitrate and format converter progream) and...
```
$ top
 
top - 11:12:54 up 53 min,  2 users,  load average: 2.51, 2.37, 1.88
Tasks: 178 total,   2 running, 175 sleeping,   0 stopped,   1 zombie
Cpu(s): 91.7%us,  6.8%sy,  0.0%ni,  1.5%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1931996k total,  1519544k used,   412452k free,     6848k buffers
Swap:  1052220k total,    54996k used,   997224k free,   779480k cached
 
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2851 ivan      20   0  230m  56m  18m R  183  3.0  41:03.62 /usr/bin/soundc
```
 
183% CPU usage? Is that reading correct? =S
 
***EDIT:*** Deming... I honestly could not understand what you've said, sounds like Indian-English (no offence, I have an Indian friend and love her). However, it is obvious that PSU gives power to computer. What do you mean by "All back-up in a PC receive their DC power via the power supply."
 
Oh, one more thing Deming. If you're trying to promote computers gold coast, let me remind you this is a support forum and not a shop or newspaper free-announcing site. Even if it was ethically correct for you to promote such site, you would definitely need to work on the advertising. I recommend you using better sentences. No harm intended, just giving my point of view.

---

