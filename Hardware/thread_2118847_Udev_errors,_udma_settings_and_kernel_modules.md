---
title: "Udev errors, udma settings and kernel modules"
date: 2013-02-22
forum: Hardware
---

### Post by Tuxest on 2013-02-22
I am trying to get **Ubuntu 12.04 server to run on Fujitsu Futro S220 thin client** and I have reached the point where I need some help. 

**************************************************
**Hardware specs**
CPU: Crusoe Transmeta TM5800 800 MHz processor 
Board: TR5670 rev 1.32 (BIOS updated to version: 4.20.00 Rev. 1.05.05) 
RAM: 512MB PC2700 DDR SDRAM 266MHz 
Video: SIS315PRO 32MB (onboard) 
Flash memory: 2GB Compact Flash Card 
Network: 10/100 Mb/s Ethernet on board

Producers official site is [here]("http://uk.ts.fujitsu.com/rl/servicesupport/techsupport/professionalpc/thinclients/futrosxx/futros2xx.htm") and the inside looks like [this]("http://www.notebook-service.biz/bilder/Motherboards/Siemens/TR5670_Futro_S200_1.jpg").
***************************************************

OS would be running from **Compact Flash (CF) card** that connects trough CF slot on a the motherboard and IDE interface (ATA2). Because it is CF card the plan is to reduce the wear by not using swap partition and use ext2 instead of ext3 or ext4 (as they are journaling file systems). Some other CF friendly tweaks could be added later but that is not crucial at this point. As the CPU doesn't support PAE, I have used netinstall iso to install Ubuntu with non-pae kernel. Non-pae netinstall iso can be downloaded [here]("http://www.archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/").

After the installation grub needs “nomodeset” boot parameter and  GRUB_GFXMODE=640x480 to be enable for grub to start and for me to see it. For my convenience I have used [Boot repair disk]("http://sourceforge.net/p/boot-repair-cd/home/Home/") to reinstall grub with these settings after the OS installation ([chroot]("http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd/") could be used instead). Later grub settings can be configured by editing  /etc/default/grub and running “update-grub” after that. After the first successful boot I have removed “quiet” and “splash” from GRUB_CMDLINE_LINUX_DEFAULT line to see what is happening during boot.


----------------------------------------------------------------------------------
Note: It is also possible to add boot parameters temporary at the grub boot menu by pressing “e” while certain menu entry is select. Boot parameter should be added to the line that starts with “linux” and to boot with these settings press f10.
----------------------------------------------------------------------------------

During boot the OS tries to set the card to various UDMA modes with no success and udev errors are displayed. The system finally boots on its own only when the “rootdelay” is set at least 100. Otherwise it hangs after some udev messages. This hang can be overcome by typing “exit” and pressing enter and then OS boots. Rootdelay can be added with "rootdelay=some-numer-here" parameter at the same place to where nomodeset goes.
I also tried “libata.force=1:udma/100” and “libata.dma=4” kernel parameters but they seemed to have no effect. In the running system hdparm always reports the card to be connected in udma1 mode.

In the BIOS HDD Timing options include: Standard, Fast PIO, Multiword DMA, Ultra ATA-33, Ultra ATA-66 and Ultra ATA-100. Does it mean that the motherboard hardware support all these speeds for CF?
Grub starts only if this is set on “Standard” or “Fast PIO”, otherwise it just hangs there with a blinking cursor. 

**UDEV errors displayed at boot:**

My wireless keyboard and mouse that connect trough usb receiver dongle:
    udev[94]: timeout: killing '/sbin/modprobe -bv hid:b0003v000004FCp000005D8'[177]

Via Rhine Ethernet controller VT6102 [Rhine-II]:
    udev[105]: timeout: killing '/sbin/modprobe -bv` pci:v00001106d00003065sv00001106sd00000105bc02sc00100' [165]

VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE:
    udev[93]: timeout: killing '/sbin/modprobe -bv pci:v00001106d00000571sv00001106sd00000571bc01sc01i8a' [163]
