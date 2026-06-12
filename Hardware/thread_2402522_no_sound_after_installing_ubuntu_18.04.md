---
title: "no sound after installing ubuntu 18.04"
date: 2018-10-01
forum: Hardware
---

### Post by reynoldsnitrr on 2018-10-01
I am very new to linux. My laptop is lava helium 14. It is pre loaded with Windows 10 but because of Academic requirement I have installed Ubuntu 18.04. After Installation, to my surprise there is no sound (both Loud speakers and headphones). please help me. i tried re-installing pulse audio but in vain.

This is the ouput of lspci
00:00.0 Host bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SoC Transaction Register (rev 36)
00:02.0 VGA compatible controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Configuration Registers (rev 36)
00:03.0 Multimedia controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Imaging Unit (rev 36)
00:0b.0 Signal processing controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller (rev 36)
00:14.0 USB controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series USB xHCI Controller (rev 36)
00:1a.0 Encryption controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Trusted Execution Engine (rev 36)
00:1f.0 ISA bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCU (rev 36)

Please help me.
thanks.

---

### Post by Yellow Pasque on 2018-10-01
^I don't see anything relevant in your list. Get more detailed info:
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by C.S.Cameron on 2018-10-01
Atom Cherry-trail processors require a different sound driver for Ubuntu.
The one downloadable from this page worked for my Computestick:

[http://linuxiumcomau.blogspot.com/2018/03/fixing-broken-hdmi-audio-again.html](http://linuxiumcomau.blogspot.com/2018/03/fixing-broken-hdmi-audio-again.html)

---

