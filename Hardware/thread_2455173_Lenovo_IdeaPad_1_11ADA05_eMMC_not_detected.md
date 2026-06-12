---
title: "Lenovo IdeaPad 1 11ADA05: eMMC not detected"
date: 2020-12-14
forum: Hardware
---

### Post by Tiedemate on 2020-12-14
Hey guys,

I have a Lenovo IdeaPad 1 11ADA05 on which I would like to install Kubuntu. I can boot into the live session just fine, everything works (graphics, WiFi, Sound...). However the installer doesn't see the eMMC this machine has. I've played around with different UEFI settings, secureboot on and off, the thing even has a "setup mode" in the UEFI, but nothing seems to make a difference. A generic non-machine specific Windows10 installation USB stick sees the eMMC and installs fine, so I guess it can't be too exotic?!? Here's a hw-probe out of the live session, I can't even tell if the kernel find's the SD-controller to which the eMMC is supposedly connected, can anyone have a look? 
[https://linux-hardware.org/?probe=5885335d44](https://linux-hardware.org/?probe=5885335d44) 
It seems to run Kubuntu very nicely and would be a pity if I couldn't install it. The UEFI lists the eMMC as Ramaxel 64GB and furthermore "hard disk" as not installed. I opened the case and found mounting holes to mount an M.2 (I guess), there are also the soldering pads on the PCB but the M.2 socket is not soldered on, so that would only be a last resort solution, if the eMMC can't be used at all...

Looking forward to any hints!
Björn

PS: attached are some screenshot of the Windows device manager, if that helps...

---

### Post by leprotic on 2021-02-02
Hi. I also got a 11ADA05 yesterday. It was an emergency and I thought the price was quite good for this configuration, just like thousands of others (apparently it's selling pretty well).

So I have the same problem. In case you've been wondering if this is an Ubuntu issue, I've tried quite a few distros (Ubuntu 20.04 / 20.10, Pop OS, Mint, ...) to no avail. I've tried pretty much all the combinations of bios options (UEFI, legacy support, secure boot,..).

As far as I understand, the problem seems to be about the proper eMMC drivers. even the latest kernel doesn't support it. there a few suggestions in different forums but none of the did the trick for me.

I can't believe there are so many unresolved cases escalated online, yet no viable solution. I've been using Linux at home for more than 20 years now. I'm far from a power user or an expert but it never took me more than a few hours to fix any problem with the help of the community (and I'm talking about dozens of problems), even 20 years ago when there were significantly fewer users you could get help from.

I'll keep trying of course and keep you posted if I can fix it.

Are we really stuck with windows in the year 2021? It feels weird.

---

### Post by Tiedemate on 2021-05-14
With the mainline Kernel 5.13.0-051300rc1-generic I now get the mmc device! Have not done anything with it, but it's a huge step forward!

---

