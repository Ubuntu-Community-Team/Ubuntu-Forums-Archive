---
title: "Big graphical issue with ASUS 1215N and Ubuntu 10.04 / 10.10"
date: 2010-11-11
forum: Hardware
---

### Post by goldenfly on 2010-11-11
Hey guys:

    I installed Ubuntu 10.10 from USB onto my new 1215N, and everything seemed to be working just fine during the install and then during the next boot-up. But then, 1 day later, starting from when I powered up the laptop, I observed the following symptoms:

- screen was backlit (as expected)
- text and images would pop up BRIEFLY, then the screen would turn into black. This "flicker" phenomenon would occur once every 10-20 seconds. This occurs at boot time, and happens during POST / BIOS settings / GRUB / different OS.
- booting into Windows 7, Ubuntu 10.10, nor the recovery partition could solve this issue
- when I attached an external monitor through VGA to the machine, the external monitor was displaying things properly, although the laptop screen would still be predominantly black.

I could not find any other references of people experiencing this type of issue, and I suspect that part of the reason might have to do with the switching between the Intel GMA and NVidia Ion 2 graphics chipsets, most likely during Ubuntu shutdown process. By the way, I DID NOT enable the proprietary NVidia drivers (since I read reports that it was not working with GNOME, and I did indeed prove that myself).

I found out that after forcing a hard power cycle (i.e. disconnecting the AC adapter AND disconnecting the battery for over 1 minute), the laptop screen would display properly upon booting into Windows 7 (i.e. as soon as you see the Windows 7 logo).

I'm still not sure exactly what is the problem, and I'm not even convinced that the steps I described above actually resolves the problem. Can anybody help me out here?

P.S.: I just tried to install 10.04, and during the installation process the screen was turned off (most likely due to power management). Unfortunately afterwards, the "flicker" phenomenon began exhibiting itself. This suggests that the problem does not have to do with 10.10 specifically.

---

