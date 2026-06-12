---
title: "Virtual Box Error"
date: 2009-10-24
forum: Installation &amp; Upgrades
---

### Post by FireStorm102389 on 2009-10-24
ok, i have the ubuntu 9.whatever, i can't remember, whatever the latest version is...and i installed the Virtualbox on my desktop to run windows XP, i have the upgrade CD and what not, well, i got all the way to where is was starting to copy files and start installing and it caused an error, is there something im missing that i need to do to make this work?...my VLOG is below...

```
00:00:03.616 VirtualBox 2.1.4_OSE r42893 linux.x86 (Mar 30 2009 00:56:07) release log
00:00:03.616 Log opened 2009-10-24T09:12:05.962524000Z
00:00:03.616 OS Product: Linux
00:00:03.616 OS Release: 2.6.28-16-generic
00:00:03.616 OS Version: #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009
00:00:03.616 Package type: LINUX_32BITS_GENERIC (OSE)
00:00:03.623 SUP: Loaded VMMR0.r0 (/usr/lib/virtualbox/VMMR0.r0) at 0xf9ade060 - ModuleInit at 00000000f9aef1f0 and ModuleTerm at 00000000f9aef1b0
00:00:03.623 SUP: VMMR0EntryEx located at 00000000f9aef0b0, VMMR0EntryFast at 00000000f9aef260 and VMMR0EntryInt at 00000000f9aee4a0
00:00:03.704 Initializing host clipboard service
00:00:03.813 VBoxSharedClipboard mode: Bidirectional
00:00:03.813 Shared clipboard: starting host clipboard thread
00:00:04.302 OpenGL Info: Render SPU: GL_VENDOR:   ATI Technologies Inc.
00:00:04.302 OpenGL Info: Render SPU: GL_RENDERER: ATI Radeon HD 4800 Series 
00:00:04.302 OpenGL Info: Render SPU: GL_VERSION:  2.1.8575
00:00:04.305 Shared crOpenGL service loaded.
00:00:04.401 ************************* CFGM dump *************************
00:00:04.401 pRoot=09a20570:{/}
00:00:04.401 [/] (level 0)
00:00:04.401   Name               <string>  = "Windows" (cch=8)
00:00:04.401   UUID               <bytes>   = "6a c7 1f e6 44 c5 a4 4d a8 5b f0 bf de 9a 88 4b" (cb=16)
00:00:04.401   RamSize            <integer> = 0x000000005dc00000 (1572864000)
00:00:04.401   NumCPUs            <integer> = 0x0000000000000001 (1)
00:00:04.401   TimerMillies       <integer> = 0x000000000000000a (10)
00:00:04.402   RawR3Enabled       <integer> = 0x0000000000000001 (1)
00:00:04.402   RawR0Enabled       <integer> = 0x0000000000000001 (1)
00:00:04.402   PATMEnabled        <integer> = 0x0000000000000001 (1)
00:00:04.402   CSAMEnabled        <integer> = 0x0000000000000001 (1)
00:00:04.402   HwVirtExtForced    <integer> = 0x0000000000000000 (0)
00:00:04.402   EnableNestedPaging <integer> = 0x0000000000000000 (0)
00:00:04.402   EnableVPID         <integer> = 0x0000000000000000 (0)
00:00:04.402   EnablePAE          <integer> = 0x0000000000000000 (0)
00:00:04.402 
00:00:04.402 [/HWVirtExt/] (level 1)
00:00:04.402   Enabled      <integer> = 0x0000000000000001 (1)
00:00:04.402   64bitEnabled <integer> = 0x0000000000000000 (0)
00:00:04.402 
00:00:04.402 [/PDM/] (level 1)
00:00:04.402 
00:00:04.402 [/PDM/Drivers/] (level 2)
00:00:04.402 
00:00:04.402 [/PDM/Drivers/VBoxC/] (level 3)
00:00:04.402   Path <string>  = "/usr/lib/virtualbox/components/VBoxC" (cch=37)
00:00:04.402 
00:00:04.402 [/Devices/] (level 1)
00:00:04.402 
00:00:04.402 [/Devices/pcarch/] (level 2)
00:00:04.402 
00:00:04.402 [/Devices/pcarch/0/] (level 3)
00:00:04.402   Trusted <integer> = 0x0000000000000001 (1)
00:00:04.402 
00:00:04.402 [/Devices/pcarch/0/Config/] (level 4)
00:00:04.402 
00:00:04.402 [/Devices/pcbios/] (level 2)
00:00:04.402 
00:00:04.402 [/Devices/pcbios/0/] (level 3)
00:00:04.402   Trusted <integer> = 0x0000000000000001 (1)
00:00:04.402 
00:00:04.402 [/Devices/pcbios/0/Config/] (level 4)
00:00:04.402   RamSize        <integer> = 0x000000005dc00000 (1572864000)
00:00:04.402   NumCPUs        <integer> = 0x0000000000000001 (1)
00:00:04.402   HardDiskDevice <string>  = "piix3ide" (cch=9)
00:00:04.402   FloppyDevice   <string>  = "i82078" (cch=7)
00:00:04.402   IOAPIC         <integer> = 0x0000000000000001 (1)
00:00:04.402   PXEDebug       <integer> = 0x0000000000000000 (0)
00:00:04.402   UUID           <bytes>   = "6a c7 1f e6 44 c5 a4 4d a8 5b f0 bf de 9a 88 4b" (cb=16)
00:00:04.402   BootDevice0    <string>  = "FLOPPY" (cch=7)
00:00:04.402   BootDevice1    <string>  = "DVD" (cch=4)
00:00:04.402   BootDevice2    <string>  = "IDE" (cch=4)
00:00:04.402   BootDevice3    <string>  = "NONE" (cch=5)
00:00:04.402 
00:00:04.402 [/Devices/8237A/] (level 2)
00:00:04.402 
00:00:04.402 [/Devices/8237A/0/] (level 3)
00:00:04.402   Trusted <integer> = 0x0000000000000001 (1)
00:00:04.402 
00:00:04.402 [/Devices/pci/] (level 2)
00:00:04.402 
00:00:04.402 [/Devices/pci/0/] (level 3)
00:00:04.402   Trusted <integer> = 0x0000000000000001 (1)
00:00:04.402 
00:00:04.402 [/Devices/pci/0/Config/] (level 4)
00:00:04.403   IOAPIC <integer> = 0x0000000000000001 (1)
00:00:04.403 
00:00:04.403 [/Devices/pckbd/] (level 2)
00:00:04.403 
00:00:04.403 [/Devices/pckbd/0/] (level 3)
00:00:04.403   Trusted <integer> = 0x0000000000000001 (1)
00:00:04.403 
00:00:04.403 [/Devices/pckbd/0/Config/] (level 4)
00:00:04.403 
00:00:04.403 [/Devices/pckbd/0/LUN#0/] (level 4)
00:00:04.403   Driver <string>  = "KeyboardQueue" (cch=14)
00:00:04.403 
00:00:04.403 [/Devices/pckbd/0/LUN#0/Config/] (level 5)
00:00:04.403   QueueSize <integer> = 0x0000000000000040 (64)
00:00:04.403 
00:00:04.403 [/Devices/pckbd/0/LUN#0/AttachedDriver/] (level 5)
00:00:04.403   Driver <string>  = "MainKeyboard" (cch=13)
00:00:04.403 
00:00:04.403 [/Devices/pckbd/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:04.403   Object <integer> = 0x00000000b5500a28 (3041921576)
00:00:04.403 
00:00:04.403 [/Devices/pckbd/0/LUN#1/] (level 4)
00:00:04.403   Driver <string>  = "MouseQueue" (cch=11)
00:00:04.403 
00:00:04.403 [/Devices/pckbd/0/LUN#1/Config/] (level 5)
00:00:04.403   QueueSize <integer> = 0x0000000000000080 (128)
00:00:04.403 
00:00:04.403 [/Devices/pckbd/0/LUN#1/AttachedDriver/] (level 5)
00:00:04.403   Driver <string>  = "MainMouse" (cch=10)
00:00:04.403 
00:00:04.403 [/Devices/pckbd/0/LUN#1/AttachedDriver/Config/] (level 6)
00:00:04.403   Object <integer> = 0x00000000b5500b00 (3041921792)
00:00:04.403 
00:00:04.403 [/Devices/i82078/] (level 2)
00:00:04.403 
00:00:04.403 [/Devices/i82078/0/] (level 3)
00:00:04.403   Trusted <integer> = 0x0000000000000001 (1)
00:00:04.403 
00:00:04.403 [/Devices/i82078/0/Config/] (level 4)
00:00:04.403   IRQ       <integer> = 0x0000000000000006 (6)
00:00:04.403   DMA       <integer> = 0x0000000000000002 (2)
00:00:04.403   MemMapped <integer> = 0x0000000000000000 (0)
00:00:04.403   IOBase    <integer> = 0x00000000000003f0 (1008)
00:00:04.403 
00:00:04.403 [/Devices/i82078/0/LUN#999/] (level 4)
00:00:04.403   Driver <string>  = "MainStatus" (cch=11)
00:00:04.403 
00:00:04.403 [/Devices/i82078/0/LUN#999/Config/] (level 5)
00:00:04.404   papLeds <integer> = 0x00000000b550067c (3041920636)
00:00:04.404   First   <integer> = 0x0000000000000000 (0)
00:00:04.404   Last    <integer> = 0x0000000000000000 (0)
00:00:04.404 
00:00:04.404 [/Devices/i82078/0/LUN#0/] (level 4)
00:00:04.404   Driver <string>  = "HostFloppy" (cch=11)
00:00:04.404 
00:00:04.404 [/Devices/i82078/0/LUN#0/Config/] (level 5)
00:00:04.404   Path <string>  = "/dev/sdb" (cch=9)
00:00:04.404 
00:00:04.404 [/Devices/i8254/] (level 2)
00:00:04.404 
00:00:04.404 [/Devices/i8254/0/] (level 3)
00:00:04.404 
00:00:04.404 [/Devices/i8254/0/Config/] (level 4)
00:00:04.404 
00:00:04.404 [/Devices/i8259/] (level 2)
00:00:04.404 
00:00:04.404 [/Devices/i8259/0/] (level 3)
00:00:04.404   Trusted <integer> = 0x0000000000000001 (1)
00:00:04.404 
00:00:04.404 [/Devices/i8259/0/Config/] (level 4)
00:00:04.404 
00:00:04.404 [/Devices/apic/] (level 2)
00:00:04.404 
00:00:04.404 [/Devices/apic/0/] (level 3)
00:00:04.404   Trusted <integer> = 0x0000000000000001 (1)
00:00:04.404 
00:00:04.404 [/Devices/apic/0/Config/] (level 4)
00:00:04.404   IOAPIC  <integer> = 0x0000000000000001 (1)
00:00:04.404   NumCPUs <integer> = 0x0000000000000001 (1)
00:00:04.404 
00:00:04.404 [/Devices/ioapic/] (level 2)
00:00:04.404 
00:00:04.404 [/Devices/ioapic/0/] (level 3)
00:00:04.404   Trusted <integer> = 0x0000000000000001 (1)
00:00:04.404 
00:00:04.404 [/Devices/ioapic/0/Config/] (level 4)
00:00:04.404 
00:00:04.404 [/Devices/mc146818/] (level 2)
00:00:04.404 
00:00:04.404 [/Devices/mc146818/0/] (level 3)
00:00:04.404 
00:00:04.404 [/Devices/mc146818/0/Config/] (level 4)
00:00:04.404 
00:00:04.404 [/Devices/vga/] (level 2)
00:00:04.404 
00:00:04.404 [/Devices/vga/0/] (level 3)
00:00:04.405   Trusted       <integer> = 0x0000000000000001 (1)
00:00:04.405   PCIDeviceNo   <integer> = 0x0000000000000002 (2)
00:00:04.405   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:04.405 
00:00:04.405 [/Devices/vga/0/Config/] (level 4)
00:00:04.405   VRamSize         <integer> = 0x0000000000c00000 (12582912)
00:00:04.405   FadeIn           <integer> = 0x0000000000000001 (1)
00:00:04.405   FadeOut          <integer> = 0x0000000000000001 (1)
00:00:04.405   LogoTime         <integer> = 0x0000000000000000 (0)
00:00:04.405   LogoFile         <string>  = "" (cch=1)
00:00:04.405   ShowBootMenu     <integer> = 0x0000000000000002 (2)
00:00:04.405   CustomVideoModes <integer> = 0x0000000000000000 (0)
00:00:04.405   HeightReduction  <integer> = 0x0000000000000000 (0)
00:00:04.405 
00:00:04.405 [/Devices/vga/0/LUN#0/] (level 4)
00:00:04.405   Driver <string>  = "MainDisplay" (cch=12)
00:00:04.405 
00:00:04.405 [/Devices/vga/0/LUN#0/Config/] (level 5)
00:00:04.405   Object <integer> = 0x00000000b5500bd8 (3041922008)
00:00:04.405 
00:00:04.405 [/Devices/piix3ide/] (level 2)
00:00:04.405 
00:00:04.405 [/Devices/piix3ide/0/] (level 3)
00:00:04.405   Trusted       <integer> = 0x0000000000000001 (1)
00:00:04.405   PCIDeviceNo   <integer> = 0x0000000000000001 (1)
00:00:04.405   PCIFunctionNo <integer> = 0x0000000000000001 (1)
00:00:04.405 
00:00:04.405 [/Devices/piix3ide/0/Config/] (level 4)
00:00:04.405   PIIX4 <integer> = 0x0000000000000001 (1)
00:00:04.405 
00:00:04.405 [/Devices/piix3ide/0/LUN#999/] (level 4)
00:00:04.405   Driver <string>  = "MainStatus" (cch=11)
00:00:04.405 
00:00:04.405 [/Devices/piix3ide/0/LUN#999/Config/] (level 5)
00:00:04.405   papLeds <integer> = 0x00000000b5500684 (3041920644)
00:00:04.405   First   <integer> = 0x0000000000000000 (0)
00:00:04.405   Last    <integer> = 0x0000000000000003 (3)
00:00:04.405 
00:00:04.405 [/Devices/piix3ide/0/LUN#0/] (level 4)
00:00:04.405   Driver <string>  = "Block" (cch=6)
00:00:04.405 
00:00:04.405 [/Devices/piix3ide/0/LUN#0/Config/] (level 5)
00:00:04.405   Type      <string>  = "HardDisk" (cch=9)
00:00:04.405   Mountable <integer> = 0x0000000000000000 (0)
00:00:04.405 
00:00:04.405 [/Devices/piix3ide/0/LUN#0/AttachedDriver/] (level 5)
00:00:04.405   Driver <string>  = "VD" (cch=3)
00:00:04.405 
00:00:04.405 [/Devices/piix3ide/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:04.405   Path   <string>  = "/home/david/.VirtualBox/HardDisks/Windows.vdi" (cch=46)
00:00:04.405   Format <string>  = "VDI" (cch=4)
00:00:04.405 
00:00:04.405 [/Devices/piix3ide/0/LUN#2/] (level 4)
00:00:04.405   Driver <string>  = "HostDVD" (cch=8)
00:00:04.405 
00:00:04.405 [/Devices/piix3ide/0/LUN#2/Config/] (level 5)
00:00:04.406   Path        <string>  = "/dev/sr0" (cch=9)
00:00:04.406   Passthrough <integer> = 0x0000000000000001 (1)
00:00:04.406 
00:00:04.406 [/Devices/pcnet/] (level 2)
00:00:04.406 
00:00:04.406 [/Devices/pcnet/0/] (level 3)
00:00:04.406   Trusted       <integer> = 0x0000000000000001 (1)
00:00:04.406   PCIDeviceNo   <integer> = 0x0000000000000003 (3)
00:00:04.406   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:04.406 
00:00:04.406 [/Devices/pcnet/0/Config/] (level 4)
00:00:04.406   Am79C973       <integer> = 0x0000000000000001 (1)
00:00:04.406   MAC            <bytes>   = "08 00 27 80 be 66" (cb=6)
00:00:04.406   CableConnected <integer> = 0x0000000000000001 (1)
00:00:04.406   LineSpeed      <integer> = 0x0000000000000000 (0)
00:00:04.406 
00:00:04.406 [/Devices/pcnet/0/LUN#999/] (level 4)
00:00:04.406   Driver <string>  = "MainStatus" (cch=11)
00:00:04.406 
00:00:04.406 [/Devices/pcnet/0/LUN#999/Config/] (level 5)
00:00:04.406   papLeds <integer> = 0x00000000b550070c (3041920780)
00:00:04.406 
00:00:04.406 [/Devices/pcnet/0/LUN#0/] (level 4)
00:00:04.406   Driver <string>  = "NAT" (cch=4)
00:00:04.406 
00:00:04.406 [/Devices/pcnet/0/LUN#0/Config/] (level 5)
00:00:04.406   TFTPPrefix <string>  = "/home/david/.VirtualBox/TFTP" (cch=29)
00:00:04.406   BootFile   <string>  = "Windows.pxe" (cch=12)
00:00:04.406 
00:00:04.406 [/Devices/e1000/] (level 2)
00:00:04.406 
00:00:04.406 [/Devices/serial/] (level 2)
00:00:04.406 
00:00:04.406 [/Devices/serial/0/] (level 3)
00:00:04.406 
00:00:04.406 [/Devices/serial/0/Config/] (level 4)
00:00:04.406   IRQ    <integer> = 0x0000000000000004 (4)
00:00:04.406   IOBase <integer> = 0x00000000000003f8 (1016)
00:00:04.406 
00:00:04.406 [/Devices/serial/1/] (level 3)
00:00:04.406 
00:00:04.406 [/Devices/serial/1/Config/] (level 4)
00:00:04.406   IRQ    <integer> = 0x0000000000000003 (3)
00:00:04.406   IOBase <integer> = 0x00000000000002f8 (760)
00:00:04.406 
00:00:04.406 [/Devices/parallel/] (level 2)
00:00:04.406 
00:00:04.406 [/Devices/VMMDev/] (level 2)
00:00:04.406 
00:00:04.406 [/Devices/VMMDev/0/] (level 3)
00:00:04.406   Trusted       <integer> = 0x0000000000000001 (1)
00:00:04.406   PCIDeviceNo   <integer> = 0x0000000000000004 (4)
00:00:04.406   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:04.407 
00:00:04.407 [/Devices/VMMDev/0/Config/] (level 4)
00:00:04.407 
00:00:04.407 [/Devices/VMMDev/0/LUN#0/] (level 4)
00:00:04.407   Driver <string>  = "MainVMMDev" (cch=11)
00:00:04.407 
00:00:04.407 [/Devices/VMMDev/0/LUN#0/Config/] (level 5)
00:00:04.407   Object <integer> = 0x00000000b5500498 (3041920152)
00:00:04.407 
00:00:04.407 [/Devices/VMMDev/0/LUN#999/] (level 4)
00:00:04.407   Driver <string>  = "MainStatus" (cch=11)
00:00:04.407 
00:00:04.407 [/Devices/VMMDev/0/LUN#999/Config/] (level 5)
00:00:04.407   papLeds <integer> = 0x00000000b550072c (3041920812)
00:00:04.407   First   <integer> = 0x0000000000000000 (0)
00:00:04.407   Last    <integer> = 0x0000000000000000 (0)
00:00:04.407 
00:00:04.407 [/Devices/AudioSniffer/] (level 2)
00:00:04.407 
00:00:04.407 [/Devices/AudioSniffer/0/] (level 3)
00:00:04.407 
00:00:04.407 [/Devices/AudioSniffer/0/Config/] (level 4)
00:00:04.407 
00:00:04.407 [/Devices/AudioSniffer/0/LUN#0/] (level 4)
00:00:04.407   Driver <string>  = "MainAudioSniffer" (cch=17)
00:00:04.407 
00:00:04.407 [/Devices/AudioSniffer/0/LUN#0/Config/] (level 5)
00:00:04.407   Object <integer> = 0x00000000b55004b8 (3041920184)
00:00:04.407 
00:00:04.407 [/Devices/ichac97/] (level 2)
00:00:04.407 
00:00:04.407 [/Devices/ichac97/0/] (level 3)
00:00:04.407   Trusted       <integer> = 0x0000000000000001 (1)
00:00:04.407   PCIDeviceNo   <integer> = 0x0000000000000005 (5)
00:00:04.407   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:04.407 
00:00:04.407 [/Devices/ichac97/0/Config/] (level 4)
00:00:04.407 
00:00:04.407 [/Devices/ichac97/0/LUN#0/] (level 4)
00:00:04.407   Driver <string>  = "AUDIO" (cch=6)
00:00:04.407 
00:00:04.407 [/Devices/ichac97/0/LUN#0/Config/] (level 5)
00:00:04.407   AudioDriver <string>  = "alsa" (cch=5)
00:00:04.407   StreamName  <string>  = "Windows" (cch=8)
00:00:04.407 
00:00:04.407 [/TM/] (level 1)
00:00:04.407   UTCOffset <integer> = 0x0000000000000000 (0)
00:00:04.407 
00:00:04.407 ********************* End of CFGM dump **********************
00:00:04.409 Logical host processors: 4, processor active mask: 000000000000000f
00:00:04.409 ************************* CPUID dump ************************
00:00:04.409          RAW Standard CPUIDs
00:00:04.409      Function  eax      ebx      ecx      edx
00:00:04.409 Gst: 00000000  00000002 68747541 444d4163 69746e65
00:00:04.409 Hst:           00000005 68747541 444d4163 69746e65
00:00:04.409 Gst: 00000001  00100f52 00000800 00000009 078bf1bf
00:00:04.409 Hst:           00100f52 01040800 00802009 178bfbff
00:00:04.409 Gst: 00000002  00000000 00000000 00000000 00000000
00:00:04.409 Hst:           00000000 00000000 00000000 00000000
00:00:04.409 Gst: 00000003  00000000 00000000 00000000 00000000*
00:00:04.409 Hst:           00000000 00000000 00000000 00000000
00:00:04.409 Gst: 00000004  00000000 00000000 00000000 00000000*
00:00:04.409 Hst:           00000000 00000000 00000000 00000000
00:00:04.409 Gst: 00000005  00000000 00000000 00000000 00000000*
00:00:04.409 Hst:           00000040 00000040 00000003 00000000
00:00:04.409 Name:                            AuthenticAMD
00:00:04.409 Supports:                        0-2
00:00:04.409 Family:                          15  	Extended: 1 	Effective: 16
00:00:04.409 Model:                           5  	Extended: 0 	Effective: 5
00:00:04.409 Stepping:                        2
00:00:04.409 APIC ID:                         0x00
00:00:04.409 Logical CPUs:                    0
00:00:04.409 CLFLUSH Size:                    8
00:00:04.409 Brand ID:                        0x00
00:00:04.409 Mnemonic - Description                 = guest (host)
00:00:04.409 FPU - x87 FPU on Chip                  = 1 (1)
00:00:04.409 VME - Virtual 8086 Mode Enhancements   = 1 (1)
00:00:04.409 DE - Debugging extensions              = 1 (1)
00:00:04.409 PSE - Page Size Extension              = 1 (1)
00:00:04.409 TSC - Time Stamp Counter               = 1 (1)
00:00:04.409 MSR - Model Specific Registers         = 1 (1)
00:00:04.410 PAE - Physical Address Extension       = 0 (1)
00:00:04.410 MCE - Machine Check Exception          = 1 (1)
00:00:04.410 CX8 - CMPXCHG8B instruction            = 1 (1)
00:00:04.410 APIC - APIC On-Chip                    = 0 (1)
00:00:04.410 Reserved                               = 0 (0)
00:00:04.410 SEP - SYSENTER and SYSEXIT             = 0 (1)
00:00:04.410 MTRR - Memory Type Range Registers     = 1 (1)
00:00:04.410 PGE - PTE Global Bit                   = 1 (1)
00:00:04.410 MCA - Machine Check Architecture       = 1 (1)
00:00:04.410 CMOV - Conditional Move Instructions   = 1 (1)
00:00:04.410 PAT - Page Attribute Table             = 1 (1)
00:00:04.410 PSE-36 - 36-bit Page Size Extention    = 1 (1)
00:00:04.410 PSN - Processor Serial Number          = 0 (0)
00:00:04.410 CLFSH - CLFLUSH Instruction.           = 1 (1)
00:00:04.410 Reserved                               = 0 (0)
00:00:04.410 DS - Debug Store                       = 0 (0)
00:00:04.410 ACPI - Thermal Mon. & Soft. Clock Ctrl.= 0 (0)
00:00:04.410 MMX - Intel MMX Technology             = 1 (1)
00:00:04.410 FXSR - FXSAVE and FXRSTOR Instructions = 1 (1)
00:00:04.410 SSE - SSE Support                      = 1 (1)
00:00:04.410 SSE2 - SSE2 Support                    = 1 (1)
00:00:04.410 SS - Self Snoop                        = 0 (0)
00:00:04.410 HTT - Hyper-Threading Technolog        = 0 (1)
00:00:04.410 TM - Thermal Monitor                   = 0 (0)
00:00:04.410 30 - Reserved                          = 0 (0)
00:00:04.410 PBE - Pending Break Enable             = 0 (0)
00:00:04.410 Supports SSE3 or not                   = 1 (1)
00:00:04.410 Reserved                               = 0 (0)
00:00:04.410 Supports MONITOR/MWAIT                 = 1 (1)
00:00:04.410 CPL-DS - CPL Qualified Debug Store     = 0 (0)
00:00:04.410 VMX - Virtual Machine Technology       = 0 (0)
00:00:04.410 Reserved                               = 0 (0)
00:00:04.410 Enhanced SpeedStep Technology          = 0 (0)
00:00:04.410 Terminal Monitor 2                     = 0 (0)
00:00:04.410 Supports Supplemental SSE3 or not      = 0 (0)
00:00:04.410 L1 Context ID                          = 0 (0)
00:00:04.410 Reserved                               = 0x0 (0x0)
00:00:04.410 CMPXCHG16B                             = 0 (1)
00:00:04.410 xTPR Update Control                    = 0 (0)
00:00:04.410 Reserved                               = 0x0 (0x100)
00:00:04.410 
00:00:04.410          RAW Extended CPUIDs
00:00:04.410      Function  eax      ebx      ecx      edx
00:00:04.410 Gst: 80000000  80000008 68747541 444d4163 69746e65
00:00:04.410 Hst:           8000001b 68747541 444d4163 69746e65
00:00:04.410 Gst: 80000001  00100f52 10005146 00000000 c383f13f
00:00:04.410 Hst:           00100f52 10005146 000037ff efd3fbff
00:00:04.410 Gst: 80000002  20444d41 6c687441 74286e6f 4920296d
00:00:04.410 Hst:           20444d41 6c687441 74286e6f 4920296d
00:00:04.410 Gst: 80000003  34582049 30323620 6f725020 73736563
00:00:04.410 Hst:           34582049 30323620 6f725020 73736563
00:00:04.410 Gst: 80000004  0000726f 00000000 00000000 00000000
00:00:04.410 Hst:           0000726f 00000000 00000000 00000000
00:00:04.410 Gst: 80000005  ff30ff10 ff30ff20 40020140 40020140
00:00:04.410 Hst:           ff30ff10 ff30ff20 40020140 40020140
00:00:04.410 Gst: 80000006  20800000 42004200 02008140 00000000
00:00:04.410 Hst:           20800000 42004200 02008140 00000000
00:00:04.410 Gst: 80000007  00000000 00000000 00000000 00000100
00:00:04.410 Hst:           00000000 00000000 00000000 000001f9
00:00:04.410 Gst: 80000008  00003030 00000000 00000000 00000000
00:00:04.410 Hst:           00003030 00000000 00002003 00000000
00:00:04.410 Gst: 80000009  00000000 00000000 00000000 00000000*
00:00:04.410 Hst:           00000000 00000000 00000000 00000000
00:00:04.410 Ext Name:                        AuthenticAMD
00:00:04.410 Ext Supports:                    0x80000000-0x80000008
00:00:04.410 Family:                          15  	Extended: 1 	Effective: 16
00:00:04.410 Model:                           5  	Extended: 0 	Effective: 5
00:00:04.410 Stepping:                        2
00:00:04.410 Brand ID:                        0x146
00:00:04.410 Mnemonic - Description                 = guest (host)
00:00:04.410 FPU - x87 FPU on Chip                  = 1 (1)
00:00:04.410 VME - Virtual 8086 Mode Enhancements   = 1 (1)
00:00:04.410 DE - Debugging extensions              = 1 (1)
00:00:04.410 PSE - Page Size Extension              = 1 (1)
00:00:04.410 TSC - Time Stamp Counter               = 1 (1)
00:00:04.410 MSR - K86 Model Specific Registers     = 1 (1)
00:00:04.410 PAE - Physical Address Extension       = 0 (1)
00:00:04.410 MCE - Machine Check Exception          = 0 (1)
00:00:04.410 CX8 - CMPXCHG8B instruction            = 1 (1)
00:00:04.410 APIC - APIC On-Chip                    = 0 (1)
00:00:04.410 10 - Reserved                          = 0 (0)
00:00:04.410 SEP - SYSCALL and SYSRET               = 0 (1)
00:00:04.410 MTRR - Memory Type Range Registers     = 1 (1)
00:00:04.410 PGE - PTE Global Bit                   = 1 (1)
00:00:04.410 MCA - Machine Check Architecture       = 1 (1)
00:00:04.410 CMOV - Conditional Move Instructions   = 1 (1)
00:00:04.410 PAT - Page Attribute Table             = 1 (1)
00:00:04.410 PSE-36 - 36-bit Page Size Extention    = 1 (1)
00:00:04.410 18 - Reserved                          = 0 (0)
00:00:04.410 19 - Reserved                          = 0 (0)
00:00:04.410 NX - No-Execute Page Protection        = 0 (1)
00:00:04.410 DS - Debug Store                       = 0 (0)
00:00:04.410 AXMMX - AMD Extensions to MMX Instr.   = 0 (1)
00:00:04.410 MMX - Intel MMX Technology             = 1 (1)
00:00:04.410 FXSR - FXSAVE and FXRSTOR Instructions = 1 (1)
00:00:04.410 25 - AMD fast FXSAVE and FXRSTOR Instr.= 1 (1)
00:00:04.410 26 - 1 GB large page support           = 0 (1)
00:00:04.410 27 - RDTSCP instruction                = 0 (1)
00:00:04.410 28 - Reserved                          = 0 (0)
00:00:04.410 29 - AMD Long Mode                     = 0 (1)
00:00:04.410 30 - AMD Extensions to 3DNow           = 1 (1)
00:00:04.410 31 - AMD 3DNow                         = 1 (1)
00:00:04.410 LahfSahf - LAHF/SAHF in 64-bit mode    = 0 (1)
00:00:04.410 CmpLegacy - Core MP legacy mode (depr) = 0 (1)
00:00:04.410 SVM - AMD VM Extensions                = 0 (1)
00:00:04.410 APIC registers starting at 0x400       = 0 (1)
00:00:04.410 AltMovCR8 - LOCK MOV CR0 means MOV CR8 = 0 (1)
00:00:04.410 Advanced bit manipulation              = 0 (1)
00:00:04.410 SSE4A instruction support              = 0 (1)
00:00:04.410 Misaligned SSE mode                    = 0 (1)
00:00:04.410 PREFETCH and PREFETCHW instruction     = 0 (1)
00:00:04.410 OS visible workaround                  = 0 (1)
00:00:04.410 Instruction based sampling             = 0 (1)
00:00:04.410 SSE5 support                           = 0 (0)
00:00:04.410 SKINIT, STGI, and DEV support          = 0 (1)
00:00:04.410 Watchdog timer support.                = 0 (1)
00:00:04.411 31:14 - Reserved                       = 0x0 (0x0)
00:00:04.411 Full Name:                       AMD Athlon(tm) II X4 620 Processor
00:00:04.411 TLB 2/4M Instr/Uni:              255 way  16 entries
00:00:04.411 TLB 2/4M Data:                   255 way  48 entries
00:00:04.411 TLB 4K Instr/Uni:                255 way  32 entries
00:00:04.411 TLB 4K Data:                     255 way  48 entries
00:00:04.411 L1 Instr Cache Line Size:        64 bytes
00:00:04.411 L1 Instr Cache Lines Per Tag:    1
00:00:04.411 L1 Instr Cache Associativity:    2 way
00:00:04.411 L1 Instr Cache Size:             64 KB
00:00:04.411 L1 Data Cache Line Size:         64 bytes
00:00:04.411 L1 Data Cache Lines Per Tag:     1
00:00:04.411 L1 Data Cache Associativity:     2 way
00:00:04.411 L1 Data Cache Size:              64 KB
00:00:04.411 L2 TLB 2/4M Instr/Uni:           off       0 entries
00:00:04.411 L2 TLB 2/4M Data:                2 way   128 entries
00:00:04.411 L2 TLB 4K Instr/Uni:             4 way   512 entries
00:00:04.411 L2 TLB 4K Data:                  4 way   512 entries
00:00:04.411 L2 Cache Line Size:              0 bytes
00:00:04.411 L2 Cache Lines Per Tag:          0
00:00:04.411 L2 Cache Associativity:          off   
00:00:04.411 L2 Cache Size:                   0 KB
00:00:04.411 APM Features:                    8
00:00:04.411 Physical Address Width:          48 bits
00:00:04.411 Virtual Address Width:           48 bits
00:00:04.411 Physical Core Count:             0
00:00:04.411 
00:00:04.411          RAW Centaur CPUIDs
00:00:04.411      Function  eax      ebx      ecx      edx
00:00:04.411 Gst: c0000000  00000000 00000000 00000000 00000000
00:00:04.411 Hst:           00000000 00000000 00000000 00000000
00:00:04.411 Gst: c0000001  00000000 00000000 00000000 00000000*
00:00:04.411 Hst:           00000000 00000000 00000000 00000000
00:00:04.411 Gst: c0000002  00000000 00000000 00000000 00000000*
00:00:04.411 Hst:           00000000 00000000 00000000 00000000
00:00:04.411 Gst: c0000003  00000000 00000000 00000000 00000000*
00:00:04.411 Hst:           00000000 00000000 00000000 00000000
00:00:04.411 Centaur Supports:                0xc0000000-0x00000000
00:00:04.411 
00:00:04.411 ******************** End of CPUID dump **********************
00:00:04.413 REM: VBoxREM32
00:00:04.471 TM: GIP - u32Mode=1 (SyncTSC) u32UpdateHz=83
00:00:04.500 TM: cTSCTicksPerSecond=0x9a0169b2 (2583783858) fTSCVirtualized=true  fTSCUseRealTSC=false
00:00:04.500 TM: fMaybeUseOffsettedHostTSC=true  TSCTiedToExecution=false TSCNotTiedToHalt=false
00:00:04.501 CoreCode: R3=b1f7d000 R0=f9c22000 RC=a0788000 Phys=000000002a4ca000 cb=0x2000
00:00:04.518 SUP: Loaded VBoxDDR0.r0 (/usr/lib/virtualbox/VBoxDDR0.r0) at 0xf9c2a060 - ModuleInit at 0000000000000000 and ModuleTerm at 0000000000000000
00:00:04.523 SUP: Loaded VBoxDD2R0.r0 (/usr/lib/virtualbox/VBoxDD2R0.r0) at 0xf9c48060 - ModuleInit at 0000000000000000 and ModuleTerm at 0000000000000000
00:00:04.523 Activating Local APIC
00:00:04.523 CPUMSetGuestCpuIdFeature: Enabled APIC
00:00:04.523 CPUMSetGuestCpuIdFeature: Disabled x2APIC
00:00:04.523 PIT: mode=3 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:04.529 Shared Folders service loaded.
00:00:05.073 VDInit finished
00:00:05.074 PIIX3 ATA: LUN#0: disk, PCHS=16383/16/63, total number of sectors 41943040
00:00:05.074 PIIX3 ATA: LUN#1: no unit
00:00:05.075 PIIX3 ATA: LUN#2: CD/DVD, total number of sectors 0, passthrough enabled
00:00:05.075 PIIX3 ATA: LUN#3: no unit
00:00:05.075 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:05.075 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:05.076 NAT: DNS address: 192.168.1.1
00:00:05.077 Audio: Trying driver 'alsa'.
00:00:05.077 Audio: set_record_source ars=0 als=0 (not implemented)
00:00:05.131 ALSA: ADC frequency 44100Hz, period size 1024, buffer size 4096
00:00:05.147 ALSA: DAC frequency 44100Hz, period size 256, buffer size 1024
00:00:05.148 Serial0: no unit
00:00:05.148 Serial1: no unit
00:00:05.149 DevPcBios: ATA LUN#0 LCHS=1024/255/63
00:00:05.149 PGMR3InitFinalize: 4 MB PSE mask 0000000fffffffff
00:00:05.167 HWACCM: No VMX or SVM CPU extension found. Reason VERR_SVM_DISABLED
00:00:05.167 HWACCM: VMX MSR_IA32_FEATURE_CONTROL=0
00:00:05.183 VM: Halt method global1 (5)
00:00:05.183 Changing the VM state from 'CREATING' to 'CREATED'.
00:00:05.183 Changing the VM state from 'CREATED' to 'RUNNING'.
00:00:05.191 Guest Log: BIOS: VirtualBox 2.1.4_OSE
00:00:05.192 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:05.212 PIIX3 ATA: Ctl#0: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:05.213 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:05.219 Guest Log: BIOS: ata0-0: PCHS=16383/16/63 LCHS=1024/255/63
00:00:05.221 PIIX3 ATA: Ctl#1: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:05.221 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:05.223 PIT: mode=2 count=0x48d3 (18643) - 64.00 Hz (ch=0)
00:00:05.231 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b0a00000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:05.771 Guest Log: Key pressed: 0086
00:00:05.790 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00000000 w=720 h=400 bpp=0 cbLine=0x0
00:00:14.822 Guest Log: Key pressed: 002E
00:00:14.828 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:14.908 Guest Log: BIOS: Booting from CD-ROM...
00:00:16.408 Guest Log: BIOS: int13_harddisk: function 15, unmapped device for ELDL=81
00:01:44.186 RTC: period=0x200 (512) 64 Hz
00:02:07.861 PIIX3 ATA: LUN#0: IDLE IMMEDIATE, CmdIf=0xc4 (-1 usec ago)
00:02:07.861 PIIX3 ATA: LUN#0: aborting current command
00:02:10.851 PIIX3 ATA: LUN#2: CD-ROM passthrough cmd=0x5a sense=5 ASC=0x24 ASCQ=0x0 VERR_DEV_IO_ERROR
00:02:10.979 PATM: Disable block at 898f651c - write 898f65ac-898f65b0
00:02:13.956 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00000000 w=720 h=396 bpp=0 cbLine=0x0
07:50:17.635 Changing the VM state from 'RUNNING' to 'SUSPENDED'.
07:50:17.724 PIIX3 ATA: LUN#2: CD/DVD, total number of sectors 0, passthrough enabled
07:50:17.724 Changing the VM state from 'SUSPENDED' to 'RUNNING'.
07:51:10.840 PIIX3 ATA: Ctl#1: RESET, DevSel=0 AIOIf=0 CmdIf0=0xa0 (4001118 usec ago) CmdIf1=0x00 (-1 usec ago)
07:51:10.867 PIIX3 ATA: Ctl#1: finished processing RESET
07:51:10.875 PIIX3 ATA: LUN#2: performing device RESET
08:00:07.458 Changing the VM state from 'RUNNING' to 'SUSPENDED'.
08:00:07.474 PIIX3 ATA: LUN#2: CD/DVD, total number of sectors 0, passthrough enabled
08:00:07.474 Changing the VM state from 'SUSPENDED' to 'RUNNING'.
08:03:42.995 Changing the VM state from 'RUNNING' to 'SUSPENDED'.
08:03:43.107 PIIX3 ATA: LUN#2: CD/DVD, total number of sectors 0, passthrough enabled
08:03:43.107 Changing the VM state from 'SUSPENDED' to 'RUNNING'.
             RTC: stopped the periodic timer
08:11:12.524 Changing the VM state from 'RUNNING' to 'RESETTING'.
08:11:13.028 CPUMSetGuestCpuIdFeature: Enabled APIC
08:11:13.028 CPUMSetGuestCpuIdFeature: Disabled x2APIC
08:11:13.028 PIT: mode=3 count=0x10000 (65536) - 18.20 Hz (ch=0)
08:11:13.085 PIIX3 ATA: Ctl#0: finished processing RESET
08:11:13.086 PIIX3 ATA: Ctl#1: finished processing RESET
08:11:13.186 Audio: set_record_source ars=0 als=0 (not implemented)
08:11:13.186 Changing the VM state from 'RESETTING' to 'RUNNING'.
08:11:13.194 Guest Log: BIOS: VirtualBox 2.1.4_OSE
08:11:13.196 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
08:11:13.221 PIIX3 ATA: Ctl#0: RESET, DevSel=0 AIOIf=0 CmdIf0=0xe7 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
08:11:13.221 PIIX3 ATA: Ctl#0: finished processing RESET
08:11:13.226 Guest Log: BIOS: ata0-0: PCHS=16383/16/63 LCHS=1024/255/63
08:11:13.228 PIIX3 ATA: Ctl#1: RESET, DevSel=0 AIOIf=0 CmdIf0=0xa0 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
08:11:13.228 PIIX3 ATA: Ctl#1: finished processing RESET
08:11:13.230 PIT: mode=2 count=0x48d3 (18643) - 64.00 Hz (ch=0)
08:11:13.236 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b0a00000 w=640 h=480 bpp=32 cbLine=0xA00
08:11:15.119 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
08:11:15.121 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00000000 w=720 h=400 bpp=0 cbLine=0x0
08:11:15.125 Guest Log: BIOS: Boot from Floppy 0 failed
08:11:15.926 Guest Log: BIOS: Booting from CD-ROM...
08:11:20.644 Guest Log: BIOS: int13_harddisk: function 15, unmapped device for ELDL=81
08:11:28.190 PATM: Disabling IDT e patch handler 804e1f25
08:11:28.193 PATM: Disable block at 804e1827 - write 804e1bf4-804e1bf8
08:11:28.193 PATM: Disabling IDT d patch handler 804e1827
08:11:28.193 PATM: Disable block at 804df417 - write 804e1bf4-804e1bf8
08:11:28.193 PATM: Disabling IDT 2a patch handler 804df417
08:11:28.193 PATM: Disable block at 804e12ca - write 804e1bb4-804e1bb8
08:11:28.193 PATM: Disabling IDT b patch handler 804e12ca
08:11:28.196 PATM: Disable block at 804e18d4 - write 804e18f7-804e18fb
08:11:28.198 PATM: Disable block at 804e1530 - write 804e15e0-804e15e4
08:11:28.198 PATM: Disabling IDT c patch handler 804e1530
08:11:28.199 PATM: Disable block at 804e1185 - write 804e11a1-804e11a5
08:11:28.199 PATM: Disabling IDT a patch handler 804e1185
08:11:28.200 PATM: Disable block at 804e1060 - write 804e1069-804e106d
08:11:28.200 PATM: Disabling IDT 9 patch handler 804e1060
08:11:28.202 PATM: Disable block at 804e0d32 - write 804e0eb0-804e0eb4
08:11:28.202 PATM: Disable block at 804e0c33 - write 804e0eb0-804e0eb4
08:11:28.202 PATM: Disabling IDT 7 patch handler 804e0c33
08:11:28.203 PATM: Disable block at 804e237f - write 804e0d90-804e0d94
08:11:28.203 PATM: Disabling IDT 10 patch handler 804e237f
08:11:28.206 PATM: Disable block at 804e05bf - write 804e0a60-804e0a64
08:11:28.206 PATM: Disabling IDT 6 patch handler 804e05bf
08:11:28.206 PATM: Disable block at 804e09a3 - write 804e09c0-804e09c4
08:11:28.210 PATM: Disable block at 804e0441 - write 804e0470-804e0474
08:11:28.210 PATM: Disabling IDT 5 patch handler 804e0441
08:11:28.210 PATM: Disable block at 804e02e0 - write 804e030c-804e0310
08:11:28.210 PATM: Disabling IDT 4 patch handler 804e02e0
08:11:28.211 PATM: Disable block at 804e015b - write 804e0190-804e0194
08:11:28.211 PATM: Disabling IDT 3 patch handler 804e015b
08:11:28.211 PATM: Disable block at 804e0032 - write 804e0072-804e0076
08:11:28.211 PATM: Disabling IDT 2d patch handler 804e0032
08:11:28.212 VERR_REM_TOO_MANY_TRAPS -> uTrap=e error=0 next_eip=00000000804e1f25 eip=00000000804e1f25 cr2=00000000fff90023
08:11:28.212 !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
08:11:28.212 !!
08:11:28.212 !!                 Guru Meditation -2304 (VERR_REM_TOO_MANY_TRAPS)
08:11:28.234 !!
08:11:28.234 !!
08:11:28.234 !! {mappings, <NULL>}
08:11:28.234 !!
08:11:28.234 
08:11:28.234 The mappings are FLOATING.
08:11:28.234 00000000ea400000 - 00000000eaffffff  Hypervisor Memory Area
08:11:28.234 !!
08:11:28.234 !! {hma, <NULL>}
08:11:28.234 !!
08:11:28.234 Hypervisor Memory Area (HMA) Layout: Base 00000000ea400000, 0x00c00000 bytes
08:11:28.234 00000000eaef6000-00000000eaef7000                   DYNAMIC          fence
08:11:28.248 00000000eaeee000-00000000eaef6000                   DYNAMIC          Dynamic mapping
08:11:28.257 00000000eaeed000-00000000eaeee000                   DYNAMIC          fence
08:11:28.257 00000000eaee2000-00000000eaeed000                   DYNAMIC          Paging
08:11:28.257 00000000eaee0000-00000000eaee2000                   MMIO2   0000000000000000 PCNetShMem
08:11:28.273 00000000eaedf000-00000000eaee0000                   DYNAMIC          fence
08:11:28.273 00000000eaebf000-00000000eaedf000 b088c000 b088c000 LOCKED  pages    alloc once (PDM_DEVICE_USER)
08:11:28.273 00000000eaebe000-00000000eaebf000                   DYNAMIC          fence
08:11:28.273 00000000eaeae000-00000000eaebe000 b094e000 b094e000 LOCKED  pages    alloc once (PDM_DEVICE_USER)
08:11:28.273 00000000eae2e000-00000000eaeae000                   MMIO2   0000000000000000 VGA VRam
08:11:28.273 00000000eae2d000-00000000eae2e000                   DYNAMIC          fence
08:11:28.273 00000000eae1a000-00000000eae2d000 b1b49000 b1b49000 LOCKED  pages    alloc once (PDM_DEVICE)
08:11:28.273 00000000eae19000-00000000eae1a000                   DYNAMIC          fence
08:11:28.273 00000000eae16000-00000000eae19000 b4d6a000 00000000 LOCKED  pages    VBoxDD2GC.gc
08:11:28.273 00000000eae15000-00000000eae16000                   DYNAMIC          fence
08:11:28.273 00000000eae08000-00000000eae15000 b1be5000 00000000 LOCKED  pages    VBoxDDGC.gc
08:11:28.274 00000000eae07000-00000000eae08000                   DYNAMIC          fence
08:11:28.274 00000000eadb5000-00000000eae07000 b1d04000 00000000 LOCKED  pages    VMMGC.gc
08:11:28.274 00000000eadb4000-00000000eadb5000                   DYNAMIC          fence
08:11:28.274 00000000eabae000-00000000eadb4000 b1d56000 b1d56000 LOCKED  pages    alloc once (PATM)
08:11:28.274 00000000eabad000-00000000eabae000                   DYNAMIC          fence
08:11:28.274 00000000eab9c000-00000000eabad000 b1f5c000 b1f5c000 LOCKED  pages    alloc once (SELM)
08:11:28.274 00000000eab9b000-00000000eab9c000                   DYNAMIC          fence
08:11:28.274 00000000eab8b000-00000000eab9b000 b1f6d000 b1f6d000 LOCKED  pages    alloc once (SELM)
08:11:28.274 00000000eab8a000-00000000eab8b000                   DYNAMIC          fence
08:11:28.274 00000000eab88000-00000000eab8a000 b1f7d000 f9c22000 HCPHYS  000000002a4ca000 Core Code
08:11:28.274 00000000eab87000-00000000eab88000                   DYNAMIC          fence
08:11:28.274 00000000eab86000-00000000eab87000 b8053000 00000000 HCPHYS  0000000035b35000 GIP
08:11:28.274 00000000eab85000-00000000eab86000                   DYNAMIC          fence
08:11:28.274 00000000ea5a8000-00000000eab85000 b2454000 b2454000 LOCKED  pages    alloc once (PGM_PHYS)
08:11:28.274 00000000ea5a7000-00000000ea5a8000                   DYNAMIC          fence
08:11:28.274 00000000ea570000-00000000ea5a7000 b2c71000 b2c71000 LOCKED  pages    alloc once (PGM_POOL)
08:11:28.274 00000000ea56f000-00000000ea570000                   DYNAMIC          fence
08:11:28.274 00000000ea56a000-00000000ea56f000                   DYNAMIC          CR3 mapping
08:11:28.274 00000000ea569000-00000000ea56a000                   DYNAMIC          fence
08:11:28.274 00000000ea429000-00000000ea569000 b2d48000 b2d48000 LOCKED  pages    Heap
08:11:28.274 00000000ea428000-00000000ea429000                   DYNAMIC          fence
08:11:28.274 00000000ea401000-00000000ea428000 b511d000 f9bce000 LOCKED  pages    VM
08:11:28.275 00000000ea400000-00000000ea401000                   DYNAMIC          fence
08:11:28.275 !!
08:11:28.275 !! {cpumguest, verbose}
08:11:28.275 !!
08:11:28.275 Guest CPUM state: se
08:11:28.275 eax=fff90023 ebx=8b64e38e ecx=00000001 edx=40000000 esi=c0000000 edi=804e9659
08:11:28.275 eip=804e1f25 esp=804dff18 ebp=804e1f38 iopl=0         nv up di pl nz na po nc
08:11:28.275 cs={0008 base=0000000000000000 limit=ffffffff flags=0000c09a} dr0=00000000 dr1=00000000
08:11:28.275 ds={0023 base=0000000000000000 limit=ffffffff flags=0000c0f3} dr2=00000000 dr3=00000000
08:11:28.275 es={0023 base=0000000000000000 limit=ffffffff flags=0000c0f3} dr4=00000000 dr5=00000000
08:11:28.275 fs={0030 base=00000000ffdff000 limit=00001fff flags=0000c093} dr6=ffff0ff0 dr7=00000000
08:11:28.275 gs={0000 base=0000000000000000 limit=0000ffff flags=00000092} cr0=fffffff7 cr2=fff90023
08:11:28.275 ss={0010 base=0000000000000000 limit=ffffffff flags=0000c093} cr3=00039000 cr4=00000000
08:11:28.275 gdtr=000000008003f000:03ff  idtr=000000008003f400:07ff  eflags=00000046
08:11:28.275 ldtr={0000 base=00000000 limit=00000000 flags=00000082}
08:11:28.275 tr  ={0028 base=80042000 limit=000020ab flags=00000089}
08:11:28.275 SysEnter={cs=0000 eip=00000000 esp=00000000}
08:11:28.275 FPU:
08:11:28.275 FCW=0000 FSW=0000 FTW=80
08:11:28.275 res1=00 FOP=0000 FPUIP=00000000 CS=0000 Rsvrd1=0000
08:11:28.275 FPUDP=0000 DS=0000 Rsvrd2=0000 MXCSR=00001f80 MXCSR_MASK=00000000
08:11:28.275 MSR:
08:11:28.275 EFER         =0000000000000000
08:11:28.275 PAT          =0007040600070406
08:11:28.275 STAR         =0000000000000000
08:11:28.275 CSTAR        =0000000000000000
08:11:28.275 LSTAR        =0000000000000000
08:11:28.275 SFMASK       =0000000000000000
08:11:28.275 KERNELGSBASE =0000000000000000
08:11:28.275 !!
08:11:28.275 !! {cpumguestinstr, verbose}
08:11:28.275 !!
08:11:28.275 
08:11:28.275 CPUM: 0008:804e1f25 00 00                   add byte [eax], al
08:11:28.275 
08:11:28.275 !!
08:11:28.275 !! {cpumhyper, verbose}
08:11:28.275 !!
08:11:28.275 Hypervisor CPUM state: se
08:11:28.275 .eax=00000000 .ebx=804e20bc .ecx=00000000 .edx=00000000 .esi=c0000000 .edi=00000001
08:11:28.275 .eip=eadb5280 .esp=ea567fe4 .ebp=804e2034 .iopl=0           nv up di pl zr na pe nc
08:11:28.275 .cs={fff8 base=0000000000000000 limit=00000000 flags=00000000} .dr0=00000000 .dr1=00000000
08:11:28.275 .ds={fff0 base=0000000000000000 limit=00000000 flags=00000000} .dr2=00000000 .dr3=00000000
08:11:28.275 .es={fff0 base=0000000000000000 limit=00000000 flags=00000000} .dr4=00000000 .dr5=00000000
08:11:28.275 .fs={0000 base=0000000000000000 limit=00000000 flags=00000000} .dr6=00000000 .dr7=00000000
08:11:28.275 .gs={0000 base=0000000000000000 limit=00000000 flags=00000000} .cr0=00000000 .cr2=00000000
08:11:28.275 .ss={fff0 base=0000000000000000 limit=00000000 flags=00000000} .cr3=35862000 .cr4=00000000
08:11:28.275 .gdtr=00000000eab8b000:ffff  .idtr=00000000ea40f390:07ff  .eflags=00000000
08:11:28.275 .ldtr={0000 base=00000000 limit=00000000 flags=00000000}
08:11:28.275 .tr  ={ffe0 base=00000000 limit=00000000 flags=00000000}
08:11:28.275 .SysEnter={cs=0000 eip=00000000 esp=00000000}
08:11:28.275 FPU:
08:11:28.275 .FCW=0000 .FSW=0000 .FTW=00
08:11:28.275 .res1=00 .FOP=0000 .FPUIP=00000000 .CS=0000 .Rsvrd1=0000
08:11:28.275 .FPUDP=0000 .DS=0000 .Rsvrd2=0000 .MXCSR=00000000 .MXCSR_MASK=00000000
08:11:28.276 MSR:
08:11:28.276 .EFER         =0000000000000000
08:11:28.276 .PAT          =0000000000000000
08:11:28.276 .STAR         =0000000000000000
08:11:28.276 .CSTAR        =0000000000000000
08:11:28.276 .LSTAR        =0000000000000000
08:11:28.276 .SFMASK       =0000000000000000
08:11:28.276 .KERNELGSBASE =0000000000000000
08:11:28.276 CR4OrMask=0x204 CR4AndMask=0x403
08:11:28.276 !!
08:11:28.276 !! {cpumhost, verbose}
08:11:28.276 !!
08:11:28.276 Host CPUM state: se
08:11:28.276 eax=xxxxxxxx ebx=f9bce000 ecx=xxxxxxxx edx=xxxxxxxx esi=00000000 edi=00000246
08:11:28.276 eip=xxxxxxxx esp=ecaf9ec8 ebp=ecaf9efc iopl=0         nv up di nt zr na pe nc
08:11:28.276 cs=0000 ds=007b es=007b fs=00d8 gs=0033                       eflags=00000082
08:11:28.276 cr0=9e6000080050033 cr2=xxxxxxxx cr3=00000690 cr4=00000000 gdtr=00000000:0000 ldtr=0000
08:11:28.276 dr[0]=ffc2a1b000 dr[1]=6000000000x dr[2]=00000000 dr[3]=00000000x dr[6]=b52d0d5000000000 dr[7]=9a5334000000037
08:11:28.276 SysEnter={cs=b575b414 eip=00000002 esp=7520766e}
08:11:28.276 !!
08:11:28.276 !! {mode, all}
08:11:28.276 !!
08:11:28.276 Guest paging mode:  32-bit, changed 1570 times, A20 enabled
08:11:28.276 Shadow paging mode: 32-bit
08:11:28.276 Host paging mode:   32-bit+G
08:11:28.276 !!
08:11:28.276 !! {cpuid, verbose}
08:11:28.276 !!
08:11:28.276          RAW Standard CPUIDs
08:11:28.276      Function  eax      ebx      ecx      edx
08:11:28.276 Gst: 00000000  00000002 68747541 444d4163 69746e65
08:11:28.276 Hst:           00000005 68747541 444d4163 69746e65
08:11:28.276 Gst: 00000001  00100f52 00000800 00000009 078bf3bf
08:11:28.276 Hst:           00100f52 03040800 00802009 178bfbff
08:11:28.276 Gst: 00000002  00000000 00000000 00000000 00000000
08:11:28.276 Hst:           00000000 00000000 00000000 00000000
08:11:28.276 Gst: 00000003  00000000 00000000 00000000 00000000*
08:11:28.276 Hst:           00000000 00000000 00000000 00000000
08:11:28.276 Gst: 00000004  00000000 00000000 00000000 00000000*
08:11:28.276 Hst:           00000000 00000000 00000000 00000000
08:11:28.276 Gst: 00000005  00000000 00000000 00000000 00000000*
08:11:28.276 Hst:           00000040 00000040 00000003 00000000
08:11:28.276 Name:                            AuthenticAMD
08:11:28.276 Supports:                        0-2
08:11:28.276 Family:                          15  	Extended: 1 	Effective: 16
08:11:28.276 Model:                           5  	Extended: 0 	Effective: 5
08:11:28.276 Stepping:                        2
08:11:28.276 APIC ID:                         0x00
08:11:28.276 Logical CPUs:                    0
08:11:28.276 CLFLUSH Size:                    8
08:11:28.276 Brand ID:                        0x00
08:11:28.276 Mnemonic - Description                 = guest (host)
08:11:28.276 FPU - x87 FPU on Chip                  = 1 (1)
08:11:28.276 VME - Virtual 8086 Mode Enhancements   = 1 (1)
08:11:28.276 DE - Debugging extensions              = 1 (1)
08:11:28.276 PSE - Page Size Extension              = 1 (1)
08:11:28.276 TSC - Time Stamp Counter               = 1 (1)
08:11:28.276 MSR - Model Specific Registers         = 1 (1)
08:11:28.276 PAE - Physical Address Extension       = 0 (1)
08:11:28.276 MCE - Machine Check Exception          = 1 (1)
08:11:28.276 CX8 - CMPXCHG8B instruction            = 1 (1)
08:11:28.276 APIC - APIC On-Chip                    = 1 (1)
08:11:28.276 Reserved                               = 0 (0)
08:11:28.276 SEP - SYSENTER and SYSEXIT             = 0 (1)
08:11:28.276 MTRR - Memory Type Range Registers     = 1 (1)
08:11:28.276 PGE - PTE Global Bit                   = 1 (1)
08:11:28.276 MCA - Machine Check Architecture       = 1 (1)
08:11:28.276 CMOV - Conditional Move Instructions   = 1 (1)
08:11:28.276 PAT - Page Attribute Table             = 1 (1)
08:11:28.276 PSE-36 - 36-bit Page Size Extention    = 1 (1)
08:11:28.276 PSN - Processor Serial Number          = 0 (0)
08:11:28.276 CLFSH - CLFLUSH Instruction.           = 1 (1)
08:11:28.276 Reserved                               = 0 (0)
08:11:28.276 DS - Debug Store                       = 0 (0)
08:11:28.276 ACPI - Thermal Mon. & Soft. Clock Ctrl.= 0 (0)
08:11:28.276 MMX - Intel MMX Technology             = 1 (1)
08:11:28.276 FXSR - FXSAVE and FXRSTOR Instructions = 1 (1)
08:11:28.277 SSE - SSE Support                      = 1 (1)
08:11:28.277 SSE2 - SSE2 Support                    = 1 (1)
08:11:28.277 SS - Self Snoop                        = 0 (0)
08:11:28.277 HTT - Hyper-Threading Technolog        = 0 (1)
08:11:28.277 TM - Thermal Monitor                   = 0 (0)
08:11:28.277 30 - Reserved                          = 0 (0)
08:11:28.277 PBE - Pending Break Enable             = 0 (0)
08:11:28.277 Supports SSE3 or not                   = 1 (1)
08:11:28.277 Reserved                               = 0 (0)
08:11:28.277 Supports MONITOR/MWAIT                 = 1 (1)
08:11:28.277 CPL-DS - CPL Qualified Debug Store     = 0 (0)
08:11:28.277 VMX - Virtual Machine Technology       = 0 (0)
08:11:28.277 Reserved                               = 0 (0)
08:11:28.277 Enhanced SpeedStep Technology          = 0 (0)
08:11:28.277 Terminal Monitor 2                     = 0 (0)
08:11:28.277 Supports Supplemental SSE3 or not      = 0 (0)
08:11:28.277 L1 Context ID                          = 0 (0)
08:11:28.277 Reserved                               = 0x0 (0x0)
08:11:28.277 CMPXCHG16B                             = 0 (1)
08:11:28.277 xTPR Update Control                    = 0 (0)
08:11:28.277 Reserved                               = 0x0 (0x100)
08:11:28.277 
08:11:28.277          RAW Extended CPUIDs
08:11:28.277      Function  eax      ebx      ecx      edx
08:11:28.277 Gst: 80000000  80000008 68747541 444d4163 69746e65
08:11:28.277 Hst:           8000001b 68747541 444d4163 69746e65
08:11:28.277 Gst: 80000001  00100f52 10005146 00000000 c383f33f
08:11:28.277 Hst:           00100f52 10005146 000037ff efd3fbff
08:11:28.277 Gst: 80000002  20444d41 6c687441 74286e6f 4920296d
08:11:28.277 Hst:           20444d41 6c687441 74286e6f 4920296d
08:11:28.277 Gst: 80000003  34582049 30323620 6f725020 73736563
08:11:28.277 Hst:           34582049 30323620 6f725020 73736563
08:11:28.277 Gst: 80000004  0000726f 00000000 00000000 00000000
08:11:28.277 Hst:           0000726f 00000000 00000000 00000000
08:11:28.277 Gst: 80000005  ff30ff10 ff30ff20 40020140 40020140
08:11:28.277 Hst:           ff30ff10 ff30ff20 40020140 40020140
08:11:28.277 Gst: 80000006  20800000 42004200 02008140 00000000
08:11:28.277 Hst:           20800000 42004200 02008140 00000000
08:11:28.277 Gst: 80000007  00000000 00000000 00000000 00000100
08:11:28.277 Hst:           00000000 00000000 00000000 000001f9
08:11:28.278 Gst: 80000008  00003030 00000000 00000000 00000000
08:11:28.278 Hst:           00003030 00000000 00002003 00000000
08:11:28.278 Gst: 80000009  00000000 00000000 00000000 00000000*
08:11:28.278 Hst:           00000000 00000000 00000000 00000000
08:11:28.278 Ext Name:                        AuthenticAMD
08:11:28.278 Ext Supports:                    0x80000000-0x80000008
08:11:28.278 Family:                          15  	Extended: 1 	Effective: 16
08:11:28.278 Model:                           5  	Extended: 0 	Effective: 5
08:11:28.278 Stepping:                        2
08:11:28.278 Brand ID:                        0x146
08:11:28.278 Mnemonic - Description                 = guest (host)
08:11:28.278 FPU - x87 FPU on Chip                  = 1 (1)
08:11:28.278 VME - Virtual 8086 Mode Enhancements   = 1 (1)
08:11:28.278 DE - Debugging extensions              = 1 (1)
08:11:28.278 PSE - Page Size Extension              = 1 (1)
08:11:28.278 TSC - Time Stamp Counter               = 1 (1)
08:11:28.278 MSR - K86 Model Specific Registers     = 1 (1)
08:11:28.278 PAE - Physical Address Extension       = 0 (1)
08:11:28.278 MCE - Machine Check Exception          = 0 (1)
08:11:28.278 CX8 - CMPXCHG8B instruction            = 1 (1)
08:11:28.278 APIC - APIC On-Chip                    = 1 (1)
08:11:28.278 10 - Reserved                          = 0 (0)
08:11:28.278 SEP - SYSCALL and SYSRET               = 0 (1)
08:11:28.278 MTRR - Memory Type Range Registers     = 1 (1)
08:11:28.278 PGE - PTE Global Bit                   = 1 (1)
08:11:28.278 MCA - Machine Check Architecture       = 1 (1)
08:11:28.278 CMOV - Conditional Move Instructions   = 1 (1)
08:11:28.278 PAT - Page Attribute Table             = 1 (1)
08:11:28.278 PSE-36 - 36-bit Page Size Extention    = 1 (1)
08:11:28.278 18 - Reserved                          = 0 (0)
08:11:28.278 19 - Reserved                          = 0 (0)
08:11:28.278 NX - No-Execute Page Protection        = 0 (1)
08:11:28.278 DS - Debug Store                       = 0 (0)
08:11:28.278 AXMMX - AMD Extensions to MMX Instr.   = 0 (1)
08:11:28.278 MMX - Intel MMX Technology             = 1 (1)
08:11:28.278 FXSR - FXSAVE and FXRSTOR Instructions = 1 (1)
08:11:28.278 25 - AMD fast FXSAVE and FXRSTOR Instr.= 1 (1)
08:11:28.278 26 - 1 GB large page support           = 0 (1)
08:11:28.278 27 - RDTSCP instruction                = 0 (1)
08:11:28.278 28 - Reserved                          = 0 (0)
08:11:28.278 29 - AMD Long Mode                     = 0 (1)
08:11:28.278 30 - AMD Extensions to 3DNow           = 1 (1)
08:11:28.278 31 - AMD 3DNow                         = 1 (1)
08:11:28.278 LahfSahf - LAHF/SAHF in 64-bit mode    = 0 (1)
08:11:28.278 CmpLegacy - Core MP legacy mode (depr) = 0 (1)
08:11:28.278 SVM - AMD VM Extensions                = 0 (1)
08:11:28.278 APIC registers starting at 0x400       = 0 (1)
08:11:28.278 AltMovCR8 - LOCK MOV CR0 means MOV CR8 = 0 (1)
08:11:28.278 Advanced bit manipulation              = 0 (1)
08:11:28.278 SSE4A instruction support              = 0 (1)
08:11:28.278 Misaligned SSE mode                    = 0 (1)
08:11:28.278 PREFETCH and PREFETCHW instruction     = 0 (1)
08:11:28.278 OS visible workaround                  = 0 (1)
08:11:28.278 Instruction based sampling             = 0 (1)
08:11:28.278 SSE5 support                           = 0 (0)
08:11:28.278 SKINIT, STGI, and DEV support          = 0 (1)
08:11:28.278 Watchdog timer support.                = 0 (1)
08:11:28.278 31:14 - Reserved                       = 0x0 (0x0)
08:11:28.278 Full Name:                       AMD Athlon(tm) II X4 620 Processor
08:11:28.278 TLB 2/4M Instr/Uni:              255 way  16 entries
08:11:28.278 TLB 2/4M Data:                   255 way  48 entries
08:11:28.278 TLB 4K Instr/Uni:                255 way  32 entries
08:11:28.278 TLB 4K Data:                     255 way  48 entries
08:11:28.278 L1 Instr Cache Line Size:        64 bytes
08:11:28.278 L1 Instr Cache Lines Per Tag:    1
08:11:28.278 L1 Instr Cache Associativity:    2 way
08:11:28.278 L1 Instr Cache Size:             64 KB
08:11:28.278 L1 Data Cache Line Size:         64 bytes
08:11:28.278 L1 Data Cache Lines Per Tag:     1
08:11:28.278 L1 Data Cache Associativity:     2 way
08:11:28.278 L1 Data Cache Size:              64 KB
08:11:28.278 L2 TLB 2/4M Instr/Uni:           off       0 entries
08:11:28.278 L2 TLB 2/4M Data:                2 way   128 entries
08:11:28.278 L2 TLB 4K Instr/Uni:             4 way   512 entries
08:11:28.278 L2 TLB 4K Data:                  4 way   512 entries
08:11:28.278 L2 Cache Line Size:              0 bytes
08:11:28.278 L2 Cache Lines Per Tag:          0
08:11:28.278 L2 Cache Associativity:          off   
08:11:28.278 L2 Cache Size:                   0 KB
08:11:28.279 APM Features:                    8
08:11:28.279 Physical Address Width:          48 bits
08:11:28.279 Virtual Address Width:           48 bits
08:11:28.279 Physical Core Count:             0
08:11:28.279 
08:11:28.279          RAW Centaur CPUIDs
08:11:28.279      Function  eax      ebx      ecx      edx
08:11:28.279 Gst: c0000000  00000000 00000000 00000000 00000000
08:11:28.279 Hst:           00000000 00000000 00000000 00000000
08:11:28.279 Gst: c0000001  00000000 00000000 00000000 00000000*
08:11:28.279 Hst:           00000000 00000000 00000000 00000000
08:11:28.279 Gst: c0000002  00000000 00000000 00000000 00000000*
08:11:28.279 Hst:           00000000 00000000 00000000 00000000
08:11:28.279 Gst: c0000003  00000000 00000000 00000000 00000000*
08:11:28.279 Hst:           00000000 00000000 00000000 00000000
08:11:28.279 Centaur Supports:                0xc0000000-0x00000000
08:11:28.279 !!
08:11:28.279 !! {gdt, <NULL>}
08:11:28.279 !!
08:11:28.279 Shadow GDT (GCAddr=eab8b000):
08:11:28.279 0008 - 0000ffff 00cfbb00 - base=00000000 limit=ffffffff dpl=1 CodeER Accessed Present Page 32-bit 
08:11:28.279 0010 - 0000ffff 00cfb300 - base=00000000 limit=ffffffff dpl=1 DataRW Accessed Present Page 32-bit 
08:11:28.279 0018 - 0000ffff 00cffb00 - base=00000000 limit=ffffffff dpl=3 CodeER Accessed Present Page 32-bit 
08:11:28.279 0020 - 0000ffff 00cff300 - base=00000000 limit=ffffffff dpl=3 DataRW Accessed Present Page 32-bit 
08:11:28.279 0030 - f0000001 ffc0b3df - base=ffdff000 limit=00001fff dpl=1 DataRW Accessed Present Page 32-bit 
08:11:28.279 0038 - 00000fff 0040f300 - base=00000000 limit=00000fff dpl=3 DataRW Accessed Present 32-bit 
08:11:28.279 0040 - 0400ffff 0000f300 - base=00000400 limit=0000ffff dpl=3 DataRW Accessed Present 16-bit 
08:11:28.279 0060 - 2f30ffff 0000b302 - base=00022f30 limit=0000ffff dpl=1 DataRW Accessed Present 16-bit 
08:11:28.279 0068 - 80003fff 0000b30b - base=000b8000 limit=00003fff dpl=1 DataRW Accessed Present 16-bit 
08:11:28.279 0070 - 700003ff ff00b3ff - base=ffff7000 limit=000003ff dpl=1 DataRW Accessed Present 16-bit 
08:11:28.279 0078 - 0000ffff 8000bb40 - base=80400000 limit=0000ffff dpl=1 CodeER Accessed Present 16-bit 
08:11:28.279 0080 - 0000ffff 8000b340 - base=80400000 limit=0000ffff dpl=1 DataRW Accessed Present 16-bit 
08:11:28.279 0088 - 00000000 0000b300 - base=00000000 limit=00000000 dpl=1 DataRW Accessed Present 16-bit 
08:11:28.279 00e8 - 0000ffff 0000b300 - base=00000000 limit=0000ffff dpl=1 DataRW Accessed Present 16-bit 
08:11:28.279 00f0 - 8b28cf7b 8003b94d - base=804d8b28 limit=0003cf7b dpl=1 CodeEO Accessed Present 16-bit 
08:11:28.279 00f8 - 0000ffff 0000b300 - base=00000000 limit=0000ffff dpl=1 DataRW Accessed Present 16-bit 
08:11:28.279 ffd8 - 08f80087 ea008941 - base=ea4108f8 limit=00000087 dpl=0 TSS32Avail Present 16-bit  HyperTSSTrap08
08:11:28.279 ffe0 - 08700087 ea008b41 - base=ea410870 limit=00000087 dpl=0 TSS32Busy Present 16-bit  HyperTSS
08:11:28.279 ffe8 - 0000ffff 00af9b00 - base=00000000 limit=ffffffff dpl=0 CodeER Accessed Present Page 16-bit  HyperCS64
08:11:28.279 fff0 - 0000ffff 00cf9300 - base=00000000 limit=ffffffff dpl=0 DataRW Accessed Present Page 32-bit  HyperDS
08:11:28.279 fff8 - 0000ffff 00cf9b00 - base=00000000 limit=ffffffff dpl=0 CodeER Accessed Present Page 32-bit  HyperCS
08:11:28.279 !!
08:11:28.279 !! {ldt, <NULL>}
08:11:28.279 !!
08:11:28.279 Shadow LDT (GCAddr=eab9c000 limit=0x0):
08:11:28.279 !!
08:11:28.279 !! {ioport, <NULL>}
08:11:28.279 !!
08:11:28.279 I/O Port R3 ranges (pVM=b511d000)
08:11:28.279 Range     pDevIns  In       Out      pvUser   Description
08:11:28.279 0000-0000 b22fc958 b1c91b90 b1c91a60 b22fc9e0 DMA
08:11:28.279 0001-0001 b22fc958 b1c91b90 b1c91a60 b22fc9e0 DMA
08:11:28.279 0002-0002 b22fc958 b1c91b90 b1c91a60 b22fc9e0 DMA
08:11:28.279 0003-0003 b22fc958 b1c91b90 b1c91a60 b22fc9e0 DMA
08:11:28.279 0004-0004 b22fc958 b1c91b90 b1c91a60 b22fc9e0 DMA
08:11:28.280 0005-0005 b22fc958 b1c91b90 b1c91a60 b22fc9e0 DMA
08:11:28.280 0006-0006 b22fc958 b1c91b90 b1c91a60 b22fc9e0 DMA
08:11:28.280 0007-0007 b22fc958 b1c91b90 b1c91a60 b22fc9e0 DMA
08:11:28.280 0008-0008 b22fc958 b1c91cb0 b1c91b60 b22fc9e0 DMA cont
08:11:28.280 0009-0009 b22fc958 b1c91cb0 b1c91b60 b22fc9e0 DMA cont
08:11:28.280 000a-000a b22fc958 b1c91cb0 b1c91b60 b22fc9e0 DMA cont
08:11:28.280 000b-000b b22fc958 b1c91cb0 b1c91b60 b22fc9e0 DMA cont
08:11:28.280 000c-000c b22fc958 b1c91cb0 b1c91b60 b22fc9e0 DMA cont
08:11:28.280 000d-000d b22fc958 b1c91cb0 b1c91b60 b22fc9e0 DMA cont
08:11:28.280 000e-000e b22fc958 b1c91cb0 b1c91b60 b22fc9e0 DMA cont
08:11:28.280 000f-000f b22fc958 b1c91cb0 b1c91b60 b22fc9e0 DMA cont
08:11:28.280 0020-0021 b2d52ed0 b1ca8300 b1ca86e0 00000000 i8259 PIC #0
08:11:28.280 0040-0043 b2d539e0 b1ca9260 b1ca9e40 00000000 i8254 Programmable Interval Timer
08:11:28.280 0060-0060 b2d52a40 b1cc06b0 b1cc1a40 00000000 PC Keyboard - Data
08:11:28.280 0061-0061 b2d539e0 b1ca9010 b1ca8f30 00000000 PC Speaker
08:11:28.280 0064-0064 b2d52a40 b1cc0820 b1cc17e0 00000000 PC Keyboard - Command / Status
08:11:28.280 0070-0071 b2d53d30 b1ca41b0 b1ca4970 00000000 MC146818 RTC/CMOS
08:11:28.280 0081-0081 b22fc958 b1c91c30 b1c91ae0 b22fc9e0 DMA Page
08:11:28.280 0082-0082 b22fc958 b1c91c30 b1c91ae0 b22fc9e0 DMA Page
08:11:28.280 0083-0083 b22fc958 b1c91c30 b1c91ae0 b22fc9e0 DMA Page
08:11:28.280 0087-0087 b22fc958 b1c91c30 b1c91ae0 b22fc9e0 DMA Page
08:11:28.280 0089-0089 b22fc958 b1c91c30 b1c91ae0 b22fca58 DMA Page
08:11:28.280 008a-008a b22fc958 b1c91c30 b1c91ae0 b22fca58 DMA Page
08:11:28.280 008b-008b b22fc958 b1c91c30 b1c91ae0 b22fca58 DMA Page
08:11:28.280 008f-008f b22fc958 b1c91c30 b1c91ae0 b22fca58 DMA Page
08:11:28.280 0092-0092 b551ef68 b1ca12b0 b1ca1260 00000000 PS/2 system control port A (A20 and more)
08:11:28.280 00a0-00a1 b2d52ed0 b1ca8300 b1ca86e0 00000001 i8259 PIC #1
08:11:28.280 00c0-00c0 b22fc958 b1c91b90 b1c91a60 b22fca58 DMA
08:11:28.280 00c2-00c2 b22fc958 b1c91b90 b1c91a60 b22fca58 DMA
08:11:28.280 00c4-00c4 b22fc958 b1c91b90 b1c91a60 b22fca58 DMA
08:11:28.280 00c6-00c6 b22fc958 b1c91b90 b1c91a60 b22fca58 DMA
08:11:28.280 00c8-00c8 b22fc958 b1c91b90 b1c91a60 b22fca58 DMA
08:11:28.280 00ca-00ca b22fc958 b1c91b90 b1c91a60 b22fca58 DMA
08:11:28.280 00cc-00cc b22fc958 b1c91b90 b1c91a60 b22fca58 DMA
08:11:28.280 00ce-00ce b22fc958 b1c91b90 b1c91a60 b22fca58 DMA
08:11:28.281 00d0-00d0 b22fc958 b1c91cb0 b1c91b60 b22fca58 DMA cont
08:11:28.283 00d2-00d2 b22fc958 b1c91cb0 b1c91b60 b22fca58 DMA cont
08:11:28.283 00d4-00d4 b22fc958 b1c91cb0 b1c91b60 b22fca58 DMA cont
08:11:28.283 00d6-00d6 b22fc958 b1c91cb0 b1c91b60 b22fca58 DMA cont
08:11:28.283 00d8-00d8 b22fc958 b1c91cb0 b1c91b60 b22fca58 DMA cont
08:11:28.283 00da-00da b22fc958 b1c91cb0 b1c91b60 b22fca58 DMA cont
08:11:28.283 00dc-00dc b22fc958 b1c91cb0 b1c91b60 b22fca58 DMA cont
08:11:28.283 00de-00de b22fc958 b1c91cb0 b1c91b60 b22fca58 DMA cont
08:11:28.283 00f0-00ff b551ef68 b1ca1250 b1ca12e0 00000000 Math Co-Processor (DOS/OS2 mode)
08:11:28.283 0170-0177 b2d655d0 b1caf210 b1cb30e0 00000001 ATA I/O Base 1
08:11:28.283 01ce-01ce b1b49000 b1cb65d0 b1cb64b0 00000000 VGA/VBE - Index
08:11:28.283 01cf-01cf b1b49000 b1cb6530 b1cb8720 00000000 VGA/VBE - Data
08:11:28.283 01f0-01f7 b2d655d0 b1caf210 b1cb30e0 00000000 ATA I/O Base 1
08:11:28.283 02f8-02ff b2d69c00 b1c8e980 b1c8eaf0 00000000 SERIAL
08:11:28.283 0376-0376 b2d655d0 b1cacf20 b1cacff0 00000001 ATA I/O Base 2
08:11:28.283 03b4-03b5 b1b49000 b1cb6430 b1cb8b50 00000000 VGA - 3b4
08:11:28.283 03b6-03b6 b1b49000 b1cb66b0 b1cb6690 00000000 VBE BIOS Extra Data
08:11:28.283 03b7-03b7 b1b49000 b1cb6650 b1cb6660 00000000 VGA BIOS debug/panic
08:11:28.283 03b8-03b8 b1b49000 b1cb6c40 b1cb99c0 00000000 BIOS Logo
08:11:28.283 03ba-03ba b1b49000 b1cb6430 b1cb8b50 00000000 VGA - 3ba
08:11:28.283 03c0-03cf b1b49000 b1cb6430 b1cb8b50 00000000 VGA - 3c0
08:11:28.283 03d4-03d5 b1b49000 b1cb6430 b1cb8b50 00000000 VGA - 3d4
08:11:28.283 03da-03da b1b49000 b1cb6430 b1cb8b50 00000000 VGA - 3da
08:11:28.283 03f1-03f5 b2200028 b1c8fd60 b1c902a0 b22000a8 FDC#1
08:11:28.283 03f6-03f6 b2d655d0 b1cacf20 b1cacff0 00000000 ATA I/O Base 2
08:11:28.283 03f7-03f7 b2200028 b1c8fd60 b1c902a0 b22000a8 FDC#2
08:11:28.283 03f8-03ff b2d699d0 b1c8e980 b1c8eaf0 00000000 SERIAL
08:11:28.283 0400-0403 b22f6018 b1ca1590 b1ca2380 00000000 Bochs PC BIOS - Panic & Debug
08:11:28.283 04d0-04d0 b2d52ed0 b1ca76a0 b1ca7710 b2d52f50 i8259 PIC #0 - elcr
08:11:28.283 04d1-04d1 b2d52ed0 b1ca76a0 b1ca7710 b2d52f70 i8259 PIC #1 - elcr
08:11:28.283 0504-0504 b55204d8 b5712c50 b1c9ed30 00000000 VMMDev backdoor logging
08:11:28.283 0505-0505 b55204d8 b1c9f510 b1c9e640 00000000 VMMDev timesync backdoor
08:11:28.283 0cf8-0cf8 b2d51f10 b1cbe4a0 b1cbe430 00000000 i440FX (PCI)
08:11:28.284 0cfc-0cff b2d51f10 b1cbe590 b1cbe510 00000000 i440FX (PCI)
08:11:28.284 8900-8900 b22f6018 b1ca1590 b1ca2380 00000000 Bochs PC BIOS - Shutdown
08:11:28.284 c000-c007 b2d655d0 b1cad510 b1cad380 00000000 ATA Bus Master DMA
08:11:28.284 c008-c00f b2d655d0 b1cad510 b1cad380 00000001 ATA Bus Master DMA
08:11:28.284 c020-c02f b2d667b0 b1c978e0 b1c97870 00000000 PCNet ARPOM
08:11:28.284 c030-c03f b2d667b0 b1c9a100 b1c9ae20 00000000 PCNet
08:11:28.284 c040-c040 b55204d8 b5712c50 b1c9fd10 b5520558 VMMDev Request Handler
08:11:28.284 c100-c1ff b5596018 b1c95290 b1c95c10 b5596098 ICHAC97 NAM
08:11:28.284 c200-c23f b5596018 b1c95080 b1c95430 b5596098 ICHAC97 NABM
08:11:28.284 I/O Port R0 ranges (pVM=b511d000)
08:11:28.284 Range     pDevIns  In       Out      pvUser   Description
08:11:28.284 0020-0021 b2d52ed0 f9c2db90 f9c2dfd0 00000000 i8259 PIC #0
08:11:28.284 0040-0043 b2d539e0 f9c2d6d0 f9c2d7e0 00000000 i8254 Programmable Interval Timer
08:11:28.284 0060-0060 b2d52a40 f9c2c7c0 f9c2c960 00000000 PC Keyboard - Data
08:11:28.284 0064-0064 b2d52a40 f9c2c930 f9c2d030 00000000 PC Keyboard - Command / Status
08:11:28.284 0070-0071 b2d53d30 f9c2e3c0 f9c2e8e0 00000000 MC146818 RTC/CMOS
08:11:28.284 00a0-00a1 b2d52ed0 f9c2db90 f9c2dfd0 00000001 i8259 PIC #1
08:11:28.284 0170-0177 b2d655d0 f9c2f840 f9c2f4a0 00000001 ATA I/O Base 1
08:11:28.284 01ce-01ce b1b49000 f9c2aa30 f9c2a910 00000000 VGA/VBE - Index (GC)
08:11:28.284 01cf-01cf b1b49000 f9c2a990 f9c2b8e0 00000000 VGA/VBE - Data (GC)
08:11:28.284 01f0-01f7 b2d655d0 f9c2f840 f9c2f4a0 00000000 ATA I/O Base 1
08:11:28.284 02f8-02ff b2d69c00 f9c319d0 f9c31af0 00000000 Serial
08:11:28.284 0376-0376 b2d655d0 f9c2f030 f9c2f100 00000001 ATA I/O Base 2
08:11:28.284 03b4-03b5 b1b49000 f9c2a890 f9c2bc90 00000000 VGA - 3b4 (GC)
08:11:28.284 03b7-03b7 b1b49000 f9c2aab0 f9c2aac0 00000000 VGA BIOS debug/panic
08:11:28.284 03ba-03ba b1b49000 f9c2a890 f9c2bc90 00000000 VGA - 3ba (GC)
08:11:28.284 03c0-03cf b1b49000 f9c2a890 f9c2bc90 00000000 VGA - 3c0 (GC)
08:11:28.284 03d4-03d5 b1b49000 f9c2a890 f9c2bc90 00000000 VGA - 3d4 (GC)
08:11:28.284 03da-03da b1b49000 f9c2a890 f9c2bc90 00000000 VGA - 3da (GC)
08:11:28.284 03f6-03f6 b2d655d0 f9c2f030 f9c2f100 00000000 ATA I/O Base 2
08:11:28.284 03f8-03ff b2d699d0 f9c319d0 f9c31af0 00000000 Serial
08:11:28.284 04d0-04d0 b2d52ed0 f9c2da00 f9c2da70 b2d52f50 i8259 PIC #0 - elcr
08:11:28.284 04d1-04d1 b2d52ed0 f9c2da00 f9c2da70 b2d52f70 i8259 PIC #1 - elcr
08:11:28.284 0cf8-0cf8 b2d51f10 f9c2a470 f9c2a400 00000000 i440FX (PCI)
08:11:28.284 0cfc-0cff b2d51f10 f9c2a580 f9c2a4e0 00000000 i440FX (PCI)
08:11:28.284 c000-c007 b2d655d0 f9c2f390 f9c2f260 00000000 ATA Bus Master DMA
08:11:28.284 c008-c00f b2d655d0 f9c2f390 f9c2f260 00000001 ATA Bus Master DMA
08:11:28.284 c020-c02f b2d667b0 f9c30000 f9c2ff90 00000000 PCNet aprom
08:11:28.285 c030-c03f b2d667b0 f9c30fb0 f9c31710 00000000 PCNet
08:11:28.285 I/O Port GC ranges (pVM=b511d000)
08:11:28.285 Range     pDevIns  In       Out      pvUser   Description
08:11:28.285 0020-0021 ea433ed0 eae0ba40 eae0be80 00000000 i8259 PIC #0
08:11:28.285 0040-0043 ea4349e0 eae0b580 eae0b690 00000000 i8254 Programmable Interval Timer
08:11:28.285 0060-0060 ea433a40 eae0a670 eae0a810 00000000 PC Keyboard - Data
08:11:28.285 0061-0061 ea4349e0 eae0b330 00000000 00000000 PC Speaker
08:11:28.285 0064-0064 ea433a40 eae0a7e0 eae0aee0 00000000 PC Keyboard - Command / Status
08:11:28.285 0070-0071 ea434d30 eae0c270 eae0c790 00000000 MC146818 RTC/CMOS
08:11:28.285 00a0-00a1 ea433ed0 eae0ba40 eae0be80 00000001 i8259 PIC #1
08:11:28.285 0170-0177 ea4465d0 eae0d990 eae0d5f0 00000001 ATA I/O Base 1
08:11:28.285 01ce-01ce eae1a000 eae08d50 eae08c30 00000000 VGA/VBE - Index (GC)
08:11:28.285 01cf-01cf eae1a000 eae08cb0 eae08b70 00000000 VGA/VBE - Data (GC)
08:11:28.285 01f0-01f7 ea4465d0 eae0d990 eae0d5f0 00000000 ATA I/O Base 1
08:11:28.285 02f8-02ff ea44ac00 eae0fb20 eae0fc40 00000000 Serial
08:11:28.285 0376-0376 ea4465d0 eae0cee0 eae0cfb0 00000001 ATA I/O Base 2
08:11:28.285 03b4-03b5 eae1a000 eae08af0 eae09ae0 00000000 VGA - 3b4 (GC)
08:11:28.285 03ba-03ba eae1a000 eae08af0 eae09ae0 00000000 VGA - 3ba (GC)
08:11:28.285 03c0-03cf eae1a000 eae08af0 eae09ae0 00000000 VGA - 3c0 (GC)
08:11:28.285 03d4-03d5 eae1a000 eae08af0 eae09ae0 00000000 VGA - 3d4 (GC)
08:11:28.285 03da-03da eae1a000 eae08af0 eae09ae0 00000000 VGA - 3da (GC)
08:11:28.285 03f6-03f6 ea4465d0 eae0cee0 eae0cfb0 00000000 ATA I/O Base 2
08:11:28.285 03f8-03ff ea44a9d0 eae0fb20 eae0fc40 00000000 Serial
08:11:28.285 04d0-04d0 ea433ed0 eae0b8b0 eae0b920 ea433f50 i8259 PIC #0 - elcr
08:11:28.285 04d1-04d1 ea433ed0 eae0b8b0 eae0b920 ea433f70 i8259 PIC #1 - elcr
08:11:28.285 0cf8-0cf8 ea432f10 eae08410 eae083a0 00000000 i440FX (PCI)
08:11:28.285 0cfc-0cff ea432f10 eae08520 eae08480 00000000 i440FX (PCI)
08:11:28.285 c000-c007 ea4465d0 eae0d240 eae0d110 00000000 ATA Bus Master DMA
08:11:28.285 c008-c00f ea4465d0 eae0d240 eae0d110 00000001 ATA Bus Master DMA
08:11:28.285 c020-c02f ea4477b0 eae0e150 eae0e0e0 00000000 PCNet aprom
08:11:28.285 c030-c03f ea4477b0 eae0f100 eae0f860 00000000 PCNet
08:11:28.285 RC Read  Ports: 0x70-0x72 ea435000 MC146818 RTC/CMOS
08:11:28.285 RC Write Ports: 0x70-0x72 ea435000 MC146818 RTC/CMOS
08:11:28.285 R3 Read  Ports: 0x70-0x72 b2d53fc0 MC146818 RTC/CMOS
08:11:28.286 R3 Write Ports: 0x70-0x72 b2d53fc0 MC146818 RTC/CMOS
08:11:28.286 !!
08:11:28.286 !! {mmio, <NULL>}
08:11:28.286 !!
08:11:28.286 MMIO ranges (pVM=b511d000)
08:11:28.286 GC Phys Range                     pDevIns  Read     Write    Fill     pvUser   Description
08:11:28.286 00000000000a0000-00000000000bffff b1b49000 b1cb96c0 b1cb9300 b1cb9c70 00000000 VGA - VGA Video Buffer
08:11:28.286                                R0 b1b49000 f9c2b330 f9c2af70 f9c2bd10 00000000
08:11:28.286                                RC eae1a000 eae094b0 eae09150 eae09b60 00000000
08:11:28.286 00000000f0000000-00000000f0000fff b2d667b0 b1c9a220 b1c9af00 00000000 b2d66830 PCNet
08:11:28.286                                R0 00000000 00000000 00000000 00000000 00000000
08:11:28.286                                RC 00000000 00000000 00000000 00000000 00000000
08:11:28.286 00000000fec00000-00000000fec00fff b2d53720 b2411710 b2411880 00000000 b2d537a0 I/O APIC Memory
08:11:28.286                                R0 b2d53720 f9c48540 f9c48650 00000000 00000000
08:11:28.286                                RC ea434720 eae164e0 eae165f0 00000000 00000000
08:11:28.286 00000000fee00000-00000000fee00fff b2d532c0 b2413b30 b2413d50 00000000 b2d53340 APIC Memory
08:11:28.286                                R0 b2d532c0 f9c49a70 f9c49800 00000000 00000000
08:11:28.286                                RC ea4342c0 eae17a10 eae177a0 00000000 00000000
08:11:28.286 !!
08:11:28.286 !! {phys, <NULL>}
08:11:28.286 !!
08:11:28.286 RAM ranges (pVM=b511d000)
08:11:28.286 GC Phys Range                     pvHC    
08:11:28.286 0000000000000000-000000005dbfffff 00000000 Base RAM
08:11:28.286 00000000e0000000-00000000e0bfffff b0a00000 VRam
08:11:28.286 00000000f0000000-00000000f0000fff 00000000 PCNet
08:11:28.286 00000000f0080000-00000000f00fffff b080c000 PCNetShMem
08:11:28.286 00000000f0400000-00000000f07fffff b1600000 VMMDev
08:11:28.286 00000000f0800000-00000000f0803fff b3083000 VMMDev Heap
08:11:28.286 00000000fec00000-00000000fec00fff 00000000 I/O APIC Memory
08:11:28.286 00000000fee00000-00000000fee00fff 00000000 APIC Memory
08:11:28.286 00000000fff80000-00000000ffffffff b1bf2000 <NULL>
08:11:28.286 !!
08:11:28.286 !! {timers, <NULL>}
08:11:28.286 !!
08:11:28.286 Timers (pVM=b511d000)
08:11:28.286 pTimerR3 offNext  offPrev  offSched Clock Time               Expire             State                     Description
08:11:28.287 b2d6a580 00000000 ffffaeb0 00000000 Real  000000000081250068 000000000081250016 ACTIVE                    EMT Yielder
08:11:28.287 b2d69980 00000000 00000000 00000000 Virt  000029483028156277 000029483038135013 ACTIVE                    Audio timer
08:11:28.287 b2d696d0 00000000 00000000 00000000 Virt  000029483028156277 000000000000000000 STOPPED                   PCNet Restore Timer
08:11:28.287 b2d69680 00000000 00000000 00000000 Virt  000029483028156277 000000000000000000 STOPPED                   PCNet SoftInt Timer
08:11:28.287 b2d69630 00000000 00000000 00000000 Virt  000029483028156277 000000000000000000 STOPPED                   PCNet Poll Timer
08:11:28.287 b2d65500 00000000 00000000 00000000 Virt  000029483028156277 000000000000000000 STOPPED                   FDC Timer
08:11:28.287 b2d65430 00005150 00000000 00000000 Real  000000000081250068 000000000081250013 ACTIVE                    VGA Refresh Timer
08:11:28.287 b2d53f70 00000000 00000000 00000000 Virt  000029483005247373 000029482990244140 STOPPED                   MC146818 RTC/CMOS - Second2
08:11:28.287 b2d53f20 00000000 fffffc80 00000000 Virt  000029483005247373 000029483990000000 ACTIVE                    MC146818 RTC/CMOS - Second
08:11:28.287 b2d53ed0 00000000 00000000 00000000 Virt  000029483005247373 000029467343750001 STOPPED                   MC146818 RTC/CMOS - Periodic
08:11:28.287 b2d53ba0 00000380 00000000 00000000 Virt  000029483005247373 000029483060172774 ACTIVE                    i8254 Programmable Interval Timer
08:11:28.287 b2d536d0 00000000 00000000 00000000 Virt  000029483005247373 000000000000000000 STOPPED                   APIC Timer
08:11:28.288 b2d51950 00000000 00000000 00000000 Virt  000029483028156277 000000000000000000 STOPPED                   PDM Poller
08:11:28.288 !!
08:11:28.288 !! {activetimers, <NULL>}
08:11:28.288 !!
08:11:28.288 Active Timers (pVM=b511d000)
08:11:28.288 pTimerR3 offNext  offPrev  offSched Clock Time               Expire             State                     Description
08:11:28.288 b2d65430 00005150 00000000 00000000 Real  000000000081250069 000000000081250013 ACTIVE                    VGA Refresh Timer
08:11:28.288 b2d6a580 00000000 ffffaeb0 00000000 Real  000000000081250069 000000000081250016 ACTIVE                    EMT Yielder
08:11:28.288 b2d69980 00000000 00000000 00000000 Virt  000029483028156277 000029483038135013 ACTIVE                    Audio timer
08:11:28.288 b2d53ba0 00000380 00000000 00000000 VrSy  000029483005247373 000029483060172774 ACTIVE                    i8254 Programmable Interval Timer
08:11:28.288 b2d53f20 00000000 fffffc80 00000000 VrSy  000029483005247373 000029483990000000 ACTIVE                    MC146818 RTC/CMOS - Second
08:11:28.288 !!
08:11:28.288 !! {handlers, phys virt hyper stats}
08:11:28.288 !!
08:11:28.288 Physical handlers: (PhysHandlers=40032 (0x9c60))
08:11:28.288 From     - To (incl) HandlerHC UserHC    HandlerGC UserGC    Type     Description
08:11:28.288 0000000000039000 - 0000000000039fff  b56f5f70  b2c71128  eade4850  ea570128  Write    Guest Paging Access Handler
08:11:28.288 000000000003a000 - 000000000003afff  b56f5f70  b2c713f8  eade4850  ea5703f8  Write    Guest Paging Access Handler
08:11:28.288 000000000003b000 - 000000000003bfff  b56f5f70  b2c71488  eade4850  ea570488  Write    Guest Paging Access Handler
08:11:28.288 000000000003d000 - 000000000003dfff  b56f5f70  b2c713b0  eade4850  ea5703b0  Write    Guest Paging Access Handler
08:11:28.288 000000000004f000 - 000000000004ffff  b56f5f70  b2c714d0  eade4850  ea5704d0  Write    Guest Paging Access Handler
08:11:28.288 00000000000a0000 - 00000000000bffff  b56d7e60  b2d65260  eadbeec0  ea446260  MMIO     VGA - VGA Video Buffer
08:11:28.288 00000000000c0000 - 00000000000c8fff  00000000  00000000  eaddf7b0  00000000  Write    VGA BIOS
08:11:28.288 00000000000e1000 - 00000000000e1fff  00000000  00000000  eaddf7b0  00000000  Write    DMI tables
08:11:28.288 00000000000e2000 - 00000000000e6fff  00000000  00000000  eaddf7b0  00000000  Write    Net Boot ROM
08:11:28.288 00000000000f0000 - 00000000000fffff  00000000  00000000  eaddf7b0  00000000  Write    PC BIOS - 0xfffff
08:11:28.288 00000000e0000000 - 00000000e0bfffff  b1cb8c80  b1b49080  eae09770  eae1a080  Write    VGA LFB
08:11:28.289 00000000f0000000 - 00000000f0000fff  b56d7e60  b2d6a190  eadbeec0  ea44b190  MMIO     PCNet
08:11:28.289 00000000fec00000 - 00000000fec00fff  b56d7e60  b2d53890  eadbeec0  ea434890  MMIO     I/O APIC Memory
08:11:28.289 00000000fee00000 - 00000000fee00fff  b56d7e60  b2d53580  eadbeec0  ea434580  MMIO     APIC Memory
08:11:28.289 00000000ffff0000 - 00000000ffffffff  00000000  00000000  eaddf7b0  00000000  Write    PC BIOS - 0xffffffff
08:11:28.289 Virtual handlers:
08:11:28.289 From     - To (excl) HandlerHC HandlerGC Type     Description
08:11:28.289 000000008003f000 - 000000008003f3ff  b56f4e30  eadb6730  Write    Guest GDT write access handler
08:11:28.289 000000008003f400 - 000000008003fbff  b56e8520  eadb6b00  Write    Guest IDT write access handler
08:11:28.289 0000000080042000 - 0000000080042087  b56f4df0  eadb6810  Write    Guest TSS write access handler
08:11:28.289 00000000804d9000 - 00000000804d9fff  b572f1c0  eade94f0  Write    CSAM-PATM self-modifying code monitor handler
08:11:28.289 00000000804db000 - 00000000804dbfff  b572f1c0  eade94f0  Write    CSAM-PATM self-modifying code monitor handler
08:11:28.289 00000000804dc000 - 00000000804dcfff  b572f1c0  eade94f0  Write    CSAM-PATM self-modifying code monitor handler
08:11:28.289 00000000804de000 - 00000000804defff  b572f1c0  eade94f0  Write    CSAM-PATM self-modifying code monitor handler
08:11:28.289 00000000804df000 - 00000000804dffff  b572f1c0  eade94f0  Write    CSAM-PATM self-modifying code monitor handler
08:11:28.289 00000000804e0000 - 00000000804e0fff  b572f1c0  eade94f0  Write    CSAM-PATM self-modifying code monitor handler
08:11:28.289 00000000804e1000 - 00000000804e1fff  b572f1c0  eade94f0  Write    CSAM-PATM self-modifying code monitor handler
08:11:28.289 00000000804e2000 - 00000000804e2fff  b572f1c0  eade94f0  Write    CSAM-PATM self-modifying code monitor handler
08:11:28.289 00000000804e3000 - 00000000804e3fff  b572f1c0  eade94f0  Write    CSAM-PATM self-modifying code monitor handler
08:11:28.289 00000000804e4000 - 00000000804e4fff  b572f1c0  eade94f0  Write    CSAM-PATM self-modifying code monitor handler
08:11:28.289 00000000804e5000 - 00000000804e5fff  b572f1c0  eade94f0  Write    CSAM-PATM self-modifying code monitor handler
08:11:28.289 00000000804ea000 - 00000000804eafff  b572f1c0  eade94f0  Write    CSAM-PATM self-modifying code monitor handler
08:11:28.289 00000000804ef000 - 00000000804effff  b572f1c0  eade94f0  Write    CSAM-PATM self-modifying code monitor handler
08:11:28.289 00000000804f1000 - 00000000804f1fff  b572f1c0  eade94f0  Write    CSAM-PATM self-modifying code monitor handler
08:11:28.289 00000000804f5000 - 00000000804f5fff  b572f1c0  eade94f0  Write    CSAM-PATM self-modifying code monitor handler
08:11:28.289 00000000804fb000 - 00000000804fbfff  b572f1c0  eade94f0  Write    CSAM-PATM self-modifying code monitor handler
08:11:28.289 000000008050c000 - 000000008050cfff  b572f1c0  eade94f0  Write    CSAM-PATM self-modifying code monitor handler
08:11:28.289 0000000080511000 - 0000000080511fff  b572f1c0  eade94f0  Write    CSAM-PATM self-modifying code monitor handler
08:11:28.289 0000000080516000 - 0000000080516fff  b572f1c0  eade94f0  Write    CSAM-PATM self-modifying code monitor handler
08:11:28.289 0000000080527000 - 0000000080527fff  b572f1c0  eade94f0  Write    CSAM-PATM self-modifying code monitor handler
08:11:28.289 0000000080534000 - 0000000080534fff  b572f1c0  eade94f0  Write    CSAM-PATM self-modifying code monitor handler
08:11:28.290 00000000806ec000 - 00000000806ecfff  b572f1c0  eade94f0  Write    CSAM-PATM self-modifying code monitor handler
08:11:28.290 00000000806ee000 - 00000000806eefff  b572f1c0  eade94f0  Write    CSAM-PATM self-modifying code monitor handler
08:11:28.290 00000000806f1000 - 00000000806f1fff  b572f1c0  eade94f0  Write    CSAM-PATM self-modifying code monitor handler
08:11:28.290 0000000080701000 - 0000000080701fff  b572f1c0  eade94f0  Write    CSAM-PATM self-modifying code monitor handler
08:11:28.290 000000008070a000 - 000000008070afff  b572f1c0  eade94f0  Write    CSAM-PATM self-modifying code monitor handler
08:11:28.290 Hypervisor Virtual handlers:
08:11:28.290 From     - To (excl) HandlerHC HandlerGC Type     Description
08:11:28.290 00000000ea40f390 - 00000000ea40fb8f  00000000  eadb69d0  WriteHyp   Shadow IDT write access handler
08:11:28.290 00000000ea410870 - 00000000ea4108f7  00000000  eadb6430  WriteHyp   Shadow TSS write access handler
08:11:28.290 00000000eab8b000 - 00000000eab9afff  00000000  eadb6550  WriteHyp   Shadow GDT write access handler
08:11:28.290 00000000eab9c000 - 00000000eabacfff  00000000  eadb64c0  WriteHyp   Shadow LDT write access handler
08:11:28.290 !!
08:11:28.290 !! {cfgm, <NULL>}
08:11:28.290 !!
08:11:28.290 pRoot=09a20570:{/}
08:11:28.290 [/] (level 0)
08:11:28.290   Name               <string>  = "Windows" (cch=8)
08:11:28.290   UUID               <bytes>   = "6a c7 1f e6 44 c5 a4 4d a8 5b f0 bf de 9a 88 4b" (cb=16)
08:11:28.290   RamSize            <integer> = 0x000000005dc00000 (1572864000)
08:11:28.290   NumCPUs            <integer> = 0x0000000000000001 (1)
08:11:28.290   TimerMillies       <integer> = 0x000000000000000a (10)
08:11:28.290   RawR3Enabled       <integer> = 0x0000000000000001 (1)
08:11:28.290   RawR0Enabled       <integer> = 0x0000000000000001 (1)
08:11:28.290   PATMEnabled        <integer> = 0x0000000000000001 (1)
08:11:28.290   CSAMEnabled        <integer> = 0x0000000000000001 (1)
08:11:28.290   HwVirtExtForced    <integer> = 0x0000000000000000 (0)
08:11:28.290   EnableNestedPaging <integer> = 0x0000000000000000 (0)
08:11:28.290   EnableVPID         <integer> = 0x0000000000000000 (0)
08:11:28.290   EnablePAE          <integer> = 0x0000000000000000 (0)
08:11:28.290 
08:11:28.290 [/HWVirtExt/] (level 1)
08:11:28.290   Enabled      <integer> = 0x0000000000000001 (1)
08:11:28.290   64bitEnabled <integer> = 0x0000000000000000 (0)
08:11:28.290 
08:11:28.290 [/PDM/] (level 1)
08:11:28.290 
08:11:28.290 [/PDM/Drivers/] (level 2)
08:11:28.290 
08:11:28.290 [/PDM/Drivers/VBoxC/] (level 3)
08:11:28.291   Path <string>  = "/usr/lib/virtualbox/components/VBoxC" (cch=37)
08:11:28.291 
08:11:28.291 [/Devices/] (level 1)
08:11:28.291 
08:11:28.291 [/Devices/pcarch/] (level 2)
08:11:28.291 
08:11:28.291 [/Devices/pcarch/0/] (level 3)
08:11:28.291   Trusted <integer> = 0x0000000000000001 (1)
08:11:28.291 
08:11:28.291 [/Devices/pcarch/0/Config/] (level 4) (restricted root)
08:11:28.291 
08:11:28.291 [/Devices/pcbios/] (level 2)
08:11:28.291 
08:11:28.291 [/Devices/pcbios/0/] (level 3)
08:11:28.291   Trusted <integer> = 0x0000000000000001 (1)
08:11:28.291 
08:11:28.291 [/Devices/pcbios/0/Config/] (level 4) (restricted root)
08:11:28.291   RamSize        <integer> = 0x000000005dc00000 (1572864000)
08:11:28.291   NumCPUs        <integer> = 0x0000000000000001 (1)
08:11:28.291   HardDiskDevice <string>  = "piix3ide" (cch=9)
08:11:28.291   FloppyDevice   <string>  = "i82078" (cch=7)
08:11:28.291   IOAPIC         <integer> = 0x0000000000000001 (1)
08:11:28.291   PXEDebug       <integer> = 0x0000000000000000 (0)
08:11:28.291   UUID           <bytes>   = "6a c7 1f e6 44 c5 a4 4d a8 5b f0 bf de 9a 88 4b" (cb=16)
08:11:28.291   BootDevice0    <string>  = "FLOPPY" (cch=7)
08:11:28.291   BootDevice1    <string>  = "DVD" (cch=4)
08:11:28.291   BootDevice2    <string>  = "IDE" (cch=4)
08:11:28.291   BootDevice3    <string>  = "NONE" (cch=5)
08:11:28.291 
08:11:28.291 [/Devices/8237A/] (level 2)
08:11:28.291 
08:11:28.291 [/Devices/8237A/0/] (level 3)
08:11:28.291   Trusted <integer> = 0x0000000000000001 (1)
08:11:28.291 
08:11:28.291 [/Devices/8237A/0/Config/] (level 4) (restricted root)
08:11:28.291 
08:11:28.291 [/Devices/pci/] (level 2)
08:11:28.291 
08:11:28.291 [/Devices/pci/0/] (level 3)
08:11:28.291   Trusted <integer> = 0x0000000000000001 (1)
08:11:28.291 
08:11:28.291 [/Devices/pci/0/Config/] (level 4) (restricted root)
08:11:28.291   IOAPIC <integer> = 0x0000000000000001 (1)
08:11:28.291 
08:11:28.291 [/Devices/pckbd/] (level 2)
08:11:28.291 
08:11:28.291 [/Devices/pckbd/0/] (level 3)
08:11:28.291   Trusted <integer> = 0x0000000000000001 (1)
08:11:28.291 
08:11:28.291 [/Devices/pckbd/0/Config/] (level 4) (restricted root)
08:11:28.291 
08:11:28.291 [/Devices/pckbd/0/LUN#0/] (level 4)
08:11:28.291   Driver <string>  = "KeyboardQueue" (cch=14)
08:11:28.291 
08:11:28.291 [/Devices/pckbd/0/LUN#0/Config/] (level 5) (restricted root)
08:11:28.291   QueueSize <integer> = 0x0000000000000040 (64)
08:11:28.291 
08:11:28.291 [/Devices/pckbd/0/LUN#0/AttachedDriver/] (level 5)
08:11:28.291   Driver <string>  = "MainKeyboard" (cch=13)
08:11:28.291 
08:11:28.291 [/Devices/pckbd/0/LUN#0/AttachedDriver/Config/] (level 6) (restricted root)
08:11:28.291   Object <integer> = 0x00000000b5500a28 (3041921576)
08:11:28.291 
08:11:28.291 [/Devices/pckbd/0/LUN#1/] (level 4)
08:11:28.291   Driver <string>  = "MouseQueue" (cch=11)
08:11:28.291 
08:11:28.291 [/Devices/pckbd/0/LUN#1/Config/] (level 5) (restricted root)
08:11:28.291   QueueSize <integer> = 0x0000000000000080 (128)
08:11:28.291 
08:11:28.291 [/Devices/pckbd/0/LUN#1/AttachedDriver/] (level 5)
08:11:28.291   Driver <string>  = "MainMouse" (cch=10)
08:11:28.291 
08:11:28.291 [/Devices/pckbd/0/LUN#1/AttachedDriver/Config/] (level 6) (restricted root)
08:11:28.291   Object <integer> = 0x00000000b5500b00 (3041921792)
08:11:28.291 
08:11:28.291 [/Devices/i82078/] (level 2)
08:11:28.291 
08:11:28.291 [/Devices/i82078/0/] (level 3)
08:11:28.291   Trusted <integer> = 0x0000000000000001 (1)
08:11:28.291 
08:11:28.291 [/Devices/i82078/0/Config/] (level 4) (restricted root)
08:11:28.291   IRQ       <integer> = 0x0000000000000006 (6)
08:11:28.291   DMA       <integer> = 0x0000000000000002 (2)
08:11:28.291   MemMapped <integer> = 0x0000000000000000 (0)
08:11:28.291   IOBase    <integer> = 0x00000000000003f0 (1008)
08:11:28.291 
08:11:28.291 [/Devices/i82078/0/LUN#999/] (level 4)
08:11:28.291   Driver <string>  = "MainStatus" (cch=11)
08:11:28.291 
08:11:28.291 [/Devices/i82078/0/LUN#999/Config/] (level 5) (restricted root)
08:11:28.291   papLeds <integer> = 0x00000000b550067c (3041920636)
08:11:28.291   First   <integer> = 0x0000000000000000 (0)
08:11:28.291   Last    <integer> = 0x0000000000000000 (0)
08:11:28.291 
08:11:28.291 [/Devices/i82078/0/LUN#0/] (level 4)
08:11:28.291   Driver <string>  = "HostFloppy" (cch=11)
08:11:28.291 
08:11:28.291 [/Devices/i82078/0/LUN#0/Config/] (level 5) (restricted root)
08:11:28.291   Path <string>  = "/dev/sdb" (cch=9)
08:11:28.291 
08:11:28.291 [/Devices/i8254/] (level 2)
08:11:28.291 
08:11:28.291 [/Devices/i8254/0/] (level 3)
08:11:28.291 
08:11:28.291 [/Devices/i8254/0/Config/] (level 4) (restricted root)
08:11:28.291 
08:11:28.291 [/Devices/i8259/] (level 2)
08:11:28.291 
08:11:28.291 [/Devices/i8259/0/] (level 3)
08:11:28.291   Trusted <integer> = 0x0000000000000001 (1)
08:11:28.291 
08:11:28.291 [/Devices/i8259/0/Config/] (level 4) (restricted root)
08:11:28.291 
08:11:28.291 [/Devices/apic/] (level 2)
08:11:28.291 
08:11:28.291 [/Devices/apic/0/] (level 3)
08:11:28.291   Trusted <integer> = 0x0000000000000001 (1)
08:11:28.291 
08:11:28.291 [/Devices/apic/0/Config/] (level 4) (restricted root)
08:11:28.291   IOAPIC  <integer> = 0x0000000000000001 (1)
08:11:28.291   NumCPUs <integer> = 0x0000000000000001 (1)
08:11:28.291 
08:11:28.291 [/Devices/ioapic/] (level 2)
08:11:28.291 
08:11:28.291 [/Devices/ioapic/0/] (level 3)
08:11:28.291   Trusted <integer> = 0x0000000000000001 (1)
08:11:28.291 
08:11:28.291 [/Devices/ioapic/0/Config/] (level 4) (restricted root)
08:11:28.291 
08:11:28.291 [/Devices/mc146818/] (level 2)
08:11:28.291 
08:11:28.291 [/Devices/mc146818/0/] (level 3)
08:11:28.291 
08:11:28.291 [/Devices/mc146818/0/Config/] (level 4) (restricted root)
08:11:28.291 
08:11:28.291 [/Devices/vga/] (level 2)
08:11:28.291 
08:11:28.291 [/Devices/vga/0/] (level 3)
08:11:28.291   Trusted       <integer> = 0x0000000000000001 (1)
08:11:28.291   PCIDeviceNo   <integer> = 0x0000000000000002 (2)
08:11:28.291   PCIFunctionNo <integer> = 0x0000000000000000 (0)
08:11:28.291 
08:11:28.291 [/Devices/vga/0/Config/] (level 4) (restricted root)
08:11:28.291   VRamSize         <integer> = 0x0000000000c00000 (12582912)
08:11:28.295   FadeIn           <integer> = 0x0000000000000001 (1)
08:11:28.295   FadeOut          <integer> = 0x0000000000000001 (1)
08:11:28.295   LogoTime         <integer> = 0x0000000000000000 (0)
08:11:28.295   LogoFile         <string>  = "" (cch=1)
08:11:28.295   ShowBootMenu     <integer> = 0x0000000000000002 (2)
08:11:28.295   CustomVideoModes <integer> = 0x0000000000000000 (0)
08:11:28.295   HeightReduction  <integer> = 0x0000000000000000 (0)
08:11:28.295 
08:11:28.295 [/Devices/vga/0/LUN#0/] (level 4)
08:11:28.295   Driver <string>  = "MainDisplay" (cch=12)
08:11:28.295 
08:11:28.295 [/Devices/vga/0/LUN#0/Config/] (level 5) (restricted root)
08:11:28.295   Object <integer> = 0x00000000b5500bd8 (3041922008)
08:11:28.295 
08:11:28.295 [/Devices/piix3ide/] (level 2)
08:11:28.295 
08:11:28.295 [/Devices/piix3ide/0/] (level 3)
08:11:28.295   Trusted       <integer> = 0x0000000000000001 (1)
08:11:28.295   PCIDeviceNo   <integer> = 0x0000000000000001 (1)
08:11:28.295   PCIFunctionNo <integer> = 0x0000000000000001 (1)
08:11:28.295 
08:11:28.295 [/Devices/piix3ide/0/Config/] (level 4) (restricted root)
08:11:28.295   PIIX4 <integer> = 0x0000000000000001 (1)
08:11:28.295 
08:11:28.295 [/Devices/piix3ide/0/LUN#999/] (level 4)
08:11:28.295   Driver <string>  = "MainStatus" (cch=11)
08:11:28.295 
08:11:28.295 [/Devices/piix3ide/0/LUN#999/Config/] (level 5) (restricted root)
08:11:28.295   papLeds <integer> = 0x00000000b5500684 (3041920644)
08:11:28.295   First   <integer> = 0x0000000000000000 (0)
08:11:28.295   Last    <integer> = 0x0000000000000003 (3)
08:11:28.296 
08:11:28.296 [/Devices/piix3ide/0/LUN#0/] (level 4)
08:11:28.296   Driver <string>  = "Block" (cch=6)
08:11:28.296 
08:11:28.296 [/Devices/piix3ide/0/LUN#0/Config/] (level 5) (restricted root)
08:11:28.296   Type      <string>  = "HardDisk" (cch=9)
08:11:28.296   Mountable <integer> = 0x0000000000000000 (0)
08:11:28.296 
08:11:28.296 [/Devices/piix3ide/0/LUN#0/AttachedDriver/] (level 5)
08:11:28.296   Driver <string>  = "VD" (cch=3)
08:11:28.296 
08:11:28.296 [/Devices/piix3ide/0/LUN#0/AttachedDriver/Config/] (level 6) (restricted root)
08:11:28.296   Path   <string>  = "/home/david/.VirtualBox/HardDisks/Windows.vdi" (cch=46)
08:11:28.296   Format <string>  = "VDI" (cch=4)
08:11:28.296 
08:11:28.296 [/Devices/piix3ide/0/LUN#2/] (level 4)
08:11:28.296   Driver <string>  = "HostDVD" (cch=8)
08:11:28.296 
08:11:28.296 [/Devices/piix3ide/0/LUN#2/Config/] (level 5) (restricted root)
08:11:28.296   Path        <string>  = "/dev/sr1" (cch=9)
08:11:28.296   Passthrough <integer> = 0x0000000000000001 (1)
08:11:28.296 
08:11:28.296 [/Devices/pcnet/] (level 2)
08:11:28.296 
08:11:28.296 [/Devices/pcnet/0/] (level 3)
08:11:28.296   Trusted       <integer> = 0x0000000000000001 (1)
08:11:28.296   PCIDeviceNo   <integer> = 0x0000000000000003 (3)
08:11:28.296   PCIFunctionNo <integer> = 0x0000000000000000 (0)
08:11:28.296 
08:11:28.296 [/Devices/pcnet/0/Config/] (level 4) (restricted root)
08:11:28.296   Am79C973       <integer> = 0x0000000000000001 (1)
08:11:28.296   MAC            <bytes>   = "08 00 27 80 be 66" (cb=6)
08:11:28.296   CableConnected <integer> = 0x0000000000000001 (1)
08:11:28.296   LineSpeed      <integer> = 0x0000000000000000 (0)
08:11:28.296 
08:11:28.296 [/Devices/pcnet/0/LUN#999/] (level 4)
08:11:28.296   Driver <string>  = "MainStatus" (cch=11)
08:11:28.296 
08:11:28.296 [/Devices/pcnet/0/LUN#999/Config/] (level 5) (restricted root)
08:11:28.296   papLeds <integer> = 0x00000000b550070c (3041920780)
08:11:28.296 
08:11:28.296 [/Devices/pcnet/0/LUN#0/] (level 4)
08:11:28.296   Driver <string>  = "NAT" (cch=4)
08:11:28.296 
08:11:28.296 [/Devices/pcnet/0/LUN#0/Config/] (level 5) (restricted root)
08:11:28.297   TFTPPrefix <string>  = "/home/david/.VirtualBox/TFTP" (cch=29)
08:11:28.297   BootFile   <string>  = "Windows.pxe" (cch=12)
08:11:28.297 
08:11:28.297 [/Devices/e1000/] (level 2)
08:11:28.297 
08:11:28.297 [/Devices/serial/] (level 2)
08:11:28.297 
08:11:28.297 [/Devices/serial/0/] (level 3)
08:11:28.298 
08:11:28.298 [/Devices/serial/0/Config/] (level 4) (restricted root)
08:11:28.298   IRQ    <integer> = 0x0000000000000004 (4)
08:11:28.298   IOBase <integer> = 0x00000000000003f8 (1016)
08:11:28.298 
08:11:28.298 [/Devices/serial/1/] (level 3)
08:11:28.298 
08:11:28.298 [/Devices/serial/1/Config/] (level 4) (restricted root)
08:11:28.298   IRQ    <integer> = 0x0000000000000003 (3)
08:11:28.298   IOBase <integer> = 0x00000000000002f8 (760)
08:11:28.298 
08:11:28.298 [/Devices/parallel/] (level 2)
08:11:28.298 
08:11:28.298 [/Devices/VMMDev/] (level 2)
08:11:28.298 
08:11:28.298 [/Devices/VMMDev/0/] (level 3)
08:11:28.298   Trusted       <integer> = 0x0000000000000001 (1)
08:11:28.298   PCIDeviceNo   <integer> = 0x0000000000000004 (4)
08:11:28.298   PCIFunctionNo <integer> = 0x0000000000000000 (0)
08:11:28.298 
08:11:28.298 [/Devices/VMMDev/0/Config/] (level 4) (restricted root)
08:11:28.298 
08:11:28.298 [/Devices/VMMDev/0/LUN#0/] (level 4)
08:11:28.298   Driver <string>  = "MainVMMDev" (cch=11)
08:11:28.298 
08:11:28.298 [/Devices/VMMDev/0/LUN#0/Config/] (level 5) (restricted root)
08:11:28.298   Object <integer> = 0x00000000b5500498 (3041920152)
08:11:28.298 
08:11:28.298 [/Devices/VMMDev/0/LUN#999/] (level 4)
08:11:28.298   Driver <string>  = "MainStatus" (cch=11)
08:11:28.298 
08:11:28.298 [/Devices/VMMDev/0/LUN#999/Config/] (level 5) (restricted root)
08:11:28.298   papLeds <integer> = 0x00000000b550072c (3041920812)
08:11:28.299   First   <integer> = 0x0000000000000000 (0)
08:11:28.299   Last    <integer> = 0x0000000000000000 (0)
08:11:28.299 
08:11:28.299 [/Devices/AudioSniffer/] (level 2)
08:11:28.299 
08:11:28.299 [/Devices/AudioSniffer/0/] (level 3)
08:11:28.299 
08:11:28.299 [/Devices/AudioSniffer/0/Config/] (level 4) (restricted root)
08:11:28.299 
08:11:28.299 [/Devices/AudioSniffer/0/LUN#0/] (level 4)
08:11:28.299   Driver <string>  = "MainAudioSniffer" (cch=17)
08:11:28.299 
08:11:28.299 [/Devices/AudioSniffer/0/LUN#0/Config/] (level 5) (restricted root)
08:11:28.299   Object <integer> = 0x00000000b55004b8 (3041920184)
08:11:28.299 
08:11:28.299 [/Devices/ichac97/] (level 2)
08:11:28.299 
08:11:28.299 [/Devices/ichac97/0/] (level 3)
08:11:28.299   Trusted       <integer> = 0x0000000000000001 (1)
08:11:28.299   PCIDeviceNo   <integer> = 0x0000000000000005 (5)
08:11:28.299   PCIFunctionNo <integer> = 0x0000000000000000 (0)
08:11:28.299 
08:11:28.299 [/Devices/ichac97/0/Config/] (level 4) (restricted root)
08:11:28.299 
08:11:28.299 [/Devices/ichac97/0/LUN#0/] (level 4)
08:11:28.299   Driver <string>  = "AUDIO" (cch=6)
08:11:28.299 
08:11:28.299 [/Devices/ichac97/0/LUN#0/Config/] (level 5) (restricted root)
08:11:28.299   AudioDriver <string>  = "alsa" (cch=5)
08:11:28.299   StreamName  <string>  = "Windows" (cch=8)
08:11:28.299 
08:11:28.299 [/TM/] (level 1)
08:11:28.299   UTCOffset <integer> = 0x0000000000000000 (0)
08:11:28.299 
08:11:28.299 [/MM/] (level 1)
08:11:28.299 
08:11:28.299 !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
08:11:29.302 Changing the VM state from 'RUNNING' to 'GURU_MEDITATION'.
08:14:27.542 Console::powerDown(): A request to power off the VM has been issued (mMachineState=6, InUninit=0)
08:14:27.785 vboxClipboardDestroy: shutting down host clipboard
08:14:27.795 Shared clipboard: host clipboard thread terminated successfully
08:14:27.796 Changing the VM state from 'GURU_MEDITATION' to 'OFF'.
08:14:27.821 Changing the VM state from 'OFF' to 'DESTROYING'.
08:14:27.821 ************************* Statistics *************************
08:14:27.821 /Devices/ATA0/Unit0/AtapiDMA            0 times
08:14:27.821 /Devices/ATA0/Unit0/AtapiPIO            0 times
08:14:27.821 /Devices/ATA0/Unit0/DMA             18380 times
08:14:27.821 /Devices/ATA0/Unit0/PIO              1551 times
08:14:27.821 /Devices/ATA0/Unit0/ReadBytes    83649536 bytes
08:14:27.821 /Devices/ATA0/Unit0/WrittenBytes 557178880 bytes
08:14:27.821 /Devices/ATA0/Unit1/AtapiDMA            0 times
08:14:27.821 /Devices/ATA0/Unit1/AtapiPIO            0 times
08:14:27.821 /Devices/ATA0/Unit1/DMA                 0 times
08:14:27.821 /Devices/ATA0/Unit1/PIO                 0 times
08:14:27.821 /Devices/ATA0/Unit1/ReadBytes           0 bytes
08:14:27.821 /Devices/ATA0/Unit1/WrittenBytes        0 bytes
08:14:27.821 /Devices/ATA1/Unit0/AtapiDMA            0 times
08:14:27.821 /Devices/ATA1/Unit0/AtapiPIO        59967 times
08:14:27.821 /Devices/ATA1/Unit0/DMA                 0 times
08:14:27.821 /Devices/ATA1/Unit0/PIO                 0 times
08:14:27.821 /Devices/ATA1/Unit0/ReadBytes    296841216 bytes
08:14:27.821 /Devices/ATA1/Unit0/WrittenBytes        0 bytes
08:14:27.821 /Devices/ATA1/Unit1/AtapiDMA            0 times
08:14:27.821 /Devices/ATA1/Unit1/AtapiPIO            0 times
08:14:27.821 /Devices/ATA1/Unit1/DMA                 0 times
08:14:27.821 /Devices/ATA1/Unit1/PIO                 0 times
08:14:27.821 /Devices/ATA1/Unit1/ReadBytes           0 bytes
08:14:27.821 /Devices/ATA1/Unit1/WrittenBytes        0 bytes
08:14:27.821 /Devices/PCNet0/ReceiveBytes            0 bytes
08:14:27.821 /Devices/PCNet0/TransmitBytes           0 bytes
08:14:27.821 /GVMM/Sum/HaltBlocking               3255 calls
08:14:27.821 /GVMM/Sum/HaltCalls                 22093 calls
08:14:27.821 /GVMM/Sum/HaltNotBlocking           18838 calls
08:14:27.821 /GVMM/Sum/HaltTimeouts               1694 calls
08:14:27.821 /GVMM/Sum/HaltWakeUps                   0 calls
08:14:27.821 /GVMM/Sum/PollCalls                     1 calls
08:14:27.821 /GVMM/Sum/PollHalts                     0 calls
08:14:27.821 /GVMM/Sum/PollWakeUps                   0 calls
08:14:27.821 /GVMM/Sum/WakeUpCalls                2699 calls
08:14:27.821 /GVMM/Sum/WakeUpNotHalted            2299 calls
08:14:27.822 /GVMM/Sum/WakeUpWakeUps                 0 calls
08:14:27.822 /GVMM/VM/HaltBlocking                3255 calls
08:14:27.822 /GVMM/VM/HaltCalls                  22093 calls
08:14:27.822 /GVMM/VM/HaltNotBlocking            18838 calls
08:14:27.822 /GVMM/VM/HaltTimeouts                1694 calls
08:14:27.822 /GVMM/VM/HaltWakeUps                    0 calls
08:14:27.822 /GVMM/VM/PollCalls                      1 calls
08:14:27.822 /GVMM/VM/PollHalts                      0 calls
08:14:27.822 /GVMM/VM/PollWakeUps                    0 calls
08:14:27.822 /GVMM/VM/WakeUpCalls                 2699 calls
08:14:27.822 /GVMM/VM/WakeUpNotHalted             2299 calls
08:14:27.822 /GVMM/VM/WakeUpWakeUps                  0 calls
08:14:27.822 /GVMM/VMs                               1 calls
08:14:27.822 /MM/HyperHeap/cbFree               947136 bytes
08:14:27.822 /MM/HyperHeap/cbHeap              1310656 bytes
08:14:27.822 /PGM/cGuestModeChanges               1570 times
08:14:27.822 /PROF/EM/ForcedActions              35730 ticks/call (167661996743 ticks, 4692408 times, max 1721795003, min     171)
08:14:27.822 /PROF/EM/Halted                  36040761 ticks/call ( 29409261145 ticks,     816 times, max  53841877, min    2659)
08:14:27.822 /PROF/EM/RAWTotal                23242870 ticks/call (75454748955055 ticks, 3246361 times, max 764607738, min   19626)
08:14:27.822 /PROF/EM/REMTotal                  435615 ticks/call (819517912767 ticks, 1881287 times, max 221302980631, min   13705)
08:14:27.822 /PROF/EM/Total                   76478829021433 ticks/call (76478829021433 ticks,       1 times, max 76478829021433, min 76478829021433)
08:14:27.822 /PROF/VM/Halt/Block               1326368 ticks/call ( 29060726080 ticks,   21910 times, max  49454539, min    1529)
08:14:27.822 /PROF/VM/Halt/Poll                    278 ticks/call (     7086563 ticks,   25488 times, max     27595, min      65)
08:14:27.822 /PROF/VM/Halt/Timers                 9863 ticks/call (   251412178 ticks,   25488 times, max   4039659, min    1044)
08:14:27.822 /PROF/VM/Halt/Yield                  8431 ticks/call (        8431 ticks,       1 times, max      8431, min    8431)
08:14:27.822 /TM/GC/1nsSteps                    553164 times
08:14:27.822 /TM/R3/1nsSteps                   1832709 times
08:14:27.822 /TM/VirtualSync/CurrentOffset    22880438 ns
08:14:27.822 ********************* End of statistics **********************
08:14:28.087 Changing the VM state from 'DESTROYING' to 'TERMINATED'.
08:14:28.235 ERROR [COM]: aRC=VBOX_E_INVALID_VM_STATE (0x80bb0002) aIID={e3c6d4a1-a935-47ca-b16d-f9e9c496e53e} aComponent={Console} aText={Invalid machine state: 1)} aWarning=false, preserve=false

```

---

### Post by FireStorm102389 on 2009-10-24
or is that normal that after an installation when the computer is supposed to restart it causes an error? cuz i opened it back up and it seems to be continuing the installation...is that what happens when the computer usually restarts during installations, or is the VM supposed to restart and for some reason it just kinda errored out?

---

