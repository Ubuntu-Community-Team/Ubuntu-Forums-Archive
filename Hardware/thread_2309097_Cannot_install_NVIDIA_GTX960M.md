---
title: "Cannot install NVIDIA GTX960M"
date: 2016-01-07
forum: Hardware
---

### Post by pkoukoulis-r on 2016-01-07
I keep getting the following message when running the nvidia installation
[FONT=courier new]ERROR: You appear to be running an X server: please exit X before installing.[/FONT]

I followed the following steps prior to attempting the installation, all in a terminal window.
[FONT=courier new]sudo apt-get update
sudo apt-get install build-essential 
sudo apt-get install linux-source 
sudo apt-get  install linux-headers-generic 
sudo vi gedit [COLOR=#000000]/etc/default/grub[/COLOR]
[/FONT]modified
[FONT=courier new]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"[/FONT]
to
[FONT=courier new]GRUB_CMDLINE_LINUX_DEFAULT="nouveau.blacklist=1 quiet splash nomodset"[/FONT]

[FONT=courier new]echo options nouveau modeset=0 | sudo tee -a /etc/modprob.d/nouveau-kms.conf[/FONT]

Created file [FONT=courier new]/etc/modprobe.d/blacklist-nouveau.conf[/FONT]
[FONT=courier new]blacklist nouveau
blacklist lbm-nouveau
options nouveau modeset=0
alias nouveau off
alias lbm-nouveau off
[/FONT]
then I ran the following:
[FONT=courier new]sudo update-initramfs -u
[FONT=arial]rebooted[/FONT]

sudo service lightdm stop
[FONT=arial]**I verified that the lightdm service had stopped:**
[FONT=courier new]tail -n 1 Xorg.0.log[/FONT]
[/FONT][ 5.483[ (II) Server terminated successfully (0). Closing log file

sudo init 3
cd ~/Downloads
sudo ./NVIDIA-Linux-x86_64-352.55.run
**error message appears**

sudo inxi -SGx
System:    Host: 12laptop Kernel: 4.2.0-22-generic x86_64 (64 bit gcc: 5.2.1)
           Desktop: N/A Distro: Ubuntu 15.10 wily
Graphics:  Card-1: Intel 4th Gen Core Processor Integrated Graphics Controller bus-ID: 00:02.0
           Card-2: NVIDIA GM107M [GeForce GTX 960M] bus-ID: 01:00.0
           Display Server: X.org 1.17.2 drivers: nouveau,intel (unloaded: nvidia,fbdev,vesa)
           tty size: 80x24 Advanced Data: N/A for root out of X


$ lspci -vnn | grep VGA -A 12
00:02.0 VGA compatible controller [0300]: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller [8086:0416] (rev 06) (prog-if 00 [VGA controller])
    Subsystem: CLEVO/KAPOK Computer Device [1558:2316]
    Flags: bus master, fast devsel, latency 0, IRQ 31
    Memory at f7400000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915


Any help would be appreciated.

[FONT=arial][/FONT]

[/FONT][LEFT][COLOR=#5C5C5C][FONT=Ubuntu]
[/FONT][/COLOR][/LEFT]

---

### Post by gordintoronto on 2016-01-08
It's simpler than you think.

I don't know where you got the idea that you had to compile the driver, but it's not true. What you need to do is install an "additional driver" from within the Ubuntu infrastructure. I use Xubuntu, so I'm not positive where that is, but I think it's in Software Centre.

---

