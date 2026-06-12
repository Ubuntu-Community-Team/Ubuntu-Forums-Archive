---
title: "NVIDIA GPU stooped being detected: 20.04 Focal Fossa"
date: 2020-05-25
forum: Hardware
---

### Post by galprasmarco on 2020-05-25
Hi. I installed my new Asus gaming laptop with ubuntu 18.04 and everything was fine. Later I upgraded to ubuntu 20.04, after a few days, ubuntu stopped to recognize my NVIDIA card. Now I am working with the Intel integrated Card. I have tried many solutions like:

1) Install/Reinstall several times different versions of the nvidia drivers.
2) Install nouveau drivers to see if the card was recognized.
3) Install different version of the linux kernel. from the 5.3 to the 5.6 
4) Enable/Disable app armor
5) Upgrade the BIOS to the latest version

The card is detected when I grab an arch linux live CD and I login into the live mode. It gives me the card in the lspci command, so this is not a HARDWARE problem. However ubuntu does not recognize the card. I am using ubuntu 20.04 gnome,  updated to the latest release. The laptop is not using Secure Boot:

Output of lspci command:
```

00:00.0 Host bridge: Intel Corporation 8th Gen Core 4-core Processor Host Bridge/DRAM Registers [Coffee Lake H] (rev 0d)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16) (rev 0d)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 630 (Mobile) (rev 02)
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 0d)
00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th/8th Gen Core Processor Gaussian Mixture Model
00:12.0 Signal processing controller: Intel Corporation Cannon Lake PCH Thermal Controller (rev 10)
00:14.0 USB controller: Intel Corporation Cannon Lake PCH USB 3.1 xHCI Host Controller (rev 10)
00:14.2 RAM memory: Intel Corporation Cannon Lake PCH Shared SRAM (rev 10)
00:14.3 Network controller: Intel Corporation Wireless-AC 9560 [Jefferson Peak] (rev 10)
00:16.0 Communication controller: Intel Corporation Cannon Lake PCH HECI Controller (rev 10)
00:17.0 SATA controller: Intel Corporation Cannon Lake Mobile PCH SATA AHCI Controller (rev 10)
00:1d.0 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #9 (rev f0)
00:1d.4 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #13 (rev f0)
00:1e.0 Communication controller: Intel Corporation Cannon Lake PCH Serial IO UART Host Controller (rev 10)
00:1f.0 ISA bridge: Intel Corporation HM470 Chipset LPC/eSPI Controller (rev 10)
00:1f.3 Audio device: Intel Corporation Cannon Lake PCH cAVS (rev 10)
00:1f.4 SMBus: Intel Corporation Cannon Lake PCH SMBus Controller (rev 10)
00:1f.5 Serial bus controller [0c80]: Intel Corporation Cannon Lake PCH SPI Controller (rev 10)
02:00.0 Non-Volatile memory controller: Micron Technology Inc Device 5410 (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)

```
There It should be an NVIDIA GTX listed, but is not. Any idea?

---

### Post by TheFu on 2020-05-26
Boot from a "try ubuntu" flash drive and see if the hardware is seen.
Normally, I'd say to re-seat the card.  Pull it out and re-insert it into the slot. On a laptop, it is probably soldered in place.
GPUs do fail from time to time or may overheat. Have you ensured the laptop is clean on the inside?  All dust removed from everything?  Overheating might cause the GPU to be disabled.

But it could just be fried, unfortunately.

After every new kernel, I have to reinstall the nvidia drivers to get them re-integrated. For my 16.04 system and 1030 card, that means:
```
sudo apt install --reinstall  nvidia-430 nvidia-430-dev
```
then rebooting.  It is a pain.  I'd always assumed it was due to my use of CustomEDID features for the card. In theory, DKMS should automatically fix it. In theory.

---

### Post by nasedil-genio on 2020-05-26
I have the same problem. Worked in 18.04 before reinstalling to 20.04, disappeared after installing 20.04.  And also working in liveCD 20.04.  I'm using ubuntu studio.

---

### Post by galprasmarco on 2020-06-05
Yes I have checked the laptop ins clean inside. Also the Gpu cannot be removed and it is detected in another OS. The problems is that it is not even detected, so it is no use to install the drivers.

---

### Post by TheFu on 2020-06-05
What does **sudo lshw -C video** show?
Should look something like this:
```
$ sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: GP108 [**GeForce GT 1030**]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: **driver=nvidia** latency=0
       resources: irq:85 memory:f5000000-f5ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:c0000-dffff
```
That shows up when the drivers are loaded for the GPU.
On another machine here, that command shows nothing, but it has an old GeForce GT 430. The machine is on, but not running X11. No GUI.  

But lspci sees it:
```
$ lspci -vk |perl -lne 'print if /VGA/ .. /^[\w]*$/'
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [**GeForce GT 430**] (rev ff) (prog-if ff)
        !!! Unknown header type 7f
        Kernel driver in use: **nvidia**
        Kernel modules: nvidiafb, nouveau, nvidia_384_drm, nvidia_384

```
Interesting.

I'm back to the "reinstall the nvidia drivers" suggestion.  After every new kernel, that may be necessary for your machine.

---

### Post by TheFu on 2020-08-04
Be very careful pulling entire OSes from unknown/untrusted sources, just like we need to be cautious about installing any software from unknown/untrusted sources.  Everything in Canonical's repos is vetted and pulled from known, cryptographically-signed, sources.  It takes years of effort before software will be included.

The files there may be 100% fine, great, do exactly what they claim AND not include any extra, unwanted, bits.  We don't know. If you can't check that for yourself, I'd skip it.

There are known nvidia issues in the 20.04 release notes. Did you see those and follow the recommendations?  I'm out of other ideas. Sorry.

---

### Post by mastablasta on 2020-08-04
Worrying issue.

> **galprasmarco said:**
> 
1) Install/Reinstall several times different versions of the nvidia drivers.


purged and then install? or just reinstall?

---

