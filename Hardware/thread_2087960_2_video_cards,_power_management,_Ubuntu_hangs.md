---
title: "2 video cards, power management, Ubuntu hangs"
date: 2012-11-25
forum: Hardware
---

### Post by pianisteg on 2012-11-25
Hello!

My system is Ubuntu 12.10. New Samsung notebook with NVidia Optimus. There are two video cards:

```

00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 0de8 (rev ff)

```

I tried to install proprietary drivers &#8212; compiz crashes, unity do not start. :(

I decided to switch off second video card:

```

echo "OFF" > /sys/kernel/debug/vgaswitcheroo/switch

```

Everything works fine, but now computer hangs when I try to reboot or awake after sleep mode.

If I turn videocard ON and go to suspend mode, everything works fine.

I guess, there is simple solution how to switch off second video card and make Ubuntu not to hang?

Can anyone help me? Thanks!

---

### Post by pianisteg on 2012-11-25
Solved my problem installing bumblebee:

```

add-apt-repository ppa:bumblebee/stable
apt-get update
apt-get install virtualgl-libs:i386 libgl1-mesa-glx:i386 libc6:i386
apt-get install acpi-call-tools acpi-call-source bbswitch-dkms bumblebee virtualgl

```

There is useful wiki page: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

