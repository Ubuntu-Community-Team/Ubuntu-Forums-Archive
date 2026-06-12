---
title: "Help, my NVIDIA drivers are completely borked"
date: 2011-11-10
forum: Hardware
---

### Post by yang on 2011-11-10
I'm on Ubuntu 10.04 LTS and everything was fine up till about two hours ago, since when I've spent all my time trying to make things work again.  I was trying to install the latest drivers from the NVIDIA website, v285.05.09 (since I'm currently using the latest drivers available in Ubuntu, nvidia-current v195.36.24, yet WebGL doesn't work in either Chrome or Firefox, and they always suggest that I try the latest driver versions).

But after installing this and rebooting, X starts with an error, prompting me to run in reduced graphics mode and/or restore my graphics settings.  When I checked /var/log/kern.log I saw:

```
NVRM: API mismatch: the client has the version 285.05.09, but
NVRM: this kernel module has the version 195.36.24.  Please
NVRM: make sure that this kernel module and all NVIDIA driver
NVRM: components have the same version.
```

My questions has two parts:

[LIST=1]
[*]How do I actually make these latest NVIDIA drivers work?
[*]If I try this out and it doesn't work...how do I roll back what I had before?  Here's what I tried, all to no avail:
[LIST]
[*]picking the restore graphics settings option in the initial error prompt from X
[*]under Administration > Hardware Drivers, I see that the "NVIDIA (current)" option is already chosen/active, so I can't do anything here
[*]ran `sudo dpkg-reconfigure nvidia-current`
[/LIST]
[/LIST]

**Update**: Some additional info:

```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 10.04.3 LTS
Release: 10.04
Codename: lucid

$ uname -a
Linux zs 2.6.32-35-generic #78-Ubuntu SMP Tue Oct 11 16:11:24 UTC 2011 x86_64 GNU/Linux

$ dpkg -l | grep nvidia
ii nvidia-173 173.14.22-0ubuntu11 NVIDIA binary Xorg driver, kernel module and VDPAU li
ii nvidia-173-modaliases 173.14.22-0ubuntu11 Modaliases for the NVIDIA binary X.Org driver
ii nvidia-96-modaliases 96.43.17-0ubuntu1.1 Modaliases for the NVIDIA binary X.Org driver
ii nvidia-common 0.2.23 Find obsolete NVIDIA drivers
ii nvidia-current 195.36.24-0ubuntu1~10.04.1 NVIDIA binary Xorg driver, kernel module and VDPAU li
ii nvidia-current-modaliases 195.36.24-0ubuntu1~10.04.1 Modaliases for the NVIDIA binary X.Org driver
ii nvidia-settings 195.36.08-0ubuntu2 Tool of configuring the NVIDIA graphics driver
```

**Update 2**: Note, this is on a *desktop*.

---

### Post by yang on 2011-11-10
Gyaaah! I tried uninstalling my current drivers, rebooting, and installing the new drivers, but the drivers still aren't working. I still have to run X in reduced graphics mode, though now my resolution is no longer ridiculously low. Checking /var/log/kern.log for any lines mentioning "nouveau" or "NV":

