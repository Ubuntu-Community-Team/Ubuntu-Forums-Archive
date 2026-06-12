---
title: "Lubuntu 13.10: Problems with Optimus, and weird UI behavior."
date: 2013-10-19
forum: Hardware
---

### Post by TamarinNOR on 2013-10-19
The card does not show up in the Software & Updates software. But it is recognized in PCI Devices in System Information.

How can I get this card to work with the native drivers?

Also, now it seems to have a rather weird behavior as well. The two screens seems to be identical, and I can't find any option to seperate them in LXDE. However, it says the two screens have different resolutions, that seems to be wrong. The laptop seems to copy the external monitor, this leads to that the resolution is the same in both windows, but also that what is not fitted in the laptop screen falls outside the windows. And this again leads to if  I click the maximize button in a window, it makes the window fill the laptop screen, making it not cover the full space available in the external monitor. Ironically, this leads to the window can fill up more space if I press maximize/restore again to un-maximize it. Is this some weird behavior of the Nouveau driver?

Output of lspci | grep VGA :
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 540M] (rev a1)

---

