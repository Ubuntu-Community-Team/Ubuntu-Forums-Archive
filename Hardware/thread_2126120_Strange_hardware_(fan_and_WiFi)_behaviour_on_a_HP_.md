---
title: "Strange hardware (fan and WiFi) behaviour on a HP EliteBook 6930p"
date: 2013-03-16
forum: Hardware
---

### Post by Lammis on 2013-03-16
Hi,
I recently installed the 64-bit version of Ubuntu 12.10 on my laptop. After the installation my fan has a different sound and the laptop it gets very warm. Could this be caused by a driver issue or is it just bad luck to have a hardware issue at the same time?

Another strange behaviour is that my WiFi LED indicator keeps flashing. It is blue when WiFI is turned on and orange when off. Now it is flashing with irregular intervals. I have never seen this before. Otherwise my internet connection seems to work just fine.

---

### Post by Lammis on 2013-03-16
My network adapter is recogized and has the following information:

03:00.0 Network controller: Intel Corporation Ultimate N WiFi Link 5300
    Subsystem: Intel Corporation Device 1011
    Flags: bus master, fast devsel, latency 0, IRQ 49
    Memory at d8100000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

---

### Post by Lammis on 2013-04-04
I am now a convinced Ubuntu fan :)

Unfortunately, I still have problems with my hardware behaviour. There are a lot of things that make me think about how linux handle certain things. I don not know if this thread should be in this or in another software related section. But somehow I hope it reaches any of you cool hard-coding guys dealing with whatever is causing the symptoms:

1. Heat management
I have noticed that the fan is on all the time an at the same speed. Previously, when I used Windows 7, the fan turned off in periods and the fan was silent for a while. Now, when it is constantly on I get tired from working in the noise. Strangely enough my laptop also gets warmer than previously.

2. Sound management
I have an external loudspeaker that charge from the USB port. I have used it for two years. When using Win7 it was silent when there was no sound output. Now, using Ubuntu it has a silent but clearly audible screeching, almost like a telegraph mixed with white noise.

3. WiFi
As stated above I have a WiFi status LED right above my keyboard that is changing between blue and orange in an irregular pattern. Since my internet connection works just fine it is not the en of the world, but it is a bit annoying.

I hope this is useful information for anyone dealing with development of this free-of-charge and still a competent alternative to Windows OS. Please feel free to contact me if you need additional information on the above.

---

### Post by Xububntu on 2013-06-10
I seem to have the same issue on my HP envy Beats edition, core i5, with switchable graphics card(ATI radeon HD5650). 
1. can hear the fan noise consistently.
2. the wifi light consistently keeps flickering.

I have 12.04LTS installed, dual boot with Win 7
any help is appreciated.

---

### Post by Xububntu on 2013-06-30
Hey Guys n Gals,

Any pointers on this issue, would really want to use LTS more often, but the fan noise and constant flickering of the wifi button does not encourage me. keep rebooting to back to windows... Any help is appreciated.

Regards...

---

### Post by Kevin S on 2013-07-01
Hi, this link may help with the continuous fan noise: [http://www.linlap.com/hp_elitebook_6930p](http://www.linlap.com/hp_elitebook_6930p)  (May be a BIOS setting.)  I recommend that you get the program Psensor from the software center; it will track whatever temp sensors it can find in your system, so you can tell if you have a heat problem.

---

### Post by Lammis on 2013-07-07
Hi Kevin S, thanks for the tip to use Psensor. I just installed it and it found 7 sensors. 
Unfortunately I am still without a solution for the fan problem after looking at all the sites recommended above.

---

### Post by Lammis on 2013-10-25
I now have Ubuntu 13.10 and the wifi LED does not flash any more.
Also I am now used to the constant noise from the fan. Hence, there is no need for having this thread open.

---