[B]
hdparm info on the card:[/B]

    hdparm -i /dev/sda:
    
     Model=CF Card, FwRev=Ver2.35, SerialNo=639C0726120000091140 
     Config={ HardSect NotMFM Fixed DTR>10Mbs } 
     RawCHS=3909/16/63, TrkSize=32256, SectSize=512, ECCbytes=4 
     BuffType=DualPort, BuffSize=1kB, MaxMultSect=1, MultSect=1 
     CurCHS=3909/16/63, CurSects=3940272, LBA=yes, LBAsects=3940272 
     IORDY=yes, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120} 
     PIO modes:  pio0 pio1 pio2 pio3 pio4 
     DMA modes:  mdma0 mdma1 mdma2 
     UDMA modes: udma0 *udma1 udma2 udma3 udma4 udma5 
     AdvancedPM=no 
     * signifies the current active mode

When I run hdparm tests (-Tt) I get such results:

     Timing cached reads:   316 MB in  2.00 seconds = 157.83 MB/sec 
     Timing buffered disk reads:  18 MB in  3.10 seconds =   5.80 MB/sec

When I run the same tests while the CF card is connected to my desktop trough USB card reader the results are these:

     Timing cached reads:   4736 MB in  2.00 seconds = 2368.05 MB/sec 
     Timing buffered disk reads:  40 MB in  3.04 seconds =  13.15 MB/sec

I don't expect the same speed in the thin client but the point is that the bottleneck seems to be in the thin clients hardware.

lshw gives me this information about the IDE interface and the CF card:

    *-ide 
             description: IDE interface 
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE 
             vendor: VIA Technologies, Inc. 
             physical id: 11.1 
             bus info: pci@0000:00:11.1 
             logical name: scsi2 
             version: 06 
             width: 32 bits 
             clock: 33MHz 
             capabilities: ide pm bus_master cap_list emulated 
             configuration: driver=pata_via latency=64 
             resources: irq:10 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1100(size=16) 
           *-disk 
                description: ATA Disk 
                product: CF Card 
                physical id: 0.0.0 
                bus info: scsi@2:0.0.0 
                logical name: /dev/sdb 
                version: Ver2 
                serial: 639C0726120000091140 
                size: 1923MiB (2017MB) 
                capabilities: partitioned partitioned:dos 
                configuration: ansiversion=5 signature=0005d7cf 
              *-volume 
                   description: Linux filesystem partition 
                   vendor: Linux 
                   physical id: 1 
                   bus info: scsi@2:0.0.0,1 
                   logical name: /dev/sdb1 
                   version: 1.0 
                   serial: 1b1fd6a4-8733-4870-a360-5adee4a1bdcc 
                   size: 1922MiB 
                   capacity: 1922MiB 
                   capabilities: primary bootable ext2 initialized 
                   configuration: filesystem=ext2 modified=2013-02-20 18:19:45 mounted=2013-02-20 18:17:11 state=clean

Additional problem is that at boot after grub the screen goes blank for some time (the exact time varies and I can see more after the fresh install) and I can't see the whole boot but rather just a bit before the OS finally boots up. I assume that is about loading the graphics driver. 

There are also some interesting ACPI related lines in the syslog (ACPI is turned on in BIOS and turning it off there seems to have no effect):

    Feb 22 08:33:00 ubuntubox kernel: [    0.759164] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
    
    Feb 22 08:33:02 ubuntubox kernel: [  120.776917] ACPI: resource vt596_smbus [io  0x1400-0x1407] conflicts with ACPI region SM06 [io 0x1406-0x1406] 
    Feb 22 08:33:02 ubuntubox kernel: [  120.776946] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver


I am sorry if it turns out that there is more than one question here. But as all these issues might be related I thought I should give you all the data on the patient. I assume that it is all about kernel and modules. This beyond my knowledge and experience but I am ready follow tips and guides to learn what to do.

Could you help me to sort this mess up? That is, to boot OS without errors and get the CF card udma settings to the maximum that the hardware can handle.

---

