---
title: "Lubuntu 16.04 64 bit: pulseaudio problem"
date: 2018-01-08
forum: Hardware
---

### Post by erotavlas on 2018-01-08
Hi,
I'm trying to repair an old PC about 10 years old. I do not know if it worked properly before. I installed lubuntu 16.04 64 bit, but I have a problem with audio output. I tried to follow all the steps described [here]("https://askubuntu.com/questions/774458/installed-lubuntu-16-04-version-no-audio-now") without success.
I also setup into BIOS enable for integrated audio card. If I open pavucontrol I can see the various applications (vlc, firefox, etc.) that are reproducing audio.
This is my lspci:
```

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 **Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)**
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:05.0 FireWire (IEEE 1394): LSI Corporation FW322/323 [TrueFire] 1394a Controller (rev 70)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 02)

```
Do you have any suggestion?
Thank you

P.S.
I noticed that also ethernet card does not work and so it could be a generalized problem.

---

### Post by Yellow Pasque on 2018-01-08
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by erotavlas on 2018-01-08
> **Temüjin said:**
> [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

Hi,
thank you for your fast reply. This is the link [http://www.alsa-project.org/db/?f=876c304f6b37c2b0b410eab585f5691899844504](http://www.alsa-project.org/db/?f=876c304f6b37c2b0b410eab585f5691899844504)
I found an old PCI audio card with hsp56 cmi8738 chip. Could it work?

---

### Post by Yellow Pasque on 2018-01-09
The alsa information looks okay.

> I found an old PCI audio card with hsp56 cmi8738 chip. Could it work?
cmi8738 is supported (snd-cmipci), but there are no guarantees a particular card works.

Before spending money, I would try a LiveUSB of Xubuntu 17.10 to see if audio works there.

---

### Post by erotavlas on 2018-01-10
> **Temüjin said:**
> The alsa information looks okay.


cmi8738 is supported (snd-cmipci), but there are no guarantees a particular card works.

Before spending money, I would try a LiveUSB of Xubuntu 17.10 to see if audio works there.

I tried with lubuntu 17.10, but the audio does not work. I have an cmi8738, should the kernel automatically recognized it?
What have I to do in order to use it?

---

### Post by Yellow Pasque on 2018-01-10
>  I have an cmi8738, should the kernel automatically recognized it?

Yes.

---

### Post by erotavlas on 2018-01-11
> **Temüjin said:**
> Yes.

Hi,
I solved by using a different audio card.
Best Regards.

---