```
...
Nov 10 11:53:23 zs kernel: [   29.935504] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 10 11:53:23 zs kernel: [   29.935512] nouveau 0000:01:00.0: setting latency timer to 64
Nov 10 11:53:23 zs kernel: [   29.939265] [drm] nouveau 0000:01:00.0: Detected an NV50 generation card (0x450300a3)
Nov 10 11:53:23 zs kernel: [   29.939787] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
Nov 10 11:53:23 zs kernel: [   29.985378] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input7
Nov 10 11:53:23 zs kernel: [   29.998478] [drm] nouveau 0000:01:00.0: ... appears to be valid
Nov 10 11:53:23 zs kernel: [   29.998483] [drm] nouveau 0000:01:00.0: BIT BIOS found
Nov 10 11:53:23 zs kernel: [   29.998486] [drm] nouveau 0000:01:00.0: Bios version 60.80.13.00
Nov 10 11:53:23 zs kernel: [   29.998490] [drm] nouveau 0000:01:00.0: TMDS table revision 2.0 not currently supported
Nov 10 11:53:23 zs kernel: [   29.998493] [drm] nouveau 0000:01:00.0: BIT table 'd' not found
Nov 10 11:53:23 zs kernel: [   29.998495] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 4.0
Nov 10 11:53:23 zs kernel: [   29.998499] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x40 5 6 2
Nov 10 11:53:23 zs kernel: [   29.998502] [drm] nouveau 0000:01:00.0:   0: 0x00001030: type 0x30 idx 0 tag 0x07
Nov 10 11:53:23 zs kernel: [   29.998506] [drm] nouveau 0000:01:00.0:   1: 0x00002130: type 0x30 idx 1 tag 0x08
Nov 10 11:53:23 zs kernel: [   29.998509] [drm] nouveau 0000:01:00.0:   2: 0x00000210: type 0x10 idx 2 tag 0xff
Nov 10 11:53:23 zs kernel: [   29.998511] [drm] nouveau 0000:01:00.0:   3: 0x00000211: type 0x11 idx 2 tag 0xff
Nov 10 11:53:23 zs kernel: [   29.998514] [drm] nouveau 0000:01:00.0:   4: 0x00000213: type 0x13 idx 2 tag 0xff
Nov 10 11:53:23 zs kernel: [   29.998517] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 04000320 00000028
Nov 10 11:53:23 zs kernel: [   29.998520] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 01000322 00000030
Nov 10 11:53:23 zs kernel: [   29.998523] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 02011310 00000028
Nov 10 11:53:23 zs kernel: [   29.998525] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 02011312 00000030
Nov 10 11:53:23 zs kernel: [   29.998528] [drm] nouveau 0000:01:00.0: Raw DCB entry 4: 010223f1 00c1c020
Nov 10 11:53:23 zs kernel: [   29.998537] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xBC7E
Nov 10 11:53:23 zs kernel: [   30.050942] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xBE86
Nov 10 11:53:23 zs kernel: [   30.120749] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xD041
Nov 10 11:53:23 zs kernel: [   30.120764] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xD130
Nov 10 11:53:23 zs kernel: [   30.140789] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xD2E7
Nov 10 11:53:23 zs kernel: [   30.140795] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table at offset 0xD34C
Nov 10 11:53:23 zs kernel: [   30.170875] [drm] nouveau 0000:01:00.0: 0xD34C: Condition still not met after 20ms, skipping following opcodes
Nov 10 11:53:23 zs kernel: [   30.170906] [drm] nouveau 0000:01:00.0: 0xAF80: parsing output script 0
Nov 10 11:53:23 zs kernel: [   30.170912] [drm] nouveau 0000:01:00.0: 0xAF80: parsing output script 0
Nov 10 11:53:23 zs kernel: [   30.170916] [drm] nouveau 0000:01:00.0: 0xA64E: parsing output script 0
Nov 10 11:53:23 zs kernel: [   30.254497] type=1505 audit(1320954803.872:10):  operation="profile_replace" pid=852 name="/sbin/dhclient3"
Nov 10 11:53:23 zs kernel: [   30.255310] type=1505 audit(1320954803.872:11):  operation="profile_replace" pid=852 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Nov 10 11:53:23 zs kernel: [   30.305204] [TTM] Zone  kernel: Available graphics memory: 1027826 kiB.
Nov 10 11:53:23 zs kernel: [   30.305217] [drm] nouveau 0000:01:00.0: 640 MiB VRAM
Nov 10 11:53:23 zs kernel: [   30.327746] [drm] nouveau 0000:01:00.0: 512 MiB GART (aperture)
Nov 10 11:53:23 zs kernel: [   30.329065] mtrr: type mismatch for c0000000,10000000 old: write-back new: write-combining
Nov 10 11:53:23 zs kernel: [   30.329664] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
Nov 10 11:53:23 zs kernel: [   30.334438] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1
Nov 10 11:53:23 zs kernel: [   30.334987] [drm] nouveau 0000:01:00.0: Detected a DAC output
Nov 10 11:53:23 zs kernel: [   30.334990] [drm] nouveau 0000:01:00.0: Detected a TMDS output
Nov 10 11:53:23 zs kernel: [   30.334993] [drm] nouveau 0000:01:00.0: Detected a DAC output
Nov 10 11:53:23 zs kernel: [   30.334995] [drm] nouveau 0000:01:00.0: Detected a TMDS output
Nov 10 11:53:23 zs kernel: [   30.334998] [drm] nouveau 0000:01:00.0: DCB encoder 1 unknown
Nov 10 11:53:23 zs kernel: [   30.335002] [drm] nouveau 0000:01:00.0: Detected a DVI-I connector
Nov 10 11:53:23 zs kernel: [   30.335629] [drm] nouveau 0000:01:00.0: Detected a DVI-I connector
Nov 10 11:53:24 zs kernel: [   30.528555] [drm] nouveau 0000:01:00.0: allocated 1680x1050 fb: 0x40250000, bo ffff880058a91000
Nov 10 11:53:24 zs kernel: [   30.528735] fb0: nouveaufb frame buffer device
Nov 10 11:53:24 zs kernel: [   30.528738] registered panic notifier
Nov 10 11:53:24 zs kernel: [   30.528746] [drm] Initialized nouveau 0.0.15 20090420 for 0000:01:00.0 on minor 0
Nov 10 11:53:24 zs kernel: [   30.540435] e1000e 0000:00:19.0: irq 27 for MSI/MSI-X
Nov 10 11:53:24 zs kernel: [   30.570248] input: HDA Intel Line In at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
Nov 10 11:53:24 zs kernel: [   30.570358] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
...
Nov 10 11:53:25 zs kernel: [   31.668292] nvidia: module license 'NVIDIA' taints kernel.
Nov 10 11:53:25 zs kernel: [   31.668296] Disabling lock debugging due to kernel taint
Nov 10 11:53:25 zs kernel: [   32.317525] NVRM: The NVIDIA probe routine was not called for 1 device(s).
Nov 10 11:53:25 zs kernel: [   32.317529] NVRM: This can occur when a driver such as nouveau, rivafb,
Nov 10 11:53:25 zs kernel: [   32.317531] NVRM: nvidiafb, or rivatv was loaded and obtained ownership of
Nov 10 11:53:25 zs kernel: [   32.317532] NVRM: the NVIDIA device(s).
Nov 10 11:53:25 zs kernel: [   32.317535] NVRM: Try unloading the conflicting kernel module (and/or
Nov 10 11:53:25 zs kernel: [   32.317536] NVRM: reconfigure your kernel without the conflicting
Nov 10 11:53:25 zs kernel: [   32.317537] NVRM: driver(s)), then try loading the NVIDIA kernel module
Nov 10 11:53:25 zs kernel: [   32.317538] NVRM: again.
Nov 10 11:53:25 zs kernel: [   32.317540] NVRM: No NVIDIA graphics adapter probed!
Nov 10 11:53:25 zs kernel: [   32.358823] [drm] nouveau 0000:01:00.0: 0x0F8F: parsing clock script 0
Nov 10 11:53:25 zs kernel: [   32.359228] Console: switching to colour frame buffer device 210x65
Nov 10 11:53:26 zs kernel: [   33.071512] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX
Nov 10 11:53:26 zs kernel: [   33.071822] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Nov 10 11:53:29 zs kernel: [   35.479454] NVRM: The NVIDIA probe routine was not called for 1 device(s).
Nov 10 11:53:29 zs kernel: [   35.479458] NVRM: This can occur when a driver such as nouveau, rivafb,
Nov 10 11:53:29 zs kernel: [   35.479460] NVRM: nvidiafb, or rivatv was loaded and obtained ownership of
Nov 10 11:53:29 zs kernel: [   35.479461] NVRM: the NVIDIA device(s).
Nov 10 11:53:29 zs kernel: [   35.479464] NVRM: Try unloading the conflicting kernel module (and/or
Nov 10 11:53:29 zs kernel: [   35.479465] NVRM: reconfigure your kernel without the conflicting
Nov 10 11:53:29 zs kernel: [   35.479466] NVRM: driver(s)), then try loading the NVIDIA kernel module
Nov 10 11:53:29 zs kernel: [   35.479467] NVRM: again.
Nov 10 11:53:29 zs kernel: [   35.479469] NVRM: No NVIDIA graphics adapter probed!
Nov 10 11:53:30 zs kernel: [   36.436692] NVRM: The NVIDIA probe routine was not called for 1 device(s).
Nov 10 11:53:30 zs kernel: [   36.436697] NVRM: This can occur when a driver such as nouveau, rivafb,
Nov 10 11:53:30 zs kernel: [   36.436698] NVRM: nvidiafb, or rivatv was loaded and obtained ownership of
Nov 10 11:53:30 zs kernel: [   36.436700] NVRM: the NVIDIA device(s).
Nov 10 11:53:30 zs kernel: [   36.436702] NVRM: Try unloading the conflicting kernel module (and/or
Nov 10 11:53:30 zs kernel: [   36.436703] NVRM: reconfigure your kernel without the conflicting
Nov 10 11:53:30 zs kernel: [   36.436704] NVRM: driver(s)), then try loading the NVIDIA kernel module
Nov 10 11:53:30 zs kernel: [   36.436706] NVRM: again.
Nov 10 11:53:30 zs kernel: [   36.436708] NVRM: No NVIDIA graphics adapter probed!
Nov 10 11:53:30 zs kernel: [   37.336097] NVRM: The NVIDIA probe routine was not called for 1 device(s).
Nov 10 11:53:30 zs kernel: [   37.336102] NVRM: This can occur when a driver such as nouveau, rivafb,
Nov 10 11:53:30 zs kernel: [   37.336103] NVRM: nvidiafb, or rivatv was loaded and obtained ownership of
Nov 10 11:53:30 zs kernel: [   37.336104] NVRM: the NVIDIA device(s).
Nov 10 11:53:30 zs kernel: [   37.336107] NVRM: Try unloading the conflicting kernel module (and/or
Nov 10 11:53:30 zs kernel: [   37.336108] NVRM: reconfigure your kernel without the conflicting
Nov 10 11:53:30 zs kernel: [   37.336109] NVRM: driver(s)), then try loading the NVIDIA kernel module
Nov 10 11:53:30 zs kernel: [   37.336110] NVRM: again.
Nov 10 11:53:30 zs kernel: [   37.336113] NVRM: No NVIDIA graphics adapter probed!
Nov 10 11:53:31 zs kernel: [   38.180042] device eth0 entered promiscuous mode
Nov 10 11:53:31 zs kernel: [   38.185035] NVRM: The NVIDIA probe routine was not called for 1 device(s).
Nov 10 11:53:31 zs kernel: [   38.185039] NVRM: This can occur when a driver such as nouveau, rivafb,
Nov 10 11:53:31 zs kernel: [   38.185040] NVRM: nvidiafb, or rivatv was loaded and obtained ownership of
Nov 10 11:53:31 zs kernel: [   38.185041] NVRM: the NVIDIA device(s).
Nov 10 11:53:31 zs kernel: [   38.185044] NVRM: Try unloading the conflicting kernel module (and/or
Nov 10 11:53:31 zs kernel: [   38.185045] NVRM: reconfigure your kernel without the conflicting
Nov 10 11:53:31 zs kernel: [   38.185046] NVRM: driver(s)), then try loading the NVIDIA kernel module
Nov 10 11:53:31 zs kernel: [   38.185047] NVRM: again.

Nov 10 11:53:31 zs kernel: [   38.185049] NVRM: No NVIDIA graphics adapter probed!
Nov 10 11:53:32 zs kernel: [   39.085538] NVRM: The NVIDIA probe routine was not called for 1 device(s).
Nov 10 11:53:32 zs kernel: [   39.085542] NVRM: This can occur when a driver such as nouveau, rivafb,
Nov 10 11:53:32 zs kernel: [   39.085544] NVRM: nvidiafb, or rivatv was loaded and obtained ownership of
Nov 10 11:53:32 zs kernel: [   39.085545] NVRM: the NVIDIA device(s).
Nov 10 11:53:32 zs kernel: [   39.085547] NVRM: Try unloading the conflicting kernel module (and/or
Nov 10 11:53:32 zs kernel: [   39.085549] NVRM: reconfigure your kernel without the conflicting
Nov 10 11:53:32 zs kernel: [   39.085550] NVRM: driver(s)), then try loading the NVIDIA kernel module
Nov 10 11:53:32 zs kernel: [   39.085551] NVRM: again.
Nov 10 11:53:32 zs kernel: [   39.085553] NVRM: No NVIDIA graphics adapter probed!
Nov 10 11:53:33 zs kernel: [   39.892052] NVRM: The NVIDIA probe routine was not called for 1 device(s).
Nov 10 11:53:33 zs kernel: [   39.892056] NVRM: This can occur when a driver such as nouveau, rivafb,
Nov 10 11:53:33 zs kernel: [   39.892058] NVRM: nvidiafb, or rivatv was loaded and obtained ownership of
Nov 10 11:53:33 zs kernel: [   39.892059] NVRM: the NVIDIA device(s).
Nov 10 11:53:33 zs kernel: [   39.892062] NVRM: Try unloading the conflicting kernel module (and/or
Nov 10 11:53:33 zs kernel: [   39.892063] NVRM: reconfigure your kernel without the conflicting
Nov 10 11:53:33 zs kernel: [   39.892064] NVRM: driver(s)), then try loading the NVIDIA kernel module
Nov 10 11:53:33 zs kernel: [   39.892065] NVRM: again.
Nov 10 11:53:33 zs kernel: [   39.892067] NVRM: No NVIDIA graphics adapter probed!
Nov 10 11:53:34 zs kernel: [   40.695893] NVRM: The NVIDIA probe routine was not called for 1 device(s).
Nov 10 11:53:34 zs kernel: [   40.695896] NVRM: This can occur when a driver such as nouveau, rivafb,
Nov 10 11:53:34 zs kernel: [   40.695898] NVRM: nvidiafb, or rivatv was loaded and obtained ownership of
Nov 10 11:53:34 zs kernel: [   40.695899] NVRM: the NVIDIA device(s).
Nov 10 11:53:34 zs kernel: [   40.695902] NVRM: Try unloading the conflicting kernel module (and/or
Nov 10 11:53:34 zs kernel: [   40.695903] NVRM: reconfigure your kernel without the conflicting
Nov 10 11:53:34 zs kernel: [   40.695904] NVRM: driver(s)), then try loading the NVIDIA kernel module
Nov 10 11:53:34 zs kernel: [   40.695905] NVRM: again.
Nov 10 11:53:34 zs kernel: [   40.695907] NVRM: No NVIDIA graphics adapter probed!
...
```

