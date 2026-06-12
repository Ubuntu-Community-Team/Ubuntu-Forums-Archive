---
title: "Touchpad lags when performing CPU-heavy tasks"
date: 2021-04-07
forum: Hardware
---

### Post by totallynotviggo on 2021-04-07
I recently installed Ubuntu 20.10 on my laptop, and have been experiencing some issues with the touchpad lagging behind when performing CPU-heavy tasks. I also tried downgrading to 20.04 LTS and installing the ```
xserver-xorg-input-synaptics
``` package as well as trying the ```
xserver-xorg-input-synaptics-hwe-18.04
``` package, but nothing so far has worked. I think this may be a Gnome issue though, as it doesn't happen on any distros that use a different DE. Any tips on how to solve this?

Thanks, totallynotviggo

Edit: Fixed some formatting

---

### Post by CelticWarrior on 2021-04-07
Welcome.

> [COLOR=#000000]I think this may be a Gnome issue though, as it doesn't happen on any distros that use a different DE. Any tips on how to solve this?[/COLOR]
There are lots of choices in the Ubuntu family. If you have an old and/or underpowered computer then Gnome, the standard in Ubuntu, isn't recommended indeed.

---

### Post by totallynotviggo on 2021-04-07
I have a Lenovo Ideapad S130-11IGM with 4GB RAM, an Intel Celeron N4000 processor and 64gb Storage and Gnome runs just fine on it except for this. I feel like this is more a driver issue in Gnome to be honest.

---

### Post by CelticWarrior on 2021-04-07
No, it isn't a driver issue.

It's an entry level CPU with embedded graphics coupled with the bare minimum RAM by current standards/requirements and an OS (and swap) running in a (comparatively to SATA SSD and NVME) slow onboard MMC drive.
It is what it is and a very cheap hardware that does a lot of light tasks, everything about it screams "please don't abuse me". It is not designed for any heavy load and as long as users understand this and adjust their expectations then it's a nice little computer, silent and with plenty of battery life.

---

