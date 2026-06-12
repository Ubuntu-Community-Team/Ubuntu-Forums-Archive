---
title: "Driver issues on lenovo 9i. Nothing works."
date: 2021-01-08
forum: Hardware
---

### Post by theogiroud on 2021-01-08
I installed ubuntu 18.04 LTS on new lenovo 9i yoga. Only the keyboard worked initially. Audio card and mic showed but were not working.

Adding few lines to /etc/modprobe.d/alsa-base/.conf fixed audio and mic.

The brightness controls are not working. Adding acpi_backlight=vendor to grub is the only option that gets the brightness bar visible but it still does not work. In case it helps, the grub setting also populates /sys/class/backlight/ with a folder "ideapad", which is not the case for any other argument like video, native, video0, or none.

The touchpad is not working. xserver-xorg-input-synaptics is installed. Grub has i8042.reset but it did not work. I am using an external mouse. 

The touchscreen does not work either. I have no expectations from fingerprint since it is not on the supported devices list.

This is my lspci output:
00:00.0 Host bridge: Intel Corporation Device 9a14 (rev 01)
00:02.0 VGA compatible controller: Intel Corporation Device 9a49 (rev 01)
00:04.0 Signal processing controller: Intel Corporation Device 9a03 (rev 01)
00:06.0 PCI bridge: Intel Corporation Device 9a09 (rev 01)
00:07.0 PCI bridge: Intel Corporation Device 9a23 (rev 01)
00:07.1 PCI bridge: Intel Corporation Device 9a25 (rev 01)
00:07.2 PCI bridge: Intel Corporation Device 9a27 (rev 01)
00:07.3 PCI bridge: Intel Corporation Device 9a29 (rev 01)
00:0a.0 Signal processing controller: Intel Corporation Device 9a0d (rev 01)
00:0d.0 USB controller: Intel Corporation Device 9a13 (rev 01)
00:0d.2 USB controller: Intel Corporation Device 9a1b (rev 01)
00:0d.3 USB controller: Intel Corporation Device 9a1d (rev 01)
00:12.0 Serial controller: Intel Corporation Device a0fc (rev 20)
00:14.0 USB controller: Intel Corporation Device a0ed (rev 20)
00:14.2 RAM memory: Intel Corporation Device a0ef (rev 20)
00:14.3 Network controller: Intel Corporation Device a0f0 (rev 20)
00:15.0 Serial bus controller [0c80]: Intel Corporation Device a0e8 (rev 20)
00:15.1 Serial bus controller [0c80]: Intel Corporation Device a0e9 (rev 20)
00:15.2 Serial bus controller [0c80]: Intel Corporation Device a0ea (rev 20)
00:15.3 Serial bus controller [0c80]: Intel Corporation Device a0eb (rev 20)
00:16.0 Communication controller: Intel Corporation Device a0e0 (rev 20)
00:1f.0 ISA bridge: Intel Corporation Device a082 (rev 20)
00:1f.3 Multimedia audio controller: Intel Corporation Device a0c8 (rev 20)
00:1f.4 SMBus: Intel Corporation Device a0a3 (rev 20)
00:1f.5 Serial bus controller [0c80]: Intel Corporation Device a0a4 (rev 20)
01:00.0 Non-Volatile memory controller: Sandisk Corp Device 5006


I really looked forward to using this laptop since it has great specs but I dont know if the new tech is supported by ubuntu yet. 

Suggestions to get anything working are very welcome.  Thanks a lot!

---

### Post by yancek on 2021-01-09
If this hardware is very new, I would not expect 18.04 to have the necessary software in a default install as it is nearly 3 years old so have you run apt update &&  apt upgrade on it?  You might have better luck with 20.04.

---

### Post by theogiroud on 2021-01-09
Thanks yancek. I did run update and upgrade.
Actually, I installed 20.04 first but ran into the same issues which is why I though 18.04 might be better since there is more record for it. If nothing, I might upgrade to 20.04 again.

---

