---
title: "Stupidity"
date: 2008-07-11
forum: General Help
---

### Post by Shippou on 2008-07-11
Hello there...

I am using a dual-boot configuration with Windows. I somewhat experimented with my monitor resolution settings using Windows, and my monitor displayed "Frequency Over Range." Every time I log using Windows, this is the message that will appear.

Do you know how to fix this? By the way, the partition containing my Windows installation cannot be mounted by my Hardy Heron installation, even after rebooting.

Stupid indeed...

But then I need the help.

---

### Post by dracayr on 2008-07-11
reset the settings by booting into windows safe mode?(F8 on startup)

EDIT: Now that with the not mounting is strange. What do you get when you type 

sudo mount /dev/*partition*

into a terminal?

dracayr

---

### Post by Shippou on 2008-07-11
This is what I get after typing the command:

mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab

Plus this "annoying" message every time I type sudo: 

sudo: unable to resolve host shippou

here is my result when typing sudo fdisk -l :

sudo: unable to resolve host shippou
[sudo] password for shippou: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bcd67

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276        2491     9767520   83  Linux
/dev/sda3            9694        9729      289170   82  Linux swap / Solaris
/dev/sda4            2492        9693    57850065   83  Linux

Partition table entries are not in disk order

---

### Post by dracayr on 2008-07-11
well, do

```

sudo mkdir /mnt/windows
sudo mount /dev/sda1 /mnt/windows
```

and post what you get

dracayr

---

### Post by avtolle on 2008-07-11
Also, take a look at the /etc/hosts file and see what is in there ```
cat /etc/hosts
```

---

### Post by mriedel on 2008-07-11
> **dracayr said:**
> well, do

```

sudo mkdir /mnt/windows
sudo mount /dev/sda1 /mnt/windows
```

and post what you get

dracayr

After that you'll almost certainly get an error message telling you that your NTFS partition hasn't been unmounted cleanly (due to you shuttung down your PC when your monitor display the frequency error). To resolve that, type

```
sudo mount -t ntfs-3g -o force /dev/sda1 /mnt/windows
```

---

### Post by Shippou on 2008-07-11
shippou@shippou:~$ sudo mkdir /mnt/windows
sudo: unable to resolve host shippou
shippou@shippou:~$ sudo mount /dev/sda /mnt/windows
sudo: unable to resolve host shippou
mount: /dev/sda already mounted or /mnt/windows busy
shippou@shippou:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 shippou.MOLAVE

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
shippou@shippou:~$

---

### Post by Shippou on 2008-07-11
> 

```
sudo mount -t ntfs-3g -o force /dev/sda1 /mnt/windows
```

Already tried that before the other commands, but then it also returns an error.

---

### Post by dracayr on 2008-07-11
I understand shippou.MOLAVE is the name of your computer?

which error?

dracayr

---

### Post by Shippou on 2008-07-11
no.. shippou is the computer name, MOLAVE is the workgroup.

I tried again the command I quoted, and this is what I got: 

shippou@shippou:~$ sudo mount -t ntfs-3g -o force /dev/sda1 /mnt/windows
sudo: unable to resolve host shippou
[sudo] password for shippou: 
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
shippou@shippou:~$ 

But then I **cannot see the partition** here in nautilus.

---

### Post by dracayr on 2008-07-11
well that's normal. but there's no error message. that means you mounted it. you will most probably see your windows partition files when navigating to /mnt/windows/. Edit your /etc/fstab so that the line regarding the windows partition (if there is none, add one) looks like this:

```
/dev/sda1 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
```

but you can't solve your windows problem like this because windows stores all its configuration data in binary files :mad:. use the safe mode for that.


dracayr

---

### Post by Shippou on 2008-07-11
Thanks for the help. :) I'll try to dual-boot now, and post again afterwards. :)

---

### Post by Shippou on 2008-07-12
Hello again..

I have solved my problem by using "Last Known Good Configuration" option in Windows. 

But then I have a new problem. When I boot up my computer, it is okay. But then when I log-in, it seems to take hours just to see the panels. 

This problem just sufficed yesterday.

Here is my history (up to now) of what I did to my computer since last Friday: 

```

sudo su
nautilus
dolphin
exit
mount -t ntfs-3g /dev/sda1/media/disk -o force
sudo mount -t ntfs-3g /dev/sda1/media/disk -o force
sudo mount -t ntfs-3g /dev/sda1/media/disk -o force
sudo mount -t ntfs-3g /dev/sda1/media/ -o force
exit
sudo apt-get install build-essential
cd Desktop
gcc hello.c
sudo apt-get install build-essential
sudo apt-get install build-essentials
sudo apt-get install build-essential
sudo apt-get update
exit
ping google.com
exit
exit
sudo mount -t ntfs-3g -o force /dev/sda1 /mnt/windows
sudo mount -t ntfs-3g -o force /dev/sda1 /mnt/windows
sudo fdisk -l
sudo mkdir /mnt/windows
sudo mount /dev/sda /mnt/windows
cat /etc/hosts
sudo apt-get install build-essential
cd Desktop
gcc hello.c
./a.out
exit
/etc/fstab
sudo /etc/fstab
sudo su /etc/fstab
sudo gedit /etc/fstab
top
sudo fdisk -l
sudo mount /dev/sda1
sudo mount /dev/sda1
sudo fdisk -l
synaptic
sudo synaptic
sudo apt-get autoremove
top
knotes
fdisk -l
sudo fdisk -l
sudo gedit /etc/fstab
sudo apt-get remove ekiga
sudo apt-get remove evolution
sudo apt-get remove pidgin
top

```

And this is what appears when I run top, with Shift+M pressed:
```

top - 08:42:46 up 14 min,  3 users,  load average: 0.45, 0.30, 0.20
Tasks:  91 total,   2 running,  89 sleeping,   0 stopped,   0 zombie
Cpu(s):  7.7%us,  0.7%sy,  0.0%ni, 91.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2450992k total,   599288k used,  1851704k free,    13212k buffers
Swap:   289160k total,        0k used,   289160k free,   282560k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                         
 5423 shippou   20   0  473m  80m  23m S  0.7  3.4   0:25.90 firefox                                                         
 5201 shippou   20   0  351m  33m  13m S  0.0  1.4   0:01.40 nautilus                                                        
 5200 shippou   20   0  313m  30m  15m S  0.0  1.3   0:07.94 gnome-panel                                                     
 5451 shippou   20   0  262m  25m  11m S  0.0  1.1   0:00.68 gnome-terminal                                                  
 4980 root      20   0  226m  23m 8684 S  4.0  1.0   0:16.28 Xorg                                                            
 5172 shippou   20   0  263m  21m 9712 S  0.0  0.9   0:01.25 gnome-settings-                                                 
 5304 shippou   20   0  236m  17m  10m S  0.0  0.7   0:00.46 mixer_applet2                                                   
 5348 shippou   20   0  203m  16m 9904 S  0.0  0.7   0:00.34 update-notifier                                                 
 5362 shippou   20   0  189m  15m 7996 S  0.0  0.7   0:00.26 python                                                          
 5307 shippou   20   0  206m  15m 9836 S  0.0  0.7   0:00.40 fast-user-switc                                                 
 5291 shippou   20   0  195m  15m 9624 S  0.0  0.6   0:00.36 trashapplet                                                     
 5415 shippou   20   0  146m  15m 7800 S  0.0  0.6   0:00.52 notification-da                                                 
 5361 shippou   20   0  194m  14m 8840 S  0.0  0.6   0:00.70 nm-applet                                                       
 5198 shippou   20   0  130m  13m 8128 S  0.0  0.6   0:02.14 metacity                                                        
 5356 shippou   39  19 76996  10m 2380 S  0.0  0.4   0:00.06 trackerd                                                        
 5115 shippou   20   0  194m 9028 7244 S  0.0  0.4   0:00.16 x-session-manag                                                 
 5376 shippou   20   0  208m 8816 5636 S  0.0  0.4   0:00.12 gnome-power-man                                                 
 5167 shippou   20   0  209m 7940 5036 S  0.0  0.3   0:00.14 seahorse-agent                                                  
 5180 shippou   20   0  152m 6404 3628 S  0.0  0.3   0:00.30 pulseaudio                                                      
 5351 shippou   20   0  118m 6372 5140 S  0.0  0.3   0:00.04 tracker-applet                                                  
 5193 shippou   20   0  135m 6296 4576 S  0.0  0.3   0:01.46 gnome-screensav                                                 
 5111 shippou   20   0 43480 5572 2056 S  0.0  0.2   0:00.72 gconfd-2                                                        
 5363 shippou   20   0  182m 5316 3556 S  0.0  0.2   0:00.02 gnome-volume-ma                                                 
 4823 haldaemo  20   0 40152 4704 3752 S  0.0  0.2   0:00.44 hald                                                            
 5286 shippou   20   0 76160 3676 2668 S  0.0  0.1   0:00.16 bonobo-activati                                                 
 4976 root      20   0  125m 3348 2304 S  0.0  0.1   0:00.02 gdm                                                             
 4658 klog      20   0  6172 2928  432 S  0.0  0.1   0:00.12 klogd                                                           
 5294 shippou   20   0 63544 2876 2288 S  0.0  0.1   0:00.03 gvfsd-trash                                                     
 5183 shippou   20   0 57836 2688 2136 S  0.0  0.1   0:00.00 gconf-helper                                                    
 4826 root      20   0 41092 2528 1688 S  0.0  0.1   0:00.02 console-kit-dae                                                 
 5113 shippou   20   0 62044 2396 1844 S  0.0  0.1   0:00.00 gnome-keyring-d                                                 
 5331 shippou   20   0 44772 2356 1968 S  0.0  0.1   0:00.00 gvfsd-burn     

```

And also my rc.local file:

```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

```

Please help... I installed Linux in order to make things faster (even though I am not so fast enough, and I end up just wasting my time in front of my Linux box.:))

Here is also my System Log, if it can help:

```

Jul 12 14:17:17 shippou syslogd 1.5.0#1ubuntu1: restart.
Jul 12 14:19:18 shippou kernel: [  609.670907] r8169: eth0: link down
Jul 12 14:19:18 shippou kernel: [  609.673368] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 12 14:42:31 shippou kernel: [ 1580.810619] ACPI: PCI interrupt for device 0000:02:05.0 disabled
Jul 12 14:42:33 shippou kernel: [ 1582.815767] swsusp: Marking nosave pages: 000000000009f000 - 0000000000100000
Jul 12 14:42:33 shippou kernel: [ 1582.815774] swsusp: Basic memory bitmaps created
Jul 12 14:42:41 shippou kernel: [ 1582.815775] Syncing filesystems ... done.
Jul 12 14:42:41 shippou kernel: [ 1582.818774] Freezing user space processes ... (elapsed 0.00 seconds) done.
Jul 12 14:42:41 shippou kernel: [ 1582.819703] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Jul 12 14:42:41 shippou kernel: [ 1582.819734] Shrinking memory...  ^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^Hdone (475686 pages freed)
Jul 12 14:42:41 shippou kernel: [ 1589.367809] Freed 1902744 kbytes in 6.55 seconds (290.49 MB/s)
Jul 12 14:42:41 shippou kernel: [ 1589.367811] Suspending console(s)
Jul 12 14:42:41 shippou kernel: [ 1589.367889] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Jul 12 14:42:41 shippou kernel: [ 1589.368339] parport_pc 00:0a: disabled
Jul 12 14:42:41 shippou kernel: [ 1589.368520] serial 00:09: disabled
Jul 12 14:42:41 shippou kernel: [ 1589.383601] ACPI: PCI interrupt for device 0000:00:14.2 disabled
Jul 12 14:42:41 shippou kernel: [ 1589.399646] ACPI: PCI interrupt for device 0000:00:13.5 disabled
Jul 12 14:42:41 shippou kernel: [ 1589.415564] ACPI: PCI interrupt for device 0000:00:13.4 disabled
Jul 12 14:42:41 shippou kernel: [ 1589.415594] ACPI: PCI interrupt for device 0000:00:13.3 disabled
Jul 12 14:42:41 shippou kernel: [ 1589.415623] ACPI: PCI interrupt for device 0000:00:13.2 disabled
Jul 12 14:42:41 shippou kernel: [ 1589.415653] ACPI: PCI interrupt for device 0000:00:13.1 disabled
Jul 12 14:42:41 shippou kernel: [ 1589.415682] ACPI: PCI interrupt for device 0000:00:13.0 disabled
Jul 12 14:42:41 shippou kernel: [ 1589.479528] ACPI: PCI interrupt for device 0000:00:12.0 disabled
Jul 12 14:42:41 shippou kernel: [ 1589.480091] Disabling non-boot CPUs ...
Jul 12 14:42:41 shippou kernel: [ 1589.480314] swsusp: critical section: 
Jul 12 14:42:41 shippou kernel: [ 1589.614558] swsusp: Need to copy 126208 pages
Jul 12 14:42:41 shippou kernel: [ 1590.295626] swsusp: critical section: done (126208 pages copied)
Jul 12 14:42:41 shippou kernel: [ 1590.297875] ACPI: Unable to turn cooling device [ffff810093bfb080] 'off'
Jul 12 14:42:41 shippou kernel: [ 1590.297952] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 14:42:41 shippou kernel: [ 1590.298038] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 14:42:41 shippou kernel: [ 1590.319447] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 17
Jul 12 14:42:41 shippou kernel: [ 1590.343397] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 18
Jul 12 14:42:41 shippou kernel: [ 1590.367355] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 17
Jul 12 14:42:41 shippou kernel: [ 1590.391315] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 18
Jul 12 14:42:41 shippou kernel: [ 1590.431244] PCI: Enabling device 0000:00:13.5 (0000 -> 0002)
Jul 12 14:42:41 shippou kernel: [ 1590.431247] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 19
Jul 12 14:42:41 shippou kernel: [ 1590.431347] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 14:42:41 shippou kernel: [ 1590.447262] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 14:42:41 shippou kernel: [ 1590.448127] serial 00:09: activated
Jul 12 14:42:41 shippou kernel: [ 1590.448847] parport_pc 00:0a: activated
Jul 12 14:42:41 shippou kernel: [ 1590.606956] ata2: SATA link down (SStatus 0 SControl 300)
Jul 12 14:42:41 shippou kernel: [ 1590.606976] ata3: SATA link down (SStatus 0 SControl 300)
Jul 12 14:42:41 shippou kernel: [ 1590.606994] ata4: SATA link down (SStatus 0 SControl 300)
Jul 12 14:42:41 shippou kernel: [ 1590.770666] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 12 14:42:41 shippou kernel: [ 1591.027104] ata1.00: configured for UDMA/133
Jul 12 14:42:41 shippou kernel: [ 1591.042213] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jul 12 14:42:41 shippou kernel: [ 1591.042225] sd 0:0:0:0: [sda] Write Protect is off
Jul 12 14:42:41 shippou kernel: [ 1591.042242] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 12 14:42:41 shippou kernel: [ 1591.145982] sd 0:0:0:0: [sda] Starting disk
Jul 12 14:42:41 shippou kernel: [ 1591.169090] hdb: UDMA/66 mode selected
Jul 12 14:42:41 shippou kernel: [ 1591.239804] Restarting tasks ... done.
Jul 12 14:42:41 shippou kernel: [ 1591.245487] swsusp: Basic memory bitmaps freed
Jul 12 14:42:42 shippou kernel: [ 1591.434374] r8169 Gigabit Ethernet driver 2.2LK loaded
Jul 12 14:42:42 shippou kernel: [ 1591.434687] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 22 (level, low) -> IRQ 22
Jul 12 14:42:42 shippou kernel: [ 1591.435569] eth0: RTL8169sc/8110sc at 0xffffc20001044000, 00:19:21:21:21:b5, XID 18000000 IRQ 22
Jul 12 14:42:42 shippou kernel: [ 1591.496048] r8169: eth0: link down
Jul 12 14:42:42 shippou kernel: [ 1591.498531] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 12 14:42:44 shippou gnome-power-manager: (shippou) Resuming computer
Jul 12 14:43:12 shippou kernel: [ 1610.730668] gvfs-fuse-daemo[5896] general protection rip:7fa56766b423 rsp:7fff712959a0 error:0
Jul 12 14:43:15 shippou kernel: [ 1613.417425] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jul 12 14:43:17 shippou exiting on signal 15
Jul 12 14:59:58 shippou syslogd 1.5.0#1ubuntu1: restart.
Jul 12 14:59:58 shippou kernel: Inspecting /boot/System.map-2.6.24-19-generic
Jul 12 14:59:58 shippou kernel: Loaded 28491 symbols from /boot/System.map-2.6.24-19-generic.
Jul 12 14:59:58 shippou kernel: Symbols match kernel version 2.6.24.
Jul 12 14:59:58 shippou kernel: Loaded 16834 symbols from 77 modules.
Jul 12 14:59:58 shippou kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 12 14:59:58 shippou kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 12 14:59:58 shippou kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:15:37 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
Jul 12 14:59:58 shippou kernel: [    0.000000] Command line: root=UUID=2e985bef-5550-421f-b1bf-e1f730273cbc ro quiet splash
Jul 12 14:59:58 shippou kernel: [    0.000000] BIOS-provided physical RAM map:
Jul 12 14:59:58 shippou kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jul 12 14:59:58 shippou kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jul 12 14:59:58 shippou kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jul 12 14:59:58 shippou kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000097fe0000 (usable)
Jul 12 14:59:58 shippou kernel: [    0.000000]  BIOS-e820: 0000000097fe0000 - 0000000097fe3000 (ACPI NVS)
Jul 12 14:59:58 shippou kernel: [    0.000000]  BIOS-e820: 0000000097fe3000 - 0000000097ff0000 (ACPI data)
Jul 12 14:59:58 shippou kernel: [    0.000000]  BIOS-e820: 0000000097ff0000 - 0000000098000000 (reserved)
Jul 12 14:59:58 shippou kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Jul 12 14:59:58 shippou kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Jul 12 14:59:58 shippou kernel: [    0.000000] end_pfn_map = 1048576
Jul 12 14:59:58 shippou kernel: [    0.000000] DMI 2.5 present.
Jul 12 14:59:58 shippou kernel: [    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F7B80 checksum 0
Jul 12 14:59:58 shippou kernel: [    0.000000] ACPI: RSDP 000F7B80, 0024 (r2 RS690 )
Jul 12 14:59:58 shippou kernel: [    0.000000] ACPI: RSDT 97FE3040, 0038 (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 12 14:59:58 shippou kernel: [    0.000000] ACPI: FACP 97FE30C0, 0074 (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 12 14:59:58 shippou kernel: [    0.000000] ACPI: DSDT 97FE3180, 4B0B (r1 RS690  AWRDACPI     1000 MSFT  3000000)
Jul 12 14:59:58 shippou kernel: [    0.000000] ACPI: FACS 97FE0000, 0040
Jul 12 14:59:58 shippou kernel: [    0.000000] ACPI: SSDT 97FE7DC0, 00D3 (r1 PTLTD  POWERNOW        1  LTP        1)
Jul 12 14:59:58 shippou kernel: [    0.000000] ACPI: HPET 97FE7F00, 0038 (r1 RS690  AWRDACPI 42302E31 AWRD       98)
Jul 12 14:59:58 shippou kernel: [    0.000000] ACPI: MCFG 97FE7F80, 003C (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 12 14:59:58 shippou kernel: [    0.000000] ACPI: APIC 97FE7D00, 0068 (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 12 14:59:58 shippou kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Jul 12 14:59:58 shippou kernel: [    0.000000] CPU has 1 num_cores
Jul 12 14:59:58 shippou kernel: [    0.000000] No NUMA configuration found
Jul 12 14:59:58 shippou kernel: [    0.000000] Faking a node at 0000000000000000-0000000097fe0000
Jul 12 14:59:58 shippou kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000097fe0000
Jul 12 14:59:58 shippou kernel: [    0.000000] Zone PFN ranges:
Jul 12 14:59:58 shippou kernel: [    0.000000]   DMA             0 ->     4096
Jul 12 14:59:58 shippou kernel: [    0.000000]   DMA32        4096 ->  1048576
Jul 12 14:59:58 shippou kernel: [    0.000000]   Normal    1048576 ->  1048576
Jul 12 14:59:58 shippou kernel: [    0.000000] Movable zone start PFN for each node
Jul 12 14:59:58 shippou kernel: [    0.000000] early_node_map[2] active PFN ranges
Jul 12 14:59:58 shippou kernel: [    0.000000]     0:        0 ->      159
Jul 12 14:59:58 shippou kernel: [    0.000000]     0:      256 ->   622560
Jul 12 14:59:58 shippou kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Jul 12 14:59:58 shippou kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Jul 12 14:59:58 shippou kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul 12 14:59:58 shippou kernel: [    0.000000] Processor #0 (Bootup-CPU)
Jul 12 14:59:58 shippou kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Jul 12 14:59:58 shippou kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul 12 14:59:58 shippou kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jul 12 14:59:58 shippou kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jul 12 14:59:58 shippou kernel: [    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
Jul 12 14:59:58 shippou kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 12 14:59:58 shippou kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jul 12 14:59:58 shippou kernel: [    0.000000] Setting APIC routing to flat
Jul 12 14:59:58 shippou kernel: [    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
Jul 12 14:59:58 shippou kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 12 14:59:58 shippou kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Jul 12 14:59:58 shippou kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Jul 12 14:59:58 shippou kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Jul 12 14:59:58 shippou kernel: [    0.000000] Allocating PCI resources starting at a0000000 (gap: 98000000:48000000)
Jul 12 14:59:58 shippou kernel: [    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
Jul 12 14:59:58 shippou kernel: [    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
Jul 12 14:59:58 shippou kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 612716
Jul 12 14:59:58 shippou kernel: [    0.000000] Policy zone: DMA32
Jul 12 14:59:58 shippou kernel: [    0.000000] Kernel command line: root=UUID=2e985bef-5550-421f-b1bf-e1f730273cbc ro quiet splash
Jul 12 14:59:58 shippou kernel: [    0.000000] Initializing CPU#0
Jul 12 14:59:58 shippou kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Jul 12 14:59:58 shippou kernel: [    0.000000] TSC calibrated against HPET
Jul 12 14:59:58 shippou kernel: [   10.076607] time.c: Detected 1799.796 MHz processor.
Jul 12 14:59:58 shippou kernel: [   10.077307] Console: colour VGA+ 80x25
Jul 12 14:59:58 shippou kernel: [   10.077311] console [tty0] enabled
Jul 12 14:59:58 shippou kernel: [   10.077328] Checking aperture...
Jul 12 14:59:58 shippou kernel: [   10.077331] CPU 0: aperture @ edc0000000 size 32 MB
Jul 12 14:59:58 shippou kernel: [   10.077333] Aperture too small (32 MB)
Jul 12 14:59:58 shippou kernel: [   10.087310] No AGP bridge found
Jul 12 14:59:58 shippou kernel: [   10.120691] Memory: 2442456k/2490240k available (2489k kernel code, 47396k reserved, 1318k data, 320k init)
Jul 12 14:59:58 shippou kernel: [   10.120729] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Jul 12 14:59:58 shippou kernel: [   10.198610] Calibrating delay using timer specific routine.. 3709.23 BogoMIPS (lpj=7418460)
Jul 12 14:59:58 shippou kernel: [   10.198657] Security Framework initialized
Jul 12 14:59:58 shippou kernel: [   10.198663] SELinux:  Disabled at boot.
Jul 12 14:59:58 shippou kernel: [   10.198676] AppArmor: AppArmor initialized
Jul 12 14:59:58 shippou kernel: [   10.198680] Failure registering capabilities with primary security module.
Jul 12 14:59:58 shippou kernel: [   10.199059] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jul 12 14:59:58 shippou kernel: [   10.203080] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jul 12 14:59:58 shippou kernel: [   10.204695] Mount-cache hash table entries: 256
Jul 12 14:59:58 shippou kernel: [   10.204843] Initializing cgroup subsys ns
Jul 12 14:59:58 shippou kernel: [   10.204847] Initializing cgroup subsys cpuacct
Jul 12 14:59:58 shippou kernel: [   10.204863] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jul 12 14:59:58 shippou kernel: [   10.204865] CPU: L2 Cache: 512K (64 bytes/line)
Jul 12 14:59:58 shippou kernel: [   10.204867] CPU 0/0 -> Node 0
Jul 12 14:59:58 shippou kernel: [   10.204895] SMP alternatives: switching to UP code
Jul 12 14:59:58 shippou kernel: [   10.205567] Early unpacking initramfs... done
Jul 12 14:59:58 shippou kernel: [   10.606464] ACPI: Core revision 20070126
Jul 12 14:59:58 shippou kernel: [   10.606525] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Jul 12 14:59:58 shippou kernel: [   10.656027] Using local APIC timer interrupts.
Jul 12 14:59:58 shippou kernel: [   10.711504] Detected 12.498 MHz APIC timer.
Jul 12 14:59:58 shippou kernel: [   10.711553] Brought up 1 CPUs
Jul 12 14:59:58 shippou kernel: [   10.711826] net_namespace: 120 bytes
Jul 12 14:59:58 shippou kernel: [   10.712229] Time: 14:59:10  Date: 07/12/08
Jul 12 14:59:58 shippou kernel: [   10.712257] NET: Registered protocol family 16
Jul 12 14:59:58 shippou kernel: [   10.712429] ACPI: bus type pci registered
Jul 12 14:59:58 shippou kernel: [   10.712497] PCI: Using configuration type 1
Jul 12 14:59:58 shippou kernel: [   10.719194] ACPI: Interpreter enabled
Jul 12 14:59:58 shippou kernel: [   10.719200] ACPI: (supports S0 S3 S4 S5)
Jul 12 14:59:58 shippou kernel: [   10.719216] ACPI: Using IOAPIC for interrupt routing
Jul 12 14:59:58 shippou kernel: [   10.724410] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul 12 14:59:58 shippou kernel: [   10.724574] pci 0000:00:12.0: set SATA to AHCI mode
Jul 12 14:59:58 shippou kernel: [   10.725377] PCI: Transparent bridge - 0000:00:14.4
Jul 12 14:59:58 shippou kernel: [   10.746130] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 14:59:58 shippou kernel: [   10.746236] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 14:59:58 shippou kernel: [   10.746339] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 14:59:58 shippou kernel: [   10.746443] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 14:59:58 shippou kernel: [   10.746546] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 14:59:58 shippou kernel: [   10.746649] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 14:59:58 shippou kernel: [   10.746751] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 14:59:58 shippou kernel: [   10.746854] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 14:59:58 shippou kernel: [   10.746969] Linux Plug and Play Support v0.97 (c) Adam Belay
Jul 12 14:59:58 shippou kernel: [   10.746997] pnp: PnP ACPI init
Jul 12 14:59:58 shippou kernel: [   10.747006] ACPI: bus type pnp registered
Jul 12 14:59:58 shippou kernel: [   10.750024] pnp: PnP ACPI: found 15 devices
Jul 12 14:59:58 shippou kernel: [   10.750027] ACPI: ACPI bus type pnp unregistered
Jul 12 14:59:58 shippou kernel: [   10.750258] PCI: Using ACPI for IRQ routing
Jul 12 14:59:58 shippou kernel: [   10.750261] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jul 12 14:59:58 shippou kernel: [   10.763461] NET: Registered protocol family 8
Jul 12 14:59:58 shippou kernel: [   10.763463] NET: Registered protocol family 20
Jul 12 14:59:58 shippou kernel: [   10.763543] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Jul 12 14:59:58 shippou kernel: [   10.763547] hpet0: 4 32-bit timers, 14318180 Hz
Jul 12 14:59:58 shippou kernel: [   10.764602] AppArmor: AppArmor Filesystem Enabled
Jul 12 14:59:58 shippou kernel: [   10.767419] Time: tsc clocksource has been installed.
Jul 12 14:59:58 shippou kernel: [   10.775401] system 00:01: ioport range 0x4100-0x411f has been reserved
Jul 12 14:59:58 shippou kernel: [   10.775404] system 00:01: ioport range 0x228-0x22f has been reserved
Jul 12 14:59:58 shippou kernel: [   10.775408] system 00:01: ioport range 0x40b-0x40b has been reserved
Jul 12 14:59:58 shippou kernel: [   10.775411] system 00:01: ioport range 0x4d6-0x4d6 has been reserved
Jul 12 14:59:58 shippou kernel: [   10.775414] system 00:01: ioport range 0xc00-0xc01 has been reserved
Jul 12 14:59:58 shippou kernel: [   10.775417] system 00:01: ioport range 0xc14-0xc14 has been reserved
Jul 12 14:59:58 shippou kernel: [   10.775420] system 00:01: ioport range 0xc50-0xc52 has been reserved
Jul 12 14:59:58 shippou kernel: [   10.775423] system 00:01: ioport range 0xc6c-0xc6d has been reserved
Jul 12 14:59:58 shippou kernel: [   10.775426] system 00:01: ioport range 0xc6f-0xc6f has been reserved
Jul 12 14:59:58 shippou kernel: [   10.775429] system 00:01: ioport range 0xcd0-0xcd1 has been reserved
Jul 12 14:59:58 shippou kernel: [   10.775432] system 00:01: ioport range 0xcd2-0xcd3 has been reserved
Jul 12 14:59:58 shippou kernel: [   10.775435] system 00:01: ioport range 0xcd4-0xcdf has been reserved
Jul 12 14:59:58 shippou kernel: [   10.775438] system 00:01: ioport range 0x4000-0x40fe has been reserved
Jul 12 14:59:58 shippou kernel: [   10.775441] system 00:01: ioport range 0x4210-0x4217 has been reserved
Jul 12 14:59:58 shippou kernel: [   10.775444] system 00:01: ioport range 0xb10-0xb1f has been reserved
Jul 12 14:59:58 shippou kernel: [   10.775454] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
Jul 12 14:59:58 shippou kernel: [   10.775457] system 00:07: ioport range 0x220-0x225 has been reserved
Jul 12 14:59:58 shippou kernel: [   10.775460] system 00:07: ioport range 0xb00-0xb0f has been reserved
Jul 12 14:59:58 shippou kernel: [   10.775469] system 00:0d: iomem range 0xe0000000-0xefffffff could not be reserved
Jul 12 14:59:58 shippou kernel: [   10.775475] system 00:0e: iomem range 0xf0000-0xfffff could not be reserved
Jul 12 14:59:58 shippou kernel: [   10.775479] system 00:0e: iomem range 0xfed00000-0xfed000ff has been reserved
Jul 12 14:59:58 shippou kernel: [   10.775482] system 00:0e: iomem range 0x97fe0000-0x97ffffff could not be reserved
Jul 12 14:59:58 shippou kernel: [   10.775486] system 00:0e: iomem range 0xffff0000-0xffffffff has been reserved
Jul 12 14:59:58 shippou kernel: [   10.775489] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
Jul 12 14:59:58 shippou kernel: [   10.775492] system 00:0e: iomem range 0x100000-0x97fdffff could not be reserved
Jul 12 14:59:58 shippou kernel: [   10.775496] system 00:0e: iomem range 0x98000000-0x9fffffff has been reserved
Jul 12 14:59:58 shippou kernel: [   10.775499] system 00:0e: iomem range 0xfec00000-0xfec00fff has been reserved
Jul 12 14:59:58 shippou kernel: [   10.775502] system 00:0e: iomem range 0xfee00000-0xfee00fff could not be reserved
Jul 12 14:59:58 shippou kernel: [   10.775506] system 00:0e: iomem range 0xfff80000-0xfffeffff has been reserved
Jul 12 14:59:58 shippou kernel: [   10.775861] PCI: Bridge: 0000:00:01.0
Jul 12 14:59:58 shippou kernel: [   10.775864]   IO window: e000-efff
Jul 12 14:59:58 shippou kernel: [   10.775867]   MEM window: fdd00000-fdefffff
Jul 12 14:59:58 shippou kernel: [   10.775869]   PREFETCH window: d8000000-dfffffff
Jul 12 14:59:58 shippou kernel: [   10.775874] PCI: Bridge: 0000:00:14.4
Jul 12 14:59:58 shippou kernel: [   10.775876]   IO window: d000-dfff
Jul 12 14:59:58 shippou kernel: [   10.775881]   MEM window: fdc00000-fdcfffff
Jul 12 14:59:58 shippou kernel: [   10.775885]   PREFETCH window: fdf00000-fdffffff
Jul 12 14:59:58 shippou kernel: [   10.775909] NET: Registered protocol family 2
Jul 12 14:59:58 shippou kernel: [   10.811462] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Jul 12 14:59:58 shippou kernel: [   10.813088] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Jul 12 14:59:58 shippou kernel: [   10.820366] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jul 12 14:59:58 shippou kernel: [   10.821246] TCP: Hash tables configured (established 524288 bind 65536)
Jul 12 14:59:58 shippou kernel: [   10.821250] TCP reno registered
Jul 12 14:59:58 shippou kernel: [   10.831437] checking if image is initramfs... it is
Jul 12 14:59:58 shippou kernel: [   11.536100] Freeing initrd memory: 8212k freed
Jul 12 14:59:58 shippou kernel: [   11.543233] audit: initializing netlink socket (disabled)
Jul 12 14:59:58 shippou kernel: [   11.543247] audit(1215874751.416:1): initialized
Jul 12 14:59:58 shippou kernel: [   11.545222] VFS: Disk quotas dquot_6.5.1
Jul 12 14:59:58 shippou kernel: [   11.545294] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jul 12 14:59:58 shippou kernel: [   11.545434] io scheduler noop registered
Jul 12 14:59:58 shippou kernel: [   11.545436] io scheduler anticipatory registered
Jul 12 14:59:58 shippou kernel: [   11.545438] io scheduler deadline registered
Jul 12 14:59:58 shippou kernel: [   11.545542] io scheduler cfq registered (default)
Jul 12 14:59:58 shippou kernel: [   11.714131] Real Time Clock Driver v1.12ac
Jul 12 14:59:58 shippou kernel: [   11.714353] Linux agpgart interface v0.102
Jul 12 14:59:58 shippou kernel: [   11.714355] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jul 12 14:59:58 shippou kernel: [   11.714506] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 12 14:59:58 shippou kernel: [   11.715096] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 12 14:59:58 shippou kernel: [   11.715795] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jul 12 14:59:58 shippou kernel: [   11.715863] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jul 12 14:59:58 shippou kernel: [   11.715950] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jul 12 14:59:58 shippou kernel: [   11.716282] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 12 14:59:58 shippou kernel: [   11.716287] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 12 14:59:58 shippou kernel: [   11.721975] mice: PS/2 mouse device common for all mice
Jul 12 14:59:58 shippou kernel: [   11.722010] cpuidle: using governor ladder
Jul 12 14:59:58 shippou kernel: [   11.722012] cpuidle: using governor menu
Jul 12 14:59:58 shippou kernel: [   11.722165] NET: Registered protocol family 1
Jul 12 14:59:58 shippou kernel: [   11.722261] registered taskstats version 1
Jul 12 14:59:58 shippou kernel: [   11.722381]   Magic number: 0:833:990
Jul 12 14:59:58 shippou kernel: [   11.722392]   hash matches device ttyd3
Jul 12 14:59:58 shippou kernel: [   11.722532] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
Jul 12 14:59:58 shippou kernel: [   11.722535] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 12 14:59:58 shippou kernel: [   11.722536] EDD information not available.
Jul 12 14:59:58 shippou kernel: [   11.722544] Freeing unused kernel memory: 320k freed
Jul 12 14:59:58 shippou kernel: [   11.749731] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jul 12 14:59:58 shippou kernel: [   12.919898] fuse init (API version 7.9)
Jul 12 14:59:58 shippou kernel: [   12.934194] ACPI: Fan [FAN] (on)
Jul 12 14:59:58 shippou kernel: [   12.940104] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Jul 12 14:59:58 shippou kernel: [   12.941447] ACPI: Thermal Zone [THRM] (40 C)
Jul 12 14:59:58 shippou kernel: [   13.489618] SCSI subsystem initialized
Jul 12 14:59:58 shippou kernel: [   13.558158] usbcore: registered new interface driver usbfs
Jul 12 14:59:58 shippou kernel: [   13.558181] usbcore: registered new interface driver hub
Jul 12 14:59:58 shippou kernel: [   13.566845] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 14:59:58 shippou kernel: [   13.566972] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
Jul 12 14:59:58 shippou kernel: [   13.566979] ahci 0000:00:12.0: controller can't do PMP, turning off CAP_PMP
Jul 12 14:59:58 shippou kernel: [   13.582606] usbcore: registered new device driver usb
Jul 12 14:59:58 shippou kernel: [   13.591259] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jul 12 14:59:58 shippou kernel: [   13.592243] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jul 12 14:59:58 shippou kernel: [   13.782327] Floppy drive(s): fd0 is 1.44M
Jul 12 14:59:58 shippou kernel: [   13.802192] FDC 0 is a post-1991 82077
Jul 12 14:59:58 shippou kernel: [   14.568859] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Jul 12 14:59:58 shippou kernel: [   14.568865] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pio slum part 
Jul 12 14:59:58 shippou kernel: [   14.570084] scsi0 : ahci
Jul 12 14:59:58 shippou kernel: [   14.570414] scsi1 : ahci
Jul 12 14:59:58 shippou kernel: [   14.570564] scsi2 : ahci
Jul 12 14:59:58 shippou kernel: [   14.570714] scsi3 : ahci
Jul 12 14:59:58 shippou kernel: [   14.570794] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 16
Jul 12 14:59:58 shippou kernel: [   14.570798] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 16
Jul 12 14:59:58 shippou kernel: [   14.570801] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 16
Jul 12 14:59:58 shippou kernel: [   14.570805] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 16
Jul 12 14:59:58 shippou kernel: [   15.044008] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 12 14:59:58 shippou kernel: [   15.092808] ata1.00: ATA-7: ST380215AS, 3.AAD, max UDMA/133
Jul 12 14:59:58 shippou kernel: [   15.092811] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32)
Jul 12 14:59:58 shippou kernel: [   15.151033] ata1.00: configured for UDMA/133
Jul 12 14:59:58 shippou kernel: [   15.459282] ata2: SATA link down (SStatus 0 SControl 300)
Jul 12 14:59:58 shippou kernel: [   15.770742] ata3: SATA link down (SStatus 0 SControl 300)
Jul 12 14:59:58 shippou kernel: [   16.082201] ata4: SATA link down (SStatus 0 SControl 300)
Jul 12 14:59:58 shippou kernel: [   16.082326] scsi 0:0:0:0: Direct-Access     ATA      ST380215AS       3.AA PQ: 0 ANSI: 5
Jul 12 14:59:58 shippou kernel: [   16.083773] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 14:59:58 shippou kernel: [   16.083889] ohci_hcd 0000:00:13.0: OHCI Host Controller
Jul 12 14:59:58 shippou kernel: [   16.084157] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Jul 12 14:59:58 shippou kernel: [   16.084177] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02e000
Jul 12 14:59:58 shippou kernel: [   16.091344] Driver 'sd' needs updating - please use bus_type methods
Jul 12 14:59:58 shippou kernel: [   16.098230] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jul 12 14:59:58 shippou kernel: [   16.098244] sd 0:0:0:0: [sda] Write Protect is off
Jul 12 14:59:58 shippou kernel: [   16.098261] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 12 14:59:58 shippou kernel: [   16.098314] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jul 12 14:59:58 shippou kernel: [   16.098322] sd 0:0:0:0: [sda] Write Protect is off
Jul 12 14:59:58 shippou kernel: [   16.098337] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 12 14:59:58 shippou kernel: [   16.098342]  sda: sda1 sda2 sda3 sda4
Jul 12 14:59:58 shippou kernel: [   16.142363] usb usb1: configuration #1 chosen from 1 choice
Jul 12 14:59:58 shippou kernel: [   16.142391] hub 1-0:1.0: USB hub found
Jul 12 14:59:58 shippou kernel: [   16.142400] hub 1-0:1.0: 2 ports detected
Jul 12 14:59:58 shippou kernel: [   16.150669] sd 0:0:0:0: [sda] Attached SCSI disk
Jul 12 14:59:58 shippou kernel: [   16.155975] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 12 14:59:58 shippou kernel: [   16.246020] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 17
Jul 12 14:59:58 shippou kernel: [   16.246154] ohci_hcd 0000:00:13.1: OHCI Host Controller
Jul 12 14:59:58 shippou kernel: [   16.246218] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Jul 12 14:59:58 shippou kernel: [   16.246244] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfe02d000
Jul 12 14:59:58 shippou kernel: [   16.306051] usb usb2: configuration #1 chosen from 1 choice
Jul 12 14:59:58 shippou kernel: [   16.306077] hub 2-0:1.0: USB hub found
Jul 12 14:59:58 shippou kernel: [   16.306086] hub 2-0:1.0: 2 ports detected
Jul 12 14:59:58 shippou kernel: [   16.409731] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 18
Jul 12 14:59:58 shippou kernel: [   16.409869] ohci_hcd 0000:00:13.2: OHCI Host Controller
Jul 12 14:59:58 shippou kernel: [   16.409930] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
Jul 12 14:59:58 shippou kernel: [   16.409954] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfe02c000
Jul 12 14:59:58 shippou kernel: [   16.470451] usb usb3: configuration #1 chosen from 1 choice
Jul 12 14:59:58 shippou kernel: [   16.470485] hub 3-0:1.0: USB hub found
Jul 12 14:59:58 shippou kernel: [   16.470495] hub 3-0:1.0: 2 ports detected
Jul 12 14:59:58 shippou kernel: [   16.573484] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 17
Jul 12 14:59:58 shippou kernel: [   16.573653] ohci_hcd 0000:00:13.3: OHCI Host Controller
Jul 12 14:59:58 shippou kernel: [   16.573720] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
Jul 12 14:59:58 shippou kernel: [   16.573740] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfe02b000
Jul 12 14:59:58 shippou kernel: [   16.633487] usb usb4: configuration #1 chosen from 1 choice
Jul 12 14:59:58 shippou kernel: [   16.633514] hub 4-0:1.0: USB hub found
Jul 12 14:59:58 shippou kernel: [   16.633523] hub 4-0:1.0: 2 ports detected
Jul 12 14:59:58 shippou kernel: [   16.635130] Attempting manual resume
Jul 12 14:59:58 shippou kernel: [   16.679607] kjournald starting.  Commit interval 5 seconds
Jul 12 14:59:58 shippou kernel: [   16.679618] EXT3-fs: mounted filesystem with ordered data mode.
Jul 12 14:59:58 shippou kernel: [   16.737154] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 18
Jul 12 14:59:58 shippou kernel: [   16.737282] ohci_hcd 0000:00:13.4: OHCI Host Controller
Jul 12 14:59:58 shippou kernel: [   16.737342] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
Jul 12 14:59:58 shippou kernel: [   16.737361] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfe02a000
Jul 12 14:59:58 shippou kernel: [   16.797204] usb usb5: configuration #1 chosen from 1 choice
Jul 12 14:59:58 shippou kernel: [   16.797230] hub 5-0:1.0: USB hub found
Jul 12 14:59:58 shippou kernel: [   16.797240] hub 5-0:1.0: 2 ports detected
Jul 12 14:59:58 shippou kernel: [   16.901048] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 19
Jul 12 14:59:58 shippou kernel: [   16.901183] ehci_hcd 0000:00:13.5: EHCI Host Controller
Jul 12 14:59:58 shippou kernel: [   16.901244] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
Jul 12 14:59:58 shippou kernel: [   16.901286] ehci_hcd 0000:00:13.5: debug port 1
Jul 12 14:59:58 shippou kernel: [   16.901304] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfe029000
Jul 12 14:59:58 shippou kernel: [   16.912763] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jul 12 14:59:58 shippou kernel: [   16.912880] usb usb6: configuration #1 chosen from 1 choice
Jul 12 14:59:58 shippou kernel: [   16.912902] hub 6-0:1.0: USB hub found
Jul 12 14:59:58 shippou kernel: [   16.912909] hub 6-0:1.0: 10 ports detected
Jul 12 14:59:58 shippou kernel: [   17.016823] SB600_PATA: IDE controller (0x1002:0x438c rev 0x00) at  PCI slot 0000:00:14.1
Jul 12 14:59:58 shippou kernel: [   17.016836] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 14:59:58 shippou kernel: [   17.016846] SB600_PATA: not 100% native mode: will probe irqs later
Jul 12 14:59:58 shippou kernel: [   17.016855]     ide0: BM-DMA at 0xf900-0xf907, BIOS settings: hda:pio, hdb:DMA
Jul 12 14:59:58 shippou kernel: [   17.803542] hdb: LITE-ON DVDRW LH-20A1P, ATAPI CD/DVD-ROM drive
Jul 12 14:59:58 shippou kernel: [   18.083062] hdb: UDMA/66 mode selected
Jul 12 14:59:58 shippou kernel: [   18.083435] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Jul 12 14:59:58 shippou kernel: [   18.096357] r8169 Gigabit Ethernet driver 2.2LK loaded
Jul 12 14:59:58 shippou kernel: [   18.096394] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 22 (level, low) -> IRQ 22
Jul 12 14:59:58 shippou kernel: [   18.096631] eth0: RTL8169sc/8110sc at 0xffffc20001044000, 00:19:21:21:21:b5, XID 18000000 IRQ 22
Jul 12 14:59:58 shippou kernel: [   23.774950] input: PC Speaker as /devices/platform/pcspkr/input/input2
Jul 12 14:59:58 shippou kernel: [   23.959906] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 12 14:59:58 shippou kernel: [   24.008534] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul 12 14:59:58 shippou kernel: [   24.064404] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Jul 12 14:59:58 shippou kernel: [   24.294232] input: Power Button (FF) as /devices/virtual/input/input3
Jul 12 14:59:58 shippou kernel: [   24.311965] ACPI: Power Button (FF) [PWRF]
Jul 12 14:59:58 shippou kernel: [   24.312030] input: Power Button (CM) as /devices/virtual/input/input4
Jul 12 14:59:58 shippou kernel: [   24.343901] ACPI: Power Button (CM) [PWRB]
Jul 12 14:59:58 shippou kernel: [   24.429755] input: ImExPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Jul 12 14:59:58 shippou kernel: [   24.458279] parport_pc 00:0a: reported by Plug and Play ACPI
Jul 12 14:59:58 shippou kernel: [   24.458337] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jul 12 14:59:58 shippou kernel: [   25.886405] r8169: eth0: link down
Jul 12 14:59:58 shippou kernel: [   25.989791] hdb: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
Jul 12 14:59:58 shippou kernel: [   25.989799] Uniform CD-ROM driver Revision: 3.20
Jul 12 14:59:58 shippou kernel: [   26.126427] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 14:59:58 shippou kernel: [   26.150624] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
Jul 12 14:59:58 shippou kernel: [   26.296635] NET: Registered protocol family 10
Jul 12 14:59:58 shippou kernel: [   26.296844] lo: Disabled Privacy Extensions
Jul 12 14:59:58 shippou kernel: [   26.297168] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 12 14:59:58 shippou kernel: [   29.101574] lp0: using parport0 (interrupt-driven).
Jul 12 14:59:58 shippou kernel: [   29.194158] Adding 289160k swap on /dev/sda3.  Priority:-1 extents:1 across:289160k
Jul 12 14:59:58 shippou kernel: [   56.189073] EXT3 FS on sda2, internal journal
Jul 12 14:59:58 shippou kernel: [   56.851778] kjournald starting.  Commit interval 5 seconds
Jul 12 14:59:58 shippou kernel: [   56.851985] EXT3 FS on sda4, internal journal
Jul 12 14:59:58 shippou kernel: [   56.851989] EXT3-fs: mounted filesystem with ordered data mode.
Jul 12 14:59:58 shippou kernel: [   57.171109] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul 12 14:59:58 shippou kernel: [   57.576905] No dock devices found.
Jul 12 14:59:58 shippou kernel: [   57.811633] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (1 cpu cores) (version 2.20.00)
Jul 12 14:59:58 shippou kernel: [   57.811672] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
Jul 12 14:59:58 shippou kernel: [   57.811675] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
Jul 12 14:59:58 shippou kernel: [   58.501334] ppdev: user-space parallel port driver
Jul 12 14:59:58 shippou kernel: [   58.577879] audit(1215845998.635:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4966 profile="/usr/sbin/cupsd" namespace="default"
Jul 12 14:59:58 shippou dhcdbd: Started up.
Jul 12 15:00:00 shippou kernel: [   60.541147] Marking TSC unstable due to cpufreq changes
Jul 12 15:00:00 shippou kernel: [   60.545399] Time: hpet clocksource has been installed.
Jul 12 15:00:01 shippou kernel: [   60.820287] Clocksource tsc unstable (delta = -223741170 ns)
Jul 12 15:00:03 shippou kernel: [   62.107961] Bluetooth: Core ver 2.11
Jul 12 15:00:03 shippou kernel: [   62.108519] NET: Registered protocol family 31
Jul 12 15:00:03 shippou kernel: [   62.108523] Bluetooth: HCI device and connection manager initialized
Jul 12 15:00:03 shippou kernel: [   62.108527] Bluetooth: HCI socket layer initialized
Jul 12 15:00:03 shippou kernel: [   62.140358] Bluetooth: L2CAP ver 2.9
Jul 12 15:00:03 shippou kernel: [   62.140363] Bluetooth: L2CAP socket layer initialized
Jul 12 15:00:03 shippou kernel: [   62.182381] Bluetooth: RFCOMM socket layer initialized
Jul 12 15:00:03 shippou kernel: [   62.182589] Bluetooth: RFCOMM TTY layer initialized
Jul 12 15:00:03 shippou kernel: [   62.182592] Bluetooth: RFCOMM ver 1.8
Jul 12 15:00:05 shippou kernel: [   63.260685] [drm] Initialized drm 1.1.0 20060810
Jul 12 15:00:11 shippou kernel: [   66.533015] hda-intel: Invalid position buffer, using LPIB read method instead.
Jul 12 15:00:36 shippou kernel: [   83.045647] UDF-fs: No VRS found
Jul 12 15:05:45 shippou kernel: [  263.666145] gvfs-fuse-daemo[5589] general protection rip:7fa5b617f423 rsp:7fffbfdaa1d0 error:0
Jul 12 15:05:48 shippou kernel: [  267.032658] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jul 12 15:05:49 shippou exiting on signal 15
Jul 12 15:06:37 shippou syslogd 1.5.0#1ubuntu1: restart.
Jul 12 15:06:37 shippou kernel: Inspecting /boot/System.map-2.6.24-19-generic
Jul 12 15:06:38 shippou kernel: Loaded 28491 symbols from /boot/System.map-2.6.24-19-generic.
Jul 12 15:06:38 shippou kernel: Symbols match kernel version 2.6.24.
Jul 12 15:06:38 shippou kernel: Loaded 16834 symbols from 77 modules.
Jul 12 15:06:38 shippou kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 12 15:06:38 shippou kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 12 15:06:38 shippou kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:15:37 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
Jul 12 15:06:38 shippou kernel: [    0.000000] Command line: root=UUID=2e985bef-5550-421f-b1bf-e1f730273cbc ro quiet splash
Jul 12 15:06:38 shippou kernel: [    0.000000] BIOS-provided physical RAM map:
Jul 12 15:06:38 shippou kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jul 12 15:06:38 shippou kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jul 12 15:06:38 shippou kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jul 12 15:06:38 shippou kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000097fe0000 (usable)
Jul 12 15:06:38 shippou kernel: [    0.000000]  BIOS-e820: 0000000097fe0000 - 0000000097fe3000 (ACPI NVS)
Jul 12 15:06:38 shippou kernel: [    0.000000]  BIOS-e820: 0000000097fe3000 - 0000000097ff0000 (ACPI data)
Jul 12 15:06:38 shippou kernel: [    0.000000]  BIOS-e820: 0000000097ff0000 - 0000000098000000 (reserved)
Jul 12 15:06:38 shippou kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Jul 12 15:06:38 shippou kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Jul 12 15:06:38 shippou kernel: [    0.000000] end_pfn_map = 1048576
Jul 12 15:06:38 shippou kernel: [    0.000000] DMI 2.5 present.
Jul 12 15:06:38 shippou kernel: [    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F7B80 checksum 0
Jul 12 15:06:38 shippou kernel: [    0.000000] ACPI: RSDP 000F7B80, 0024 (r2 RS690 )
Jul 12 15:06:38 shippou kernel: [    0.000000] ACPI: RSDT 97FE3040, 0038 (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 12 15:06:38 shippou kernel: [    0.000000] ACPI: FACP 97FE30C0, 0074 (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 12 15:06:38 shippou kernel: [    0.000000] ACPI: DSDT 97FE3180, 4B0B (r1 RS690  AWRDACPI     1000 MSFT  3000000)
Jul 12 15:06:38 shippou kernel: [    0.000000] ACPI: FACS 97FE0000, 0040
Jul 12 15:06:38 shippou kernel: [    0.000000] ACPI: SSDT 97FE7DC0, 00D3 (r1 PTLTD  POWERNOW        1  LTP        1)
Jul 12 15:06:38 shippou kernel: [    0.000000] ACPI: HPET 97FE7F00, 0038 (r1 RS690  AWRDACPI 42302E31 AWRD       98)
Jul 12 15:06:38 shippou kernel: [    0.000000] ACPI: MCFG 97FE7F80, 003C (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 12 15:06:38 shippou kernel: [    0.000000] ACPI: APIC 97FE7D00, 0068 (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 12 15:06:38 shippou kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Jul 12 15:06:38 shippou kernel: [    0.000000] CPU has 1 num_cores
Jul 12 15:06:38 shippou kernel: [    0.000000] No NUMA configuration found
Jul 12 15:06:38 shippou kernel: [    0.000000] Faking a node at 0000000000000000-0000000097fe0000
Jul 12 15:06:38 shippou kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000097fe0000
Jul 12 15:06:38 shippou kernel: [    0.000000] Zone PFN ranges:
Jul 12 15:06:38 shippou kernel: [    0.000000]   DMA             0 ->     4096
Jul 12 15:06:38 shippou kernel: [    0.000000]   DMA32        4096 ->  1048576
Jul 12 15:06:38 shippou kernel: [    0.000000]   Normal    1048576 ->  1048576
Jul 12 15:06:38 shippou kernel: [    0.000000] Movable zone start PFN for each node
Jul 12 15:06:38 shippou kernel: [    0.000000] early_node_map[2] active PFN ranges
Jul 12 15:06:38 shippou kernel: [    0.000000]     0:        0 ->      159
Jul 12 15:06:38 shippou kernel: [    0.000000]     0:      256 ->   622560
Jul 12 15:06:38 shippou kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Jul 12 15:06:38 shippou kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Jul 12 15:06:38 shippou kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul 12 15:06:38 shippou kernel: [    0.000000] Processor #0 (Bootup-CPU)
Jul 12 15:06:38 shippou kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Jul 12 15:06:38 shippou kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul 12 15:06:38 shippou kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jul 12 15:06:38 shippou kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jul 12 15:06:38 shippou kernel: [    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
Jul 12 15:06:38 shippou kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 12 15:06:38 shippou kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jul 12 15:06:38 shippou kernel: [    0.000000] Setting APIC routing to flat
Jul 12 15:06:38 shippou kernel: [    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
Jul 12 15:06:38 shippou kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 12 15:06:38 shippou kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Jul 12 15:06:38 shippou kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Jul 12 15:06:38 shippou kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Jul 12 15:06:38 shippou kernel: [    0.000000] Allocating PCI resources starting at a0000000 (gap: 98000000:48000000)
Jul 12 15:06:38 shippou kernel: [    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
Jul 12 15:06:38 shippou kernel: [    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
Jul 12 15:06:38 shippou kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 612716
Jul 12 15:06:38 shippou kernel: [    0.000000] Policy zone: DMA32
Jul 12 15:06:38 shippou kernel: [    0.000000] Kernel command line: root=UUID=2e985bef-5550-421f-b1bf-e1f730273cbc ro quiet splash
Jul 12 15:06:38 shippou kernel: [    0.000000] Initializing CPU#0
Jul 12 15:06:38 shippou kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Jul 12 15:06:38 shippou kernel: [    0.000000] TSC calibrated against HPET
Jul 12 15:06:38 shippou kernel: [   19.331350] time.c: Detected 1799.788 MHz processor.
Jul 12 15:06:38 shippou kernel: [   19.332048] Console: colour VGA+ 80x25
Jul 12 15:06:38 shippou kernel: [   19.332051] console [tty0] enabled
Jul 12 15:06:38 shippou kernel: [   19.332068] Checking aperture...
Jul 12 15:06:38 shippou kernel: [   19.332070] CPU 0: aperture @ edc0000000 size 32 MB
Jul 12 15:06:38 shippou kernel: [   19.332072] Aperture too small (32 MB)
Jul 12 15:06:38 shippou kernel: [   19.341885] No AGP bridge found
Jul 12 15:06:38 shippou kernel: [   19.374621] Memory: 2442456k/2490240k available (2489k kernel code, 47396k reserved, 1318k data, 320k init)
Jul 12 15:06:38 shippou kernel: [   19.374661] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Jul 12 15:06:38 shippou kernel: [   19.453358] Calibrating delay using timer specific routine.. 3709.05 BogoMIPS (lpj=7418113)
Jul 12 15:06:38 shippou kernel: [   19.453404] Security Framework initialized
Jul 12 15:06:38 shippou kernel: [   19.453410] SELinux:  Disabled at boot.
Jul 12 15:06:38 shippou kernel: [   19.453423] AppArmor: AppArmor initialized
Jul 12 15:06:38 shippou kernel: [   19.453426] Failure registering capabilities with primary security module.
Jul 12 15:06:38 shippou kernel: [   19.453805] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jul 12 15:06:38 shippou kernel: [   19.457828] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jul 12 15:06:38 shippou kernel: [   19.459452] Mount-cache hash table entries: 256
Jul 12 15:06:38 shippou kernel: [   19.459602] Initializing cgroup subsys ns
Jul 12 15:06:38 shippou kernel: [   19.459606] Initializing cgroup subsys cpuacct
Jul 12 15:06:38 shippou kernel: [   19.459623] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jul 12 15:06:38 shippou kernel: [   19.459625] CPU: L2 Cache: 512K (64 bytes/line)
Jul 12 15:06:38 shippou kernel: [   19.459627] CPU 0/0 -> Node 0
Jul 12 15:06:38 shippou kernel: [   19.459655] SMP alternatives: switching to UP code
Jul 12 15:06:38 shippou kernel: [   19.460343] Early unpacking initramfs... done
Jul 12 15:06:38 shippou kernel: [   19.861100] ACPI: Core revision 20070126
Jul 12 15:06:38 shippou kernel: [   19.861162] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Jul 12 15:06:38 shippou kernel: [   19.910631] Using local APIC timer interrupts.
Jul 12 15:06:38 shippou kernel: [   19.966109] Detected 12.498 MHz APIC timer.
Jul 12 15:06:38 shippou kernel: [   19.966159] Brought up 1 CPUs
Jul 12 15:06:38 shippou kernel: [   19.966432] net_namespace: 120 bytes
Jul 12 15:06:38 shippou kernel: [   19.966834] Time: 15:06:18  Date: 07/12/08
Jul 12 15:06:38 shippou kernel: [   19.966863] NET: Registered protocol family 16
Jul 12 15:06:38 shippou kernel: [   19.967035] ACPI: bus type pci registered
Jul 12 15:06:38 shippou kernel: [   19.967103] PCI: Using configuration type 1
Jul 12 15:06:38 shippou kernel: [   19.973810] ACPI: Interpreter enabled
Jul 12 15:06:38 shippou kernel: [   19.973816] ACPI: (supports S0 S3 S4 S5)
Jul 12 15:06:38 shippou kernel: [   19.973832] ACPI: Using IOAPIC for interrupt routing
Jul 12 15:06:38 shippou kernel: [   19.979019] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul 12 15:06:38 shippou kernel: [   19.979181] pci 0000:00:12.0: set SATA to AHCI mode
Jul 12 15:06:38 shippou kernel: [   19.979978] PCI: Transparent bridge - 0000:00:14.4
Jul 12 15:06:38 shippou kernel: [   20.000735] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 15:06:38 shippou kernel: [   20.000841] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 15:06:38 shippou kernel: [   20.000944] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 15:06:38 shippou kernel: [   20.001048] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 15:06:38 shippou kernel: [   20.001151] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 15:06:38 shippou kernel: [   20.001254] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 15:06:38 shippou kernel: [   20.001357] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 15:06:38 shippou kernel: [   20.001460] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 15:06:38 shippou kernel: [   20.001576] Linux Plug and Play Support v0.97 (c) Adam Belay
Jul 12 15:06:38 shippou kernel: [   20.001604] pnp: PnP ACPI init
Jul 12 15:06:38 shippou kernel: [   20.001613] ACPI: bus type pnp registered
Jul 12 15:06:38 shippou kernel: [   20.004632] pnp: PnP ACPI: found 15 devices
Jul 12 15:06:38 shippou kernel: [   20.004635] ACPI: ACPI bus type pnp unregistered
Jul 12 15:06:38 shippou kernel: [   20.004864] PCI: Using ACPI for IRQ routing
Jul 12 15:06:38 shippou kernel: [   20.004867] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jul 12 15:06:38 shippou kernel: [   20.018065] NET: Registered protocol family 8
Jul 12 15:06:38 shippou kernel: [   20.018067] NET: Registered protocol family 20
Jul 12 15:06:38 shippou kernel: [   20.018147] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Jul 12 15:06:38 shippou kernel: [   20.018152] hpet0: 4 32-bit timers, 14318180 Hz
Jul 12 15:06:38 shippou kernel: [   20.019205] AppArmor: AppArmor Filesystem Enabled
Jul 12 15:06:38 shippou kernel: [   20.022024] Time: tsc clocksource has been installed.
Jul 12 15:06:38 shippou kernel: [   20.030005] system 00:01: ioport range 0x4100-0x411f has been reserved
Jul 12 15:06:38 shippou kernel: [   20.030009] system 00:01: ioport range 0x228-0x22f has been reserved
Jul 12 15:06:38 shippou kernel: [   20.030012] system 00:01: ioport range 0x40b-0x40b has been reserved
Jul 12 15:06:38 shippou kernel: [   20.030015] system 00:01: ioport range 0x4d6-0x4d6 has been reserved
Jul 12 15:06:38 shippou kernel: [   20.030018] system 00:01: ioport range 0xc00-0xc01 has been reserved
Jul 12 15:06:38 shippou kernel: [   20.030021] system 00:01: ioport range 0xc14-0xc14 has been reserved
Jul 12 15:06:38 shippou kernel: [   20.030024] system 00:01: ioport range 0xc50-0xc52 has been reserved
Jul 12 15:06:38 shippou kernel: [   20.030027] system 00:01: ioport range 0xc6c-0xc6d has been reserved
Jul 12 15:06:38 shippou kernel: [   20.030030] system 00:01: ioport range 0xc6f-0xc6f has been reserved
Jul 12 15:06:38 shippou kernel: [   20.030033] system 00:01: ioport range 0xcd0-0xcd1 has been reserved
Jul 12 15:06:38 shippou kernel: [   20.030036] system 00:01: ioport range 0xcd2-0xcd3 has been reserved
Jul 12 15:06:38 shippou kernel: [   20.030039] system 00:01: ioport range 0xcd4-0xcdf has been reserved
Jul 12 15:06:38 shippou kernel: [   20.030042] system 00:01: ioport range 0x4000-0x40fe has been reserved
Jul 12 15:06:38 shippou kernel: [   20.030045] system 00:01: ioport range 0x4210-0x4217 has been reserved
Jul 12 15:06:38 shippou kernel: [   20.030048] system 00:01: ioport range 0xb10-0xb1f has been reserved
Jul 12 15:06:38 shippou kernel: [   20.030058] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
Jul 12 15:06:38 shippou kernel: [   20.030061] system 00:07: ioport range 0x220-0x225 has been reserved
Jul 12 15:06:38 shippou kernel: [   20.030064] system 00:07: ioport range 0xb00-0xb0f has been reserved
Jul 12 15:06:38 shippou kernel: [   20.030073] system 00:0d: iomem range 0xe0000000-0xefffffff could not be reserved
Jul 12 15:06:38 shippou kernel: [   20.030079] system 00:0e: iomem range 0xf0000-0xfffff could not be reserved
Jul 12 15:06:38 shippou kernel: [   20.030083] system 00:0e: iomem range 0xfed00000-0xfed000ff has been reserved
Jul 12 15:06:38 shippou kernel: [   20.030086] system 00:0e: iomem range 0x97fe0000-0x97ffffff could not be reserved
Jul 12 15:06:38 shippou kernel: [   20.030090] system 00:0e: iomem range 0xffff0000-0xffffffff has been reserved
Jul 12 15:06:38 shippou kernel: [   20.030093] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
Jul 12 15:06:38 shippou kernel: [   20.030096] system 00:0e: iomem range 0x100000-0x97fdffff could not be reserved
Jul 12 15:06:38 shippou kernel: [   20.030100] system 00:0e: iomem range 0x98000000-0x9fffffff has been reserved
Jul 12 15:06:38 shippou kernel: [   20.030103] system 00:0e: iomem range 0xfec00000-0xfec00fff has been reserved
Jul 12 15:06:38 shippou kernel: [   20.030106] system 00:0e: iomem range 0xfee00000-0xfee00fff could not be reserved
Jul 12 15:06:38 shippou kernel: [   20.030110] system 00:0e: iomem range 0xfff80000-0xfffeffff has been reserved
Jul 12 15:06:38 shippou kernel: [   20.030467] PCI: Bridge: 0000:00:01.0
Jul 12 15:06:38 shippou kernel: [   20.030470]   IO window: e000-efff
Jul 12 15:06:38 shippou kernel: [   20.030473]   MEM window: fdd00000-fdefffff
Jul 12 15:06:38 shippou kernel: [   20.030475]   PREFETCH window: d8000000-dfffffff
Jul 12 15:06:38 shippou kernel: [   20.030480] PCI: Bridge: 0000:00:14.4
Jul 12 15:06:38 shippou kernel: [   20.030482]   IO window: d000-dfff
Jul 12 15:06:38 shippou kernel: [   20.030487]   MEM window: fdc00000-fdcfffff
Jul 12 15:06:38 shippou kernel: [   20.030491]   PREFETCH window: fdf00000-fdffffff
Jul 12 15:06:38 shippou kernel: [   20.030515] NET: Registered protocol family 2
Jul 12 15:06:38 shippou kernel: [   20.066065] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Jul 12 15:06:38 shippou kernel: [   20.067693] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Jul 12 15:06:38 shippou kernel: [   20.075003] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jul 12 15:06:38 shippou kernel: [   20.075867] TCP: Hash tables configured (established 524288 bind 65536)
Jul 12 15:06:38 shippou kernel: [   20.075870] TCP reno registered
Jul 12 15:06:38 shippou kernel: [   20.086040] checking if image is initramfs... it is
Jul 12 15:06:38 shippou kernel: [   20.790684] Freeing initrd memory: 8212k freed
Jul 12 15:06:38 shippou kernel: [   20.797816] audit: initializing netlink socket (disabled)
Jul 12 15:06:38 shippou kernel: [   20.797829] audit(1215875178.416:1): initialized
Jul 12 15:06:38 shippou kernel: [   20.799803] VFS: Disk quotas dquot_6.5.1
Jul 12 15:06:38 shippou kernel: [   20.799875] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jul 12 15:06:38 shippou kernel: [   20.800018] io scheduler noop registered
Jul 12 15:06:38 shippou kernel: [   20.800020] io scheduler anticipatory registered
Jul 12 15:06:38 shippou kernel: [   20.800022] io scheduler deadline registered
Jul 12 15:06:38 shippou kernel: [   20.800125] io scheduler cfq registered (default)
Jul 12 15:06:38 shippou kernel: [   20.968734] Real Time Clock Driver v1.12ac
Jul 12 15:06:38 shippou kernel: [   20.968961] Linux agpgart interface v0.102
Jul 12 15:06:38 shippou kernel: [   20.968963] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jul 12 15:06:38 shippou kernel: [   20.969113] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 12 15:06:38 shippou kernel: [   20.969706] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 12 15:06:38 shippou kernel: [   20.970410] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jul 12 15:06:38 shippou kernel: [   20.970480] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jul 12 15:06:38 shippou kernel: [   20.970572] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jul 12 15:06:38 shippou kernel: [   20.970905] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 12 15:06:38 shippou kernel: [   20.970910] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 12 15:06:38 shippou kernel: [   20.976580] mice: PS/2 mouse device common for all mice
Jul 12 15:06:38 shippou kernel: [   20.976616] cpuidle: using governor ladder
Jul 12 15:06:38 shippou kernel: [   20.976619] cpuidle: using governor menu
Jul 12 15:06:38 shippou kernel: [   20.976771] NET: Registered protocol family 1
Jul 12 15:06:38 shippou kernel: [   20.976870] registered taskstats version 1
Jul 12 15:06:38 shippou kernel: [   20.976991]   Magic number: 0:562:133
Jul 12 15:06:38 shippou kernel: [   20.977137]   hash matches device device:08
Jul 12 15:06:38 shippou kernel: [   20.977143] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
Jul 12 15:06:38 shippou kernel: [   20.977146] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 12 15:06:38 shippou kernel: [   20.977148] EDD information not available.
Jul 12 15:06:38 shippou kernel: [   20.977156] Freeing unused kernel memory: 320k freed
Jul 12 15:06:38 shippou kernel: [   21.004331] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jul 12 15:06:38 shippou kernel: [   22.178842] fuse init (API version 7.9)
Jul 12 15:06:38 shippou kernel: [   22.193239] ACPI: Fan [FAN] (on)
Jul 12 15:06:38 shippou kernel: [   22.199128] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Jul 12 15:06:38 shippou kernel: [   22.200466] ACPI: Thermal Zone [THRM] (40 C)
Jul 12 15:06:38 shippou kernel: [   22.741500] SCSI subsystem initialized
Jul 12 15:06:38 shippou kernel: [   22.813671] usbcore: registered new interface driver usbfs
Jul 12 15:06:38 shippou kernel: [   22.813694] usbcore: registered new interface driver hub
Jul 12 15:06:38 shippou kernel: [   22.825264] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 15:06:38 shippou kernel: [   22.825379] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
Jul 12 15:06:38 shippou kernel: [   22.825386] ahci 0000:00:12.0: controller can't do PMP, turning off CAP_PMP
Jul 12 15:06:38 shippou kernel: [   22.841173] usbcore: registered new device driver usb
Jul 12 15:06:38 shippou kernel: [   22.849161] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jul 12 15:06:38 shippou kernel: [   22.851222] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jul 12 15:06:38 shippou kernel: [   23.040865] Floppy drive(s): fd0 is 1.44M
Jul 12 15:06:38 shippou kernel: [   23.062024] FDC 0 is a post-1991 82077
Jul 12 15:06:38 shippou kernel: [   23.827440] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Jul 12 15:06:38 shippou kernel: [   23.827446] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pio slum part 
Jul 12 15:06:38 shippou kernel: [   23.828653] scsi0 : ahci
Jul 12 15:06:38 shippou kernel: [   23.828980] scsi1 : ahci
Jul 12 15:06:38 shippou kernel: [   23.829130] scsi2 : ahci
Jul 12 15:06:38 shippou kernel: [   23.829282] scsi3 : ahci
Jul 12 15:06:38 shippou kernel: [   23.829362] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 16
Jul 12 15:06:38 shippou kernel: [   23.829367] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 16
Jul 12 15:06:38 shippou kernel: [   23.829371] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 16
Jul 12 15:06:38 shippou kernel: [   23.829375] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 16
Jul 12 15:06:38 shippou kernel: [   24.302590] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 12 15:06:38 shippou kernel: [   24.348503] ata1.00: ATA-7: ST380215AS, 3.AAD, max UDMA/133
Jul 12 15:06:38 shippou kernel: [   24.348506] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32)
Jul 12 15:06:38 shippou kernel: [   24.406725] ata1.00: configured for UDMA/133
Jul 12 15:06:38 shippou kernel: [   24.717860] ata2: SATA link down (SStatus 0 SControl 300)
Jul 12 15:06:38 shippou kernel: [   25.029318] ata3: SATA link down (SStatus 0 SControl 300)
Jul 12 15:06:38 shippou kernel: [   25.340775] ata4: SATA link down (SStatus 0 SControl 300)
Jul 12 15:06:38 shippou kernel: [   25.340899] scsi 0:0:0:0: Direct-Access     ATA      ST380215AS       3.AA PQ: 0 ANSI: 5
Jul 12 15:06:38 shippou kernel: [   25.342353] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 15:06:38 shippou kernel: [   25.342472] ohci_hcd 0000:00:13.0: OHCI Host Controller
Jul 12 15:06:38 shippou kernel: [   25.342742] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Jul 12 15:06:38 shippou kernel: [   25.342762] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02e000
Jul 12 15:06:38 shippou kernel: [   25.349881] Driver 'sd' needs updating - please use bus_type methods
Jul 12 15:06:38 shippou kernel: [   25.356805] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jul 12 15:06:38 shippou kernel: [   25.356818] sd 0:0:0:0: [sda] Write Protect is off
Jul 12 15:06:38 shippou kernel: [   25.356835] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 12 15:06:38 shippou kernel: [   25.356887] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jul 12 15:06:38 shippou kernel: [   25.356895] sd 0:0:0:0: [sda] Write Protect is off
Jul 12 15:06:38 shippou kernel: [   25.356910] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 12 15:06:38 shippou kernel: [   25.356914]  sda: sda1 sda2 sda3 sda4
Jul 12 15:06:38 shippou kernel: [   25.400922] usb usb1: configuration #1 chosen from 1 choice
Jul 12 15:06:38 shippou kernel: [   25.400947] hub 1-0:1.0: USB hub found
Jul 12 15:06:38 shippou kernel: [   25.400957] hub 1-0:1.0: 2 ports detected
Jul 12 15:06:38 shippou kernel: [   25.406563] sd 0:0:0:0: [sda] Attached SCSI disk
Jul 12 15:06:38 shippou kernel: [   25.411972] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 12 15:06:38 shippou kernel: [   25.504616] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 17
Jul 12 15:06:38 shippou kernel: [   25.504743] ohci_hcd 0000:00:13.1: OHCI Host Controller
Jul 12 15:06:38 shippou kernel: [   25.504852] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Jul 12 15:06:38 shippou kernel: [   25.504877] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfe02d000
Jul 12 15:06:38 shippou kernel: [   25.564661] usb usb2: configuration #1 chosen from 1 choice
Jul 12 15:06:38 shippou kernel: [   25.564687] hub 2-0:1.0: USB hub found
Jul 12 15:06:38 shippou kernel: [   25.564696] hub 2-0:1.0: 2 ports detected
Jul 12 15:06:38 shippou kernel: [   25.668303] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 18
Jul 12 15:06:38 shippou kernel: [   25.668416] ohci_hcd 0000:00:13.2: OHCI Host Controller
Jul 12 15:06:38 shippou kernel: [   25.668478] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
Jul 12 15:06:38 shippou kernel: [   25.668502] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfe02c000
Jul 12 15:06:38 shippou kernel: [   25.728376] usb usb3: configuration #1 chosen from 1 choice
Jul 12 15:06:38 shippou kernel: [   25.728411] hub 3-0:1.0: USB hub found
Jul 12 15:06:38 shippou kernel: [   25.728420] hub 3-0:1.0: 2 ports detected
Jul 12 15:06:38 shippou kernel: [   25.764647] Attempting manual resume
Jul 12 15:06:38 shippou kernel: [   25.810565] kjournald starting.  Commit interval 5 seconds
Jul 12 15:06:38 shippou kernel: [   25.810577] EXT3-fs: mounted filesystem with ordered data mode.
Jul 12 15:06:38 shippou kernel: [   25.832022] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 17
Jul 12 15:06:38 shippou kernel: [   25.832160] ohci_hcd 0000:00:13.3: OHCI Host Controller
Jul 12 15:06:38 shippou kernel: [   25.832220] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
Jul 12 15:06:38 shippou kernel: [   25.832240] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfe02b000
Jul 12 15:06:38 shippou kernel: [   25.892082] usb usb4: configuration #1 chosen from 1 choice
Jul 12 15:06:38 shippou kernel: [   25.892107] hub 4-0:1.0: USB hub found
Jul 12 15:06:38 shippou kernel: [   25.892117] hub 4-0:1.0: 2 ports detected
Jul 12 15:06:38 shippou kernel: [   25.995752] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 18
Jul 12 15:06:38 shippou kernel: [   25.995912] ohci_hcd 0000:00:13.4: OHCI Host Controller
Jul 12 15:06:38 shippou kernel: [   25.995974] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
Jul 12 15:06:38 shippou kernel: [   25.995992] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfe02a000
Jul 12 15:06:38 shippou kernel: [   26.055768] usb usb5: configuration #1 chosen from 1 choice
Jul 12 15:06:38 shippou kernel: [   26.055792] hub 5-0:1.0: USB hub found
Jul 12 15:06:38 shippou kernel: [   26.055801] hub 5-0:1.0: 2 ports detected
Jul 12 15:06:38 shippou kernel: [   26.159604] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 19
Jul 12 15:06:38 shippou kernel: [   26.159742] ehci_hcd 0000:00:13.5: EHCI Host Controller
Jul 12 15:06:38 shippou kernel: [   26.159803] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
Jul 12 15:06:38 shippou kernel: [   26.159843] ehci_hcd 0000:00:13.5: debug port 1
Jul 12 15:06:38 shippou kernel: [   26.159862] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfe029000
Jul 12 15:06:38 shippou kernel: [   26.171344] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jul 12 15:06:38 shippou kernel: [   26.171459] usb usb6: configuration #1 chosen from 1 choice
Jul 12 15:06:38 shippou kernel: [   26.171484] hub 6-0:1.0: USB hub found
Jul 12 15:06:38 shippou kernel: [   26.171492] hub 6-0:1.0: 10 ports detected
Jul 12 15:06:38 shippou kernel: [   26.275405] SB600_PATA: IDE controller (0x1002:0x438c rev 0x00) at  PCI slot 0000:00:14.1
Jul 12 15:06:38 shippou kernel: [   26.275418] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 15:06:38 shippou kernel: [   26.275430] SB600_PATA: not 100% native mode: will probe irqs later
Jul 12 15:06:38 shippou kernel: [   26.275438]     ide0: BM-DMA at 0xf900-0xf907, BIOS settings: hda:pio, hdb:DMA
Jul 12 15:06:38 shippou kernel: [   27.062105] hdb: LITE-ON DVDRW LH-20A1P, ATAPI CD/DVD-ROM drive
Jul 12 15:06:38 shippou kernel: [   27.341638] hdb: UDMA/66 mode selected
Jul 12 15:06:38 shippou kernel: [   27.342014] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Jul 12 15:06:38 shippou kernel: [   27.354986] r8169 Gigabit Ethernet driver 2.2LK loaded
Jul 12 15:06:38 shippou kernel: [   27.355022] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 22 (level, low) -> IRQ 22
Jul 12 15:06:38 shippou kernel: [   27.355255] eth0: RTL8169sc/8110sc at 0xffffc20001044000, 00:19:21:21:21:b5, XID 18000000 IRQ 22
Jul 12 15:06:38 shippou kernel: [   32.459891] input: PC Speaker as /devices/platform/pcspkr/input/input2
Jul 12 15:06:38 shippou kernel: [   32.637997] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 12 15:06:38 shippou kernel: [   32.690488] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul 12 15:06:38 shippou kernel: [   32.794039] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Jul 12 15:06:38 shippou kernel: [   33.084424] input: Power Button (FF) as /devices/virtual/input/input3
Jul 12 15:06:38 shippou kernel: [   33.113507] input: ImExPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input4
Jul 12 15:06:38 shippou kernel: [   33.115268] ACPI: Power Button (FF) [PWRF]
Jul 12 15:06:38 shippou kernel: [   33.115329] input: Power Button (CM) as /devices/virtual/input/input5
Jul 12 15:06:38 shippou kernel: [   33.143232] ACPI: Power Button (CM) [PWRB]
Jul 12 15:06:38 shippou kernel: [   33.174592] parport_pc 00:0a: reported by Plug and Play ACPI
Jul 12 15:06:38 shippou kernel: [   33.174651] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jul 12 15:06:38 shippou kernel: [   34.598344] r8169: eth0: link down
Jul 12 15:06:38 shippou kernel: [   34.672410] hdb: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
Jul 12 15:06:38 shippou kernel: [   34.672418] Uniform CD-ROM driver Revision: 3.20
Jul 12 15:06:38 shippou kernel: [   34.789605] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 15:06:38 shippou kernel: [   34.814177] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
Jul 12 15:06:38 shippou kernel: [   34.964915] NET: Registered protocol family 10
Jul 12 15:06:38 shippou kernel: [   34.965120] lo: Disabled Privacy Extensions
Jul 12 15:06:38 shippou kernel: [   34.965442] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 12 15:06:38 shippou kernel: [   36.785586] lp0: using parport0 (interrupt-driven).
Jul 12 15:06:38 shippou kernel: [   36.878631] Adding 289160k swap on /dev/sda3.  Priority:-1 extents:1 across:289160k
Jul 12 15:06:38 shippou kernel: [   37.433594] EXT3 FS on sda2, internal journal
Jul 12 15:06:38 shippou kernel: [   38.158229] kjournald starting.  Commit interval 5 seconds
Jul 12 15:06:38 shippou kernel: [   38.158429] EXT3 FS on sda4, internal journal
Jul 12 15:06:38 shippou kernel: [   38.158433] EXT3-fs: mounted filesystem with ordered data mode.
Jul 12 15:06:38 shippou kernel: [   38.618892] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul 12 15:06:38 shippou kernel: [   39.108168] No dock devices found.
Jul 12 15:06:38 shippou kernel: [   39.359372] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (1 cpu cores) (version 2.20.00)
Jul 12 15:06:38 shippou kernel: [   39.359412] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
Jul 12 15:06:38 shippou kernel: [   39.359415] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
Jul 12 15:06:38 shippou kernel: [   40.182029] ppdev: user-space parallel port driver
Jul 12 15:06:38 shippou kernel: [   40.326762] audit(1215846398.656:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4765 profile="/usr/sbin/cupsd" namespace="default"
Jul 12 15:06:38 shippou dhcdbd: Started up.
Jul 12 15:06:41 shippou kernel: [   42.706667] Marking TSC unstable due to cpufreq changes
Jul 12 15:06:41 shippou kernel: [   42.710709] Time: hpet clocksource has been installed.
Jul 12 15:06:41 shippou kernel: [   43.061139] Clocksource tsc unstable (delta = -222228359 ns)
Jul 12 15:06:43 shippou kernel: [   44.253724] Bluetooth: Core ver 2.11
Jul 12 15:06:43 shippou kernel: [   44.254310] NET: Registered protocol family 31
Jul 12 15:06:43 shippou kernel: [   44.254314] Bluetooth: HCI device and connection manager initialized
Jul 12 15:06:43 shippou kernel: [   44.254318] Bluetooth: HCI socket layer initialized
Jul 12 15:06:43 shippou kernel: [   44.283768] Bluetooth: L2CAP ver 2.9
Jul 12 15:06:43 shippou kernel: [   44.283772] Bluetooth: L2CAP socket layer initialized
Jul 12 15:06:43 shippou kernel: [   44.327959] Bluetooth: RFCOMM socket layer initialized
Jul 12 15:06:43 shippou kernel: [   44.328173] Bluetooth: RFCOMM TTY layer initialized
Jul 12 15:06:43 shippou kernel: [   44.328177] Bluetooth: RFCOMM ver 1.8
Jul 12 15:06:46 shippou kernel: [   45.531068] [drm] Initialized drm 1.1.0 20060810
Jul 12 15:06:52 shippou kernel: [   49.775423] hda-intel: Invalid position buffer, using LPIB read method instead.
Jul 12 15:07:16 shippou kernel: [   64.830097] UDF-fs: No VRS found
Jul 12 15:12:59 shippou kernel: [  300.159549] r8169: eth0: link up
Jul 12 15:12:59 shippou kernel: [  300.161980] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jul 12 15:26:37 shippou -- MARK --
Jul 12 15:46:37 shippou -- MARK --
Jul 12 15:54:05 shippou kernel: [ 1744.828213] usb 6-6: new high speed USB device using ehci_hcd and address 2
Jul 12 15:54:05 shippou kernel: [ 1744.902157] usb 6-6: configuration #1 chosen from 1 choice
Jul 12 15:54:05 shippou kernel: [ 1744.992078] usbcore: registered new interface driver libusual
Jul 12 15:54:05 shippou kernel: [ 1745.015146] Initializing USB Mass Storage driver...
Jul 12 15:54:05 shippou kernel: [ 1745.020675] scsi4 : SCSI emulation for USB Mass Storage devices
Jul 12 15:54:05 shippou kernel: [ 1745.024233] usbcore: registered new interface driver usb-storage
Jul 12 15:54:05 shippou kernel: [ 1745.024239] USB Mass Storage support registered.
Jul 12 15:54:10 shippou kernel: [ 1748.323085] scsi scan: INQUIRY result too short (5), using 36
Jul 12 15:54:10 shippou kernel: [ 1748.323091] scsi 4:0:0:0: Direct-Access     USB 2.0  (HS) Flash Disk  1.00 PQ: 0 ANSI: 0 CCS
Jul 12 15:54:10 shippou kernel: [ 1748.334197] sd 4:0:0:0: [sdb] 1993649 512-byte hardware sectors (1021 MB)
Jul 12 15:54:10 shippou kernel: [ 1748.334675] sd 4:0:0:0: [sdb] Write Protect is off
Jul 12 15:54:10 shippou kernel: [ 1748.336692] sd 4:0:0:0: [sdb] 1993649 512-byte hardware sectors (1021 MB)
Jul 12 15:54:10 shippou kernel: [ 1748.337434] sd 4:0:0:0: [sdb] Write Protect is off
Jul 12 15:54:10 shippou kernel: [ 1748.337448]  sdb: unknown partition table
Jul 12 15:54:10 shippou kernel: [ 1748.345329] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Jul 12 15:54:10 shippou kernel: [ 1748.345372] sd 4:0:0:0: Attached scsi generic sg1 type 0
Jul 12 16:06:37 shippou -- MARK --
Jul 12 16:09:34 shippou kernel: [ 2367.526444] usb 6-6: USB disconnect, address 2
Jul 12 16:10:13 shippou kernel: [ 2389.958685] usb 6-6: new high speed USB device using ehci_hcd and address 3
Jul 12 16:10:13 shippou kernel: [ 2390.032608] usb 6-6: configuration #1 chosen from 1 choice
Jul 12 16:10:13 shippou kernel: [ 2390.052171] scsi5 : SCSI emulation for USB Mass Storage devices
Jul 12 16:10:18 shippou kernel: [ 2392.827656] scsi scan: INQUIRY result too short (5), using 36
Jul 12 16:10:18 shippou kernel: [ 2392.827662] scsi 5:0:0:0: Direct-Access     USB 2.0  (HS) Flash Disk  1.00 PQ: 0 ANSI: 0 CCS
Jul 12 16:10:18 shippou kernel: [ 2392.829187] sd 5:0:0:0: [sdb] 1993649 512-byte hardware sectors (1021 MB)
Jul 12 16:10:18 shippou kernel: [ 2392.833759] sd 5:0:0:0: [sdb] Write Protect is off
Jul 12 16:10:18 shippou kernel: [ 2392.835059] sd 5:0:0:0: [sdb] 1993649 512-byte hardware sectors (1021 MB)
Jul 12 16:10:18 shippou kernel: [ 2392.835337] sd 5:0:0:0: [sdb] Write Protect is off
Jul 12 16:10:18 shippou kernel: [ 2392.835348]  sdb: unknown partition table
Jul 12 16:10:18 shippou kernel: [ 2392.839672] sd 5:0:0:0: [sdb] Attached SCSI removable disk
Jul 12 16:10:18 shippou kernel: [ 2392.839716] sd 5:0:0:0: Attached scsi generic sg1 type 0
Jul 12 16:26:37 shippou -- MARK --
Jul 12 16:44:54 shippou kernel: [ 3866.797230] usb 6-6: USB disconnect, address 3
Jul 12 16:44:54 shippou kernel: [ 3866.913264] usb 6-6: new high speed USB device using ehci_hcd and address 4
Jul 12 16:44:54 shippou kernel: [ 3867.047263] usb 6-6: configuration #1 chosen from 1 choice
Jul 12 16:44:54 shippou kernel: [ 3867.078082] scsi6 : SCSI emulation for USB Mass Storage devices
Jul 12 16:44:57 shippou kernel: [ 3869.677018] usb 6-6: USB disconnect, address 4
Jul 12 16:44:57 shippou kernel: [ 3869.788265] usb 6-6: new high speed USB device using ehci_hcd and address 5
Jul 12 16:44:57 shippou kernel: [ 3869.921313] usb 6-6: configuration #1 chosen from 1 choice
Jul 12 16:44:57 shippou kernel: [ 3869.948348] scsi7 : SCSI emulation for USB Mass Storage devices
Jul 12 16:45:02 shippou kernel: [ 3874.944218] scsi scan: INQUIRY result too short (5), using 36
Jul 12 16:45:02 shippou kernel: [ 3874.944224] scsi 7:0:0:0: Direct-Access     USB 2.0  (HS) Flash Disk  1.00 PQ: 0 ANSI: 0 CCS
Jul 12 16:45:02 shippou kernel: [ 3874.955330] sd 7:0:0:0: [sdb] 1993649 512-byte hardware sectors (1021 MB)
Jul 12 16:45:02 shippou kernel: [ 3874.955809] sd 7:0:0:0: [sdb] Write Protect is off
Jul 12 16:45:02 shippou kernel: [ 3874.957816] sd 7:0:0:0: [sdb] 1993649 512-byte hardware sectors (1021 MB)
Jul 12 16:45:02 shippou kernel: [ 3874.958312] sd 7:0:0:0: [sdb] Write Protect is off
Jul 12 16:45:02 shippou kernel: [ 3874.958324]  sdb: unknown partition table
Jul 12 16:45:02 shippou kernel: [ 3874.966962] sd 7:0:0:0: [sdb] Attached SCSI removable disk
Jul 12 16:45:02 shippou kernel: [ 3874.967007] sd 7:0:0:0: Attached scsi generic sg1 type 0
Jul 12 16:51:29 shippou kernel: [ 4122.739890] gvfs-fuse-daemo[5388] general protection rip:7f03b1ce7423 rsp:7fffbb911e00 error:0
Jul 12 16:51:31 shippou kernel: [ 4124.494992] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jul 12 16:51:32 shippou exiting on signal 15
Jul 12 01:07:30 shippou syslogd 1.5.0#1ubuntu1: restart.
Jul 12 01:07:31 shippou kernel: Inspecting /boot/System.map-2.6.24-19-generic
Jul 12 01:07:31 shippou kernel: Loaded 28491 symbols from /boot/System.map-2.6.24-19-generic.
Jul 12 01:07:31 shippou kernel: Symbols match kernel version 2.6.24.
Jul 12 01:07:31 shippou kernel: Loaded 16834 symbols from 77 modules.
Jul 12 01:07:31 shippou kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 12 01:07:31 shippou kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 12 01:07:31 shippou kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:15:37 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
Jul 12 01:07:31 shippou kernel: [    0.000000] Command line: root=UUID=2e985bef-5550-421f-b1bf-e1f730273cbc ro quiet splash
Jul 12 01:07:31 shippou kernel: [    0.000000] BIOS-provided physical RAM map:
Jul 12 01:07:31 shippou kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jul 12 01:07:31 shippou kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jul 12 01:07:31 shippou kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jul 12 01:07:31 shippou kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000097fe0000 (usable)
Jul 12 01:07:31 shippou kernel: [    0.000000]  BIOS-e820: 0000000097fe0000 - 0000000097fe3000 (ACPI NVS)
Jul 12 01:07:31 shippou kernel: [    0.000000]  BIOS-e820: 0000000097fe3000 - 0000000097ff0000 (ACPI data)
Jul 12 01:07:31 shippou kernel: [    0.000000]  BIOS-e820: 0000000097ff0000 - 0000000098000000 (reserved)
Jul 12 01:07:31 shippou kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Jul 12 01:07:31 shippou kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Jul 12 01:07:31 shippou kernel: [    0.000000] end_pfn_map = 1048576
Jul 12 01:07:31 shippou kernel: [    0.000000] DMI 2.5 present.
Jul 12 01:07:31 shippou kernel: [    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F7B80 checksum 0
Jul 12 01:07:31 shippou kernel: [    0.000000] ACPI: RSDP 000F7B80, 0024 (r2 RS690 )
Jul 12 01:07:31 shippou kernel: [    0.000000] ACPI: RSDT 97FE3040, 0038 (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 12 01:07:31 shippou kernel: [    0.000000] ACPI: FACP 97FE30C0, 0074 (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 12 01:07:31 shippou kernel: [    0.000000] ACPI: DSDT 97FE3180, 4B0B (r1 RS690  AWRDACPI     1000 MSFT  3000000)
Jul 12 01:07:31 shippou kernel: [    0.000000] ACPI: FACS 97FE0000, 0040
Jul 12 01:07:31 shippou kernel: [    0.000000] ACPI: SSDT 97FE7DC0, 00D3 (r1 PTLTD  POWERNOW        1  LTP        1)
Jul 12 01:07:31 shippou kernel: [    0.000000] ACPI: HPET 97FE7F00, 0038 (r1 RS690  AWRDACPI 42302E31 AWRD       98)
Jul 12 01:07:31 shippou kernel: [    0.000000] ACPI: MCFG 97FE7F80, 003C (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 12 01:07:31 shippou kernel: [    0.000000] ACPI: APIC 97FE7D00, 0068 (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 12 01:07:31 shippou kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Jul 12 01:07:31 shippou kernel: [    0.000000] CPU has 1 num_cores
Jul 12 01:07:31 shippou kernel: [    0.000000] No NUMA configuration found
Jul 12 01:07:31 shippou kernel: [    0.000000] Faking a node at 0000000000000000-0000000097fe0000
Jul 12 01:07:31 shippou kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000097fe0000
Jul 12 01:07:31 shippou kernel: [    0.000000] Zone PFN ranges:
Jul 12 01:07:31 shippou kernel: [    0.000000]   DMA             0 ->     4096
Jul 12 01:07:31 shippou kernel: [    0.000000]   DMA32        4096 ->  1048576
Jul 12 01:07:31 shippou kernel: [    0.000000]   Normal    1048576 ->  1048576
Jul 12 01:07:31 shippou kernel: [    0.000000] Movable zone start PFN for each node
Jul 12 01:07:31 shippou kernel: [    0.000000] early_node_map[2] active PFN ranges
Jul 12 01:07:31 shippou kernel: [    0.000000]     0:        0 ->      159
Jul 12 01:07:31 shippou kernel: [    0.000000]     0:      256 ->   622560
Jul 12 01:07:31 shippou kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Jul 12 01:07:31 shippou kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Jul 12 01:07:31 shippou kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul 12 01:07:31 shippou kernel: [    0.000000] Processor #0 (Bootup-CPU)
Jul 12 01:07:31 shippou kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Jul 12 01:07:31 shippou kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul 12 01:07:31 shippou kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jul 12 01:07:31 shippou kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jul 12 01:07:31 shippou kernel: [    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
Jul 12 01:07:31 shippou kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 12 01:07:31 shippou kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jul 12 01:07:31 shippou kernel: [    0.000000] Setting APIC routing to flat
Jul 12 01:07:31 shippou kernel: [    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
Jul 12 01:07:31 shippou kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 12 01:07:31 shippou kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Jul 12 01:07:31 shippou kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Jul 12 01:07:31 shippou kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Jul 12 01:07:31 shippou kernel: [    0.000000] Allocating PCI resources starting at a0000000 (gap: 98000000:48000000)
Jul 12 01:07:31 shippou kernel: [    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
Jul 12 01:07:31 shippou kernel: [    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
Jul 12 01:07:31 shippou kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 612716
Jul 12 01:07:31 shippou kernel: [    0.000000] Policy zone: DMA32
Jul 12 01:07:31 shippou kernel: [    0.000000] Kernel command line: root=UUID=2e985bef-5550-421f-b1bf-e1f730273cbc ro quiet splash
Jul 12 01:07:31 shippou kernel: [    0.000000] Initializing CPU#0
Jul 12 01:07:31 shippou kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Jul 12 01:07:31 shippou kernel: [    0.000000] TSC calibrated against HPET
Jul 12 01:07:31 shippou kernel: [   19.072671] time.c: Detected 1799.801 MHz processor.
Jul 12 01:07:31 shippou kernel: [   19.073358] Console: colour VGA+ 80x25
Jul 12 01:07:31 shippou kernel: [   19.073361] console [tty0] enabled
Jul 12 01:07:31 shippou kernel: [   19.073378] Checking aperture...
Jul 12 01:07:31 shippou kernel: [   19.073380] CPU 0: aperture @ fc40000000 size 32 MB
Jul 12 01:07:31 shippou kernel: [   19.073382] Aperture too small (32 MB)
Jul 12 01:07:31 shippou kernel: [   19.083194] No AGP bridge found
Jul 12 01:07:31 shippou kernel: [   19.116586] Memory: 2442456k/2490240k available (2489k kernel code, 47396k reserved, 1318k data, 320k init)
Jul 12 01:07:31 shippou kernel: [   19.116625] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Jul 12 01:07:31 shippou kernel: [   19.194678] Calibrating delay using timer specific routine.. 3708.90 BogoMIPS (lpj=7417818)
Jul 12 01:07:31 shippou kernel: [   19.194725] Security Framework initialized
Jul 12 01:07:31 shippou kernel: [   19.194731] SELinux:  Disabled at boot.
Jul 12 01:07:31 shippou kernel: [   19.194744] AppArmor: AppArmor initialized
Jul 12 01:07:31 shippou kernel: [   19.194747] Failure registering capabilities with primary security module.
Jul 12 01:07:31 shippou kernel: [   19.195126] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jul 12 01:07:31 shippou kernel: [   19.199146] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jul 12 01:07:31 shippou kernel: [   19.200766] Mount-cache hash table entries: 256
Jul 12 01:07:31 shippou kernel: [   19.200916] Initializing cgroup subsys ns
Jul 12 01:07:31 shippou kernel: [   19.200920] Initializing cgroup subsys cpuacct
Jul 12 01:07:31 shippou kernel: [   19.200935] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jul 12 01:07:31 shippou kernel: [   19.200938] CPU: L2 Cache: 512K (64 bytes/line)
Jul 12 01:07:31 shippou kernel: [   19.200940] CPU 0/0 -> Node 0
Jul 12 01:07:31 shippou kernel: [   19.200968] SMP alternatives: switching to UP code
Jul 12 01:07:31 shippou kernel: [   19.201654] Early unpacking initramfs... done
Jul 12 01:07:31 shippou kernel: [   19.602398] ACPI: Core revision 20070126
Jul 12 01:07:31 shippou kernel: [   19.602460] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Jul 12 01:07:31 shippou kernel: [   19.651916] Using local APIC timer interrupts.
Jul 12 01:07:31 shippou kernel: [   19.707393] Detected 12.498 MHz APIC timer.
Jul 12 01:07:31 shippou kernel: [   19.707443] Brought up 1 CPUs
Jul 12 01:07:31 shippou kernel: [   19.707715] net_namespace: 120 bytes
Jul 12 01:07:31 shippou kernel: [   19.708116] Time: 17:07:11  Date: 07/12/08
Jul 12 01:07:31 shippou kernel: [   19.708145] NET: Registered protocol family 16
Jul 12 01:07:31 shippou kernel: [   19.708318] ACPI: bus type pci registered
Jul 12 01:07:31 shippou kernel: [   19.708385] PCI: Using configuration type 1
Jul 12 01:07:31 shippou kernel: [   19.715089] ACPI: Interpreter enabled
Jul 12 01:07:31 shippou kernel: [   19.715095] ACPI: (supports S0 S3 S4 S5)
Jul 12 01:07:31 shippou kernel: [   19.715111] ACPI: Using IOAPIC for interrupt routing
Jul 12 01:07:31 shippou kernel: [   19.720297] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul 12 01:07:31 shippou kernel: [   19.720460] pci 0000:00:12.0: set SATA to AHCI mode
Jul 12 01:07:31 shippou kernel: [   19.721256] PCI: Transparent bridge - 0000:00:14.4
Jul 12 01:07:31 shippou kernel: [   19.742004] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 01:07:31 shippou kernel: [   19.742110] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 01:07:31 shippou kernel: [   19.742213] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 01:07:31 shippou kernel: [   19.742316] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 01:07:31 shippou kernel: [   19.742420] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 01:07:31 shippou kernel: [   19.742522] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 01:07:31 shippou kernel: [   19.742625] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 01:07:31 shippou kernel: [   19.742727] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 01:07:31 shippou kernel: [   19.742843] Linux Plug and Play Support v0.97 (c) Adam Belay
Jul 12 01:07:31 shippou kernel: [   19.742872] pnp: PnP ACPI init
Jul 12 01:07:31 shippou kernel: [   19.742881] ACPI: bus type pnp registered
Jul 12 01:07:31 shippou kernel: [   19.745901] pnp: PnP ACPI: found 15 devices
Jul 12 01:07:31 shippou kernel: [   19.745904] ACPI: ACPI bus type pnp unregistered
Jul 12 01:07:31 shippou kernel: [   19.746130] PCI: Using ACPI for IRQ routing
Jul 12 01:07:31 shippou kernel: [   19.746133] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jul 12 01:07:31 shippou kernel: [   19.759348] NET: Registered protocol family 8
Jul 12 01:07:31 shippou kernel: [   19.759350] NET: Registered protocol family 20
Jul 12 01:07:31 shippou kernel: [   19.759430] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Jul 12 01:07:31 shippou kernel: [   19.759434] hpet0: 4 32-bit timers, 14318180 Hz
Jul 12 01:07:31 shippou kernel: [   19.760490] AppArmor: AppArmor Filesystem Enabled
Jul 12 01:07:31 shippou kernel: [   19.763308] Time: tsc clocksource has been installed.
Jul 12 01:07:31 shippou kernel: [   19.771291] system 00:01: ioport range 0x4100-0x411f has been reserved
Jul 12 01:07:31 shippou kernel: [   19.771294] system 00:01: ioport range 0x228-0x22f has been reserved
Jul 12 01:07:31 shippou kernel: [   19.771297] system 00:01: ioport range 0x40b-0x40b has been reserved
Jul 12 01:07:31 shippou kernel: [   19.771300] system 00:01: ioport range 0x4d6-0x4d6 has been reserved
Jul 12 01:07:31 shippou kernel: [   19.771303] system 00:01: ioport range 0xc00-0xc01 has been reserved
Jul 12 01:07:31 shippou kernel: [   19.771306] system 00:01: ioport range 0xc14-0xc14 has been reserved
Jul 12 01:07:31 shippou kernel: [   19.771310] system 00:01: ioport range 0xc50-0xc52 has been reserved
Jul 12 01:07:31 shippou kernel: [   19.771313] system 00:01: ioport range 0xc6c-0xc6d has been reserved
Jul 12 01:07:31 shippou kernel: [   19.771316] system 00:01: ioport range 0xc6f-0xc6f has been reserved
Jul 12 01:07:31 shippou kernel: [   19.771319] system 00:01: ioport range 0xcd0-0xcd1 has been reserved
Jul 12 01:07:31 shippou kernel: [   19.771322] system 00:01: ioport range 0xcd2-0xcd3 has been reserved
Jul 12 01:07:31 shippou kernel: [   19.771325] system 00:01: ioport range 0xcd4-0xcdf has been reserved
Jul 12 01:07:31 shippou kernel: [   19.771328] system 00:01: ioport range 0x4000-0x40fe has been reserved
Jul 12 01:07:31 shippou kernel: [   19.771331] system 00:01: ioport range 0x4210-0x4217 has been reserved
Jul 12 01:07:31 shippou kernel: [   19.771334] system 00:01: ioport range 0xb10-0xb1f has been reserved
Jul 12 01:07:31 shippou kernel: [   19.771344] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
Jul 12 01:07:31 shippou kernel: [   19.771347] system 00:07: ioport range 0x220-0x225 has been reserved
Jul 12 01:07:31 shippou kernel: [   19.771350] system 00:07: ioport range 0xb00-0xb0f has been reserved
Jul 12 01:07:31 shippou kernel: [   19.771360] system 00:0d: iomem range 0xe0000000-0xefffffff could not be reserved
Jul 12 01:07:31 shippou kernel: [   19.771366] system 00:0e: iomem range 0xf0000-0xfffff could not be reserved
Jul 12 01:07:31 shippou kernel: [   19.771369] system 00:0e: iomem range 0xfed00000-0xfed000ff has been reserved
Jul 12 01:07:31 shippou kernel: [   19.771373] system 00:0e: iomem range 0x97fe0000-0x97ffffff could not be reserved
Jul 12 01:07:31 shippou kernel: [   19.771376] system 00:0e: iomem range 0xffff0000-0xffffffff has been reserved
Jul 12 01:07:31 shippou kernel: [   19.771380] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
Jul 12 01:07:31 shippou kernel: [   19.771383] system 00:0e: iomem range 0x100000-0x97fdffff could not be reserved
Jul 12 01:07:31 shippou kernel: [   19.771386] system 00:0e: iomem range 0x98000000-0x9fffffff has been reserved
Jul 12 01:07:31 shippou kernel: [   19.771389] system 00:0e: iomem range 0xfec00000-0xfec00fff has been reserved
Jul 12 01:07:31 shippou kernel: [   19.771393] system 00:0e: iomem range 0xfee00000-0xfee00fff could not be reserved
Jul 12 01:07:31 shippou kernel: [   19.771396] system 00:0e: iomem range 0xfff80000-0xfffeffff has been reserved
Jul 12 01:07:31 shippou kernel: [   19.771753] PCI: Bridge: 0000:00:01.0
Jul 12 01:07:31 shippou kernel: [   19.771756]   IO window: e000-efff
Jul 12 01:07:31 shippou kernel: [   19.771759]   MEM window: fdd00000-fdefffff
Jul 12 01:07:31 shippou kernel: [   19.771761]   PREFETCH window: d8000000-dfffffff
Jul 12 01:07:31 shippou kernel: [   19.771766] PCI: Bridge: 0000:00:14.4
Jul 12 01:07:31 shippou kernel: [   19.771769]   IO window: d000-dfff
Jul 12 01:07:31 shippou kernel: [   19.771773]   MEM window: fdc00000-fdcfffff
Jul 12 01:07:31 shippou kernel: [   19.771777]   PREFETCH window: fdf00000-fdffffff
Jul 12 01:07:31 shippou kernel: [   19.771802] NET: Registered protocol family 2
Jul 12 01:07:31 shippou kernel: [   19.807349] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Jul 12 01:07:31 shippou kernel: [   19.808976] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Jul 12 01:07:31 shippou kernel: [   19.816277] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jul 12 01:07:31 shippou kernel: [   19.817139] TCP: Hash tables configured (established 524288 bind 65536)
Jul 12 01:07:31 shippou kernel: [   19.817143] TCP reno registered
Jul 12 01:07:31 shippou kernel: [   19.827326] checking if image is initramfs... it is
Jul 12 01:07:31 shippou kernel: [   20.531976] Freeing initrd memory: 8212k freed
Jul 12 01:07:31 shippou kernel: [   20.539110] audit: initializing netlink socket (disabled)
Jul 12 01:07:31 shippou kernel: [   20.539123] audit(1215882431.416:1): initialized
Jul 12 01:07:31 shippou kernel: [   20.541097] VFS: Disk quotas dquot_6.5.1
Jul 12 01:07:31 shippou kernel: [   20.541169] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jul 12 01:07:31 shippou kernel: [   20.541310] io scheduler noop registered
Jul 12 01:07:31 shippou kernel: [   20.541313] io scheduler anticipatory registered
Jul 12 01:07:31 shippou kernel: [   20.541314] io scheduler deadline registered
Jul 12 01:07:31 shippou kernel: [   20.541418] io scheduler cfq registered (default)
Jul 12 01:07:31 shippou kernel: [   20.710095] Real Time Clock Driver v1.12ac
Jul 12 01:07:31 shippou kernel: [   20.710322] Linux agpgart interface v0.102
Jul 12 01:07:31 shippou kernel: [   20.710324] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jul 12 01:07:31 shippou kernel: [   20.710473] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 12 01:07:31 shippou kernel: [   20.711060] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 12 01:07:31 shippou kernel: [   20.711764] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jul 12 01:07:31 shippou kernel: [   20.711833] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jul 12 01:07:31 shippou kernel: [   20.711924] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jul 12 01:07:31 shippou kernel: [   20.712260] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 12 01:07:31 shippou kernel: [   20.712264] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 12 01:07:31 shippou kernel: [   20.717871] mice: PS/2 mouse device common for all mice
Jul 12 01:07:31 shippou kernel: [   20.717905] cpuidle: using governor ladder
Jul 12 01:07:31 shippou kernel: [   20.717907] cpuidle: using governor menu
Jul 12 01:07:31 shippou kernel: [   20.718056] NET: Registered protocol family 1
Jul 12 01:07:31 shippou kernel: [   20.718153] registered taskstats version 1
Jul 12 01:07:31 shippou kernel: [   20.718274]   Magic number: 0:774:137
Jul 12 01:07:31 shippou kernel: [   20.718427] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
Jul 12 01:07:31 shippou kernel: [   20.718430] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 12 01:07:31 shippou kernel: [   20.718432] EDD information not available.
Jul 12 01:07:31 shippou kernel: [   20.718440] Freeing unused kernel memory: 320k freed
Jul 12 01:07:31 shippou kernel: [   20.745621] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jul 12 01:07:31 shippou kernel: [   21.917043] fuse init (API version 7.9)
Jul 12 01:07:31 shippou kernel: [   21.931458] ACPI: Fan [FAN] (on)
Jul 12 01:07:31 shippou kernel: [   21.937261] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Jul 12 01:07:31 shippou kernel: [   21.938601] ACPI: Thermal Zone [THRM] (40 C)
Jul 12 01:07:31 shippou kernel: [   22.479441] SCSI subsystem initialized
Jul 12 01:07:31 shippou kernel: [   22.544527] usbcore: registered new interface driver usbfs
Jul 12 01:07:31 shippou kernel: [   22.544550] usbcore: registered new interface driver hub
Jul 12 01:07:31 shippou kernel: [   22.556123] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 01:07:31 shippou kernel: [   22.556270] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
Jul 12 01:07:31 shippou kernel: [   22.556276] ahci 0000:00:12.0: controller can't do PMP, turning off CAP_PMP
Jul 12 01:07:31 shippou kernel: [   22.570897] usbcore: registered new device driver usb
Jul 12 01:07:31 shippou kernel: [   22.583347] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jul 12 01:07:31 shippou kernel: [   22.584354] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jul 12 01:07:31 shippou kernel: [   22.778237] Floppy drive(s): fd0 is 1.44M
Jul 12 01:07:31 shippou kernel: [   22.797927] FDC 0 is a post-1991 82077
Jul 12 01:07:31 shippou kernel: [   23.556771] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Jul 12 01:07:31 shippou kernel: [   23.556777] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pio slum part 
Jul 12 01:07:31 shippou kernel: [   23.557978] scsi0 : ahci
Jul 12 01:07:31 shippou kernel: [   23.558305] scsi1 : ahci
Jul 12 01:07:31 shippou kernel: [   23.558453] scsi2 : ahci
Jul 12 01:07:31 shippou kernel: [   23.558597] scsi3 : ahci
Jul 12 01:07:31 shippou kernel: [   23.558676] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 16
Jul 12 01:07:31 shippou kernel: [   23.558680] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 16
Jul 12 01:07:31 shippou kernel: [   23.558684] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 16
Jul 12 01:07:31 shippou kernel: [   23.558687] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 16
Jul 12 01:07:31 shippou kernel: [   24.031920] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 12 01:07:31 shippou kernel: [   24.078182] ata1.00: ATA-7: ST380215AS, 3.AAD, max UDMA/133
Jul 12 01:07:31 shippou kernel: [   24.078187] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32)
Jul 12 01:07:31 shippou kernel: [   24.136398] ata1.00: configured for UDMA/133
Jul 12 01:07:31 shippou kernel: [   24.447196] ata2: SATA link down (SStatus 0 SControl 300)
Jul 12 01:07:31 shippou kernel: [   24.758657] ata3: SATA link down (SStatus 0 SControl 300)
Jul 12 01:07:31 shippou kernel: [   25.070118] ata4: SATA link down (SStatus 0 SControl 300)
Jul 12 01:07:31 shippou kernel: [   25.070238] scsi 0:0:0:0: Direct-Access     ATA      ST380215AS       3.AA PQ: 0 ANSI: 5
Jul 12 01:07:31 shippou kernel: [   25.071682] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 01:07:31 shippou kernel: [   25.071801] ohci_hcd 0000:00:13.0: OHCI Host Controller
Jul 12 01:07:31 shippou kernel: [   25.072079] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Jul 12 01:07:31 shippou kernel: [   25.072099] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02e000
Jul 12 01:07:31 shippou kernel: [   25.079190] Driver 'sd' needs updating - please use bus_type methods
Jul 12 01:07:31 shippou kernel: [   25.086145] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jul 12 01:07:31 shippou kernel: [   25.086159] sd 0:0:0:0: [sda] Write Protect is off
Jul 12 01:07:31 shippou kernel: [   25.086177] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 12 01:07:31 shippou kernel: [   25.086229] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jul 12 01:07:31 shippou kernel: [   25.086237] sd 0:0:0:0: [sda] Write Protect is off
Jul 12 01:07:31 shippou kernel: [   25.086253] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 12 01:07:31 shippou kernel: [   25.086257]  sda: sda1 sda2 sda3 sda4
Jul 12 01:07:31 shippou kernel: [   25.130261] usb usb1: configuration #1 chosen from 1 choice
Jul 12 01:07:31 shippou kernel: [   25.130286] hub 1-0:1.0: USB hub found
Jul 12 01:07:31 shippou kernel: [   25.130296] hub 1-0:1.0: 2 ports detected
Jul 12 01:07:31 shippou kernel: [   25.136035] sd 0:0:0:0: [sda] Attached SCSI disk
Jul 12 01:07:31 shippou kernel: [   25.141773] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 12 01:07:31 shippou kernel: [   25.233935] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 17
Jul 12 01:07:31 shippou kernel: [   25.234090] ohci_hcd 0000:00:13.1: OHCI Host Controller
Jul 12 01:07:31 shippou kernel: [   25.234156] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Jul 12 01:07:31 shippou kernel: [   25.234181] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfe02d000
Jul 12 01:07:31 shippou kernel: [   25.293975] usb usb2: configuration #1 chosen from 1 choice
Jul 12 01:07:31 shippou kernel: [   25.294000] hub 2-0:1.0: USB hub found
Jul 12 01:07:31 shippou kernel: [   25.294010] hub 2-0:1.0: 2 ports detected
Jul 12 01:07:31 shippou kernel: [   25.397659] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 18
Jul 12 01:07:31 shippou kernel: [   25.397772] ohci_hcd 0000:00:13.2: OHCI Host Controller
Jul 12 01:07:31 shippou kernel: [   25.397834] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
Jul 12 01:07:31 shippou kernel: [   25.397858] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfe02c000
Jul 12 01:07:31 shippou kernel: [   25.457699] usb usb3: configuration #1 chosen from 1 choice
Jul 12 01:07:31 shippou kernel: [   25.457734] hub 3-0:1.0: USB hub found
Jul 12 01:07:31 shippou kernel: [   25.457743] hub 3-0:1.0: 2 ports detected
Jul 12 01:07:31 shippou kernel: [   25.561374] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 17
Jul 12 01:07:31 shippou kernel: [   25.561570] ohci_hcd 0000:00:13.3: OHCI Host Controller
Jul 12 01:07:31 shippou kernel: [   25.561631] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
Jul 12 01:07:31 shippou kernel: [   25.561650] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfe02b000
Jul 12 01:07:31 shippou kernel: [   25.576120] Attempting manual resume
Jul 12 01:07:31 shippou kernel: [   25.621397] usb usb4: configuration #1 chosen from 1 choice
Jul 12 01:07:31 shippou kernel: [   25.621424] hub 4-0:1.0: USB hub found
Jul 12 01:07:31 shippou kernel: [   25.621433] hub 4-0:1.0: 2 ports detected
Jul 12 01:07:31 shippou kernel: [   25.623397] kjournald starting.  Commit interval 5 seconds
Jul 12 01:07:31 shippou kernel: [   25.623407] EXT3-fs: mounted filesystem with ordered data mode.
Jul 12 01:07:31 shippou kernel: [   25.725078] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 18
Jul 12 01:07:31 shippou kernel: [   25.725267] ohci_hcd 0000:00:13.4: OHCI Host Controller
Jul 12 01:07:31 shippou kernel: [   25.725328] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
Jul 12 01:07:31 shippou kernel: [   25.725346] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfe02a000
Jul 12 01:07:31 shippou kernel: [   25.785119] usb usb5: configuration #1 chosen from 1 choice
Jul 12 01:07:31 shippou kernel: [   25.785143] hub 5-0:1.0: USB hub found
Jul 12 01:07:31 shippou kernel: [   25.785152] hub 5-0:1.0: 2 ports detected
Jul 12 01:07:31 shippou kernel: [   25.888972] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 19
Jul 12 01:07:31 shippou kernel: [   25.889113] ehci_hcd 0000:00:13.5: EHCI Host Controller
Jul 12 01:07:31 shippou kernel: [   25.889175] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
Jul 12 01:07:31 shippou kernel: [   25.889216] ehci_hcd 0000:00:13.5: debug port 1
Jul 12 01:07:31 shippou kernel: [   25.889235] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfe029000
Jul 12 01:07:31 shippou kernel: [   25.900686] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jul 12 01:07:31 shippou kernel: [   25.900816] usb usb6: configuration #1 chosen from 1 choice
Jul 12 01:07:31 shippou kernel: [   25.900841] hub 6-0:1.0: USB hub found
Jul 12 01:07:31 shippou kernel: [   25.900848] hub 6-0:1.0: 10 ports detected
Jul 12 01:07:31 shippou kernel: [   26.004744] SB600_PATA: IDE controller (0x1002:0x438c rev 0x00) at  PCI slot 0000:00:14.1
Jul 12 01:07:31 shippou kernel: [   26.004756] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 01:07:31 shippou kernel: [   26.004767] SB600_PATA: not 100% native mode: will probe irqs later
Jul 12 01:07:31 shippou kernel: [   26.004775]     ide0: BM-DMA at 0xf900-0xf907, BIOS settings: hda:pio, hdb:DMA
Jul 12 01:07:31 shippou kernel: [   26.791459] hdb: LITE-ON DVDRW LH-20A1P, ATAPI CD/DVD-ROM drive
Jul 12 01:07:31 shippou kernel: [   27.070989] hdb: UDMA/66 mode selected
Jul 12 01:07:31 shippou kernel: [   27.071365] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Jul 12 01:07:31 shippou kernel: [   27.084263] r8169 Gigabit Ethernet driver 2.2LK loaded
Jul 12 01:07:31 shippou kernel: [   27.084298] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 22 (level, low) -> IRQ 22
Jul 12 01:07:31 shippou kernel: [   27.084526] eth0: RTL8169sc/8110sc at 0xffffc20001044000, 00:19:21:21:21:b5, XID 18000000 IRQ 22
Jul 12 01:07:31 shippou kernel: [   33.236887] input: PC Speaker as /devices/platform/pcspkr/input/input2
Jul 12 01:07:31 shippou kernel: [   33.539482] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 12 01:07:31 shippou kernel: [   33.580016] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul 12 01:07:31 shippou kernel: [   33.616906] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Jul 12 01:07:31 shippou kernel: [   33.763210] input: Power Button (FF) as /devices/virtual/input/input3
Jul 12 01:07:31 shippou kernel: [   33.791052] ACPI: Power Button (FF) [PWRF]
Jul 12 01:07:31 shippou kernel: [   33.791108] input: Power Button (CM) as /devices/virtual/input/input4
Jul 12 01:07:31 shippou kernel: [   33.815054] ACPI: Power Button (CM) [PWRB]
Jul 12 01:07:31 shippou kernel: [   33.900051] input: ImExPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Jul 12 01:07:31 shippou kernel: [   33.925481] parport_pc 00:0a: reported by Plug and Play ACPI
Jul 12 01:07:31 shippou kernel: [   33.925575] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jul 12 01:07:31 shippou kernel: [   35.289529] r8169: eth0: link up
Jul 12 01:07:31 shippou kernel: [   35.406779] hdb: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
Jul 12 01:07:31 shippou kernel: [   35.406787] Uniform CD-ROM driver Revision: 3.20
Jul 12 01:07:31 shippou kernel: [   35.558089] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 01:07:31 shippou kernel: [   35.581771] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
Jul 12 01:07:31 shippou kernel: [   35.759714] NET: Registered protocol family 10
Jul 12 01:07:31 shippou kernel: [   35.759922] lo: Disabled Privacy Extensions
Jul 12 01:07:31 shippou kernel: [   37.521506] lp0: using parport0 (interrupt-driven).
Jul 12 01:07:31 shippou kernel: [   37.614350] Adding 289160k swap on /dev/sda3.  Priority:-1 extents:1 across:289160k
Jul 12 01:07:31 shippou kernel: [   38.169472] EXT3 FS on sda2, internal journal
Jul 12 01:07:31 shippou kernel: [   39.085378] kjournald starting.  Commit interval 5 seconds
Jul 12 01:07:31 shippou kernel: [   39.085578] EXT3 FS on sda4, internal journal
Jul 12 01:07:31 shippou kernel: [   39.085582] EXT3-fs: mounted filesystem with ordered data mode.
Jul 12 01:07:31 shippou kernel: [   39.570994] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul 12 01:07:31 shippou kernel: [   40.043666] No dock devices found.
Jul 12 01:07:31 shippou kernel: [   40.303198] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (1 cpu cores) (version 2.20.00)
Jul 12 01:07:31 shippou kernel: [   40.303237] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
Jul 12 01:07:31 shippou kernel: [   40.303239] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
Jul 12 01:07:31 shippou kernel: [   41.134157] ppdev: user-space parallel port driver
Jul 12 01:07:32 shippou kernel: [   41.628113] audit(1215796052.130:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4784 profile="/usr/sbin/cupsd" namespace="default"
Jul 12 01:07:32 shippou dhcdbd: Started up.
Jul 12 01:07:34 shippou kernel: [   43.538258] Marking TSC unstable due to cpufreq changes
Jul 12 01:07:34 shippou kernel: [   43.542094] Time: hpet clocksource has been installed.
Jul 12 01:07:34 shippou kernel: [   43.678516] Bluetooth: Core ver 2.11
Jul 12 01:07:34 shippou kernel: [   43.679104] NET: Registered protocol family 31
Jul 12 01:07:34 shippou kernel: [   43.679109] Bluetooth: HCI device and connection manager initialized
Jul 12 01:07:34 shippou kernel: [   43.679113] Bluetooth: HCI socket layer initialized
Jul 12 01:07:34 shippou kernel: [   43.710938] Bluetooth: L2CAP ver 2.9
Jul 12 01:07:34 shippou kernel: [   43.710942] Bluetooth: L2CAP socket layer initialized
Jul 12 01:07:34 shippou kernel: [   43.765113] Bluetooth: RFCOMM socket layer initialized
Jul 12 01:07:34 shippou kernel: [   43.765130] Bluetooth: RFCOMM TTY layer initialized
Jul 12 01:07:34 shippou kernel: [   43.765132] Bluetooth: RFCOMM ver 1.8
Jul 12 01:07:34 shippou kernel: [   43.841595] Clocksource tsc unstable (delta = -222234238 ns)
Jul 12 01:07:36 shippou kernel: [   44.941979] [drm] Initialized drm 1.1.0 20060810
Jul 12 01:07:43 shippou kernel: [   48.628839] hda-intel: Invalid position buffer, using LPIB read method instead.
Jul 12 01:07:59 shippou kernel: [   58.337320] r8169: eth0: link down
Jul 12 01:08:01 shippou kernel: [   59.760311] r8169: eth0: link up
Jul 12 01:12:27 shippou kernel: [  217.930296] usb 6-6: new high speed USB device using ehci_hcd and address 2
Jul 12 01:12:27 shippou kernel: [  218.006737] usb 6-6: configuration #1 chosen from 1 choice
Jul 12 01:12:27 shippou kernel: [  218.098551] usbcore: registered new interface driver libusual
Jul 12 01:12:27 shippou kernel: [  218.121089] Initializing USB Mass Storage driver...
Jul 12 01:12:27 shippou kernel: [  218.123775] scsi4 : SCSI emulation for USB Mass Storage devices
Jul 12 01:12:27 shippou kernel: [  218.127743] usbcore: registered new interface driver usb-storage
Jul 12 01:12:27 shippou kernel: [  218.127749] USB Mass Storage support registered.
Jul 12 01:12:32 shippou kernel: [  220.901272] scsi scan: INQUIRY result too short (5), using 36
Jul 12 01:12:32 shippou kernel: [  220.901278] scsi 4:0:0:0: Direct-Access     USB 2.0  (HS) Flash Disk  1.00 PQ: 0 ANSI: 0 CCS
Jul 12 01:12:32 shippou kernel: [  220.907363] sd 4:0:0:0: [sdb] 1993649 512-byte hardware sectors (1021 MB)
Jul 12 01:12:32 shippou kernel: [  220.907858] sd 4:0:0:0: [sdb] Write Protect is off
Jul 12 01:12:32 shippou kernel: [  220.909093] sd 4:0:0:0: [sdb] 1993649 512-byte hardware sectors (1021 MB)
Jul 12 01:12:32 shippou kernel: [  220.909371] sd 4:0:0:0: [sdb] Write Protect is off
Jul 12 01:12:32 shippou kernel: [  220.909380]  sdb: unknown partition table
Jul 12 01:12:32 shippou kernel: [  220.913846] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Jul 12 01:12:32 shippou kernel: [  220.913889] sd 4:0:0:0: Attached scsi generic sg1 type 0
Jul 12 01:27:30 shippou -- MARK --
Jul 12 01:39:43 shippou kernel: [ 1671.913548] usb 6-6: USB disconnect, address 2
Jul 12 01:39:43 shippou kernel: [ 1672.025680] usb 6-6: new high speed USB device using ehci_hcd and address 3
Jul 12 01:39:43 shippou kernel: [ 1672.159716] usb 6-6: configuration #1 chosen from 1 choice
Jul 12 01:39:43 shippou kernel: [ 1672.197243] scsi5 : SCSI emulation for USB Mass Storage devices
Jul 12 01:39:45 shippou kernel: [ 1674.682773] usb 6-6: USB disconnect, address 3
Jul 12 01:39:46 shippou kernel: [ 1674.792867] usb 6-6: new high speed USB device using ehci_hcd and address 4
Jul 12 01:39:46 shippou kernel: [ 1674.925958] usb 6-6: configuration #1 chosen from 1 choice
Jul 12 01:39:46 shippou kernel: [ 1674.950671] scsi6 : SCSI emulation for USB Mass Storage devices
Jul 12 01:39:47 shippou kernel: [ 1676.160827] usb 6-6: USB disconnect, address 4
Jul 12 01:39:47 shippou kernel: [ 1676.274299] usb 6-6: new high speed USB device using ehci_hcd and address 5
Jul 12 01:39:48 shippou kernel: [ 1676.817365] usb 6-6: new high speed USB device using ehci_hcd and address 6
Jul 12 01:39:48 shippou kernel: [ 1677.064940] usb 6-6: new high speed USB device using ehci_hcd and address 7
Jul 12 01:39:48 shippou kernel: [ 1677.424315] usb 6-6: new high speed USB device using ehci_hcd and address 8
Jul 12 01:39:48 shippou kernel: [ 1677.445679] usb 6-6: configuration #1 chosen from 1 choice
Jul 12 01:39:48 shippou kernel: [ 1677.482567] scsi7 : SCSI emulation for USB Mass Storage devices
Jul 12 01:39:48 shippou kernel: [ 1677.695121] usb 6-6: USB disconnect, address 8
Jul 12 01:39:49 shippou kernel: [ 1677.807660] usb 6-6: new high speed USB device using ehci_hcd and address 9
Jul 12 01:39:49 shippou kernel: [ 1677.940791] usb 6-6: configuration #1 chosen from 1 choice
Jul 12 01:39:49 shippou kernel: [ 1677.975776] scsi8 : SCSI emulation for USB Mass Storage devices
Jul 12 01:39:49 shippou kernel: [ 1678.178886] usb 6-6: USB disconnect, address 9
Jul 12 01:39:49 shippou kernel: [ 1678.294205] usb 6-6: new high speed USB device using ehci_hcd and address 10
Jul 12 01:39:49 shippou kernel: [ 1678.425524] usb 6-6: configuration #1 chosen from 1 choice
Jul 12 01:39:49 shippou kernel: [ 1678.458120] scsi9 : SCSI emulation for USB Mass Storage devices
Jul 12 01:39:49 shippou kernel: [ 1678.507354] usb 6-6: USB disconnect, address 10
Jul 12 01:39:49 shippou kernel: [ 1678.622234] usb 6-6: new high speed USB device using ehci_hcd and address 11
Jul 12 01:39:50 shippou kernel: [ 1678.979189] usb 6-6: configuration #1 chosen from 1 choice
Jul 12 01:39:50 shippou kernel: [ 1679.015091] scsi10 : SCSI emulation for USB Mass Storage devices
Jul 12 01:39:55 shippou kernel: [ 1684.017820] scsi scan: INQUIRY result too short (5), using 36
Jul 12 01:39:55 shippou kernel: [ 1684.017826] scsi 10:0:0:0: Direct-Access     USB 2.0  (HS) Flash Disk  1.00 PQ: 0 ANSI: 0 CCS
Jul 12 01:39:55 shippou kernel: [ 1684.030171] sd 10:0:0:0: [sdb] 1993649 512-byte hardware sectors (1021 MB)
Jul 12 01:39:55 shippou kernel: [ 1684.030925] sd 10:0:0:0: [sdb] Write Protect is off
Jul 12 01:39:55 shippou kernel: [ 1684.033412] sd 10:0:0:0: [sdb] 1993649 512-byte hardware sectors (1021 MB)
Jul 12 01:39:55 shippou kernel: [ 1684.033906] sd 10:0:0:0: [sdb] Write Protect is off
Jul 12 01:39:55 shippou kernel: [ 1684.033918]  sdb: unknown partition table
Jul 12 01:39:55 shippou kernel: [ 1684.052924] sd 10:0:0:0: [sdb] Attached SCSI removable disk
Jul 12 01:39:55 shippou kernel: [ 1684.052971] sd 10:0:0:0: Attached scsi generic sg1 type 0
Jul 12 02:07:31 shippou -- MARK --
Jul 12 02:27:31 shippou -- MARK --
Jul 12 02:34:32 shippou kernel: [ 4946.691001] usb 6-6: USB disconnect, address 11
Jul 12 02:34:32 shippou kernel: [ 4946.806933] usb 6-6: new high speed USB device using ehci_hcd and address 12
Jul 12 02:34:33 shippou kernel: [ 4947.435900] usb 6-6: new high speed USB device using ehci_hcd and address 13
Jul 12 02:34:33 shippou kernel: [ 4947.978959] usb 6-6: new high speed USB device using ehci_hcd and address 14
Jul 12 02:34:34 shippou kernel: [ 4948.498054] usb 6-6: new high speed USB device using ehci_hcd and address 15
Jul 12 02:34:34 shippou kernel: [ 4948.519322] usb 6-6: configuration #1 chosen from 1 choice
Jul 12 02:34:34 shippou kernel: [ 4948.542656] scsi11 : SCSI emulation for USB Mass Storage devices
Jul 12 02:34:34 shippou kernel: [ 4948.562076] usb 6-6: USB disconnect, address 15
Jul 12 02:34:34 shippou kernel: [ 4948.679382] usb 6-6: new high speed USB device using ehci_hcd and address 16
Jul 12 02:34:34 shippou kernel: [ 4949.031149] usb 6-6: configuration #1 chosen from 1 choice
Jul 12 02:34:34 shippou kernel: [ 4949.068248] scsi12 : SCSI emulation for USB Mass Storage devices
Jul 12 02:34:35 shippou kernel: [ 4949.381577] usb 6-6: USB disconnect, address 16
Jul 12 02:34:35 shippou kernel: [ 4949.492329] usb 6-6: new high speed USB device using ehci_hcd and address 17
Jul 12 02:34:35 shippou kernel: [ 4950.123238] usb 6-6: new high speed USB device using ehci_hcd and address 18
Jul 12 02:34:36 shippou kernel: [ 4950.670305] usb 6-6: new high speed USB device using ehci_hcd and address 19
Jul 12 02:34:36 shippou kernel: [ 4951.189398] usb 6-6: new high speed USB device using ehci_hcd and address 20
Jul 12 02:47:31 shippou -- MARK --
Jul 12 02:59:17 shippou kernel: [ 6418.024290] gvfs-fuse-daemo[5379] general protection rip:7f1004a06423 rsp:7fff0e62ed30 error:0
Jul 12 02:59:21 shippou kernel: [ 6421.765415] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jul 12 02:59:22 shippou exiting on signal 15
Jul 12 11:23:01 shippou syslogd 1.5.0#1ubuntu1: restart.
Jul 12 11:23:01 shippou kernel: Inspecting /boot/System.map-2.6.24-19-generic
Jul 12 11:23:01 shippou kernel: Loaded 28491 symbols from /boot/System.map-2.6.24-19-generic.
Jul 12 11:23:01 shippou kernel: Symbols match kernel version 2.6.24.
Jul 12 11:23:01 shippou kernel: Loaded 17426 symbols from 79 modules.
Jul 12 11:23:01 shippou kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 12 11:23:01 shippou kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 12 11:23:01 shippou kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:15:37 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
Jul 12 11:23:01 shippou kernel: [    0.000000] Command line: root=UUID=2e985bef-5550-421f-b1bf-e1f730273cbc ro quiet splash
Jul 12 11:23:01 shippou kernel: [    0.000000] BIOS-provided physical RAM map:
Jul 12 11:23:01 shippou kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jul 12 11:23:01 shippou kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jul 12 11:23:01 shippou kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jul 12 11:23:01 shippou kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000097fe0000 (usable)
Jul 12 11:23:01 shippou kernel: [    0.000000]  BIOS-e820: 0000000097fe0000 - 0000000097fe3000 (ACPI NVS)
Jul 12 11:23:01 shippou kernel: [    0.000000]  BIOS-e820: 0000000097fe3000 - 0000000097ff0000 (ACPI data)
Jul 12 11:23:01 shippou kernel: [    0.000000]  BIOS-e820: 0000000097ff0000 - 0000000098000000 (reserved)
Jul 12 11:23:01 shippou kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Jul 12 11:23:01 shippou kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Jul 12 11:23:01 shippou kernel: [    0.000000] end_pfn_map = 1048576
Jul 12 11:23:01 shippou kernel: [    0.000000] DMI 2.5 present.
Jul 12 11:23:01 shippou kernel: [    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F7B80 checksum 0
Jul 12 11:23:01 shippou kernel: [    0.000000] ACPI: RSDP 000F7B80, 0024 (r2 RS690 )
Jul 12 11:23:01 shippou kernel: [    0.000000] ACPI: RSDT 97FE3040, 0038 (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 12 11:23:01 shippou kernel: [    0.000000] ACPI: FACP 97FE30C0, 0074 (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 12 11:23:01 shippou kernel: [    0.000000] ACPI: DSDT 97FE3180, 4B0B (r1 RS690  AWRDACPI     1000 MSFT  3000000)
Jul 12 11:23:01 shippou kernel: [    0.000000] ACPI: FACS 97FE0000, 0040
Jul 12 11:23:01 shippou kernel: [    0.000000] ACPI: SSDT 97FE7DC0, 00D3 (r1 PTLTD  POWERNOW        1  LTP        1)
Jul 12 11:23:01 shippou kernel: [    0.000000] ACPI: HPET 97FE7F00, 0038 (r1 RS690  AWRDACPI 42302E31 AWRD       98)
Jul 12 11:23:01 shippou kernel: [    0.000000] ACPI: MCFG 97FE7F80, 003C (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 12 11:23:01 shippou kernel: [    0.000000] ACPI: APIC 97FE7D00, 0068 (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 12 11:23:01 shippou kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Jul 12 11:23:01 shippou kernel: [    0.000000] CPU has 1 num_cores
Jul 12 11:23:01 shippou kernel: [    0.000000] No NUMA configuration found
Jul 12 11:23:01 shippou kernel: [    0.000000] Faking a node at 0000000000000000-0000000097fe0000
Jul 12 11:23:01 shippou kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000097fe0000
Jul 12 11:23:01 shippou kernel: [    0.000000] Zone PFN ranges:
Jul 12 11:23:01 shippou kernel: [    0.000000]   DMA             0 ->     4096
Jul 12 11:23:01 shippou kernel: [    0.000000]   DMA32        4096 ->  1048576
Jul 12 11:23:01 shippou kernel: [    0.000000]   Normal    1048576 ->  1048576
Jul 12 11:23:01 shippou kernel: [    0.000000] Movable zone start PFN for each node
Jul 12 11:23:01 shippou kernel: [    0.000000] early_node_map[2] active PFN ranges
Jul 12 11:23:01 shippou kernel: [    0.000000]     0:        0 ->      159
Jul 12 11:23:01 shippou kernel: [    0.000000]     0:      256 ->   622560
Jul 12 11:23:01 shippou kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Jul 12 11:23:01 shippou kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Jul 12 11:23:01 shippou kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul 12 11:23:01 shippou kernel: [    0.000000] Processor #0 (Bootup-CPU)
Jul 12 11:23:01 shippou kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Jul 12 11:23:01 shippou kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul 12 11:23:01 shippou kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jul 12 11:23:01 shippou kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jul 12 11:23:01 shippou kernel: [    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
Jul 12 11:23:01 shippou kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 12 11:23:01 shippou kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jul 12 11:23:01 shippou kernel: [    0.000000] Setting APIC routing to flat
Jul 12 11:23:01 shippou kernel: [    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
Jul 12 11:23:01 shippou kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 12 11:23:01 shippou kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Jul 12 11:23:01 shippou kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Jul 12 11:23:01 shippou kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Jul 12 11:23:01 shippou kernel: [    0.000000] Allocating PCI resources starting at a0000000 (gap: 98000000:48000000)
Jul 12 11:23:01 shippou kernel: [    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
Jul 12 11:23:01 shippou kernel: [    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
Jul 12 11:23:01 shippou kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 612716
Jul 12 11:23:01 shippou kernel: [    0.000000] Policy zone: DMA32
Jul 12 11:23:01 shippou kernel: [    0.000000] Kernel command line: root=UUID=2e985bef-5550-421f-b1bf-e1f730273cbc ro quiet splash
Jul 12 11:23:01 shippou kernel: [    0.000000] Initializing CPU#0
Jul 12 11:23:01 shippou kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Jul 12 11:23:01 shippou kernel: [    0.000000] TSC calibrated against HPET
Jul 12 11:23:01 shippou kernel: [   12.308463] time.c: Detected 1799.794 MHz processor.
Jul 12 11:23:01 shippou kernel: [   12.309152] Console: colour VGA+ 80x25
Jul 12 11:23:01 shippou kernel: [   12.309155] console [tty0] enabled
Jul 12 11:23:01 shippou kernel: [   12.309171] Checking aperture...
Jul 12 11:23:01 shippou kernel: [   12.309174] CPU 0: aperture @ ffc0000000 size 32 MB
Jul 12 11:23:01 shippou kernel: [   12.309176] Aperture too small (32 MB)
Jul 12 11:23:01 shippou kernel: [   12.318986] No AGP bridge found
Jul 12 11:23:01 shippou kernel: [   12.352393] Memory: 2442456k/2490240k available (2489k kernel code, 47396k reserved, 1318k data, 320k init)
Jul 12 11:23:01 shippou kernel: [   12.352433] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Jul 12 11:23:01 shippou kernel: [   12.430471] Calibrating delay using timer specific routine.. 3709.20 BogoMIPS (lpj=7418412)
Jul 12 11:23:01 shippou kernel: [   12.430518] Security Framework initialized
Jul 12 11:23:01 shippou kernel: [   12.430524] SELinux:  Disabled at boot.
Jul 12 11:23:01 shippou kernel: [   12.430537] AppArmor: AppArmor initialized
Jul 12 11:23:01 shippou kernel: [   12.430541] Failure registering capabilities with primary security module.
Jul 12 11:23:01 shippou kernel: [   12.430920] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jul 12 11:23:01 shippou kernel: [   12.434943] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jul 12 11:23:01 shippou kernel: [   12.436566] Mount-cache hash table entries: 256
Jul 12 11:23:01 shippou kernel: [   12.436716] Initializing cgroup subsys ns
Jul 12 11:23:01 shippou kernel: [   12.436720] Initializing cgroup subsys cpuacct
Jul 12 11:23:01 shippou kernel: [   12.436735] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jul 12 11:23:01 shippou kernel: [   12.436737] CPU: L2 Cache: 512K (64 bytes/line)
Jul 12 11:23:01 shippou kernel: [   12.436740] CPU 0/0 -> Node 0
Jul 12 11:23:01 shippou kernel: [   12.436768] SMP alternatives: switching to UP code
Jul 12 11:23:01 shippou kernel: [   12.437453] Early unpacking initramfs... done
Jul 12 11:23:01 shippou kernel: [   12.838334] ACPI: Core revision 20070126
Jul 12 11:23:01 shippou kernel: [   12.838396] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Jul 12 11:23:01 shippou kernel: [   12.887858] Using local APIC timer interrupts.
Jul 12 11:23:01 shippou kernel: [   12.943336] Detected 12.498 MHz APIC timer.
Jul 12 11:23:01 shippou kernel: [   12.943385] Brought up 1 CPUs
Jul 12 11:23:01 shippou kernel: [   12.943658] net_namespace: 120 bytes
Jul 12 11:23:01 shippou kernel: [   12.944059] Time: 11:22:40  Date: 07/12/08
Jul 12 11:23:01 shippou kernel: [   12.944088] NET: Registered protocol family 16
Jul 12 11:23:01 shippou kernel: [   12.944260] ACPI: bus type pci registered
Jul 12 11:23:01 shippou kernel: [   12.944328] PCI: Using configuration type 1
Jul 12 11:23:01 shippou kernel: [   12.951034] ACPI: Interpreter enabled
Jul 12 11:23:01 shippou kernel: [   12.951040] ACPI: (supports S0 S3 S4 S5)
Jul 12 11:23:01 shippou kernel: [   12.951056] ACPI: Using IOAPIC for interrupt routing
Jul 12 11:23:01 shippou kernel: [   12.956244] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul 12 11:23:01 shippou kernel: [   12.956405] pci 0000:00:12.0: set SATA to AHCI mode
Jul 12 11:23:01 shippou kernel: [   12.957205] PCI: Transparent bridge - 0000:00:14.4
Jul 12 11:23:01 shippou kernel: [   12.977943] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 11:23:01 shippou kernel: [   12.978048] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 11:23:01 shippou kernel: [   12.978152] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 11:23:01 shippou kernel: [   12.978255] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 11:23:01 shippou kernel: [   12.978358] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 11:23:01 shippou kernel: [   12.978461] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 11:23:01 shippou kernel: [   12.978564] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 11:23:01 shippou kernel: [   12.978667] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 11:23:01 shippou kernel: [   12.978782] Linux Plug and Play Support v0.97 (c) Adam Belay
Jul 12 11:23:01 shippou kernel: [   12.978811] pnp: PnP ACPI init
Jul 12 11:23:01 shippou kernel: [   12.978820] ACPI: bus type pnp registered
Jul 12 11:23:01 shippou kernel: [   12.981839] pnp: PnP ACPI: found 15 devices
Jul 12 11:23:01 shippou kernel: [   12.981842] ACPI: ACPI bus type pnp unregistered
Jul 12 11:23:01 shippou kernel: [   12.982071] PCI: Using ACPI for IRQ routing
Jul 12 11:23:01 shippou kernel: [   12.982074] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jul 12 11:23:01 shippou kernel: [   12.995291] NET: Registered protocol family 8
Jul 12 11:23:01 shippou kernel: [   12.995293] NET: Registered protocol family 20
Jul 12 11:23:01 shippou kernel: [   12.995373] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Jul 12 11:23:01 shippou kernel: [   12.995378] hpet0: 4 32-bit timers, 14318180 Hz
Jul 12 11:23:01 shippou kernel: [   12.996430] AppArmor: AppArmor Filesystem Enabled
Jul 12 11:23:01 shippou kernel: [   12.999250] Time: tsc clocksource has been installed.
Jul 12 11:23:01 shippou kernel: [   13.007233] system 00:01: ioport range 0x4100-0x411f has been reserved
Jul 12 11:23:01 shippou kernel: [   13.007236] system 00:01: ioport range 0x228-0x22f has been reserved
Jul 12 11:23:01 shippou kernel: [   13.007240] system 00:01: ioport range 0x40b-0x40b has been reserved
Jul 12 11:23:01 shippou kernel: [   13.007243] system 00:01: ioport range 0x4d6-0x4d6 has been reserved
Jul 12 11:23:01 shippou kernel: [   13.007246] system 00:01: ioport range 0xc00-0xc01 has been reserved
Jul 12 11:23:01 shippou kernel: [   13.007249] system 00:01: ioport range 0xc14-0xc14 has been reserved
Jul 12 11:23:01 shippou kernel: [   13.007252] system 00:01: ioport range 0xc50-0xc52 has been reserved
Jul 12 11:23:01 shippou kernel: [   13.007255] system 00:01: ioport range 0xc6c-0xc6d has been reserved
Jul 12 11:23:01 shippou kernel: [   13.007258] system 00:01: ioport range 0xc6f-0xc6f has been reserved
Jul 12 11:23:01 shippou kernel: [   13.007261] system 00:01: ioport range 0xcd0-0xcd1 has been reserved
Jul 12 11:23:01 shippou kernel: [   13.007264] system 00:01: ioport range 0xcd2-0xcd3 has been reserved
Jul 12 11:23:01 shippou kernel: [   13.007267] system 00:01: ioport range 0xcd4-0xcdf has been reserved
Jul 12 11:23:01 shippou kernel: [   13.007270] system 00:01: ioport range 0x4000-0x40fe has been reserved
Jul 12 11:23:01 shippou kernel: [   13.007273] system 00:01: ioport range 0x4210-0x4217 has been reserved
Jul 12 11:23:01 shippou kernel: [   13.007276] system 00:01: ioport range 0xb10-0xb1f has been reserved
Jul 12 11:23:01 shippou kernel: [   13.007285] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
Jul 12 11:23:01 shippou kernel: [   13.007288] system 00:07: ioport range 0x220-0x225 has been reserved
Jul 12 11:23:01 shippou kernel: [   13.007291] system 00:07: ioport range 0xb00-0xb0f has been reserved
Jul 12 11:23:01 shippou kernel: [   13.007301] system 00:0d: iomem range 0xe0000000-0xefffffff could not be reserved
Jul 12 11:23:01 shippou kernel: [   13.007307] system 00:0e: iomem range 0xf0000-0xfffff could not be reserved
Jul 12 11:23:01 shippou kernel: [   13.007310] system 00:0e: iomem range 0xfed00000-0xfed000ff has been reserved
Jul 12 11:23:01 shippou kernel: [   13.007314] system 00:0e: iomem range 0x97fe0000-0x97ffffff could not be reserved
Jul 12 11:23:01 shippou kernel: [   13.007317] system 00:0e: iomem range 0xffff0000-0xffffffff has been reserved
Jul 12 11:23:01 shippou kernel: [   13.007320] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
Jul 12 11:23:01 shippou kernel: [   13.007324] system 00:0e: iomem range 0x100000-0x97fdffff could not be reserved
Jul 12 11:23:01 shippou kernel: [   13.007327] system 00:0e: iomem range 0x98000000-0x9fffffff has been reserved
Jul 12 11:23:01 shippou kernel: [   13.007330] system 00:0e: iomem range 0xfec00000-0xfec00fff has been reserved
Jul 12 11:23:01 shippou kernel: [   13.007334] system 00:0e: iomem range 0xfee00000-0xfee00fff could not be reserved
Jul 12 11:23:01 shippou kernel: [   13.007337] system 00:0e: iomem range 0xfff80000-0xfffeffff has been reserved
Jul 12 11:23:01 shippou kernel: [   13.007693] PCI: Bridge: 0000:00:01.0
Jul 12 11:23:01 shippou kernel: [   13.007696]   IO window: e000-efff
Jul 12 11:23:01 shippou kernel: [   13.007699]   MEM window: fdd00000-fdefffff
Jul 12 11:23:01 shippou kernel: [   13.007701]   PREFETCH window: d8000000-dfffffff
Jul 12 11:23:01 shippou kernel: [   13.007706] PCI: Bridge: 0000:00:14.4
Jul 12 11:23:01 shippou kernel: [   13.007709]   IO window: d000-dfff
Jul 12 11:23:01 shippou kernel: [   13.007713]   MEM window: fdc00000-fdcfffff
Jul 12 11:23:01 shippou kernel: [   13.007717]   PREFETCH window: fdf00000-fdffffff
Jul 12 11:23:01 shippou kernel: [   13.007741] NET: Registered protocol family 2
Jul 12 11:23:01 shippou kernel: [   13.043291] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Jul 12 11:23:01 shippou kernel: [   13.044921] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Jul 12 11:23:01 shippou kernel: [   13.052229] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jul 12 11:23:01 shippou kernel: [   13.053106] TCP: Hash tables configured (established 524288 bind 65536)
Jul 12 11:23:01 shippou kernel: [   13.053110] TCP reno registered
Jul 12 11:23:01 shippou kernel: [   13.063268] checking if image is initramfs... it is
Jul 12 11:23:01 shippou kernel: [   13.767929] Freeing initrd memory: 8212k freed
Jul 12 11:23:01 shippou kernel: [   13.775025] audit: initializing netlink socket (disabled)
Jul 12 11:23:01 shippou kernel: [   13.775039] audit(1215861760.416:1): initialized
Jul 12 11:23:01 shippou kernel: [   13.777014] VFS: Disk quotas dquot_6.5.1
Jul 12 11:23:01 shippou kernel: [   13.777085] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jul 12 11:23:01 shippou kernel: [   13.777228] io scheduler noop registered
Jul 12 11:23:01 shippou kernel: [   13.777230] io scheduler anticipatory registered
Jul 12 11:23:01 shippou kernel: [   13.777232] io scheduler deadline registered
Jul 12 11:23:01 shippou kernel: [   13.777336] io scheduler cfq registered (default)
Jul 12 11:23:01 shippou kernel: [   13.946220] Real Time Clock Driver v1.12ac
Jul 12 11:23:01 shippou kernel: [   13.946445] Linux agpgart interface v0.102
Jul 12 11:23:01 shippou kernel: [   13.946448] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jul 12 11:23:01 shippou kernel: [   13.946597] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 12 11:23:01 shippou kernel: [   13.947196] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 12 11:23:01 shippou kernel: [   13.947898] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jul 12 11:23:01 shippou kernel: [   13.947967] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jul 12 11:23:01 shippou kernel: [   13.948056] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jul 12 11:23:01 shippou kernel: [   13.948391] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 12 11:23:01 shippou kernel: [   13.948396] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 12 11:23:01 shippou kernel: [   13.953814] mice: PS/2 mouse device common for all mice
Jul 12 11:23:01 shippou kernel: [   13.953848] cpuidle: using governor ladder
Jul 12 11:23:01 shippou kernel: [   13.953850] cpuidle: using governor menu
Jul 12 11:23:01 shippou kernel: [   13.953999] NET: Registered protocol family 1
Jul 12 11:23:01 shippou kernel: [   13.954096] registered taskstats version 1
Jul 12 11:23:01 shippou kernel: [   13.954214]   Magic number: 0:894:377
Jul 12 11:23:01 shippou kernel: [   13.954348]   hash matches device PNP0700:00
Jul 12 11:23:01 shippou kernel: [   13.954363] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
Jul 12 11:23:01 shippou kernel: [   13.954366] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 12 11:23:01 shippou kernel: [   13.954368] EDD information not available.
Jul 12 11:23:01 shippou kernel: [   13.954375] Freeing unused kernel memory: 320k freed
Jul 12 11:23:01 shippou kernel: [   13.981561] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jul 12 11:23:01 shippou kernel: [   15.154975] fuse init (API version 7.9)
Jul 12 11:23:01 shippou kernel: [   15.169535] ACPI: Fan [FAN] (on)
Jul 12 11:23:01 shippou kernel: [   15.176303] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Jul 12 11:23:01 shippou kernel: [   15.177696] ACPI: Thermal Zone [THRM] (40 C)
Jul 12 11:23:01 shippou kernel: [   15.714774] SCSI subsystem initialized
Jul 12 11:23:01 shippou kernel: [   15.794680] usbcore: registered new interface driver usbfs
Jul 12 11:23:01 shippou kernel: [   15.794702] usbcore: registered new interface driver hub
Jul 12 11:23:01 shippou kernel: [   15.802493] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 11:23:01 shippou kernel: [   15.802610] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
Jul 12 11:23:01 shippou kernel: [   15.802617] ahci 0000:00:12.0: controller can't do PMP, turning off CAP_PMP
Jul 12 11:23:01 shippou kernel: [   15.815944] usbcore: registered new device driver usb
Jul 12 11:23:01 shippou kernel: [   15.816973] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jul 12 11:23:01 shippou kernel: [   15.817977] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jul 12 11:23:01 shippou kernel: [   16.018165] Floppy drive(s): fd0 is 1.44M
Jul 12 11:23:01 shippou kernel: [   16.040055] FDC 0 is a post-1991 82077
Jul 12 11:23:01 shippou kernel: [   16.804680] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Jul 12 11:23:01 shippou kernel: [   16.804685] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pio slum part 
Jul 12 11:23:01 shippou kernel: [   16.805901] scsi0 : ahci
Jul 12 11:23:01 shippou kernel: [   16.806233] scsi1 : ahci
Jul 12 11:23:01 shippou kernel: [   16.806384] scsi2 : ahci
Jul 12 11:23:01 shippou kernel: [   16.806537] scsi3 : ahci
Jul 12 11:23:01 shippou kernel: [   16.806616] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 16
Jul 12 11:23:01 shippou kernel: [   16.806620] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 16
Jul 12 11:23:01 shippou kernel: [   16.806625] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 16
Jul 12 11:23:01 shippou kernel: [   16.806629] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 16
Jul 12 11:23:01 shippou kernel: [   17.279830] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 12 11:23:01 shippou kernel: [   17.323241] ata1.00: ATA-7: ST380215AS, 3.AAD, max UDMA/133
Jul 12 11:23:01 shippou kernel: [   17.323244] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32)
Jul 12 11:23:01 shippou kernel: [   17.381466] ata1.00: configured for UDMA/133
Jul 12 11:23:01 shippou kernel: [   17.691108] ata2: SATA link down (SStatus 0 SControl 300)
Jul 12 11:23:01 shippou kernel: [   18.002567] ata3: SATA link down (SStatus 0 SControl 300)
Jul 12 11:23:01 shippou kernel: [   18.314026] ata4: SATA link down (SStatus 0 SControl 300)
Jul 12 11:23:01 shippou kernel: [   18.314148] scsi 0:0:0:0: Direct-Access     ATA      ST380215AS       3.AA PQ: 0 ANSI: 5
Jul 12 11:23:01 shippou kernel: [   18.315597] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 11:23:01 shippou kernel: [   18.315713] ohci_hcd 0000:00:13.0: OHCI Host Controller
Jul 12 11:23:01 shippou kernel: [   18.315972] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Jul 12 11:23:01 shippou kernel: [   18.315992] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02e000
Jul 12 11:23:01 shippou kernel: [   18.323140] Driver 'sd' needs updating - please use bus_type methods
Jul 12 11:23:01 shippou kernel: [   18.330054] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jul 12 11:23:01 shippou kernel: [   18.330067] sd 0:0:0:0: [sda] Write Protect is off
Jul 12 11:23:01 shippou kernel: [   18.330084] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 12 11:23:01 shippou kernel: [   18.330136] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jul 12 11:23:01 shippou kernel: [   18.330144] sd 0:0:0:0: [sda] Write Protect is off
Jul 12 11:23:01 shippou kernel: [   18.330159] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 12 11:23:01 shippou kernel: [   18.330164]  sda: sda1 sda2 sda3 sda4
Jul 12 11:23:01 shippou kernel: [   18.374172] usb usb1: configuration #1 chosen from 1 choice
Jul 12 11:23:01 shippou kernel: [   18.374197] hub 1-0:1.0: USB hub found
Jul 12 11:23:01 shippou kernel: [   18.374206] hub 1-0:1.0: 2 ports detected
Jul 12 11:23:01 shippou kernel: [   18.381094] sd 0:0:0:0: [sda] Attached SCSI disk
Jul 12 11:23:01 shippou kernel: [   18.386503] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 12 11:23:01 shippou kernel: [   18.477843] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 17
Jul 12 11:23:01 shippou kernel: [   18.477979] ohci_hcd 0000:00:13.1: OHCI Host Controller
Jul 12 11:23:01 shippou kernel: [   18.478088] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Jul 12 11:23:01 shippou kernel: [   18.478133] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfe02d000
Jul 12 11:23:01 shippou kernel: [   18.537872] usb usb2: configuration #1 chosen from 1 choice
Jul 12 11:23:01 shippou kernel: [   18.537896] hub 2-0:1.0: USB hub found
Jul 12 11:23:01 shippou kernel: [   18.537905] hub 2-0:1.0: 2 ports detected
Jul 12 11:23:01 shippou kernel: [   18.641552] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 18
Jul 12 11:23:01 shippou kernel: [   18.641669] ohci_hcd 0000:00:13.2: OHCI Host Controller
Jul 12 11:23:01 shippou kernel: [   18.641733] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
Jul 12 11:23:01 shippou kernel: [   18.641756] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfe02c000
Jul 12 11:23:01 shippou kernel: [   18.701597] usb usb3: configuration #1 chosen from 1 choice
Jul 12 11:23:01 shippou kernel: [   18.701629] hub 3-0:1.0: USB hub found
Jul 12 11:23:01 shippou kernel: [   18.701638] hub 3-0:1.0: 2 ports detected
Jul 12 11:23:01 shippou kernel: [   18.805269] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 17
Jul 12 11:23:01 shippou kernel: [   18.805401] ohci_hcd 0000:00:13.3: OHCI Host Controller
Jul 12 11:23:01 shippou kernel: [   18.805467] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
Jul 12 11:23:01 shippou kernel: [   18.805487] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfe02b000
Jul 12 11:23:01 shippou kernel: [   18.829506] Attempting manual resume
Jul 12 11:23:01 shippou kernel: [   18.865305] usb usb4: configuration #1 chosen from 1 choice
Jul 12 11:23:01 shippou kernel: [   18.865331] hub 4-0:1.0: USB hub found
Jul 12 11:23:01 shippou kernel: [   18.865341] hub 4-0:1.0: 2 ports detected
Jul 12 11:23:01 shippou kernel: [   18.876764] kjournald starting.  Commit interval 5 seconds
Jul 12 11:23:01 shippou kernel: [   18.876774] EXT3-fs: mounted filesystem with ordered data mode.
Jul 12 11:23:01 shippou kernel: [   18.969004] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 18
Jul 12 11:23:01 shippou kernel: [   18.969191] ohci_hcd 0000:00:13.4: OHCI Host Controller
Jul 12 11:23:01 shippou kernel: [   18.969254] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
Jul 12 11:23:01 shippou kernel: [   18.969272] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfe02a000
Jul 12 11:23:01 shippou kernel: [   19.029025] usb usb5: configuration #1 chosen from 1 choice
Jul 12 11:23:01 shippou kernel: [   19.029050] hub 5-0:1.0: USB hub found
Jul 12 11:23:01 shippou kernel: [   19.029059] hub 5-0:1.0: 2 ports detected
Jul 12 11:23:01 shippou kernel: [   19.116631] usb 3-2: new full speed USB device using ohci_hcd and address 2
Jul 12 11:23:01 shippou kernel: [   19.132846] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 19
Jul 12 11:23:01 shippou kernel: [   19.132983] ehci_hcd 0000:00:13.5: EHCI Host Controller
Jul 12 11:23:01 shippou kernel: [   19.133045] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
Jul 12 11:23:01 shippou kernel: [   19.133087] ehci_hcd 0000:00:13.5: debug port 1
Jul 12 11:23:01 shippou kernel: [   19.133106] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfe029000
Jul 12 11:23:01 shippou kernel: [   19.316277] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jul 12 11:23:01 shippou kernel: [   19.316409] usb usb6: configuration #1 chosen from 1 choice
Jul 12 11:23:01 shippou kernel: [   19.316434] hub 6-0:1.0: USB hub found
Jul 12 11:23:01 shippou kernel: [   19.316440] hub 6-0:1.0: 10 ports detected
Jul 12 11:23:01 shippou kernel: [   19.420345] SB600_PATA: IDE controller (0x1002:0x438c rev 0x00) at  PCI slot 0000:00:14.1
Jul 12 11:23:01 shippou kernel: [   19.420359] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 11:23:01 shippou kernel: [   19.420371] SB600_PATA: not 100% native mode: will probe irqs later
Jul 12 11:23:01 shippou kernel: [   19.420379]     ide0: BM-DMA at 0xf900-0xf907, BIOS settings: hda:pio, hdb:DMA
Jul 12 11:23:01 shippou kernel: [   20.007080] usb 6-6: new high speed USB device using ehci_hcd and address 2
Jul 12 11:23:01 shippou kernel: [   20.140039] usb 6-6: configuration #1 chosen from 1 choice
Jul 12 11:23:01 shippou kernel: [   20.207066] hdb: LITE-ON DVDRW LH-20A1P, ATAPI CD/DVD-ROM drive
Jul 12 11:23:01 shippou kernel: [   20.486592] hdb: UDMA/66 mode selected
Jul 12 11:23:01 shippou kernel: [   20.486969] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Jul 12 11:23:01 shippou kernel: [   20.499883] r8169 Gigabit Ethernet driver 2.2LK loaded
Jul 12 11:23:01 shippou kernel: [   20.499921] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 22 (level, low) -> IRQ 22
Jul 12 11:23:01 shippou kernel: [   20.500155] eth0: RTL8169sc/8110sc at 0xffffc20001044000, 00:19:21:21:21:b5, XID 18000000 IRQ 22
Jul 12 11:23:01 shippou kernel: [   25.482915] input: PC Speaker as /devices/platform/pcspkr/input/input2
Jul 12 11:23:01 shippou kernel: [   25.707520] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 12 11:23:01 shippou kernel: [   25.768628] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul 12 11:23:01 shippou kernel: [   25.825162] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Jul 12 11:23:01 shippou kernel: [   26.170130] input: Power Button (FF) as /devices/virtual/input/input3
Jul 12 11:23:01 shippou kernel: [   26.180392] ACPI: Power Button (FF) [PWRF]
Jul 12 11:23:01 shippou kernel: [   26.180477] input: Power Button (CM) as /devices/virtual/input/input4
Jul 12 11:23:01 shippou kernel: [   26.196331] ACPI: Power Button (CM) [PWRB]
Jul 12 11:23:01 shippou kernel: [   26.237889] input: ImExPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Jul 12 11:23:01 shippou kernel: [   26.250788] parport_pc 00:0a: reported by Plug and Play ACPI
Jul 12 11:23:01 shippou kernel: [   26.250848] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jul 12 11:23:01 shippou kernel: [   27.748224] r8169: eth0: link down
Jul 12 11:23:01 shippou kernel: [   27.841891] hdb: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
Jul 12 11:23:01 shippou kernel: [   27.841899] Uniform CD-ROM driver Revision: 3.20
Jul 12 11:23:01 shippou kernel: [   28.018782] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 11:23:01 shippou kernel: [   28.043011] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
Jul 12 11:23:01 shippou kernel: [   28.054623] usbcore: registered new interface driver libusual
Jul 12 11:23:01 shippou kernel: [   28.069127] Initializing USB Mass Storage driver...
Jul 12 11:23:01 shippou kernel: [   28.081450] scsi4 : SCSI emulation for USB Mass Storage devices
Jul 12 11:23:01 shippou kernel: [   28.083455] usbcore: registered new interface driver usb-storage
Jul 12 11:23:01 shippou kernel: [   28.083462] USB Mass Storage support registered.
Jul 12 11:23:01 shippou kernel: [   28.276513] NET: Registered protocol family 10
Jul 12 11:23:01 shippou kernel: [   28.276738] lo: Disabled Privacy Extensions
Jul 12 11:23:01 shippou kernel: [   28.277065] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 12 11:23:01 shippou kernel: [   30.966002] lp0: using parport0 (interrupt-driven).
Jul 12 11:23:01 shippou kernel: [   31.058676] Adding 289160k swap on /dev/sda3.  Priority:-1 extents:1 across:289160k
Jul 12 11:23:01 shippou kernel: [   31.613721] EXT3 FS on sda2, internal journal
Jul 12 11:23:01 shippou kernel: [   32.538231] kjournald starting.  Commit interval 5 seconds
Jul 12 11:23:01 shippou kernel: [   32.538428] EXT3 FS on sda4, internal journal
Jul 12 11:23:01 shippou kernel: [   32.538432] EXT3-fs: mounted filesystem with ordered data mode.
Jul 12 11:23:01 shippou kernel: [   32.998907] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul 12 11:23:01 shippou kernel: [   33.075226] scsi scan: INQUIRY result too short (5), using 36
Jul 12 11:23:01 shippou kernel: [   33.075235] scsi 4:0:0:0: Direct-Access     USB 2.0  (HS) Flash Disk  1.00 PQ: 0 ANSI: 0 CCS
Jul 12 11:23:01 shippou kernel: [   33.087411] sd 4:0:0:0: [sdb] 1993649 512-byte hardware sectors (1021 MB)
Jul 12 11:23:01 shippou kernel: [   33.087966] sd 4:0:0:0: [sdb] Write Protect is off
Jul 12 11:23:01 shippou kernel: [   33.089953] sd 4:0:0:0: [sdb] 1993649 512-byte hardware sectors (1021 MB)
Jul 12 11:23:01 shippou kernel: [   33.090453] sd 4:0:0:0: [sdb] Write Protect is off
Jul 12 11:23:01 shippou kernel: [   33.090463]  sdb: unknown partition table
Jul 12 11:23:01 shippou kernel: [   33.098479] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Jul 12 11:23:01 shippou kernel: [   33.098526] sd 4:0:0:0: Attached scsi generic sg1 type 0
Jul 12 11:23:01 shippou kernel: [   33.700879] No dock devices found.
Jul 12 11:23:01 shippou kernel: [   33.972284] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (1 cpu cores) (version 2.20.00)
Jul 12 11:23:01 shippou kernel: [   33.972320] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
Jul 12 11:23:01 shippou kernel: [   33.972322] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
Jul 12 11:23:01 shippou kernel: [   34.794947] ppdev: user-space parallel port driver
Jul 12 11:23:22 shippou kernel: [   54.913980] audit(1215833002.091:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4822 profile="/usr/sbin/cupsd" namespace="default"
Jul 12 11:23:42 shippou dhcdbd: Started up.
Jul 12 11:23:43 shippou kernel: [   76.394749] Marking TSC unstable due to cpufreq changes
Jul 12 11:23:43 shippou kernel: [   76.397132] Time: hpet clocksource has been installed.
Jul 12 11:23:43 shippou kernel: [   76.546726] Bluetooth: Core ver 2.11
Jul 12 11:23:43 shippou kernel: [   76.547317] NET: Registered protocol family 31
Jul 12 11:23:43 shippou kernel: [   76.547321] Bluetooth: HCI device and connection manager initialized
Jul 12 11:23:43 shippou kernel: [   76.547325] Bluetooth: HCI socket layer initialized
Jul 12 11:23:43 shippou kernel: [   76.579234] Bluetooth: L2CAP ver 2.9
Jul 12 11:23:43 shippou kernel: [   76.579239] Bluetooth: L2CAP socket layer initialized
Jul 12 11:23:43 shippou kernel: [   76.592374] Clocksource tsc unstable (delta = -158413071 ns)
Jul 12 11:23:44 shippou kernel: [   76.634454] Bluetooth: RFCOMM socket layer initialized
Jul 12 11:23:44 shippou kernel: [   76.634716] Bluetooth: RFCOMM TTY layer initialized
Jul 12 11:23:44 shippou kernel: [   76.634720] Bluetooth: RFCOMM ver 1.8
Jul 12 11:23:45 shippou kernel: [   77.329730] [drm] Initialized drm 1.1.0 20060810
Jul 12 11:23:51 shippou kernel: [   80.887557] hda-intel: Invalid position buffer, using LPIB read method instead.
Jul 12 11:25:37 shippou kernel: [  140.464041] usb 6-6: USB disconnect, address 2
Jul 12 11:26:37 shippou syslogd 1.5.0#1ubuntu1: restart.
Jul 12 11:26:37 shippou kernel: Inspecting /boot/System.map-2.6.24-19-generic
Jul 12 11:26:37 shippou kernel: Loaded 28491 symbols from /boot/System.map-2.6.24-19-generic.
Jul 12 11:26:37 shippou kernel: Symbols match kernel version 2.6.24.
Jul 12 11:26:37 shippou kernel: Loaded 16834 symbols from 77 modules.
Jul 12 11:26:37 shippou kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 12 11:26:37 shippou kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 12 11:26:37 shippou kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:15:37 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
Jul 12 11:26:37 shippou kernel: [    0.000000] Command line: root=UUID=2e985bef-5550-421f-b1bf-e1f730273cbc ro quiet splash
Jul 12 11:26:37 shippou kernel: [    0.000000] BIOS-provided physical RAM map:
Jul 12 11:26:37 shippou kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jul 12 11:26:37 shippou kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jul 12 11:26:37 shippou kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jul 12 11:26:37 shippou kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000097fe0000 (usable)
Jul 12 11:26:37 shippou kernel: [    0.000000]  BIOS-e820: 0000000097fe0000 - 0000000097fe3000 (ACPI NVS)
Jul 12 11:26:37 shippou kernel: [    0.000000]  BIOS-e820: 0000000097fe3000 - 0000000097ff0000 (ACPI data)
Jul 12 11:26:37 shippou kernel: [    0.000000]  BIOS-e820: 0000000097ff0000 - 0000000098000000 (reserved)
Jul 12 11:26:37 shippou kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Jul 12 11:26:37 shippou kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Jul 12 11:26:37 shippou kernel: [    0.000000] end_pfn_map = 1048576
Jul 12 11:26:37 shippou kernel: [    0.000000] DMI 2.5 present.
Jul 12 11:26:37 shippou kernel: [    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F7B80 checksum 0
Jul 12 11:26:37 shippou kernel: [    0.000000] ACPI: RSDP 000F7B80, 0024 (r2 RS690 )
Jul 12 11:26:37 shippou kernel: [    0.000000] ACPI: RSDT 97FE3040, 0038 (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 12 11:26:37 shippou kernel: [    0.000000] ACPI: FACP 97FE30C0, 0074 (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 12 11:26:37 shippou kernel: [    0.000000] ACPI: DSDT 97FE3180, 4B0B (r1 RS690  AWRDACPI     1000 MSFT  3000000)
Jul 12 11:26:37 shippou kernel: [    0.000000] ACPI: FACS 97FE0000, 0040
Jul 12 11:26:37 shippou kernel: [    0.000000] ACPI: SSDT 97FE7DC0, 00D3 (r1 PTLTD  POWERNOW        1  LTP        1)
Jul 12 11:26:37 shippou kernel: [    0.000000] ACPI: HPET 97FE7F00, 0038 (r1 RS690  AWRDACPI 42302E31 AWRD       98)
Jul 12 11:26:37 shippou kernel: [    0.000000] ACPI: MCFG 97FE7F80, 003C (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 12 11:26:37 shippou kernel: [    0.000000] ACPI: APIC 97FE7D00, 0068 (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 12 11:26:37 shippou kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Jul 12 11:26:37 shippou kernel: [    0.000000] CPU has 1 num_cores
Jul 12 11:26:37 shippou kernel: [    0.000000] No NUMA configuration found
Jul 12 11:26:37 shippou kernel: [    0.000000] Faking a node at 0000000000000000-0000000097fe0000
Jul 12 11:26:37 shippou kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000097fe0000
Jul 12 11:26:37 shippou kernel: [    0.000000] Zone PFN ranges:
Jul 12 11:26:37 shippou kernel: [    0.000000]   DMA             0 ->     4096
Jul 12 11:26:37 shippou kernel: [    0.000000]   DMA32        4096 ->  1048576
Jul 12 11:26:37 shippou kernel: [    0.000000]   Normal    1048576 ->  1048576
Jul 12 11:26:37 shippou kernel: [    0.000000] Movable zone start PFN for each node
Jul 12 11:26:37 shippou kernel: [    0.000000] early_node_map[2] active PFN ranges
Jul 12 11:26:37 shippou kernel: [    0.000000]     0:        0 ->      159
Jul 12 11:26:37 shippou kernel: [    0.000000]     0:      256 ->   622560
Jul 12 11:26:37 shippou kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Jul 12 11:26:37 shippou kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Jul 12 11:26:37 shippou kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul 12 11:26:37 shippou kernel: [    0.000000] Processor #0 (Bootup-CPU)
Jul 12 11:26:37 shippou kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Jul 12 11:26:37 shippou kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul 12 11:26:37 shippou kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jul 12 11:26:37 shippou kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jul 12 11:26:37 shippou kernel: [    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
Jul 12 11:26:37 shippou kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 12 11:26:37 shippou kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jul 12 11:26:37 shippou kernel: [    0.000000] Setting APIC routing to flat
Jul 12 11:26:37 shippou kernel: [    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
Jul 12 11:26:37 shippou kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 12 11:26:37 shippou kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Jul 12 11:26:37 shippou kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Jul 12 11:26:37 shippou kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Jul 12 11:26:37 shippou kernel: [    0.000000] Allocating PCI resources starting at a0000000 (gap: 98000000:48000000)
Jul 12 11:26:37 shippou kernel: [    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
Jul 12 11:26:37 shippou kernel: [    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
Jul 12 11:26:37 shippou kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 612716
Jul 12 11:26:37 shippou kernel: [    0.000000] Policy zone: DMA32
Jul 12 11:26:37 shippou kernel: [    0.000000] Kernel command line: root=UUID=2e985bef-5550-421f-b1bf-e1f730273cbc ro quiet splash
Jul 12 11:26:37 shippou kernel: [    0.000000] Initializing CPU#0
Jul 12 11:26:37 shippou kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Jul 12 11:26:37 shippou kernel: [    0.000000] TSC calibrated against HPET
Jul 12 11:26:37 shippou kernel: [   10.853272] time.c: Detected 1799.818 MHz processor.
Jul 12 11:26:37 shippou kernel: [   10.853959] Console: colour VGA+ 80x25
Jul 12 11:26:37 shippou kernel: [   10.853962] console [tty0] enabled
Jul 12 11:26:37 shippou kernel: [   10.853979] Checking aperture...
Jul 12 11:26:37 shippou kernel: [   10.853982] CPU 0: aperture @ b4c0000000 size 32 MB
Jul 12 11:26:37 shippou kernel: [   10.853984] Aperture too small (32 MB)
Jul 12 11:26:37 shippou kernel: [   10.863796] No AGP bridge found
Jul 12 11:26:37 shippou kernel: [   10.896540] Memory: 2442456k/2490240k available (2489k kernel code, 47396k reserved, 1318k data, 320k init)
Jul 12 11:26:37 shippou kernel: [   10.896579] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Jul 12 11:26:37 shippou kernel: [   10.975274] Calibrating delay using timer specific routine.. 3708.68 BogoMIPS (lpj=7417362)
Jul 12 11:26:37 shippou kernel: [   10.975321] Security Framework initialized
Jul 12 11:26:37 shippou kernel: [   10.975326] SELinux:  Disabled at boot.
Jul 12 11:26:37 shippou kernel: [   10.975340] AppArmor: AppArmor initialized
Jul 12 11:26:37 shippou kernel: [   10.975343] Failure registering capabilities with primary security module.
Jul 12 11:26:37 shippou kernel: [   10.975721] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jul 12 11:26:37 shippou kernel: [   10.979744] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jul 12 11:26:37 shippou kernel: [   10.981366] Mount-cache hash table entries: 256
Jul 12 11:26:37 shippou kernel: [   10.981516] Initializing cgroup subsys ns
Jul 12 11:26:37 shippou kernel: [   10.981519] Initializing cgroup subsys cpuacct
Jul 12 11:26:37 shippou kernel: [   10.981536] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jul 12 11:26:37 shippou kernel: [   10.981538] CPU: L2 Cache: 512K (64 bytes/line)
Jul 12 11:26:37 shippou kernel: [   10.981541] CPU 0/0 -> Node 0
Jul 12 11:26:37 shippou kernel: [   10.981568] SMP alternatives: switching to UP code
Jul 12 11:26:37 shippou kernel: [   10.982254] Early unpacking initramfs... done
Jul 12 11:26:37 shippou kernel: [   11.383131] ACPI: Core revision 20070126
Jul 12 11:26:37 shippou kernel: [   11.383191] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Jul 12 11:26:37 shippou kernel: [   11.432651] Using local APIC timer interrupts.
Jul 12 11:26:37 shippou kernel: [   11.488128] Detected 12.498 MHz APIC timer.
Jul 12 11:26:37 shippou kernel: [   11.488177] Brought up 1 CPUs
Jul 12 11:26:37 shippou kernel: [   11.488449] net_namespace: 120 bytes
Jul 12 11:26:37 shippou kernel: [   11.488850] Time: 11:26:15  Date: 07/12/08
Jul 12 11:26:37 shippou kernel: [   11.488880] NET: Registered protocol family 16
Jul 12 11:26:37 shippou kernel: [   11.489051] ACPI: bus type pci registered
Jul 12 11:26:37 shippou kernel: [   11.489119] PCI: Using configuration type 1
Jul 12 11:26:37 shippou kernel: [   11.495825] ACPI: Interpreter enabled
Jul 12 11:26:37 shippou kernel: [   11.495831] ACPI: (supports S0 S3 S4 S5)
Jul 12 11:26:37 shippou kernel: [   11.495848] ACPI: Using IOAPIC for interrupt routing
Jul 12 11:26:37 shippou kernel: [   11.501037] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul 12 11:26:37 shippou kernel: [   11.501198] pci 0000:00:12.0: set SATA to AHCI mode
Jul 12 11:26:37 shippou kernel: [   11.501992] PCI: Transparent bridge - 0000:00:14.4
Jul 12 11:26:37 shippou kernel: [   11.522730] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 11:26:37 shippou kernel: [   11.522836] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 11:26:37 shippou kernel: [   11.522939] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 11:26:37 shippou kernel: [   11.523043] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 11:26:37 shippou kernel: [   11.523146] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 11:26:37 shippou kernel: [   11.523249] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 11:26:37 shippou kernel: [   11.523352] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 11:26:37 shippou kernel: [   11.523455] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 11:26:37 shippou kernel: [   11.523571] Linux Plug and Play Support v0.97 (c) Adam Belay
Jul 12 11:26:37 shippou kernel: [   11.523600] pnp: PnP ACPI init
Jul 12 11:26:37 shippou kernel: [   11.523608] ACPI: bus type pnp registered
Jul 12 11:26:37 shippou kernel: [   11.526625] pnp: PnP ACPI: found 15 devices
Jul 12 11:26:37 shippou kernel: [   11.526628] ACPI: ACPI bus type pnp unregistered
Jul 12 11:26:37 shippou kernel: [   11.526858] PCI: Using ACPI for IRQ routing
Jul 12 11:26:37 shippou kernel: [   11.526860] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jul 12 11:26:37 shippou kernel: [   11.540083] NET: Registered protocol family 8
Jul 12 11:26:37 shippou kernel: [   11.540084] NET: Registered protocol family 20
Jul 12 11:26:37 shippou kernel: [   11.540164] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Jul 12 11:26:37 shippou kernel: [   11.540168] hpet0: 4 32-bit timers, 14318180 Hz
Jul 12 11:26:37 shippou kernel: [   11.541222] AppArmor: AppArmor Filesystem Enabled
Jul 12 11:26:37 shippou kernel: [   11.544043] Time: tsc clocksource has been installed.
Jul 12 11:26:37 shippou kernel: [   11.552025] system 00:01: ioport range 0x4100-0x411f has been reserved
Jul 12 11:26:37 shippou kernel: [   11.552028] system 00:01: ioport range 0x228-0x22f has been reserved
Jul 12 11:26:37 shippou kernel: [   11.552032] system 00:01: ioport range 0x40b-0x40b has been reserved
Jul 12 11:26:37 shippou kernel: [   11.552035] system 00:01: ioport range 0x4d6-0x4d6 has been reserved
Jul 12 11:26:37 shippou kernel: [   11.552038] system 00:01: ioport range 0xc00-0xc01 has been reserved
Jul 12 11:26:37 shippou kernel: [   11.552041] system 00:01: ioport range 0xc14-0xc14 has been reserved
Jul 12 11:26:37 shippou kernel: [   11.552044] system 00:01: ioport range 0xc50-0xc52 has been reserved
Jul 12 11:26:37 shippou kernel: [   11.552047] system 00:01: ioport range 0xc6c-0xc6d has been reserved
Jul 12 11:26:37 shippou kernel: [   11.552050] system 00:01: ioport range 0xc6f-0xc6f has been reserved
Jul 12 11:26:37 shippou kernel: [   11.552053] system 00:01: ioport range 0xcd0-0xcd1 has been reserved
Jul 12 11:26:37 shippou kernel: [   11.552056] system 00:01: ioport range 0xcd2-0xcd3 has been reserved
Jul 12 11:26:37 shippou kernel: [   11.552059] system 00:01: ioport range 0xcd4-0xcdf has been reserved
Jul 12 11:26:37 shippou kernel: [   11.552062] system 00:01: ioport range 0x4000-0x40fe has been reserved
Jul 12 11:26:37 shippou kernel: [   11.552065] system 00:01: ioport range 0x4210-0x4217 has been reserved
Jul 12 11:26:37 shippou kernel: [   11.552068] system 00:01: ioport range 0xb10-0xb1f has been reserved
Jul 12 11:26:37 shippou kernel: [   11.552078] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
Jul 12 11:26:37 shippou kernel: [   11.552081] system 00:07: ioport range 0x220-0x225 has been reserved
Jul 12 11:26:37 shippou kernel: [   11.552084] system 00:07: ioport range 0xb00-0xb0f has been reserved
Jul 12 11:26:37 shippou kernel: [   11.552093] system 00:0d: iomem range 0xe0000000-0xefffffff could not be reserved
Jul 12 11:26:37 shippou kernel: [   11.552099] system 00:0e: iomem range 0xf0000-0xfffff could not be reserved
Jul 12 11:26:37 shippou kernel: [   11.552103] system 00:0e: iomem range 0xfed00000-0xfed000ff has been reserved
Jul 12 11:26:37 shippou kernel: [   11.552106] system 00:0e: iomem range 0x97fe0000-0x97ffffff could not be reserved
Jul 12 11:26:37 shippou kernel: [   11.552110] system 00:0e: iomem range 0xffff0000-0xffffffff has been reserved
Jul 12 11:26:37 shippou kernel: [   11.552113] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
Jul 12 11:26:37 shippou kernel: [   11.552116] system 00:0e: iomem range 0x100000-0x97fdffff could not be reserved
Jul 12 11:26:37 shippou kernel: [   11.552120] system 00:0e: iomem range 0x98000000-0x9fffffff has been reserved
Jul 12 11:26:37 shippou kernel: [   11.552123] system 00:0e: iomem range 0xfec00000-0xfec00fff has been reserved
Jul 12 11:26:37 shippou kernel: [   11.552126] system 00:0e: iomem range 0xfee00000-0xfee00fff could not be reserved
Jul 12 11:26:37 shippou kernel: [   11.552130] system 00:0e: iomem range 0xfff80000-0xfffeffff has been reserved
Jul 12 11:26:37 shippou kernel: [   11.552486] PCI: Bridge: 0000:00:01.0
Jul 12 11:26:37 shippou kernel: [   11.552489]   IO window: e000-efff
Jul 12 11:26:37 shippou kernel: [   11.552492]   MEM window: fdd00000-fdefffff
Jul 12 11:26:37 shippou kernel: [   11.552494]   PREFETCH window: d8000000-dfffffff
Jul 12 11:26:37 shippou kernel: [   11.552499] PCI: Bridge: 0000:00:14.4
Jul 12 11:26:37 shippou kernel: [   11.552502]   IO window: d000-dfff
Jul 12 11:26:37 shippou kernel: [   11.552506]   MEM window: fdc00000-fdcfffff
Jul 12 11:26:37 shippou kernel: [   11.552510]   PREFETCH window: fdf00000-fdffffff
Jul 12 11:26:37 shippou kernel: [   11.552535] NET: Registered protocol family 2
Jul 12 11:26:37 shippou kernel: [   11.588085] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Jul 12 11:26:37 shippou kernel: [   11.589718] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Jul 12 11:26:37 shippou kernel: [   11.597026] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jul 12 11:26:37 shippou kernel: [   11.597907] TCP: Hash tables configured (established 524288 bind 65536)
Jul 12 11:26:37 shippou kernel: [   11.597912] TCP reno registered
Jul 12 11:26:37 shippou kernel: [   11.608061] checking if image is initramfs... it is
Jul 12 11:26:37 shippou kernel: [   12.312735] Freeing initrd memory: 8212k freed
Jul 12 11:26:37 shippou kernel: [   12.319873] audit: initializing netlink socket (disabled)
Jul 12 11:26:37 shippou kernel: [   12.319886] audit(1215861975.416:1): initialized
Jul 12 11:26:37 shippou kernel: [   12.321865] VFS: Disk quotas dquot_6.5.1
Jul 12 11:26:37 shippou kernel: [   12.321937] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jul 12 11:26:37 shippou kernel: [   12.322079] io scheduler noop registered
Jul 12 11:26:37 shippou kernel: [   12.322081] io scheduler anticipatory registered
Jul 12 11:26:37 shippou kernel: [   12.322083] io scheduler deadline registered
Jul 12 11:26:37 shippou kernel: [   12.322187] io scheduler cfq registered (default)
Jul 12 11:26:37 shippou kernel: [   12.490752] Real Time Clock Driver v1.12ac
Jul 12 11:26:37 shippou kernel: [   12.490976] Linux agpgart interface v0.102
Jul 12 11:26:37 shippou kernel: [   12.490978] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jul 12 11:26:37 shippou kernel: [   12.491126] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 12 11:26:37 shippou kernel: [   12.491716] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 12 11:26:37 shippou kernel: [   12.492412] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jul 12 11:26:37 shippou kernel: [   12.492480] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jul 12 11:26:37 shippou kernel: [   12.492568] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jul 12 11:26:37 shippou kernel: [   12.492902] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 12 11:26:37 shippou kernel: [   12.492906] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 12 11:26:37 shippou kernel: [   12.502599] mice: PS/2 mouse device common for all mice
Jul 12 11:26:37 shippou kernel: [   12.502634] cpuidle: using governor ladder
Jul 12 11:26:37 shippou kernel: [   12.502636] cpuidle: using governor menu
Jul 12 11:26:37 shippou kernel: [   12.502787] NET: Registered protocol family 1
Jul 12 11:26:37 shippou kernel: [   12.502883] registered taskstats version 1
Jul 12 11:26:37 shippou kernel: [   12.503002]   Magic number: 0:447:428
Jul 12 11:26:37 shippou kernel: [   12.503153] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
Jul 12 11:26:37 shippou kernel: [   12.503156] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 12 11:26:37 shippou kernel: [   12.503158] EDD information not available.
Jul 12 11:26:37 shippou kernel: [   12.503166] Freeing unused kernel memory: 320k freed
Jul 12 11:26:37 shippou kernel: [   12.530358] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jul 12 11:26:37 shippou kernel: [   13.700580] fuse init (API version 7.9)
Jul 12 11:26:37 shippou kernel: [   13.714984] ACPI: Fan [FAN] (on)
Jul 12 11:26:37 shippou kernel: [   13.721784] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Jul 12 11:26:37 shippou kernel: [   13.723135] ACPI: Thermal Zone [THRM] (40 C)
Jul 12 11:26:37 shippou kernel: [   14.267576] SCSI subsystem initialized
Jul 12 11:26:37 shippou kernel: [   14.337117] usbcore: registered new interface driver usbfs
Jul 12 11:26:37 shippou kernel: [   14.337139] usbcore: registered new interface driver hub
Jul 12 11:26:37 shippou kernel: [   14.347634] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 11:26:37 shippou kernel: [   14.347769] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
Jul 12 11:26:37 shippou kernel: [   14.347775] ahci 0000:00:12.0: controller can't do PMP, turning off CAP_PMP
Jul 12 11:26:37 shippou kernel: [   14.357724] usbcore: registered new device driver usb
Jul 12 11:26:37 shippou kernel: [   14.371235] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jul 12 11:26:37 shippou kernel: [   14.372206] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jul 12 11:26:37 shippou kernel: [   14.567006] Floppy drive(s): fd0 is 1.44M
Jul 12 11:26:37 shippou kernel: [   14.586643] FDC 0 is a post-1991 82077
Jul 12 11:26:37 shippou kernel: [   15.349522] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Jul 12 11:26:37 shippou kernel: [   15.349528] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pio slum part 
Jul 12 11:26:37 shippou kernel: [   15.350745] scsi0 : ahci
Jul 12 11:26:37 shippou kernel: [   15.351078] scsi1 : ahci
Jul 12 11:26:37 shippou kernel: [   15.351228] scsi2 : ahci
Jul 12 11:26:37 shippou kernel: [   15.351380] scsi3 : ahci
Jul 12 11:26:37 shippou kernel: [   15.351459] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 16
Jul 12 11:26:37 shippou kernel: [   15.351463] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 16
Jul 12 11:26:37 shippou kernel: [   15.351467] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 16
Jul 12 11:26:37 shippou kernel: [   15.351470] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 16
Jul 12 11:26:37 shippou kernel: [   15.824675] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 12 11:26:37 shippou kernel: [   15.868249] ata1.00: ATA-7: ST380215AS, 3.AAD, max UDMA/133
Jul 12 11:26:37 shippou kernel: [   15.868252] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32)
Jul 12 11:26:37 shippou kernel: [   15.926473] ata1.00: configured for UDMA/133
Jul 12 11:26:37 shippou kernel: [   16.235963] ata2: SATA link down (SStatus 0 SControl 300)
Jul 12 11:26:37 shippou kernel: [   16.547425] ata3: SATA link down (SStatus 0 SControl 300)
Jul 12 11:26:37 shippou kernel: [   16.858888] ata4: SATA link down (SStatus 0 SControl 300)
Jul 12 11:26:37 shippou kernel: [   16.859012] scsi 0:0:0:0: Direct-Access     ATA      ST380215AS       3.AA PQ: 0 ANSI: 5
Jul 12 11:26:37 shippou kernel: [   16.860476] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 11:26:37 shippou kernel: [   16.860598] ohci_hcd 0000:00:13.0: OHCI Host Controller
Jul 12 11:26:37 shippou kernel: [   16.860857] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Jul 12 11:26:37 shippou kernel: [   16.860878] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02e000
Jul 12 11:26:37 shippou kernel: [   16.868053] Driver 'sd' needs updating - please use bus_type methods
Jul 12 11:26:37 shippou kernel: [   16.874919] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jul 12 11:26:37 shippou kernel: [   16.874933] sd 0:0:0:0: [sda] Write Protect is off
Jul 12 11:26:37 shippou kernel: [   16.874949] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 12 11:26:37 shippou kernel: [   16.875001] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jul 12 11:26:37 shippou kernel: [   16.875010] sd 0:0:0:0: [sda] Write Protect is off
Jul 12 11:26:37 shippou kernel: [   16.875025] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 12 11:26:37 shippou kernel: [   16.875030]  sda: sda1 sda2 sda3 sda4
Jul 12 11:26:37 shippou kernel: [   16.919053] usb usb1: configuration #1 chosen from 1 choice
Jul 12 11:26:37 shippou kernel: [   16.919079] hub 1-0:1.0: USB hub found
Jul 12 11:26:37 shippou kernel: [   16.919088] hub 1-0:1.0: 2 ports detected
Jul 12 11:26:37 shippou kernel: [   16.926102] sd 0:0:0:0: [sda] Attached SCSI disk
Jul 12 11:26:37 shippou kernel: [   16.931398] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 12 11:26:37 shippou kernel: [   17.022710] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 17
Jul 12 11:26:37 shippou kernel: [   17.022840] ohci_hcd 0000:00:13.1: OHCI Host Controller
Jul 12 11:26:37 shippou kernel: [   17.022904] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Jul 12 11:26:37 shippou kernel: [   17.022930] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfe02d000
Jul 12 11:26:37 shippou kernel: [   17.082752] usb usb2: configuration #1 chosen from 1 choice
Jul 12 11:26:37 shippou kernel: [   17.082779] hub 2-0:1.0: USB hub found
Jul 12 11:26:37 shippou kernel: [   17.082788] hub 2-0:1.0: 2 ports detected
Jul 12 11:26:37 shippou kernel: [   17.186422] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 18
Jul 12 11:26:37 shippou kernel: [   17.186546] ohci_hcd 0000:00:13.2: OHCI Host Controller
Jul 12 11:26:37 shippou kernel: [   17.186607] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
Jul 12 11:26:37 shippou kernel: [   17.186630] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfe02c000
Jul 12 11:26:37 shippou kernel: [   17.246465] usb usb3: configuration #1 chosen from 1 choice
Jul 12 11:26:37 shippou kernel: [   17.246499] hub 3-0:1.0: USB hub found
Jul 12 11:26:37 shippou kernel: [   17.246509] hub 3-0:1.0: 2 ports detected
Jul 12 11:26:37 shippou kernel: [   17.350859] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 17
Jul 12 11:26:37 shippou kernel: [   17.351008] ohci_hcd 0000:00:13.3: OHCI Host Controller
Jul 12 11:26:37 shippou kernel: [   17.351074] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
Jul 12 11:26:37 shippou kernel: [   17.351094] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfe02b000
Jul 12 11:26:37 shippou kernel: [   17.357867] Attempting manual resume
Jul 12 11:26:37 shippou kernel: [   17.393495] EXT3-fs: INFO: recovery required on readonly filesystem.
Jul 12 11:26:37 shippou kernel: [   17.393501] EXT3-fs: write access will be enabled during recovery.
Jul 12 11:26:37 shippou kernel: [   17.410171] usb usb4: configuration #1 chosen from 1 choice
Jul 12 11:26:37 shippou kernel: [   17.410194] hub 4-0:1.0: USB hub found
Jul 12 11:26:37 shippou kernel: [   17.410203] hub 4-0:1.0: 2 ports detected
Jul 12 11:26:37 shippou kernel: [   17.468915] kjournald starting.  Commit interval 5 seconds
Jul 12 11:26:37 shippou kernel: [   17.468932] EXT3-fs: sda2: orphan cleanup on readonly fs
Jul 12 11:26:37 shippou kernel: [   17.468964] EXT3-fs: sda2: 1 orphan inode deleted
Jul 12 11:26:37 shippou kernel: [   17.468965] EXT3-fs: recovery complete.
Jul 12 11:26:37 shippou kernel: [   17.471071] EXT3-fs: mounted filesystem with ordered data mode.
Jul 12 11:26:37 shippou kernel: [   17.513856] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 18
Jul 12 11:26:37 shippou kernel: [   17.514004] ohci_hcd 0000:00:13.4: OHCI Host Controller
Jul 12 11:26:37 shippou kernel: [   17.514066] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
Jul 12 11:26:37 shippou kernel: [   17.514084] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfe02a000
Jul 12 11:26:37 shippou kernel: [   17.573901] usb usb5: configuration #1 chosen from 1 choice
Jul 12 11:26:37 shippou kernel: [   17.573926] hub 5-0:1.0: USB hub found
Jul 12 11:26:37 shippou kernel: [   17.573935] hub 5-0:1.0: 2 ports detected
Jul 12 11:26:37 shippou kernel: [   17.677725] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 19
Jul 12 11:26:37 shippou kernel: [   17.677873] ehci_hcd 0000:00:13.5: EHCI Host Controller
Jul 12 11:26:37 shippou kernel: [   17.677937] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
Jul 12 11:26:37 shippou kernel: [   17.677977] ehci_hcd 0000:00:13.5: debug port 1
Jul 12 11:26:37 shippou kernel: [   17.677996] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfe029000
Jul 12 11:26:37 shippou kernel: [   17.689456] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jul 12 11:26:37 shippou kernel: [   17.689567] usb usb6: configuration #1 chosen from 1 choice
Jul 12 11:26:37 shippou kernel: [   17.689590] hub 6-0:1.0: USB hub found
Jul 12 11:26:37 shippou kernel: [   17.689596] hub 6-0:1.0: 10 ports detected
Jul 12 11:26:37 shippou kernel: [   17.793435] r8169 Gigabit Ethernet driver 2.2LK loaded
Jul 12 11:26:37 shippou kernel: [   17.793471] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 22 (level, low) -> IRQ 22
Jul 12 11:26:37 shippou kernel: [   17.793703] eth0: RTL8169sc/8110sc at 0xffffc20001044000, 00:19:21:21:21:b5, XID 18000000 IRQ 22
Jul 12 11:26:37 shippou kernel: [   17.794455] SB600_PATA: IDE controller (0x1002:0x438c rev 0x00) at  PCI slot 0000:00:14.1
Jul 12 11:26:37 shippou kernel: [   17.794462] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 11:26:37 shippou kernel: [   17.794469] SB600_PATA: not 100% native mode: will probe irqs later
Jul 12 11:26:37 shippou kernel: [   17.794478]     ide0: BM-DMA at 0xf900-0xf907, BIOS settings: hda:pio, hdb:DMA
Jul 12 11:26:37 shippou kernel: [   18.580249] hdb: LITE-ON DVDRW LH-20A1P, ATAPI CD/DVD-ROM drive
Jul 12 11:26:37 shippou kernel: [   18.859784] hdb: UDMA/66 mode selected
Jul 12 11:26:37 shippou kernel: [   18.860158] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Jul 12 11:26:37 shippou kernel: [   25.117705] input: PC Speaker as /devices/platform/pcspkr/input/input2
Jul 12 11:26:37 shippou kernel: [   25.352299] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 12 11:26:37 shippou kernel: [   25.392259] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul 12 11:26:37 shippou kernel: [   25.488083] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Jul 12 11:26:37 shippou kernel: [   25.622996] input: Power Button (FF) as /devices/virtual/input/input3
Jul 12 11:26:37 shippou kernel: [   25.647769] ACPI: Power Button (FF) [PWRF]
Jul 12 11:26:37 shippou kernel: [   25.647826] input: Power Button (CM) as /devices/virtual/input/input4
Jul 12 11:26:37 shippou kernel: [   25.667864] ACPI: Power Button (CM) [PWRB]
Jul 12 11:26:37 shippou kernel: [   25.762286] input: ImExPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Jul 12 11:26:37 shippou kernel: [   25.790021] parport_pc 00:0a: reported by Plug and Play ACPI
Jul 12 11:26:37 shippou kernel: [   25.790079] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jul 12 11:26:37 shippou kernel: [   27.253708] r8169: eth0: link down
Jul 12 11:26:37 shippou kernel: [   27.382261] hdb: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
Jul 12 11:26:37 shippou kernel: [   27.382269] Uniform CD-ROM driver Revision: 3.20
Jul 12 11:26:37 shippou kernel: [   27.480946] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 11:26:37 shippou kernel: [   27.506374] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
Jul 12 11:26:37 shippou kernel: [   27.804620] NET: Registered protocol family 10
Jul 12 11:26:37 shippou kernel: [   27.804836] lo: Disabled Privacy Extensions
Jul 12 11:26:37 shippou kernel: [   27.805162] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 12 11:26:37 shippou kernel: [   30.442449] lp0: using parport0 (interrupt-driven).
Jul 12 11:26:37 shippou kernel: [   30.535372] Adding 289160k swap on /dev/sda3.  Priority:-1 extents:1 across:289160k
Jul 12 11:26:37 shippou kernel: [   31.090441] EXT3 FS on sda2, internal journal
Jul 12 11:26:37 shippou kernel: [   32.222552] kjournald starting.  Commit interval 5 seconds
Jul 12 11:26:37 shippou kernel: [   32.222755] EXT3 FS on sda4, internal journal
Jul 12 11:26:37 shippou kernel: [   32.222759] EXT3-fs: mounted filesystem with ordered data mode.
Jul 12 11:26:37 shippou kernel: [   32.666604] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul 12 11:26:37 shippou kernel: [   33.130626] No dock devices found.
Jul 12 11:26:37 shippou kernel: [   33.390487] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (1 cpu cores) (version 2.20.00)
Jul 12 11:26:37 shippou kernel: [   33.390526] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
Jul 12 11:26:37 shippou kernel: [   33.390529] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
Jul 12 11:26:37 shippou kernel: [   34.204788] ppdev: user-space parallel port driver
Jul 12 11:26:58 shippou kernel: [   54.340494] audit(1215833218.046:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4788 profile="/usr/sbin/cupsd" namespace="default"
Jul 12 11:27:18 shippou dhcdbd: Started up.
Jul 12 11:27:19 shippou kernel: [   75.983882] Bluetooth: Core ver 2.11
Jul 12 11:27:19 shippou kernel: [   75.984544] NET: Registered protocol family 31
Jul 12 11:27:19 shippou kernel: [   75.984549] Bluetooth: HCI device and connection manager initialized
Jul 12 11:27:19 shippou kernel: [   75.984554] Bluetooth: HCI socket layer initialized
Jul 12 11:27:19 shippou kernel: [   76.026228] Bluetooth: L2CAP ver 2.9
Jul 12 11:27:19 shippou kernel: [   76.026233] Bluetooth: L2CAP socket layer initialized
Jul 12 11:27:19 shippou kernel: [   76.087008] Bluetooth: RFCOMM socket layer initialized
Jul 12 11:27:19 shippou kernel: [   76.087031] Bluetooth: RFCOMM TTY layer initialized
Jul 12 11:27:19 shippou kernel: [   76.087033] Bluetooth: RFCOMM ver 1.8
Jul 12 11:27:19 shippou kernel: [   76.168781] Marking TSC unstable due to cpufreq changes
Jul 12 11:27:19 shippou kernel: [   76.177676] Time: hpet clocksource has been installed.
Jul 12 11:27:20 shippou kernel: [   76.518761] Clocksource tsc unstable (delta = -222242366 ns)
Jul 12 11:27:21 shippou kernel: [   76.841425] [drm] Initialized drm 1.1.0 20060810
Jul 12 11:27:27 shippou kernel: [   80.416861] hda-intel: Invalid position buffer, using LPIB read method instead.
Jul 12 11:27:40 shippou kernel: [   87.638446] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jul 12 11:27:41 shippou exiting on signal 15
Jul 12 11:28:27 shippou syslogd 1.5.0#1ubuntu1: restart.
Jul 12 11:28:27 shippou kernel: Inspecting /boot/System.map-2.6.24-19-generic
Jul 12 11:28:27 shippou kernel: Loaded 28491 symbols from /boot/System.map-2.6.24-19-generic.
Jul 12 11:28:27 shippou kernel: Symbols match kernel version 2.6.24.
Jul 12 11:28:27 shippou kernel: Loaded 16834 symbols from 77 modules.
Jul 12 11:28:27 shippou kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 12 11:28:27 shippou kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 12 11:28:27 shippou kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:15:37 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
Jul 12 11:28:27 shippou kernel: [    0.000000] Command line: root=UUID=2e985bef-5550-421f-b1bf-e1f730273cbc ro quiet splash
Jul 12 11:28:27 shippou kernel: [    0.000000] BIOS-provided physical RAM map:
Jul 12 11:28:27 shippou kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jul 12 11:28:27 shippou kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jul 12 11:28:27 shippou kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jul 12 11:28:27 shippou kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000097fe0000 (usable)
Jul 12 11:28:27 shippou kernel: [    0.000000]  BIOS-e820: 0000000097fe0000 - 0000000097fe3000 (ACPI NVS)
Jul 12 11:28:27 shippou kernel: [    0.000000]  BIOS-e820: 0000000097fe3000 - 0000000097ff0000 (ACPI data)
Jul 12 11:28:27 shippou kernel: [    0.000000]  BIOS-e820: 0000000097ff0000 - 0000000098000000 (reserved)
Jul 12 11:28:27 shippou kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Jul 12 11:28:27 shippou kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Jul 12 11:28:27 shippou kernel: [    0.000000] end_pfn_map = 1048576
Jul 12 11:28:27 shippou kernel: [    0.000000] DMI 2.5 present.
Jul 12 11:28:27 shippou kernel: [    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F7B80 checksum 0
Jul 12 11:28:27 shippou kernel: [    0.000000] ACPI: RSDP 000F7B80, 0024 (r2 RS690 )
Jul 12 11:28:27 shippou kernel: [    0.000000] ACPI: RSDT 97FE3040, 0038 (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 12 11:28:27 shippou kernel: [    0.000000] ACPI: FACP 97FE30C0, 0074 (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 12 11:28:27 shippou kernel: [    0.000000] ACPI: DSDT 97FE3180, 4B0B (r1 RS690  AWRDACPI     1000 MSFT  3000000)
Jul 12 11:28:27 shippou kernel: [    0.000000] ACPI: FACS 97FE0000, 0040
Jul 12 11:28:27 shippou kernel: [    0.000000] ACPI: SSDT 97FE7DC0, 00D3 (r1 PTLTD  POWERNOW        1  LTP        1)
Jul 12 11:28:27 shippou kernel: [    0.000000] ACPI: HPET 97FE7F00, 0038 (r1 RS690  AWRDACPI 42302E31 AWRD       98)
Jul 12 11:28:27 shippou kernel: [    0.000000] ACPI: MCFG 97FE7F80, 003C (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 12 11:28:27 shippou kernel: [    0.000000] ACPI: APIC 97FE7D00, 0068 (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 12 11:28:27 shippou kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Jul 12 11:28:27 shippou kernel: [    0.000000] CPU has 1 num_cores
Jul 12 11:28:27 shippou kernel: [    0.000000] No NUMA configuration found
Jul 12 11:28:27 shippou kernel: [    0.000000] Faking a node at 0000000000000000-0000000097fe0000
Jul 12 11:28:27 shippou kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000097fe0000
Jul 12 11:28:27 shippou kernel: [    0.000000] Zone PFN ranges:
Jul 12 11:28:27 shippou kernel: [    0.000000]   DMA             0 ->     4096
Jul 12 11:28:27 shippou kernel: [    0.000000]   DMA32        4096 ->  1048576
Jul 12 11:28:27 shippou kernel: [    0.000000]   Normal    1048576 ->  1048576
Jul 12 11:28:27 shippou kernel: [    0.000000] Movable zone start PFN for each node
Jul 12 11:28:27 shippou kernel: [    0.000000] early_node_map[2] active PFN ranges
Jul 12 11:28:27 shippou kernel: [    0.000000]     0:        0 ->      159
Jul 12 11:28:27 shippou kernel: [    0.000000]     0:      256 ->   622560
Jul 12 11:28:27 shippou kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Jul 12 11:28:27 shippou kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Jul 12 11:28:27 shippou kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul 12 11:28:27 shippou kernel: [    0.000000] Processor #0 (Bootup-CPU)
Jul 12 11:28:27 shippou kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Jul 12 11:28:27 shippou kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul 12 11:28:27 shippou kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jul 12 11:28:27 shippou kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jul 12 11:28:27 shippou kernel: [    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
Jul 12 11:28:27 shippou kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 12 11:28:27 shippou kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jul 12 11:28:27 shippou kernel: [    0.000000] Setting APIC routing to flat
Jul 12 11:28:27 shippou kernel: [    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
Jul 12 11:28:27 shippou kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 12 11:28:27 shippou kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Jul 12 11:28:27 shippou kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Jul 12 11:28:27 shippou kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Jul 12 11:28:27 shippou kernel: [    0.000000] Allocating PCI resources starting at a0000000 (gap: 98000000:48000000)
Jul 12 11:28:27 shippou kernel: [    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
Jul 12 11:28:27 shippou kernel: [    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
Jul 12 11:28:27 shippou kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 612716
Jul 12 11:28:27 shippou kernel: [    0.000000] Policy zone: DMA32
Jul 12 11:28:27 shippou kernel: [    0.000000] Kernel command line: root=UUID=2e985bef-5550-421f-b1bf-e1f730273cbc ro quiet splash
Jul 12 11:28:27 shippou kernel: [    0.000000] Initializing CPU#0
Jul 12 11:28:27 shippou kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Jul 12 11:28:27 shippou kernel: [    0.000000] TSC calibrated against HPET
Jul 12 11:28:27 shippou kernel: [   11.065561] time.c: Detected 1799.787 MHz processor.
Jul 12 11:28:27 shippou kernel: [   11.066246] Console: colour VGA+ 80x25
Jul 12 11:28:27 shippou kernel: [   11.066249] console [tty0] enabled
Jul 12 11:28:27 shippou kernel: [   11.066267] Checking aperture...
Jul 12 11:28:27 shippou kernel: [   11.066270] CPU 0: aperture @ ffc0000000 size 32 MB
Jul 12 11:28:27 shippou kernel: [   11.066272] Aperture too small (32 MB)
Jul 12 11:28:27 shippou kernel: [   11.076126] No AGP bridge found
Jul 12 11:28:27 shippou kernel: [   11.109497] Memory: 2442456k/2490240k available (2489k kernel code, 47396k reserved, 1318k data, 320k init)
Jul 12 11:28:27 shippou kernel: [   11.109537] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Jul 12 11:28:27 shippou kernel: [   11.187566] Calibrating delay using timer specific routine.. 3708.81 BogoMIPS (lpj=7417631)
Jul 12 11:28:27 shippou kernel: [   11.187613] Security Framework initialized
Jul 12 11:28:27 shippou kernel: [   11.187619] SELinux:  Disabled at boot.
Jul 12 11:28:27 shippou kernel: [   11.187632] AppArmor: AppArmor initialized
Jul 12 11:28:27 shippou kernel: [   11.187636] Failure registering capabilities with primary security module.
Jul 12 11:28:27 shippou kernel: [   11.188015] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jul 12 11:28:27 shippou kernel: [   11.192039] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jul 12 11:28:27 shippou kernel: [   11.193655] Mount-cache hash table entries: 256
Jul 12 11:28:27 shippou kernel: [   11.193803] Initializing cgroup subsys ns
Jul 12 11:28:27 shippou kernel: [   11.193807] Initializing cgroup subsys cpuacct
Jul 12 11:28:27 shippou kernel: [   11.193823] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jul 12 11:28:27 shippou kernel: [   11.193825] CPU: L2 Cache: 512K (64 bytes/line)
Jul 12 11:28:27 shippou kernel: [   11.193827] CPU 0/0 -> Node 0
Jul 12 11:28:27 shippou kernel: [   11.193855] SMP alternatives: switching to UP code
Jul 12 11:28:27 shippou kernel: [   11.194527] Early unpacking initramfs... done
Jul 12 11:28:27 shippou kernel: [   11.595368] ACPI: Core revision 20070126
Jul 12 11:28:27 shippou kernel: [   11.595429] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Jul 12 11:28:27 shippou kernel: [   11.644889] Using local APIC timer interrupts.
Jul 12 11:28:27 shippou kernel: [   11.700367] Detected 12.498 MHz APIC timer.
Jul 12 11:28:27 shippou kernel: [   11.700415] Brought up 1 CPUs
Jul 12 11:28:27 shippou kernel: [   11.700687] net_namespace: 120 bytes
Jul 12 11:28:27 shippou kernel: [   11.701089] Time: 11:28:05  Date: 07/12/08
Jul 12 11:28:27 shippou kernel: [   11.701118] NET: Registered protocol family 16
Jul 12 11:28:27 shippou kernel: [   11.701291] ACPI: bus type pci registered
Jul 12 11:28:27 shippou kernel: [   11.701358] PCI: Using configuration type 1
Jul 12 11:28:27 shippou kernel: [   11.708049] ACPI: Interpreter enabled
Jul 12 11:28:27 shippou kernel: [   11.708055] ACPI: (supports S0 S3 S4 S5)
Jul 12 11:28:27 shippou kernel: [   11.708072] ACPI: Using IOAPIC for interrupt routing
Jul 12 11:28:27 shippou kernel: [   11.713263] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul 12 11:28:27 shippou kernel: [   11.713426] pci 0000:00:12.0: set SATA to AHCI mode
Jul 12 11:28:27 shippou kernel: [   11.714222] PCI: Transparent bridge - 0000:00:14.4
Jul 12 11:28:27 shippou kernel: [   11.734961] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 11:28:27 shippou kernel: [   11.735067] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 11:28:27 shippou kernel: [   11.735170] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 11:28:27 shippou kernel: [   11.735274] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 11:28:27 shippou kernel: [   11.735377] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 11:28:27 shippou kernel: [   11.735480] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 11:28:27 shippou kernel: [   11.735582] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 11:28:27 shippou kernel: [   11.735685] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 11:28:27 shippou kernel: [   11.735801] Linux Plug and Play Support v0.97 (c) Adam Belay
Jul 12 11:28:27 shippou kernel: [   11.735829] pnp: PnP ACPI init
Jul 12 11:28:27 shippou kernel: [   11.735838] ACPI: bus type pnp registered
Jul 12 11:28:27 shippou kernel: [   11.738859] pnp: PnP ACPI: found 15 devices
Jul 12 11:28:27 shippou kernel: [   11.738862] ACPI: ACPI bus type pnp unregistered
Jul 12 11:28:27 shippou kernel: [   11.739091] PCI: Using ACPI for IRQ routing
Jul 12 11:28:27 shippou kernel: [   11.739094] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jul 12 11:28:27 shippou kernel: [   11.752322] NET: Registered protocol family 8
Jul 12 11:28:27 shippou kernel: [   11.752324] NET: Registered protocol family 20
Jul 12 11:28:27 shippou kernel: [   11.752404] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Jul 12 11:28:27 shippou kernel: [   11.752408] hpet0: 4 32-bit timers, 14318180 Hz
Jul 12 11:28:27 shippou kernel: [   11.753461] AppArmor: AppArmor Filesystem Enabled
Jul 12 11:28:27 shippou kernel: [   11.756281] Time: tsc clocksource has been installed.
Jul 12 11:28:27 shippou kernel: [   11.764263] system 00:01: ioport range 0x4100-0x411f has been reserved
Jul 12 11:28:27 shippou kernel: [   11.764266] system 00:01: ioport range 0x228-0x22f has been reserved
Jul 12 11:28:27 shippou kernel: [   11.764270] system 00:01: ioport range 0x40b-0x40b has been reserved
Jul 12 11:28:27 shippou kernel: [   11.764273] system 00:01: ioport range 0x4d6-0x4d6 has been reserved
Jul 12 11:28:27 shippou kernel: [   11.764276] system 00:01: ioport range 0xc00-0xc01 has been reserved
Jul 12 11:28:27 shippou kernel: [   11.764279] system 00:01: ioport range 0xc14-0xc14 has been reserved
Jul 12 11:28:27 shippou kernel: [   11.764282] system 00:01: ioport range 0xc50-0xc52 has been reserved
Jul 12 11:28:27 shippou kernel: [   11.764285] system 00:01: ioport range 0xc6c-0xc6d has been reserved
Jul 12 11:28:27 shippou kernel: [   11.764288] system 00:01: ioport range 0xc6f-0xc6f has been reserved
Jul 12 11:28:27 shippou kernel: [   11.764291] system 00:01: ioport range 0xcd0-0xcd1 has been reserved
Jul 12 11:28:27 shippou kernel: [   11.764294] system 00:01: ioport range 0xcd2-0xcd3 has been reserved
Jul 12 11:28:27 shippou kernel: [   11.764297] system 00:01: ioport range 0xcd4-0xcdf has been reserved
Jul 12 11:28:27 shippou kernel: [   11.764300] system 00:01: ioport range 0x4000-0x40fe has been reserved
Jul 12 11:28:27 shippou kernel: [   11.764303] system 00:01: ioport range 0x4210-0x4217 has been reserved
Jul 12 11:28:27 shippou kernel: [   11.764306] system 00:01: ioport range 0xb10-0xb1f has been reserved
Jul 12 11:28:27 shippou kernel: [   11.764316] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
Jul 12 11:28:27 shippou kernel: [   11.764319] system 00:07: ioport range 0x220-0x225 has been reserved
Jul 12 11:28:27 shippou kernel: [   11.764322] system 00:07: ioport range 0xb00-0xb0f has been reserved
Jul 12 11:28:27 shippou kernel: [   11.764331] system 00:0d: iomem range 0xe0000000-0xefffffff could not be reserved
Jul 12 11:28:27 shippou kernel: [   11.764337] system 00:0e: iomem range 0xf0000-0xfffff could not be reserved
Jul 12 11:28:27 shippou kernel: [   11.764341] system 00:0e: iomem range 0xfed00000-0xfed000ff has been reserved
Jul 12 11:28:27 shippou kernel: [   11.764344] system 00:0e: iomem range 0x97fe0000-0x97ffffff could not be reserved
Jul 12 11:28:27 shippou kernel: [   11.764348] system 00:0e: iomem range 0xffff0000-0xffffffff has been reserved
Jul 12 11:28:27 shippou kernel: [   11.764351] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
Jul 12 11:28:27 shippou kernel: [   11.764354] system 00:0e: iomem range 0x100000-0x97fdffff could not be reserved
Jul 12 11:28:27 shippou kernel: [   11.764358] system 00:0e: iomem range 0x98000000-0x9fffffff has been reserved
Jul 12 11:28:27 shippou kernel: [   11.764361] system 00:0e: iomem range 0xfec00000-0xfec00fff has been reserved
Jul 12 11:28:27 shippou kernel: [   11.764364] system 00:0e: iomem range 0xfee00000-0xfee00fff could not be reserved
Jul 12 11:28:27 shippou kernel: [   11.764368] system 00:0e: iomem range 0xfff80000-0xfffeffff has been reserved
Jul 12 11:28:27 shippou kernel: [   11.764730] PCI: Bridge: 0000:00:01.0
Jul 12 11:28:27 shippou kernel: [   11.764732]   IO window: e000-efff
Jul 12 11:28:27 shippou kernel: [   11.764735]   MEM window: fdd00000-fdefffff
Jul 12 11:28:27 shippou kernel: [   11.764738]   PREFETCH window: d8000000-dfffffff
Jul 12 11:28:27 shippou kernel: [   11.764743] PCI: Bridge: 0000:00:14.4
Jul 12 11:28:27 shippou kernel: [   11.764745]   IO window: d000-dfff
Jul 12 11:28:27 shippou kernel: [   11.764750]   MEM window: fdc00000-fdcfffff
Jul 12 11:28:27 shippou kernel: [   11.764754]   PREFETCH window: fdf00000-fdffffff
Jul 12 11:28:27 shippou kernel: [   11.764780] NET: Registered protocol family 2
Jul 12 11:28:27 shippou kernel: [   11.800323] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Jul 12 11:28:27 shippou kernel: [   11.801953] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Jul 12 11:28:27 shippou kernel: [   11.809225] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jul 12 11:28:27 shippou kernel: [   11.810101] TCP: Hash tables configured (established 524288 bind 65536)
Jul 12 11:28:27 shippou kernel: [   11.810105] TCP reno registered
Jul 12 11:28:27 shippou kernel: [   11.820298] checking if image is initramfs... it is
Jul 12 11:28:27 shippou kernel: [   12.524979] Freeing initrd memory: 8212k freed
Jul 12 11:28:27 shippou kernel: [   12.532120] audit: initializing netlink socket (disabled)
Jul 12 11:28:27 shippou kernel: [   12.532134] audit(1215862085.416:1): initialized
Jul 12 11:28:27 shippou kernel: [   12.534105] VFS: Disk quotas dquot_6.5.1
Jul 12 11:28:27 shippou kernel: [   12.534176] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jul 12 11:28:27 shippou kernel: [   12.534317] io scheduler noop registered
Jul 12 11:28:27 shippou kernel: [   12.534319] io scheduler anticipatory registered
Jul 12 11:28:27 shippou kernel: [   12.534321] io scheduler deadline registered
Jul 12 11:28:27 shippou kernel: [   12.534425] io scheduler cfq registered (default)
Jul 12 11:28:27 shippou kernel: [   12.703281] Real Time Clock Driver v1.12ac
Jul 12 11:28:27 shippou kernel: [   12.703507] Linux agpgart interface v0.102
Jul 12 11:28:27 shippou kernel: [   12.703509] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jul 12 11:28:27 shippou kernel: [   12.703659] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 12 11:28:27 shippou kernel: [   12.704254] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 12 11:28:27 shippou kernel: [   12.704950] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jul 12 11:28:27 shippou kernel: [   12.705018] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jul 12 11:28:27 shippou kernel: [   12.705107] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jul 12 11:28:27 shippou kernel: [   12.705443] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 12 11:28:27 shippou kernel: [   12.705447] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 12 11:28:27 shippou kernel: [   12.714834] mice: PS/2 mouse device common for all mice
Jul 12 11:28:27 shippou kernel: [   12.714870] cpuidle: using governor ladder
Jul 12 11:28:27 shippou kernel: [   12.714872] cpuidle: using governor menu
Jul 12 11:28:27 shippou kernel: [   12.715025] NET: Registered protocol family 1
Jul 12 11:28:27 shippou kernel: [   12.715122] registered taskstats version 1
Jul 12 11:28:27 shippou kernel: [   12.715242]   Magic number: 0:0:479
Jul 12 11:28:27 shippou kernel: [   12.715393] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
Jul 12 11:28:27 shippou kernel: [   12.715396] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 12 11:28:27 shippou kernel: [   12.715398] EDD information not available.
Jul 12 11:28:27 shippou kernel: [   12.715406] Freeing unused kernel memory: 320k freed
Jul 12 11:28:27 shippou kernel: [   12.742580] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jul 12 11:28:27 shippou kernel: [   13.916214] fuse init (API version 7.9)
Jul 12 11:28:27 shippou kernel: [   13.931473] ACPI: Fan [FAN] (on)
Jul 12 11:28:27 shippou kernel: [   13.937339] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Jul 12 11:28:27 shippou kernel: [   13.938674] ACPI: Thermal Zone [THRM] (40 C)
Jul 12 11:28:27 shippou kernel: [   14.504197] usbcore: registered new interface driver usbfs
Jul 12 11:28:27 shippou kernel: [   14.504219] usbcore: registered new interface driver hub
Jul 12 11:28:27 shippou kernel: [   14.516866] SCSI subsystem initialized
Jul 12 11:28:27 shippou kernel: [   14.530589] usbcore: registered new device driver usb
Jul 12 11:28:27 shippou kernel: [   14.563497] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 11:28:27 shippou kernel: [   14.563606] ohci_hcd 0000:00:13.0: OHCI Host Controller
Jul 12 11:28:27 shippou kernel: [   14.563860] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Jul 12 11:28:27 shippou kernel: [   14.563885] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02e000
Jul 12 11:28:27 shippou kernel: [   14.607800] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jul 12 11:28:27 shippou kernel: [   14.607807] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jul 12 11:28:27 shippou kernel: [   14.623574] usb usb1: configuration #1 chosen from 1 choice
Jul 12 11:28:27 shippou kernel: [   14.623601] hub 1-0:1.0: USB hub found
Jul 12 11:28:27 shippou kernel: [   14.623611] hub 1-0:1.0: 2 ports detected
Jul 12 11:28:27 shippou kernel: [   14.727245] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 17
Jul 12 11:28:27 shippou kernel: [   14.727368] ohci_hcd 0000:00:13.1: OHCI Host Controller
Jul 12 11:28:27 shippou kernel: [   14.727430] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Jul 12 11:28:27 shippou kernel: [   14.727457] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfe02d000
Jul 12 11:28:27 shippou kernel: [   14.787732] usb usb2: configuration #1 chosen from 1 choice
Jul 12 11:28:27 shippou kernel: [   14.787757] hub 2-0:1.0: USB hub found
Jul 12 11:28:27 shippou kernel: [   14.787767] hub 2-0:1.0: 2 ports detected
Jul 12 11:28:27 shippou kernel: [   14.788176] Floppy drive(s): fd0 is 1.44M
Jul 12 11:28:27 shippou kernel: [   14.806765] FDC 0 is a post-1991 82077
Jul 12 11:28:27 shippou kernel: [   14.890979] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 18
Jul 12 11:28:27 shippou kernel: [   14.891108] ohci_hcd 0000:00:13.2: OHCI Host Controller
Jul 12 11:28:27 shippou kernel: [   14.891174] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
Jul 12 11:28:27 shippou kernel: [   14.891198] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfe02c000
Jul 12 11:28:27 shippou kernel: [   14.951010] usb usb3: configuration #1 chosen from 1 choice
Jul 12 11:28:27 shippou kernel: [   14.951034] hub 3-0:1.0: USB hub found
Jul 12 11:28:27 shippou kernel: [   14.951044] hub 3-0:1.0: 2 ports detected
Jul 12 11:28:27 shippou kernel: [   15.054687] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 17
Jul 12 11:28:27 shippou kernel: [   15.054827] ohci_hcd 0000:00:13.3: OHCI Host Controller
Jul 12 11:28:27 shippou kernel: [   15.054889] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
Jul 12 11:28:27 shippou kernel: [   15.054908] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfe02b000
Jul 12 11:28:27 shippou kernel: [   15.114698] usb usb4: configuration #1 chosen from 1 choice
Jul 12 11:28:27 shippou kernel: [   15.114725] hub 4-0:1.0: USB hub found
Jul 12 11:28:27 shippou kernel: [   15.114735] hub 4-0:1.0: 2 ports detected
Jul 12 11:28:27 shippou kernel: [   15.218378] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 18
Jul 12 11:28:27 shippou kernel: [   15.218512] ohci_hcd 0000:00:13.4: OHCI Host Controller
Jul 12 11:28:27 shippou kernel: [   15.218575] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
Jul 12 11:28:27 shippou kernel: [   15.218594] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfe02a000
Jul 12 11:28:27 shippou kernel: [   15.278477] usb usb5: configuration #1 chosen from 1 choice
Jul 12 11:28:27 shippou kernel: [   15.278503] hub 5-0:1.0: USB hub found
Jul 12 11:28:27 shippou kernel: [   15.278513] hub 5-0:1.0: 2 ports detected
Jul 12 11:28:27 shippou kernel: [   15.382217] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 19
Jul 12 11:28:27 shippou kernel: [   15.382359] ehci_hcd 0000:00:13.5: EHCI Host Controller
Jul 12 11:28:27 shippou kernel: [   15.382422] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
Jul 12 11:28:27 shippou kernel: [   15.382463] ehci_hcd 0000:00:13.5: debug port 1
Jul 12 11:28:27 shippou kernel: [   15.382482] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfe029000
Jul 12 11:28:27 shippou kernel: [   15.394000] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jul 12 11:28:27 shippou kernel: [   15.394127] usb usb6: configuration #1 chosen from 1 choice
Jul 12 11:28:27 shippou kernel: [   15.394152] hub 6-0:1.0: USB hub found
Jul 12 11:28:27 shippou kernel: [   15.394159] hub 6-0:1.0: 10 ports detected
Jul 12 11:28:27 shippou kernel: [   15.498030] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 11:28:27 shippou kernel: [   15.498189] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
Jul 12 11:28:27 shippou kernel: [   15.498195] ahci 0000:00:12.0: controller can't do PMP, turning off CAP_PMP
Jul 12 11:28:27 shippou kernel: [   16.500063] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Jul 12 11:28:27 shippou kernel: [   16.500068] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pio slum part 
Jul 12 11:28:27 shippou kernel: [   16.501255] scsi0 : ahci
Jul 12 11:28:27 shippou kernel: [   16.501580] scsi1 : ahci
Jul 12 11:28:27 shippou kernel: [   16.501728] scsi2 : ahci
Jul 12 11:28:27 shippou kernel: [   16.501874] scsi3 : ahci
Jul 12 11:28:27 shippou kernel: [   16.501952] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 16
Jul 12 11:28:27 shippou kernel: [   16.501957] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 16
Jul 12 11:28:27 shippou kernel: [   16.501961] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 16
Jul 12 11:28:27 shippou kernel: [   16.501965] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 16
Jul 12 11:28:27 shippou kernel: [   16.975206] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 12 11:28:27 shippou kernel: [   17.018564] ata1.00: ATA-7: ST380215AS, 3.AAD, max UDMA/133
Jul 12 11:28:27 shippou kernel: [   17.018567] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32)
Jul 12 11:28:27 shippou kernel: [   17.076789] ata1.00: configured for UDMA/133
Jul 12 11:28:27 shippou kernel: [   17.386486] ata2: SATA link down (SStatus 0 SControl 300)
Jul 12 11:28:27 shippou kernel: [   17.697944] ata3: SATA link down (SStatus 0 SControl 300)
Jul 12 11:28:27 shippou kernel: [   18.009403] ata4: SATA link down (SStatus 0 SControl 300)
Jul 12 11:28:27 shippou kernel: [   18.009525] scsi 0:0:0:0: Direct-Access     ATA      ST380215AS       3.AA PQ: 0 ANSI: 5
Jul 12 11:28:27 shippou kernel: [   18.010946] SB600_PATA: IDE controller (0x1002:0x438c rev 0x00) at  PCI slot 0000:00:14.1
Jul 12 11:28:27 shippou kernel: [   18.010958] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 11:28:27 shippou kernel: [   18.010969] SB600_PATA: not 100% native mode: will probe irqs later
Jul 12 11:28:27 shippou kernel: [   18.010978]     ide0: BM-DMA at 0xf900-0xf907, BIOS settings: hda:pio, hdb:DMA
Jul 12 11:28:27 shippou kernel: [   18.024164] Driver 'sd' needs updating - please use bus_type methods
Jul 12 11:28:27 shippou kernel: [   18.025443] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jul 12 11:28:27 shippou kernel: [   18.025456] sd 0:0:0:0: [sda] Write Protect is off
Jul 12 11:28:27 shippou kernel: [   18.025474] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 12 11:28:27 shippou kernel: [   18.025532] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jul 12 11:28:27 shippou kernel: [   18.025540] sd 0:0:0:0: [sda] Write Protect is off
Jul 12 11:28:27 shippou kernel: [   18.025556] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 12 11:28:27 shippou kernel: [   18.025560]  sda: sda1 sda2 sda3 sda4
Jul 12 11:28:27 shippou kernel: [   18.076403] sd 0:0:0:0: [sda] Attached SCSI disk
Jul 12 11:28:27 shippou kernel: [   18.082844] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 12 11:28:27 shippou kernel: [   18.474921] Attempting manual resume
Jul 12 11:28:27 shippou kernel: [   18.522196] kjournald starting.  Commit interval 5 seconds
Jul 12 11:28:27 shippou kernel: [   18.522208] EXT3-fs: mounted filesystem with ordered data mode.
Jul 12 11:28:27 shippou kernel: [   18.796360] hdb: LITE-ON DVDRW LH-20A1P, ATAPI CD/DVD-ROM drive
Jul 12 11:28:27 shippou kernel: [   19.075887] hdb: UDMA/66 mode selected
Jul 12 11:28:27 shippou kernel: [   19.076263] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Jul 12 11:28:27 shippou kernel: [   19.089208] r8169 Gigabit Ethernet driver 2.2LK loaded
Jul 12 11:28:27 shippou kernel: [   19.089244] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 22 (level, low) -> IRQ 22
Jul 12 11:28:27 shippou kernel: [   19.089474] eth0: RTL8169sc/8110sc at 0xffffc20001044000, 00:19:21:21:21:b5, XID 18000000 IRQ 22
Jul 12 11:28:27 shippou kernel: [   25.330777] input: PC Speaker as /devices/platform/pcspkr/input/input2
Jul 12 11:28:27 shippou kernel: [   25.442564] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 12 11:28:27 shippou kernel: [   25.472228] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul 12 11:28:27 shippou kernel: [   25.612230] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Jul 12 11:28:27 shippou kernel: [   25.789812] input: Power Button (FF) as /devices/virtual/input/input3
Jul 12 11:28:27 shippou kernel: [   25.811860] ACPI: Power Button (FF) [PWRF]
Jul 12 11:28:27 shippou kernel: [   25.811929] input: Power Button (CM) as /devices/virtual/input/input4
Jul 12 11:28:27 shippou kernel: [   25.843875] ACPI: Power Button (CM) [PWRB]
Jul 12 11:28:27 shippou kernel: [   25.971099] input: ImExPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Jul 12 11:28:27 shippou kernel: [   25.998966] parport_pc 00:0a: reported by Plug and Play ACPI
Jul 12 11:28:27 shippou kernel: [   25.999023] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jul 12 11:28:27 shippou kernel: [   27.439438] r8169: eth0: link down
Jul 12 11:28:27 shippou kernel: [   27.603495] hdb: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
Jul 12 11:28:27 shippou kernel: [   27.603503] Uniform CD-ROM driver Revision: 3.20
Jul 12 11:28:27 shippou kernel: [   27.675875] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 11:28:27 shippou kernel: [   27.698379] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
Jul 12 11:28:27 shippou kernel: [   27.981960] NET: Registered protocol family 10
Jul 12 11:28:27 shippou kernel: [   27.982169] lo: Disabled Privacy Extensions
Jul 12 11:28:27 shippou kernel: [   27.982493] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 12 11:28:27 shippou kernel: [   30.661400] lp0: using parport0 (interrupt-driven).
Jul 12 11:28:27 shippou kernel: [   30.754120] Adding 289160k swap on /dev/sda3.  Priority:-1 extents:1 across:289160k
Jul 12 11:28:27 shippou kernel: [   31.308910] EXT3 FS on sda2, internal journal
Jul 12 11:28:27 shippou kernel: [   32.225303] kjournald starting.  Commit interval 5 seconds
Jul 12 11:28:27 shippou kernel: [   32.225498] EXT3 FS on sda4, internal journal
Jul 12 11:28:27 shippou kernel: [   32.225503] EXT3-fs: mounted filesystem with ordered data mode.
Jul 12 11:28:27 shippou kernel: [   32.661022] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul 12 11:28:27 shippou kernel: [   33.142346] No dock devices found.
Jul 12 11:28:27 shippou kernel: [   33.393245] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (1 cpu cores) (version 2.20.00)
Jul 12 11:28:27 shippou kernel: [   33.393285] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
Jul 12 11:28:27 shippou kernel: [   33.393288] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
Jul 12 11:28:27 shippou kernel: [   34.232496] ppdev: user-space parallel port driver
Jul 12 11:28:47 shippou kernel: [   54.351583] audit(1215833327.837:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4837 profile="/usr/sbin/cupsd" namespace="default"
Jul 12 11:29:07 shippou dhcdbd: Started up.
Jul 12 11:29:09 shippou kernel: [   75.970050] Bluetooth: Core ver 2.11
Jul 12 11:29:09 shippou kernel: [   75.970701] NET: Registered protocol family 31
Jul 12 11:29:09 shippou kernel: [   75.970706] Bluetooth: HCI device and connection manager initialized
Jul 12 11:29:09 shippou kernel: [   75.970710] Bluetooth: HCI socket layer initialized
Jul 12 11:29:09 shippou kernel: [   76.014910] Bluetooth: L2CAP ver 2.9
Jul 12 11:29:09 shippou kernel: [   76.014915] Bluetooth: L2CAP socket layer initialized
Jul 12 11:29:09 shippou kernel: [   76.073165] Bluetooth: RFCOMM socket layer initialized
Jul 12 11:29:09 shippou kernel: [   76.073188] Bluetooth: RFCOMM TTY layer initialized
Jul 12 11:29:09 shippou kernel: [   76.073190] Bluetooth: RFCOMM ver 1.8
Jul 12 11:29:09 shippou kernel: [   76.379942] Marking TSC unstable due to cpufreq changes
Jul 12 11:29:09 shippou kernel: [   76.383778] Time: hpet clocksource has been installed.
Jul 12 11:29:10 shippou kernel: [   76.727654] Clocksource tsc unstable (delta = -222224053 ns)
Jul 12 11:29:10 shippou kernel: [   76.936875] [drm] Initialized drm 1.1.0 20060810
Jul 12 11:29:17 shippou kernel: [   80.503736] hda-intel: Invalid position buffer, using LPIB read method instead.
Jul 12 11:40:34 shippou kernel: [  472.588876] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jul 12 11:40:35 shippou exiting on signal 15
Jul 12 11:41:16 shippou syslogd 1.5.0#1ubuntu1: restart.
Jul 12 11:41:16 shippou kernel: Inspecting /boot/System.map-2.6.24-19-generic
Jul 12 11:41:16 shippou kernel: Loaded 28491 symbols from /boot/System.map-2.6.24-19-generic.
Jul 12 11:41:16 shippou kernel: Symbols match kernel version 2.6.24.
Jul 12 11:41:16 shippou kernel: Loaded 16834 symbols from 77 modules.
Jul 12 11:41:16 shippou kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 12 11:41:16 shippou kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 12 11:41:16 shippou kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:15:37 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
Jul 12 11:41:16 shippou kernel: [    0.000000] Command line: root=UUID=2e985bef-5550-421f-b1bf-e1f730273cbc ro quiet splash
Jul 12 11:41:16 shippou kernel: [    0.000000] BIOS-provided physical RAM map:
Jul 12 11:41:16 shippou kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jul 12 11:41:16 shippou kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jul 12 11:41:16 shippou kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jul 12 11:41:16 shippou kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000097fe0000 (usable)
Jul 12 11:41:16 shippou kernel: [    0.000000]  BIOS-e820: 0000000097fe0000 - 0000000097fe3000 (ACPI NVS)
Jul 12 11:41:16 shippou kernel: [    0.000000]  BIOS-e820: 0000000097fe3000 - 0000000097ff0000 (ACPI data)
Jul 12 11:41:16 shippou kernel: [    0.000000]  BIOS-e820: 0000000097ff0000 - 0000000098000000 (reserved)
Jul 12 11:41:16 shippou kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Jul 12 11:41:16 shippou kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Jul 12 11:41:16 shippou kernel: [    0.000000] end_pfn_map = 1048576
Jul 12 11:41:16 shippou kernel: [    0.000000] DMI 2.5 present.
Jul 12 11:41:16 shippou kernel: [    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F7B80 checksum 0
Jul 12 11:41:16 shippou kernel: [    0.000000] ACPI: RSDP 000F7B80, 0024 (r2 RS690 )
Jul 12 11:41:16 shippou kernel: [    0.000000] ACPI: RSDT 97FE3040, 0038 (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 12 11:41:16 shippou kernel: [    0.000000] ACPI: FACP 97FE30C0, 0074 (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 12 11:41:16 shippou kernel: [    0.000000] ACPI: DSDT 97FE3180, 4B0B (r1 RS690  AWRDACPI     1000 MSFT  3000000)
Jul 12 11:41:16 shippou kernel: [    0.000000] ACPI: FACS 97FE0000, 0040
Jul 12 11:41:16 shippou kernel: [    0.000000] ACPI: SSDT 97FE7DC0, 00D3 (r1 PTLTD  POWERNOW        1  LTP        1)
Jul 12 11:41:16 shippou kernel: [    0.000000] ACPI: HPET 97FE7F00, 0038 (r1 RS690  AWRDACPI 42302E31 AWRD       98)
Jul 12 11:41:16 shippou kernel: [    0.000000] ACPI: MCFG 97FE7F80, 003C (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 12 11:41:16 shippou kernel: [    0.000000] ACPI: APIC 97FE7D00, 0068 (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 12 11:41:16 shippou kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Jul 12 11:41:16 shippou kernel: [    0.000000] CPU has 1 num_cores
Jul 12 11:41:16 shippou kernel: [    0.000000] No NUMA configuration found
Jul 12 11:41:16 shippou kernel: [    0.000000] Faking a node at 0000000000000000-0000000097fe0000
Jul 12 11:41:16 shippou kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000097fe0000
Jul 12 11:41:16 shippou kernel: [    0.000000] Zone PFN ranges:
Jul 12 11:41:16 shippou kernel: [    0.000000]   DMA             0 ->     4096
Jul 12 11:41:16 shippou kernel: [    0.000000]   DMA32        4096 ->  1048576
Jul 12 11:41:16 shippou kernel: [    0.000000]   Normal    1048576 ->  1048576
Jul 12 11:41:16 shippou kernel: [    0.000000] Movable zone start PFN for each node
Jul 12 11:41:16 shippou kernel: [    0.000000] early_node_map[2] active PFN ranges
Jul 12 11:41:16 shippou kernel: [    0.000000]     0:        0 ->      159
Jul 12 11:41:16 shippou kernel: [    0.000000]     0:      256 ->   622560
Jul 12 11:41:16 shippou kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Jul 12 11:41:16 shippou kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Jul 12 11:41:16 shippou kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul 12 11:41:16 shippou kernel: [    0.000000] Processor #0 (Bootup-CPU)
Jul 12 11:41:16 shippou kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Jul 12 11:41:16 shippou kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul 12 11:41:16 shippou kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jul 12 11:41:16 shippou kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jul 12 11:41:16 shippou kernel: [    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
Jul 12 11:41:16 shippou kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 12 11:41:16 shippou kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jul 12 11:41:16 shippou kernel: [    0.000000] Setting APIC routing to flat
Jul 12 11:41:16 shippou kernel: [    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
Jul 12 11:41:16 shippou kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 12 11:41:16 shippou kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Jul 12 11:41:16 shippou kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Jul 12 11:41:16 shippou kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Jul 12 11:41:16 shippou kernel: [    0.000000] Allocating PCI resources starting at a0000000 (gap: 98000000:48000000)
Jul 12 11:41:16 shippou kernel: [    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
Jul 12 11:41:16 shippou kernel: [    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
Jul 12 11:41:16 shippou kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 612716
Jul 12 11:41:16 shippou kernel: [    0.000000] Policy zone: DMA32
Jul 12 11:41:16 shippou kernel: [    0.000000] Kernel command line: root=UUID=2e985bef-5550-421f-b1bf-e1f730273cbc ro quiet splash
Jul 12 11:41:16 shippou kernel: [    0.000000] Initializing CPU#0
Jul 12 11:41:16 shippou kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Jul 12 11:41:16 shippou kernel: [    0.000000] TSC calibrated against HPET
Jul 12 11:41:16 shippou kernel: [    9.549772] time.c: Detected 1799.789 MHz processor.
Jul 12 11:41:16 shippou kernel: [    9.550461] Console: colour VGA+ 80x25
Jul 12 11:41:16 shippou kernel: [    9.550464] console [tty0] enabled
Jul 12 11:41:16 shippou kernel: [    9.550481] Checking aperture...
Jul 12 11:41:16 shippou kernel: [    9.550484] CPU 0: aperture @ ffc0000000 size 32 MB
Jul 12 11:41:16 shippou kernel: [    9.550485] Aperture too small (32 MB)
Jul 12 11:41:16 shippou kernel: [    9.560338] No AGP bridge found
Jul 12 11:41:16 shippou kernel: [    9.593080] Memory: 2442456k/2490240k available (2489k kernel code, 47396k reserved, 1318k data, 320k init)
Jul 12 11:41:16 shippou kernel: [    9.593119] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Jul 12 11:41:16 shippou kernel: [    9.671773] Calibrating delay using timer specific routine.. 3708.91 BogoMIPS (lpj=7417829)
Jul 12 11:41:16 shippou kernel: [    9.671819] Security Framework initialized
Jul 12 11:41:16 shippou kernel: [    9.671825] SELinux:  Disabled at boot.
Jul 12 11:41:16 shippou kernel: [    9.671838] AppArmor: AppArmor initialized
Jul 12 11:41:16 shippou kernel: [    9.671842] Failure registering capabilities with primary security module.
Jul 12 11:41:16 shippou kernel: [    9.672221] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jul 12 11:41:16 shippou kernel: [    9.676245] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jul 12 11:41:16 shippou kernel: [    9.677864] Mount-cache hash table entries: 256
Jul 12 11:41:16 shippou kernel: [    9.678014] Initializing cgroup subsys ns
Jul 12 11:41:16 shippou kernel: [    9.678018] Initializing cgroup subsys cpuacct
Jul 12 11:41:16 shippou kernel: [    9.678035] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jul 12 11:41:16 shippou kernel: [    9.678037] CPU: L2 Cache: 512K (64 bytes/line)
Jul 12 11:41:16 shippou kernel: [    9.678039] CPU 0/0 -> Node 0
Jul 12 11:41:16 shippou kernel: [    9.678067] SMP alternatives: switching to UP code
Jul 12 11:41:16 shippou kernel: [    9.678755] Early unpacking initramfs... done
Jul 12 11:41:16 shippou kernel: [   10.079495] ACPI: Core revision 20070126
Jul 12 11:41:16 shippou kernel: [   10.079557] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Jul 12 11:41:16 shippou kernel: [   10.129020] Using local APIC timer interrupts.
Jul 12 11:41:16 shippou kernel: [   10.184498] Detected 12.498 MHz APIC timer.
Jul 12 11:41:16 shippou kernel: [   10.184547] Brought up 1 CPUs
Jul 12 11:41:16 shippou kernel: [   10.184820] net_namespace: 120 bytes
Jul 12 11:41:16 shippou kernel: [   10.185221] Time: 11:40:54  Date: 07/12/08
Jul 12 11:41:16 shippou kernel: [   10.185250] NET: Registered protocol family 16
Jul 12 11:41:16 shippou kernel: [   10.185422] ACPI: bus type pci registered
Jul 12 11:41:16 shippou kernel: [   10.185489] PCI: Using configuration type 1
Jul 12 11:41:16 shippou kernel: [   10.192193] ACPI: Interpreter enabled
Jul 12 11:41:16 shippou kernel: [   10.192199] ACPI: (supports S0 S3 S4 S5)
Jul 12 11:41:16 shippou kernel: [   10.192215] ACPI: Using IOAPIC for interrupt routing
Jul 12 11:41:16 shippou kernel: [   10.197404] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul 12 11:41:16 shippou kernel: [   10.197566] pci 0000:00:12.0: set SATA to AHCI mode
Jul 12 11:41:16 shippou kernel: [   10.198361] PCI: Transparent bridge - 0000:00:14.4
Jul 12 11:41:16 shippou kernel: [   10.219110] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 11:41:16 shippou kernel: [   10.219216] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 11:41:16 shippou kernel: [   10.219319] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 11:41:16 shippou kernel: [   10.219422] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 11:41:16 shippou kernel: [   10.219526] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 11:41:16 shippou kernel: [   10.219628] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 11:41:16 shippou kernel: [   10.219731] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 11:41:16 shippou kernel: [   10.219834] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 11:41:16 shippou kernel: [   10.219950] Linux Plug and Play Support v0.97 (c) Adam Belay
Jul 12 11:41:16 shippou kernel: [   10.219979] pnp: PnP ACPI init
Jul 12 11:41:16 shippou kernel: [   10.219988] ACPI: bus type pnp registered
Jul 12 11:41:16 shippou kernel: [   10.223007] pnp: PnP ACPI: found 15 devices
Jul 12 11:41:16 shippou kernel: [   10.223010] ACPI: ACPI bus type pnp unregistered
Jul 12 11:41:16 shippou kernel: [   10.223235] PCI: Using ACPI for IRQ routing
Jul 12 11:41:16 shippou kernel: [   10.223238] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jul 12 11:41:16 shippou kernel: [   10.236454] NET: Registered protocol family 8
Jul 12 11:41:16 shippou kernel: [   10.236456] NET: Registered protocol family 20
Jul 12 11:41:16 shippou kernel: [   10.236536] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Jul 12 11:41:16 shippou kernel: [   10.236540] hpet0: 4 32-bit timers, 14318180 Hz
Jul 12 11:41:16 shippou kernel: [   10.237597] AppArmor: AppArmor Filesystem Enabled
Jul 12 11:41:16 shippou kernel: [   10.240413] Time: tsc clocksource has been installed.
Jul 12 11:41:16 shippou kernel: [   10.248396] system 00:01: ioport range 0x4100-0x411f has been reserved
Jul 12 11:41:16 shippou kernel: [   10.248399] system 00:01: ioport range 0x228-0x22f has been reserved
Jul 12 11:41:16 shippou kernel: [   10.248403] system 00:01: ioport range 0x40b-0x40b has been reserved
Jul 12 11:41:16 shippou kernel: [   10.248406] system 00:01: ioport range 0x4d6-0x4d6 has been reserved
Jul 12 11:41:16 shippou kernel: [   10.248409] system 00:01: ioport range 0xc00-0xc01 has been reserved
Jul 12 11:41:16 shippou kernel: [   10.248412] system 00:01: ioport range 0xc14-0xc14 has been reserved
Jul 12 11:41:16 shippou kernel: [   10.248415] system 00:01: ioport range 0xc50-0xc52 has been reserved
Jul 12 11:41:16 shippou kernel: [   10.248418] system 00:01: ioport range 0xc6c-0xc6d has been reserved
Jul 12 11:41:16 shippou kernel: [   10.248421] system 00:01: ioport range 0xc6f-0xc6f has been reserved
Jul 12 11:41:16 shippou kernel: [   10.248424] system 00:01: ioport range 0xcd0-0xcd1 has been reserved
Jul 12 11:41:16 shippou kernel: [   10.248427] system 00:01: ioport range 0xcd2-0xcd3 has been reserved
Jul 12 11:41:16 shippou kernel: [   10.248430] system 00:01: ioport range 0xcd4-0xcdf has been reserved
Jul 12 11:41:16 shippou kernel: [   10.248433] system 00:01: ioport range 0x4000-0x40fe has been reserved
Jul 12 11:41:16 shippou kernel: [   10.248436] system 00:01: ioport range 0x4210-0x4217 has been reserved
Jul 12 11:41:16 shippou kernel: [   10.248439] system 00:01: ioport range 0xb10-0xb1f has been reserved
Jul 12 11:41:16 shippou kernel: [   10.248449] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
Jul 12 11:41:16 shippou kernel: [   10.248452] system 00:07: ioport range 0x220-0x225 has been reserved
Jul 12 11:41:16 shippou kernel: [   10.248455] system 00:07: ioport range 0xb00-0xb0f has been reserved
Jul 12 11:41:16 shippou kernel: [   10.248464] system 00:0d: iomem range 0xe0000000-0xefffffff could not be reserved
Jul 12 11:41:16 shippou kernel: [   10.248470] system 00:0e: iomem range 0xf0000-0xfffff could not be reserved
Jul 12 11:41:16 shippou kernel: [   10.248474] system 00:0e: iomem range 0xfed00000-0xfed000ff has been reserved
Jul 12 11:41:16 shippou kernel: [   10.248477] system 00:0e: iomem range 0x97fe0000-0x97ffffff could not be reserved
Jul 12 11:41:16 shippou kernel: [   10.248481] system 00:0e: iomem range 0xffff0000-0xffffffff has been reserved
Jul 12 11:41:16 shippou kernel: [   10.248484] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
Jul 12 11:41:16 shippou kernel: [   10.248487] system 00:0e: iomem range 0x100000-0x97fdffff could not be reserved
Jul 12 11:41:16 shippou kernel: [   10.248491] system 00:0e: iomem range 0x98000000-0x9fffffff has been reserved
Jul 12 11:41:16 shippou kernel: [   10.248494] system 00:0e: iomem range 0xfec00000-0xfec00fff has been reserved
Jul 12 11:41:16 shippou kernel: [   10.248497] system 00:0e: iomem range 0xfee00000-0xfee00fff could not be reserved
Jul 12 11:41:16 shippou kernel: [   10.248501] system 00:0e: iomem range 0xfff80000-0xfffeffff has been reserved
Jul 12 11:41:16 shippou kernel: [   10.248858] PCI: Bridge: 0000:00:01.0
Jul 12 11:41:16 shippou kernel: [   10.248860]   IO window: e000-efff
Jul 12 11:41:16 shippou kernel: [   10.248863]   MEM window: fdd00000-fdefffff
Jul 12 11:41:16 shippou kernel: [   10.248866]   PREFETCH window: d8000000-dfffffff
Jul 12 11:41:16 shippou kernel: [   10.248870] PCI: Bridge: 0000:00:14.4
Jul 12 11:41:16 shippou kernel: [   10.248873]   IO window: d000-dfff
Jul 12 11:41:16 shippou kernel: [   10.248878]   MEM window: fdc00000-fdcfffff
Jul 12 11:41:16 shippou kernel: [   10.248882]   PREFETCH window: fdf00000-fdffffff
Jul 12 11:41:16 shippou kernel: [   10.248906] NET: Registered protocol family 2
Jul 12 11:41:16 shippou kernel: [   10.284455] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Jul 12 11:41:16 shippou kernel: [   10.286083] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Jul 12 11:41:16 shippou kernel: [   10.293394] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jul 12 11:41:16 shippou kernel: [   10.294273] TCP: Hash tables configured (established 524288 bind 65536)
Jul 12 11:41:16 shippou kernel: [   10.294277] TCP reno registered
Jul 12 11:41:16 shippou kernel: [   10.304430] checking if image is initramfs... it is
Jul 12 11:41:16 shippou kernel: [   11.009067] Freeing initrd memory: 8212k freed
Jul 12 11:41:16 shippou kernel: [   11.016196] audit: initializing netlink socket (disabled)
Jul 12 11:41:16 shippou kernel: [   11.016210] audit(1215862854.416:1): initialized
Jul 12 11:41:16 shippou kernel: [   11.018185] VFS: Disk quotas dquot_6.5.1
Jul 12 11:41:16 shippou kernel: [   11.018257] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jul 12 11:41:16 shippou kernel: [   11.018398] io scheduler noop registered
Jul 12 11:41:16 shippou kernel: [   11.018400] io scheduler anticipatory registered
Jul 12 11:41:16 shippou kernel: [   11.018402] io scheduler deadline registered
Jul 12 11:41:16 shippou kernel: [   11.018507] io scheduler cfq registered (default)
Jul 12 11:41:16 shippou kernel: [   11.187112] Real Time Clock Driver v1.12ac
Jul 12 11:41:16 shippou kernel: [   11.187336] Linux agpgart interface v0.102
Jul 12 11:41:16 shippou kernel: [   11.187338] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jul 12 11:41:16 shippou kernel: [   11.187489] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 12 11:41:16 shippou kernel: [   11.188081] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 12 11:41:16 shippou kernel: [   11.188779] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jul 12 11:41:16 shippou kernel: [   11.188846] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jul 12 11:41:16 shippou kernel: [   11.188934] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jul 12 11:41:16 shippou kernel: [   11.189270] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 12 11:41:16 shippou kernel: [   11.189274] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 12 11:41:16 shippou kernel: [   11.194966] mice: PS/2 mouse device common for all mice
Jul 12 11:41:16 shippou kernel: [   11.195001] cpuidle: using governor ladder
Jul 12 11:41:16 shippou kernel: [   11.195003] cpuidle: using governor menu
Jul 12 11:41:16 shippou kernel: [   11.195154] NET: Registered protocol family 1
Jul 12 11:41:16 shippou kernel: [   11.195250] registered taskstats version 1
Jul 12 11:41:16 shippou kernel: [   11.195371]   Magic number: 0:206:681
Jul 12 11:41:16 shippou kernel: [   11.195522] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
Jul 12 11:41:16 shippou kernel: [   11.195524] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 12 11:41:16 shippou kernel: [   11.195526] EDD information not available.
Jul 12 11:41:16 shippou kernel: [   11.195534] Freeing unused kernel memory: 320k freed
Jul 12 11:41:16 shippou kernel: [   11.222721] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jul 12 11:41:16 shippou kernel: [   12.394749] fuse init (API version 7.9)
Jul 12 11:41:16 shippou kernel: [   12.409140] ACPI: Fan [FAN] (on)
Jul 12 11:41:16 shippou kernel: [   12.415843] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Jul 12 11:41:16 shippou kernel: [   12.417190] ACPI: Thermal Zone [THRM] (40 C)
Jul 12 11:41:16 shippou kernel: [   12.959902] SCSI subsystem initialized
Jul 12 11:41:16 shippou kernel: [   13.031632] usbcore: registered new interface driver usbfs
Jul 12 11:41:16 shippou kernel: [   13.031654] usbcore: registered new interface driver hub
Jul 12 11:41:16 shippou kernel: [   13.040502] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 11:41:16 shippou kernel: [   13.040640] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
Jul 12 11:41:16 shippou kernel: [   13.040647] ahci 0000:00:12.0: controller can't do PMP, turning off CAP_PMP
Jul 12 11:41:16 shippou kernel: [   13.051603] usbcore: registered new device driver usb
Jul 12 11:41:16 shippou kernel: [   13.063544] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jul 12 11:41:16 shippou kernel: [   13.064518] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jul 12 11:41:16 shippou kernel: [   13.252899] Floppy drive(s): fd0 is 1.44M
Jul 12 11:41:16 shippou kernel: [   13.270937] FDC 0 is a post-1991 82077
Jul 12 11:41:16 shippou kernel: [   14.041838] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Jul 12 11:41:16 shippou kernel: [   14.041843] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pio slum part 
Jul 12 11:41:16 shippou kernel: [   14.043050] scsi0 : ahci
Jul 12 11:41:16 shippou kernel: [   14.043381] scsi1 : ahci
Jul 12 11:41:16 shippou kernel: [   14.043531] scsi2 : ahci
Jul 12 11:41:16 shippou kernel: [   14.043683] scsi3 : ahci
Jul 12 11:41:16 shippou kernel: [   14.043760] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 16
Jul 12 11:41:16 shippou kernel: [   14.043764] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 16
Jul 12 11:41:16 shippou kernel: [   14.043767] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 16
Jul 12 11:41:16 shippou kernel: [   14.043771] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 16
Jul 12 11:41:16 shippou kernel: [   14.516984] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 12 11:41:16 shippou kernel: [   14.565772] ata1.00: ATA-7: ST380215AS, 3.AAD, max UDMA/133
Jul 12 11:41:16 shippou kernel: [   14.565775] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32)
Jul 12 11:41:16 shippou kernel: [   14.623998] ata1.00: configured for UDMA/133
Jul 12 11:41:16 shippou kernel: [   14.932258] ata2: SATA link down (SStatus 0 SControl 300)
Jul 12 11:41:16 shippou kernel: [   15.243716] ata3: SATA link down (SStatus 0 SControl 300)
Jul 12 11:41:16 shippou kernel: [   15.555173] ata4: SATA link down (SStatus 0 SControl 300)
Jul 12 11:41:16 shippou kernel: [   15.555296] scsi 0:0:0:0: Direct-Access     ATA      ST380215AS       3.AA PQ: 0 ANSI: 5
Jul 12 11:41:16 shippou kernel: [   15.556747] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 11:41:16 shippou kernel: [   15.556865] ohci_hcd 0000:00:13.0: OHCI Host Controller
Jul 12 11:41:16 shippou kernel: [   15.557137] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Jul 12 11:41:16 shippou kernel: [   15.557157] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02e000
Jul 12 11:41:16 shippou kernel: [   15.564307] Driver 'sd' needs updating - please use bus_type methods
Jul 12 11:41:16 shippou kernel: [   15.571201] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jul 12 11:41:16 shippou kernel: [   15.571215] sd 0:0:0:0: [sda] Write Protect is off
Jul 12 11:41:16 shippou kernel: [   15.571231] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 12 11:41:16 shippou kernel: [   15.571283] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jul 12 11:41:16 shippou kernel: [   15.571291] sd 0:0:0:0: [sda] Write Protect is off
Jul 12 11:41:16 shippou kernel: [   15.571306] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 12 11:41:16 shippou kernel: [   15.571311]  sda: sda1 sda2 sda3 sda4
Jul 12 11:41:16 shippou kernel: [   15.615319] usb usb1: configuration #1 chosen from 1 choice
Jul 12 11:41:16 shippou kernel: [   15.615344] hub 1-0:1.0: USB hub found
Jul 12 11:41:16 shippou kernel: [   15.615353] hub 1-0:1.0: 2 ports detected
Jul 12 11:41:16 shippou kernel: [   15.623631] sd 0:0:0:0: [sda] Attached SCSI disk
Jul 12 11:41:16 shippou kernel: [   15.628992] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 12 11:41:16 shippou kernel: [   15.718994] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 17
Jul 12 11:41:16 shippou kernel: [   15.719132] ohci_hcd 0000:00:13.1: OHCI Host Controller
Jul 12 11:41:16 shippou kernel: [   15.719198] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Jul 12 11:41:16 shippou kernel: [   15.719224] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfe02d000
Jul 12 11:41:16 shippou kernel: [   15.779020] usb usb2: configuration #1 chosen from 1 choice
Jul 12 11:41:16 shippou kernel: [   15.779045] hub 2-0:1.0: USB hub found
Jul 12 11:41:16 shippou kernel: [   15.779055] hub 2-0:1.0: 2 ports detected
Jul 12 11:41:16 shippou kernel: [   15.882710] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 18
Jul 12 11:41:16 shippou kernel: [   15.882858] ohci_hcd 0000:00:13.2: OHCI Host Controller
Jul 12 11:41:16 shippou kernel: [   15.882920] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
Jul 12 11:41:16 shippou kernel: [   15.882944] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfe02c000
Jul 12 11:41:16 shippou kernel: [   15.942739] usb usb3: configuration #1 chosen from 1 choice
Jul 12 11:41:16 shippou kernel: [   15.942772] hub 3-0:1.0: USB hub found
Jul 12 11:41:16 shippou kernel: [   15.942781] hub 3-0:1.0: 2 ports detected
Jul 12 11:41:16 shippou kernel: [   16.046415] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 17
Jul 12 11:41:16 shippou kernel: [   16.046564] ohci_hcd 0000:00:13.3: OHCI Host Controller
Jul 12 11:41:16 shippou kernel: [   16.046627] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
Jul 12 11:41:16 shippou kernel: [   16.046647] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfe02b000
Jul 12 11:41:16 shippou kernel: [   16.088666] Attempting manual resume
Jul 12 11:41:16 shippou kernel: [   16.106470] usb usb4: configuration #1 chosen from 1 choice
Jul 12 11:41:16 shippou kernel: [   16.106496] hub 4-0:1.0: USB hub found
Jul 12 11:41:16 shippou kernel: [   16.106505] hub 4-0:1.0: 2 ports detected
Jul 12 11:41:16 shippou kernel: [   16.135937] kjournald starting.  Commit interval 5 seconds
Jul 12 11:41:16 shippou kernel: [   16.135949] EXT3-fs: mounted filesystem with ordered data mode.
Jul 12 11:41:16 shippou kernel: [   16.210161] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 18
Jul 12 11:41:16 shippou kernel: [   16.210389] ohci_hcd 0000:00:13.4: OHCI Host Controller
Jul 12 11:41:16 shippou kernel: [   16.210449] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
Jul 12 11:41:16 shippou kernel: [   16.210468] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfe02a000
Jul 12 11:41:16 shippou kernel: [   16.270171] usb usb5: configuration #1 chosen from 1 choice
Jul 12 11:41:16 shippou kernel: [   16.270195] hub 5-0:1.0: USB hub found
Jul 12 11:41:16 shippou kernel: [   16.270204] hub 5-0:1.0: 2 ports detected
Jul 12 11:41:16 shippou kernel: [   16.374012] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 19
Jul 12 11:41:16 shippou kernel: [   16.374148] ehci_hcd 0000:00:13.5: EHCI Host Controller
Jul 12 11:41:16 shippou kernel: [   16.374210] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
Jul 12 11:41:16 shippou kernel: [   16.374250] ehci_hcd 0000:00:13.5: debug port 1
Jul 12 11:41:16 shippou kernel: [   16.374269] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfe029000
Jul 12 11:41:16 shippou kernel: [   16.385731] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jul 12 11:41:16 shippou kernel: [   16.385847] usb usb6: configuration #1 chosen from 1 choice
Jul 12 11:41:16 shippou kernel: [   16.385872] hub 6-0:1.0: USB hub found
Jul 12 11:41:16 shippou kernel: [   16.385878] hub 6-0:1.0: 10 ports detected
Jul 12 11:41:16 shippou kernel: [   16.489795] SB600_PATA: IDE controller (0x1002:0x438c rev 0x00) at  PCI slot 0000:00:14.1
Jul 12 11:41:16 shippou kernel: [   16.489809] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 11:41:16 shippou kernel: [   16.489819] SB600_PATA: not 100% native mode: will probe irqs later
Jul 12 11:41:16 shippou kernel: [   16.489827]     ide0: BM-DMA at 0xf900-0xf907, BIOS settings: hda:pio, hdb:DMA
Jul 12 11:41:16 shippou kernel: [   17.276505] hdb: LITE-ON DVDRW LH-20A1P, ATAPI CD/DVD-ROM drive
Jul 12 11:41:16 shippou kernel: [   17.556031] hdb: UDMA/66 mode selected
Jul 12 11:41:16 shippou kernel: [   17.556406] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Jul 12 11:41:16 shippou kernel: [   17.569308] r8169 Gigabit Ethernet driver 2.2LK loaded
Jul 12 11:41:16 shippou kernel: [   17.569344] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 22 (level, low) -> IRQ 22
Jul 12 11:41:16 shippou kernel: [   17.569575] eth0: RTL8169sc/8110sc at 0xffffc20001044000, 00:19:21:21:21:b5, XID 18000000 IRQ 22
Jul 12 11:41:16 shippou kernel: [   23.484761] input: PC Speaker as /devices/platform/pcspkr/input/input2
Jul 12 11:41:16 shippou kernel: [   23.613136] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 12 11:41:16 shippou kernel: [   23.650618] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul 12 11:41:16 shippou kernel: [   23.861023] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Jul 12 11:41:16 shippou kernel: [   24.135918] input: ImExPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input3
Jul 12 11:41:16 shippou kernel: [   24.158767] parport_pc 00:0a: reported by Plug and Play ACPI
Jul 12 11:41:16 shippou kernel: [   24.158825] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jul 12 11:41:16 shippou kernel: [   24.162838] input: Power Button (FF) as /devices/virtual/input/input4
Jul 12 11:41:16 shippou kernel: [   24.188192] ACPI: Power Button (FF) [PWRF]
Jul 12 11:41:16 shippou kernel: [   24.188253] input: Power Button (CM) as /devices/virtual/input/input5
Jul 12 11:41:16 shippou kernel: [   24.216155] ACPI: Power Button (CM) [PWRB]
Jul 12 11:41:16 shippou kernel: [   25.565131] r8169: eth0: link down
Jul 12 11:41:16 shippou kernel: [   25.671329] hdb: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
Jul 12 11:41:16 shippou kernel: [   25.671337] Uniform CD-ROM driver Revision: 3.20
Jul 12 11:41:16 shippou kernel: [   25.811154] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 11:41:16 shippou kernel: [   25.835184] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
Jul 12 11:41:16 shippou kernel: [   26.078776] NET: Registered protocol family 10
Jul 12 11:41:16 shippou kernel: [   26.078985] lo: Disabled Privacy Extensions
Jul 12 11:41:16 shippou kernel: [   26.079304] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 12 11:41:16 shippou kernel: [   28.807349] lp0: using parport0 (interrupt-driven).
Jul 12 11:41:16 shippou kernel: [   28.900023] Adding 289160k swap on /dev/sda3.  Priority:-1 extents:1 across:289160k
Jul 12 11:41:16 shippou kernel: [   29.454913] EXT3 FS on sda2, internal journal
Jul 12 11:41:16 shippou kernel: [   30.362955] kjournald starting.  Commit interval 5 seconds
Jul 12 11:41:16 shippou kernel: [   30.363151] EXT3 FS on sda4, internal journal
Jul 12 11:41:16 shippou kernel: [   30.363155] EXT3-fs: mounted filesystem with ordered data mode.
Jul 12 11:41:16 shippou kernel: [   30.840256] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul 12 11:41:16 shippou kernel: [   31.321237] No dock devices found.
Jul 12 11:41:16 shippou kernel: [   31.580841] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (1 cpu cores) (version 2.20.00)
Jul 12 11:41:16 shippou kernel: [   31.580880] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
Jul 12 11:41:16 shippou kernel: [   31.580882] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
Jul 12 11:41:16 shippou dhcdbd: Started up.
Jul 12 11:41:18 shippou kernel: [   34.015169] Marking TSC unstable due to cpufreq changes
Jul 12 11:41:18 shippou kernel: [   34.019043] Time: hpet clocksource has been installed.
Jul 12 11:41:18 shippou kernel: [   34.318547] Clocksource tsc unstable (delta = -222233424 ns)
Jul 12 11:41:20 shippou kernel: [   34.972041] [drm] Initialized drm 1.1.0 20060810
Jul 12 11:41:26 shippou kernel: [   39.134763] hda-intel: Invalid position buffer, using LPIB read method instead.
Jul 12 12:01:16 shippou -- MARK --
Jul 12 12:11:45 shippou kernel: [ 1357.167675] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jul 12 12:11:46 shippou exiting on signal 15
Jul 12 17:31:05 shippou syslogd 1.5.0#1ubuntu1: restart.
Jul 12 17:31:05 shippou kernel: Inspecting /boot/System.map-2.6.24-19-generic
Jul 12 17:31:05 shippou kernel: Loaded 28491 symbols from /boot/System.map-2.6.24-19-generic.
Jul 12 17:31:05 shippou kernel: Symbols match kernel version 2.6.24.
Jul 12 17:31:05 shippou kernel: Loaded 16834 symbols from 77 modules.
Jul 12 17:31:05 shippou kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 12 17:31:05 shippou kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 12 17:31:05 shippou kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:15:37 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
Jul 12 17:31:05 shippou kernel: [    0.000000] Command line: root=UUID=2e985bef-5550-421f-b1bf-e1f730273cbc ro quiet splash
Jul 12 17:31:05 shippou kernel: [    0.000000] BIOS-provided physical RAM map:
Jul 12 17:31:05 shippou kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jul 12 17:31:05 shippou kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jul 12 17:31:05 shippou kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jul 12 17:31:05 shippou kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000097fe0000 (usable)
Jul 12 17:31:05 shippou kernel: [    0.000000]  BIOS-e820: 0000000097fe0000 - 0000000097fe3000 (ACPI NVS)
Jul 12 17:31:05 shippou kernel: [    0.000000]  BIOS-e820: 0000000097fe3000 - 0000000097ff0000 (ACPI data)
Jul 12 17:31:05 shippou kernel: [    0.000000]  BIOS-e820: 0000000097ff0000 - 0000000098000000 (reserved)
Jul 12 17:31:05 shippou kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Jul 12 17:31:05 shippou kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Jul 12 17:31:05 shippou kernel: [    0.000000] end_pfn_map = 1048576
Jul 12 17:31:05 shippou kernel: [    0.000000] DMI 2.5 present.
Jul 12 17:31:05 shippou kernel: [    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F7B80 checksum 0
Jul 12 17:31:05 shippou kernel: [    0.000000] ACPI: RSDP 000F7B80, 0024 (r2 RS690 )
Jul 12 17:31:05 shippou kernel: [    0.000000] ACPI: RSDT 97FE3040, 0038 (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 12 17:31:05 shippou kernel: [    0.000000] ACPI: FACP 97FE30C0, 0074 (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 12 17:31:05 shippou kernel: [    0.000000] ACPI: DSDT 97FE3180, 4B0B (r1 RS690  AWRDACPI     1000 MSFT  3000000)
Jul 12 17:31:05 shippou kernel: [    0.000000] ACPI: FACS 97FE0000, 0040
Jul 12 17:31:05 shippou kernel: [    0.000000] ACPI: SSDT 97FE7DC0, 00D3 (r1 PTLTD  POWERNOW        1  LTP        1)
Jul 12 17:31:05 shippou kernel: [    0.000000] ACPI: HPET 97FE7F00, 0038 (r1 RS690  AWRDACPI 42302E31 AWRD       98)
Jul 12 17:31:05 shippou kernel: [    0.000000] ACPI: MCFG 97FE7F80, 003C (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 12 17:31:05 shippou kernel: [    0.000000] ACPI: APIC 97FE7D00, 0068 (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 12 17:31:05 shippou kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Jul 12 17:31:05 shippou kernel: [    0.000000] CPU has 1 num_cores
Jul 12 17:31:05 shippou kernel: [    0.000000] No NUMA configuration found
Jul 12 17:31:05 shippou kernel: [    0.000000] Faking a node at 0000000000000000-0000000097fe0000
Jul 12 17:31:05 shippou kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000097fe0000
Jul 12 17:31:05 shippou kernel: [    0.000000] Zone PFN ranges:
Jul 12 17:31:05 shippou kernel: [    0.000000]   DMA             0 ->     4096
Jul 12 17:31:05 shippou kernel: [    0.000000]   DMA32        4096 ->  1048576
Jul 12 17:31:05 shippou kernel: [    0.000000]   Normal    1048576 ->  1048576
Jul 12 17:31:05 shippou kernel: [    0.000000] Movable zone start PFN for each node
Jul 12 17:31:05 shippou kernel: [    0.000000] early_node_map[2] active PFN ranges
Jul 12 17:31:05 shippou kernel: [    0.000000]     0:        0 ->      159
Jul 12 17:31:05 shippou kernel: [    0.000000]     0:      256 ->   622560
Jul 12 17:31:05 shippou kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Jul 12 17:31:05 shippou kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Jul 12 17:31:05 shippou kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul 12 17:31:05 shippou kernel: [    0.000000] Processor #0 (Bootup-CPU)
Jul 12 17:31:05 shippou kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Jul 12 17:31:05 shippou kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul 12 17:31:05 shippou kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jul 12 17:31:05 shippou kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jul 12 17:31:05 shippou kernel: [    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
Jul 12 17:31:05 shippou kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 12 17:31:05 shippou kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jul 12 17:31:05 shippou kernel: [    0.000000] Setting APIC routing to flat
Jul 12 17:31:05 shippou kernel: [    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
Jul 12 17:31:05 shippou kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 12 17:31:05 shippou kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Jul 12 17:31:05 shippou kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Jul 12 17:31:05 shippou kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Jul 12 17:31:05 shippou kernel: [    0.000000] Allocating PCI resources starting at a0000000 (gap: 98000000:48000000)
Jul 12 17:31:05 shippou kernel: [    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
Jul 12 17:31:05 shippou kernel: [    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
Jul 12 17:31:05 shippou kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 612716
Jul 12 17:31:05 shippou kernel: [    0.000000] Policy zone: DMA32
Jul 12 17:31:05 shippou kernel: [    0.000000] Kernel command line: root=UUID=2e985bef-5550-421f-b1bf-e1f730273cbc ro quiet splash
Jul 12 17:31:05 shippou kernel: [    0.000000] Initializing CPU#0
Jul 12 17:31:05 shippou kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Jul 12 17:31:05 shippou kernel: [    0.000000] TSC calibrated against HPET
Jul 12 17:31:05 shippou kernel: [   12.792176] time.c: Detected 1799.797 MHz processor.
Jul 12 17:31:05 shippou kernel: [   12.792865] Console: colour VGA+ 80x25
Jul 12 17:31:05 shippou kernel: [   12.792868] console [tty0] enabled
Jul 12 17:31:05 shippou kernel: [   12.792885] Checking aperture...
Jul 12 17:31:05 shippou kernel: [   12.792888] CPU 0: aperture @ ff40000000 size 32 MB
Jul 12 17:31:05 shippou kernel: [   12.792890] Aperture too small (32 MB)
Jul 12 17:31:05 shippou kernel: [   12.802700] No AGP bridge found
Jul 12 17:31:05 shippou kernel: [   12.836059] Memory: 2442456k/2490240k available (2489k kernel code, 47396k reserved, 1318k data, 320k init)
Jul 12 17:31:05 shippou kernel: [   12.836098] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Jul 12 17:31:05 shippou kernel: [   12.914179] Calibrating delay using timer specific routine.. 3708.98 BogoMIPS (lpj=7417975)
Jul 12 17:31:05 shippou kernel: [   12.914226] Security Framework initialized
Jul 12 17:31:05 shippou kernel: [   12.914231] SELinux:  Disabled at boot.
Jul 12 17:31:05 shippou kernel: [   12.914245] AppArmor: AppArmor initialized
Jul 12 17:31:05 shippou kernel: [   12.914248] Failure registering capabilities with primary security module.
Jul 12 17:31:05 shippou kernel: [   12.914627] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jul 12 17:31:05 shippou kernel: [   12.918635] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jul 12 17:31:05 shippou kernel: [   12.920243] Mount-cache hash table entries: 256
Jul 12 17:31:05 shippou kernel: [   12.920394] Initializing cgroup subsys ns
Jul 12 17:31:05 shippou kernel: [   12.920397] Initializing cgroup subsys cpuacct
Jul 12 17:31:05 shippou kernel: [   12.920413] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jul 12 17:31:05 shippou kernel: [   12.920415] CPU: L2 Cache: 512K (64 bytes/line)
Jul 12 17:31:05 shippou kernel: [   12.920418] CPU 0/0 -> Node 0
Jul 12 17:31:05 shippou kernel: [   12.920447] SMP alternatives: switching to UP code
Jul 12 17:31:05 shippou kernel: [   12.921132] Early unpacking initramfs... done
Jul 12 17:31:05 shippou kernel: [   13.322039] ACPI: Core revision 20070126
Jul 12 17:31:05 shippou kernel: [   13.322100] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Jul 12 17:31:05 shippou kernel: [   13.371578] Using local APIC timer interrupts.
Jul 12 17:31:05 shippou kernel: [   13.427056] Detected 12.498 MHz APIC timer.
Jul 12 17:31:05 shippou kernel: [   13.427105] Brought up 1 CPUs
Jul 12 17:31:05 shippou kernel: [   13.427376] net_namespace: 120 bytes
Jul 12 17:31:05 shippou kernel: [   13.427778] Time: 17:30:44  Date: 07/12/08
Jul 12 17:31:05 shippou kernel: [   13.427807] NET: Registered protocol family 16
Jul 12 17:31:05 shippou kernel: [   13.427979] ACPI: bus type pci registered
Jul 12 17:31:05 shippou kernel: [   13.428047] PCI: Using configuration type 1
Jul 12 17:31:05 shippou kernel: [   13.434748] ACPI: Interpreter enabled
Jul 12 17:31:05 shippou kernel: [   13.434754] ACPI: (supports S0 S3 S4 S5)
Jul 12 17:31:05 shippou kernel: [   13.434770] ACPI: Using IOAPIC for interrupt routing
Jul 12 17:31:05 shippou kernel: [   13.439960] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul 12 17:31:05 shippou kernel: [   13.440122] pci 0000:00:12.0: set SATA to AHCI mode
Jul 12 17:31:05 shippou kernel: [   13.440922] PCI: Transparent bridge - 0000:00:14.4
Jul 12 17:31:05 shippou kernel: [   13.461666] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 17:31:05 shippou kernel: [   13.461772] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 17:31:05 shippou kernel: [   13.461875] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 17:31:05 shippou kernel: [   13.461979] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 17:31:05 shippou kernel: [   13.462082] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 17:31:05 shippou kernel: [   13.462185] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 17:31:05 shippou kernel: [   13.462287] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 17:31:05 shippou kernel: [   13.462390] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 12 17:31:05 shippou kernel: [   13.462506] Linux Plug and Play Support v0.97 (c) Adam Belay
Jul 12 17:31:05 shippou kernel: [   13.462534] pnp: PnP ACPI init
Jul 12 17:31:05 shippou kernel: [   13.462543] ACPI: bus type pnp registered
Jul 12 17:31:05 shippou kernel: [   13.465563] pnp: PnP ACPI: found 15 devices
Jul 12 17:31:05 shippou kernel: [   13.465566] ACPI: ACPI bus type pnp unregistered
Jul 12 17:31:05 shippou kernel: [   13.465798] PCI: Using ACPI for IRQ routing
Jul 12 17:31:05 shippou kernel: [   13.465801] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jul 12 17:31:05 shippou kernel: [   13.479011] NET: Registered protocol family 8
Jul 12 17:31:05 shippou kernel: [   13.479013] NET: Registered protocol family 20
Jul 12 17:31:05 shippou kernel: [   13.479094] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Jul 12 17:31:05 shippou kernel: [   13.479098] hpet0: 4 32-bit timers, 14318180 Hz
Jul 12 17:31:05 shippou kernel: [   13.480151] AppArmor: AppArmor Filesystem Enabled
Jul 12 17:31:05 shippou kernel: [   13.482971] Time: tsc clocksource has been installed.
Jul 12 17:31:05 shippou kernel: [   13.490953] system 00:01: ioport range 0x4100-0x411f has been reserved
Jul 12 17:31:05 shippou kernel: [   13.490957] system 00:01: ioport range 0x228-0x22f has been reserved
Jul 12 17:31:05 shippou kernel: [   13.490960] system 00:01: ioport range 0x40b-0x40b has been reserved
Jul 12 17:31:05 shippou kernel: [   13.490963] system 00:01: ioport range 0x4d6-0x4d6 has been reserved
Jul 12 17:31:05 shippou kernel: [   13.490966] system 00:01: ioport range 0xc00-0xc01 has been reserved
Jul 12 17:31:05 shippou kernel: [   13.490969] system 00:01: ioport range 0xc14-0xc14 has been reserved
Jul 12 17:31:05 shippou kernel: [   13.490973] system 00:01: ioport range 0xc50-0xc52 has been reserved
Jul 12 17:31:05 shippou kernel: [   13.490976] system 00:01: ioport range 0xc6c-0xc6d has been reserved
Jul 12 17:31:05 shippou kernel: [   13.490979] system 00:01: ioport range 0xc6f-0xc6f has been reserved
Jul 12 17:31:05 shippou kernel: [   13.490982] system 00:01: ioport range 0xcd0-0xcd1 has been reserved
Jul 12 17:31:05 shippou kernel: [   13.490985] system 00:01: ioport range 0xcd2-0xcd3 has been reserved
Jul 12 17:31:05 shippou kernel: [   13.490988] system 00:01: ioport range 0xcd4-0xcdf has been reserved
Jul 12 17:31:05 shippou kernel: [   13.490991] system 00:01: ioport range 0x4000-0x40fe has been reserved
Jul 12 17:31:05 shippou kernel: [   13.490994] system 00:01: ioport range 0x4210-0x4217 has been reserved
Jul 12 17:31:05 shippou kernel: [   13.490997] system 00:01: ioport range 0xb10-0xb1f has been reserved
Jul 12 17:31:05 shippou kernel: [   13.491006] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
Jul 12 17:31:05 shippou kernel: [   13.491009] system 00:07: ioport range 0x220-0x225 has been reserved
Jul 12 17:31:05 shippou kernel: [   13.491012] system 00:07: ioport range 0xb00-0xb0f has been reserved
Jul 12 17:31:05 shippou kernel: [   13.491022] system 00:0d: iomem range 0xe0000000-0xefffffff could not be reserved
Jul 12 17:31:05 shippou kernel: [   13.491028] system 00:0e: iomem range 0xf0000-0xfffff could not be reserved
Jul 12 17:31:05 shippou kernel: [   13.491032] system 00:0e: iomem range 0xfed00000-0xfed000ff has been reserved
Jul 12 17:31:05 shippou kernel: [   13.491035] system 00:0e: iomem range 0x97fe0000-0x97ffffff could not be reserved
Jul 12 17:31:05 shippou kernel: [   13.491039] system 00:0e: iomem range 0xffff0000-0xffffffff has been reserved
Jul 12 17:31:05 shippou kernel: [   13.491042] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
Jul 12 17:31:05 shippou kernel: [   13.491045] system 00:0e: iomem range 0x100000-0x97fdffff could not be reserved
Jul 12 17:31:05 shippou kernel: [   13.491049] system 00:0e: iomem range 0x98000000-0x9fffffff has been reserved
Jul 12 17:31:05 shippou kernel: [   13.491052] system 00:0e: iomem range 0xfec00000-0xfec00fff has been reserved
Jul 12 17:31:05 shippou kernel: [   13.491055] system 00:0e: iomem range 0xfee00000-0xfee00fff could not be reserved
Jul 12 17:31:05 shippou kernel: [   13.491059] system 00:0e: iomem range 0xfff80000-0xfffeffff has been reserved
Jul 12 17:31:05 shippou kernel: [   13.491415] PCI: Bridge: 0000:00:01.0
Jul 12 17:31:05 shippou kernel: [   13.491417]   IO window: e000-efff
Jul 12 17:31:05 shippou kernel: [   13.491420]   MEM window: fdd00000-fdefffff
Jul 12 17:31:05 shippou kernel: [   13.491423]   PREFETCH window: d8000000-dfffffff
Jul 12 17:31:05 shippou kernel: [   13.491427] PCI: Bridge: 0000:00:14.4
Jul 12 17:31:05 shippou kernel: [   13.491430]   IO window: d000-dfff
Jul 12 17:31:05 shippou kernel: [   13.491435]   MEM window: fdc00000-fdcfffff
Jul 12 17:31:05 shippou kernel: [   13.491439]   PREFETCH window: fdf00000-fdffffff
Jul 12 17:31:05 shippou kernel: [   13.491463] NET: Registered protocol family 2
Jul 12 17:31:05 shippou kernel: [   13.527014] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Jul 12 17:31:05 shippou kernel: [   13.528645] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Jul 12 17:31:05 shippou kernel: [   13.535923] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jul 12 17:31:05 shippou kernel: [   13.536802] TCP: Hash tables configured (established 524288 bind 65536)
Jul 12 17:31:05 shippou kernel: [   13.536806] TCP reno registered
Jul 12 17:31:05 shippou kernel: [   13.546988] checking if image is initramfs... it is
Jul 12 17:31:05 shippou kernel: [   14.251625] Freeing initrd memory: 8212k freed
Jul 12 17:31:05 shippou kernel: [   14.258725] audit: initializing netlink socket (disabled)
Jul 12 17:31:05 shippou kernel: [   14.258740] audit(1215883844.416:1): initialized
Jul 12 17:31:05 shippou kernel: [   14.260719] VFS: Disk quotas dquot_6.5.1
Jul 12 17:31:05 shippou kernel: [   14.260792] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jul 12 17:31:05 shippou kernel: [   14.260934] io scheduler noop registered
Jul 12 17:31:05 shippou kernel: [   14.260936] io scheduler anticipatory registered
Jul 12 17:31:05 shippou kernel: [   14.260938] io scheduler deadline registered
Jul 12 17:31:05 shippou kernel: [   14.261042] io scheduler cfq registered (default)
Jul 12 17:31:05 shippou kernel: [   14.429271] Real Time Clock Driver v1.12ac
Jul 12 17:31:05 shippou kernel: [   14.429987] Linux agpgart interface v0.102
Jul 12 17:31:05 shippou kernel: [   14.429990] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jul 12 17:31:05 shippou kernel: [   14.430142] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 12 17:31:05 shippou kernel: [   14.430761] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 12 17:31:05 shippou kernel: [   14.431447] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jul 12 17:31:05 shippou kernel: [   14.431514] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jul 12 17:31:05 shippou kernel: [   14.431604] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jul 12 17:31:05 shippou kernel: [   14.431942] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 12 17:31:05 shippou kernel: [   14.431946] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 12 17:31:05 shippou kernel: [   14.441400] mice: PS/2 mouse device common for all mice
Jul 12 17:31:05 shippou kernel: [   14.441433] cpuidle: using governor ladder
Jul 12 17:31:05 shippou kernel: [   14.441436] cpuidle: using governor menu
Jul 12 17:31:05 shippou kernel: [   14.441584] NET: Registered protocol family 1
Jul 12 17:31:05 shippou kernel: [   14.441680] registered taskstats version 1
Jul 12 17:31:05 shippou kernel: [   14.441799]   Magic number: 0:189:542
Jul 12 17:31:05 shippou kernel: [   14.441946] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
Jul 12 17:31:05 shippou kernel: [   14.441949] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 12 17:31:05 shippou kernel: [   14.441951] EDD information not available.
Jul 12 17:31:05 shippou kernel: [   14.441959] Freeing unused kernel memory: 320k freed
Jul 12 17:31:05 shippou kernel: [   14.469275] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jul 12 17:31:05 shippou kernel: [   15.641813] fuse init (API version 7.9)
Jul 12 17:31:05 shippou kernel: [   15.656306] ACPI: Fan [FAN] (on)
Jul 12 17:31:05 shippou kernel: [   15.663112] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Jul 12 17:31:05 shippou kernel: [   15.664552] ACPI: Thermal Zone [THRM] (40 C)
Jul 12 17:31:05 shippou kernel: [   16.202459] SCSI subsystem initialized
Jul 12 17:31:05 shippou kernel: [   16.274558] usbcore: registered new interface driver usbfs
Jul 12 17:31:05 shippou kernel: [   16.274579] usbcore: registered new interface driver hub
Jul 12 17:31:05 shippou kernel: [   16.286329] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 17:31:05 shippou kernel: [   16.286459] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
Jul 12 17:31:05 shippou kernel: [   16.286466] ahci 0000:00:12.0: controller can't do PMP, turning off CAP_PMP
Jul 12 17:31:05 shippou kernel: [   16.302151] usbcore: registered new device driver usb
Jul 12 17:31:05 shippou kernel: [   16.314093] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jul 12 17:31:05 shippou kernel: [   16.315063] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jul 12 17:31:05 shippou kernel: [   16.502988] Floppy drive(s): fd0 is 1.44M
Jul 12 17:31:05 shippou kernel: [   16.523372] FDC 0 is a post-1991 82077
Jul 12 17:31:05 shippou kernel: [   17.288407] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Jul 12 17:31:05 shippou kernel: [   17.288412] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pio slum part 
Jul 12 17:31:05 shippou kernel: [   17.289621] scsi0 : ahci
Jul 12 17:31:05 shippou kernel: [   17.289949] scsi1 : ahci
Jul 12 17:31:05 shippou kernel: [   17.290099] scsi2 : ahci
Jul 12 17:31:05 shippou kernel: [   17.290249] scsi3 : ahci
Jul 12 17:31:05 shippou kernel: [   17.290330] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 16
Jul 12 17:31:05 shippou kernel: [   17.290334] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 16
Jul 12 17:31:05 shippou kernel: [   17.290337] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 16
Jul 12 17:31:05 shippou kernel: [   17.290341] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 16
Jul 12 17:31:05 shippou kernel: [   17.763552] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 12 17:31:05 shippou kernel: [   17.807734] ata1.00: ATA-7: ST380215AS, 3.AAD, max UDMA/133
Jul 12 17:31:05 shippou kernel: [   17.807737] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32)
Jul 12 17:31:05 shippou kernel: [   17.865960] ata1.00: configured for UDMA/133
Jul 12 17:31:05 shippou kernel: [   18.174835] ata2: SATA link down (SStatus 0 SControl 300)
Jul 12 17:31:05 shippou kernel: [   18.486295] ata3: SATA link down (SStatus 0 SControl 300)
Jul 12 17:31:05 shippou kernel: [   18.797754] ata4: SATA link down (SStatus 0 SControl 300)
Jul 12 17:31:05 shippou kernel: [   18.797878] scsi 0:0:0:0: Direct-Access     ATA      ST380215AS       3.AA PQ: 0 ANSI: 5
Jul 12 17:31:05 shippou kernel: [   18.799332] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 17:31:05 shippou kernel: [   18.799450] ohci_hcd 0000:00:13.0: OHCI Host Controller
Jul 12 17:31:05 shippou kernel: [   18.799712] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Jul 12 17:31:05 shippou kernel: [   18.799731] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02e000
Jul 12 17:31:05 shippou kernel: [   18.806891] Driver 'sd' needs updating - please use bus_type methods
Jul 12 17:31:05 shippou kernel: [   18.813785] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jul 12 17:31:05 shippou kernel: [   18.813798] sd 0:0:0:0: [sda] Write Protect is off
Jul 12 17:31:05 shippou kernel: [   18.813815] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 12 17:31:05 shippou kernel: [   18.813868] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jul 12 17:31:05 shippou kernel: [   18.813876] sd 0:0:0:0: [sda] Write Protect is off
Jul 12 17:31:05 shippou kernel: [   18.813891] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 12 17:31:05 shippou kernel: [   18.813895]  sda: sda1 sda2 sda3 sda4
Jul 12 17:31:05 shippou kernel: [   18.857899] usb usb1: configuration #1 chosen from 1 choice
Jul 12 17:31:05 shippou kernel: [   18.857924] hub 1-0:1.0: USB hub found
Jul 12 17:31:05 shippou kernel: [   18.857933] hub 1-0:1.0: 2 ports detected
Jul 12 17:31:05 shippou kernel: [   18.865596] sd 0:0:0:0: [sda] Attached SCSI disk
Jul 12 17:31:05 shippou kernel: [   18.870931] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 12 17:31:05 shippou kernel: [   18.961604] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 17
Jul 12 17:31:05 shippou kernel: [   18.961735] ohci_hcd 0000:00:13.1: OHCI Host Controller
Jul 12 17:31:05 shippou kernel: [   18.961798] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Jul 12 17:31:05 shippou kernel: [   18.961824] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfe02d000
Jul 12 17:31:05 shippou kernel: [   19.021609] usb usb2: configuration #1 chosen from 1 choice
Jul 12 17:31:05 shippou kernel: [   19.021635] hub 2-0:1.0: USB hub found
Jul 12 17:31:05 shippou kernel: [   19.021644] hub 2-0:1.0: 2 ports detected
Jul 12 17:31:05 shippou kernel: [   19.125286] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 18
Jul 12 17:31:05 shippou kernel: [   19.125469] ohci_hcd 0000:00:13.2: OHCI Host Controller
Jul 12 17:31:05 shippou kernel: [   19.125526] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
Jul 12 17:31:05 shippou kernel: [   19.125549] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfe02c000
Jul 12 17:31:05 shippou kernel: [   19.185361] usb usb3: configuration #1 chosen from 1 choice
Jul 12 17:31:05 shippou kernel: [   19.185395] hub 3-0:1.0: USB hub found
Jul 12 17:31:05 shippou kernel: [   19.185405] hub 3-0:1.0: 2 ports detected
Jul 12 17:31:05 shippou kernel: [   19.230825] Attempting manual resume
Jul 12 17:31:05 shippou kernel: [   19.278114] kjournald starting.  Commit interval 5 seconds
Jul 12 17:31:05 shippou kernel: [   19.278125] EXT3-fs: mounted filesystem with ordered data mode.
Jul 12 17:31:05 shippou kernel: [   19.289026] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 17
Jul 12 17:31:05 shippou kernel: [   19.289165] ohci_hcd 0000:00:13.3: OHCI Host Controller
Jul 12 17:31:05 shippou kernel: [   19.289229] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
Jul 12 17:31:05 shippou kernel: [   19.289247] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfe02b000
Jul 12 17:31:05 shippou kernel: [   19.349038] usb usb4: configuration #1 chosen from 1 choice
Jul 12 17:31:05 shippou kernel: [   19.349064] hub 4-0:1.0: USB hub found
Jul 12 17:31:05 shippou kernel: [   19.349073] hub 4-0:1.0: 2 ports detected
Jul 12 17:31:05 shippou kernel: [   19.452732] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 18
Jul 12 17:31:05 shippou kernel: [   19.452888] ohci_hcd 0000:00:13.4: OHCI Host Controller
Jul 12 17:31:05 shippou kernel: [   19.452951] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
Jul 12 17:31:05 shippou kernel: [   19.452970] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfe02a000
Jul 12 17:31:05 shippou kernel: [   19.512758] usb usb5: configuration #1 chosen from 1 choice
Jul 12 17:31:05 shippou kernel: [   19.512784] hub 5-0:1.0: USB hub found
Jul 12 17:31:05 shippou kernel: [   19.512793] hub 5-0:1.0: 2 ports detected
Jul 12 17:31:05 shippou kernel: [   19.616582] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 19
Jul 12 17:31:05 shippou kernel: [   19.616723] ehci_hcd 0000:00:13.5: EHCI Host Controller
Jul 12 17:31:05 shippou kernel: [   19.616784] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
Jul 12 17:31:05 shippou kernel: [   19.616824] ehci_hcd 0000:00:13.5: debug port 1
Jul 12 17:31:05 shippou kernel: [   19.616845] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfe029000
Jul 12 17:31:05 shippou kernel: [   19.628324] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jul 12 17:31:05 shippou kernel: [   19.628444] usb usb6: configuration #1 chosen from 1 choice
Jul 12 17:31:05 shippou kernel: [   19.628469] hub 6-0:1.0: USB hub found
Jul 12 17:31:05 shippou kernel: [   19.628476] hub 6-0:1.0: 10 ports detected
Jul 12 17:31:05 shippou kernel: [   19.732385] SB600_PATA: IDE controller (0x1002:0x438c rev 0x00) at  PCI slot 0000:00:14.1
Jul 12 17:31:05 shippou kernel: [   19.732398] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 17:31:05 shippou kernel: [   19.732409] SB600_PATA: not 100% native mode: will probe irqs later
Jul 12 17:31:05 shippou kernel: [   19.732417]     ide0: BM-DMA at 0xf900-0xf907, BIOS settings: hda:pio, hdb:DMA
Jul 12 17:31:05 shippou kernel: [   20.519097] hdb: LITE-ON DVDRW LH-20A1P, ATAPI CD/DVD-ROM drive
Jul 12 17:31:05 shippou kernel: [   20.798621] hdb: UDMA/66 mode selected
Jul 12 17:31:05 shippou kernel: [   20.798995] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Jul 12 17:31:05 shippou kernel: [   20.811908] r8169 Gigabit Ethernet driver 2.2LK loaded
Jul 12 17:31:05 shippou kernel: [   20.811945] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 22 (level, low) -> IRQ 22
Jul 12 17:31:05 shippou kernel: [   20.812179] eth0: RTL8169sc/8110sc at 0xffffc20001044000, 00:19:21:21:21:b5, XID 18000000 IRQ 22
Jul 12 17:31:05 shippou kernel: [   26.769631] input: PC Speaker as /devices/platform/pcspkr/input/input2
Jul 12 17:31:05 shippou kernel: [   27.059459] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 12 17:31:05 shippou kernel: [   27.107463] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul 12 17:31:05 shippou kernel: [   27.175280] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Jul 12 17:31:05 shippou kernel: [   27.287148] input: Power Button (FF) as /devices/virtual/input/input3
Jul 12 17:31:05 shippou kernel: [   27.315025] ACPI: Power Button (FF) [PWRF]
Jul 12 17:31:05 shippou kernel: [   27.315086] input: Power Button (CM) as /devices/virtual/input/input4
Jul 12 17:31:05 shippou kernel: [   27.346977] ACPI: Power Button (CM) [PWRB]
Jul 12 17:31:05 shippou kernel: [   27.426586] input: ImExPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Jul 12 17:31:05 shippou kernel: [   27.449259] parport_pc 00:0a: reported by Plug and Play ACPI
Jul 12 17:31:05 shippou kernel: [   27.449317] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jul 12 17:31:05 shippou kernel: [   28.892831] r8169: eth0: link down
Jul 12 17:31:05 shippou kernel: [   28.988950] hdb: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
Jul 12 17:31:05 shippou kernel: [   28.988959] Uniform CD-ROM driver Revision: 3.20
Jul 12 17:31:05 shippou kernel: [   29.105889] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
Jul 12 17:31:05 shippou kernel: [   29.129672] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
Jul 12 17:31:05 shippou kernel: [   29.339101] NET: Registered protocol family 10
Jul 12 17:31:05 shippou kernel: [   29.339308] lo: Disabled Privacy Extensions
Jul 12 17:31:05 shippou kernel: [   29.339646] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 12 17:31:05 shippou kernel: [   31.051439] lp0: using parport0 (interrupt-driven).
Jul 12 17:31:05 shippou kernel: [   31.144377] Adding 289160k swap on /dev/sda3.  Priority:-1 extents:1 across:289160k
Jul 12 17:31:05 shippou kernel: [   31.699145] EXT3 FS on sda2, internal journal
Jul 12 17:31:05 shippou kernel: [   32.615352] kjournald starting.  Commit interval 5 seconds
Jul 12 17:31:05 shippou kernel: [   32.615546] EXT3 FS on sda4, internal journal
Jul 12 17:31:05 shippou kernel: [   32.615551] EXT3-fs: mounted filesystem with ordered data mode.
Jul 12 17:31:05 shippou kernel: [   33.092646] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul 12 17:31:05 shippou kernel: [   33.557134] No dock devices found.
Jul 12 17:31:05 shippou kernel: [   33.816559] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (1 cpu cores) (version 2.20.00)
Jul 12 17:31:05 shippou kernel: [   33.816598] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
Jul 12 17:31:05 shippou kernel: [   33.816601] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
Jul 12 17:31:05 shippou dhcdbd: Started up.
Jul 12 17:31:05 shippou kernel: [   34.782125] Marking TSC unstable due to cpufreq changes
Jul 12 17:31:05 shippou kernel: [   34.785999] Time: hpet clocksource has been installed.
Jul 12 17:31:06 shippou kernel: [   35.074417] Clocksource tsc unstable (delta = -222234538 ns)
Jul 12 17:31:12 shippou kernel: [   38.536932] [drm] Initialized drm 1.1.0 20060810
Jul 12 17:31:19 shippou kernel: [   42.166959] hda-intel: Invalid position buffer, using LPIB read method instead.
Jul 12 17:32:37 shippou kernel: [   86.189402] UDF-fs: No VRS found
Jul 12 17:51:05 shippou -- MARK --
Jul 12 17:58:41 shippou kernel: [ 1027.313285] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jul 12 17:58:42 shippou exiting on signal 15
Jul 13 08:28:07 shippou syslogd 1.5.0#1ubuntu1: restart.
Jul 13 08:28:07 shippou kernel: Inspecting /boot/System.map-2.6.24-19-generic
Jul 13 08:28:07 shippou kernel: Loaded 28491 symbols from /boot/System.map-2.6.24-19-generic.
Jul 13 08:28:07 shippou kernel: Symbols match kernel version 2.6.24.
Jul 13 08:28:07 shippou kernel: Loaded 16834 symbols from 77 modules.
Jul 13 08:28:07 shippou kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 13 08:28:07 shippou kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 13 08:28:07 shippou kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:15:37 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
Jul 13 08:28:07 shippou kernel: [    0.000000] Command line: root=UUID=2e985bef-5550-421f-b1bf-e1f730273cbc ro quiet splash
Jul 13 08:28:07 shippou kernel: [    0.000000] BIOS-provided physical RAM map:
Jul 13 08:28:07 shippou kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jul 13 08:28:07 shippou kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jul 13 08:28:07 shippou kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jul 13 08:28:07 shippou kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000097fe0000 (usable)
Jul 13 08:28:07 shippou kernel: [    0.000000]  BIOS-e820: 0000000097fe0000 - 0000000097fe3000 (ACPI NVS)
Jul 13 08:28:07 shippou kernel: [    0.000000]  BIOS-e820: 0000000097fe3000 - 0000000097ff0000 (ACPI data)
Jul 13 08:28:07 shippou kernel: [    0.000000]  BIOS-e820: 0000000097ff0000 - 0000000098000000 (reserved)
Jul 13 08:28:07 shippou kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Jul 13 08:28:07 shippou kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Jul 13 08:28:07 shippou kernel: [    0.000000] end_pfn_map = 1048576
Jul 13 08:28:07 shippou kernel: [    0.000000] DMI 2.5 present.
Jul 13 08:28:07 shippou kernel: [    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F7B80 checksum 0
Jul 13 08:28:07 shippou kernel: [    0.000000] ACPI: RSDP 000F7B80, 0024 (r2 RS690 )
Jul 13 08:28:07 shippou kernel: [    0.000000] ACPI: RSDT 97FE3040, 0038 (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 13 08:28:07 shippou kernel: [    0.000000] ACPI: FACP 97FE30C0, 0074 (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 13 08:28:07 shippou kernel: [    0.000000] ACPI: DSDT 97FE3180, 4B0B (r1 RS690  AWRDACPI     1000 MSFT  3000000)
Jul 13 08:28:07 shippou kernel: [    0.000000] ACPI: FACS 97FE0000, 0040
Jul 13 08:28:07 shippou kernel: [    0.000000] ACPI: SSDT 97FE7DC0, 00D3 (r1 PTLTD  POWERNOW        1  LTP        1)
Jul 13 08:28:07 shippou kernel: [    0.000000] ACPI: HPET 97FE7F00, 0038 (r1 RS690  AWRDACPI 42302E31 AWRD       98)
Jul 13 08:28:07 shippou kernel: [    0.000000] ACPI: MCFG 97FE7F80, 003C (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 13 08:28:07 shippou kernel: [    0.000000] ACPI: APIC 97FE7D00, 0068 (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 13 08:28:07 shippou kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Jul 13 08:28:07 shippou kernel: [    0.000000] CPU has 1 num_cores
Jul 13 08:28:07 shippou kernel: [    0.000000] No NUMA configuration found
Jul 13 08:28:07 shippou kernel: [    0.000000] Faking a node at 0000000000000000-0000000097fe0000
Jul 13 08:28:07 shippou kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000097fe0000
Jul 13 08:28:07 shippou kernel: [    0.000000] Zone PFN ranges:
Jul 13 08:28:07 shippou kernel: [    0.000000]   DMA             0 ->     4096
Jul 13 08:28:07 shippou kernel: [    0.000000]   DMA32        4096 ->  1048576
Jul 13 08:28:07 shippou kernel: [    0.000000]   Normal    1048576 ->  1048576
Jul 13 08:28:07 shippou kernel: [    0.000000] Movable zone start PFN for each node
Jul 13 08:28:07 shippou kernel: [    0.000000] early_node_map[2] active PFN ranges
Jul 13 08:28:07 shippou kernel: [    0.000000]     0:        0 ->      159
Jul 13 08:28:07 shippou kernel: [    0.000000]     0:      256 ->   622560
Jul 13 08:28:07 shippou kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Jul 13 08:28:07 shippou kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Jul 13 08:28:07 shippou kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul 13 08:28:07 shippou kernel: [    0.000000] Processor #0 (Bootup-CPU)
Jul 13 08:28:07 shippou kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Jul 13 08:28:07 shippou kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul 13 08:28:07 shippou kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jul 13 08:28:07 shippou kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jul 13 08:28:07 shippou kernel: [    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
Jul 13 08:28:07 shippou kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 13 08:28:07 shippou kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jul 13 08:28:07 shippou kernel: [    0.000000] Setting APIC routing to flat
Jul 13 08:28:07 shippou kernel: [    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
Jul 13 08:28:07 shippou kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 13 08:28:07 shippou kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Jul 13 08:28:07 shippou kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Jul 13 08:28:07 shippou kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Jul 13 08:28:07 shippou kernel: [    0.000000] Allocating PCI resources starting at a0000000 (gap: 98000000:48000000)
Jul 13 08:28:07 shippou kernel: [    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
Jul 13 08:28:07 shippou kernel: [    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
Jul 13 08:28:07 shippou kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 612716
Jul 13 08:28:07 shippou kernel: [    0.000000] Policy zone: DMA32
Jul 13 08:28:07 shippou kernel: [    0.000000] Kernel command line: root=UUID=2e985bef-5550-421f-b1bf-e1f730273cbc ro quiet splash
Jul 13 08:28:07 shippou kernel: [    0.000000] Initializing CPU#0
Jul 13 08:28:07 shippou kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Jul 13 08:28:07 shippou kernel: [    0.000000] TSC calibrated against HPET
Jul 13 08:28:07 shippou kernel: [   10.166834] time.c: Detected 1799.807 MHz processor.
Jul 13 08:28:07 shippou kernel: [   10.167523] Console: colour VGA+ 80x25
Jul 13 08:28:07 shippou kernel: [   10.167526] console [tty0] enabled
Jul 13 08:28:07 shippou kernel: [   10.167543] Checking aperture...
Jul 13 08:28:07 shippou kernel: [   10.167546] CPU 0: aperture @ ff40000000 size 32 MB
Jul 13 08:28:07 shippou kernel: [   10.167547] Aperture too small (32 MB)
Jul 13 08:28:07 shippou kernel: [   10.177394] No AGP bridge found
Jul 13 08:28:07 shippou kernel: [   10.210780] Memory: 2442456k/2490240k available (2489k kernel code, 47396k reserved, 1318k data, 320k init)
Jul 13 08:28:07 shippou kernel: [   10.210819] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Jul 13 08:28:07 shippou kernel: [   10.288837] Calibrating delay using timer specific routine.. 3710.16 BogoMIPS (lpj=7420336)
Jul 13 08:28:07 shippou kernel: [   10.288884] Security Framework initialized
Jul 13 08:28:07 shippou kernel: [   10.288889] SELinux:  Disabled at boot.
Jul 13 08:28:07 shippou kernel: [   10.288902] AppArmor: AppArmor initialized
Jul 13 08:28:07 shippou kernel: [   10.288906] Failure registering capabilities with primary security module.
Jul 13 08:28:07 shippou kernel: [   10.289284] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jul 13 08:28:07 shippou kernel: [   10.293307] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jul 13 08:28:07 shippou kernel: [   10.294897] Mount-cache hash table entries: 256
Jul 13 08:28:07 shippou kernel: [   10.295047] Initializing cgroup subsys ns
Jul 13 08:28:07 shippou kernel: [   10.295051] Initializing cgroup subsys cpuacct
Jul 13 08:28:07 shippou kernel: [   10.295067] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jul 13 08:28:07 shippou kernel: [   10.295069] CPU: L2 Cache: 512K (64 bytes/line)
Jul 13 08:28:07 shippou kernel: [   10.295071] CPU 0/0 -> Node 0
Jul 13 08:28:07 shippou kernel: [   10.295100] SMP alternatives: switching to UP code
Jul 13 08:28:07 shippou kernel: [   10.295786] Early unpacking initramfs... done
Jul 13 08:28:07 shippou kernel: [   10.696743] ACPI: Core revision 20070126
Jul 13 08:28:07 shippou kernel: [   10.696803] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Jul 13 08:28:07 shippou kernel: [   10.746304] Using local APIC timer interrupts.
Jul 13 08:28:07 shippou kernel: [   10.801782] Detected 12.498 MHz APIC timer.
Jul 13 08:28:07 shippou kernel: [   10.801830] Brought up 1 CPUs
Jul 13 08:28:07 shippou kernel: [   10.802102] net_namespace: 120 bytes
Jul 13 08:28:07 shippou kernel: [   10.802504] Time:  8:27:46  Date: 07/13/08
Jul 13 08:28:07 shippou kernel: [   10.802533] NET: Registered protocol family 16
Jul 13 08:28:07 shippou kernel: [   10.802705] ACPI: bus type pci registered
Jul 13 08:28:07 shippou kernel: [   10.802773] PCI: Using configuration type 1
Jul 13 08:28:07 shippou kernel: [   10.809477] ACPI: Interpreter enabled
Jul 13 08:28:07 shippou kernel: [   10.809484] ACPI: (supports S0 S3 S4 S5)
Jul 13 08:28:07 shippou kernel: [   10.809500] ACPI: Using IOAPIC for interrupt routing
Jul 13 08:28:07 shippou kernel: [   10.814690] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul 13 08:28:07 shippou kernel: [   10.814852] pci 0000:00:12.0: set SATA to AHCI mode
Jul 13 08:28:07 shippou kernel: [   10.815653] PCI: Transparent bridge - 0000:00:14.4
Jul 13 08:28:07 shippou kernel: [   10.836398] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 13 08:28:07 shippou kernel: [   10.836504] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 13 08:28:07 shippou kernel: [   10.836607] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 13 08:28:07 shippou kernel: [   10.836711] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 13 08:28:07 shippou kernel: [   10.836814] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 13 08:28:07 shippou kernel: [   10.836917] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 13 08:28:07 shippou kernel: [   10.837020] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 13 08:28:07 shippou kernel: [   10.837123] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 13 08:28:07 shippou kernel: [   10.837239] Linux Plug and Play Support v0.97 (c) Adam Belay
Jul 13 08:28:07 shippou kernel: [   10.837268] pnp: PnP ACPI init
Jul 13 08:28:07 shippou kernel: [   10.837277] ACPI: bus type pnp registered
Jul 13 08:28:07 shippou kernel: [   10.840300] pnp: PnP ACPI: found 15 devices
Jul 13 08:28:07 shippou kernel: [   10.840303] ACPI: ACPI bus type pnp unregistered
Jul 13 08:28:07 shippou kernel: [   10.840535] PCI: Using ACPI for IRQ routing
Jul 13 08:28:07 shippou kernel: [   10.840538] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jul 13 08:28:07 shippou kernel: [   10.853737] NET: Registered protocol family 8
Jul 13 08:28:07 shippou kernel: [   10.853739] NET: Registered protocol family 20
Jul 13 08:28:07 shippou kernel: [   10.853818] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Jul 13 08:28:07 shippou kernel: [   10.853823] hpet0: 4 32-bit timers, 14318180 Hz
Jul 13 08:28:07 shippou kernel: [   10.854878] AppArmor: AppArmor Filesystem Enabled
Jul 13 08:28:07 shippou kernel: [   10.857696] Time: tsc clocksource has been installed.
Jul 13 08:28:07 shippou kernel: [   10.865678] system 00:01: ioport range 0x4100-0x411f has been reserved
Jul 13 08:28:07 shippou kernel: [   10.865682] system 00:01: ioport range 0x228-0x22f has been reserved
Jul 13 08:28:07 shippou kernel: [   10.865685] system 00:01: ioport range 0x40b-0x40b has been reserved
Jul 13 08:28:07 shippou kernel: [   10.865688] system 00:01: ioport range 0x4d6-0x4d6 has been reserved
Jul 13 08:28:07 shippou kernel: [   10.865691] system 00:01: ioport range 0xc00-0xc01 has been reserved
Jul 13 08:28:07 shippou kernel: [   10.865694] system 00:01: ioport range 0xc14-0xc14 has been reserved
Jul 13 08:28:07 shippou kernel: [   10.865697] system 00:01: ioport range 0xc50-0xc52 has been reserved
Jul 13 08:28:07 shippou kernel: [   10.865700] system 00:01: ioport range 0xc6c-0xc6d has been reserved
Jul 13 08:28:07 shippou kernel: [   10.865703] system 00:01: ioport range 0xc6f-0xc6f has been reserved
Jul 13 08:28:07 shippou kernel: [   10.865706] system 00:01: ioport range 0xcd0-0xcd1 has been reserved
Jul 13 08:28:07 shippou kernel: [   10.865709] system 00:01: ioport range 0xcd2-0xcd3 has been reserved
Jul 13 08:28:07 shippou kernel: [   10.865712] system 00:01: ioport range 0xcd4-0xcdf has been reserved
Jul 13 08:28:07 shippou kernel: [   10.865716] system 00:01: ioport range 0x4000-0x40fe has been reserved
Jul 13 08:28:07 shippou kernel: [   10.865719] system 00:01: ioport range 0x4210-0x4217 has been reserved
Jul 13 08:28:07 shippou kernel: [   10.865722] system 00:01: ioport range 0xb10-0xb1f has been reserved
Jul 13 08:28:07 shippou kernel: [   10.865731] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
Jul 13 08:28:07 shippou kernel: [   10.865734] system 00:07: ioport range 0x220-0x225 has been reserved
Jul 13 08:28:07 shippou kernel: [   10.865737] system 00:07: ioport range 0xb00-0xb0f has been reserved
Jul 13 08:28:07 shippou kernel: [   10.865747] system 00:0d: iomem range 0xe0000000-0xefffffff could not be reserved
Jul 13 08:28:07 shippou kernel: [   10.865753] system 00:0e: iomem range 0xf0000-0xfffff could not be reserved
Jul 13 08:28:07 shippou kernel: [   10.865756] system 00:0e: iomem range 0xfed00000-0xfed000ff has been reserved
Jul 13 08:28:07 shippou kernel: [   10.865760] system 00:0e: iomem range 0x97fe0000-0x97ffffff could not be reserved
Jul 13 08:28:07 shippou kernel: [   10.865763] system 00:0e: iomem range 0xffff0000-0xffffffff has been reserved
Jul 13 08:28:07 shippou kernel: [   10.865767] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
Jul 13 08:28:07 shippou kernel: [   10.865770] system 00:0e: iomem range 0x100000-0x97fdffff could not be reserved
Jul 13 08:28:07 shippou kernel: [   10.865773] system 00:0e: iomem range 0x98000000-0x9fffffff has been reserved
Jul 13 08:28:07 shippou kernel: [   10.865776] system 00:0e: iomem range 0xfec00000-0xfec00fff has been reserved
Jul 13 08:28:07 shippou kernel: [   10.865780] system 00:0e: iomem range 0xfee00000-0xfee00fff could not be reserved
Jul 13 08:28:07 shippou kernel: [   10.865783] system 00:0e: iomem range 0xfff80000-0xfffeffff has been reserved
Jul 13 08:28:07 shippou kernel: [   10.866139] PCI: Bridge: 0000:00:01.0
Jul 13 08:28:07 shippou kernel: [   10.866142]   IO window: e000-efff
Jul 13 08:28:07 shippou kernel: [   10.866145]   MEM window: fdd00000-fdefffff
Jul 13 08:28:07 shippou kernel: [   10.866147]   PREFETCH window: d8000000-dfffffff
Jul 13 08:28:07 shippou kernel: [   10.866152] PCI: Bridge: 0000:00:14.4
Jul 13 08:28:07 shippou kernel: [   10.866155]   IO window: d000-dfff
Jul 13 08:28:07 shippou kernel: [   10.866160]   MEM window: fdc00000-fdcfffff
Jul 13 08:28:07 shippou kernel: [   10.866164]   PREFETCH window: fdf00000-fdffffff
Jul 13 08:28:07 shippou kernel: [   10.866188] NET: Registered protocol family 2
Jul 13 08:28:07 shippou kernel: [   10.901739] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Jul 13 08:28:07 shippou kernel: [   10.903366] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Jul 13 08:28:07 shippou kernel: [   10.911333] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jul 13 08:28:07 shippou kernel: [   10.912212] TCP: Hash tables configured (established 524288 bind 65536)
Jul 13 08:28:07 shippou kernel: [   10.912216] TCP reno registered
Jul 13 08:28:07 shippou kernel: [   10.921710] checking if image is initramfs... it is
Jul 13 08:28:07 shippou kernel: [   11.626377] Freeing initrd memory: 8212k freed
Jul 13 08:28:07 shippou kernel: [   11.633500] audit: initializing netlink socket (disabled)
Jul 13 08:28:07 shippou kernel: [   11.633514] audit(1215937666.416:1): initialized
Jul 13 08:28:07 shippou kernel: [   11.635481] VFS: Disk quotas dquot_6.5.1
Jul 13 08:28:07 shippou kernel: [   11.635554] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jul 13 08:28:07 shippou kernel: [   11.635695] io scheduler noop registered
Jul 13 08:28:07 shippou kernel: [   11.635698] io scheduler anticipatory registered
Jul 13 08:28:07 shippou kernel: [   11.635700] io scheduler deadline registered
Jul 13 08:28:07 shippou kernel: [   11.635804] io scheduler cfq registered (default)
Jul 13 08:28:07 shippou kernel: [   11.804410] Real Time Clock Driver v1.12ac
Jul 13 08:28:07 shippou kernel: [   11.804631] Linux agpgart interface v0.102
Jul 13 08:28:07 shippou kernel: [   11.804634] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jul 13 08:28:07 shippou kernel: [   11.804782] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 13 08:28:07 shippou kernel: [   11.805368] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 13 08:28:07 shippou kernel: [   11.806061] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jul 13 08:28:07 shippou kernel: [   11.806128] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jul 13 08:28:07 shippou kernel: [   11.806216] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jul 13 08:28:07 shippou kernel: [   11.806552] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 13 08:28:07 shippou kernel: [   11.806556] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 13 08:28:07 shippou kernel: [   11.812258] mice: PS/2 mouse device common for all mice
Jul 13 08:28:07 shippou kernel: [   11.812293] cpuidle: using governor ladder
Jul 13 08:28:07 shippou kernel: [   11.812295] cpuidle: using governor menu
Jul 13 08:28:07 shippou kernel: [   11.812447] NET: Registered protocol family 1
Jul 13 08:28:07 shippou kernel: [   11.812543] registered taskstats version 1
Jul 13 08:28:07 shippou kernel: [   11.812664]   Magic number: 0:754:472
Jul 13 08:28:07 shippou kernel: [   11.812812]   hash matches device LNXSYSTM:00
Jul 13 08:28:07 shippou kernel: [   11.812816] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
Jul 13 08:28:07 shippou kernel: [   11.812819] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 13 08:28:07 shippou kernel: [   11.812820] EDD information not available.
Jul 13 08:28:07 shippou kernel: [   11.812829] Freeing unused kernel memory: 320k freed
Jul 13 08:28:07 shippou kernel: [   11.840013] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jul 13 08:28:07 shippou kernel: [   13.010569] fuse init (API version 7.9)
Jul 13 08:28:07 shippou kernel: [   13.025828] ACPI: Fan [FAN] (on)
Jul 13 08:28:07 shippou kernel: [   13.031709] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Jul 13 08:28:07 shippou kernel: [   13.033049] ACPI: Thermal Zone [THRM] (40 C)
Jul 13 08:28:07 shippou kernel: [   13.571030] SCSI subsystem initialized
Jul 13 08:28:07 shippou kernel: [   13.631686] usbcore: registered new interface driver usbfs
Jul 13 08:28:07 shippou kernel: [   13.631708] usbcore: registered new interface driver hub
Jul 13 08:28:07 shippou kernel: [   13.645015] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 13 08:28:07 shippou kernel: [   13.645134] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
Jul 13 08:28:07 shippou kernel: [   13.645141] ahci 0000:00:12.0: controller can't do PMP, turning off CAP_PMP
Jul 13 08:28:07 shippou kernel: [   13.656920] usbcore: registered new device driver usb
Jul 13 08:28:07 shippou kernel: [   13.669866] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jul 13 08:28:07 shippou kernel: [   13.670839] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jul 13 08:28:07 shippou kernel: [   13.872938] Floppy drive(s): fd0 is 1.44M
Jul 13 08:28:07 shippou kernel: [   13.892579] FDC 0 is a post-1991 82077
Jul 13 08:28:07 shippou kernel: [   14.647187] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Jul 13 08:28:07 shippou kernel: [   14.647194] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pio slum part 
Jul 13 08:28:07 shippou kernel: [   14.648403] scsi0 : ahci
Jul 13 08:28:07 shippou kernel: [   14.648731] scsi1 : ahci
Jul 13 08:28:07 shippou kernel: [   14.648881] scsi2 : ahci
Jul 13 08:28:07 shippou kernel: [   14.649025] scsi3 : ahci
Jul 13 08:28:07 shippou kernel: [   14.649105] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 16
Jul 13 08:28:07 shippou kernel: [   14.649109] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 16
Jul 13 08:28:07 shippou kernel: [   14.649112] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 16
Jul 13 08:28:07 shippou kernel: [   14.649116] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 16
Jul 13 08:28:07 shippou kernel: [   15.122329] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 13 08:28:07 shippou kernel: [   15.165762] ata1.00: ATA-7: ST380215AS, 3.AAD, max UDMA/133
Jul 13 08:28:07 shippou kernel: [   15.165766] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32)
Jul 13 08:28:07 shippou kernel: [   15.223988] ata1.00: configured for UDMA/133
Jul 13 08:28:07 shippou kernel: [   15.533613] ata2: SATA link down (SStatus 0 SControl 300)
Jul 13 08:28:07 shippou kernel: [   15.845076] ata3: SATA link down (SStatus 0 SControl 300)
Jul 13 08:28:07 shippou kernel: [   16.156538] ata4: SATA link down (SStatus 0 SControl 300)
Jul 13 08:28:07 shippou kernel: [   16.156664] scsi 0:0:0:0: Direct-Access     ATA      ST380215AS       3.AA PQ: 0 ANSI: 5
Jul 13 08:28:07 shippou kernel: [   16.158119] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 13 08:28:07 shippou kernel: [   16.158238] ohci_hcd 0000:00:13.0: OHCI Host Controller
Jul 13 08:28:07 shippou kernel: [   16.158506] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Jul 13 08:28:07 shippou kernel: [   16.158526] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02e000
Jul 13 08:28:07 shippou kernel: [   16.165681] Driver 'sd' needs updating - please use bus_type methods
Jul 13 08:28:07 shippou kernel: [   16.172566] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jul 13 08:28:07 shippou kernel: [   16.172580] sd 0:0:0:0: [sda] Write Protect is off
Jul 13 08:28:07 shippou kernel: [   16.172596] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 13 08:28:07 shippou kernel: [   16.172649] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jul 13 08:28:07 shippou kernel: [   16.172658] sd 0:0:0:0: [sda] Write Protect is off
Jul 13 08:28:07 shippou kernel: [   16.172673] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 13 08:28:07 shippou kernel: [   16.172677]  sda: sda1 sda2 sda3 sda4
Jul 13 08:28:07 shippou kernel: [   16.216683] usb usb1: configuration #1 chosen from 1 choice
Jul 13 08:28:07 shippou kernel: [   16.216708] hub 1-0:1.0: USB hub found
Jul 13 08:28:07 shippou kernel: [   16.216717] hub 1-0:1.0: 2 ports detected
Jul 13 08:28:07 shippou kernel: [   16.224043] sd 0:0:0:0: [sda] Attached SCSI disk
Jul 13 08:28:07 shippou kernel: [   16.229328] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 13 08:28:07 shippou kernel: [   16.320362] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 17
Jul 13 08:28:07 shippou kernel: [   16.320526] ohci_hcd 0000:00:13.1: OHCI Host Controller
Jul 13 08:28:07 shippou kernel: [   16.320660] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Jul 13 08:28:07 shippou kernel: [   16.320685] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfe02d000
Jul 13 08:28:07 shippou kernel: [   16.380403] usb usb2: configuration #1 chosen from 1 choice
Jul 13 08:28:07 shippou kernel: [   16.380429] hub 2-0:1.0: USB hub found
Jul 13 08:28:07 shippou kernel: [   16.380439] hub 2-0:1.0: 2 ports detected
Jul 13 08:28:07 shippou kernel: [   16.484071] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 18
Jul 13 08:28:07 shippou kernel: [   16.484213] ohci_hcd 0000:00:13.2: OHCI Host Controller
Jul 13 08:28:07 shippou kernel: [   16.484276] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
Jul 13 08:28:07 shippou kernel: [   16.484299] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfe02c000
Jul 13 08:28:07 shippou kernel: [   16.544204] usb usb3: configuration #1 chosen from 1 choice
Jul 13 08:28:07 shippou kernel: [   16.544239] hub 3-0:1.0: USB hub found
Jul 13 08:28:07 shippou kernel: [   16.544248] hub 3-0:1.0: 2 ports detected
Jul 13 08:28:07 shippou kernel: [   16.605505] Attempting manual resume
Jul 13 08:28:07 shippou kernel: [   16.647778] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 17
Jul 13 08:28:07 shippou kernel: [   16.647899] ohci_hcd 0000:00:13.3: OHCI Host Controller
Jul 13 08:28:07 shippou kernel: [   16.647962] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
Jul 13 08:28:07 shippou kernel: [   16.647980] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfe02b000
Jul 13 08:28:07 shippou kernel: [   16.652792] kjournald starting.  Commit interval 5 seconds
Jul 13 08:28:07 shippou kernel: [   16.652805] EXT3-fs: mounted filesystem with ordered data mode.
Jul 13 08:28:07 shippou kernel: [   16.707828] usb usb4: configuration #1 chosen from 1 choice
Jul 13 08:28:07 shippou kernel: [   16.707853] hub 4-0:1.0: USB hub found
Jul 13 08:28:07 shippou kernel: [   16.707862] hub 4-0:1.0: 2 ports detected
Jul 13 08:28:07 shippou kernel: [   16.811500] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 18
Jul 13 08:28:07 shippou kernel: [   16.811667] ohci_hcd 0000:00:13.4: OHCI Host Controller
Jul 13 08:28:07 shippou kernel: [   16.811727] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
Jul 13 08:28:07 shippou kernel: [   16.811746] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfe02a000
Jul 13 08:28:07 shippou kernel: [   16.871548] usb usb5: configuration #1 chosen from 1 choice
Jul 13 08:28:07 shippou kernel: [   16.871572] hub 5-0:1.0: USB hub found
Jul 13 08:28:07 shippou kernel: [   16.871581] hub 5-0:1.0: 2 ports detected
Jul 13 08:28:07 shippou kernel: [   16.975375] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 19
Jul 13 08:28:07 shippou kernel: [   16.975504] ehci_hcd 0000:00:13.5: EHCI Host Controller
Jul 13 08:28:07 shippou kernel: [   16.975566] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
Jul 13 08:28:07 shippou kernel: [   16.975607] ehci_hcd 0000:00:13.5: debug port 1
Jul 13 08:28:07 shippou kernel: [   16.975626] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfe029000
Jul 13 08:28:07 shippou kernel: [   16.987113] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jul 13 08:28:07 shippou kernel: [   16.987230] usb usb6: configuration #1 chosen from 1 choice
Jul 13 08:28:07 shippou kernel: [   16.987255] hub 6-0:1.0: USB hub found
Jul 13 08:28:07 shippou kernel: [   16.987262] hub 6-0:1.0: 10 ports detected
Jul 13 08:28:07 shippou kernel: [   17.091159] SB600_PATA: IDE controller (0x1002:0x438c rev 0x00) at  PCI slot 0000:00:14.1
Jul 13 08:28:07 shippou kernel: [   17.091172] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
Jul 13 08:28:07 shippou kernel: [   17.091183] SB600_PATA: not 100% native mode: will probe irqs later
Jul 13 08:28:07 shippou kernel: [   17.091191]     ide0: BM-DMA at 0xf900-0xf907, BIOS settings: hda:pio, hdb:DMA
Jul 13 08:28:07 shippou kernel: [   17.877889] hdb: LITE-ON DVDRW LH-20A1P, ATAPI CD/DVD-ROM drive
Jul 13 08:28:07 shippou kernel: [   18.157415] hdb: UDMA/66 mode selected
Jul 13 08:28:07 shippou kernel: [   18.157791] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Jul 13 08:28:07 shippou kernel: [   18.170702] r8169 Gigabit Ethernet driver 2.2LK loaded
Jul 13 08:28:07 shippou kernel: [   18.170739] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 22 (level, low) -> IRQ 22
Jul 13 08:28:07 shippou kernel: [   18.170968] eth0: RTL8169sc/8110sc at 0xffffc20001044000, 00:19:21:21:21:b5, XID 18000000 IRQ 22
Jul 13 08:28:07 shippou kernel: [   23.345568] input: PC Speaker as /devices/platform/pcspkr/input/input2
Jul 13 08:28:07 shippou kernel: [   23.600042] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 13 08:28:07 shippou kernel: [   23.646703] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul 13 08:28:07 shippou kernel: [   23.686620] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Jul 13 08:28:07 shippou kernel: [   23.956621] input: Power Button (FF) as /devices/virtual/input/input3
Jul 13 08:28:07 shippou kernel: [   23.975192] ACPI: Power Button (FF) [PWRF]
Jul 13 08:28:07 shippou kernel: [   23.975252] input: Power Button (CM) as /devices/virtual/input/input4
Jul 13 08:28:07 shippou kernel: [   24.003025] ACPI: Power Button (CM) [PWRB]
Jul 13 08:28:07 shippou kernel: [   24.074289] input: ImExPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Jul 13 08:28:07 shippou kernel: [   24.105327] parport_pc 00:0a: reported by Plug and Play ACPI
Jul 13 08:28:07 shippou kernel: [   24.105385] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jul 13 08:28:07 shippou kernel: [   25.344817] hdb: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
Jul 13 08:28:07 shippou kernel: [   25.344825] Uniform CD-ROM driver Revision: 3.20
Jul 13 08:28:07 shippou kernel: [   25.614767] r8169: eth0: link up
Jul 13 08:28:07 shippou kernel: [   25.656479] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
Jul 13 08:28:07 shippou kernel: [   25.681917] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
Jul 13 08:28:07 shippou kernel: [   26.027593] NET: Registered protocol family 10
Jul 13 08:28:07 shippou kernel: [   26.027809] lo: Disabled Privacy Extensions
Jul 13 08:28:07 shippou kernel: [   28.767029] lp0: using parport0 (interrupt-driven).
Jul 13 08:28:07 shippou kernel: [   28.859816] Adding 289160k swap on /dev/sda3.  Priority:-1 extents:1 across:289160k
Jul 13 08:28:07 shippou kernel: [   29.414330] EXT3 FS on sda2, internal journal
Jul 13 08:28:07 shippou kernel: [   30.322627] kjournald starting.  Commit interval 5 seconds
Jul 13 08:28:07 shippou kernel: [   30.322822] EXT3 FS on sda4, internal journal
Jul 13 08:28:07 shippou kernel: [   30.322827] EXT3-fs: mounted filesystem with ordered data mode.
Jul 13 08:28:07 shippou kernel: [   30.766643] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul 13 08:28:07 shippou kernel: [   31.239491] No dock devices found.
Jul 13 08:28:07 shippou kernel: [   31.498866] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (1 cpu cores) (version 2.20.00)
Jul 13 08:28:07 shippou kernel: [   31.498907] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
Jul 13 08:28:07 shippou kernel: [   31.498909] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
Jul 13 08:28:07 shippou dhcdbd: Started up.
Jul 13 08:28:08 shippou kernel: [   33.406807] Marking TSC unstable due to cpufreq changes
Jul 13 08:28:08 shippou kernel: [   33.419594] Time: hpet clocksource has been installed.
Jul 13 08:28:09 shippou kernel: [   33.563290] Clocksource tsc unstable (delta = -125446001 ns)
Jul 13 08:28:14 shippou kernel: [   36.471769] [drm] Initialized drm 1.1.0 20060810
Jul 13 08:28:20 shippou kernel: [   40.138988] hda-intel: Invalid position buffer, using LPIB read method instead.
Jul 13 08:28:22 shippou kernel: [   41.711756] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jul 13 08:28:23 shippou exiting on signal 15
Jul 13 08:29:08 shippou syslogd 1.5.0#1ubuntu1: restart.
Jul 13 08:29:08 shippou kernel: Inspecting /boot/System.map-2.6.24-19-generic
Jul 13 08:29:08 shippou kernel: Loaded 28491 symbols from /boot/System.map-2.6.24-19-generic.
Jul 13 08:29:08 shippou kernel: Symbols match kernel version 2.6.24.
Jul 13 08:29:08 shippou kernel: Loaded 16834 symbols from 77 modules.
Jul 13 08:29:08 shippou kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 13 08:29:08 shippou kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 13 08:29:08 shippou kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:15:37 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
Jul 13 08:29:08 shippou kernel: [    0.000000] Command line: root=UUID=2e985bef-5550-421f-b1bf-e1f730273cbc ro quiet splash
Jul 13 08:29:08 shippou kernel: [    0.000000] BIOS-provided physical RAM map:
Jul 13 08:29:08 shippou kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jul 13 08:29:08 shippou kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jul 13 08:29:08 shippou kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jul 13 08:29:08 shippou kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000097fe0000 (usable)
Jul 13 08:29:08 shippou kernel: [    0.000000]  BIOS-e820: 0000000097fe0000 - 0000000097fe3000 (ACPI NVS)
Jul 13 08:29:08 shippou kernel: [    0.000000]  BIOS-e820: 0000000097fe3000 - 0000000097ff0000 (ACPI data)
Jul 13 08:29:08 shippou kernel: [    0.000000]  BIOS-e820: 0000000097ff0000 - 0000000098000000 (reserved)
Jul 13 08:29:08 shippou kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Jul 13 08:29:08 shippou kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Jul 13 08:29:08 shippou kernel: [    0.000000] end_pfn_map = 1048576
Jul 13 08:29:08 shippou kernel: [    0.000000] DMI 2.5 present.
Jul 13 08:29:08 shippou kernel: [    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F7B80 checksum 0
Jul 13 08:29:08 shippou kernel: [    0.000000] ACPI: RSDP 000F7B80, 0024 (r2 RS690 )
Jul 13 08:29:08 shippou kernel: [    0.000000] ACPI: RSDT 97FE3040, 0038 (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 13 08:29:08 shippou kernel: [    0.000000] ACPI: FACP 97FE30C0, 0074 (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 13 08:29:08 shippou kernel: [    0.000000] ACPI: DSDT 97FE3180, 4B0B (r1 RS690  AWRDACPI     1000 MSFT  3000000)
Jul 13 08:29:08 shippou kernel: [    0.000000] ACPI: FACS 97FE0000, 0040
Jul 13 08:29:08 shippou kernel: [    0.000000] ACPI: SSDT 97FE7DC0, 00D3 (r1 PTLTD  POWERNOW        1  LTP        1)
Jul 13 08:29:08 shippou kernel: [    0.000000] ACPI: HPET 97FE7F00, 0038 (r1 RS690  AWRDACPI 42302E31 AWRD       98)
Jul 13 08:29:08 shippou kernel: [    0.000000] ACPI: MCFG 97FE7F80, 003C (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 13 08:29:08 shippou kernel: [    0.000000] ACPI: APIC 97FE7D00, 0068 (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Jul 13 08:29:08 shippou kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Jul 13 08:29:08 shippou kernel: [    0.000000] CPU has 1 num_cores
Jul 13 08:29:08 shippou kernel: [    0.000000] No NUMA configuration found
Jul 13 08:29:08 shippou kernel: [    0.000000] Faking a node at 0000000000000000-0000000097fe0000
Jul 13 08:29:08 shippou kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000097fe0000
Jul 13 08:29:08 shippou kernel: [    0.000000] Zone PFN ranges:
Jul 13 08:29:08 shippou kernel: [    0.000000]   DMA             0 ->     4096
Jul 13 08:29:08 shippou kernel: [    0.000000]   DMA32        4096 ->  1048576
Jul 13 08:29:08 shippou kernel: [    0.000000]   Normal    1048576 ->  1048576
Jul 13 08:29:08 shippou kernel: [    0.000000] Movable zone start PFN for each node
Jul 13 08:29:08 shippou kernel: [    0.000000] early_node_map[2] active PFN ranges
Jul 13 08:29:08 shippou kernel: [    0.000000]     0:        0 ->      159
Jul 13 08:29:08 shippou kernel: [    0.000000]     0:      256 ->   622560
Jul 13 08:29:08 shippou kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Jul 13 08:29:08 shippou kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Jul 13 08:29:08 shippou kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul 13 08:29:08 shippou kernel: [    0.000000] Processor #0 (Bootup-CPU)
Jul 13 08:29:08 shippou kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Jul 13 08:29:08 shippou kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul 13 08:29:08 shippou kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jul 13 08:29:08 shippou kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jul 13 08:29:08 shippou kernel: [    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
Jul 13 08:29:08 shippou kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 13 08:29:08 shippou kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jul 13 08:29:08 shippou kernel: [    0.000000] Setting APIC routing to flat
Jul 13 08:29:08 shippou kernel: [    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
Jul 13 08:29:08 shippou kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 13 08:29:08 shippou kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Jul 13 08:29:08 shippou kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Jul 13 08:29:08 shippou kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Jul 13 08:29:08 shippou kernel: [    0.000000] Allocating PCI resources starting at a0000000 (gap: 98000000:48000000)
Jul 13 08:29:08 shippou kernel: [    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
Jul 13 08:29:08 shippou kernel: [    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
Jul 13 08:29:08 shippou kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 612716
Jul 13 08:29:08 shippou kernel: [    0.000000] Policy zone: DMA32
Jul 13 08:29:08 shippou kernel: [    0.000000] Kernel command line: root=UUID=2e985bef-5550-421f-b1bf-e1f730273cbc ro quiet splash
Jul 13 08:29:08 shippou kernel: [    0.000000] Initializing CPU#0
Jul 13 08:29:08 shippou kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Jul 13 08:29:08 shippou kernel: [    0.000000] TSC calibrated against HPET
Jul 13 08:29:08 shippou kernel: [   11.258353] time.c: Detected 1799.809 MHz processor.
Jul 13 08:29:08 shippou kernel: [   11.259050] Console: colour VGA+ 80x25
Jul 13 08:29:08 shippou kernel: [   11.259053] console [tty0] enabled
Jul 13 08:29:08 shippou kernel: [   11.259070] Checking aperture...
Jul 13 08:29:08 shippou kernel: [   11.259072] CPU 0: aperture @ bc50000000 size 32 MB
Jul 13 08:29:08 shippou kernel: [   11.259074] Aperture too small (32 MB)
Jul 13 08:29:08 shippou kernel: [   11.268876] No AGP bridge found
Jul 13 08:29:08 shippou kernel: [   11.302182] Memory: 2442456k/2490240k available (2489k kernel code, 47396k reserved, 1318k data, 320k init)
Jul 13 08:29:08 shippou kernel: [   11.302221] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Jul 13 08:29:08 shippou kernel: [   11.380361] Calibrating delay using timer specific routine.. 3709.34 BogoMIPS (lpj=7418699)
Jul 13 08:29:08 shippou kernel: [   11.380408] Security Framework initialized
Jul 13 08:29:08 shippou kernel: [   11.380414] SELinux:  Disabled at boot.
Jul 13 08:29:08 shippou kernel: [   11.380427] AppArmor: AppArmor initialized
Jul 13 08:29:08 shippou kernel: [   11.380430] Failure registering capabilities with primary security module.
Jul 13 08:29:08 shippou kernel: [   11.380809] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jul 13 08:29:08 shippou kernel: [   11.384817] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jul 13 08:29:08 shippou kernel: [   11.386425] Mount-cache hash table entries: 256
Jul 13 08:29:08 shippou kernel: [   11.386575] Initializing cgroup subsys ns
Jul 13 08:29:08 shippou kernel: [   11.386579] Initializing cgroup subsys cpuacct
Jul 13 08:29:08 shippou kernel: [   11.386595] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jul 13 08:29:08 shippou kernel: [   11.386597] CPU: L2 Cache: 512K (64 bytes/line)
Jul 13 08:29:08 shippou kernel: [   11.386599] CPU 0/0 -> Node 0
Jul 13 08:29:08 shippou kernel: [   11.386628] SMP alternatives: switching to UP code
Jul 13 08:29:08 shippou kernel: [   11.387314] Early unpacking initramfs... done
Jul 13 08:29:08 shippou kernel: [   11.788167] ACPI: Core revision 20070126
Jul 13 08:29:08 shippou kernel: [   11.788228] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Jul 13 08:29:08 shippou kernel: [   11.837711] Using local APIC timer interrupts.
Jul 13 08:29:08 shippou kernel: [   11.893188] Detected 12.498 MHz APIC timer.
Jul 13 08:29:08 shippou kernel: [   11.893237] Brought up 1 CPUs
Jul 13 08:29:08 shippou kernel: [   11.893508] net_namespace: 120 bytes
Jul 13 08:29:08 shippou kernel: [   11.893909] Time:  8:28:47  Date: 07/13/08
Jul 13 08:29:08 shippou kernel: [   11.893938] NET: Registered protocol family 16
Jul 13 08:29:08 shippou kernel: [   11.894110] ACPI: bus type pci registered
Jul 13 08:29:08 shippou kernel: [   11.894178] PCI: Using configuration type 1
Jul 13 08:29:08 shippou kernel: [   11.900877] ACPI: Interpreter enabled
Jul 13 08:29:08 shippou kernel: [   11.900884] ACPI: (supports S0 S3 S4 S5)
Jul 13 08:29:08 shippou kernel: [   11.900900] ACPI: Using IOAPIC for interrupt routing
Jul 13 08:29:08 shippou kernel: [   11.906094] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul 13 08:29:08 shippou kernel: [   11.906256] pci 0000:00:12.0: set SATA to AHCI mode
Jul 13 08:29:08 shippou kernel: [   11.907055] PCI: Transparent bridge - 0000:00:14.4
Jul 13 08:29:08 shippou kernel: [   11.927796] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 13 08:29:08 shippou kernel: [   11.927902] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 13 08:29:08 shippou kernel: [   11.928005] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 13 08:29:08 shippou kernel: [   11.928108] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 13 08:29:08 shippou kernel: [   11.928212] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 13 08:29:08 shippou kernel: [   11.928314] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 13 08:29:08 shippou kernel: [   11.928417] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 13 08:29:08 shippou kernel: [   11.928520] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 13 08:29:08 shippou kernel: [   11.928636] Linux Plug and Play Support v0.97 (c) Adam Belay
Jul 13 08:29:08 shippou kernel: [   11.928665] pnp: PnP ACPI init
Jul 13 08:29:08 shippou kernel: [   11.928673] ACPI: bus type pnp registered
Jul 13 08:29:08 shippou kernel: [   11.931690] pnp: PnP ACPI: found 15 devices
Jul 13 08:29:08 shippou kernel: [   11.931694] ACPI: ACPI bus type pnp unregistered
Jul 13 08:29:08 shippou kernel: [   11.931925] PCI: Using ACPI for IRQ routing
Jul 13 08:29:08 shippou kernel: [   11.931928] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jul 13 08:29:08 shippou kernel: [   11.945144] NET: Registered protocol family 8
Jul 13 08:29:08 shippou kernel: [   11.945146] NET: Registered protocol family 20
Jul 13 08:29:08 shippou kernel: [   11.945225] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Jul 13 08:29:08 shippou kernel: [   11.945230] hpet0: 4 32-bit timers, 14318180 Hz
Jul 13 08:29:08 shippou kernel: [   11.946284] AppArmor: AppArmor Filesystem Enabled
Jul 13 08:29:08 shippou kernel: [   11.949103] Time: tsc clocksource has been installed.
Jul 13 08:29:08 shippou kernel: [   11.957085] system 00:01: ioport range 0x4100-0x411f has been reserved
Jul 13 08:29:08 shippou kernel: [   11.957088] system 00:01: ioport range 0x228-0x22f has been reserved
Jul 13 08:29:08 shippou kernel: [   11.957092] system 00:01: ioport range 0x40b-0x40b has been reserved
Jul 13 08:29:08 shippou kernel: [   11.957095] system 00:01: ioport range 0x4d6-0x4d6 has been reserved
Jul 13 08:29:08 shippou kernel: [   11.957098] system 00:01: ioport range 0xc00-0xc01 has been reserved
Jul 13 08:29:08 shippou kernel: [   11.957101] system 00:01: ioport range 0xc14-0xc14 has been reserved
Jul 13 08:29:08 shippou kernel: [   11.957104] system 00:01: ioport range 0xc50-0xc52 has been reserved
Jul 13 08:29:08 shippou kernel: [   11.957107] system 00:01: ioport range 0xc6c-0xc6d has been reserved
Jul 13 08:29:08 shippou kernel: [   11.957110] system 00:01: ioport range 0xc6f-0xc6f has been reserved
Jul 13 08:29:08 shippou kernel: [   11.957113] system 00:01: ioport range 0xcd0-0xcd1 has been reserved
Jul 13 08:29:08 shippou kernel: [   11.957116] system 00:01: ioport range 0xcd2-0xcd3 has been reserved
Jul 13 08:29:08 shippou kernel: [   11.957119] system 00:01: ioport range 0xcd4-0xcdf has been reserved
Jul 13 08:29:08 shippou kernel: [   11.957122] system 00:01: ioport range 0x4000-0x40fe has been reserved
Jul 13 08:29:08 shippou kernel: [   11.957125] system 00:01: ioport range 0x4210-0x4217 has been reserved
Jul 13 08:29:08 shippou kernel: [   11.957128] system 00:01: ioport range 0xb10-0xb1f has been reserved
Jul 13 08:29:08 shippou kernel: [   11.957137] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
Jul 13 08:29:08 shippou kernel: [   11.957140] system 00:07: ioport range 0x220-0x225 has been reserved
Jul 13 08:29:08 shippou kernel: [   11.957143] system 00:07: ioport range 0xb00-0xb0f has been reserved
Jul 13 08:29:08 shippou kernel: [   11.957153] system 00:0d: iomem range 0xe0000000-0xefffffff could not be reserved
Jul 13 08:29:08 shippou kernel: [   11.957159] system 00:0e: iomem range 0xf0000-0xfffff could not be reserved
Jul 13 08:29:08 shippou kernel: [   11.957163] system 00:0e: iomem range 0xfed00000-0xfed000ff has been reserved
Jul 13 08:29:08 shippou kernel: [   11.957166] system 00:0e: iomem range 0x97fe0000-0x97ffffff could not be reserved
Jul 13 08:29:08 shippou kernel: [   11.957170] system 00:0e: iomem range 0xffff0000-0xffffffff has been reserved
Jul 13 08:29:08 shippou kernel: [   11.957173] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
Jul 13 08:29:08 shippou kernel: [   11.957176] system 00:0e: iomem range 0x100000-0x97fdffff could not be reserved
Jul 13 08:29:08 shippou kernel: [   11.957180] system 00:0e: iomem range 0x98000000-0x9fffffff has been reserved
Jul 13 08:29:08 shippou kernel: [   11.957183] system 00:0e: iomem range 0xfec00000-0xfec00fff has been reserved
Jul 13 08:29:08 shippou kernel: [   11.957186] system 00:0e: iomem range 0xfee00000-0xfee00fff could not be reserved
Jul 13 08:29:08 shippou kernel: [   11.957190] system 00:0e: iomem range 0xfff80000-0xfffeffff has been reserved
Jul 13 08:29:08 shippou kernel: [   11.957547] PCI: Bridge: 0000:00:01.0
Jul 13 08:29:08 shippou kernel: [   11.957549]   IO window: e000-efff
Jul 13 08:29:08 shippou kernel: [   11.957552]   MEM window: fdd00000-fdefffff
Jul 13 08:29:08 shippou kernel: [   11.957555]   PREFETCH window: d8000000-dfffffff
Jul 13 08:29:08 shippou kernel: [   11.957559] PCI: Bridge: 0000:00:14.4
Jul 13 08:29:08 shippou kernel: [   11.957562]   IO window: d000-dfff
Jul 13 08:29:08 shippou kernel: [   11.957567]   MEM window: fdc00000-fdcfffff
Jul 13 08:29:08 shippou kernel: [   11.957571]   PREFETCH window: fdf00000-fdffffff
Jul 13 08:29:08 shippou kernel: [   11.957595] NET: Registered protocol family 2
Jul 13 08:29:08 shippou kernel: [   11.993145] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Jul 13 08:29:08 shippou kernel: [   11.994775] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Jul 13 08:29:08 shippou kernel: [   12.002048] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jul 13 08:29:08 shippou kernel: [   12.002927] TCP: Hash tables configured (established 524288 bind 65536)
Jul 13 08:29:08 shippou kernel: [   12.002930] TCP reno registered
Jul 13 08:29:08 shippou kernel: [   12.013120] checking if image is initramfs... it is
Jul 13 08:29:08 shippou kernel: [   12.717782] Freeing initrd memory: 8212k freed
Jul 13 08:29:08 shippou kernel: [   12.724893] audit: initializing netlink socket (disabled)
Jul 13 08:29:08 shippou kernel: [   12.724907] audit(1215937727.416:1): initialized
Jul 13 08:29:08 shippou kernel: [   12.726884] VFS: Disk quotas dquot_6.5.1
Jul 13 08:29:08 shippou kernel: [   12.726958] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jul 13 08:29:08 shippou kernel: [   12.727098] io scheduler noop registered
Jul 13 08:29:08 shippou kernel: [   12.727100] io scheduler anticipatory registered
Jul 13 08:29:08 shippou kernel: [   12.727102] io scheduler deadline registered
Jul 13 08:29:08 shippou kernel: [   12.727207] io scheduler cfq registered (default)
Jul 13 08:29:08 shippou kernel: [   12.895813] Real Time Clock Driver v1.12ac
Jul 13 08:29:08 shippou kernel: [   12.896033] Linux agpgart interface v0.102
Jul 13 08:29:08 shippou kernel: [   12.896035] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jul 13 08:29:08 shippou kernel: [   12.896185] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 13 08:29:08 shippou kernel: [   12.896778] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 13 08:29:08 shippou kernel: [   12.897478] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jul 13 08:29:08 shippou kernel: [   12.897549] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jul 13 08:29:08 shippou kernel: [   12.897640] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jul 13 08:29:08 shippou kernel: [   12.897976] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 13 08:29:08 shippou kernel: [   12.897981] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 13 08:29:08 shippou kernel: [   12.903666] mice: PS/2 mouse device common for all mice
Jul 13 08:29:08 shippou kernel: [   12.903702] cpuidle: using governor ladder
Jul 13 08:29:08 shippou kernel: [   12.903704] cpuidle: using governor menu
Jul 13 08:29:08 shippou kernel: [   12.903858] NET: Registered protocol family 1
Jul 13 08:29:08 shippou kernel: [   12.903957] registered taskstats version 1
Jul 13 08:29:08 shippou kernel: [   12.904078]   Magic number: 0:754:472
Jul 13 08:29:08 shippou kernel: [   12.904227]   hash matches device LNXSYSTM:00
Jul 13 08:29:08 shippou kernel: [   12.904231] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
Jul 13 08:29:08 shippou kernel: [   12.904234] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 13 08:29:08 shippou kernel: [   12.904235] EDD information not available.
Jul 13 08:29:08 shippou kernel: [   12.904244] Freeing unused kernel memory: 320k freed
Jul 13 08:29:08 shippou kernel: [   12.931421] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jul 13 08:29:08 shippou kernel: [   14.101439] fuse init (API version 7.9)
Jul 13 08:29:08 shippou kernel: [   14.116719] ACPI: Fan [FAN] (on)
Jul 13 08:29:08 shippou kernel: [   14.122661] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Jul 13 08:29:08 shippou kernel: [   14.123999] ACPI: Thermal Zone [THRM] (40 C)
Jul 13 08:29:08 shippou kernel: [   14.668620] SCSI subsystem initialized
Jul 13 08:29:08 shippou kernel: [   14.739139] usbcore: registered new interface driver usbfs
Jul 13 08:29:08 shippou kernel: [   14.739161] usbcore: registered new interface driver hub
Jul 13 08:29:08 shippou kernel: [   14.746416] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 13 08:29:08 shippou kernel: [   14.746557] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
Jul 13 08:29:08 shippou kernel: [   14.746563] ahci 0000:00:12.0: controller can't do PMP, turning off CAP_PMP
Jul 13 08:29:08 shippou kernel: [   14.760294] usbcore: registered new device driver usb
Jul 13 08:29:08 shippou kernel: [   14.768312] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jul 13 08:29:08 shippou kernel: [   14.769286] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jul 13 08:29:08 shippou kernel: [   14.964342] Floppy drive(s): fd0 is 1.44M
Jul 13 08:29:08 shippou kernel: [   14.986023] FDC 0 is a post-1991 82077
Jul 13 08:29:08 shippou kernel: [   15.746576] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Jul 13 08:29:08 shippou kernel: [   15.746582] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pio slum part 
Jul 13 08:29:08 shippou kernel: [   15.747778] scsi0 : ahci
Jul 13 08:29:08 shippou kernel: [   15.748104] scsi1 : ahci
Jul 13 08:29:08 shippou kernel: [   15.748253] scsi2 : ahci
Jul 13 08:29:08 shippou kernel: [   15.748403] scsi3 : ahci
Jul 13 08:29:08 shippou kernel: [   15.748480] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 16
Jul 13 08:29:08 shippou kernel: [   15.748484] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 16
Jul 13 08:29:08 shippou kernel: [   15.748489] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 16
Jul 13 08:29:08 shippou kernel: [   15.748493] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 16
Jul 13 08:29:08 shippou kernel: [   16.221733] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 13 08:29:08 shippou kernel: [   16.268432] ata1.00: ATA-7: ST380215AS, 3.AAD, max UDMA/133
Jul 13 08:29:08 shippou kernel: [   16.268435] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32)
Jul 13 08:29:08 shippou kernel: [   16.326654] ata1.00: configured for UDMA/133
Jul 13 08:29:08 shippou kernel: [   16.637008] ata2: SATA link down (SStatus 0 SControl 300)
Jul 13 08:29:08 shippou kernel: [   16.949469] ata3: SATA link down (SStatus 0 SControl 300)
Jul 13 08:29:08 shippou kernel: [   17.259929] ata4: SATA link down (SStatus 0 SControl 300)
Jul 13 08:29:08 shippou kernel: [   17.260053] scsi 0:0:0:0: Direct-Access     ATA      ST380215AS       3.AA PQ: 0 ANSI: 5
Jul 13 08:29:08 shippou kernel: [   17.261499] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 13 08:29:08 shippou kernel: [   17.261618] ohci_hcd 0000:00:13.0: OHCI Host Controller
Jul 13 08:29:08 shippou kernel: [   17.261889] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Jul 13 08:29:08 shippou kernel: [   17.261910] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02e000
Jul 13 08:29:08 shippou kernel: [   17.270160] Driver 'sd' needs updating - please use bus_type methods
Jul 13 08:29:08 shippou kernel: [   17.275959] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jul 13 08:29:08 shippou kernel: [   17.275973] sd 0:0:0:0: [sda] Write Protect is off
Jul 13 08:29:08 shippou kernel: [   17.275990] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 13 08:29:08 shippou kernel: [   17.276042] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jul 13 08:29:08 shippou kernel: [   17.276050] sd 0:0:0:0: [sda] Write Protect is off
Jul 13 08:29:08 shippou kernel: [   17.276066] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 13 08:29:08 shippou kernel: [   17.276070]  sda: sda1 sda2 sda3 sda4
Jul 13 08:29:08 shippou kernel: [   17.320077] usb usb1: configuration #1 chosen from 1 choice
Jul 13 08:29:08 shippou kernel: [   17.320102] hub 1-0:1.0: USB hub found
Jul 13 08:29:08 shippou kernel: [   17.320111] hub 1-0:1.0: 2 ports detected
Jul 13 08:29:08 shippou kernel: [   17.326286] sd 0:0:0:0: [sda] Attached SCSI disk
Jul 13 08:29:08 shippou kernel: [   17.331618] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 13 08:29:08 shippou kernel: [   17.423761] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 17
Jul 13 08:29:08 shippou kernel: [   17.423895] ohci_hcd 0000:00:13.1: OHCI Host Controller
Jul 13 08:29:08 shippou kernel: [   17.423961] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Jul 13 08:29:08 shippou kernel: [   17.423987] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfe02d000
Jul 13 08:29:08 shippou kernel: [   17.483792] usb usb2: configuration #1 chosen from 1 choice
Jul 13 08:29:08 shippou kernel: [   17.483816] hub 2-0:1.0: USB hub found
Jul 13 08:29:08 shippou kernel: [   17.483825] hub 2-0:1.0: 2 ports detected
Jul 13 08:29:08 shippou kernel: [   17.588492] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 18
Jul 13 08:29:08 shippou kernel: [   17.588631] ohci_hcd 0000:00:13.2: OHCI Host Controller
Jul 13 08:29:08 shippou kernel: [   17.588695] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
Jul 13 08:29:08 shippou kernel: [   17.588718] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfe02c000
Jul 13 08:29:08 shippou kernel: [   17.647521] usb usb3: configuration #1 chosen from 1 choice
Jul 13 08:29:08 shippou kernel: [   17.647557] hub 3-0:1.0: USB hub found
Jul 13 08:29:08 shippou kernel: [   17.647566] hub 3-0:1.0: 2 ports detected
Jul 13 08:29:08 shippou kernel: [   17.684558] Attempting manual resume
Jul 13 08:29:08 shippou kernel: [   17.730491] kjournald starting.  Commit interval 5 seconds
Jul 13 08:29:08 shippou kernel: [   17.730502] EXT3-fs: mounted filesystem with ordered data mode.
Jul 13 08:29:08 shippou kernel: [   17.751185] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 17
Jul 13 08:29:08 shippou kernel: [   17.751318] ohci_hcd 0000:00:13.3: OHCI Host Controller
Jul 13 08:29:08 shippou kernel: [   17.751380] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
Jul 13 08:29:08 shippou kernel: [   17.751399] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfe02b000
Jul 13 08:29:08 shippou kernel: [   17.811254] usb usb4: configuration #1 chosen from 1 choice
Jul 13 08:29:08 shippou kernel: [   17.811280] hub 4-0:1.0: USB hub found
Jul 13 08:29:08 shippou kernel: [   17.811289] hub 4-0:1.0: 2 ports detected
Jul 13 08:29:08 shippou kernel: [   17.914897] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 18
Jul 13 08:29:08 shippou kernel: [   17.915067] ohci_hcd 0000:00:13.4: OHCI Host Controller
Jul 13 08:29:08 shippou kernel: [   17.915172] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
Jul 13 08:29:08 shippou kernel: [   17.915190] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfe02a000
Jul 13 08:29:08 shippou kernel: [   17.974937] usb usb5: configuration #1 chosen from 1 choice
Jul 13 08:29:08 shippou kernel: [   17.974961] hub 5-0:1.0: USB hub found
Jul 13 08:29:08 shippou kernel: [   17.974970] hub 5-0:1.0: 2 ports detected
Jul 13 08:29:08 shippou kernel: [   18.078771] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 19
Jul 13 08:29:08 shippou kernel: [   18.078914] ehci_hcd 0000:00:13.5: EHCI Host Controller
Jul 13 08:29:08 shippou kernel: [   18.078975] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
Jul 13 08:29:08 shippou kernel: [   18.079017] ehci_hcd 0000:00:13.5: debug port 1
Jul 13 08:29:08 shippou kernel: [   18.079036] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfe029000
Jul 13 08:29:08 shippou kernel: [   18.090523] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jul 13 08:29:08 shippou kernel: [   18.090641] usb usb6: configuration #1 chosen from 1 choice
Jul 13 08:29:08 shippou kernel: [   18.090667] hub 6-0:1.0: USB hub found
Jul 13 08:29:08 shippou kernel: [   18.090674] hub 6-0:1.0: 10 ports detected
Jul 13 08:29:08 shippou kernel: [   18.194567] SB600_PATA: IDE controller (0x1002:0x438c rev 0x00) at  PCI slot 0000:00:14.1
Jul 13 08:29:08 shippou kernel: [   18.194579] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
Jul 13 08:29:08 shippou kernel: [   18.194590] SB600_PATA: not 100% native mode: will probe irqs later
Jul 13 08:29:08 shippou kernel: [   18.194599]     ide0: BM-DMA at 0xf900-0xf907, BIOS settings: hda:pio, hdb:DMA
Jul 13 08:29:08 shippou kernel: [   18.981285] hdb: LITE-ON DVDRW LH-20A1P, ATAPI CD/DVD-ROM drive
Jul 13 08:29:08 shippou kernel: [   19.260811] hdb: UDMA/66 mode selected
Jul 13 08:29:08 shippou kernel: [   19.261182] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Jul 13 08:29:08 shippou kernel: [   19.274089] r8169 Gigabit Ethernet driver 2.2LK loaded
Jul 13 08:29:08 shippou kernel: [   19.274128] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 22 (level, low) -> IRQ 22
Jul 13 08:29:08 shippou kernel: [   19.274362] eth0: RTL8169sc/8110sc at 0xffffc20001044000, 00:19:21:21:21:b5, XID 18000000 IRQ 22
Jul 13 08:29:08 shippou kernel: [   24.263931] input: PC Speaker as /devices/platform/pcspkr/input/input2
Jul 13 08:29:08 shippou kernel: [   24.460517] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Jul 13 08:29:08 shippou kernel: [   24.555348] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 13 08:29:08 shippou kernel: [   24.596884] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul 13 08:29:08 shippou kernel: [   24.876224] input: Power Button (FF) as /devices/virtual/input/input3
Jul 13 08:29:08 shippou kernel: [   24.891056] ACPI: Power Button (FF) [PWRF]
Jul 13 08:29:08 shippou kernel: [   24.891172] input: Power Button (CM) as /devices/virtual/input/input4
Jul 13 08:29:08 shippou kernel: [   24.906715] ACPI: Power Button (CM) [PWRB]
Jul 13 08:29:08 shippou kernel: [   25.012844] input: ImExPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Jul 13 08:29:08 shippou kernel: [   25.025124] parport_pc 00:0a: reported by Plug and Play ACPI
Jul 13 08:29:08 shippou kernel: [   25.025182] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jul 13 08:29:08 shippou kernel: [   26.481504] r8169: eth0: link up
Jul 13 08:29:08 shippou kernel: [   26.615925] hdb: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
Jul 13 08:29:08 shippou kernel: [   26.615933] Uniform CD-ROM driver Revision: 3.20
Jul 13 08:29:08 shippou kernel: [   26.757452] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
Jul 13 08:29:08 shippou kernel: [   26.781318] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
Jul 13 08:29:08 shippou kernel: [   27.047424] NET: Registered protocol family 10
Jul 13 08:29:08 shippou kernel: [   27.047638] lo: Disabled Privacy Extensions
Jul 13 08:29:08 shippou kernel: [   29.753292] lp0: using parport0 (interrupt-driven).
Jul 13 08:29:08 shippou kernel: [   29.845912] Adding 289160k swap on /dev/sda3.  Priority:-1 extents:1 across:289160k
Jul 13 08:29:08 shippou kernel: [   30.400579] EXT3 FS on sda2, internal journal
Jul 13 08:29:08 shippou kernel: [   31.317192] kjournald starting.  Commit interval 5 seconds
Jul 13 08:29:08 shippou kernel: [   31.317392] EXT3 FS on sda4, internal journal
Jul 13 08:29:08 shippou kernel: [   31.317396] EXT3-fs: mounted filesystem with ordered data mode.
Jul 13 08:29:08 shippou kernel: [   31.752905] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul 13 08:29:08 shippou kernel: [   32.233716] No dock devices found.
Jul 13 08:29:08 shippou kernel: [   32.485107] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (1 cpu cores) (version 2.20.00)
Jul 13 08:29:08 shippou kernel: [   32.485151] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
Jul 13 08:29:08 shippou kernel: [   32.485153] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
Jul 13 08:29:08 shippou dhcdbd: Started up.
Jul 13 08:29:09 shippou kernel: [   34.490257] Marking TSC unstable due to cpufreq changes
Jul 13 08:29:09 shippou kernel: [   34.505790] Time: hpet clocksource has been installed.
Jul 13 08:29:10 shippou kernel: [   34.652394] Clocksource tsc unstable (delta = -129977758 ns)
Jul 13 08:29:15 shippou kernel: [   37.491965] [drm] Initialized drm 1.1.0 20060810
Jul 13 08:29:21 shippou kernel: [   41.736240] hda-intel: Invalid position buffer, using LPIB read method instead.
Jul 13 08:30:39 shippou kernel: [   85.542058] UDF-fs: No VRS found

```

Sorry for this long post. I really need help. :(

---

