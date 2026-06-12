---
title: "Single-shot speaker test does not work with alsa"
date: 2016-11-15
forum: Hardware
---

### Post by PeterTaps on 2016-11-15
Environment: Ubuntu 12.04, Kernel 3.2, Openbox
Audio card: Xonar DG
Audio: Only Alsa. No pulse.

Hi,

When I run the following command, all the six speakers work as expected:

$ speaker-test -c6 -Dhw:1,0 -twav

But when I try to test individual speakers, there is no sound produced:

$ speaker-test -c6 -Dhw:1,0 -twav -s1

There is no error reported either.

I see a similar problem with any other speaker number.

This problem seems to be with Xonar DG card only. All other cards seem to work fine.

We didn't have to install any special driver for this card. As I understand, this card is inherently supported by any Linux kernel 3.14 or better.

I am wondering if anyone knows why six-speaker test would work but single-shot speaker test would not produce any audio.

Thank you in advance for your help.

Regards,
Peter

---

