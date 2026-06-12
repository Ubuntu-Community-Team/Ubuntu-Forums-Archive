---
title: "Fan never turns off! (power managment)"
date: 2009-11-14
forum: Hardware
---

### Post by moh980 on 2009-11-14
OK so i just bought a new Toshiba laptop (L510) and i thought i should give visat a try (my first time trying) but i couldn't stand more than a week (i had to wait for the new release of Ubuntu 9.10)...so i did a clean install and as it was expected everything worked like charm out of the box

and now i start noticing a strange problem i never had before with older versions of Ubuntu on my old Toshiba
the problem is:
i when i start the computer the CPU Temp. around 33C and after using the computer for a while it start getting hotter and the fan will start at full speed around 80C and the temp will drop and keep droping till it fix at 31~33C but the fan never turns off or switch to a lower speed ( on vista all worked fine)

now my question is: is it configuration/ubuntu bug? or a hardware failure (i still have warranty)?

your help will be highly appreciated

Cheers!
Moh 

P.S: H/W
# Intel Core 2 Duo P7350(2.0GHz)
# ATI Mobility Radeon HD4570 (256MB)
# 2GB DDRII 800MHz
# 320G (5400rpm) SATA
# 14&#21515; HD(1366x768) CSV
# 8x DVD SuperMulti(+/-R DL)
# 802.11agn&#12289;V2.1+EDR
# eSATA, HDMI

---

### Post by nixscripter on 2009-11-18
You might need to set up your CPU frequency with dynamic scaling. See if this makes your computer not build heat so fast.

Open a Terminal right after you log in, and type:

```
sudo cpufreq-set -g powersave
```

That will make it use the minimum CPU speed supported by the hardware all the time. It should cool it down a bit.

If that works, then you can try a different governor (-g) such as "ondemand" or "conservative".

Hope this helps.

---

### Post by moh980 on 2009-11-18
Thank you for your help! i already solved the problem, which was fairly easy 
[http://ubuntuforums.org/showthread.php?t=1297008&page=5](http://ubuntuforums.org/showthread.php?t=1297008&page=5)


Cheers!
Moh

---

### Post by astamaja on 2009-11-20
I have had a similar problem, the fan is almost constantly on. The cpu-temperature starts at about 55°C and works it way quickly up to 72-79°C. If I watch computer streaming episodes online or something it get even higher (80-90°), and sometimes the computer shuts itself off (a safety mechanism, to avoid overheating Iwould guess?).

I tried this command, but all I get is a error message:

sudo cpufreq-set -g powersave

sudo: cpufreq-set: command not found

Any ideas why?

ps. I have Ubuntu 9.04, if it makes a difference.

---

### Post by moh980 on 2009-11-20
> **astamaja said:**
> I have had a similar problem, the fan is almost constantly on. The cpu-temperature starts at about 55°C and works it way quickly up to 72-79°C. If I watch computer streaming episodes online or something it get even higher (80-90°), and sometimes the computer shuts itself off (a safety mechanism, to avoid overheating Iwould guess?).

I tried this command, but all I get is a error message:

sudo cpufreq-set -g powersave

sudo: cpufreq-set: command not found

Any ideas why?

ps. I have Ubuntu 9.04, if it makes a difference.

try to check your graphic driver, and also refer to this thread (how i solved my problem) [http://ubuntuforums.org/showthread.php?t=1297008&page=5](http://ubuntuforums.org/showthread.php?t=1297008&page=5)

---

