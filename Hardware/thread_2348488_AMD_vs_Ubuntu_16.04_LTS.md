---
title: "AMD vs Ubuntu 16.04 LTS"
date: 2017-01-04
forum: Hardware
---

### Post by andrea-c on 2017-01-04
Hi All
Can anyone cast some light on the new situation between Ubuntu and AMD?
I have a  *[AMD/ATI] Cape Verde PRO [FirePro W600]*
Will I be able to use it if I update to the new LTS?

---

### Post by pakro on 2017-01-04
Hi, 
I found the following link [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD). 
You may run into the problem that your GPU is not compatible with the radeon driver package which is used by default. But as the link states the problem is solvable.

---

### Post by andrea-c on 2017-01-04
Ah that's cool thanks I read on another blog that that provcedure wans't allowed

---

### Post by QIII on 2017-01-04
If by "that procedure" you mean installing Catalyst/fglrx on 16.04, then it is not possible.

When you install 16.04 on a machine with AMD graphics, the installer will determine which of two open source drivers is appropriate:  Radeon or AMDGPU.

Some GPUs will further support AMDGPU-PRO, which is AMDGPU with the proprietary overlay.

But Catalyst/fglrx is dead from 16.04 forward.

---

### Post by donbrew on 2017-01-04
I was finally able to put Ubuntu on my old machine with ATI HD3450 and HD4350 graphics with 16.04LTS!

The only problem I had was that I wanted my 1080P TV to be my only monitor.  Ubuntu/AMD insisted that a VGA monitor be used for installation.  I solved that by using xrandr and adding a couple of lines to .xprofile and monitors.xml.

---

### Post by andrea-c on 2017-01-05
> **QIII said:**
> If by "that procedure" you mean installing Catalyst/fglrx on 16.04, then it is not possible.

When you install 16.04 on a machine with AMD graphics, the installer will determine which of two open source drivers is appropriate:  Radeon or AMDGPU.

Some GPUs will further support AMDGPU-PRO, which is AMDGPU with the proprietary overlay.

But Catalyst/fglrx is dead from 16.04 forward.

Thanks for the clear answer.
So no more proprietary driver then. What's the reason behind it?

---

### Post by pakro on 2017-01-05
you can read about it @ [http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04](http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04)

---

### Post by donbrew on 2017-01-05
Because AMD made open source drivers for the new kernel, finally?:D

---

### Post by QIII on 2017-01-05
Yes.  We got what we've been asking for for years.

Be careful what you ask for.

They worked as a team with open source developers (primarily Canonical).

---

