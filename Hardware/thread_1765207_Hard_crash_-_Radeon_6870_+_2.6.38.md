---
title: "Hard crash - Radeon 6870 + 2.6.38"
date: 2011-05-22
forum: Hardware
---

### Post by teddyp on 2011-05-22
I've been searching all day and have found no answers to help me, so maybe someone else has encountered this issue. I was running mint 10 and waiting for xubuntu 11.04 to drop so I could actually use my 6870. I downloaded 11.04 today and I can't even boot into the live disk. It starts, I select to enter the live os, it shows the xubuntu logo, then the monitor turns off (it says "entering  sleep mode"). I have 2 monitors and the other says no signal. I downloaded 10.10. I can boot off the live disk without issue. I installed 10.10 and it ran fine. I upgraded all. I tried to boot off 2.6.38 and the same issue. I tried to boot off 2.6.35-5 and it crashes now too, but a bit differently. Cursor just blinks. I'm going to reinstall ubuntu 10 to get a working system first, but any ideas on fixing this? Running all 64bit OS's here.

Hardware:
Mobo: MSI 890FXA-GD70
CPU: Phenom II x6 1090T
RAM: G.SKILL Ripjaws F3-10666CL7D-8GBRH
GFX: XFX HD-687A-ZNBC Radeon HD 6870 BE
PSU: Corsair AX1200

---

### Post by teddyp on 2011-05-22
Just tried the alternate setup disk. Installation went fine, but same behavior. xubuntu logo shows, then both monitors shut off. I have to hard reset to get anything. going back to 10.10 now.

---

### Post by alex2399 on 2011-05-23
I had a similar problem and there is no solution with open source drivers. Only installing via the alternate installer, then going to recovery mode and installing the fglrx drivers after adding the x-swat ppa.

---

### Post by teddyp on 2011-05-23
Outstanding. I'll have to give that a shot then. I installed via the alt disk yesterday and still wasn't able to boot into 2.6.38, but I didnt try recovery mode. I installed 10.10, installed kernel 2.6.38 from the repos and tried to boot into that with no avail. Funny thing was that when I checked the kernel log, I see nothing out of the ordinary between 2.6.38 and 2.6.35, but 2.6.38 just will not boot. I'll give your solution a shot soon. I installed catalyst  11.5 in 10.10 and it seems to work fine.

---

