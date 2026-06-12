---
title: "Question about laptop battery charge data"
date: 2021-01-21
forum: Hardware
---

### Post by operius on 2021-01-21
Hi all, I have a 3 or 4 years old hp-pavilion laptop and I'm having troubles with the battery.
When the battery level gets below +/- 45% the charge drops very fast until the laptop shuts down.
After this the battery will not charge to 100% anymore, but to about 80%.

Now I know how to 'recalibrate' the battery.
I boot into the bios screen and let it drain the battery, and after the battery is fully unloaded I charge it again without using the laptop until the indicator indicates that it is fully charged again.
After this I can use my laptop normally as before, until the battery gets below 45% again.

So maybe this battery is bad, I don't know.
What confuses me is that when the battery will not charge beyond 80% power statistics show that the battery has a energy level of 23,4 watt, which is the maximum, but battery percentage shows 80%.
The indicator on the laptop is orange indicating that the battery is not fully charged.

So where is this contradicting information coming from?
Does the battery itself give information about it's energy level directly to the OS (ubuntu 20.04), or does the OS get the information from something on the motherboard.
And how can the information on the OS contradict is self?
Saying the energy-level is at a maximum of 23,4 watt and also saying the battery is charged 80%.

Is this a hardware or a software problem?

---

### Post by CatKiller on 2021-01-21
> **operius said:**
> So maybe this battery is bad, I don't know. 

It is. Batteries have a finite lifetime. Things like letting them get hot, keeping them fully charged for extended periods, or discharging them quickly reduce the lifetime further. 

> Does the battery itself give information about it's energy level directly to the OS (ubuntu 20.04), or does the OS get the information from something on the motherboard.

The battery provides the information. The OS reads that information through a motherboard interface. Some of the information is precise, like the current discharge rate, and the rest is estimated based on past usage.

---

### Post by operius on 2021-01-21
Thank you for your reply.
So I will get a new battery.
But I'm still confused about what the OS is telling me.
From what I understand from you is that the energy level is the most accurate information since it comes directly (almost) from the battery itself, and the percentage is a 'guess' based on usage history.
But what is making that guess?
I suppose it is something on the motherboard since the hardware itself also indicates that the battery is not fully charged via an orange light at the side of the laptop.
So, am I correct in saying that all battery information I see in ubuntu is coming in one way or another from the motherboard and nothing is being guessed/calculated by ubuntu itself?

---

### Post by CatKiller on 2021-01-21
> **operius said:**
> So, am I correct in saying that all battery information I see in ubuntu is coming in one way or another from the motherboard and nothing is being guessed/calculated by ubuntu itself?
I don't know for sure, but my intuition from poking around with my battery previously is that the current is read by the battery, the remaining charge is estimated by the battery, and the remaining time until charged/discharged is estimated by the OS. The maximum charge that a battery can hold changes over time, and is also estimated by the battery.

---

### Post by CelticWarrior on 2021-01-21
> **CatKiller said:**
> I don't know for sure, but my intuition from poking around with my battery previously is that the current is read by the battery, the remaining charge is estimated by the battery, and the remaining time until charged/discharged is estimated by the OS. The maximum charge that a battery can hold changes over time, and is also estimated by the battery.

This ^^^ exactly.
In a nutshell, everything except time to fully charge/discharge is info given by the hardware. In my experience, most modern Linux distro guesstimate more accurately then Windows but they're far from perfect.

---

### Post by operius on 2021-01-21
Thank you and Catkiller for your reply's.
For a while I thought I had to 'teach' the OS about the battery by letting it discharge almost fully and then charge it again to 100% so the OS could would get a scale of some sort.

Thanks to you both it is more clear to me now how this works.
But it remains strange that mobile phones never seem to have issues like I had with my laptop.
My phone is almost 5 years old and still works like new.

---

### Post by Autodave on 2021-01-21
I have had laptop batteries in excess of 10 years old that still worked great.  And, I have had ones not make it to their first birthday.  Also, if you buy a battery, be vary wary of off name units: some aren't worth a dime.

---

