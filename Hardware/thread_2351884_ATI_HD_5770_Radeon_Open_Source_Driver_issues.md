---
title: "ATI HD 5770 Radeon Open Source Driver issues"
date: 2017-02-07
forum: Hardware
---

### Post by R.E.A.D001 on 2017-02-07
Hello all,

I've been distro hopping here lately since the xorg change, looking for direct gaming level performance from my ATI HD 5770 video card. I've been able to narrow things down to the AMD open source Radeon driver, as opposed to the AMD driver for newer cards, however it would appear that one of two things are happening here. Either 1, the driver enables itself by default, and the performance just isn't as good as the catalyst driver was, or 2 I am not enabling/installing the new Radeon open source driver properly, and this is what is hurting my video performance. Either way, I'm more than open to suggestions, and would love some feedback/information as to how I can get this card back to full power again under Ubuntu.

Thank you,
R.E.A.D001

---

### Post by QIII on 2017-02-07
Hello!

The Radeon driver is installed by default on any release prior to 16.04.  After that, the default is chosen from Radeon or AMDGPU depending on the capabilities of the GPU.  In your case, Radeon will be the default.  That card is not compatible with AMDGPU.  The Radeon driver is not "new".

fglrx is not an option starting with 16.04, so Radeon is your only option.

The Radeon driver is simply not up to full-on gaming, so there simply isn't much to be done with that GPU.

---

### Post by R.E.A.D001 on 2017-02-07
Ok, thank you for the quick response.

---

