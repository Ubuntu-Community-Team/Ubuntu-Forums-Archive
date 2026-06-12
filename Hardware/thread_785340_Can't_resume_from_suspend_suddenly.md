---
title: "Can't resume from suspend suddenly"
date: 2008-05-07
forum: Hardware
---

### Post by fird on 2008-05-07
My laptop is using an ATI x1300 video card. Since I updated my Ubuntu 7.10 to 8.04, I was glad to see that suspending worked well with the new fglix driver.

Unfortunately, from yesterday, I found my laptop can't resume from suspend suddenly. When I woke up my laptop, my screen backlight turned on and the mouse cursor appeared on screen. But besides the cursor, the screen was all black. And the computer never responded my input (both mouse and keyboard) any more. I had nothing to do but turn off my computer by force. 

Since the last successful resuming from suspend, I think the following changes to my system maybe affects:
1.Updated automatically from the main server (I noticed that "hal" was updated).
2.installed "ATI Catalyst Control Center" from the "Add/Remove programs" and changed some sets.
3.modified xorg.conf to enable "DPMS" of the monitor

I have tried to turned all sets to default in the ATI control center and disable DPMS again. All these didn't work.

here is my pm-suspend.log about resume
```
Wed May  7 19:36:20 CST 2008: running resume hooks.
===== Wed May  7 19:36:20 CST 2008: running hook: /usr/lib/pm-utils/sleep.d/99video =====
===== Wed May  7 19:36:20 CST 2008: running hook: /usr/lib/pm-utils/sleep.d/95led =====
===== Wed May  7 19:36:20 CST 2008: running hook: /usr/lib/pm-utils/sleep.d/94cpufreq =====
===== Wed May  7 19:36:20 CST 2008: running hook: /usr/lib/pm-utils/sleep.d/90clock =====
===== Wed May  7 19:36:20 CST 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
```

Can anyone give me some suggestions? Thank you!

---

### Post by fird on 2008-05-08
> **fird said:**
> My laptop is using an ATI x1300 video card. Since I updated my Ubuntu 7.10 to 8.04, I was glad to see that suspending worked well with the new fglix driver.

Unfortunately, from yesterday, I found my laptop can't resume from suspend suddenly. When I woke up my laptop, my screen backlight turned on and the mouse cursor appeared on screen. But besides the cursor, the screen was all black. And the computer never responded my input (both mouse and keyboard) any more. I had nothing to do but turn off my computer by force. 

Since the last successful resuming from suspend, I think the following changes to my system maybe affects:
1.Updated automatically from the main server (I noticed that "hal" was updated).
2.installed "ATI Catalyst Control Center" from the "Add/Remove programs" and changed some sets.
3.modified xorg.conf to enable "DPMS" of the monitor

I have tried to turned all sets to default in the ATI control center and disable DPMS again. All these didn't work.

here is my pm-suspend.log about resume
```
Wed May  7 19:36:20 CST 2008: running resume hooks.
===== Wed May  7 19:36:20 CST 2008: running hook: /usr/lib/pm-utils/sleep.d/99video =====
===== Wed May  7 19:36:20 CST 2008: running hook: /usr/lib/pm-utils/sleep.d/95led =====
===== Wed May  7 19:36:20 CST 2008: running hook: /usr/lib/pm-utils/sleep.d/94cpufreq =====
===== Wed May  7 19:36:20 CST 2008: running hook: /usr/lib/pm-utils/sleep.d/90clock =====
===== Wed May  7 19:36:20 CST 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
```

Can anyone give me some suggestions? Thank you!
I finally solved the problem myself.

It was the "ATI Catalyst Control Center" who caused all the problem. After restored "/etc/ati/amdpcsdb" from "/etc/ati/amdpcsdb.default", I can successfully resume from suspend now!

It's unlucky to have an ATI video card in a linux machine...

---

### Post by latev on 2008-10-30
Would you please provide some support on exactly how you managed to get the suspend to ram work on your Linux box.
I use the latest proprietary fglrx precompiled ati driver from the Ubuntu repositories and I'm starting to loose hope that things can get working.
I'm also using the x64 edition of 8.04 Ubuntu

By restoring "/etc/ati/amdpcsdb" from "/etc/ati/amdpcsdb.default do you mean overwriting the first file with the content of the second? In my case that's what I'm doing, however it doesn't seem to make any difference and on top of that - the file somehow restores to it's previous state after I do the cold reboot /which is inevitable after each suspend attempt/

The /etc/ati/amdpcsdb.default file is significantly smaller than etc/ati/amdpcsdb

I'm pretty sure it's a driver issue, most probably the ati driver, since WinXP 32 resumes nicely from S3 suspend mode.

I too have an X1300 ati card, AMD Athlon 3500+ x64 CPU - desktop
What versions of the driver are you using? Do you use compiz?

---

