---
title: "X server not working"
date: 2016-02-03
forum: Hardware
---

### Post by konx2 on 2016-02-03
Hello everyone.

I am starting a project at my new workplace and I received as heritage from the previous person a laptop. I cannot ask this person details, since he passed away.

The problem I am facing right now is that there is no X server functioning. I have tried to look around for solutions, but so far nothing seems to work.

Useful details of the system:

```

more /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.03 LTS"

```

```

sudo lshw -c video
-display UNCLAIMED
   description: VGA compatible controller
   vendor: Advanced Micro Devices, Inc. [AMD/ATI]
   physical id: 0
   (other stuff)
   capabilities: pm pciexpress msi vga_controller bus_master cap_list
   **configuration: latency=0**

```

From what I have read online, the bold part seems to be important, but I don't understand why.

```

lspci -nnk | grep -i VGA -A3
VGA compatible controller: Advanced micro Devices, Inc. [AMD/ATI]
RV635/M86 [Mobility Radeon HD 3650]
     Subsystem: Hewlett-Packard Company Device [103c:30e7]

```

while if I run the command:

```

lspci -nnk | grep -i VGA -A3 | grep 'Kernel modules'

```

I don't get anything.

I have tried to run Xorg -configure but it didn't solve any problem. I have tried some other solutions involving the creation of a configuration file, but they screwed up the system even more, so I had to revert back to the original solution.

Any help is appreciated! If nothing comes out, I will revert to format and reinstall everything ^^

cheers

Konx

---

