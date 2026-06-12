---
title: "is there any way to identify a 16gb intel optane module via terminal ?"
date: 2019-06-14
forum: Hardware
---

### Post by gh0zt362 on 2019-06-14
I was sold a laptop that allegedly has intel optane module . but the experience isnt quite as fluid , bit of lagging . And I just want to view / confirm there is actually an optane module on the motherboard without cracking the laptop case . 

Any way to " see " the module on hardware spec list of any kind ?

---

### Post by TheFu on 2019-06-15
IDK, but does **inxi -Fz** or **inxi -D** show it?  Had to look it up. Seems to be some sort of m.2 storage that intel is claiming to be like RAM, but clearly it is just a disk cache. I'd think special setup would be needed to use it as anything other than storage.  ZFS has a disk cache capability, but it has to be enabled. [https://www.phoronix.com/scan.php?page=article&item=intel-optane-16gb&num=1](https://www.phoronix.com/scan.php?page=article&item=intel-optane-16gb&num=1) says
> the Intel Optane 16GB device was detected right away as an NVMe block device.
 
```
$ inxi -D
Drives:    HDD Total Size: 500.1GB (7.3% used)
           ID-1: /dev/sda model: Samsung_SSD_860 size: 500.1GB
```
Nope. I don't have it.

Found this - seems some setup is needed [https://wiki.ubuntu.com/ServerTeam/Bcache](https://wiki.ubuntu.com/ServerTeam/Bcache) to use it.  I suppose if the machine has a spinning disk, this is like having 2 separate storage devices instead of a hybrid SSDH.

I have an Asus laptop with the same CPU that you have. It came with a slow 1TB HDD, but I swapped that out for a 500G SSD (see above). I actually never booted the HDD, since it has Win10 on it.  When the warranty is up on the laptop, I'll re-purpose that HDD elsewhere.

---

### Post by jeremy31 on 2019-06-15
Intel Optane only works for system acceleration in Windows 10
See [https://www.intel.com/content/www/us/en/support/articles/000024018/memory-and-storage/intel-optane-memory.html](https://www.intel.com/content/www/us/en/support/articles/000024018/memory-and-storage/intel-optane-memory.html) Scroll down to Operating Systems

---

### Post by gh0zt362 on 2019-06-15
First post says works but has to be enabled 

Second says only works on windows. 

Mystery deepens . 

What are all these loop devices as well ?? 

```
$ sudo blkid[sudo] password for gh0tz: 
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sda1: UUID="85C7-C81E" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="974fda74-fc53-4aea-9fed-afc4bba6c4e2"
/dev/sda2: UUID="b14f2c7e-2859-400e-b5d8-0390fd60729d" TYPE="ext4" PARTUUID="3551802a-a5e0-4067-8266-35f38f8f55a7"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"
/dev/loop14: TYPE="squashfs"
/dev/loop15: TYPE="squashfs"
/dev/loop16: TYPE="squashfs"
/dev/loop17: TYPE="squashfs"
/dev/loop18: TYPE="squashfs"
/dev/loop19: TYPE="squashfs"
/dev/loop20: TYPE="squashfs"
```

---

### Post by gh0zt362 on 2019-06-15
uhhhh... why do I have all these /dev/loops ?

```
df -hFilesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           786M  1.5M  785M   1% /run
/dev/sda2       1.8T  106G  1.6T   7% /
tmpfs           3.9G   41M  3.8G   2% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/loop1      565M  565M     0 100% /snap/supertuxkart/78
/dev/loop4       75M   75M     0 100% /snap/audio-recorder/113
/dev/loop5       54M   54M     0 100% /snap/core18/782
/dev/loop9      3.8M  3.8M     0 100% /snap/gnome-system-monitor/87
/dev/loop7      3.8M  3.8M     0 100% /snap/gnome-system-monitor/83
/dev/loop13      90M   90M     0 100% /snap/core/6818
/dev/loop14      54M   54M     0 100% /snap/core18/970
/dev/loop6      565M  565M     0 100% /snap/supertuxkart/90
/dev/loop0       36M   36M     0 100% /snap/gtk-common-themes/1269
/dev/loop3       43M   43M     0 100% /snap/snap-store/136
/dev/loop11     565M  565M     0 100% /snap/supertuxkart/85
/dev/loop2      152M  152M     0 100% /snap/gnome-3-28-1804/55
/dev/loop17      43M   43M     0 100% /snap/snap-store/111
/dev/loop12     917M  917M     0 100% /snap/xonotic/34
/dev/loop15     152M  152M     0 100% /snap/gnome-3-28-1804/51
/dev/loop16      89M   89M     0 100% /snap/core/6964
/dev/loop10     457M  457M     0 100% /snap/wine-platform/128
/dev/loop8       54M   54M     0 100% /snap/core18/941
/dev/loop19      90M   90M     0 100% /snap/core/6673
/dev/loop18      36M   36M     0 100% /snap/gtk-common-themes/1198
/dev/loop20     112M  112M     0 100% /snap/simplescreenrecorder-brlin/69
/dev/sda1       511M  7.6M  504M   2% /boot/efi
tmpfs           786M   12K  786M   1% /run/user/1000
``` 

Could they be the intel optane ?  From what I know of dev loops they cache of files viewed as blocks to speed up the access correct ?

---

### Post by deadflowr on 2019-06-15
To remove the loops run it with -x squashfs like
```
df -hT -x squashfs
```

They relate to snap packages which are installable through the Software store.
To see whether an application in the Store is a snap package or a regular package scroll down to the Details section of the applications software store page.
All snaps will show as available from the Snap Store.

[What are snap packages]("https://en.wikipedia.org/wiki/Snappy_(package_manager)")?

> Could they be the intel optane ? 
No. [s]I don't even think I see the optane listed in the two outputs.
(Well it would have to have something in it mounted to even show in the df output and the blkid output isn't very verbose for that.)

You'd probably want to run something like lshw or inxi to see whether to optane is even usable
Something easy like
```
sudo lshw -C disk
or
inxi -D[/s]
```
I think inxi may or may not be installed and there may or moy not be a more verbose output command that'll give more info on the matter.[/s]

Nevermnid, I didn't pre-skim TheFu's post. Seems to have a far better understanding of it then I.

---

### Post by #&amp;thj^% on 2019-06-15
Introduction to ipmctl and ndctl: [https://software.intel.com/en-us/articles/quick-start-guide-configure-intel-optane-dc-persistent-memory-on-linux](https://software.intel.com/en-us/articles/quick-start-guide-configure-intel-optane-dc-persistent-memory-on-linux)

These two utilities have some common functionality. We&#8217;ll use ipmctl for all tasks except namespace management.

**ipmctl:**

**ipmctl is a platform utility for configuration and management of Intel Optane DC persistent memory modules. It supports the following functionality:**
[list]
    [*]Discovery
    [*]Configuration
    [*]Firmware management
    [*]Security functionality management
    [*]Health monitoring
    [*]Performance tracking
    [*]Debug and troubleshooting on linux:[/list]

**ndctl is a Linux only, vendor-neutral utility used to manage hardware and OS features:**
[list]
    [*]Show Module Information
    [*]Manage Namespaces and Config Labels
    [*]Monitor Health
    [*]Manage Security - Passphrases and Secure Erase
    [*]Error Injection/Testing[/list]

For more information about ndctl, see the NDCTL User Guide at pmem.io. :[https://github.com/intel/ipmctl](https://github.com/intel/ipmctl)
```
NDCTL(1)                         ndctl Manual                         NDCTL(1)

NAME
       ndctl - Manage "libnvdimm" subsystem devices (Non-volatile Memory)

SYNOPSIS
       ndctl [--version] [--help] [OPTIONS] COMMAND [ARGS]

OPTIONS
       -v, --version
           Display ndctl version.

       -h, --help
           Run ndctl help command.

DESCRIPTION
       ndctl is utility for managing the "libnvdimm" kernel subsystem. The
       "libnvdimm" subsystem defines a kernel device model and control message
       interface for platform NVDIMM resources like those defined by the ACPI
       6.0 NFIT (NVDIMM Firmware Interface Table). Operations supported by the
       tool include, provisioning capacity (namespaces), as well as
       enumerating/enabling/disabling the devices (dimms, regions, namspaces)
       associated with an NVDIMM bus.

COPYRIGHT
       Copyright (c) 2016 - 2019, Intel Corporation. License GPLv2: GNU GPL
       version 2 http://gnu.org/licenses/gpl.html. This is free software: you
       are free to change and redistribute it. There is NO WARRANTY, to the
       extent permitted by law.

SEE ALSO
       ndctl-create-namespace(1), ndctl-destroy-namespace(1),
       ndctl-check-namespace(1), ndctl-enable-region(1),
       ndctl-disable-region(1), ndctl-enable-dimm(1), ndctl-disable-dimm(1),
       ndctl-enable-namespace(1), ndctl-disable-namespace(1),
       ndctl-zero-labels(1), ndctl-read-labels(1), ndctl-inject-error(1),
       ndctl-list(1), LIBNVDIMM
       <https://www.kernel.org/doc/Documentation/nvdimm/nvdimm.txt> Overview"
       , NVDIMM Driver
       <http://pmem.io/documents/NVDIMM_Driver_Writers_Guide.pdf> Writer&#8217;s
       Guide"

ndctl                             2019-05-11                          NDCTL(1)
```
Also just for viewing memory:
```
sudo inxi -mxxx
Memory:
  RAM: total: 11.43 GiB used: 1.34 GiB (11.7%) 
  Array-1: capacity: 16 GiB slots: 2 EC: None max module size: 8 GiB 
  note: est. 
  Device-1: ChannelA-DIMM0 size: 4 GiB speed: 1600 MT/s type: DDR3 
  detail: synchronous bus width: 64 bits total: 64 bits 
  manufacturer: Hynix/Hyundai part-no: HMT351S6EFR8C-PB serial: 0A77933A 
  Device-2: ChannelB-DIMM0 size: 8 GiB speed: 1600 MT/s type: DDR3 
  detail: synchronous bus width: 64 bits total: 64 bits 
  manufacturer: Hynix/Hyundai part-no: HMT41GS6AFR8C-PB serial: 33A6384C 

```
And for storage look at:
```
inxi -D
Drives:
  Local Storage: total: 5.62 TiB used: 3.59 TiB (63.9%) 
  ID-1: /dev/sda vendor: Intel model: SSDSC2BW180A3L size: 167.68 GiB 
  ID-2: /dev/sdb type: USB vendor: Western Digital model: WD My Book 1140 
  size: 1.82 TiB 
  ID-3: /dev/sdc type: USB vendor: Western Digital 
  model: WD My Passport 25E1 size: 1.82 TiB 
  ID-4: /dev/sdd type: USB vendor: Western Digital 
  model: WD My Passport 25E2 size: 1.82 TiB 


```

---

### Post by gh0zt362 on 2019-06-15
```
 sudo inxi -mxxxMemory:    RAM: total: 7.67 GiB used: 1.59 GiB (20.8%) 
           Array-1: capacity: 32 GiB slots: 2 EC: None max module size: 16 GiB note: est. 
           Device-1: Bottom-Slot 1(left) size: 8 GiB speed: 2400 MT/s type: DDR4 detail: synchronous unbuffered (unregistered) 
           bus width: 64 bits total: 64 bits manufacturer: Micron part-no: 8ATF1G64HZ-2G6E1 serial: 1D0FCE54 
           Device-2: Bottom-Slot 2(right) size: No Module Installed 
```


I dont even see the optane module listed . Im thinking i may have been lied to .

---

### Post by TheFu on 2019-06-15
There's something funky about your copy/paste above.  Perhaps you could put the \n characters where they are needed so it looks like the terminal output?

Also, since it is an m.2 storage connection, I wouldn't be surprised if it shows up in the storage output, not the RAM output from inxi.

---

### Post by #&amp;thj^% on 2019-06-15
TheFu may be on to something, Initially, Intel launched Optane as a memory module designed to provide an additional data cache between its CPUs and storage devices such as traditional hard drives (HDDs). Since then, Optane-based solid state drives (SSDs) have been released.

Most consumers will first experience Optane memory in its module form, where Intel is positioning it as a way to get expensive, SSD-style speed and responsiveness in systems equipped with slower (but cheaper) spinning HDDs. As a memory module, Optane does not replace traditional DRAM but serves a similar purpose, holding frequently used data and programs so they can be fed instantly to the CPU.

---

### Post by gh0zt362 on 2019-06-15
Not sure what you mean by /n  .   I know my way around linux but i still have much to learn so I apologize if the syntax is wrong . 

lsblk doesnt seem to list it either .  I got took !!   

```
$sudo lsblk[sudo] password for gh0tz: 
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0    7:0    0  35.4M  1 loop /snap/gtk-common-themes/1269
loop1    7:1    0   564M  1 loop /snap/supertuxkart/78
loop2    7:2    0 151.2M  1 loop /snap/gnome-3-28-1804/55
loop3    7:3    0  42.8M  1 loop /snap/snap-store/136
loop4    7:4    0  74.9M  1 loop /snap/audio-recorder/113
loop5    7:5    0  53.7M  1 loop /snap/core18/782
loop6    7:6    0   564M  1 loop /snap/supertuxkart/90
loop7    7:7    0   3.7M  1 loop /snap/gnome-system-monitor/83
loop8    7:8    0  53.7M  1 loop /snap/core18/941
loop9    7:9    0   3.7M  1 loop /snap/gnome-system-monitor/87
loop10   7:10   0 456.4M  1 loop /snap/wine-platform/128
loop11   7:11   0   564M  1 loop /snap/supertuxkart/85
loop12   7:12   0 916.7M  1 loop /snap/xonotic/34
loop13   7:13   0  89.4M  1 loop /snap/core/6818
loop14   7:14   0  53.7M  1 loop /snap/core18/970
loop15   7:15   0   151M  1 loop /snap/gnome-3-28-1804/51
loop16   7:16   0  88.4M  1 loop /snap/core/6964
loop17   7:17   0  42.8M  1 loop /snap/snap-store/111
loop18   7:18   0  35.3M  1 loop /snap/gtk-common-themes/1198
loop19   7:19   0  89.3M  1 loop /snap/core/6673
loop20   7:20   0 111.5M  1 loop /snap/simplescreenrecorder-brlin/69
sda      8:0    0   1.8T  0 disk 
&#9500;&#9472;sda1   8:1    0   512M  0 part /boot/efi
&#9492;&#9472;sda2   8:2    0   1.8T  0 part /
sr0     11:0    1  1024M  0 rom  

```

---

### Post by TheFu on 2019-06-15
\n ---- a newline.  The inxi output in #8 doesn't have them where they were in the terminal. When it is hard to read, nobody will read it.

```
inxi -D
```
Please, as suggested  .... in post #2.

BTW, does the BIOS show it?
Fresh Optane article:
[https://www.phoronix.com/scan.php?page=article&item=optane-linux-raid&num=1](https://www.phoronix.com/scan.php?page=article&item=optane-linux-raid&num=1)
**Optane SSD RAID Performance With ZFS On Linux, EXT4, XFS, Btrfs, F2FS**

---

### Post by gh0zt362 on 2019-07-04
Ok , I wasn't as brave messing with the BIOS but I finally went in there. The intel optane is registering as a raid device which im pretty sure lsblk isnt registering as a NvMe device.   It had an option to " reset to non-optane " erasing all the data on the disk . 

Obviously not knowing the ramifications of such an operation I backed out of it .  Just knowing it is there is a good start . 

So , researching a bit I found an article or two referencing a possible resetting from raid to AHCI to use ubuntu drivers to identify the optane module as an Nvme device .  Is this possible without losing my current OS ( ubuntu studio 19.04 ) hdd ? 
 

What will reset to non-optane do ?   what data is currently on the module considering ubuntu cant see it ?


As I said identifying the module being there in BIOS is a good start . Now what ?

---

### Post by gh0zt362 on 2019-07-04
Ok , after much reading . It seems the 16gb optane module is utterly useless on an already installed HDD example of Ubuntu . 

The only use it has apparently is if you are installing a fresh distro to the module from LIVEusb stick if im not mistaken . Only then can it be discovered as an NVMe block device. 

Can anyone confirm this to be correct ?   

As far as I can tell I have a 16gb optane module but cant do anything with it ......at all .  Im surprised it cant be repurposed in an existing installed distro .  Oh well .

---

### Post by gh0zt362 on 2019-07-04
Ok , perhaps pull optane and buy a m.2 SSD ?  will that get me a new drive visible from ubuntu ?  would reset to non optane get me a 16gb ssd ?  I dunno what something that small would be good for but .

---

### Post by oldfred on 2019-07-04
Some info:
       Intel Optane - See Intel response that no performance difference between RAID & AHCI.
[https://communities.intel.com/thread/121155](https://communities.intel.com/thread/121155) 
    
       HP Pavilion Gaming Laptop 15 -cx0049nr Disable Optane memory
[https://askubuntu.com/questions/1134503/cant-boot-ubuntu-because-windows-10-rewrites-entire-efi-partition-solved](https://askubuntu.com/questions/1134503/cant-boot-ubuntu-because-windows-10-rewrites-entire-efi-partition-solved)

If you have a SSD, I am not sure that Optane module buys much. As posted above, vendors were required to add hardware (small SSD) as boot cache to make Windows boot faster. Otherwise not used. Intel seems to have used Optane as its brand.
But with SSD dropping in price & especially with faster still  NVMe SSDs also dropping in price, less need for a boot cache.

If boot cache was large enough, some user have used it just for / and had /home on HDD. But then Windows could not use it. Some had 32GB SSD and 8GB of RAM. Only 8GB of 32 was ever used and I have seen user keep Windows cache & still then add / to that small SSD. Probably had  32GB as system may support 32GB of RAM and cache would then need to be that large.

[https://www.intel.com/content/www/us/en/architecture-and-technology/intel-optane-technology/reimagine-memory-storage-in-the-data-center.html](https://www.intel.com/content/www/us/en/architecture-and-technology/intel-optane-technology/reimagine-memory-storage-in-the-data-center.html)

---

### Post by gh0zt362 on 2019-07-04
I have an HDD spinup disk .   Perhaps it may have use as a generic drive cache ?   Does anyone know what resetting to non-optane does to the disk in BIOS ?

---

### Post by gh0zt362 on 2019-07-04
So if thats true and its really useless with ubuntu can I pull it and put in an M.2 1tb SSD for ubuntu to use ?

---

### Post by #&amp;thj^% on 2019-07-04
> **gh0zt362 said:**
> Does anyone know what resetting to non-optane does to the disk in BIOS ?
[https://www.dell.com/support/article/us/en/04/sln306541/optane-enabled-system-may-not-boot-when-a-hard-drive-or-optane-device-fails?lang=en](https://www.dell.com/support/article/us/en/04/sln306541/optane-enabled-system-may-not-boot-when-a-hard-drive-or-optane-device-fails?lang=en)

---

### Post by gh0zt362 on 2019-07-04
I better just leave it alone.   All that intel gui there isnt even available for ubuntu .   .  Maybe ill just scrap the HDD and the optane and put a 2tb SSD in this thing,  That would make it faster .

---

