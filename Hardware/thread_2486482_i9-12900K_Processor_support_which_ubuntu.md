---
title: "i9-12900K Processor support which ubuntu?"
date: 2023-05-02
forum: Hardware
---

### Post by som9591 on 2023-05-02
[FONT=Arial]I have i9-12900K -16 Thread processor. [/FONT]
[FONT=Arial]I have to install "ubuntu-20.04 or 18.04 LTS". Which ubuntu version support this processor? 

[/FONT]
[FONT=Arial]I have 3 SSD: 1st SSD: Windows, 2nd: ubuntu, 3rd: Data storage. [/FONT]
[FONT=Arial]Graphics: NVIDA RTX 3060Ti - 8GB. [/FONT]

---

### Post by Autodave on 2023-05-02
Is there a reason that you cannot use 22.04?  I would definitely use that for such a new processor.  20.04 may wok just fine, too.

---

### Post by aljames2 on 2023-05-02
I have an i5-12500 system.  Both are Alder Lake, same generation released at the same time. No problems with 20.04 for me.  Although, I did do a fresh install of 22.04 since then and no issues.  Not sure I would go 18.04 if you have the choice, support ends this month for 18.04.

---

### Post by som9591 on 2023-05-03
We are installing OpenCV & Deep Learning libraries. I tried on 23.04. But, some packages are giving error. Hence, I thought of 20.04. Is there any official docs or some reference, where I can check, How to install ubuntu 22.04 on dedicated SSD drive. 
Problem-1: 
Ubuntu 20.04 LTS install on SSD drive or 
Ubuntu 18.04 LTS install on SSD drive


Configuration:
1: Processor:  i9-12900K -16 Thread processor. 
2: I have 3 SSD: 1st SSD: Windows,
    2nd SSD: For ubuntu,
	3rd SSD: Data storage. 
3: Graphics: NVIDA RTX 3060Ti - 8GB. 
4: Ubuntu 20.04 LTS installed on SSD drive. But, it is not showing Ethernet or Wi-Fi icon. 


Problem-2: 
I have 500 GB SSD. I have partition this. In 200GB, I have install ubuntu 20.04 LTS.
But, in ubuntu, it is not showing Ethernet or Wi-Fi icon.

---

### Post by TheFu on 2023-05-07
You should be looking at 22.04 for new Ubuntu installations today.  Nobody should be doing a new install with 18.04 anymore. Support ends ... this month.  In fact, most people should already be off 18.04 completely at this point.

Wifi doesn't make sense.  Use wired ethernet.  This is a completely separate problem and deserves a thread just for that.  Start by saying the hardware in the system.  Not vague ideas, but use **lshw** or **lspci** or **inxi** to gather detailed information to be shared.
```
inxi -bz
```
Will show a brief overview of the system and hardware. This includes the specific NIC.  For example:
```
$ inxi -bz
System:
  Kernel: **5.15.0-71-generic** x86_64 bits: 64 Desktop: [B]FVWM 2.6.7
[/B]  Distro: **Ubuntu 20.04.6 LTS** (Focal Fossa) 
Machine:
  Type: Desktop **Mobo: ASUSTeK model: ROG STRIX B450-F GAMING v: Rev 1.xx** 
  serial: <filter> UEFI: American Megatrends v: 5003 date: 02/03/2023 
CPU:
  6-Core: AMD **Ryzen 5 5600G** with Radeon Graphics type: MT MCP speed: 4196 MHz 
  min/max: 1400/4200 MHz 
Graphics:
  Device-1: AMD driver: amdgpu v: kernel 
  Display: server: X.Org 1.20.8 driver: **amdgpu** resolution: **1920x1200~77Hz** 
  OpenGL: renderer: llvmpipe (LLVM 12.0.0 256 bits) v: 4.5 Mesa 21.2.6 
Network:[B]
  Device-1: Intel I211 Gigabit Network driver: igb 
  Device-2: Intel 82575GB Gigabit Network driver: igb 
  Device-3: Intel 82575GB Gigabit Network driver: igb 
  Device-4: Intel 82575GB Gigabit Network driver: igb 
  Device-5: Intel 82575GB Gigabit Network driver: igb [/B]
Drives:
  Local Storage: total: 37.13 TiB used: 19.59 TiB (52.7%) 
Info:
  Processes: 671 Uptime: 4d 17m Memory: 30.72 GiB used: 21.21 GiB (69.0%) 
  Shell: bash inxi: 3.0.38 

```
Lots of good information in that output formatted to be read easily.

---

