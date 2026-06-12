---
title: "Overheating &amp; Excessive Cpu Use"
date: 2010-07-21
forum: Hardware
---

### Post by daz1uk on 2010-07-21
Hi,

I have seen a few posts around regarding similar issues as mine but nothing to resolve it. 

Generally my Core2Duo sits at 1Ghz per core whilst running Ubuntu 10.04 and nothing else, this seems a little high to me, but anyway.

Occasionally for no apparent reason the cpu's will start alternating full load, this is still with just the os running, running my cpu temps up to 70degrees, ouch! If this carries on it is going to destroy my laptop.

I have already started getting screen flicker at times which is caused by the graphics chip overheating, I know this because I have already lost one laptop to similar issues a couple of years ago.

I have tried installing ACPI to fix this to no avail (Thought it was strange that ACPI wasn't installed as default?).

Please help.

---

### Post by cliffdodger on 2010-07-21
Have you run top to see what's taking up all the cpu juice? Not to jump to conclusions but the first thing I would check is to see if you've been hacked or someone dropped a rootkit on your system. Rootkit or not - if you're hacked at all someone could be doing things behind your back on your machine.

That would be my first guess. If not let us know. (try searching for "root kit hunter" in google if you don't have it installed already - not sure if it's available via the ubuntu package manager but check there too)

---

### Post by TBABill on 2010-07-21
A few items to try: 1) install proprietary driver 2) install Sun Java instead of open source java and 3) make sure your CPU scaling is actually jumping properly (using "ondemand" with CPUFREQ is probably best).

---

### Post by daz1uk on 2010-07-21
> **TBABill said:**
> A few items to try: 1) install proprietary driver 2) install Sun Java instead of open source java and 3) make sure your CPU scaling is actually jumping properly (using "ondemand" with CPUFREQ is probably best).

Hi,

Thanks for your response, could you please explain how to check the frequency scaling with "ondemand"?

---

### Post by TBABill on 2010-07-22
You will need to install CPUFREQ from the repository (Synaptic). I can't recall if that is the exact name, or if it may be CPUFREQUTILS or something similar. Search CPUFREQ and you should find it. 
 
Once installed you will need to go to a terminal and type > cpufreq-info The result will be almost a full screen but somewhere there will be your setting in quotes. Most likely it will be either ondemand or performance. If it says ondemand you are already operating in that mode, which scales you down to the lowest CPU speed and immediately scales back up when system demand requires it. It will do so incrementally, for example 800MHz at slowest, 1.1GHz, possibly another speed higher and then your max CPU speed. Sometimes you will see a jump from lowest to highest immediately. There is a Gnome applet to monitor CPU speed on a panel. Your numbers (speeds) will vary based on your processor.
 
If the setting is currently at performance, use the following to set it to ondemand > cpufreq-set --governor ondemand
 
You may need to logout and back in to see the change....can't recall. Good luck!

---

### Post by daz1uk on 2010-07-22
Hi

So far so good, but have you got any idea why my cpu's would be set to run at a minimum of 1000hz, seems odd to me, how about you?

"current policy: frequency should be within 1000 MHz and 1.83 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range."

---

### Post by TBABill on 2010-07-25
I think that's predetermined within the CPU by what it is capable of. It's not a Linux thing, but rather Linux using what the CPU is designed to be able to do.

---

