---
title: "LVM not detecting one of my drives on boot"
date: 2012-09-21
forum: Hardware
---

### Post by ericartman_ on 2012-09-21
Hi there. Right now when I try to boot in to linux (Arch, though this question is probably not specific to that distro) I get an error from lvm saying that it is able to detect two of my drives, but not the third which is plugged in via USB. I've tried booting in to an Ubuntu livecd, and, once booted, the volume group works fine, but, because my /boot partition is in that group, I cannot boot in to arch right now. How do I fix this?

The error looks like this:
```

Couldn't find device with uuid bla bla bla.
Refusing activation of partial LV data. Use --partial to override.
2 logical volume(s) in volume group "VolGroup" now active

```

There are three drives in the group. The boot just stops at this point.

---

