---
title: "sda drive now nvme!"
date: 2017-11-17
forum: Hardware
---

### Post by debdrex on 2017-11-17
[FONT=arial]I dual-installed Ubuntu 16.04 onto an HP Spectre X360[COLOR=#000000] convertible 13-acOXX with Windows 10 two weeks ago. I'm new to Linux.

I noticed yesterday that my hard drive has somehow changed from an SDA to NVME. I definitely have an SSD drive not HDD. I don't know if this is related but when I logged into Windows instead of Linux I found that Windows is now very slow and more irritating to use than it was when I started using Ubuntu.

When I ran **sudo lshw** I couldn't find any hard drive in the list.This could be my inexperience, but there was nothing that I could recognize as a drive. 

I also checked **/dev, lsblk** and **mount **as well as
Disks in the GUI and the drive is NVME.

Any ideas about what I've done or what has happened and how to fix it?

Thanks,
Debbie[/COLOR][/FONT]

---

### Post by TheFu on 2017-11-18
Google found this: [https://itpeernetwork.intel.com/finding-your-new-intel-ssd-for-pcie-think-nvme-not-scsi/](https://itpeernetwork.intel.com/finding-your-new-intel-ssd-for-pcie-think-nvme-not-scsi/)

I don't have any nvme hardware, so I've never seen this.  My m.2 SATA devices show up as sdX (where 'sd' is for SATA or SCSI).

Device names change all the time based on the driver used.  If it is working, I wouldn't worry. It probably means that an NVME driver got installed and is being used now.  Since SATA is limited to 6Gbps and NVME is 32Gbps, you should be happy.  ;)  If you have tools/scripts that only know about sd*, then you'll need to modify those for the new disk types.  I see fd*, hd*, vd*, sd* and guess now nvme* will be happening.  Something similar has been part of the different network adapter drivers for decades.

That's my guess, but I don't really know.

Rather than describing what you've done, please run the commands and POST the output.  For storage, I'd like to see:

```
df -h
mount -a
ls -l  /dev/disk/by-uuid/
lsblk
sudo lshw -C storage
```

I can understand why **lshw** & **lsblk** don't see the new devices (if that is what is happening).  Those projects are run by others and they might know know to look for nvme* devices.  **df** and **mount** must know about those devices for them to work at all.

When you post the cmd + output, please, please, use code tags. This makes it readable here.  Adv Reply (#)

But I really don't know.

---

### Post by debdrex on 2017-11-18
Thanks for the link to the intel page - I hadn't come across that in my search. Running the commands on that site seems to suggest that my HDD has miraculously turned itself into a SSD drive! :P Sudo mount -a yielded no return at all but here are the rest:

```
$ df -hFilesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G   10M  1.6G   1% /run
/dev/nvme0n1p6  200G   11G  179G   6% /
tmpfs           7.8G   68M  7.8G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/nvme0n1p1  256M   78M  179M  31% /boot/efi
tmpfs           1.6G   72K  1.6G   1% /run/user/1000
 
```


```
$ ls -l /dev/disk/by-uuid/total 0
lrwxrwxrwx 1 root root 15 Nov 17 16:15 2C76-B3FD -> ../../nvme0n1p1
lrwxrwxrwx 1 root root 15 Nov 17 08:36 3ff6cf4b-d1ab-4304-b7d8-584c8ff03062 -> ../../nvme0n1p6
lrwxrwxrwx 1 root root 15 Nov 17 08:36 48EAEE1BEAEE0552 -> ../../nvme0n1p4
lrwxrwxrwx 1 root root 15 Nov 17 08:36 7eee4d21-f7f8-4165-9e70-ef12f9576129 -> ../../nvme0n1p7
lrwxrwxrwx 1 root root 15 Nov 17 08:36 900A9C070A9BE90C -> ../../nvme0n1p5
lrwxrwxrwx 1 root root 15 Nov 17 16:48 D6F01C94F01C7D45 -> ../../nvme0n1p3
 
```


```
$ lsblkNAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
nvme0n1     259:0    0   477G  0 disk 
&#9500;&#9472;nvme0n1p5 259:5    0  10.5G  0 part 
&#9500;&#9472;nvme0n1p3 259:3    0 246.2G  0 part 
&#9500;&#9472;nvme0n1p1 259:1    0   260M  0 part /boot/efi
&#9500;&#9472;nvme0n1p6 259:6    0 202.4G  0 part /
&#9500;&#9472;nvme0n1p4 259:4    0   1.8G  0 part 
&#9500;&#9472;nvme0n1p2 259:2    0    16M  0 part 
&#9492;&#9472;nvme0n1p7 259:7    0  15.9G  0 part [SWAP]


 
```

```
$ sudo lshw -C storage  *-storage               
       description: Non-Volatile memory controller
       product: Samsung Electronics Co Ltd
       vendor: Samsung Electronics Co Ltd
       physical id: 0
       bus info: pci@0000:6d:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: storage pm msi pciexpress msix nvm_express bus_master cap_list
       configuration: driver=nvme latency=0
       resources: irq:16 memory:dc000000-dc003fff


 
```

---

### Post by TheFu on 2017-11-18
I would be surprised if any "convertable" didn't come with an SSD these days, especially for a 200G-250G size.

I think this is a non-issue.

The driver used it nvme.
The mount points are from nvme devices.
You haven't said that anything isn't working, just some tools aren't showing what you expect.  Seems like inexperience here.

As for Windows being slow, I always find Windows slow, so cannot help with that.  There isn't usually any performance impacts on a dual-boot system just because drivers change between Linux and Windows.  Sometimes, with really, really, new drivers for network cards, Windows has been known to break the Linux drivers because the Windows drivers don't clear/initialize all the card registers at reboot.  I find it highly unlikely that any storage controller would be impacted by something like that.  Just an opinion.  I don't have any facts. Sorry.

---

### Post by debdrex on 2017-11-18
My convertible came with HDD. I had a choice and that's what I got. However, it looks as though it was installed with the NVME names and it's working fine so I'm going to accept your proclamation that it's a non-issue.

Windows was doing updates and isn't slow anymore so that was also a non-issue.

Thanks much for your help!

---

### Post by TheFu on 2017-11-18
I can't imagine any way that a SATA controller would be confused by the kernel as an NVMe controller.  They speak different protocols. I would doubt that you got a spinning HDD based on the driver used and working.

---

### Post by debdrex on 2017-11-18
You're right After I wrote so confidently about what I had I began to wonder...so I looked in Windows and on my sales slip for the computer and I do, indeed, have an SSD.

---

### Post by efflandt on 2017-11-18
NVMe is an M.2 SSD card that connects directly through the PCIe bus faster than M.2 or anything else through a SATA controller.

The only computer I have with Win10 is a low end HP laptop with Pentium N3700 upgraded from 4 to 8 GB RAM. The only comparison I have between Win10 and dual booting 64-bit Ubuntu 16.04 is that minecraft (a Java game) was unplayable 1-5 fps in Win10 and not fast, but at least playable at 16-18 fps in Ubuntu. And that was probably after Win10 had settled down from often using 100% disk access for many minutes after it boots checking for/installing updates and malicious software scanning. In one case a few days after leaving it on all night (without going into suspend), it spent 6 hours going from hogging 100% of my DSL Internet and at times most of cpu and disk, to after some hours, alternating between 40% of cpu and 100% disk. Then it needed to reboot several times to install (Creator's Update?), so Win10 was busy for about 8 hours total.

---

