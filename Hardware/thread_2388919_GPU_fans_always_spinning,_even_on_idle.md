---
title: "GPU fans always spinning, even on idle"
date: 2018-04-09
forum: Hardware
---

### Post by seeyouza on 2018-04-09
Hi

Minor problem, but it is an annoyance.

I have a Zotac GeForce GTX 1080 Ti AMP Extreme Core Edition. Running Ubuntu 16.04 with kernel 4.8.17.

I have the latest Nvidia proprietary drivers installed. (390.48)

This GPU has passive cooling support, such that when it is idle, the fans will stop entirely. This happens without issue in Windows 10. However in Ubuntu, the fans will always spin. If I check Nvidia X Server Settings, it reports 0% GPU usage, is in Adaptive mode, but the fans will run at a minimum of 30% speed, never lower, and never switching off entirely.

Is there a way to enable this feature in Ubuntu?

Thanks in advance

---

### Post by Yellow Pasque on 2018-04-09
First off, kernel 4.8 is no longer supported. Why are you still running it?

Second, maybe try coolbits. I'm not sure if it works on newer cards like yours:
[http://www.upubuntu.com/2015/05/how-to-controladjust-gpu-fan-speed-for.html](http://www.upubuntu.com/2015/05/how-to-controladjust-gpu-fan-speed-for.html)

---

### Post by seeyouza on 2018-04-09
Thanks - I've updated to 4.15, as the Nvidia drivers wouldn't install at all with 4.16. Same issue though.

I don't really want to manually control the fan speed - merely interested to why the Linux Nvidia drivers don't function the same way as the Windows drivers when it comes down to shutting the fans down when the card is idleing.

---

### Post by Yellow Pasque on 2018-04-09
> I don't really want to manually control the fan speed - merely interested to why the Linux Nvidia drivers don't function the same way as the Windows drivers when it comes down to shutting the fans down when the card is idleing. 

It's a closed source driver. Ask Nvidia. FWIW, no problems here on an Asus Strix GTX 950. Fan stays off at idle.

---

