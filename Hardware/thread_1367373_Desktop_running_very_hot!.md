---
title: "Desktop running very hot!"
date: 2009-12-29
forum: Hardware
---

### Post by jmvbxx on 2009-12-29
My computer is running very hot and I can't seem to figure out why.

I have 64-bit intel on intel motherboard w/ 3GB of ram.

Here is sensor output:

Sys Temp:   +101.0°C  (high = +96.0°C, hyst = +96.0°C)  ALARM  sensor = diode
CPU Temp:    +90.0°C  (high = +80.0°C, hyst = +75.0°C)  ALARM  sensor = diode

I even bought a brand new fancy heat sink and my temps didn't drop at all.

Any help/guidance will be much appreciate!

---

### Post by lukeiamyourfather on 2009-12-29
Are you sure those are Celsius, and are you sure the sensors are accurate? When you touch the heatsink does it burn your finger or does it feel slightly warm?

---

### Post by jmvbxx on 2009-12-29
Just putting my fingers near it while running and I can feel that it's hot!

I'm also getting near perpetual warnings is

/var/log/messages
/var/log/syslog
/var/log/kern.log

Sample:
Dec 29 13:21:19 j-a kernel: [ 2420.156495] CPU1: Temperature above threshold, cpu clock throttled (total events = 138532)
Dec 29 13:21:19 j-a kernel: [ 2420.156523] CPU0: Temperature above threshold, cpu clock throttled (total events = 138540)
Dec 29 13:21:19 j-a kernel: [ 2420.174517] CPU1: Temperature/speed normal
Dec 29 13:21:19 j-a kernel: [ 2420.174529] CPU0: Temperature/speed normal
Dec 29 13:21:19 j-a kernel: [ 2420.178935] CPU1: Temperature above threshold, cpu clock throttled (total events = 138533)
Dec 29 13:21:19 j-a kernel: [ 2420.178964] CPU0: Temperature above threshold, cpu clock throttled (total events = 138541)
Dec 29 13:21:19 j-a kernel: [ 2420.198432] CPU1: Temperature/speed normal
Dec 29 13:21:19 j-a kernel: [ 2420.198436] CPU0: Temperature/speed normal
Dec 29 13:21:19 j-a kernel: [ 2420.202028] CPU1: Temperature above threshold, cpu clock throttled (total events = 138534)
Dec 29 13:21:19 j-a kernel: [ 2420.202047] CPU0: Temperature above threshold, cpu clock throttled (total events = 138542)

---

### Post by MooPi on 2009-12-29
How old is computer and did you build it ?

---

### Post by jmvbxx on 2009-12-29
The processor is older (approx 4 yrs) and the rest is new (less than 6 mths) and yes I built it.

---

### Post by MooPi on 2009-12-29
Sounds as if maybe the heatsink  and fan assembly isn't attached properly. You may need to remove the heatsink and reapply thermal paste and make certain that the heatsink is seated properly. No level of CPU activity should raise your temps that high. I'm surprised that your motherboard didn't shut it down prior to getting that high.

---

### Post by jmvbxx on 2009-12-29
My previous heatsink only had 3 good clips on it so I thought that was the issue.  I bought a new one and it is properly installed with silicon.

I'm going to reboot and see what the bios says the temp is.

Lately I've been having hardware issues (for example not going past bios screen - even the computer rebooting itself if moved) and then finally the whole system went wonky and I isolated it to a ram issue.  I just replaced the ram today so I can't be completely sure of my diagnosis.

---

### Post by lukeiamyourfather on 2009-12-29
That's really hot. Does it get that hot right away or does it take a while? It could be the system doesn't have enough ventilation (like stuck in a wood desk cabinet). If only one sensor was getting hot I'd say its a thermal paste issue or a heatsink clamp issue but with more than one it seems to be related to the environment the computer is in or the case fans. Cheers!

---

### Post by jmvbxx on 2009-12-29
I checked the bios and the temps are 60C cpu and 75C for the motherboard.

I'm currently using 9.10 64-bit and about 20 min ago I booted via USB into an old 7.10 hdd.  So far no overheating at all and no messages in syslog, messages or kern.log.

You think this might be an OS issue?

---

### Post by MooPi on 2009-12-29
Those temps are still on the very high side. Ideally you'd want something in the range of 50 degrees Celsius. 60=140 fahrenheit and 75=167. You may want to consider opening the side or increasing ventilation to your case. By comparison my quad core AMD runs about 42 Celsius under stress.

---

### Post by jmvbxx on 2009-12-29
The case is completely open.  I read in the intel manual that temps up to 75C can be considered normal for my configuration.

What obviously isn't normal is around 90C where I'm at with 9.10 64bit.

Any suggestions or should I install a 32bit instead?

---