### Post by #&amp;thj^% on 2021-01-09
not sure if this will help you but, is " input-wacom" "xf86-input-wacom" "libwacom" installed?
```
modinfo wacom | grep version
version:        v2.00
srcversion:     261A641E57A3D8C5DD1ED29
```
X1 Carbon 7th Gen:
```
System:
  Host: archme Kernel: 5.10.5.a-2-hardened x86_64 bits: 64 
  Desktop: MATE 1.24.1 Distro: Arch Linux 
Machine:
  Type: Laptop System: LENOVO product: 20R10010US v: ThinkPad X1 Carbon 7th 
  serial: <superuser required> 
  Mobo: LENOVO model: 20R10010US v: SDK0J40697 WIN 
  serial: <superuser required> UEFI: LENOVO v: N2QET36W(1.30 ) 
  date: 11/09/2020 
Battery:
  ID-1: BAT0 charge: 49.5 Wh condition: 52.0/51.0 Wh (102%) 
CPU:
  Info: Quad Core model: Intel Core i5-10210U bits: 64 type: MT MCP 
  L2 cache: 6 MiB 
  Speed: 800 MHz min/max: 400/4200 MHz Core speeds (MHz): 1: 800 2: 800 
  3: 800 4: 799 5: 800 6: 800 7: 800 8: 800 
Graphics:
  Device-1: Intel UHD Graphics driver: i915 v: kernel 
  Device-2: IMC Networks Integrated Camera type: USB driver: uvcvideo 
  Display: x11 server: X.Org 1.20.10 driver: intel s-res: 1920x1080 
  OpenGL: renderer: Mesa Intel UHD Graphics (CML GT2) v: 4.6 Mesa 20.3.2 
Audio:
  Device-1: Intel driver: sof-audio-pci 
  Sound Server: ALSA v: k5.10.5.a-2-hardened 
Network:
  Device-1: Intel Wireless-AC 9462 driver: iwlwifi 
  IF: wlp0s20f3 state: up mac: 74:d8:3e:93:80:4b 
  Device-2: Intel Ethernet I219-V driver: e1000e 
  IF: enp0s31f6 state: down mac: 00:2b:67:2c:ad:fe 
  IF-ID-1: tun0 state: unknown speed: 10 Mbps duplex: full mac: N/A 
Drives:
  Local Storage: total: 406.16 GiB used: 38.09 GiB (9.4%) 
  ID-1: /dev/nvme0n1 vendor: Western Digital 
  model: PC SN730 SDBQNTY-256G-1001 size: 238.47 GiB 
  ID-2: /dev/sda type: USB vendor: Intel model: SSDSC2BW180A3L 
  size: 167.68 GiB 
Partition:
  ID-1:/ size: 225.25 GiB used: 21.71 GiB (9.6%) fs: ext4 
  dev: /dev/nvme0n1p3 
  ID-2: /boot size: 1022 MiB used: 107 MiB (10.5%) fs: vfat 
  dev: /dev/nvme0n1p1 
Swap:
  ID-1: swap-1 type: partition size: 7.62 GiB used: 0 KiB (0.0%) 
  dev: /dev/nvme0n1p2 
Sensors:
  System Temperatures: cpu: 56.0 C mobo: N/A 
  Fan Speeds (RPM): cpu: 0 
Info:
  Processes: 247 Uptime: 2h 32m Memory: 7.45 GiB used: 1.87 GiB (25.1%) 
  Shell: Bash inxi: 3.2.01 


```
Special parameters in grub:
```
GRUB_CMDLINE_LINUX_DEFAULT="loglevel=3 apparmor=1 lsm=lockdown,yama,apparmor ipv
6.disable=1 quiet"

```
I have to admit, it wasn't the easiest install i've done. ;)

---

### Post by theogiroud on 2021-01-09
Thanks 1fallen.
However, adding the grub parameters do not change anything. Using only these parameters, the brightness bar disappears.
Apparently, only acpi_backlight=vendor gets the useless but visible brightness bar.

---

### Post by theogiroud on 2021-01-12
I updated to 20.04 but having the same trouble.

---

### Post by Yellow Pasque on 2021-01-13
Try a newer kernel. You can always boot back to the old one if things go wrong.
```
sudo apt-get install linux-generic-hwe-20.04
```
See if it works any better after running ^that command and rebooting.

---

### Post by theogiroud on 2021-01-13
Things are working! Thanks a lot Yellow Pasque! 

This fixed the  brightness button but there was no control so I changed grub  acpi_backlight to video. Brightness is working! I can now look at the  screen without my eyes hurting.

My touch-pad also works now,  though it lags a bit. The touchscreen is still not detecting my stylus.  But I am happy it works like a normal, non-yoga laptop now.

Thanks a lot!

---

