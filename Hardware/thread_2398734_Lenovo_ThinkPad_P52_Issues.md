---
title: "Lenovo ThinkPad P52 Issues"
date: 2018-08-16
forum: Hardware
---

### Post by danboyd on 2018-08-16
Hello -- I just bought a Lenovo ThinkPad P52 and booted from a ubuntu 18.04.1 live USB.

The internal NVMe SSD was not detected and the trackpad didn't work.

I'll just run Windows for awhile until this gets fixed, but just wanted to make everyone aware.

---

### Post by mörgæs on 2018-08-16
Hi, welcome to the fora.

Maybe it's already fixed in 18.10. Would it be possible for you to test this one, please?

---

### Post by antiplex on 2018-10-30
@danboyd: sounds like you are booting in legacy mode (BIOS)? try booting through UEFI, which should make nvme-storage-media available.
also: which firmware do you have installed? secure boot enables or disabled? TPM on or off?

I'm currently fighting with installing 18.10 in a dual boot config and havent figured out a seamless solution so far. IIRC, TPM on and secure boot off worked, but provided issues with pre-ibstalled win 10 and bitlocker :/

EDIT: correction of mix-ups above. another important thing is to set hybrid graphics off (discrete) during install, then install the nvidia driver from the repo (390 worked for me, but NOT 390-dkms!) and (if one prefers to) enable hybrid gfx afterwards.

---

