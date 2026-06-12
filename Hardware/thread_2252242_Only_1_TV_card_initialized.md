---
title: "Only 1 TV card initialized"
date: 2014-11-10
forum: Hardware
---

### Post by Mike_Brown on 2014-11-10
I have 2 Hauppauge HVR-1600 TV cards. Only 1 of them can be accessed. 

My lspci -v section showing the cards is:
```

03:00.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
    Subsystem: Hauppauge computer works Inc. Device 7400
    Flags: bus master, medium devsel, latency 64, IRQ 16
    Memory at f4000000 (32-bit, non-prefetchable) [size=64M]
    Capabilities: [44] Vital Product Data
    Capabilities: [4c] Power Management version 2
    Kernel driver in use: cx18


03:02.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
    Subsystem: Hauppauge computer works Inc. WinTV HVR-1600
    Flags: bus master, medium devsel, latency 64, IRQ 18
    Memory at f8000000 (32-bit, non-prefetchable) [size=64M]
    Capabilities: [44] Vital Product Data
    Capabilities: [4c] Power Management version 2

```
As you can see, the 1 in the 1st pci slot has 'Kernel driver in use: cx18' and the second does not show a driver in use. 

This is the return from dmesg | grep cx
```

[    8.731923] cx18:  Start initialization, version 1.5.1
[    8.731957] cx18-0: Initializing card 0
[    8.731958] cx18-0: Autodetected Hauppauge card
[    8.735391] cx18-0: cx23418 revision 01010000 (B)
[    8.949625] cx18-0: Autodetected Hauppauge HVR-1600
[    8.949626] cx18-0: Simultaneous Digital and Analog TV capture supported
[    9.189668] cs5345 0-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[    9.381018] cx18-0: Registered device video0 for encoder MPEG (64 x 32.00 kB)
[    9.381020] DVB: registering new adapter (cx18)
[    9.627461] cx18 0000:03:00.0: DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[    9.627566] cx18-0: DVB Frontend registered
[    9.627568] cx18-0: Registered DVB adapter0 for TS (32 x 32.00 kB)
[    9.627620] cx18-0: Registered device video32 for encoder YUV (20 x 101.25 kB)
[    9.627664] cx18-0: Registered device vbi0 for encoder VBI (20 x 51984 bytes)
[    9.627707] cx18-0: Registered device video24 for encoder PCM audio (256 x 4.00 kB)
[    9.627748] cx18-0: Registered device radio0 for encoder radio
[    9.627750] cx18-0: Initialized card: Hauppauge HVR-1600
[    9.627772] cx18-1: Initializing card 1
[    9.627774] cx18-1: Autodetected Hauppauge card
[    9.630943] cx18-1: ioremap failed. Can't get a window into CX23418 memory and register space
[    9.630948] cx18-1: Each capture card with a CX23418 needs 64 MB of vmalloc address space for the window
[    9.630951] cx18-1: Check the output of 'grep Vmalloc /proc/meminfo'
[    9.630953] cx18-1: Use the vmalloc= kernel command line option to set VmallocTotal to a larger value
[    9.630958] cx18-1: Error -12 on initialization
[    9.630963] cx18: probe of 0000:03:02.0 failed with error -12
[    9.630978] cx18:  End initialization
[    9.708326] cx18-alsa: module loading...
[   10.412092] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   10.564968] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   10.571521] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   11.453014] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   11.472650] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)

```

lspci shows each card having 64Mb, but grep cx says that there is insufficient memory allocated. I am new enough to Ubuntu that I am not sure of how to make the change that grep cx says needs to be made.
 
I have had to re-load Mythbuntu several times to get it working somewhat. One of those previous times, both cards worked -- all other times, only the 1st card.

Any help would be appreciated. Like I said, I am new enough that the instructions need to be step-by-step.

Thanks for any help.

---

