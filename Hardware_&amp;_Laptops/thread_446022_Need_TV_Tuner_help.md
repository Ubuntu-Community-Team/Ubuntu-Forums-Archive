---
title: "Need TV Tuner help"
date: 2007-05-16
forum: Hardware &amp; Laptops
---

### Post by theaceoffire on 2007-05-16
As far as I can tell, I have the AVerMedia M150-D tv tuner...

(Found this link here: [http://mythtv.org/wiki/index.php/AVerMedia_M150-D](http://mythtv.org/wiki/index.php/AVerMedia_M150-D) )

And when I do "sudo lspci -v", I get the following:

> 
02:05.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
        Subsystem: Avermedia Technologies Inc Unknown device c111
        Flags: bus master, medium devsel, latency 64, IRQ 22
        Memory at bc000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: [44] Vital Product Data
        Capabilities: [4c] Power Management version 2

02:05.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
        Subsystem: Avermedia Technologies Inc Unknown device c111
        Flags: bus master, medium devsel, latency 64, IRQ 22
        Memory at bd000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: [4c] Power Management version 2

02:05.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
        Subsystem: Avermedia Technologies Inc Unknown device c111
        Flags: bus master, medium devsel, latency 64, IRQ 22
        Memory at be000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: [4c] Power Management version 2


I have been trying to search for help, but its been a little tough on me...

How do I install the "cx88 and cx88-blackbird kernel modules", and verify that they are being used?

Any Ideas Welcome...

{I am running with 1.5 GB of ram, Pentium 4 3.06 GHz processor, ATI Radeon 9250 Video card. Currently dual booting with XP and Ubuntu 7.04, I have beryl working using the 'radeon' driver instead of fglrx, and so forth... if you need to know more info, just ask.}

---

### Post by newlinux on 2007-05-16
I believe the two modules you want to load are cx88-dvb and cx88-blackbird. You use the modprobe command.

```
sudo modprobe cx88-dvb
sudo modprobe cx88-blackbird
```

Then type:

```
dmesg

```
to see what happened (if it helps to recognize your card).


to have these modules loaded on boot put cx88-dvb and cx88-blackbird in your /etc/modules file.

---

### Post by theaceoffire on 2007-05-16
Thank you for your quick response: Linux assistance has always been half the reason I wanted to leave Windows.

For anyone else interested, my card was also known as ASUS PVR-416 (better google results I think), 
This link almost fixed my issue as well, so in case someone needs em:
[http://www.linuxquestions.org/questions/showthread.php?t=344884](http://www.linuxquestions.org/questions/showthread.php?t=344884)
How to set it up for myth tv: [http://mythtv.org/wiki/index.php/AVerMedia_M150-D](http://mythtv.org/wiki/index.php/AVerMedia_M150-D)

^_^ Hope it helps someone else.

---

### Post by elias85 on 2007-09-02
[SIZE="4"]my tv card is V-STREAM (with lspci i get 02:07.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05) how can i watch tv on my pc? pls help![/SIZE]

---

