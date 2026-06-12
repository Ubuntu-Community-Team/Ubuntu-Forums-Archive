---
title: "Latitude 3150 random crashes"
date: 2016-06-20
forum: Hardware
---

### Post by j.backer on 2016-06-20
[HR][/HR]My laptop (Latitude 3150) is having issues. It's supported according to [here]("http://www.ubuntu.com/certification/hardware/201412-16319/") and it doesn't have the slow [resume]("http://www.ubuntu.com/certification/hardware/201412-16318/") issues either. I've tried multiple BIOS versions up to A04 I believe.

However, what it is doing with Ubuntu Gnome 14.04 and 16.04 installs (freshly updated, and for what it's worth, Fedora as well) is freezing up at completely random times. It seems to be regardless of the load it's having. I can't switch over to another console either, I have to forcefully shut it down and start it again. Doing some searching has some talks on disabling Bluetooth support but also recent kernels not having the issue anymore, which I believe I have.

(For what it's worth, Windows is running 100% stable, also under higher load situations, so likely I can rule out any heat issues).

Would anyone mind giving me a hand looking for clues? Normally I do know quite well where to start but I honestly don't have a clue on where to start this time :)

---

### Post by Freefalldart on 2016-10-31
Same problem here. Tested with Ubuntu 16.04.1 x64 an newest BIOS version (A06). This was not happening before with Ubuntu 14.04 x64 an Dell provided driver pack.

I couldn't see anything related on system logs.

---

### Post by eugenial on 2017-01-22
I created an account and I came here to confirm that the newer versions of Ubuntu (16.04 and 16.10 + updates) do NOT work properly with the DELL 3150. There are RANDOM crashes happening, as early as the kernel loads, but most often, the hang happens later on when xorg fails to load. A few times xorg manages to load, and then it crashes later (after it has completely loaded). It's really random where the bug will occur! My guess is that it's a kernel driver that causes the problem, since the old versions of Ubuntu worked kinda ok with this same laptop. There are no interesting logs about it to find out what's going on... For the record, I used BIOS A06. Windows on the same laptop works fine.

---

### Post by eugenial on 2017-01-23
An update: The bug is with the 4.8.x kernel. It is fixed on the 4.9.x kernel. I installed Fedora to test, and the default Fedora 25 also crashed the same way. But after I managed to install all its updates (which also updated the kernel to the latest version), the bug disappeared. So I'm guessing that the next version of Ubuntu should have this bug fixed too.

---

