---
title: "CPU Frequency Scaling -- worked in dapper, not in hardy"
date: 2008-06-19
forum: Hardware
---

### Post by randysparks on 2008-06-19
I'm trying to get manual control over CPU throttling on an AMD Athlon64 2.4GHz chip.

It worked fine under Dapper once I'd run sudo dpkg-reconfigure gnome-applets and enabled sudo access.

Now with hardy it just won't work. I've tried installing cpufreqd, but no dice, so I switched back to powernow. 

I've tried entering noapic in my kernel line. No good. 

What am I missing?

---

### Post by stchman on 2008-06-19
> **randysparks said:**
> I'm trying to get manual control over CPU throttling on an AMD Athlon64 2.4GHz chip.

It worked fine under Dapper once I'd run sudo dpkg-reconfigure gnome-applets and enabled sudo access.

Now with hardy it just won't work. I've tried installing cpufreqd, but no dice, so I switched back to powernow. 

I've tried entering noapic in my kernel line. No good. 

What am I missing?

You need to have the frequency scaling called powernow enabled in the BIOS.  Once you do that Ubuntu will be able to scale the frequency according to load.\

I have an Atlong 64 3500+ (2.2GHz) and it scales well using Hardy 64.

---

### Post by randysparks on 2008-06-20
> **stchman said:**
> You need to have the frequency scaling called powernow enabled in the BIOS.  Once you do that Ubuntu will be able to scale the frequency according to load.\

I have an Atlong 64 3500+ (2.2GHz) and it scales well using Hardy 64.

Well, I couldn't find anyting in the BIOS along those lines. All I saw was "Cool and Quiet", which is disabled, as I believe it has to be for this to work. 

Besides which, it worked fine on Dapper and I haven't tweaked the BIOS since then. 

Oh well.

---

### Post by ukripper on 2008-06-20
can you post output of the following:
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
```

---

