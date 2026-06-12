---
title: "Laptop hard drive occasionally grinds for several minutes after suspend/resume"
date: 2010-08-08
forum: Hardware
---

### Post by zak on 2010-08-08
Most of the time, when I suspend (not hibernate) my laptop, it resumes in about 10 seconds. About 1 in 5 times, the hard drive grinds for several minutes before the computer becomes usable again. Is there a known issue or workaround for this?

Hardware details:

Thinkpad W500, 4gb memory, FireGL v5700, Core2Duo T9600, 320gb conventional disk.

---

### Post by zak on 2010-08-21
After investigating with iotop, it appears that the problem is ubuntuone-syncd being a disk hog as soon as it has the ability to run after resume. This sometimes results in the computer being entirely unusable (i.e. the backlight doesn't turn on and/or the password prompt doesn't appear) for *minutes* after opening the lid or pressing the power button.

I'll research a bit more and report a bug.

---

