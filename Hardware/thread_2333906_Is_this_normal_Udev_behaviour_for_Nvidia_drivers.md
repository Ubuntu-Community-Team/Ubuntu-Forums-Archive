---
title: "Is this normal Udev behaviour for Nvidia drivers?"
date: 2016-08-14
forum: Hardware
---

### Post by irvine_himself2 on 2016-08-14
The basic background is important, so bear with me. I have successfully mirrored the display screen of my laptop to the Tv using an HDMI cable. Subsequently, I have written two bash scripts: The first toggles audio output between the Tv and Laptop speakers, and the second configures the mirrored displays. All is fine, so, proceeding to the logical next step, I want the bash which configures mirrored display to run automatically when the Tv is connected.

After a bit of research, the solution seemed to be a Udev rule, and following[ this guide]("https://blog.sleeplessbeastie.eu/2013/01/07/how-to-automatically-set-up-external-monitor/"), I tried to identify the HDMI connection  event with: 

```
udevadm monitor
```

However, rather than getting the expected two line output when I switch the Tv off and on, I get a continuous stream of output from the Nvidia GPU and its drivers being added and removed. After only a few seconds, the resulting piped output  file is larger than the maximum permitted attachment size, but here is a small sample output:

```
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent

UDEV  [14440.552483] remove   /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/drm/card1 (drm)
UDEV  [14440.560974] remove   /bus/pci/drivers/nvidia (drivers)
KERNEL[14440.562213] add      /module/nvidia (module)
KERNEL[14440.563154] add      /kernel/slab/:t-0012288 (slab)
KERNEL[14440.563509] add      /bus/pci/drivers/nvidia (drivers)
KERNEL[14440.563671] add      /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/drm/card1 (drm)
KERNEL[14440.563761] remove   /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/drm/card1 (drm)
KERNEL[14440.563834] remove   /bus/pci/drivers/nvidia (drivers)
KERNEL[14440.563971] remove   /kernel/slab/:t-0012288 (slab)
KERNEL[14440.569458] remove   /module/nvidia (module)
UDEV  [14440.571633] remove   /kernel/slab/:t-0012288 (slab)
UDEV  [14440.577659] add      /module/nvidia (module)
UDEV  [14440.597497] add      /kernel/slab/:t-0012288 (slab)
UDEV  [14440.598784] remove   /module/nvidia (module)
UDEV  [14440.605035] add      /bus/pci/drivers/nvidia (drivers)
UDEV  [14440.619170] add      /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/drm/card1 (drm)
KERNEL[14440.621393] add      /module/nvidia (module)
KERNEL[14440.622310] add      /kernel/slab/:t-0012288 (slab)
KERNEL[14440.622649] add      /bus/pci/drivers/nvidia (drivers)
KERNEL[14440.622790] add      /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/drm/card1 (drm)
KERNEL[14440.622853] remove   /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/drm/card1 (drm)
KERNEL[14440.622887] remove   /bus/pci/drivers/nvidia (drivers)
KERNEL[14440.623014] remove   /kernel/slab/:t-0012288 (slab)
KERNEL[14440.627200] remove   /module/nvidia (module)
UDEV  [14440.635671] remove   /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/drm/card1 (drm)
UDEV  [14440.643708] remove   /bus/pci/drivers/nvidia (drivers)
KERNEL[14440.652367] add      /module/nvidia (module)
KERNEL[14440.653270] add      /kernel/slab/:t-0012288 (slab)
KERNEL[14440.653648] add      /bus/pci/drivers/nvidia (drivers)
KERNEL[14440.653827] add      /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/drm/card1 (drm)
KERNEL[14440.653875] remove   /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/drm/card1 (drm)
KERNEL[14440.653894] remove   /bus/pci/drivers/nvidia (drivers)
KERNEL[14440.654252] remove   /kernel/slab/:t-0012288 (slab)
UDEV  [14440.654911] remove   /kernel/slab/:t-0012288 (slab)
KERNEL[14440.658198] remove   /module/nvidia (module)
UDEV  [14440.666908] add      /module/nvidia (module)
UDEV  [14440.678497] remove   /module/nvidia (module)
UDEV  [14440.680399] add      /kernel/slab/:t-0012288 (slab)
UDEV  [14440.693247] add      /bus/pci/drivers/nvidia (drivers)
KERNEL[14440.697839] add      /module/nvidia (module)
KERNEL[14440.698836] add      /kernel/slab/:t-0012288 (slab)
KERNEL[14440.700519] add      /bus/pci/drivers/nvidia (drivers)
KERNEL[14440.700551] add      /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/drm/card1 (drm)
KERNEL[14440.700577] remove   /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/drm/card1 (drm)
KERNEL[14440.700589] remove   /bus/pci/drivers/nvidia (drivers)
KERNEL[14440.700598] remove   /kernel/slab/:t-0012288 (slab)
UDEV  [14440.705601] add      /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/drm/card1 (drm)
KERNEL[14440.708196] remove   /module/nvidia (module)
UDEV  [14440.722433] remove   /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/drm/card1 (drm)
UDEV  [14440.730862] remove   /bus/pci/drivers/nvidia (drivers)
KERNEL[14440.734712] add      /module/nvidia (module)
KERNEL[14440.735655] add      /kernel/slab/:t-0012288 (slab)
KERNEL[14440.736016] add      /bus/pci/drivers/nvidia (drivers)
KERNEL[14440.736398] add      /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/drm/card1 (drm)
KERNEL[14440.736426] remove   /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/drm/card1 (drm)
KERNEL[14440.736439] remove   /bus/pci/drivers/nvidia (drivers)
KERNEL[14440.736449] remove   /kernel/slab/:t-0012288 (slab)
UDEV  [14440.741292] remove   /kernel/slab/:t-0012288 (slab)
KERNEL[14440.742178] remove   /module/nvidia (module)
UDEV  [14440.749833] add      /module/nvidia (module)
UDEV  [14440.765556] remove   /module/nvidia (module)
UDEV  [14440.767684] add      /kernel/slab/:t-0012288 (slab)
UDEV  [14440.780442] add      /bus/pci/drivers/nvidia (drivers)
KERNEL[14440.782908] add      /module/nvidia (module)
KERNEL[14440.783815] add      /kernel/slab/:t-0012288 (slab)
KERNEL[14440.784178] add      /bus/pci/drivers/nvidia (drivers)
KERNEL[14440.784318] add      /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/drm/card1 (drm)
KERNEL[14440.784386] remove   /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/drm/card1 (drm)
KERNEL[14440.784429] remove   /bus/pci/drivers/nvidia (drivers)
KERNEL[14440.784554] remove   /kernel/slab/:t-0012288 (slab)
KERNEL[14440.789210] remove   /module/nvidia (module)
UDEV  [14440.792506] add      /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/drm/card1 (drm)
KERNEL[14440.809515] add      /module/nvidia (module)
UDEV  [14440.810740] remove   /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/drm/card1 (drm)
KERNEL[14440.810824] add      /kernel/slab/:t-0012288 (slab)
KERNEL[14440.811828] add      /bus/pci/drivers/nvidia (drivers)
KERNEL[14440.812187] add      /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/drm/card1 (drm)
KERNEL[14440.812303] remove   /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/drm/card1 (drm)
KERNEL[14440.812397] remove   /bus/pci/drivers/nvidia (drivers)
KERNEL[14440.812597] remove   /kernel/slab/:t-0012288 (slab)
KERNEL[14440.816162] remove   /module/nvidia (module)
UDEV  [14440.817922] remove   /bus/pci/drivers/nvidia (drivers)
UDEV  [14440.823715] add      /module/nvidia (module)
UDEV  [14440.829403] remove   /kernel/slab/:t-0012288 (slab)
UDEV  [14440.838920] remove   /module/nvidia (module)
UDEV  [14440.856197] add      /kernel/slab/:t-0012288 (slab)
KERNEL[14440.858765] add      /module/nvidia (module)
KERNEL[14440.859681] add      /kernel/slab/:t-0012288 (slab)
KERNEL[14440.860063] add      /bus/pci/drivers/nvidia (drivers)
KERNEL[14440.860200] add      /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/drm/card1 (drm)
KERNEL[14440.860267] remove   /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/drm/card1 (drm)
KERNEL[14440.860306] remove   /bus/pci/drivers/nvidia (drivers)
KERNEL[14440.860434] remove   /kernel/slab/:t-0012288 (slab)
UDEV  [14440.863263] add      /bus/pci/drivers/nvidia (drivers)
KERNEL[14440.865203] remove   /module/nvidia (module)
UDEV  [14440.875851] add      /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/drm/card1 (drm)
KERNEL[14440.887815] add      /module/nvidia (module)
KERNEL[14440.888724] add      /kernel/slab/:t-0012288 (slab)
KERNEL[14440.889088] add      /bus/pci/drivers/nvidia (drivers)
KERNEL[14440.889233] add      /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/drm/card1 (drm)
KERNEL[14440.889301] remove   /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/drm/card1 (drm)
KERNEL[14440.889682] remove   /bus/pci/drivers/nvidia (drivers)
KERNEL[14440.889693] remove   /kernel/slab/:t-0012288 (slab)
UDEV  [14440.893455] remove   /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/drm/card1 (drm)
KERNEL[14440.894181] remove   /module/nvidia (module)
UDEV  [14440.900469] remove   /bus/pci/drivers/nvidia (drivers)
UDEV  [14440.903132] add      /module/nvidia (module)
UDEV  [14440.911530] remove   /kernel/slab/:t-0012288 (slab)
UDEV  [14440.922637] remove   /module/nvidia (module)
UDEV  [14440.939144] add      /kernel/slab/:t-0012288 (slab)
KERNEL[14440.942925] add      /module/nvidia (module)
KERNEL[14440.943855] add      /kernel/slab/:t-0012288 (slab)
KERNEL[14440.944222] add      /bus/pci/drivers/nvidia (drivers)
```

