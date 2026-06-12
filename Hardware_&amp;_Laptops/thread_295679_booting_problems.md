---
title: "booting problems"
date: 2006-11-08
forum: Hardware &amp; Laptops
---

### Post by howlingmadhowie on 2006-11-08
hi everybody :)

just thought i'd say, i installed ubuntu eft on an intel centrino duo with ipw3945 wlan card and radeon X1400 mobility graphic card and the whole thing has some problems booting. sometimes it works, sometimes it doesn't. is this likely to be a hardware problem? or have i just got too much beta-software on it (beryl, ipw and graphic card drivers...).

if someone has a similar constellation (it's a toshiba satellite M100-152), i'd love to hear from them :)

howie

---

### Post by pitkali on 2006-11-08
> **howlingmadhowie said:**
> hi everybody :)

just thought i'd say, i installed ubuntu eft on an intel centrino duo with ipw3945 wlan card and radeon X1400 mobility graphic card and the whole thing has some problems booting. sometimes it works, sometimes it doesn't. is this likely to be a hardware problem? or have i just got too much beta-software on it (beryl, ipw and graphic card drivers...).

if someone has a similar constellation (it's a toshiba satellite M100-152), i'd love to hear from them :)

howie

I have centrino duo, ipw3945 wlan and X1300 and no problems with booting. What exactly are the symptoms you observe?

---

### Post by howlingmadhowie on 2006-11-10
thanks for your reply :)

well, booting works, mostly. sometimes it just hangs at a seemingly random place. i've managed to convince myself, that switching on the wlan-card helps here, but i've only booted the thing about 20 times, so any assumption of causality here is to be taken with a pinch of salt. 

once it's booted, as said, it's rock stable (beryl sometimes goes wrong with the result that i have to hard-reboot, but i attribute that to the beta-nature of beryl and the closed-source drivers from ati).

i'll start keeping a journal of when it doesn't boot so i can report :)

howie

---

### Post by pitkali on 2006-11-11
> **howlingmadhowie said:**
>  sometimes it just hangs at a seemingly random place. 
The boot hangs? Or is it only the progress bar - because it happened to me a few times - the progress bar stops at certain moment and then it just sits there. Yet still HDD LED is active and after some time gdm shows up.

Regards,

---

### Post by antraxx on 2006-11-11
> **howlingmadhowie said:**
> hi everybody :)

just thought i'd say, i installed ubuntu eft on an intel centrino duo with ipw3945 wlan card and radeon X1400 mobility graphic card and the whole thing has some problems booting. sometimes it works, sometimes it doesn't. is this likely to be a hardware problem? or have i just got too much beta-software on it (beryl, ipw and graphic card drivers...).

if someone has a similar constellation (it's a toshiba satellite M100-152), i'd love to hear from them :)

howie


I have exactly the same problem on my Thinkpad R60 /cetrino duo,ipw3945 radeo n X1400/. Booting sometimes hang on. Has someone any ideas?

---

### Post by howlingmadhowie on 2006-11-13
it certainly hangs. i switch off quiet and splash when booting nowadays :)

update:
i sometimes get huge amounts of segmentation faults during booting as well. haven't got a clue what's going on.

---

### Post by sauerlanddon on 2006-12-02
Hi,
i have the same problem. While booting Ubuntu 6.10 my notebook suddenly hangs. I noticed that this problem only occurs, if my WLAN is disabled (3945ABG). If I enable WLAN there are no problems.

I have a IBM Z61m Notebook.

---

### Post by pitkali on 2006-12-02
Yes, that is a well known problem. My girlfriend has the same issue on her R60. Now there's no doubt why it is called 'kill switch' ;)

---

### Post by trondvh on 2006-12-03
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/63418](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/63418)

---

