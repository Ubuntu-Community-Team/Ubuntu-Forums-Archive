---
title: "Dell Inspiron 1545 Overheating Issue"
date: 2011-04-24
forum: Hardware
---

### Post by Shinypaper on 2011-04-24
Hi all.

I've got a Dell Inspiron 1545 here with Ubuntu Desktop 10.10 64 bit installed.
Problem is the CPU is getting to insanely high temperatures before the fan finally kicks in.

Is there any way I can just set my fans to 100% constantly. I'm really not bothered about noise at all.

Thanks!

---

### Post by KegHead on 2011-04-24
Hi!

You could working in your bios.

Or update your kernel;

sudo apt-get update

sudo aptitude install linux-image -f

KegHead

---

### Post by Shinypaper on 2011-04-24
Ah, yeah, I've already tried that, and my bios is one of those rubbish Dell ones that only gives you the most basic options. I don't think Dell want us tweaking our systems =/

I've also tried with lm-sensors and pwmconfig to no avail :(

---

### Post by KegHead on 2011-04-24
Hmm,

Have you looked at:

cpufreqd type programs?

KegHead

---

### Post by Shinypaper on 2011-04-24
I'm trying that now - I'll have a play around with it and let you know how it goes, though I've never heard of this tool before, it looks like it's more for scaling the CPU frequency, can you control your CPU fan with it?

---

### Post by Shinypaper on 2011-04-25
sorry I didn't get back to you - got distracted and didn't realize how late it was. I tried cpufreqd btw and that was just to scale the CPU, it didn't have any kind of fan controls :(

---

### Post by KegHead on 2011-04-25
Hmm,

Have you overclocked?

Bios up to date?

The is some chatter about a bios upgrade for Dell.

KegHead

---

### Post by Shinypaper on 2011-04-25
Nah, haven't overclocked (this bios has all the advanced tweaking stuff removed) and the bios is current. All I really need is a way to maintain 100% fan speed constantly.

---

### Post by lifelike27 on 2011-04-25
I used to get this problem too, but then I realized I didn't activate my ATI driver. (Administrator > Additional Drivers)

I have a Dell Studio 1558.

---

### Post by Shinypaper on 2011-04-25
Ah, yeah I've got all the right drivers. Besides my problem's with my CPU fan, not video card :)

---

### Post by fyfe54 on 2011-08-24
I have same Insp 1545 and it was really hot.  Left leg was getting cooked.
Then I found this.
[http://ubuntuforums.org/showthread.php?t=1792877](http://ubuntuforums.org/showthread.php?t=1792877)

It did two things.  One, laptop running MUCH cooler.  Two, battery life now seems to be about 4 hours from fully charged.

---

