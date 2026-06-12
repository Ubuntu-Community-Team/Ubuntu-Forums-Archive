---
title: "Driver for ATI Radeon HD 3870X2"
date: 2009-12-19
forum: Hardware
---

### Post by wi11iamedward on 2009-12-19
I am having horrible issues from setting up the driver for my graphics card. Currently Ubuntu will run but to change any of the preferences for the display (30in HP monitor) it won't accept Normal or Extra... errs with "Desktop effect could not be enabled".

There is a Restricted Driver for the card however when it installs it creates a watermark on the bottom right. And thus far every time I uninstall the driver or use xserver I have to reinstall due to Ubuntu not reverting back to the original setup.

Here's the card I have. Thanks for your help.

EAH3870X2/G/3DHTI/1G
ATI Radeon HD 3870X2

---

### Post by hselvaggi on 2009-12-20
Hi,

I have had some problems installing the propietary driver for ATI on my machine. I tried this [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) and it work on my machine, now I have a really good aceleration. So I think this will work for you also.

The only problem is that after doing those steps I'm not able to run compiz, everytime I try to start compiz I get a white screen and I can't see nothing else than the cursor. I read that it is posible to be something that fglrx has left on my machine, so I tried to all the steps that page says to remove it but I still have the same problem.

running dpkg -nn | grep '*fglrx*' I got this:

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  fglrx-amdcccle <none>         (no description available)
un  fglrx-control  <none>         (no description available)
un  fglrx-control- <none>         (no description available)
un  fglrx-driver   <none>         (no description available)
rc  fglrx-kernel-s 2:8.660-0ubunt Kernel module source for the ATI graphics ac
ii  fglrx-modalias 2:8.660-0ubunt Identifiers supported by the ATI graphics dr
un  xfree86-driver <none>         (no description available)
rc  xorg-driver-fg 2:8.660-0ubunt Video driver for the ATI graphics accelerato

Does anybody has any ideas about how to fix compiz ?

Regards:
Harold.

---

### Post by asyed94 on 2009-12-29
I posted instructions on how to hack and install the proprietary ATI drivers to make them work with the 3870x2 abd get rid of the "Unsupported Hardware" watermark here: [http://ubuntuforums.org/showthread.php?t=1272346](http://ubuntuforums.org/showthread.php?t=1272346). Hope it helps.

---

