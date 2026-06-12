---
title: "LVM Restoration"
date: 2024-07-05
forum: Hardware
---

### Post by fingerbiceps on 2024-07-05
Hi,
I am attempting to restore my LVM and recover access to my data. Before this, I added a larger NVME drive, added it to my LVM, and moved the data to it. My system was still booting off of my HDD EFI partition. This was fine for months. When updating the night before, grub borked. I booted up a live cd and mounted all the expected folders to run grub-install, but after various attempts, I couldn't boot back into my OS. The data from the LVM took 100% of the new drive. The original plan was to use lvreduce to gain 512M and create an EFI partition directly on the NVME so that I could see if I could get grub to behave by getting everything on just the one NVME drive.

```
 
sudo vgscan
sudo vgchange -a y

sudo lvdisplay

sudo lvreduce -L -512M /dev/ubuntu-vg/root
sudo resize2fs /dev/ubuntu-vg/root

```

I believe these were the operations
When I went into GParted to make the partition though, it showed all of my data was gone so I stopped here
I ran e2fsck at this point, I believe, and it said something about superblocks and journals were all errored
I found that I could us vgcfgrestore to go back to a previous point prior to these operations
In GParted it now shows the space is used again, but I could not mount the system.
I used testdisk to see if I could see the files. It was able to get some stuff, but not the config files I was looking for.
I ran this command using data from testdisk fsck.ext4 -p -b [superblock number] -B 4096 /dev/nvme0n1
Now the drive will mount, but I can't see the files.
I used dd to image the drive so I could try to use strings to scan it from relevant text in the mean time if I can't find a way to restore the LVM
I have not rebooted or continued to mess with it

Is there any path forward to restoring access to the data on the LVM? I am trying to recover config files so the LVM doesn't necessarily need to usable, but it is preferred. 

Inix output:

```

System:
  Kernel: 6.5.0-9-generic arch: x86_64 bits: 64 compiler: N/A Console: pty pts/3 Distro: Ubuntu
    23.10 (Mantic Minotaur)
Machine:
  Type: Desktop System: ASUS product: N/A v: N/A serial: N/A
  Mobo: ASUSTeK model: TUF GAMING B560M-PLUS WIFI v: Rev 1.xx serial: <filter>
    UEFI: American Megatrends v: 1017 date: 07/13/2021
CPU:
  Info: 8-core model: 11th Gen Intel Core i9-11900K bits: 64 type: MT MCP arch: Rocket Lake rev: 1
    cache: L1: 640 KiB L2: 4 MiB L3: 16 MiB
  Speed (MHz): avg: 800 high: 801 min/max: 800/5100:5300 cores: 1: 800 2: 800 3: 800 4: 800
    5: 800 6: 800 7: 800 8: 800 9: 800 10: 800 11: 801 12: 800 13: 800 14: 800 15: 800 16: 800
    bogomips: 112128
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3
Graphics:
  Device-1: Intel RocketLake-S GT1 [UHD Graphics 750] vendor: ASUSTeK driver: i915 v: kernel
    arch: Gen-12.1 bus-ID: 00:02.0
  Display: server: X.org v: 1.21.1.7 with: Xwayland v: 23.2.0 driver: X: loaded: modesetting
    unloaded: fbdev,vesa dri: iris gpu: i915 tty: 209x111 resolution: 1920x1080
  API: OpenGL Message: GL data unavailable in console for root.
Audio:
  Device-1: Intel Tiger Lake-H HD Audio vendor: ASUSTeK driver: snd_hda_intel v: kernel
    bus-ID: 00:1f.3
  API: ALSA v: k6.5.0-9-generic status: kernel-api
  Server-1: PipeWire v: 0.3.79 status: n/a (root, process)
Network:
  Device-1: Intel Tiger Lake PCH CNVi WiFi driver: iwlwifi v: kernel bus-ID: 00:14.3
  IF: wlo1 state: down mac: <filter>
  Device-2: Realtek RTL8125 2.5GbE vendor: ASUSTeK driver: r8169 v: kernel port: 4000
    bus-ID: 03:00.0
  IF: enp3s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
Bluetooth:
  Device-1: Intel AX201 Bluetooth driver: btusb v: 0.8 type: USB bus-ID: 1-14:9
  Report: hciconfig ID: hci0 rfk-id: 0 state: up address: <filter> bt-v: 5.2 lmp-v: 11
Drives:
  Local Storage: total: 46.85 TiB lvm-free: 129.6 GiB used: 40.04 TiB (85.5%)
  ID-1: /dev/nvme0n1 vendor: Western Digital model: WD Blue SN570 1TB size: 931.51 GiB
    temp: 36.9 C
  ID-2: /dev/sda vendor: Western Digital model: WD5000LPLX-08ZNTT0 size: 465.76 GiB
  ID-3: /dev/sdb vendor: Western Digital model: WD180EDGZ-11BLDS0 size: 16.37 TiB type: USB
  ID-4: /dev/sdc vendor: SanDisk model: Cruzer Glide size: 14.32 GiB type: USB
  ID-5: /dev/sdd vendor: Western Digital model: WD160EDGZ-11B2DA0 size: 14.55 TiB type: USB
  ID-6: /dev/sde vendor: Western Digital model: WD160EDGZ-11B2DA0 size: 14.55 TiB type: USB
Partition:
  ID-1: / size: 15.55 GiB used: 339 MiB (2.1%) fs: overlay source: ERR-102
Swap:
  Alert: No swap data was found.
Sensors:
  System Temperatures: cpu: 24.0 C mobo: N/A
  Fan Speeds (rpm): N/A
Info:
  Processes: 441 Uptime: 22h 16m Memory: total: 32 GiB available: 31.1 GiB used: 3.28 GiB (10.5%)
  igpu: 64 MiB Init: systemd target: graphical (5) Compilers: N/A Packages: 1864 Shell: Bash
  v: 5.2.15 inxi: 3.3.29

```
Thanks,
Fingerbiceps

---

### Post by Dennis N on 2024-07-05
In first display, the file system should be resized before reducing the LV size. There is a warning in man lvreduce:

> Be careful when reducing an LV's size, because data in the reduced  area
       is lost. Ensure that any file system on the LV is resized before running
       lvreduce so that the removed extents are not in use by the file system.

You can also just use the -r option in lvreduce to resize the file system before reducing the LV. Read the man page of lvreduce for more information.

---