I tried uninstalling xserver-xorg-video-nouveau (and hence xserver-xorg-video-all), but that didn't do anything.

Here's all I have left installed:

```
$ dpkg -l | grep nvidia
ii  nvidia-173-modaliases                                                        173.14.22-0ubuntu11                             Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-96-modaliases                                                         96.43.17-0ubuntu1.1                             Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-common                                                                0.2.23                                          Find obsolete NVIDIA drivers
ii  nvidia-current-modaliases                                                    195.36.24-0ubuntu1~10.04.1                      Modaliases for the NVIDIA binary X.Org driver

$ aptitude search nouveau
i   libdrm-nouveau1                 - Userspace interface to nouveau-specific ke
p   libdrm-nouveau1-dbg             - Userspace interface to nouveau-specific ke
p   nouveau-firmware                - Firmware for nVidia graphics cards        
p   xserver-xorg-video-nouveau      - X.Org X server -- Nouveau display driver (
```

Last bit of info on drivers:

```
$ lspci -v
01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)
        Subsystem: nVidia Corporation Device 0421
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at de000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at dc000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at dc80 [size=128]
        Expansion ROM at dfe00000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: nouveau
        Kernel modules: nvidia, nvidiafb, nouveau

$ lsmod | egrep 'nouveau|nvidia'
nouveau               515227  3 
ttm                    61039  1 nouveau
drm_kms_helper         30742  1 nouveau
drm                   200288  3 nouveau,ttm,drm_kms_helper
i2c_algo_bit            6024  1 nouveau
```