The thing is, at the moment, I am not even using the Nvidia GPU. The laptop is set to use the Intel GPU in power saving mode. For reference I am using Xenial Xerus with proprietary drivers for both the Nvidia and Intel GPU’s

I am a complete Noob when it comes to Udev and have not got a clue about any of this.

Thanks in advance 

Irvine

---

### Post by irvine_himself2 on 2016-08-15
Okay, I am going to mark this as solved, but only because it seems to be a long standing kernel bug, (see demesg output below,) it may also be related to [this bug report]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/342926") on launchpad

For reference, when installing Ubuntu Studio I had problems because the Xserver wouldn't work with the open source Nouvelle drivers, ([see here]("https://ubuntuforums.org/showthread.php?t=2314746"),) I suspect this may be a related issue? On a side note, I was also unable to get  BumbleBee  working.

For general info, here is abridged output of dmesg:

```
               NVRM: information.
[   42.061858] nvidia: probe of 0000:01:00.0 failed with error -1
[   42.061875] nvidia-nvlink: alloc_chrdev_region failed: -16
[   42.061878] Error: Driver 'ebridge' is already registered, aborting...
[   42.061879] nvidia-nvlink: EBRIDGE: No device found!
[   42.062045] NVRM: The NVIDIA probe routine failed for 1 device(s).
[   42.062046] NVRM: None of the NVIDIA graphics adapters were initialized!
[   42.062047] [drm] Module unloaded
[   42.062159] NVRM: NVIDIA init module failed!
[   42.089556] NVRM: This is a 64-bit BAR mapped above 4GB by the system
               NVRM: BIOS or the Linux kernel, but the PCI bridge
               NVRM: immediately upstream of this GPU does not define
               NVRM: a matching prefetchable memory window.
[   42.089560] NVRM: This may be due to a known Linux kernel bug.  Please
               NVRM: see the README section on 64-bit BARs for additional
               NVRM: information.
```


