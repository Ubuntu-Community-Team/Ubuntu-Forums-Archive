---
title: "Kernel upgrade breaks suspend"
date: 2020-10-18
forum: Hardware
---

### Post by StoneyHillZA on 2020-10-18
Hi,

With kernel 5.4.0-47-generic, suspend works flawlessly. With 5.4.0-48-generic and later versions, the display refuses to wake up after a suspend.

Is there something I can do to resolve the issue and where's the best place to report the issue?

```
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.1 LTS
Release:    20.04
Codename:    focal
$ uname -a
Linux OptiPlex-380 5.4.0-47-generic #51-Ubuntu SMP Fri Sep 4 19:50:52 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
$ sudo dmidecode -t 2
# dmidecode 3.2
Getting SMBIOS data from sysfs.
SMBIOS 2.5 present.

Handle 0x0200, DMI type 2, 8 bytes
Base Board Information
    Manufacturer: Dell Inc.
    Product Name: 01TKCC
    Version: A01
    Serial Number: ..CN7360413H00SW.
```

Selected output from nvidia-settings:
```
Nvidia driver version: 440.100
Screens: 1
GPU: GeForce GT 710
Bus Type: PCI Express x8 Gen1
```

---

### Post by ra7411 on 2020-10-18
I had suspend / wakeup problems over several Ub versions, over three AMD desktop machines, with a lot of time wastage looking for solutions. I finally figured out that it was a kernel problem.

The way I solved it with 18.04 was to use "ubuntu kernel update utility" to find a kernel version that didn't have suspend / wakeup failures (with my hardware), then to suspend kernel updates using: sudo apt-mark hold 5xxxxxx for the kernel that worked.

Kernel updates do have some security features, but I've run into no problems doing things this way for 8 months. The people developing the kernel updates are either unaware or unable to avoid causing problems with suspend/wakeup which is a major convenience in computer usage.

---

### Post by StoneyHillZA on 2020-10-19
Locking a particular kernel version works for now, but I anticipate keeping this hardware for some years still and I'm going to bump up against this issue again in the future. I feel it's worth reporting the error as I have identified two adjacent kernel releases with one working and the other not. The problem is now confined to a limited number of changes.

I wonder if the Ubuntu community has a mechanism for reporting kernel errors upstream or is the user expected to dive into kernel.org?

---

### Post by ra7411 on 2020-10-19
Try this and let us know how it goes.

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by StoneyHillZA on 2020-10-19
> **ra7411 said:**
> [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Thanks, good clear instructions here.

[Bug reported]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1900584")

---

### Post by MartyBuntu on 2020-10-19
Kernel upgrades are not the same thing as OS upgrades. That's a "Windows thing".

Stick with the stable kernel release unless it addresses a specific problem...and not just "it feels better".

---

