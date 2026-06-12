---
title: "Ubuntu 9.04 not booting"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by aslamsha on 2009-05-09
Hi all,
I use a Lenovo laptop. I upgraded from Ubuntu 8.10 to 9.04 recently and it was working fine. Only that some graphics were not supported. I installed some new graphics driver which I guess was the wrong move. I am getting the boot screen but after that my monitor blinks a couple of times and goes blank. I am unable to understand what has gone wrong here. Please help. I data is important, it is my production machine.

---

### Post by cariboo on 2009-05-09
Start in recovery mode and at the prompt choose drop to root prompt. At the prompt type:

```
cp /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf
```

You will be asked to confirm overwriting the existing xorg.conf, just say yes, then type exit to resume on to your desktop.

---

### Post by grashdur on 2009-05-09
I had a very similar problem after doing a fresh install of JJ on my Gateway (desktop) computer. After installing the recommended monitor driver, I rebooted again and again into a blank screen. I tried the command you suggested, but got an error message in response, saying there's no such file.

But then I looked back at the recovery-mode menu and discovered that I can scroll down to an option called something like "repair graphics." I tried that, and now it works again. Now I'll try one of the other two drivers and see whether one of them works.

I'm so glad I tried that, as I was just about to try reinstalling again! (As I thought it was that old busybox initramfs problem again preventing me from booting up.)

---

### Post by grashdur on 2009-05-09
Details: That recovery mode option was "Try to repair graphic problems"; after running that, you can just select "Resume normal boot."

Results: For me, versions 180 and 173 of the Nvidia screen drivers gave me a blank screen at login. But version 96 seems to be working just fine.

---

