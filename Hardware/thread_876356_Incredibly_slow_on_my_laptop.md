---
title: "Incredibly slow on my laptop"
date: 2008-07-31
forum: Hardware
---

### Post by mcwattersm on 2008-07-31
Hey guys, yesterday I install Ububtu on my laptop with Wubi.

When I finished the install and rebooted it was incredibly slow. I was on pidgin the chat would freeze multipul times while I was trying to send a message. I tried reinstalling and no such luck. I have Ubuntu on my desktop PC. My desktops specs are Pentium 4, 2ghz processor, 512MB ram. Runs Ubuntu fine. My laptop specs are Pentium M, 1.73 ghz processor, 512MB ram. So I figured it would be a bit slower than my desktop but it is much much slower.

I am dual booting Windows Media Center and it runs very fast, fast than my desktop on Windows. So something doesn't seem right. I don't know what the problem, I hope you guys do because I can't stand being on Windows much longer.

---

### Post by finito on 2008-07-31
try running the laptop on AC power instead of Batteries.

---

### Post by mcwattersm on 2008-07-31
No such luck, thanks though.

---

### Post by trash on 2008-07-31
I'm running xubuntu on a pentium m 1.2ghz, very peppy here and i doubt gnome would make that much of a difference.
have you run 'top' or system monitor to see if anything is hogging resourses?

---

### Post by finito on 2008-07-31
Yes it seems to be the Pentium M Driver at fault.

Since the Pentium M works by only using as much speed as need to save battery 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/120759](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/120759)

---

### Post by trash on 2008-07-31
> **finito said:**
> Yes it seems to be the Pentium M Driver at fault.

Since the Pentium M works by only using as much speed as need to save battery 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/120759](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/120759)

how come i don't have any speed changes plugged or unplugged? or does that only kickin after some time on battery?

EDIT: just checked my bios and speedstep was already enabled:)

---

### Post by finito on 2008-08-01
trash I am confused do you face a similar problem?

I am not sure what 'peppy' means. I assumed 'well' or 'good'

> 
how come i don't have any speed changes plugged or unplugged? or does that only kickin after some time on battery?


it didnt make a difference for mcwattersm when he plugged it in to AC Power either.

---

### Post by trash on 2008-08-01
> **finito said:**
> trash I am confused do you face a similar problem?

I am not sure what 'peppy' means. I assumed 'well' or 'good'



it didnt make a difference for mcwattersm when he plugged it in to AC Power either.

no i don't have that problem, yes peppy is good:). After you posted i just wondered why i don't face the same problems since mine is a pentium m... I edited my post after i read the speedstep thing.

---

### Post by finito on 2008-08-01
o i c,

It could merely be chipset difference. I am making an assumption on the processor being at fault, cause I know that these processor at least the early ones had a similar problem with early XP and I don't rmeber if Windows made the fix or Intel but it was a driver issue.

---

