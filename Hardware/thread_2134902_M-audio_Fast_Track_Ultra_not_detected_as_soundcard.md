---
title: "M-audio Fast Track Ultra not detected as soundcard"
date: 2013-04-12
forum: Hardware
---

### Post by N00BinTheShell on 2013-04-12
Greetings everyone,

Here is my problem, I'm trying to get my M-Audio Fast Track Ultra sound card to work with my xubuntu.
Unfortunately, my sound card is not detected as one as you can see:

```

sudo asoundconf list
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

Names of available sound cards:
Intel
NVidia
```

even with the following command:
```

lspci -v | grep -i audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
```

but it is well detected on my usb port:
```

lsusb | grep M-Audio
Bus 002 Device 003: ID 0763:2080 Midiman M-Audio RunTime DFU
```

I hope it will be enough for you to know where my problem comes from.
In advance, thanks for answering

---

