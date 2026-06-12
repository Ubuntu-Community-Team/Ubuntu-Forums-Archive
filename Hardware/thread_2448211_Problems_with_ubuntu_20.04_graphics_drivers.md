---
title: "Problems with ubuntu 20.04 graphics drivers"
date: 2020-08-04
forum: Hardware
---

### Post by yanunim95 on 2020-08-04
Hello. 

I have troubles with ubuntu 20.04.
After some time my displays are freezing.
I cannot do anything.
SysRq+REISUB restarts computer without problems
Login via ssh on "hanged" computer works.
And computer is manageable.

But Xorg.log has no error entries.
**UPD:** 
I'm not able to restart lightdm from ssh. 
After submitting:
```
sudo systemctl restart lightdm 
```
I'm not getting bash prompt free.
If i try to reboot with sudo reboot it needs more that 5 minutes to restart.
Before reboot via ssh i see black screen messages that system is trying to stop chrome, cairo dock + some other opened apps.

I have also tried to switch to drivers from oibaf ppa, but without success.  

How can i debug this and repair my X session?

Specs:
[LIST]
[*]Ubuntu 20.04 installed from mini.iso + ubuntu-mate-desktop with compiz and Cairo dock
[*]Ryzen 7 1700
[*]64GB Ram(2133Mhz)
[*]Samsung 970 Pro
[*]Asus TUF B450M-Pro
[*]Radeon 5500XT with attached 4k Display via Display port
[*]Radeon R7 250 with attached older 19 Display via DVI
[/LIST]

---

### Post by CatKiller on 2020-08-04
That doesn't particularly sound like a graphics driver issue to me.

If I were to hazard a guess, that sounds much more like out of RAM.

---

### Post by yanunim95 on 2020-08-04
> **CatKiller said:**
> That doesn't particularly sound like a graphics driver issue to me.

If I were to hazard a guess, that sounds much more like out of RAM.


I think you are wrong.
I was testing XMP profile, however it was not really working. 
So my RAM is configured to use default DDR4 speed 2133MHz.

Also, if it was RAM issue, i would not be able to login of computer with ssh from laptop.
This hangs i got within different RAM consumption: from 5GB up to 37GB used.

Also it looks more like graphics issue, cause i'm not able to restart lightdm from ssh.

---

### Post by P-I H on 2020-08-04
My configuration is quite similar and I had problems with Ubuntu  20.04 freezing sometimes when I closed Chrome.
My solution was to upgrade the kernel to 5.7.
```
p-i@asus-b450-f:~$ inxi -Fz
System:    Kernel: 5.7.7-050707-generic x86_64 bits: 64 Desktop: Gnome 3.36.4 Distro: Ubuntu 20.04.1 LTS (Focal Fossa) 
Machine:   Type: Desktop Mobo: ASUSTeK model: ROG STRIX B450-F GAMING v: Rev 1.xx serial: <filter> UEFI: American Megatrends 
           v: 2704 date: 08/23/2019 
CPU:       Topology: 8-Core model: AMD Ryzen 7 1700 bits: 64 type: MT MCP L2 cache: 4096 KiB 
           Speed: 1372 MHz min/max: 1550/3750 MHz Core speeds (MHz): 1: 1368 2: 1362 3: 1414 4: 1357 5: 1374 6: 1371 7: 1375 
           8: 1375 9: 1424 10: 1361 11: 1373 12: 1375 13: 1373 14: 1374 15: 1356 16: 1355 
Graphics:  Device-1: Advanced Micro Devices [AMD/ATI] Navi 10 [Radeon RX 5600 OEM/5600 XT / 5700/5700 XT] driver: amdgpu 
           v: kernel 
           Display: x11 server: X.Org 1.20.8 driver: amdgpu resolution: 2560x1440~60Hz 
           OpenGL: renderer: AMD Radeon RX 5700 (NAVI10 DRM 3.37.0 5.7.7-050707-generic LLVM 10.0.0) v: 4.6 Mesa 20.0.8 
Audio:     Device-1: Advanced Micro Devices [AMD/ATI] Navi 10 HDMI Audio driver: snd_hda_intel 
           Device-2: Advanced Micro Devices [AMD] Family 17h HD Audio driver: snd_hda_intel 
           Device-3: Logitech Webcam C250 type: USB driver: snd-usb-audio,uvcvideo 
           Sound Server: ALSA v: k5.7.7-050707-generic 
Network:   Device-1: Intel I211 Gigabit Network driver: igb 
           IF: enp4s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:    Local Storage: total: 698.65 GiB used: 75.60 GiB (10.8%) 
           ID-1: /dev/nvme0n1 vendor: Kingston model: SA1000M8480G size: 447.13 GiB 
           ID-2: /dev/nvme1n1 vendor: Kingston model: SA2000M8500G size: 465.76 GiB 
           ID-3: /dev/nvme2n1 vendor: Samsung model: SSD 960 EVO 250GB size: 232.89 GiB 
           ID-4: /dev/sda vendor: Samsung model: SSD 850 EVO 250GB size: 232.89 GiB 
Partition: ID-1: / size: 456.96 GiB used: 75.55 GiB (16.5%) fs: ext4 dev: /dev/nvme1n1p2 
Sensors:   System Temperatures: cpu: 35.6 C mobo: 38.0 C gpu: amdgpu temp: 48 C 
           Fan Speeds (RPM): cpu: 597 case-1: 913 case-2: 835 case-3: 516 gpu: amdgpu fan: 0 
Info:      Processes: 373 Uptime: 21h 33m Memory: 15.56 GiB used: 2.01 GiB (12.9%) Shell: bash inxi: 3.0.38 
p-i@asus-b450-f:~$ 

```

---

### Post by yanunim95 on 2020-08-05
I have not found kernel 5.7 in repos.
Do you have compiled kernel from source?

---

### Post by P-I H on 2020-08-05
These are my instructions to change kernel

Fetch from [http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)
Select the wanted kernel
Select amd64/
Fetch these kernel components
linux-headers-------all.deb
linux-headers----generic----amd64.deb
linux-image------amd64.deb
linux-modules-------amd64.deb
Make a new directory in home.
Copy the fetched kernel components to the new directory
Open a terminal and run the commands
```
cd "new directory"
sudo dpkg -i *.deb
```
and reboot.

Updates with Software Updater works as normal, but the kernel isn't updated. I upgrade the kernel with this procedure now and then. This install is now at kernel 5.7.7. The latest is 5.7.13 from 2020-08-05.
In "Changes" the changes are listed and in kernel 5.7.13, there are 2 changes related to amdgpu.

---

### Post by yanunim95 on 2020-08-07
I have noticed that ubuntu got 20.04.1 update.
With kernel-oem-5.6 update.
I will test it and report later.

---

### Post by yanunim95 on 2020-08-10
Switch to 5.6 kernel has not helped.
I still getting freezes.
I also got instant reboot.
How can i debug it to get more logs and pass this error to ubuntu Bug tracker?

---

### Post by backspin on 2020-08-10
If you are still thinking this is graphics related, AMD just released new drivers for the 5500XT -  [https://www.amd.com/en/support/graphics/amd-radeon-5500-series/amd-radeon-rx-5500-series/amd-radeon-rx-5500-xt](https://www.amd.com/en/support/graphics/amd-radeon-5500-series/amd-radeon-rx-5500-series/amd-radeon-rx-5500-xt)

I do not recommend the pro driver as a gamer they suck.  Just install using this command -  amdgpu-install -y --opencl=pal

---

