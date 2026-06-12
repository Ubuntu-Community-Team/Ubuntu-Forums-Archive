---
title: "Graphics is llvmpipe and sound is lost after upgrade to 22.04"
date: 2022-05-06
forum: Hardware
---

### Post by goldbeere on 2022-05-06
Hi,

I'm new to the forum. ):P

I've upgraded Ubuntu from 21.10 to 22.04. It was a full functioning installation for running a game with lutris.

Now I have 1 fps in the game and also things are rendered slowly in firefox.

I use a Sapphire Nitro+ Radeon RX 580.

I have lost the sound too. No output at all.

In the settings of the Gnome Desktop one can see:

```

    Settings->About
        Graphics: llvmpipe (LLVM 13.0.1, 256 bits)

    Settings->Sound
        Output Device: "Dummy Output"
        (there is no other option available for selection)

```

(I have an Ubuntu 20.04 LTS installation at another SSD at the same computer. There all is as usual. Graphics card/driver and sound are working fine, but I've noticed that the kernel release over there is 5.13.0-40, whereas it is 5.13.0-39 here.)

I have tried to install amdgpu, but I've failed (see below). For the sound I had no idea at all.

Do you have any suggestions what to do besides a new OS-installation?

Thank you in advance for your time and effort. <3

Andreas


-------- some info from my system ---------------------
```

uname -a
    Linux ******* 5.13.0-39-generic #44-Ubuntu SMP Thu Mar 24 15:35:05 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

HardInfo shows (under 'Computer'):

    Graphics
        1920x1080
        llvmpipe (LLVM 13.0.1, 256 bits)
        The X.Org Foundation

inxi -G
    Graphics:
      Device-1: AMD Ellesmere [Radeon RX 470/480/570/570X/580/580X/590]
        driver: N/A
      Display: x11 server: X.Org v: 1.21.1.3 driver: X: loaded: ati,vesa
        unloaded: fbdev,modesetting,radeon gpu: N/A resolution: 1920x1080
      OpenGL: renderer: llvmpipe (LLVM 13.0.1 256 bits) v: 4.5 Mesa 22.0.1

sudo lshw -c video
  *-display UNCLAIMED       
       description: VGA compatible controller
       product: Ellesmere [Radeon RX 470/480/570/570X/580/580X/590]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:04:00.0
       version: e7
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:c0000000-cfffffff memory:d0000000-d01fffff ioport:d000(size=256) memory:fe700000-fe73ffff memory:c0000-dffff

dpkg --print-architecture
    amd64

dpkg --print-foreign-architectures
    i386


```

-------- Full inxi System information ---------------------
```
 

sudo inxi -F -x
    System:
      Host: **** Kernel: 5.13.0-39-generic x86_64 bits: 64
        compiler: gcc v: 11.2.0 Desktop: GNOME 42.0
        Distro: Ubuntu 22.04 LTS (Jammy Jellyfish)
    Machine:
      Type: Desktop Mobo: ASRock model: 990FX Killer serial: M80-6B024600096
        UEFI-[Legacy]: American Megatrends v: P1.60 date: 01/06/2016
    CPU:
      Info: 6-core model: AMD FX-6300 bits: 64 type: MT MCP arch: Piledriver
        rev: 0 cache: L1: 288 KiB L2: 6 MiB L3: 8 MiB
      Speed (MHz): avg: 1400 min/max: 1400/3500 boost: enabled cores: 1: 1400
        2: 1400 3: 1400 4: 1400 5: 1400 6: 1400 bogomips: 45154
      Flags: avx ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm
    Graphics:
      Device-1: AMD Ellesmere [Radeon RX 470/480/570/570X/580/580X/590]
        vendor: Sapphire Nitro+ driver: N/A bus-ID: 04:00.0
      Display: server: X.Org v: 1.21.1.3 driver: X: loaded: ati,vesa
        unloaded: fbdev,modesetting,radeon gpu: N/A resolution: 1920x1080
      OpenGL: renderer: llvmpipe (LLVM 13.0.1 256 bits) v: 4.5 Mesa 22.0.1
        direct render: Yes
    Audio:
      Device-1: AMD SBx00 Azalia vendor: ASRock driver: N/A bus-ID: 00:14.2
      Device-2: AMD Ellesmere HDMI Audio [Radeon RX 470/480 / 570/580/590]
        vendor: Sapphire driver: N/A bus-ID: 04:00.1
      Sound Server-1: PulseAudio v: 15.99.1 running: yes
      Sound Server-2: PipeWire v: 0.3.48 running: yes
    Network:
      Device-1: Qualcomm Atheros Killer E220x Gigabit Ethernet vendor: ASRock
        driver: alx v: kernel port: e000 bus-ID: 03:00.0
      IF: enp3s0 state: up speed: 1000 Mbps duplex: full mac: 70:85:c2:2d:3c:0f
    Drives:
      Local Storage: total: 2.16 TiB used: 93.79 GiB (4.2%)
      ID-1: /dev/nvme0n1 vendor: Corsair model: Force MP600 size: 931.51 GiB
        temp: 33.9 C
      ID-2: /dev/sda vendor: Samsung model: SSD 840 EVO 250GB size: 232.89 GiB
      ID-3: /dev/sdb vendor: Samsung model: SSD 860 EVO 1TB size: 931.51 GiB
      ID-4: /dev/sdc vendor: SanDisk model: SDSSDP128G size: 119.24 GiB
    Partition:
      ID-1: / size: 393.86 GiB used: 93.64 GiB (23.8%) fs: ext4 dev: /dev/sdb3
      ID-2: /boot size: 991.9 MiB used: 157.4 MiB (15.9%) fs: ext4
        dev: /dev/sdb1
    Swap:
      ID-1: swap-1 type: partition size: 8 GiB used: 0 KiB (0.0%) dev: /dev/sdb2
    Sensors:
      Message: No sensor data found. Is lm-sensors configured?
    Info:
      Processes: 279 Uptime: 1m Memory: 7.68 GiB used: 1.68 GiB (21.9%)
      Init: systemd runlevel: 5 Compilers: gcc: 11.2.0 Packages: 2470 Shell: Sudo
      v: 1.9.9 inxi: 3.3.13

```

-------- Attempt to install amdgpu ---------------------
```


sudo apt-get install ./amdgpu-install_21.50.2.50002-1_all.deb
    Reading package lists... Done
    Building dependency tree... Done
    Reading state information... Done
    Note, selecting 'amdgpu-install' instead of './amdgpu-install_21.50.2.50002-1_all.deb'
    amdgpu-install is already the newest version (21.50.2.50002-1384495).
    0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


amdgpu-install
    Hit:1 http://de.archive.ubuntu.com/ubuntu jammy InRelease
    Get:2 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]
    Hit:3 http://de.archive.ubuntu.com/ubuntu jammy-updates InRelease                                      
    Hit:4 http://de.archive.ubuntu.com/ubuntu jammy-backports InRelease                                    
    Hit:5 https://repo.radeon.com/amdgpu/21.50.2/ubuntu focal InRelease               
    Hit:6 https://repo.radeon.com/rocm/apt/5.0.2 ubuntu InRelease
    Fetched 110 kB in 1s (146 kB/s)
    Reading package lists... Done
    Reading package lists... Done
    Building dependency tree... Done
    Reading state information... Done
    Package linux-headers-5.13.0-39-generic is not available, but is referred to by another package.
    This may mean that the package is missing, has been obsoleted, or
    is only available from another source

    Package linux-modules-extra-5.13.0-39-generic is not available, but is referred to by another package.
    This may mean that the package is missing, has been obsoleted, or
    is only available from another source

    E: Package 'linux-headers-5.13.0-39-generic' has no installation candidate
    E: Package 'linux-modules-extra-5.13.0-39-generic' has no installation candidate
(same results with sudo)


amdgpu-install --no-dkms
    Hit:1 http://de.archive.ubuntu.com/ubuntu jammy InRelease
    Hit:2 http://de.archive.ubuntu.com/ubuntu jammy-updates InRelease      
    Get:3 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]
    Hit:4 http://de.archive.ubuntu.com/ubuntu jammy-backports InRelease                                    
    Hit:5 https://repo.radeon.com/amdgpu/21.50.2/ubuntu focal InRelease                                    
    Hit:6 https://repo.radeon.com/rocm/apt/5.0.2 ubuntu InRelease
    Fetched 110 kB in 1s (139 kB/s)
    Reading package lists... Done
    Reading package lists... Done
    Building dependency tree... Done
    Reading state information... Done
    Some packages could not be installed. This may mean that you have
    requested an impossible situation or if you are using the unstable
    distribution that some required packages have not yet been created
    or been moved out of Incoming.
    The following information may help to resolve the situation:

    The following packages have unmet dependencies:
     rocm-llvm : Depends: python but it is not installable
                 Depends: libstdc++-5-dev but it is not installable or
                          libstdc++-7-dev but it is not installable
                 Depends: libgcc-5-dev but it is not installable or
                          libgcc-7-dev but it is not installable
                 Recommends: gcc-multilib but it is not going to be installed
                 Recommends: g++-multilib but it is not going to be installed
     xserver-xorg-amdgpu-video-amdgpu : Depends: xorg-video-abi-24 but it is not installable
    E: Unable to correct problems, you have held broken packages.

```

---

### Post by Yellow Pasque on 2022-05-07
> Kernel: 5.13.0-39-generic x86_64 bits: 64

For some reason, you are still booting into the kernel from 21.10. Boot into the 5.15.x kernel and things should be better.

---

### Post by goldbeere on 2022-05-08
The hint about "booting into" lead me to the solution.

I use the boot manager from the parallel Ubuntu installation. So it wasn't updated by the upgrade process.
I've updated it by using boot-repair. Now it boots into a 5.15 kernel.

```

uname -a
Linux *** 5.15.0-27-generic #28-Ubuntu SMP Thu Apr 14 04:55:28 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

```

I've sound again and the graphics card is recognized. The game is working again too. 

Thank you for your help. :D

---

