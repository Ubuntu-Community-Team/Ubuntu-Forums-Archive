---
title: "bumblebeem nvidia-settings, monitors and such"
date: 2014-04-29
forum: Hardware
---

### Post by landersohn-m on 2014-04-29
I have just unstalled xubuntu 14.04 64 bit and get some wierd behaviors that I hope somebody can help me with. I have an HP laptop with Optimus card (Intel integrated graphics & GeForce 650) and I am running a bumbleebee with nvidia-331 drivers. I did manually edit bumblebee.conf to point it to the -331 driver.
The output of "lsmod" is:
drm                   302817  2 i915,drm_kms_helper
rtsx_pci               45956  2 rtsx_pci_ms,rtsx_pci_sdmmc
mii                    13934  1 r8169
video                  19476  1 i915

The output of "optirun lsmod" is
drm                   302817  2 i915,drm_kms_helper,nvidia
rtsx_pci               45956  2 rtsx_pci_ms,rtsx_pci_sdmmc
mii                    13934  1 r8169
video                  19476  1 i915

optirun works, no issues there but here are my problems:


1) under Settings-Displays: I see only a "default" monitor in the configuration dialog, not even the monitor I have. I can attach a second monitor and clone the display but cannot configure it, it does not show up. In the upstart log files I get a message that no device is bound to VGA
2) nvidia-settings apparently requires nvidia-prime, it won't start without it: I get "prime supported? No" and nvidia-settings exits. Running with optirun, it just exits, w/o optirun it also throws a seg fault
3) nvidia-prime does not work at all, nvidia-settings shows nothing as far as X config is concerned.
4) when I logout I don't get the greeter but a black screen and everthing is unresponsive, I have to do a hard power-off.

Does anybody have any ideas?

---

