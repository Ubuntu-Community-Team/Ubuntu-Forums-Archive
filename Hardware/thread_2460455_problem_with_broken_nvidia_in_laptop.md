---
title: "problem with broken nvidia in laptop"
date: 2021-04-10
forum: Hardware
---

### Post by warex on 2021-04-10
Few days ago I started having problems with nvidia graphics card. Artifacts appeared (screenshot). Sony laptop with i5-2450m processor and nvidia 540m card (the rest of the specifications are shown in the screenshot).

After a short time, the computer freezes. When I run live cd with nomodeset option my computer stopped freezing but there are still artifacts.
I am asking for advice what next? I would like to switch to a card built into the hd 3000 processor with complete omission of nvidia. Can it be done and will it help? If so, how. I can install ubuntu from scratch.

---

### Post by CelticWarrior on 2021-04-10
IF you can switch then at Nvidia X Server Settings it should show both profiles. Change and reboot.

---

### Post by warex on 2021-04-11
I don't have this  at Nvidia X Server Settings. I used prime-selector. Yes, it shows intel, but screen is crapy and system halt.

---

### Post by CelticWarrior on 2021-04-11
Your hardware is definitely defective.

---

### Post by warex on 2021-04-11
> **CelticWarrior said:**
> Your hardware is definitely defective.

Yep, Sherlock ](*,), I know... I am here because I wonder if it is possible to bypass nvidia programmatically, because the specialist says that it is necessary to replace the card or motherboard.

---

### Post by CelticWarrior on 2021-04-11
No specialist would say that. 
Either it's possible to toggle or enable/disable the dGPU Nvidia and use the iGPU Intel in UEFI ("BIOS") or, if not, the only option is to toggle via software, i.e. by the Nvidia driver (Ubuntu or Windows). The latter option is what you already tried with prime-select. Again it should be available for profile selection at Nvidia X Server Settings. Not having such option suggests the wrong Nvidia driver is installed and/or Secure Boot is enabled and/or the driver itself is broken due to improper installation or too many "experiences" installing several different versions or installing it directly from downloaded Nvidia binaries.

In any case, if you were actually successful in toggling the Intel Graphics and had issues, that suggests the motherboard itself is now defective.

---

