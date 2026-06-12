---
title: "Installing Bumblebee causes lightdm to not startup"
date: 2015-12-18
forum: Hardware
---

### Post by TheReturningVoid on 2015-12-18
Hello everyone,

I'm trying to setup Bumblebee alongside the proprietary nVidia drivers (nvidia-352 package). However, upon rebooting, lightdm doesn't start properly and leaves me on a screen looking like [this]("http://i.imgur.com/TnbzlL1.png"). I have to boot into failsafe graphics mode and remove the bumblebee packages to be able to log in normally again. My card is a GeForce GTX 765M. The card on it's own with proprietary drivers will work fine, but it's Bumblebee that causes lightdm to trip up at boot.

Using Ubuntu 15.10 installed from LiveUSB in UEFI boot mode.

Output of "uname -a":
```

Linux shiny-box 4.2.0-22-generic #27-Ubuntu SMP Thu Dec 17 22:57:08 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

Output of "lspci | grep VGA":
```

00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
01:00.0 VGA compatible controller: NVIDIA Corporation GK106M [GeForce GTX 765M] (rev a1)

```

If anymore information is needed, let me know and I will supply.

Thanks in advance!

---

