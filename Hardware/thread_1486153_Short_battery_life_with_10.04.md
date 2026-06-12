---
title: "Short battery life with 10.04"
date: 2010-05-17
forum: Hardware
---

### Post by andlinux on 2010-05-17
I'm using ubuntu for several years now and a week after 10.04 was released I upgraded my laptop with it. 
The problem is when I'm using my laptops battery power. If I'm just reading a text on the net then I see my battery power dropping at an enormous level. 
Now I can use my laptop one hour and when I had ubuntu 9.10 I could use it for about 3 hours. 
My laptop is 1.5 years old and it's a compal JHL90, the battery problem started when I upgraded to 10.04.

So my question is: are there more people with this problem ?

---

### Post by lidex on 2010-05-17
Tips here:
[http://www.linwik.com/wiki/increasing+battery+life+under+linux]("http://www.linwik.com/wiki/increasing+battery+life+under+linux")

---

### Post by andlinux on 2010-05-21
The kernel scheduler is the problem why I'm losing so much power.

I monitored it with powertop.

Top causes for wakeups:
  40,5% (108,7)   [kernel scheduler] Load balancing tick

Sometimes lower sometimes more.

---

### Post by yossell on 2010-05-22
I've just changed to 10.04 from 9.04, and haven't yet had enough time to get a good feel for how battery life has been affected - but, like you, powertop's readings paint a very different picture of wakeups. Under 9.04, and in an openbox session, I could get wakeups-from-idle down to under 10 a second, if I wasn't doing too much - and averaging about 50. It made a big difference to battery life. Under 10.04, I don't see it under a hundred, with that load balancing tick being a major reason. I thought it would be a problem.

However, surprisingly,  under an openbox session, my average power usage readings under powertop were pretty low, lower than before, even with the greater number of wakeups caused by load balancing, and the battery drainage seemed to be slightly slower than before. 

I've not tried this out enough in the real world to be sure that these figures are correct, how things work out in gnome - my openbox sessions are very minimal (no wireless, no fancy graphics, just work), and I'm not sure why I seem to be getting better battery life despite the extra wakeups here - but it may not be those extra wakeups that are causing the problem.

---

### Post by lisati on 2010-05-22
I had to tinker with cpu scaling on my Toshiba laptop once I put 10.04 on it. I've noticed that 10.04 sometimes retains the "performance" setting if I've been using Windows even though I usually have 10.04 set to "on demand".

---

### Post by Aditya Bhavaraju on 2010-05-22
> **andlinux said:**
> I'm using ubuntu for several years now and a week after 10.04 was released I upgraded my laptop with it. 
The problem is when I'm using my laptops battery power. If I'm just reading a text on the net then I see my battery power dropping at an enormous level. 
Now I can use my laptop one hour and when I had ubuntu 9.10 I could use it for about 3 hours. 
My laptop is 1.5 years old and it's a compal JHL90, the battery problem started when I upgraded to 10.04.

So my question is: are there more people with this problem ?
Don't worry we are all experiencing the same problem as you are.Hope it will be resolved soon.Look forward for updates...
cheers
Aditya Bhavaraju

---

### Post by andlinux on 2010-05-22
> **Aditya Bhavaraju said:**
> Don't worry we are all experiencing the same problem as you are.Hope it will be resolved soon.Look forward for updates...
cheers
Aditya Bhavaraju

It's good to know that I'm not the only one. ;)

---

### Post by Applelnx on 2010-09-07
Hi, any luck with this issue? I'm having the same problem and my battery life is only 30 minutes long :s

---

### Post by andlinux on 2010-09-08
> **Applelnx said:**
> Hi, any luck with this issue? I'm having the same problem and my battery life is only 30 minutes long :s
It's better now, probably because of a kernel update.

---

### Post by ttreadway81 on 2010-09-21
I have the 30 minute limit myself.  I wonder if it is an Ubuntu issue or an actual issue with the battery.  The laptop is feeling its age a little.

---

### Post by Applelnx on 2010-09-21
> **ttreadway81 said:**
> I have the 30 minute limit myself.  I wonder if it is an Ubuntu issue or an actual issue with the battery.  The laptop is feeling its age a little.

I believe it's the Ubuntu Power Manager. When my battery gets to 25%, the laptop shuts down automatically.

Something is wrong when Ubuntu boots. See the /var/log/dmesg:

```
[   0.358998] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[   0.360329] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
...
[  21.060834] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
```

---

### Post by ttreadway81 on 2010-09-21
I checked the same log, and I didn't see what you pointed out.  It seems that my battery can only provide 30 minutes of power when fully charged.  That is the way it's been since I installed Ubuntu.  Even the old XP install got at least twice as much life.

---

### Post by Axx83 on 2010-09-22
try this:

[http://ubuntuforums.org/showpost.php?p=8315253&postcount=1]("http://ubuntuforums.org/showpost.php?p=8315253&postcount=1")

ONLY the part where is says usb auto suspend

---

### Post by ttreadway81 on 2010-09-23
Thanks.  It doesn't do much, but it would help if I have anything attacked while on battery.  Although, it seems that the short life still persists.  Would anyone recommend this powertop I keep hearing about?

---

### Post by Axx83 on 2010-09-24
you could try the 64 bit version of ubuntu, if you don't have already, otherwise if you want to keep your installation a standard one (heavily recommended) there is not much else you can do.

Powertop only tells you what program is using more cpu and your average power consumption, plus some tips but most of them are already implemented. Try it out anyway, it's very useful.

My battery life is just as bad as yours, in windows xp it was just a little bit more, 1h30m instead of 1h, I think it's not a vanilla linux problem but essentially it's the way ubuntu is built, very generic and not that well optimized for battery usage.

---

### Post by ttreadway81 on 2010-09-24
You may be right, this battery issue seems to be more on the nature of Ubuntu than anything else.  Oh well, I guess I can try to tweak as best I can.  Hopefully we can get better battery management built into the OS in the future.

---

### Post by andlinux on 2010-09-24
I had no problems with the previous versions of ubuntu but 10.04 was a disaster after I upgraded.

---

### Post by Axx83 on 2010-09-25
well yes 10.10 is only a few weeks away, try that, otherwise try a fresh installation of 10.04

---

