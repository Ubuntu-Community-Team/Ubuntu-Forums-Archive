---
title: "SD CARD READER NOT RECOGNIZED (It mounted fine in Windows)"
date: 2015-08-30
forum: Hardware
---

### Post by popckorn on 2015-08-30
Hello Wizards!!

I  am new to Linux, and I am loving it. Way better than Windows, but still  there are some issues to tune, so please let me tell you my  predicament:

Linux is not reading the SD cards I plug into the laptop. Windows did read them.

My Laptop Model:  Samsung Satellite E45-B4200

OS: Linux Mint Cinnamon 17.2  64-bit


```
redbeard@Leif-Ericson ~ $ inxi -Fxz
System:    Host: Leif-Ericson Kernel: 3.16.0-38-generic x86_64 (64 bit, gcc: 4.8.2) 
           Desktop: Cinnamon 2.6.13  Distro: Linux Mint 17.2 Rafaela
Machine:   System: TOSHIBA product: Satellite E45-B version: PSPN2U-003003
           Mobo: TOSHIBA model: CA10SU Bios: TOSHIBA version: 1.40 date: 12/05/2014
CPU:        Dual core Intel Core i5-4210U CPU (-HT-MCP-) cache: 3072 KB flags: (lm  nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 9577.88 
           Clock Speeds: 1: 2247.375 MHz 2: 2017.500 MHz 3: 1188.093 MHz 4: 1708.875 MHz
Graphics:  Card: Intel Haswell-ULT Integrated Graphics Controller bus-ID: 00:02.0 
           X.Org: 1.15.1 drivers: intel (unloaded: fbdev,vesa) Resolution: 1920x1080@60.0hz 
           GLX Renderer: Mesa DRI Intel Haswell Mobile GLX Version: 3.0 Mesa 10.1.3 Direct Rendering: Yes
Audio:     Card-1: Intel Lynx Point-LP HD Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0 
           Card-2: Intel Haswell-ULT HD Audio Controller driver: snd_hda_intel bus-ID: 00:03.0 
           Sound: Advanced Linux Sound Architecture ver: k3.16.0-38-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
           driver: r8169 ver: 2.3LK-NAPI port: e000 bus-ID: 03:00.0
           IF: eth0 state: down mac: <filter>
           Card-2: Intel Wireless 3160 driver: iwlwifi ver: in-tree: bus-ID: 02:00.0
           IF: wlan0 state: up mac: <filter>
Drives:    HDD Total Size: 500.1GB (5.8% used) 1: id: /dev/sda model: WDC_WD5000BPKX size: 500.1GB 
Partition: ID: / size: 446G used: 28G (7%) fs: ext4 ID: /boot size: 237M used: 50M (23%) fs: ext2 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 47.0C mobo: N/A 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 185 Uptime: 18 min Memory: 1038.5/11928.4MB Runlevel: 2 Gcc sys: 4.8.4 
           Client: Shell (bash 4.3.11) inxi: 1.9.17 
 
```

I am wondering whether there is a repository where to find my driver. 


I asked a friend who is also a wizard and taught me I am looking to compile a MODULE not a DRIVER, and that I should try LSPCI. 

This is my LSPCI output:
```
lspci
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 1 (rev e4)
00:1c.2 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 4 (rev e4)
00:1c.5 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 6 (rev e4)
00:1d.0 USB controller: Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
02:00.0 Network controller: Intel Corporation Wireless 3160 (rev 83)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
04:00.0 Unassigned class [ff00]: Device 1aea:6601

```

And this is the output for lsusb with nothing plugged to the USB/SD ports:
```
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 04f2:b446 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 8087:07dc Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I suspect the Chicony Electronics Co., Ltd is the one 

Thank you for your kind patience, I might be making naive assumptions or unable to see obvious things. 

Thank you all!

---

### Post by Vladlenin5000 on 2015-08-30
No. Chicony is your webcam.

Your SD card reader is indeed in the PCI bus like your friend suggested:
```
04:00.0 Unassigned class [ff00]: Device [COLOR=#ff0000]1aea:6601[/COLOR]
```

From there we know it's based on the **Alcor Micro AU6601** chip for which there's a driver but it isn't in the kernel. The good news is you don't need to compile a module because someone else already did it.

```
sudo add-apt-repository ppa:iacobs/au6601
sudo apt-get update
sudo apt-get install au6601
```

---

### Post by popckorn on 2015-08-31
Wow! Much obliged Vladlenin5000! 

I really appreciate how this community works together towards pushing the boundaries of free and open-source software in the most esoteric ways, but it also has time to spoon-feed us newbies. 

I am not getting tired of recommending Ubunbtu to friends who are NOT ok with the blatant key-logging of Windows 10.  

Thank you very much to all!

---

### Post by popckorn on 2015-08-31
Ok I did install the driver but it still does not read cards.

This is my new LSPCI:
```

lspci
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 1 (rev e4)
00:1c.2 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 4 (rev e4)
00:1c.5 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 6 (rev e4)
00:1d.0 USB controller: Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
02:00.0 Network controller: Intel Corporation Wireless 3160 (rev 83)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
04:00.0 Unassigned class [ff00]: Device 1aea:6601

```

So apparently it did not install the kernel. 

Should I retry or is the compilation not compatible with my os?

Thank you.

---

### Post by srliner on 2015-09-07
I have exactly the same problem with my Toshiba E45t. The Alcor Micro PCI SD card reader works fine in Windows (dual boot) but not Ubuntu 14.04.3 LTS. I added the repository and installed the package (sudo apt-get install au6601-dkms  not sudo apt-get install au6601), but I still cannot use the card reader.  Any other ideas?

EDIT: Shortly after posting the above, I ran lsblk and found the card at /dev/mmcblk0p1 but it was not mounted. I then ran "sudo mount /dev/mmcblk0p1 /media/sdcard".  I am now able to access the card but do not want to manually mount each time. Do I have to modify fstab or is there another way to get the card to mount when inserted in the reader?

---

