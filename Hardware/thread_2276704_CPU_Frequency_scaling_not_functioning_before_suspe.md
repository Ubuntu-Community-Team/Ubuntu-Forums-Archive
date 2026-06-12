---
title: "CPU Frequency scaling not functioning before suspend/resume"
date: 2015-05-04
forum: Hardware
---

### Post by olivier-the-olive on 2015-05-04
Greetings, I am experiencing a rather peculiar issue.

My CPU is an AMD fx-4350 (quad-core) and I have the clock speed set so the maximum is 4.2 GHz. I would like to be able to use cpu frequency scaling.

However, all the cores are at 4.2 GHz and the MATE indicator applet nor the _cpufreq-set_ command could change any of them, even though other options are provided, they don't take effect.

One day I noticed that 'suddenly' cpu frequency scaling was functioning on the last 3 cores (CPU1, CPU2 and CPU3).
I eventually tracked this down and discovered that this was because I had suspended and resumed. Indeed, I have confirmed that suspending and resuming 'resolves' the issue.

Though, I would like to be able to use cpu frequency scaling without first suspending and resuming -- as in, that is the issue I would like to solve by means of this forum thread.

Running the command _cpufreq-info_ (from cpufrequtils, I believe) **before** suspending/resuming outputs [http://paste.ubuntu.com/10984269/](http://paste.ubuntu.com/10984269/) .
Of particular interest (to me, maybe my interest is misguided):

  > current policy: frequency should be within 4.20 GHz and 4.20 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.

I should note that setting the governor to 'powersave' which should normally select the lowest frequency, gives similarly:

> current policy: frequency should be within 4.20 GHz and 4.20 GHz.
The governor "powersave" may decide which speed to use
within this range.

I would assume that there is a way to change the current policy to a different range, though I do not know if that is the case or if that is the correct route to follow.

I would be grateful with any solutions or guidance you could provide me with to attempt to resolve this issue. Thank you in advance.

---

### Post by olivier-the-olive on 2015-05-04
Well, I feel a bit stupid for not reading the man pages for cpufreq-set until now, but using these commands:
```
sudo cpufreq-set -c 0 -d 1.4GHz
sudo cpufreq-set -c 1 -d 1.4GHz
sudo cpufreq-set -c 2 -d 1.4GHz
sudo cpufreq-set -c 3 -d 1.4GHz
```

resolves the behaviour by changing the minimum allowed frequency.

---

