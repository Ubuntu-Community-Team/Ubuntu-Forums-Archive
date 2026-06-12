---
title: "Suggestion: UpdateManager"
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by damies on 2009-09-13
Hi All,

First let me say I love Ubuntu, Thanks.

I would like to suggest that an option be added to Update Manager's setting to not download kernel updates. The reason is I have often found that to get support for some piece of hardware you need to compile a driver, as soon as you get a kernel update the driver fails and so does the hardware, this is fine, but a bit annoying for someone like me who can compile a driver. It would be a much bigger pain for someone who is scared of a command line.

As a better long term solution kernel/drivers that weren't so interdependent would be better, ie a driver should be compiled by default for the major kernel version ie 2.6 and only need compiling for the next major version ie. 2.7 or even better from 3.0 to 4.0

So I guess it's really 2 suggestions. Some examples of where I have experienced this is: virtual box guest additions, vmware host network drivers, dvb tv tuner cards.

Dave.

---

### Post by jacksaff on 2009-09-13
Much of what you want is implemented in DKMS which automatically recompiles drivers for a new kernel.

If you want to make sure your kernel doesn't upgrade, search for 'linux' in synaptic, select your kernel and click 'lock version' in the 'package' menu.

---

### Post by snowpine on 2009-09-13
Hi Dave, the solution is simple:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

will give you all updates, including kernel updates.

```
sudo apt-get update
sudo apt-get upgrade
```

will skip kernel updates.

I have no idea why that option isn't part of the GUI update manager; another reason to use the command line I guess. :)

ps You also always have the option to choose your old kernel from the GRUB menu if the new kernel breaks something.

---

