---
title: "ATI Closed Source vs Open Source issues"
date: 2011-02-17
forum: Hardware
---

### Post by ivanmmj on 2011-02-17
Hello guys and girls,

I have an Acer Aspire 5740G with the following specs:
i5 520m
4GB DDR3
ATI HD 5650 (unfortunately, the igp in the i5 is disabled in the BIOS and cannot not be enabled to get switchable graphics.)

I've tried both the open source driver and closed source drivers and I've liked and hated them both for different reasons.

My current setup is:
Tri booting:
Windows 7
Ubuntu 10.10 (I need to back up my data from this partition and just kill it...)
Kubuntu 10.10 (I wanted to try KDE4.6 without mixing QT and GTK programs in the menus.)

Both Ubuntu and Kubuntu are running my own 2.6.37 kernel compiled with several changes as well as some patches to make it more "ubuntu compatible."
Anyhow, I'm using the 11.1 ati driver at the moment. I noticed the following pros and cons, though:

Pros:
[LIST]
[*]Performs well.
[*]Battery life is great (PowerPlay)
[*]Does not over heat (PowerPlay)
[*]The fan isn't at full blast the whole time (PowerPlay)
[/LIST]

Cons:
[LIST]
[*]Upgrading my kernel to 2.6.38 or upgrading to the newer ati driver breaks everything and forces me to work on compiling fixes here and there.
[*]No KMS = no pretty plymouth. Even with the "fixes", the resolutions are always ugly.
[*]It's closed source.
[/LIST]

The open source driver on the other hand is the EXACT opposite (except it also gives decent performance in what I use it for.)

So my question is this: Is there something that I am missing in getting PowerPlay to work on the open source drivers? Has anyone with the same graphics card been able to enable PowerPlay (or something similar (e.g. undervolting, underclocking, fan control) with the open source drivers?

---

### Post by ivanmmj on 2011-02-18
As an update and a bump:

I have found a reference to using radeon.dynpm=1 in grub to enable dynamic power management but I've also found many references (although older posts) of people with similar GPU's having a lot of issues with it.
Before I remove my fgrlx and install the open source drivers to test this: Has anyone had any experience with this switch and the open source ati drivers?

---

### Post by ivanmmj on 2011-02-20
I'm having issues with getting the open source driver to work. I've had it working before but stopped using it because of the power draw and overheating issues but now I can't seem to make it work much (I finally got it partially working but it's only partially accelerated and it seems that KMS isn't on.)

---

### Post by coffeecat on 2011-02-20
If you're trying to get the open source driver working on a system that you've installed the proprietary driver to, and it's not working as well as it did before, then some of the proprietary stuff may not have uninstalled properly. Or some packages associated with the OS driver may need re-installing. Details here:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

---

### Post by ivanmmj on 2011-02-21
> **coffeecat said:**
> If you're trying to get the open source driver working on a system that you've installed the proprietary driver to, and it's not working as well as it did before, then some of the proprietary stuff may not have uninstalled properly. Or some packages associated with the OS driver may need re-installing. Details here:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

I thought the same so after running after that walkthrough, I ended up reinstalling Kubuntu on a free partition but I'm running into the same problem. If I leave it as is, I can't get accelerated stuff enabled. If I use xorg-edgers, I get a corrupted display.

I'll look more into it tomorrow and post more information. I'll go through that walkthrough again though. Thank you.

---

### Post by ivanmmj on 2011-02-22
It turns out the issue was with the kernel I was using and the switch I was using (which is why both the stock kernel and the 2.6.38 kernel failed. I had used the stock kernel with the bad switch and the 2.6.38 kernel with and without a switch.) After recompiling my own 2.6.38 kernel, I've got it running.
As far as powersaving goes, I found the following (that seems to actually be working):

> sudo -i
#to turn yourself into root

echo dynpm > /sys/class/drm/card0/device/power_method
## dynamic clock switching based on GPU load

echo profile > /sys/class/drm/card0/device/power_method
## profile based frequency switching; this is the default mode

And for the profile method, there is also this:

> echo low > /sys/class/drm/card0/device/power_profile 
## forces GPU to lowest available frequency 

echo high > /sys/class/drm/card0/device/power_profile
## forces GPU to highest available frequency

echo auto > /sys/class/drm/card-0/device/power_profile
## switches between high and low frequencies depending on whether the system in on battery power or not

Right now I'm running on dynpm and it is running great. Not all effects are being enabled in Kubuntu's effects manager, but I'm working on that. As for the grub option I was using, it is no longer valid as of 2.6.35.

---

### Post by ivanmmj on 2011-02-25
It looks like the power draw is still a good 10W-12W higher with the open source drivers than with the closed sourced drivers. I guess I'm going to have to keep to the closed source drivers on my laptop until they bring that further down.

---