Anyone?

---

### Post by vikrant82 on 2011-11-10
Since I am also new to NVIDIA stuff (on a new laptop), here's what I did to get me going.

I got rid of all these nouveau stuff and ran the installer downloaded from NVIDIA website. This works all the time. Though I have to do this everytime I upgrade my Kernel.

Stop your X, CTRL ALT F1, sudo /etc/init.d/gdm stop or kdm etc (or boot into recovery mode)

and run the installer sudo ./NVIDIA_Watever_you_Download.run

The installer should blacklist any nouveau drivers from loading up. Say yes to most of prompts in the installer, let it re-write your xorg.conf etc..

---

### Post by yang on 2011-11-10
Issue resolved:

[http://askubuntu.com/questions/77801/help-my-nvidia-drivers-are-completely-broken/77844#77844](http://askubuntu.com/questions/77801/help-my-nvidia-drivers-are-completely-broken/77844#77844)

---

### Post by vikrant82 on 2011-11-10
Yup, as you noticed, getting nouveau blacklisted and not loaded while you install the new driver is the key.

---

### Post by LinuxFan999 on 2011-11-10
Please mark your thread as [solved].

---

### Post by halw on 2011-11-11
> **vikrant82 said:**
> Yup, as you noticed, getting nouveau blacklisted and not loaded while you install the new driver is the key.

How do you blacklist nouveau?

I'm having one hell of a time with Kubuntu 11.10 and a nvidia geforce fx go5200 video card on my Dell Inpiron 5150 laptop.

---

### Post by northd_tech on 2011-11-11
> **halw said:**
> How do you blacklist nouveau?

I'm having one hell of a time with Kubuntu 11.10 and a nvidia geforce fx go5200 video card on my Dell Inpiron 5150 laptop.

Can you post the output of the 3 following terminal commands here on this thread?

```
lsmod | egrep 'nv|nou'

egrep 'nvid|nouv' /etc/modprobe.d/black*.*

ls /etc/modprobe.d/

```

---

### Post by halw on 2011-11-11
> **northd_tech said:**
> Can you post the output of the 3 following terminal commands here on this thread?

```
lsmod | egrep 'nv|nou'

egrep 'nvid|nouv' /etc/modprobe.d/black*.*

ls /etc/modprobe.d/

```
Wish I could but after loading nvidia drivers the display was so borked that I installed Ubuntu 10.4 to see if things were going to work and they do.

Would still like to give Kubuntu 11.10 a go though. One thing about 10.4 is that it uses the 173.14.22 version of the nvidia driver.

---

### Post by beew on 2011-11-11
You could have gotten the 285.05 by just adding this ppa,[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates") and upgrade with Synaptic (provided your previous version is not installed manually from Nvidia).  I have been using it with Maverick and Natty for quite a while. There is no need to download from Nvidia and then reinstall your driver every time there is a kernel update. There is no advantage in installing manually from Nvidia as far as I can tell,--you can even get the latest beta driver from the xorg-edgers ppa if you want absolute bleeding edge though that may be risky for obvious reasons,-- but you run considerably more risk in breaking your system and not to mention the hassles of having to reinstall whenever there is a kernel upgrade.

Also since Ubuntu10.10 there is no need to remove the nouveau stuffs, if the Nvidia driver is present it will be loaded automatically.

---

### Post by Cardale on 2012-05-18
Simply installing the PPA doesn't work.

If you are getting an API mismatch as of writing this post those packages don't detect manually installed versions of Nvidia drivers or any left overs from an incorrect removal.

The only way to correct a mismatch is to manually install a Nvidia driver which actually detects the old version or old kernel module files and then uninstall it.  If your goal is to use Ubuntu's nvidia-current package or x-swat.

If you want to use the Nvidia drivers from their website just install it and your done.

It is pretty simple to do simple 

terminal
```
telinit 3; sudo service lightdm stop
```

Then just 
```
chmod +x
```
The nvidia .run file and run it

something like
```
sudo ./NVIDIA-YOUR-DRIVER-VERSION
```

which is probably in your downloads folder.

---

