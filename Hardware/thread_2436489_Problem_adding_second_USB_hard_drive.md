---
title: "Problem adding second USB hard drive"
date: 2020-02-07
forum: Hardware
---

### Post by jds102 on 2020-02-07
I have a Dell laptop with two USB 3.0 sockets, running an up-to-date Ubuntu 19.10. One socket is permanently occupied by an external hard drive used for automatic backups and storage of odds and ends. When I plug a second hard drive into the other socket, the first is briefly disconnected --- disastrous if it is in the middle of a backup. I say "briefly", but often after unmounting and removing the second HD I find that the first is still unmounted, and has to be physically unplugged and replugged-in for the system to "see" it again. This has been the case for months if not years, so it is not a new bug -- I've just got tired of living with it.

---

### Post by guiverc on 2020-02-07
Are the external drives powered? or using the laptop power? (via USB cable).

I wonder if your PSU (laptop power supply unit) is struggling to provide enough power (amperage/amps) for the USB ports, and thus plugging in the second HDD/ssd causes power to drop,  the other drive electronics momentarily fail due to insufficient power & thus disconnect (ie. power unit is no longer providing the power needed briefly). 

If drives are externally powered (have their own power supplies) this idea is most probably wrong, but if the drives get their power from the laptop; this is not a Ubuntu function, but your PSU is getting old & no longer supplies the required power (and it'll get worse, though decline can be slow or fast; if you use external-powered drives the issue will likely disappear). 

My 2c/thought.

---

### Post by jds102 on 2020-02-07
> **guiverc said:**
> Are the external drives powered? or using the laptop power? (via USB cable).

I wonder if your PSU (laptop power supply unit) is struggling to provide enough power (amperage/amps) for the USB ports, and thus plugging in the second HDD/ssd causes power to drop,  the other drive electronics momentarily fail due to insufficient power & thus disconnect (ie. power unit is no longer providing the power needed briefly). 

If drives are externally powered (have their own power supplies) this idea is most probably wrong, but if the drives get their power from the laptop; this is not a Ubuntu function, but your PSU is getting old & no longer supplies the required power (and it'll get worse, though decline can be slow or fast; if you use external-powered drives the issue will likely disappear). 

My 2c/thought.


It's a good thought -- both drives are indeed powered from the computer. I'll mark this solved, buy myself an externally powered drive, and come back here if the problem persists. Thanks for the reply!

---

### Post by him610 on 2020-02-07
You might also consider a relatively inexpensive powered USB hub.

---

