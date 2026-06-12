---
title: "Unknown Hardware"
date: 2017-06-25
forum: Hardware
---

### Post by bks on 2017-06-25
I am running Ubuntu 17.04 on a Lenovo Yoga 3 11 (80J8), Intel® Core™ M-5Y71 CPU @ 1.20GHz × 4, Intel® HD Graphics 5300 (Broadwell GT2). I have been having a lot of instability issues that seem to get worse the longer the system is on. The issues include simple things like general system lag, to system updates not able to install, to apt-get being locked for no apparent reason, to complete and total freeze. Sometimes the screen won't even turn back on if I leave it for a few minutes. I did change the settings so that the screen turns off, but the system doesn't suspend. I did that because the computer was unusable IF it came back from suspension. This seems like a hardware driver or compatibility issue (chipset maybe?), but I don't know how to figure it out. 

I took a screenshot of the additional drivers window because I wonder if anyone has seen this before and may have some insight as to how to figure out what is not being recognized. Maybe this has something to do with my system being unstable. 

[ATTACH=CONFIG]275770[/ATTACH]

Thanks in advance for your help!

---

### Post by howefield on 2017-06-25
The description for the intel-microcode package which is what you see in your screen shot is as follows...

```
Description-en_GB: Processor microcode firmware for Intel CPUs
 This package contains updated system processor microcode for Intel i686
 and Intel X86-64 processors.  Intel releases microcode updates to correct
 processor behavior as documented in the respective processor specification
 updates.
 .
 For AMD processors, please refer to the amd64-microcode package.
```

I always install it but as to whether or not it provides any tangible benefit.. <shrug>

There is no reason for you not to try installing it unless you are completely against using proprietary code on your machine.

---

### Post by bks on 2017-06-25
I am not opposed to proprietary code, and I have had it install before, but the system was still unstable.

---

### Post by howefield on 2017-06-25
The brief hardware specifications you posted aren't particularly strong, at least for running the Unity desktop environment, perhaps trying a lighter version of Ubuntu would work better ?

---

### Post by bks on 2017-06-25
Any recommendations? Is Cinnamon Mint any lighter? Or can I change desktop environments/window managers?

---

### Post by CatKiller on 2017-06-25
Just a quick thought: have you checked your temperatures? Increasing instability the longer the computer is on is exactly the kind of thing you'd expect to see with overheating.

---

### Post by howefield on 2017-06-26
> **bks said:**
> Any recommendations? Is Cinnamon Mint any lighter? Or can I change desktop environments/window managers?

The lighter flavours are generally Lubuntu and Xubuntu, I'd give them a go with a Live media for an hour or two.

---

