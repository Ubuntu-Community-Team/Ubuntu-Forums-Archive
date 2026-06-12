---
title: "Hauppauge HVR-1600 IRQ Problem"
date: 2010-08-19
forum: Hardware
---

### Post by thegodfaza on 2010-08-19
I followed [[COLOR="Blue"]this tutorial[/COLOR]]("http://www.mythtv.org/wiki/Hauppauge_HVR-1600") to get my Hauppauge HVR 1600 working but I get an error about IRQ when I look at dmesg | grep cx18 and there isn't an interface in /dev/ for it. I'm using Ubuntu Server amd64 10.04. I have to boot with noapic or I don't have access to my SATA controller or my NIC. I've tried booting with "pci=bios" and "pci=biosirq" with no effect. The motherboard is a Asus A8AE-LE rebranded as a Compaq AmberineM-GL6E.

```
justin@singularity:~$ sudo dmesg | grep cx18
[sudo] password for justin:
[    8.638050] cx18:  Start initialization, version 1.4.0
[    8.642994] cx18-0: Initializing card 0
[    8.643000] cx18-0: Autodetected Hauppauge card
[    8.668118] cx18 0000:02:09.0: can't find IRQ for PCI INT A; please try using pci=biosirq
[    8.669298] cx18-0: cx23418 revision 01010000 (B)
[    9.181158] cx18-0: Autodetected Hauppauge HVR-1600
[    9.181161] cx18-0: Simultaneous Digital and Analog TV capture supported
[    9.447264] IRQ 0/cx18-0: IRQF_DISABLED is not guaranteed on shared IRQs
[    9.750647] cx18-0: Failed to register irq -16
[    9.752353] cx18-0: Error -16 on initialization
[    9.752436] cx18: probe of 0000:02:09.0 failed with error -16
[    9.752471] cx18:  End initialization

justin@singularity:~$ sudo lspci -vvv
02:09.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
        Subsystem: Hauppauge computer works Inc. Device 7444
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 64 (500ns min, 50000ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 0
        Region 0: Memory at f4000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: [44] Vital Product Data <?>
        Capabilities: [4c] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Kernel modules: cx18

justin@singularity:~$ uname -r
2.6.32-24-generic

justin@singularity:~$ ls /dev
adsp             loop7               ram7        tty11  tty39  tty9
audio            mapper              ram8        tty12  tty4   ttyS0
block            mcelog              ram9        tty13  tty40  ttyS1
bsg              mem                 random      tty14  tty41  ttyS2
cdrom1           mixer               rfkill      tty15  tty42  ttyS3
cdrw1            net                 root        tty16  tty43  urandom
char             network_latency     rtc         tty17  tty44  usbmon0
console          network_throughput  rtc0        tty18  tty45  vcs
core             null                scd0        tty19  tty46  vcs1
cpu_dma_latency  oldmem              sda         tty2   tty47  vcs2
disk             pktcdvd             sda1        tty20  tty48  vcs3
dri              port                sdb         tty21  tty49  vcs4
dsp              ppp                 sdb1        tty22  tty5   vcs5
dvd1             Primary             sequencer   tty23  tty50  vcs6
dvdrw1           psaux               sequencer2  tty24  tty51  vcs7
ecryptfs         ptmx                sg0         tty25  tty52  vcsa
fb0              pts                 sg1         tty26  tty53  vcsa1
fd               ram0                sg2         tty27  tty54  vcsa2
full             ram1                shm         tty28  tty55  vcsa3
fuse             ram10               snapshot    tty29  tty56  vcsa4
input            ram11               snd         tty3   tty57  vcsa5
kmsg             ram12               sndstat     tty30  tty58  vcsa6
log              ram13               sr0         tty31  tty59  vcsa7
loop0            ram14               stderr      tty32  tty6   vga_arbiter
loop1            ram15               stdin       tty33  tty60  zero
loop2            ram2                stdout      tty34  tty61
loop3            ram3                tty         tty35  tty62
loop4            ram4                tty0        tty36  tty63
loop5            ram5                tty1        tty37  tty7
loop6            ram6                tty10       tty38  tty8
```

---

### Post by thegodfaza on 2010-08-22
I was looking around some more and found a couple mentions of people having a similar problem with their BIOS set to "Windows". I took a look and my BIOS had a "Plug and Play OS" option. I disabled that and booted with "pci=biosirq" and all works well. 

Now I just need to find a good Server - Client HTPC software. I used SageTV on windows before but I don't feel like buying another license just because I want to run the server on linux instead of windows. I also looked at MythTV but it's a pain to set up and I couldn't get it working on all my clients. I think there was a mod for XBMC that did server - client setups but I'd have to look into that again.

---