**Workarounds**
This is where it gets difficult. In my case the bug seems to be intermittent with the most immediately visible symptom being the cooling fan switching more frequently to “boost mode”, in other words a slight overheating problem. As a result, short of a fix from the developers, it is very difficult to say with any certainty what effect any workaround has.

[This post]("http://www.domaigne.com/blog/computing/fix-nvidia-optimus-issues-after-fedora-upgrade/") recommended re-installing the associated Nvidia drivers after an upgrade. Tried it, and although I still get hit, it does seem to be less frequent. 

What I have found to be most effective when I confirm a hit by calling “udevadm monitor” is to either reboot or restart the udev service with 

```
sudo /etc/init.d/udev restart
```

It may take two or three restarts before udev stops looping

The reulting dmesg output is:

```
[  300.856079] [drm] Module unloaded
[  300.856269] NVRM: NVIDIA init module failed!
[  312.627046] EXT4-fs (sdc1): error count since last fsck: 10
[  312.627062] EXT4-fs (sdc1): initial error at time 1457936526: ext4_do_update_inode:4504
[  312.627073] EXT4-fs (sdc1): last error at time 1457936703: ext4_put_super:811
[  341.078607] pcieport 0000:00:1c.4: AER: Corrected error received: id=00e4
[  341.078639] pcieport 0000:00:1c.4: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e4(Receiver ID)
[  341.078651] pcieport 0000:00:1c.4:   device [8086:9d14] error status/mask=00000001/00002000
[  341.078660] pcieport 0000:00:1c.4:    [ 0] Receiver Error        
memyself@Mine:~$ 

```

Anyway, although I am marking this thread as solved, if anybody has any insights, solutions or comments, I would be more than happy to hear them.

For now though, I am going to concentrate on figuring out why my first attempt at udev rule is not working. Though I will start a new thread for that issue.

Irvine

---

