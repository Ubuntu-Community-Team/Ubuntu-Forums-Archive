---
title: "Problems with nVidia during updates"
date: 2013-03-03
forum: Hardware
---

### Post by sloe on 2013-03-03
Every time I do an update, the nVidia driver fails. I've now memorized the steps to fix it, but why should I have to?

Every time I go through the nVidia installer, it asks me if I want to install the DKMS packages for auto-rebuilding of the driver when I update the kernel, and I say **YES**.

It never works, however.  Why not? What am I doing wrong? Does it have something to do with the "Pre-installation script failed to run. Do you wish to continue" error that pops up every time I install the driver?

Oh, BTW, it's an Asus G55VW with an nVidia 660M video card, non-optimus enabled. I'm running the nVidia driver 310.32. And on every reboot after the update and driver fix, I submit the 5 or 6 crash reports for X.org, Compiz, and udev that always pop up.

---

### Post by sloe on 2013-03-03
Curioser and curiouser....

Just fond this in my dpkg list:
```
ii  nvidia-common  1:0.2.71.1   amd64        transitional package for ubuntu-d
ii  nvidia-current 304.64-0ubun amd64        NVIDIA binary Xorg driver, kernel
rc  nvidia-current 304.51-0ubun amd64        NVIDIA binary Xorg driver, kernel
ii  nvidia-setting 304.64-0ubun amd64        Tool for configuring the NVIDIA g
rc  nvidia-setting 304.51-0ubun amd64        Tool for configuring the NVIDIA g

```

and this in dkms:
```

nvidia, 310.32, 3.5.0-25-generic, x86_64: installed
nvidia-current, 304.64, 3.5.0-24-generic, x86_64: installed
nvidia-current, 304.64, 3.5.0-25-generic, x86_64: installed

```

It seems I skipped a step or two when initially getting this thing working in the first place.

So, what exactly did I skip, and how do I clean it up? What other info do y'all need?

---

