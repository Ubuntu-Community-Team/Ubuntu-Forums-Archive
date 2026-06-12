---
title: "Disappearing Device"
date: 2011-07-08
forum: Hardware
---

### Post by Ri.Kenji on 2011-07-08
I was about to play a video on my computer when I realized there was no sound. I checked the volume and the connections just to be sure. And to prove to myself it wasn't a hardware problem, I boot the same computer into a live CD and I was able to get audio.

The sound preferences window (screenshots attached) shows one less audio device where there should be two. (The other one is my USB microphone.) I'm guessing Ubuntu somehow "forgot" my device.

Has anyone had this problem before? And is there any way to force Ubuntu to detect "new" hardware (like the live CD does)?

Output of **lshw**:
```
H/W path      Device      Class       Description
=================================================
                          system      To Be Filled By O.E.M. (To Be Filled By O.E.M.)
/0                        bus         To be filled by O.E.M.
/0/0                      memory      64KiB BIOS
/0/4                      processor   Intel(R) Atom(TM) CPU  330   @ 1.60GHz
/0/4/5                    memory      48KiB L1 cache
/0/4/6                    memory      1MiB L2 cache
/0/24                     memory      4GiB System Memory
/0/24/0                   memory      2GiB DIMM SDRAM Synchronous 2048 MHz (0.5 ns)
/0/24/1                   memory      [empty]
/0/24/2                   memory      2GiB DIMM SDRAM Synchronous 2048 MHz (0.5 ns)
/0/24/3                   memory      [empty]
/0/100                    bridge      MCP79 Host Bridge
/0/100/0.1                memory      RAM memory
/0/100/3                  bridge      MCP79 LPC Bridge
/0/100/3.1                memory      RAM memory
/0/100/3.2                bus         MCP79 SMBus
/0/100/3.3                memory      RAM memory
/0/100/3.5                processor   MCP79 Co-processor
/0/100/4                  bus         MCP79 OHCI USB 1.1 Controller
/0/100/4.1                bus         MCP79 EHCI USB 2.0 Controller
/0/100/6                  bus         MCP79 OHCI USB 1.1 Controller
/0/100/6.1                bus         MCP79 EHCI USB 2.0 Controller
/0/100/8                  multimedia  MCP79 High Definition Audio
/0/100/9                  bridge      MCP79 PCI Bridge
/0/100/a      eth0        network     MCP79 Ethernet
/0/100/b      scsi0       storage     MCP79 SATA Controller
/0/100/b/0    /dev/sda    disk        320GB WDC WD3200BEKT-0
/0/100/b/0/1  /dev/sda1   volume      512MiB EXT4 volume
/0/100/b/0/2  /dev/sda2   volume      4095MiB Linux Swap partition
/0/100/b/0/3  /dev/sda3   volume      32GiB EXT4 volume
/0/100/b/0/4  /dev/sda4   volume      261GiB Data partition
/0/100/b/1    /dev/cdrom  disk        BD-CMB UJ-120
/0/100/b/1/0  /dev/cdrom  disk        
/0/100/c                  bridge      MCP79 PCI Express Bridge
/0/100/10                 bridge      MCP79 PCI Express Bridge
/0/100/10/0               display     ION VGA
/0/100/15                 bridge      MCP79 PCI Express Bridge
/0/100/15/0   wlan0       network     AR928X Wireless Network Adapter (PCI-Express)
/0/100/16                 bridge      MCP79 PCI Express Bridge
/0/100/17                 bridge      MCP79 PCI Express Bridge
/0/100/18                 bridge      MCP79 PCI Express Bridge
```
The item of interest is /0/100/8, multimedia, MCP79 High Definition Audio.

---

