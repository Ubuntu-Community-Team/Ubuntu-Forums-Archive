---
title: "Breezy on Sony Vaio TX650P"
date: 2005-11-08
forum: Hardware &amp; Laptops
---

### Post by outdooricon on 2005-11-08
I just bought this laptop (TX650), and LOVE IT! So, the intention here is to provide an area where people can all discuss how to get this beauty working great in linux as well as allow me to provide my progress.

**What I did:**
Booted it up, went through the usual Windows junk. Then, ran the recovery backup utility which backs up everything onto two dvds. Then I installed Breezy (annihilating everything on the disk and starting fresh). Also, I bought an extra stick of 1 GB ram from Newegg and put that in this. It runs even faster and I think is worth the investment.

**What Works right away after Breezy Install:**
[LIST]
[*]CD / DVD Player
[*]Wi-Fi
[*]Sound
[*]Mute Sound Button
[*]Ethernet
[*]Suspend to Disk (even my Wi-Fi connection was NOT lost)
[*]FN Keys
[*]Headphones plug
[*]USB
[*]Bluetooth
[/LIST]

**What doesn't work right away after Breezy Install:**
[LIST]
[*]Touchpads special abilities (scrolling, multiple tapping, etc.) Even the touchpad use itself is a little flakey, If you quickly move the mouse and lift off your finger, it seems to take that as select. It gets real frustrating when using the Preferences menu because I require two mouse movements on the pad to get to the bottom of the menu, but If you don't do it carefully, you'll select whatever the mouse is hovering over when you lift the finger off the pad. **Fix is provided below**
[*]Volume Buttons
[*]All AV Buttons
[*]WWAN
[*]Reboot **Fix is provided below**
[*]The Battery doesn't appear to ever be marked as fully charged. The icon always shows the plug-in with the lightning bolt, and never just a plug-in. The wierd thing is, Windows never recognized it as fully charged either. This is a minor annoyance.
[*]SD Card / Memory Stick Slots
[*]Native Resolution Display ( xorg.conf says the correct 1366x768 although the resolution utility says 1368x768, resulting in an extra column of pixels on the screen which is annoying but still functional) **Fix is provided below**
[/LIST]

**What I haven't yet tested:**
[LIST]
[*]Microphone plug
[*]PCMCIA Slot
[*]Modem
[*]CD-R/RW, DVD-R/RW
[*]VGA Out
[*]IS400 slot
[/LIST]

**Things Worth Mentioning:**
[LIST]
[*]I use the MPlayer plugin instead of Totem in Firefox. If you're getting choppy streams of video and audio, right-click on the mPlayer plug-in that's playing and choose configure. Then set video output to 'x11' and audio output to 'oss'. The oss selection is key to eliminating the choppyness. I've found that OSS seems the best to use overall for sound on this machine as it recognizes the RealTek Audio. I also switched my volume changer in the ubuntu bar to control OSS's PCM-2, which is the speaker output. The main OSS volume will control the volume through the headphones.
[*]WPA works beautifully after install via Synaptic! After configuring the wpa conf file, just run the following code to test it out and connect:```
sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd

``` Then run this to get dhcp:```
sudo dhclient eth1
```
[*]I have a Logitech T270 bluetooth mouse that I hooked up with this. To get it working, all I had to do was first run the following to see if the mouse is detected (the mouse must be turned on for this to work): ```
sudo hcitool scan
``` This should end up showing the mouse along with it's MAC address. Then, to connect to the mouse, run this (where MAC_ADDRESS is replaced with the MAC address you found with the scan): ```
sudo hidd --connect MAC_ADDRESS
``` Now, you're mouse should be working great on the computer. To have the mouse start each time with the computer, make the following changes in /etc/default/bluez-utils (where MAC_ADDRESS is replaced with the MAC address you found with the scan):```
HIDD_ENABLED=1
HIDD_OPTIONS="--connect MAC_ADDRESS --server"

```

[/LIST]

**Fixes:**
[LIST]
[*]_**Touchpad**_. Most of the information here is derived from [this post]("http://ubuntuforums.org/showthread.php?t=78904") (most if not all recognition for the following should go to scubajeff for figuring all of this out). However, I felt it would be easier if I put here the exact information that I applied to this laptop. First, you need to get the 'build-essential' package ('Make' is the most importent package you need which should be included as a dependency, if not install 'make' as well) in Synaptic. Then, download the new Synaptics/ALPS driver [here]("http://web.telia.com/~u89404340/touchpad/"). Unpackage it and type within the directory: ```
sudo make
``` Then we need to backup the old driver and then copy over the driver we just compiled: ```
sudo cp /usr/X11R6/lib/modules/input/synaptics_drv.o /usr/X11R6/lib/modules/input/synaptics_drv.o.bckp
sudo cp synaptics_drv.o /usr/X11R6/lib/modules/input/
``` Now, we need to deal with the fact that the event corresponding with the touchpad may change if anouther mouse is in use as well. When we go to editing the xorg.conf file next, we will be changing how it recognizes the touchpad, so we need to prepare for this. First we need to create the rule: ```
sudo nano /etc/udev/alps.rules
``` In which we will place the following line: ```
BUS="serio", SYSFS{description}="i8042 Aux Port", KERNEL="event?", SYMLINK="input/alps"
``` Now we need to create a symlink to that rule (if you are wondering why we are doing all of this, please click the above post link and read scubajeffs hard work): ```
sudo ln -s /etc/udev/alps.rules /etc/udev/rules.d/40_alps.rules
``` Next, we must edit the xorg.conf file: ```
sudo nano /etc/X11/xorg.conf
```Finally, we need to change the 'InputDevice' section for the 'Synaptics Touchpad' to be the following: ```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
#       Option          "Device"                "/dev/psaux"
        Option          "Device"                "/dev/input/alps"
#       Option          "Protocol"              "auto-dev"
        Option          "Protocol"              "event"
        Option          "SHMConfig"             "true"
        Option          "LeftEdge"              "120"
        Option          "RightEdge"             "830"
        Option          "TopEdge"               "120"
        Option          "BottomEdge"            "650"
        Option          "FingerLow"             "14"
        Option          "FingerHigh"            "15"
        Option          "MaxTapTime"            "180"
        Option          "MaxTapMove"            "110"
        Option          "EmulateMidButtonTime"  "75"
        Option          "VertScrollDelta"       "20"
#       Option          "HorizScrollDelta"      "0"
        Option          "HorizScrollDelta"      "20"
        Option          "MinSpeed"              "0.3"
        Option          "MaxSpeed"              "0.75"
        Option          "AccelFactor"           "0.015"
        Option          "EdgeMotionMinSpeed"    "200"
        Option          "EdgeMotionMaxSpeed"    "200"
        Option          "UpDownScrolling"       "1"
        Option          "CircularScrolling"     "1"
        Option          "CircScrollDelta"       "0.1"
        Option          "CircScrollTrigger"     "2"
        Option          "GuestMouseOff"         "0"
EndSection

```
You can change these features to represent exactly what you want. Also, note that each commented out lines is what was originally in this file but has been replaced by the line right below it. Now, restart your laptop. Welcome to a fully featured touchpad!
[*]_**Reboot**_. Much thanks goes to trelirodia for this fix. We need to edit the  /boot/grub/menu.lst file: ```
sudo nano /boot/grub/menu.lst
``` We want to change this section (the actual kernel number you have may be slightly different): ```

title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot
```
to the following (Note the addition of "reboot=h"): ```

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash reboot=h
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot
```
Now just shutdown and bootup the laptop, and be ready for effortless reboots!
[*]_**Native Screen Resolution**_. Well, I feel pretty stupid about this one as I was just about to write up a seperate thread to see if anyone could help me with this one. Let's just say, if all else fails, try the obvious. To get this to be 1366x768 in stead of 1368x768 (thus eliminating that extra column on the side of the desktop), simply go to the Screen Resolution
 utility and select the 1366x768 'Resolution' instead. No biggie.
[/LIST]
**NOTE:** I will update this as I discover more issues / fixes. Please feel free to join in helping me to figure out how to get all of this to work.

---

### Post by &amp;ergio on 2005-11-11
Have you seen this: [http://www.linux-on-laptops.com/sony.html](http://www.linux-on-laptops.com/sony.html) and this: [http://tuxmobil.org/sony.html](http://tuxmobil.org/sony.html) (VGN-T notebooks)
IMHO VGN-T1XP and VGN-TX -- aren't the same. VGN-T1XP -- hasn't wan...
...
can you show me dmesg, lspci -vvv ... anything more?

---

### Post by outdooricon on 2005-11-11
[QUOTE=&ergio]Have you seen this: [http://www.linux-on-laptops.com/sony.html](http://www.linux-on-laptops.com/sony.html) and this: [http://tuxmobil.org/sony.html](http://tuxmobil.org/sony.html) (VGN-T notebooks)
IMHO VGN-T1XP and VGN-TX -- aren't the same. VGN-T1XP -- hasn't wan...
...
can you show me dmesg, lspci -vvv ... anything more?[/QUOTE]

Mmm, good point. I'll remove that part...

sudo dmesg gives:
```
[4294668.064000] Enabling unmasked SIMD FPU exception support... done.
[4294668.064000] Checking 'hlt' instruction... OK.
[4294668.068000] Checking for popad bug... OK.
[4294668.068000] checking if image is initramfs... it is
[4294668.809000] Freeing initrd memory: 5171k freed
[4294668.809000] ACPI: Looking for DSDT in initrd... not found!
[4294668.878000]  not found!
[4294668.962000] ENABLING IO-APIC IRQs
[4294668.962000] ..TIMER: vector=0x31 pin1=2 pin2=-1
[4294669.073000] NET: Registered protocol family 16
[4294669.073000] EISA bus registered
[4294669.073000] ACPI: bus type pci registered
[4294669.073000] PCI: PCI BIOS revision 2.10 entry at 0xfd911, last bus=7
[4294669.073000] PCI: Using MMCONFIG
[4294669.073000] mtrr: v2.0 (20020519)
[4294669.074000] ACPI: Subsystem revision 20050729
[4294669.082000] ACPI: Interpreter enabled
[4294669.082000] ACPI: Using IOAPIC for interrupt routing
[4294669.082000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294669.082000] PCI: Probing PCI hardware (bus 00)
[4294669.082000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294669.089000] Boot video device is 0000:00:02.0
[4294669.089000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[4294669.090000] PCI: Transparent bridge - 0000:00:1e.0
[4294669.100000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294669.102000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[4294669.103000] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
[4294669.103000] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[4294669.104000] ACPI: PCI Interrupt Link [LNKC] (IRQs 10) *0, disabled.
[4294669.104000] ACPI: PCI Interrupt Link [LNKD] (IRQs *10)
[4294669.104000] ACPI: PCI Interrupt Link [LNKE] (IRQs *10)
[4294669.105000] ACPI: PCI Interrupt Link [LNKF] (IRQs 10) *3
[4294669.105000] ACPI: PCI Interrupt Link [LNKG] (IRQs *10)
[4294669.105000] ACPI: PCI Interrupt Link [LNKH] (IRQs *10)
[4294669.106000] burst-mode-ec-10-Aug
[4294669.106000] ACPI: Embedded Controller [EC0] (gpe 23)
[4294669.108000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294669.108000] pnp: PnP ACPI init
[4294669.109000] pnp: PnP ACPI: found 10 devices
[4294669.109000] PnPBIOS: Disabled by ACPI PNP
[4294669.110000] PCI: Using ACPI for IRQ routing
[4294669.110000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294669.130000] Simple Boot Flag at 0x49 set to 0x1
[4294669.130000] audit: initializing netlink socket (disabled)
[4294669.130000] audit: initialized
[4294669.130000] highmem bounce pool size: 64 pages
[4294669.130000] VFS: Disk quotas dquot_6.5.1
[4294669.130000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294669.130000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294669.130000] devfs: boot_options: 0x0
[4294669.130000] Initializing Cryptographic API
[4294669.131000] isapnp: Scanning for PnP cards...
[4294669.484000] isapnp: No Plug & Play device found
[4294669.505000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294669.513000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294669.513000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294669.513000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294669.516000] io scheduler noop registered
[4294669.516000] io scheduler anticipatory registered
[4294669.516000] io scheduler deadline registered
[4294669.516000] io scheduler cfq registered
[4294669.517000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294669.518000] EISA: Probing bus 0 at eisa.0
[4294669.518000] Cannot allocate resource for EISA slot 1
[4294669.518000] Cannot allocate resource for EISA slot 2
[4294669.518000] EISA: Detected 0 cards.
[4294669.518000] NET: Registered protocol family 2
[4294669.528000] IP: routing cache hash table of 16384 buckets, 128Kbytes
[4294669.528000] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
[4294669.531000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[4294669.531000] TCP: Hash tables configured (established 262144 bind 65536)
[4294669.531000] NET: Registered protocol family 8
[4294669.531000] NET: Registered protocol family 20
[4294669.531000] ACPI wakeup devices:
[4294669.531000] PWRB USB1 USB2 USB3 USB4 USB7 LANC  EC0
[4294669.531000] ACPI: (supports S0 S3 S4 S5)
[4294669.532000] Freeing unused kernel memory: 224k freed
[4294669.552000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294669.553000] vga16fb: initializing
[4294669.553000] vga16fb: mapped to 0xc00a0000
[4294669.697000] Console: switching to colour frame buffer device 80x30
[4294669.697000] fb0: VGA16 VGA frame buffer device
[4294670.821000] Capability LSM initialized
[4294670.833000] NET: Registered protocol family 1
[4294670.851000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294670.851000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294670.851000] ACPI: bus type ide registered
[4294670.856000] ICH6: IDE controller at PCI slot 0000:00:1f.1
[4294670.856000] ACPI: PCI Interrupt 0000:00:1f.1[B] -> GSI 18 (level, low) -> IRQ 18
[4294670.856000] ICH6: chipset revision 3
[4294670.856000] ICH6: not 100% native mode: will probe irqs later
[4294670.856000]     ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:DMA, hdb:DMA
[4294670.856000] Probing IDE interface ide0...
[4294671.120000] hda: TOSHIBA MK6006GAH, ATA DISK drive
[4294671.834000] hdb: MATSHITAUJ-832D, ATAPI CD/DVD-ROM drive
[4294671.885000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294671.885000] Probing IDE interface ide1...
[4294672.398000] Probing IDE interface ide2...
[4294672.910000] Probing IDE interface ide3...
[4294673.422000] Probing IDE interface ide4...
[4294673.934000] Probing IDE interface ide5...
[4294674.449000] hda: max request size: 1024KiB
[4294674.473000] hda: 117210240 sectors (60011 MB), CHS=16383/255/63, UDMA(100)
[4294674.473000] hda: cache flushes supported
[4294674.473000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294674.516000] hdb: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[4294674.516000] Uniform CD-ROM driver Revision: 3.20
[4294674.785000] Attempting manual resume
[4294674.798000] swsusp: Suspend partition has wrong signature?
[4294674.846000] usbcore: registered new driver usbfs
[4294674.846000] usbcore: registered new driver hub
[4294674.847000] USB Universal Host Controller Interface driver v2.2
[4294674.847000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 17 (level, low) -> IRQ 17
[4294674.847000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294674.847000] uhci_hcd 0000:00:1d.0: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
[4294674.909000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294674.909000] uhci_hcd 0000:00:1d.0: irq 17, io base 0x00001820
[4294674.909000] hub 1-0:1.0: USB hub found
[4294674.909000] hub 1-0:1.0: 2 ports detected
[4294674.912000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[4294674.912000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294674.912000] uhci_hcd 0000:00:1d.1: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
[4294674.974000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294674.974000] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[4294674.974000] hub 2-0:1.0: USB hub found
[4294674.974000] hub 2-0:1.0: 2 ports detected
[4294674.977000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 21 (level, low) -> IRQ 21
[4294674.977000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294674.977000] uhci_hcd 0000:00:1d.2: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
[4294675.039000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294675.039000] uhci_hcd 0000:00:1d.2: irq 21, io base 0x00001860
[4294675.039000] hub 3-0:1.0: USB hub found
[4294675.039000] hub 3-0:1.0: 2 ports detected
[4294675.042000] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 17 (level, low) -> IRQ 17
[4294675.042000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[4294675.042000] uhci_hcd 0000:00:1d.3: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
[4294675.104000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[4294675.104000] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[4294675.104000] hub 4-0:1.0: USB hub found
[4294675.104000] hub 4-0:1.0: 2 ports detected
[4294675.144000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 23
[4294675.144000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294675.144000] ehci_hcd 0000:00:1d.7: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
[4294675.144000] ehci_hcd 0000:00:1d.7: debug port 1
[4294675.144000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[4294675.144000] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xb0004000
[4294675.148000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[4294675.148000] ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294675.148000] hub 5-0:1.0: USB hub found
[4294675.148000] hub 5-0:1.0: 8 ports detected
[4294675.241000] e100: Intel(R) PRO/100 Network Driver, 3.4.8-k2-NAPI
[4294675.241000] e100: Copyright(c) 1999-2005 Intel Corporation
[4294675.241000] ACPI: PCI Interrupt 0000:06:08.0[A] -> GSI 20 (level, low) -> IRQ 20
[4294675.270000] e100: eth0: e100_probe: addr 0xb0107000, irq 20, MAC addr 00:01:4A:98:1A:49
[4294675.708000] usb 3-1: new full speed USB device using uhci_hcd and address 2
[4294677.716000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[4294677.716000] ACPI: Processor [CPU0] (supports 8 throttling states)
[4294677.719000] ACPI: Thermal Zone [ATF0] (32 C)
[4294677.896000] Attempting manual resume
[4294677.897000] swsusp: Suspend partition has wrong signature?
[4294677.916000] kjournald starting.  Commit interval 5 seconds
[4294677.916000] EXT3-fs: mounted filesystem with ordered data mode.
[4294679.478000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294682.952000] Adding 1485972k swap on /dev/hda5.  Priority:-1 extents:1
[4294683.270000] EXT3 FS on hda1, internal journal
[4294694.085000] lp: driver loaded but no devices found
[4294694.111000] mice: PS/2 mouse device common for all mice
[4294694.157000] ieee1394: Initialized config rom entry `ip1394'
[4294694.164000] SCSI subsystem initialized
[4294694.169000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4294694.410000] alps.c: Enabling hardware tapping
[4294694.473000] input: PS/2 Mouse on isa0060/serio1
[4294694.475000] input: AlpsPS/2 ALPS GlidePoint on isa0060/serio1
[4294695.024000] ts: Compaq touchscreen protocol output
[4294698.114000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294699.126000] cdrom: open failed.
[4294701.606000] Linux agpgart interface v0.101 (c) Dave Jones
[4294701.614000] agpgart: Detected an Intel 915GM Chipset.
[4294701.615000] agpgart: Detected 7932K stolen memory.
[4294701.651000] agpgart: AGP aperture is 256M @ 0xc0000000
[4294702.131000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 19 (level, low) -> IRQ 19
[4294702.131000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[4294703.536000] hw_random hardware driver 1.0.0 loaded
[4294703.835000] Linux Kernel Card Services
[4294703.835000]   options:  [pci] [cardbus] [pm]
[4294703.848000] ACPI: PCI Interrupt 0000:06:05.0[A] -> GSI 21 (level, low) -> IRQ 21
[4294703.848000] Yenta: CardBus bridge found at 0000:06:05.0 [104d:81e2]
[4294703.848000] Yenta: Enabling burst memory read transactions
[4294703.848000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294703.848000] Yenta: Routing CardBus interrupts to PCI
[4294703.848000] Yenta TI: socket 0000:06:05.0, mfunc 0x01af1b22, devctl 0x64
[4294704.069000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 21
[4294704.069000] Socket status: 30000006
[4294704.348000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294704.348000] ACPI: PCI Interrupt 0000:06:05.2[C] -> GSI 20 (level, low) -> IRQ 20
[4294704.402000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[b0106000-b01067ff]  Max Packet=[2048]
[4294704.610000] ieee80211_crypt: registered algorithm 'NULL'
[4294704.615000] ieee80211: 802.11 data/management/control stack, 1.0.3
[4294704.615000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4294704.625000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
[4294704.625000] ipw2200: Copyright(c) 2003-2004 Intel Corporation
[4294704.629000] ACPI: PCI Interrupt 0000:06:0b.0[A] -> GSI 22 (level, low) -> IRQ 22
[4294704.629000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[4294706.583000] Bluetooth: Core ver 2.7
[4294706.583000] NET: Registered protocol family 31
[4294706.583000] Bluetooth: HCI device and connection manager initialized
[4294706.583000] Bluetooth: HCI socket layer initialized
[4294706.585000] Bluetooth: HCI USB driver ver 2.8
[4294706.589000] usbcore: registered new driver hci_usb
[4294707.115000] Real Time Clock Driver v1.12
[4294708.047000] NET: Registered protocol family 17
[4294774.304000] NET: Registered protocol family 10
[4294774.304000] Disabled Privacy Extensions on device c02eb280(lo)
[4294774.305000] IPv6 over IPv4 tunneling driver
[4294776.785000] ACPI: AC Adapter [ACAD] (on-line)
[4294776.835000] ACPI: Battery Slot [BAT1] (battery present)
[4294776.858000] ACPI: Lid Switch [LID0]
[4294776.858000] ACPI: Power Button (CM) [PWRB]
[4294776.981000] ibm_acpi: ec object not found
[4294777.034000] ACPI Sony Notebook Control Driver v0.2 successfully installed
[4294777.113000] ACPI: Video Device [NGFX] (multi-head: yes  rom: no  post: no)
[4294777.114000] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[4294784.323000] eth1: no IPv6 routers present
[4294784.563000] eth0: no IPv6 routers present
[4294784.751000] [drm] Initialized drm 1.0.0 20040925
[4294784.756000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294784.761000] [drm] Initialized i915 1.2.0 20040405 on minor 0: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller
[4294784.762000] mtrr: base(0xc0020000) is not aligned on a size(0x600000) boundary
[4294789.832000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294789.832000] apm: overridden by ACPI.
[4294789.989000] Sony Vaio Jogdial input method installed.
[4294790.007000] Sony Vaio Keys input method installed.
[4294790.187000] sonypi: Sony Programmable I/O Controller Driverv1.26.
[4294790.187000] sonypi: detected type3 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = on
[4294790.187000] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084
[4294790.187000] sonypi: device allocated minor is 61
[4294791.049000] cs: IO port probe 0x100-0x4ff: excluding 0x4d0-0x4d7
[4294791.052000] cs: IO port probe 0xc00-0xcf7: clean.
[4294791.053000] cs: IO port probe 0xa00-0xaff: clean.
[4294792.324000] Bluetooth: L2CAP ver 2.7
[4294792.324000] Bluetooth: L2CAP socket layer initialized
[4294792.347000] Bluetooth: RFCOMM ver 1.5
[4294792.347000] Bluetooth: RFCOMM socket layer initialized
[4294792.347000] Bluetooth: RFCOMM TTY layer initialized
[4296098.996000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296098.996000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296099.114000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296099.114000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.

```

sudo lspci -vvv gives:
```
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
        Subsystem: Sony Corporation: Unknown device 81e2
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 0
        Capabilities: [e0] #09 [2109]

0000:00:02.0 VGA compatible controller: Intel Corp. Mobile Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Sony Corporation: Unknown device 81e2
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at b0080000 (32-bit, non-prefetchable) [size=512K]
        Region 1: I/O ports at 1800 [size=8]
        Region 2: Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Region 3: Memory at b0040000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: [d0] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:02.1 Display controller: Intel Corp. Mobile Graphics Controller (rev 03)
        Subsystem: Sony Corporation: Unknown device 81e2
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Region 0: Memory at 60000000 (32-bit, non-prefetchable) [disabled] [size=512K]
        Capabilities: [d0] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
        Subsystem: Sony Corporation: Unknown device 81e2
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 0x10 (64 bytes)
        Interrupt: pin A routed to IRQ 19
        Region 0: Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000
        Capabilities: [70] #10 [0091]

0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation: Unknown device 81e2
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 17
        Region 4: I/O ports at 1820 [size=32]

0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation: Unknown device 81e2
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 19
        Region 4: I/O ports at 1840 [size=32]

0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation: Unknown device 81e2
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin C routed to IRQ 21
        Region 4: I/O ports at 1860 [size=32]

0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation: Unknown device 81e2
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 17
        Region 4: I/O ports at 1880 [size=32]

0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Sony Corporation: Unknown device 81e2
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin D routed to IRQ 23
        Region 0: Memory at b0004000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [58] #0a [20a0]

0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=06, subordinate=07, sec-latency=32
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: b0100000-b01fffff
        Prefetchable memory behind bridge: 00000000fff00000-0000000000000000
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: [50] #0d [0000]

0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
        Subsystem: Sony Corporation: Unknown device 81e2
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Sony Corporation: Unknown device 81e2
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 18
        Region 0: I/O ports at <unassigned>
        Region 1: I/O ports at <unassigned>
        Region 2: I/O ports at <unassigned>
        Region 3: I/O ports at <unassigned>
        Region 4: I/O ports at 1810 [size=16]

0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
        Subsystem: Sony Corporation: Unknown device 81e2
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Region 4: I/O ports at 18a0 [size=32]

0000:06:05.0 CardBus bridge: Texas Instruments: Unknown device 8031
        Subsystem: Sony Corporation: Unknown device 81e2
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 168, Cache Line Size: 0x20 (128 bytes)
        Interrupt: pin A routed to IRQ 21
        Region 0: Memory at 60080000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 60400000-607ff000 (prefetchable)
        Memory window 1: 60800000-60bff000
        I/O window 0: 00004000-000040ff
        I/O window 1: 00004400-000044ff
        BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
        16-bit legacy interface ports at 0001

0000:06:05.2 FireWire (IEEE 1394): Texas Instruments: Unknown device 8032 (prog-if 10 [OHCI])
        Subsystem: Sony Corporation: Unknown device 81e2
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (750ns min, 1000ns max), Cache Line Size: 0x10 (64 bytes)
        Interrupt: pin C routed to IRQ 20
        Region 0: Memory at b0106000 (32-bit, non-prefetchable) [size=2K]
        Region 1: Memory at b0100000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME+

0000:06:05.3 Unknown mass storage controller: Texas Instruments: Unknown device 8033
        Subsystem: Sony Corporation: Unknown device 81e2
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 57 (1750ns min, 1000ns max), Cache Line Size: 0x10 (64 bytes)
        Interrupt: pin B routed to IRQ 10
        Region 0: Memory at b0104000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [44] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:06:08.0 Ethernet controller: Intel Corp.: Unknown device 1069 (rev 03)
        Subsystem: Sony Corporation: Unknown device 81e2
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 66 (2000ns min, 14000ns max), Cache Line Size: 0x10 (64 bytes)
        Interrupt: pin A routed to IRQ 20
        Region 0: Memory at b0107000 (32-bit, non-prefetchable) [size=4K]
        Region 1: I/O ports at 2000 [size=64]
        Capabilities: [dc] Power Management version 2
                Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=2 PME-

0000:06:0b.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
        Subsystem: Intel Corp.: Unknown device 2751
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (750ns min, 6000ns max), Cache Line Size: 0x10 (64 bytes)
        Interrupt: pin A routed to IRQ 22
        Region 0: Memory at b0108000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=1 PME-

```

Anything else you'd like?

---

### Post by &amp;ergio on 2005-11-11
I can't see anything about gprs modem. Can you show me /proc/bus/usb/devices

FYI:
$ mount | grep usb
usbfs on /proc/bus/usb type usbfs (rw)
$

---

### Post by outdooricon on 2005-11-11
[QUOTE=&ergio]I can't see anything about gprs modem. Can you show me /proc/bus/usb/devices

FYI:
$ mount | grep usb
usbfs on /proc/bus/usb type usbfs (rw)
$[/QUOTE]

I don't quite know what you're saying with that grep of mount but 'cat /proc/bus/usb/devices' reveals:
```
T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.12-9-386 ehci_hcd
S:  Product=Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
S:  SerialNumber=0000:00:1d.7
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=256ms

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.12-9-386 uhci_hcd
S:  Product=Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
S:  SerialNumber=0000:00:1d.3
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc= 27/900 us ( 3%), #Int=  1, #Iso=  2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.12-9-386 uhci_hcd
S:  Product=Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
S:  SerialNumber=0000:00:1d.2
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(unk. ) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=044e ProdID=300c Rev=19.15
S:  Manufacturer=ALPS
S:  Product=UGX
C:* #Ifs= 3 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(unk. ) Sub=01 Prot=01 Driver=hci_usb
E:  Ad=81(I) Atr=03(Int.) MxPS=  16 Ivl=1ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(unk. ) Sub=01 Prot=01 Driver=hci_usb
E:  Ad=03(O) Atr=01(Isoc) MxPS=   0 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=   0 Ivl=1ms
I:  If#= 1 Alt= 1 #EPs= 2 Cls=e0(unk. ) Sub=01 Prot=01 Driver=hci_usb
E:  Ad=03(O) Atr=01(Isoc) MxPS=   9 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=   9 Ivl=1ms
I:  If#= 1 Alt= 2 #EPs= 2 Cls=e0(unk. ) Sub=01 Prot=01 Driver=hci_usb
E:  Ad=03(O) Atr=01(Isoc) MxPS=  17 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  17 Ivl=1ms
I:  If#= 1 Alt= 3 #EPs= 2 Cls=e0(unk. ) Sub=01 Prot=01 Driver=hci_usb
E:  Ad=03(O) Atr=01(Isoc) MxPS=  25 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  25 Ivl=1ms
I:  If#= 1 Alt= 4 #EPs= 2 Cls=e0(unk. ) Sub=01 Prot=01 Driver=hci_usb
E:  Ad=03(O) Atr=01(Isoc) MxPS=  33 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  33 Ivl=1ms
I:  If#= 1 Alt= 5 #EPs= 2 Cls=e0(unk. ) Sub=01 Prot=01 Driver=hci_usb
E:  Ad=03(O) Atr=01(Isoc) MxPS=  49 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  49 Ivl=1ms
I:  If#= 2 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=00 Driver=(none)

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.12-9-386 uhci_hcd
S:  Product=Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
S:  SerialNumber=0000:00:1d.1
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.12-9-386 uhci_hcd
S:  Product=Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
S:  SerialNumber=0000:00:1d.0
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

```

---

### Post by trelirodia on 2005-11-12
Hello, 

have you had any luck with fixing the shutdown/reboot freeze? I got a very similar problem after my upgrade from Hoary to Breezy, though mine is restricted to reboot and basically, after all processes are shutdown and it is about to begin instead of the Grub screen I see a very peculiar screen of black and white flickering lines. I also have a sony vaio (VGN-FX195XP), though had no problem what so ever with Hoary. Please let me know if you've had better luck ... I am desperately trying to avoid doing a clean install, at least for the next couple of months. 

Thanks and good luck. Sorry for not being any help to your problems too...

M

---

### Post by &amp;ergio on 2005-11-12
Goolge says, that UGX (Manufacturer: ALPS) -- is the touchpad.
But where is the gprs modem? Have you slot for sim. (under the battery)?
There are button that switch cordless interfaces. What if is it hardware button? Can you play with it an see into logs (dmesg, syslog, usb, messages.....)?

---

### Post by outdooricon on 2005-11-14
[QUOTE=trelirodia]Hello, 

have you had any luck with fixing the shutdown/reboot freeze? I got a very similar problem after my upgrade from Hoary to Breezy, though mine is restricted to reboot and basically, after all processes are shutdown and it is about to begin instead of the Grub screen I see a very peculiar screen of black and white flickering lines. I also have a sony vaio (VGN-FX195XP), though had no problem what so ever with Hoary. Please let me know if you've had better luck ... I am desperately trying to avoid doing a clean install, at least for the next couple of months. 

Thanks and good luck. Sorry for not being any help to your problems too...

M[/QUOTE]

Hmm, The problem that you're mentioning doesn't seem to be the same as mine. Mine actually halts before shutdown, not once it starts back up. I will let you koow when I fix it though.

---

### Post by outdooricon on 2005-11-14
[QUOTE=&ergio]Goolge says, that UGX (Manufacturer: ALPS) -- is the touchpad.
But where is the gprs modem? Have you slot for sim. (under the battery)?
There are button that switch cordless interfaces. What if is it hardware button? Can you play with it an see into logs (dmesg, syslog, usb, messages.....)?[/QUOTE]

I'm almost sure that the WWAN (I assume this is the GPRS you are talking about) will not work in linux, at least right now. Yes, there is a slot for the SIM Card under the battery.  The hardware button only turns on and off Bluetooth / WiFi (Software switches Wi-Fi to WWAN and vice-versa in Windows). So, I'm pretty sure showing you the logs when I turn it off and on, it will reveal nothing to you in the logs.

---

### Post by &amp;ergio on 2005-11-14
[quote=outdooricon]I'm almost sure that the WWAN (I assume this is the GPRS you are talking about) will not work in linux, at least right now. Yes, there is a slot for the SIM Card under the battery. The hardware button only turns on and off Bluetooth / WiFi (Software switches Wi-Fi to WWAN and vice-versa in Windows). So, I'm pretty sure showing you the logs when I turn it off and on, it will reveal nothing to you in the logs.[/quote]

OK. But what interface uses wwan? not pci, not usb... ???

---

### Post by outdooricon on 2005-11-15
[QUOTE=&ergio]OK. But what interface uses wwan? not pci, not usb... ???[/QUOTE]

That's a good question. I wish I could activate it so I could find out through some kind of software switch. My guess is it relates to the wireless network controller itself somehow.

---

### Post by outdooricon on 2005-11-17
I've Been looking into the SD Card / MemoryStick Slot not working. From what I can tell from the Toshiba website, It's a Texas Instruments PCI7411 controller. I did a quick search on these forums and found that someone has this controller listed in their lspci ([here]("http://www.ubuntuforums.org/showthread.php?t=59033&highlight=pci7411")). This gives me some hope (as you can see above a few posts my lspci doesn't show this)... I wonder If It's something that I can enable in the kernel... I sure wish someone else out there was dealing with this issue as well....

---

### Post by ushooz on 2005-11-17
I have the shutdown and reboot issue where it stops without rebooting. Sony Vaio S560,

Also, while it does not appear to be running the disk the entire time. My HD light never goes out or flashes. When I boot the install CD and during install it flashes as it copies files. It is only after it is fully installed that it never goes out.

Dual booting into Windows the drive light acts as expected. Flashing on drive access.

---

### Post by &amp;ergio on 2005-11-17
[quote=outdooricon]That's a good question. I wish I could activate it so I could find out through some kind of software switch. My guess is it relates to the wireless network controller itself somehow.[/quote]

under windows it is impossible to use wi-fi and gprs simultaneously...
I don't  know is it hardware feature or windows bug.
If it is windows bug -- it is very stupid bug.
If it is hardware feature -- I don't understand how ethernet card (wi-fi) can transform into modem (gprs)...

---

### Post by &amp;ergio on 2005-11-17
[quote=outdooricon]
**What I haven't yet tested:**[LIST]
[*]Bluetooth
[*]Microphone plug
[*]PCMCIA Slot
[*]Modem
[*]CD-R/RW, DVD, DVD-R/RW
[*]VGA Out
[*]IS400 slot [/LIST][/quote] ok wwan is not cricital. what about Bluetooth PCMCIA Slot CD-R/RW, DVD, DVD-R/RW and VGA Out? if it's works (I hope) I'll buy this notebook  as soon as possible
 
 and what is 'IS400 slot' ??

---

### Post by outdooricon on 2005-11-19
Sergio, I will address all those things I haven't tested yet as soon as I can, I've got a lot of school stuff going on right now and don't have much time for troubleshooting at the moment.

On a seperate note, a quick search for that TI PCI7411 controller has revealed a couple of interesting sites worth watching. I ahven't gotten to lok at these very closely, but a driver is possibly being developed? The sites are these: 
[A Forum On this Topic]("http://www.linux-on-laptops.com/forum/showthread.php?t=55") and [A Possible Driver Being Developed]("http://tifm21.berlios.de/"). More on this all when I get some time.

---

### Post by &amp;ergio on 2005-11-19
Sergio. Not Ergio. (:

---

### Post by outdooricon on 2005-11-19
[QUOTE=&ergio]Sergio. Not Ergio. (:[/QUOTE]

lol, my bad. Edit has been made.

---

### Post by outdooricon on 2005-11-25
[QUOTE=&ergio]ok wwan is not cricital. what about Bluetooth PCMCIA Slot CD-R/RW, DVD, DVD-R/RW and VGA Out? if it's works (I hope) I'll buy this notebook  as soon as possible
 
 and what is 'IS400 slot' ??[/QUOTE]

Ok, I finally got a Bluetooth mouse, so I've verified bluetooth works (for more details on mouse, see first post). I honestly don't know what the IS400 slot is supposed to be. It's on the back and I thought it was a mini firewire hookup, but the letter etching above it say IS400. So, I don't know. I'll test the other things as I get time here.

---

### Post by &amp;ergio on 2005-11-25
[QUOTE=outdooricon]Ok, I finally got a Bluetooth mouse, so I've verified bluetooth works (for more details on mouse, see first post). I honestly don't know what the IS400 slot is supposed to be. It's on the back and I thought it was a mini firewire hookup, but the letter etching above it say IS400. So, I don't know. I'll test the other things as I get time here.[/QUOTE]
It's great. I'll buy this laptop ASAP.

---

### Post by keithw on 2005-11-26
IS400 is a type of firewire connection.

[QUOTE=outdooricon]Ok, I finally got a Bluetooth mouse, so I've verified bluetooth works (for more details on mouse, see first post). I honestly don't know what the IS400 slot is supposed to be. It's on the back and I thought it was a mini firewire hookup, but the letter etching above it say IS400. So, I don't know. I'll test the other things as I get time here.[/QUOTE]

---

### Post by 1c3d0g on 2005-11-28
Yeah...it's probably the proprietary iLink interface of Sony (based on Apple's FireWire). I'm planning on getting a very similar notebook (the TX670P with 1GB of RAM) and since I'll be getting an external mouse, does anyone know how to **turn off** the touchpad? Or is this impossible to do? I just hate those clunky things, that's all... ;)

---

### Post by trelirodia on 2005-12-03
I don't know if you managed to solve the reboot problem, but if not, here is a possible solution. It worked like great for me and I can now happily say that my upgrade to breezy was a success. It took a while though :-) 

[QUOTE=varunus]Guys, I found out the problem!

I posted to a bug report, and Matthew Garett was kind enough to give a fix.  This issue will be fixed in dapper, but until then, follow the following guide:

Open up your /boot/grub/menu.lst file using:

```
sudo gedit /boot/grub/menu.lst
```

Find your kernel lines (mine is 686, yours could be 386 or k7):

```
title           Ubuntu, kernel 2.6.12-10-686
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-686 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-686
savedefault
boot
```


Change it to:
```

title           Ubuntu, kernel 2.6.12-10-686
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-686 root=/dev/hda3 ro quiet splash reboot=h
initrd          /boot/initrd.img-2.6.12-10-686
savedefault
boot
```

(Add the reboot=h to the end of the kernel line.)

Reboot once again by turning off and on, and the next time you boot up and reboot, you'll be able to choose reboot from System->Log Off![/QUOTE]

FYI the thread it was posted in was: 
[http://www.ubuntuforums.org/showthread.php?t=75314&page=6&highlight=reboot+hang](http://www.ubuntuforums.org/showthread.php?t=75314&page=6&highlight=reboot+hang)

Best of luck, 
M

---

### Post by outdooricon on 2005-12-04
[QUOTE=trelirodia]I don't know if you managed to solve the reboot problem, but if not, here is a possible solution. It worked like great for me and I can now happily say that my upgrade to breezy was a success. It took a while though :-) 



FYI the thread it was posted in was: 
[http://www.ubuntuforums.org/showthread.php?t=75314&page=6&highlight=reboot+hang](http://www.ubuntuforums.org/showthread.php?t=75314&page=6&highlight=reboot+hang)

Best of luck, 
M[/QUOTE]

Excellent! That solved the problem... Thanks a lot! I'll update the main page.

---

### Post by &amp;ergio on 2005-12-17
I have bought it. And I have truubles whith sound. (I'm using debian stable (sarge) and 2.6.8 kernel)

Please, can you show your lsmod? What kernel are you using? What is sound modulename? Why oss, not alsa?

---

### Post by outdooricon on 2005-12-17
[QUOTE=&ergio]I have bought it. And I have truubles whith sound. (I'm using debian stable (sarge) and 2.6.8 kernel)

Please, can you show your lsmod? What kernel are you using? What is sound modulename? Why oss, not alsa?[/QUOTE]

lsmod shows:
```
Module                  Size  Used by
binfmt_misc            10888  1
rfcomm                 34972  0
hidp                   14848  2
l2cap                  22404  10 rfcomm,hidp
speedstep_centrino      7380  1
cpufreq_userspace       4444  1
cpufreq_stats           5124  0
freq_table              4484  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
pcmcia                 24584  2
sonypi                 23984  0
i915                   17920  1
drm                    58004  2 i915
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  13
af_packet              20232  4
rtc                    11832  0
hci_usb                13192  2
bluetooth              43012  8 rfcomm,hidp,l2cap,hci_usb
ipw2200                92680  0
firmware_class          9472  1 ipw2200
ieee80211              27012  1 ipw2200
ieee80211_crypt         5636  2 ipw2200,ieee80211
ohci1394               30644  0
yenta_socket           22540  1
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
tpm_nsc                 6528  0
tpm                     9504  1 tpm_nsc
hw_random               5268  0
snd_hda_intel          15872  2
snd_hda_codec          72064  1 snd_hda_intel
snd_pcm_oss            46368  0
snd_mixer_oss          16128  3 snd_pcm_oss
snd_pcm                78344  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  6 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  3 snd
snd_page_alloc         10120  2 snd_hda_intel,snd_pcm
intel_agp              21276  1
agpgart                32328  3 drm,intel_agp
dm_mod                 50364  1
joydev                  9280  0
tsdev                   7616  0
evdev                   9088  1
sr_mod                 15652  0
sbp2                   21128  0
scsi_mod              124872  2 sr_mod,sbp2
ieee1394               90936  2 ohci1394,sbp2
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  0
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  2 speedstep_centrino,thermal
fan                     4740  0
e100                   32768  0
mii                     5248  1 e100
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104316  4 hci_usb,ehci_hcd,uhci_hcd
ide_cd                 36996  0
cdrom                  33952  2 sr_mod,ide_cd
ide_disk               16128  3
ide_generic             1664  0
piix                    9476  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,piix
unix                   24624  865
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

```

I'm using kernel 2.6.12-10-386 . What do you mean by sound module name? I use mostly oss becase when i use (for example in firefox mplayer) the video and sound is choppy. But other things I use alsa for.. it's frustrating because it's a mix-and-match use of sound daemons.

---

### Post by &amp;ergio on 2005-12-26
Debian Sarge. xorg and kernel (2.6.14) from backports.org

troubles:

Video:
1) virtual size of xorg is 1368×768. ([outdooricon, can you grab desktop with gimp, for example and see it size? and could you show you /etc/X11/xorg.conf]("http://ubuntuforums.org/member.php?u=18143"))
2) I can't change backlight brightness (spictrl do nothing)
3) i810switch works, but it's impossible to switch lcd (not external) display off and I can't set video mode for the external display.

Events:
1) I can'n catch mute button (over sonypi)
2) for the Fn-F(1-12) sonypi catch press event, but for release event for the Fn-F(1-11) sonypi says, that event is unknown. For release event for Fn-F12 sony says nothing. Other buttons (volume +/-, wireless on, eject button) are catchable, but for some of that sonypi says the same events.
avmode, play, stop, ref and, ff works fine.

I have torubles with touchpad (synaptics),  but imho, it's my troubles.

Flash memory:
[http://www.webcon.ca/~imorgan/tifm21/]("http://www.webcon.ca/%7Eimorgan/tifm21/")

I can't switch wi-fi off
I dont know where is the wwan (egprs modem)


modem and pcmcia are untested.


P.S. There was dvd/cd player and picture viewer (from flash memory) (You neet to press AV mode button, when power is off)
That player is the linux kernel, some ext2fs and data files:
InstantON/initreg:        ASCII text, with CRLF line terminators
InstantON/intanton16.ico: MPEG sequence
InstantON/ivi:            x86 boot sector
InstantON/ivi-fs:         data
InstantON/ivi-id:         data
InstantON/reg:            Linux rev 1.0 ext2 filesystem data (mounted or unclean)
InstantON/samp:           Linux rev 1.0 ext2 filesystem data (mounted or unclean)
InstantON/tmp:            Linux rev 1.0 ext2 filesystem data (mounted or unclean)


manufactorer: [www.intervideo.com]("http://www.intervideo.com")

I don't know anything about this. I don't know how to boot it. It is need to specify correct root option.

---

### Post by outdooricon on 2005-12-29
> **&ergio]Debian Sarge. xorg and kernel (2.6.14) from backports.org

troubles:

Video:
1) virtual size of xorg is 1368&#215 said:**
> outdooricon, can you grab desktop with gimp, for example and see it size? and could you show you /etc/X11/xorg.conf[/URL])
2) I can't change backlight brightness (spictrl do nothing)
3) i810switch works, but it's impossible to switch lcd (not external) display off and I can't set video mode for the external display.

Events:
1) I can'n catch mute button (over sonypi)
2) for the Fn-F(1-12) sonypi catch press event, but for release event for the Fn-F(1-11) sonypi says, that event is unknown. For release event for Fn-F12 sony says nothing. Other buttons (volume +/-, wireless on, eject button) are catchable, but for some of that sonypi says the same events.
avmode, play, stop, ref and, ff works fine.

I have torubles with touchpad (synaptics),  but imho, it's my troubles.

Flash memory:
[http://www.webcon.ca/~imorgan/tifm21/]("http://www.webcon.ca/%7Eimorgan/tifm21/")

I can't switch wi-fi off
I dont know where is the wwan (egprs modem)


modem and pcmcia are untested.


P.S. There was dvd/cd player and picture viewer (from flash memory) (You neet to press AV mode button, when power is off)
That player is the linux kernel, some ext2fs and data files:
InstantON/initreg:        ASCII text, with CRLF line terminators
InstantON/intanton16.ico: MPEG sequence
InstantON/ivi:            x86 boot sector
InstantON/ivi-fs:         data
InstantON/ivi-id:         data
InstantON/reg:            Linux rev 1.0 ext2 filesystem data (mounted or unclean)
InstantON/samp:           Linux rev 1.0 ext2 filesystem data (mounted or unclean)
InstantON/tmp:            Linux rev 1.0 ext2 filesystem data (mounted or unclean)


manufactorer: [www.intervideo.com]("http://www.intervideo.com")

I don't know anything about this. I don't know how to boot it. It is need to specify correct root option.

whew, where too begin... first, attached is a picture showing my screenshot opened in gimp (circled in red are the dimensions which you can see are correctly 1366x768 ). Secondly, also attached is my xorg.conf file. 

Backlight brightness changing works fine for me (I would assume it works through sonypi, as my other FN features in the F# row do some things that aren't quite mentioned on my keyboard).

I have nothing to test the i810 switch with, so I can't comment on that one.

Mute button works fine for me (both the FN-F2 combo and the actual button on the front. I thought the button was actually a hardware switch, so it struck me really odd that it wasn't working for you). Which version of sonypi are you using?

When you say "avmode, play, stop, ref and, ff works fine" are you actually talking about the buttons right next to the power button? If so, I'm dying to know why yours works... mine are unresponsive. How are you able to see what signals all of these different buttons send?

Is your flashmemory actually working? I know about the project and am on the mailing list for it (there is an actual alpha out that I believe mounts these cards correctly now, however, the creator of this doesn't want people sending him emails about why it won't work on their own system,,, as it is still alpha).

i was sure the wifi was hardware switch too. are you saying that if slide the wireless butto over to off that the bluetooth and wireless lights don't turn off?

No clue about the wwan (as we've already discussed).

As far as the AVMode information is concerned. Here's what I know, there are some actual files that the AVMode uses that get installed on the Windows partition. I don't know which ones and I don't know where, but It uses some files that it installs in Windows. So I fear it is harder to use then simply getting the right boot option...

I'm glad you got this laptop finally, it's more exciting now to try to get all of this working now that I know I'm not alone in the effort. :)

---

### Post by mhx on 2005-12-30
the AV-mode button is controled all in windows

theres 2 things you need to install off the sony recovery cd
an application called Instant Mode and the drivers for for the button.  windows is required for this to work..

im installing ubuntu right now  I will let u guys know how it goes.. im dual booting with winxp.. i use slackware mainly, but i had alot of issues with slackware working with all the odds and ends the tx650 has.. I figured I would give this a try since I heard this OS is pretty cool.. I just got 1gb from newegg today..it does seem faster!

---

### Post by ph030 on 2006-01-03
Hi there :)

If I got this right from searching the Web, the TX650 is exactly the same as my TX1XP/B?

I just wanted to state, what's working for me and what's not:

Working:
DVD-Burner
Sound (not using the drivers delivered with the kernel, but the one directly from ALSA)
Wireless (via IPW2200)
Fullscreen-Resolution (via modified xorg.conf)
Brightness-Control (via 'echo {1-8} > /proc/acpi/sony/brightness)
PCMCIA (via yenta-socket)
Media-Buttons: play/pause, stop, prev, next
Touchpad (Scrolling, etc.)

Not Working:
every Fn+Fx-Kombo (don't even get any event by this)
Eject-Button
AV-Mode, Vol +/- (they all give the same event)

The rest is untested!

My system is running under Gentoo Linux and I'd be glad, if I could somehow get the other features to work, too.

I've made a little page about my experience with Gentoo on this book; you can have a look at it -> [here]("http://ph030.de/?q=node/6").

If you need more of my configs or have a solution to my open problems, please let me know :)

cheers,
ph030

---

### Post by outdooricon on 2006-01-04
> **ph030]Hi there :)

If I got this right from searching the Web, the TX650 is exactly the same as my TX1XP/B?

I just wanted to state, what's working for me and what's not:

Working:
DVD-Burner
Sound (not using the drivers delivered with the kernel, but the one directly from ALSA)
Wireless (via IPW2200)
Fullscreen-Resolution (via modified xorg.conf)
Brightness-Control (via 'echo {1-8} > /proc/acpi/sony/brightness)
PCMCIA (via yenta-socket)
Media-Buttons: play/pause, stop, prev, next
Touchpad (Scrolling, etc.)

Not Working:
every Fn+Fx-Kombo (don't even get any event by this)
Eject-Button
AV-Mode, Vol +/- (they all give the same event)

The rest is untested!

My system is running under Gentoo Linux and I'd be glad, if I could somehow get the other features to work, too.

I've made a little page about my experience with Gentoo on this book said:**
> here[/URL].

If you need more of my configs or have a solution to my open problems, please let me know :)

cheers,
ph030

Thanks for the info ph030... Interesting bit you did with xmodmap. Unfortunately I don't have an .xmodmap file in home directory... So maybe I'll just wait untill dapper to mess with that stuff. On a different note, What version of acpi and sonypi do you have?

---

### Post by mhx on 2006-01-06
whoo! i got mine work on my sony tx650 laptop..this thing is runing good no!  this is my first time with ubuntu.  im a slackware ho, but found a good post about this supporting my sony.. so gave it a whirl.  so far impressed.

at least i can be anywhere in the house on linux now!

the biggest problem i found was the /etc/wpa_supplicant.conf
1.  run

wpa_passphrase your_ssid | grep -v "#psk" | sudo tee -a /etc/wpa_supplicant.conf

it will just sit there enter your passphrase in press enter

2. sudo pico /etc/wpa_supplicant.conf
and make sure it looks like this: remove everything else

ctrl_interface=/var/run/wpa_supplicant

# reading passphrase from stdin
network={
        ssid="your_ssid"
        psk=your_key
}

3. sudo pico /etc/default/wpasupplicant
and make sure it looks like this: remove everything else
ENABLED=1

OPTIONS="-D ipw -i eth1 -c /etc/wpa_supplicant.conf -w"

best advice I can give for people

---

### Post by &amp;ergio on 2006-01-09
1) I know how turn on egprs modem !!! It's work!!!!
2) There are 9 levels of brightness, not 8. 0-8, not 1-8.
3) I can turn off wifi, but imho it isn't correct. I can't turn it on.

I'll put patches for sonypi, spicctrl and sony_acpi on the [http://sergio.spb.ru/vaio.xhtml](http://sergio.spb.ru/vaio.xhtml) tomorrow

but virtual size of xorg is still 1368×768.... ):  xorg version   6.9.0.dfsg.1-1
current config: [http://sergio.spb.ru/xorg.conf.html](http://sergio.spb.ru/xorg.conf.html) plain text: [http://sergio.spb.ru/xorg.conf](http://sergio.spb.ru/xorg.conf)
I don't know, what to do. ): log: [http://sergio.spb.ru/Xorg.0.log](http://sergio.spb.ru/Xorg.0.log)

---

### Post by &amp;ergio on 2006-01-09
1) I know how turn on egprs modem !!! It's work!!!!
2) There are 9 levels of brightness, not 8. 0-8, not 1-8.
3) I can turn off wifi, but imho it isn't correct. I can't turn it on.

I'll put patches for sonypi, spicctrl and sony_acpi on the [http://sergio.spb.ru/vaio.xhtml](http://sergio.spb.ru/vaio.xhtml) tomorrow

but virtual size of xorg is still 1368×768.... ):  xorg version   6.9.0.dfsg.1-1
current config: [http://sergio.spb.ru/xorg.conf.html](http://sergio.spb.ru/xorg.conf.html) plain text: [http://sergio.spb.ru/xorg.conf](http://sergio.spb.ru/xorg.conf)
I don't know, what to do. ): log: [http://sergio.spb.ru/Xorg.0.log](http://sergio.spb.ru/Xorg.0.log)

---

### Post by ph030 on 2006-01-09
Sorry for being away a few days :)

> Thanks for the info ph030... Interesting bit you did with xmodmap. Unfortunately I don't have an .xmodmap file in home directory

That's normal, just create a .Xmodmap by entering
```
touch ~/.Xmodmap
```
into a shell and fill it with what you need.
```
man xmodmap
```
may help with that.
Finally you need to start xmodmap with your X-Session, so depending on your WM/DE you can do it like this
```
xmodmap ~/.Xmodmap >> ~/.xinitrc
```
or enter it directly to your WM/DE - for Gnome this can be done via Gnome-Session IIRC.

For the other questions, I've got the latest sony_acpi from [Stelian's homepage](http://popies.net/) and the sonypi which is delivered with kernel 2.6.15-gentoo(vanilla-kernel + some patches.)

@&ergio
Have you tried my xorg.conf? For me it works.

---

### Post by &amp;ergio on 2006-01-09
I have the same troubles with your xorg.conf ([http://ph030.de/files/ph030/sony/tx1xp-xorg](http://ph030.de/files/ph030/sony/tx1xp-xorg))
or with outdoricon's file ([http://ubuntuforums.org/attachment.php?attachmentid=4893&d=1135833672](http://ubuntuforums.org/attachment.php?attachmentid=4893&d=1135833672)) :(

---

### Post by ph030 on 2006-01-10
@&ergio
I don't know if I missed it, but can you please tell me, what exactly your problem is?
For me, making an App fullscreen gives no problems, no overlapping to other vr-desktops, nor missing parts of the window, not anything at all, just like under WinXP.
The only thing I need to mention here is that it only works for me with the latest unstable version of x.org, which is 6.8.99.15-r4 on Gentoo(haven't tested the final 6.9/7.0, yet).

---

### Post by &amp;ergio on 2006-01-10
[quote=ph030]@&ergio
I don't know if I missed it, but can you please tell me, what exactly your problem is?
For me, making an App fullscreen gives no problems, no overlapping to other vr-desktops, nor missing parts of the window, not anything at all, just like under WinXP.
The only thing I need to mention here is that it only works for me with the latest unstable version of x.org, which is 6.8.99.15-r4 on Gentoo(haven't tested the final 6.9/7.0, yet).[/quote] I have correct resolution ( 1366×768 ), but incorrect virtual screen resolution (1368×768 ). In /var/log/Xorg.0.log I have (**) I810(0): Virtual size is 1368x768 (pitch 2048 ) I use Debian stable with backports (backport.org). This problem was with 6.8.2.dfsg.1-10bpo1 version too.

---

### Post by outdooricon on 2006-01-10
[QUOTE=&ergio]I have correct resolution ( 1366&#215;768 ), but incorrect virtual screen resolution (1368&#215;768 ). In /var/log/Xorg.0.log I have (**) I810(0): Virtual size is 1368x768 (pitch 2048 ) I use Debian stable with backports (backport.org). This problem was with 6.8.2.dfsg.1-10bpo1 version too.[/QUOTE]

I just verified what you're saying... I found this bit in my xorg.0.log file:
```
(II) I810(0): Generic Monitor: Using hsync range of 43.89-48.51 kHz
(II) I810(0): Generic Monitor: Using vrefresh value of 60.00 Hz
(II) I810(0): Not using mode "1366x768" (no mode of this name)
(II) I810(0): Correcting stride (1368 -> 5504)
(II) I810(0): Increasing the scanline pitch to allow tiling mode (1376 -> 2048).(--) I810(0): Virtual size is 1368x768 (pitch 2048)
(**) I810(0):  Built-in mode "1360x768"
(**) I810(0):  Built-in mode "1024x768"
(==) I810(0): DPI set to (75, 75)

```

This doesn't seem to affect my desktop, However, in gdm, I have noticed that before login, I do have that extra column of pixels again, basically showing that it's running in 1368. I have no answers right now, only the verification that my log says what yours does. I am interested in how you got the epgrs modem to work...

---

### Post by &amp;ergio on 2006-01-10
[http://sergio.spb.ru/vaio/index.xhtml](http://sergio.spb.ru/vaio/index.xhtml)

---

### Post by &amp;ergio on 2006-01-10
[quote=outdooricon]I just verified what you're saying... I found this bit in my xorg.0.log file:
```
(II) I810(0): Generic Monitor: Using hsync range of 43.89-48.51 kHz
(II) I810(0): Generic Monitor: Using vrefresh value of 60.00 Hz
(II) I810(0): Not using mode "1366x768" (no mode of this name)
(II) I810(0): Correcting stride (1368 -> 5504)
(II) I810(0): Increasing the scanline pitch to allow tiling mode (1376 -> 2048).(--) I810(0): Virtual size is 1368x768 (pitch 2048)
(**) I810(0):  Built-in mode "1360x768"
(**) I810(0):  Built-in mode "1024x768"
(==) I810(0): DPI set to (75, 75)

``` 
This doesn't seem to affect my desktop, However, in gdm, I have noticed that before login, I do have that extra column of pixels again, basically showing that it's running in 1368. I have no answers right now, only the verification that my log says what yours does. I am interested in how you got the epgrs modem to work...[/quote]
but some posts before you said that all work fine??

---

### Post by outdooricon on 2006-01-11
[QUOTE=&ergio]but some posts before you said that all work fine??[/QUOTE]
Yes, that is because at the GMD login, I rarely use my mouse, so it was by mere accident that I moved the cursor over to the far side of the screen and noticed that the window moved over a little. After the GDM Login, the desktops size is fine.

---

### Post by &amp;ergio on 2006-01-11
[quote=outdooricon]Yes, that is because at the GMD login, I rarely use my mouse, so it was by mere accident that I moved the cursor over to the far side of the screen and noticed that the window moved over a little. After the GDM Login, the desktops size is fine.[/quote]
I don't use gdm.. startx instead (: I'll try..

---

### Post by Mausoleum on 2006-01-13
So I looked a little bit into the resolution issue and it looks like X.org is exposing 3 resolutions using the xrandr extension: 1366x768, 1024x768, 1368x768.  The first one is 1366x768, but for some reason, X.org is choosing the last one as default.  This is not a gnome issue (verified by running naked X:  startx bash -- :1  )  The Gnome App just uses xrandr to change resolutions.  At any rate, I am still trying to figure out how to tell X to use 1366x768 by default.  So far, changing it per-user work, but isn't quite the right answer, IMHO.

Martin

PS: Anyone know how to put the laptop into sleep (not hibernate) mode?  executing /etc/acpi/sleep.sh  did nothing for me

---

### Post by rojus on 2006-01-19
[QUOTE=Mausoleum] 
PS: Anyone know how to put the laptop into sleep (not hibernate) mode?  executing /etc/acpi/sleep.sh  did nothing for me[/QUOTE]

check out the first line of 
/etc/default/acpi-support
But it does **not** really work. It kind of does but takes more than a minute to wake up. It seems to like to boot from cd-rom, since it starts off on wake-up first. But then nothing for a long time until it comes back up. 
We should work on this one definitely.

---

### Post by blahyada on 2006-01-25
[QUOTE=&ergio]1) I know how turn on egprs modem !!! It's work!!!!
2) There are 9 levels of brightness, not 8. 0-8, not 1-8.
3) I can turn off wifi, but imho it isn't correct. I can't turn it on.

I'll put patches for sonypi, spicctrl and sony_acpi on the [http://sergio.spb.ru/vaio.xhtml](http://sergio.spb.ru/vaio.xhtml) tomorrow

but virtual size of xorg is still 1368×768.... ):  xorg version   6.9.0.dfsg.1-1
current config: [http://sergio.spb.ru/xorg.conf.html](http://sergio.spb.ru/xorg.conf.html) plain text: [http://sergio.spb.ru/xorg.conf](http://sergio.spb.ru/xorg.conf)
I don't know, what to do. ): log: [http://sergio.spb.ru/Xorg.0.log](http://sergio.spb.ru/Xorg.0.log)[/QUOTE]

sorry if i missed it, but how did you get your gprs modem to work? i've been trying to figure this out forever.  thanks.

---

### Post by &amp;ergio on 2006-01-26
[quote=blahyada]sorry if i missed it, but how did you get your gprs modem to work? i've been trying to figure this out forever.  thanks.[/quote]
[http://sergio.spb.ru/vaio/index.xhtml](http://sergio.spb.ru/vaio/index.xhtml)

---

### Post by &amp;ergio on 2006-01-31
Sony don't want to provide source code of dvd player.
The answer was:
"We regret that we have been unable to resolve your request. However, you have been provided with all the support and/or contact information for this issue available through e-mail. If you wish to discuss this issue further, we recommend you contact our telephone support representatives. The VAIO Customer Information Service Center is available toll-free. We are available at 888-476-6972, 24 hours a day, 7 days a week. Outside the US or Canada, you may contact us at 239-768-7676."

I don't speak english very well. Can anyobody contact with the Sony and get out source code of dvd player.

P.S. Under dvd player, I mean whole system, not the player itselfs.
P.P.S. The dvd player, which turns on by the avmode button from off state is based on linux.

---

### Post by outdooricon on 2006-02-02
I think you're contacting the wrong people... you should send an email to intervideo about their instanton software.. I unfortunately have no extra time right now, so I can't contact anyone, but give intervideo a try, not sony. Since this is all gpl, they should have to give the source, right?

---

### Post by llopis on 2006-02-03
Thanks for the great thread. I just got a TX650P and installed Breezey without a hitch.

I got all the updates and I was able to use the special features of the pad without installing any extra drivers by hand (just tweakig the xorg.conf file as described in the first post).

One question: Has anybody gotten suspend to work? Hibernate is working fine, but it takes too long to restore from disk. I would really like to have the option to suspend, but when I try it, it never comes back. Any thoughts?

Thanks!

---

### Post by &amp;ergio on 2006-02-03
[quote=outdooricon]I think you're contacting the wrong people... you should send an email to intervideo about their instanton software.. I unfortunately have no extra time right now, so I can't contact anyone, but give intervideo a try, not sony. Since this is all gpl, they should have to give the source, right?[/quote]
[FONT=Arial][SIZE=2][COLOR=#000000]
	[/COLOR][/SIZE][/FONT]intervideo:
[FONT=Arial][SIZE=2][COLOR=#000000]Thank you for contacting Intervideo support. At this time,Intervideo TSD (Technical support department) does not offer support onOEM bundle software and support on this product will need to go to yourOEM vendor for further assistance. 
[/COLOR][/SIZE][/FONT]

[FONT=Arial][SIZE=2][COLOR=#000000]:cry:
[/COLOR][/SIZE][/FONT]

---

### Post by &amp;ergio on 2006-02-03
[quote=llopis]
One question: Has anybody gotten suspend to work? Hibernate is working fine, but it takes too long to restore from disk. I would really like to have the option to suspend, but when I try it, it never comes back. Any thoughts?
 Thanks![/quote]



The same ):

---

### Post by llopis on 2006-02-08
Oh, one more thing. Breezy is working great, but I noticed that sometimes, when I come back from hibernation, the brightness keys don't seem to work (Fn + F4/F5). Has anybody seen that? Any idea what to do about it?
Thanks again for this very useful thread!

---

### Post by Herios on 2006-02-09
moved up to gutsy, trying to get back in the swing of things with this laptop. My last post was rather pathetic. Will try and put something useful here if I can.

---

### Post by &amp;ergio on 2006-02-15
Please, anybody, contact with sony!

[quote=&ergio]Sony don't want to provide source code of dvd player.
The answer was:
"We regret that we have been unable to resolve your request. However, you have been provided with all the support and/or contact information for this issue available through e-mail. If you wish to discuss this issue further, we recommend you contact our telephone support representatives. The VAIO Customer Information Service Center is available toll-free. We are available at 888-476-6972, 24 hours a day, 7 days a week. Outside the US or Canada, you may contact us at 239-768-7676."

I don't speak english very well. Can anyobody contact with the Sony and get out source code of dvd player.

P.S. Under dvd player, I mean whole system, not the player itselfs.
P.P.S. The dvd player, which turns on by the avmode button from off state is based on linux.[/quote]

---

### Post by huliber on 2006-02-18
[QUOTE=llopis]
One question: Has anybody gotten suspend to work? Hibernate is working fine, but it takes too long to restore from disk. I would really like to have the option to suspend, but when I try it, it never comes back. Any thoughts?
[/QUOTE]

I disabled the splash screen on boot

```

kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet reboot=h resume=/dev/hda3

```

and I enabled RESET_DRIVE on resume (/etc/default/acpi-support)

```
# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
RESET_DRIVE=true

```

Now hibernate/resume works for me.

---

### Post by hsimah on 2006-04-03
Hi guys. Hope I am not bringing this thread back form the dead. I found it via google. It is great and has helped me with many issues with my new Vaio TX.

I'm from Australia so we don't get the same models over here. I have a VGN-TX27GP. It was realesed about 3 weeks ago and is pretty sweet, although expensive :(

I am a Slacker at heart, in fact I haven't picked up another distro... ever. But Slack just didn't cut it with this laptop (I think someone else said this earlier) and I was reccommended Ubuntu. Nice install, and everything worked right out of the box. GNOME is so much better than KDE (I'm a console whore and rarely use a GUI on Linux).

Anyhoo, just saying that the reboot problem helped me a lot. I have remapped the AV keys to Play, Stop, Next Track, Previous Track, but Eject won't register as a button. Anyone get their drive to auto eject? Also the volume up/down buttons only register as the one (this is on the front of the laptop next to mute) button.

Also, from what I read the TI chipset used for the SD and Memorystick slots still doesn't work. What a pity :(

Hope I don't get in trouble for bumping this :) We should put it on a site somewhere to help all Vaio users :D

---

### Post by deeeed on 2006-04-30
Hi
i have a problem to compil the synaptic driver ... I got lots of erros when i try to run make :
```

root@clara:~/synaptics-0.14.4# make
...
synaptics.c:235: attention : assignment makes pointer from integer without a cast
synaptics.c: In function ‘SynapticsPreInit’:
synaptics.c:283: attention : assignment makes pointer from integer without a cast
synaptics.c: In function ‘DeviceControl’:
synaptics.c:514: erreur: ‘BadValue’ undeclared (first use in this function)
synaptics.c:514: erreur: (Chaque identificateur non déclaré est rapporté une seule fois
synaptics.c:514: erreur: pour chaque fonction dans laquelle il apparaît.)
synaptics.c: In function ‘DeviceOn’:
synaptics.c:523: erreur: déréférencement d'un pointeur de type incomplet
synaptics.c:532: erreur: ‘Success’ undeclared (first use in this function)
synaptics.c:549: erreur: déréférencement d'un pointeur de type incomplet
synaptics.c: In function ‘DeviceOff’:
synaptics.c:557: erreur: déréférencement d'un pointeur de type incomplet
synaptics.c:573: erreur: déréférencement d'un pointeur de type incomplet
synaptics.c:574: erreur: ‘Success’ undeclared (first use in this function)
synaptics.c: In function ‘DeviceClose’:
synaptics.c:581: erreur: déréférencement d'un pointeur de type incomplet
synaptics.c: In function ‘DeviceInit’:
synaptics.c:592: erreur: déréférencement d'un pointeur de type incomplet
synaptics.c:601: erreur: déréférencement d'un pointeur de type incomplet
synaptics.c:603: erreur: syntax error before ‘dev’
synaptics.c:618: erreur: ‘Success’ undeclared (first use in this function)
synaptics.c: Hors de toute fonction :
synaptics.c:724: erreur: ‘timerFunc’ declared as function returning a function
synaptics.c: In function ‘timerFunc’:
synaptics.c:736: attention : assignment makes integer from pointer without a cast
synaptics.c:744: attention : usage en arithmétique d'un pointeur vers une fonction
synaptics.c:744: erreur: membre gauche de l'affectation invalide
synaptics.c:745: attention : ISO C interdit les comparaisons ordonnées de pointeurs vers des fonctions
synaptics.c:746: erreur: membre gauche de l'affectation invalide
synaptics.c: Hors de toute foncation :
synaptics.c:1714: erreur: syntax error before ‘xDeviceCtl’
synaptics.c: In function ‘ControlProc’:
synaptics.c:1717: erreur: ‘Success’ undeclared (first use in this function)
synaptics.c: In function ‘SwitchMode’:
synaptics.c:1731: erreur: ‘Success’ undeclared (first use in this function)
make: *** [synaptics.o] Erreur 1

```
Actually my battery life is about 4h45min and i would like to know how much time it is on yours ??
I'd like to disable cdrom and others stuff like in windows to get more battery life, did you try that ?
Another problem with the display because when i move my mouse to the far side of the screen the window move a little (not only for gdm, i have this problem with gnome and others wm).
Thx

Sorry for my english witch is so... not english. ;) 


[QUOTE=outdooricon]I just bought this laptop (TX650), and LOVE IT! So, the intention here is to provide an area where people can all discuss how to get this beauty working great in linux as well as allow me to provide my progress.

**What I did:**
Booted it up, went through the usual Windows junk. Then, ran the recovery backup utility which backs up everything onto two dvds. Then I installed Breezy (annihilating everything on the disk and starting fresh). Also, I bought an extra stick of 1 GB ram from Newegg and put that in this. It runs even faster and I think is worth the investment.

**What Works right away after Breezy Install:**
[LIST]
[*]CD / DVD Player
[*]Wi-Fi
[*]Sound
[*]Mute Sound Button
[*]Ethernet
[*]Suspend to Disk (even my Wi-Fi connection was NOT lost)
[*]FN Keys
[*]Headphones plug
[*]USB
[*]Bluetooth
[/LIST]

**What doesn't work right away after Breezy Install:**
[LIST]
[*]Touchpads special abilities (scrolling, multiple tapping, etc.) Even the touchpad use itself is a little flakey, If you quickly move the mouse and lift off your finger, it seems to take that as select. It gets real frustrating when using the Preferences menu because I require two mouse movements on the pad to get to the bottom of the menu, but If you don't do it carefully, you'll select whatever the mouse is hovering over when you lift the finger off the pad. **Fix is provided below**
[*]Volume Buttons
[*]All AV Buttons
[*]WWAN
[*]Reboot **Fix is provided below**
[*]The Battery doesn't appear to ever be marked as fully charged. The icon always shows the plug-in with the lightning bolt, and never just a plug-in. The wierd thing is, Windows never recognized it as fully charged either. This is a minor annoyance.
[*]SD Card / Memory Stick Slots
[*]Native Resolution Display ( xorg.conf says the correct 1366x768 although the resolution utility says 1368x768, resulting in an extra column of pixels on the screen which is annoying but still functional) **Fix is provided below**
[/LIST]

**What I haven't yet tested:**
[LIST]
[*]Microphone plug
[*]PCMCIA Slot
[*]Modem
[*]CD-R/RW, DVD-R/RW
[*]VGA Out
[*]IS400 slot
[/LIST]

**Things Worth Mentioning:**
[LIST]
[*]I use the MPlayer plugin instead of Totem in Firefox. If you're getting choppy streams of video and audio, right-click on the mPlayer plug-in that's playing and choose configure. Then set video output to 'x11' and audio output to 'oss'. The oss selection is key to eliminating the choppyness. I've found that OSS seems the best to use overall for sound on this machine as it recognizes the RealTek Audio. I also switched my volume changer in the ubuntu bar to control OSS's PCM-2, which is the speaker output. The main OSS volume will control the volume through the headphones.
[*]WPA works beautifully after install via Synaptic! After configuring the wpa conf file, just run the following code to test it out and connect:```
sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd

``` Then run this to get dhcp:```
sudo dhclient eth1
```
[*]I have a Logitech T270 bluetooth mouse that I hooked up with this. To get it working, all I had to do was first run the following to see if the mouse is detected (the mouse must be turned on for this to work): ```
sudo hcitool scan
``` This should end up showing the mouse along with it's MAC address. Then, to connect to the mouse, run this (where MAC_ADDRESS is replaced with the MAC address you found with the scan): ```
sudo hidd --connect MAC_ADDRESS
``` Now, you're mouse should be working great on the computer. To have the mouse start each time with the computer, make the following changes in /etc/default/bluez-utils (where MAC_ADDRESS is replaced with the MAC address you found with the scan):```
HIDD_ENABLED=1
HIDD_OPTIONS="--connect MAC_ADDRESS --server"

```

[/LIST]

**Fixes:**
[LIST]
[*]_**Touchpad**_. Most of the information here is derived from [this post]("http://ubuntuforums.org/showthread.php?t=78904") (most if not all recognition for the following should go to scubajeff for figuring all of this out). However, I felt it would be easier if I put here the exact information that I applied to this laptop. First, you need to get the 'build-essential' package ('Make' is the most importent package you need which should be included as a dependency, if not install 'make' as well) in Synaptic. Then, download the new Synaptics/ALPS driver [here]("http://web.telia.com/~u89404340/touchpad/"). Unpackage it and type within the directory: ```
sudo make
``` Then we need to backup the old driver and then copy over the driver we just compiled: ```
sudo cp /usr/X11R6/lib/modules/input/synaptics_drv.o /usr/X11R6/lib/modules/input/synaptics_drv.o.bckp
sudo cp synaptics_drv.o /usr/X11R6/lib/modules/input/
``` Now, we need to deal with the fact that the event corresponding with the touchpad may change if anouther mouse is in use as well. When we go to editing the xorg.conf file next, we will be changing how it recognizes the touchpad, so we need to prepare for this. First we need to create the rule: ```
sudo nano /etc/udev/alps.rules
``` In which we will place the following line: ```
BUS="serio", SYSFS{description}="i8042 Aux Port", KERNEL="event?", SYMLINK="input/alps"
``` Now we need to create a symlink to that rule (if you are wondering why we are doing all of this, please click the above post link and read scubajeffs hard work): ```
sudo ln -s /etc/udev/alps.rules /etc/udev/rules.d/40_alps.rules
``` Next, we must edit the xorg.conf file: ```
sudo nano /etc/X11/xorg.conf
```Finally, we need to change the 'InputDevice' section for the 'Synaptics Touchpad' to be the following: ```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
#       Option          "Device"                "/dev/psaux"
        Option          "Device"                "/dev/input/alps"
#       Option          "Protocol"              "auto-dev"
        Option          "Protocol"              "event"
        Option          "SHMConfig"             "true"
        Option          "LeftEdge"              "120"
        Option          "RightEdge"             "830"
        Option          "TopEdge"               "120"
        Option          "BottomEdge"            "650"
        Option          "FingerLow"             "14"
        Option          "FingerHigh"            "15"
        Option          "MaxTapTime"            "180"
        Option          "MaxTapMove"            "110"
        Option          "EmulateMidButtonTime"  "75"
        Option          "VertScrollDelta"       "20"
#       Option          "HorizScrollDelta"      "0"
        Option          "HorizScrollDelta"      "20"
        Option          "MinSpeed"              "0.3"
        Option          "MaxSpeed"              "0.75"
        Option          "AccelFactor"           "0.015"
        Option          "EdgeMotionMinSpeed"    "200"
        Option          "EdgeMotionMaxSpeed"    "200"
        Option          "UpDownScrolling"       "1"
        Option          "CircularScrolling"     "1"
        Option          "CircScrollDelta"       "0.1"
        Option          "CircScrollTrigger"     "2"
        Option          "GuestMouseOff"         "0"
EndSection

```
You can change these features to represent exactly what you want. Also, note that each commented out lines is what was originally in this file but has been replaced by the line right below it. Now, restart your laptop. Welcome to a fully featured touchpad!
[*]_**Reboot**_. Much thanks goes to trelirodia for this fix. We need to edit the  /boot/grub/menu.lst file: ```
sudo nano /boot/grub/menu.lst
``` We want to change this section (the actual kernel number you have may be slightly different): ```

title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot
```
to the following (Note the addition of "reboot=h"): ```

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash reboot=h
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot
```
Now just shutdown and bootup the laptop, and be ready for effortless reboots!
[*]_**Native Screen Resolution**_. Well, I feel pretty stupid about this one as I was just about to write up a seperate thread to see if anyone could help me with this one. Let's just say, if all else fails, try the obvious. To get this to be 1366x768 in stead of 1368x768 (thus eliminating that extra column on the side of the desktop), simply go to the Screen Resolution
 utility and select the 1366x768 'Resolution' instead. No biggie.
[/LIST]
**NOTE:** I will update this as I discover more issues / fixes. Please feel free to join in helping me to figure out how to get all of this to work.[/QUOTE]

---

### Post by llopis on 2006-05-06
[QUOTE=deeeed]Another problem with the display because when i move my mouse to the far side of the screen the window move a little (not only for gdm, i have this problem with gnome and others wm).[/QUOTE]

Do you realize that the answer to that question is in the huge quote you left in your post?

---

### Post by deeeed on 2006-05-12
Actually no, i don't realize :s
Maybe you can tell me more about this paste? 
;)

---

### Post by matthewc on 2006-06-03
I found this thread looking for info on configuring the VGA output for my TX690. At the time (a few weeks ago) I got it working almost - I couldn't get the full wide-screen resolution for the built in screen and also the external output working at the same time. Now, since upgrading to Dapper 6.06 release I actually could no longer get wide-screen 1366x768 working at all, whatever I tried. I don't quite understand, but something to do with x upgrades meant the larger built in modes were no longer being recognised, and this stopped it working. The answer is the following option in the Monitor section:

```
Option "UseEdidFreqs" "0"
```

I think that line above is necessary for anyone using Dapper on one of the TX series. Unfortunately Dapper doesn't seem to correctly configure the resolution for these laptops - Breezy did (almost, as per the OP) which is a real shame. I haven't yet tested the final release CD, but the RC CD left me with 1024x768 :(

Now, for more fun: here is the entire section of my xorg.conf for setting up one big desktop extended onto an external monitor, in my case a flat panel running at 1280x1024.

Have fun, and I hope this saves someone the hours it took me to get all of this working :)

```

Section "Device"
        Identifier      "Intel Corporation Intel Default Card"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option          "MonitorLayout" "CRT,LFP"
        Screen          1
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Option          "UseEdidFreqs" "0"
EndSection

Section "Device"
        Identifier      "Intel VGA Out"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option          "MonitorLayout" "CRT,LFP"
        Screen          0
EndSection

Section "Monitor"
        Identifier      "Monitor VGA Out"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Intel Default Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1366x768"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Second Screen"
        Device          "Intel VGA Out"
        Monitor         "Monitor VGA Out"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Option          "Xinerama" "on"
        Option          "Clone" "off"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
        Screen          "Second Screen" RightOf "Default Screen"
EndSection


```

---

### Post by mfzap on 2006-06-06
Hi everyone!

Dapper runs great on my TX790P.

The installer setup dual boot with XP without any problems.

I did not have to do anything special for wifi, touchpad, sound, or display.

Wireless Logitech mouse worked just by sliding in the USB connector, no questions asked.

Gnome set the resolution to 1368x768 which as noted is 2 pixels too wide but I simply changed it in my preferences to another provided option of 1366x768.

Gnome seems to understand most of the special buttons but not all of them. Important ones like Power and Eject are fine.

Seems like with every version Ubuntu is adding more native support for laptops.

BTW, perhaps you all already know this but NetworkManager is really slick and lets you pick wifi networks from a pulldown menu on a Gnome applet:
[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

I'm here trying to read info on getting the modem supported. That's the first thing that stumped me. ;-)

Cheers,
Martin

---

### Post by yanychar on 2006-09-06
I run Dapper on TX770P. It has had a problem with multi-tapping (no locking drag).

I had to increase my MaxTapTime to 270 or above to fix the dragging. Works Great now.
```

Section "InputDevice"
	...
	Option 		"MaxTapTime" 		"270"
	...
EndSection

```

 Thanks for the help to TwiceOver [here]("http://www.ubuntuforums.org/showthread.php?t=78904&page=6").

---

### Post by Gzae on 2007-03-26
i think i find source of av mode player for tx series , but cant setup 
[http://www.sony.net/Products/Linux/Download/VGN-TX_Series_InstantMode_version_122.html](http://www.sony.net/Products/Linux/Download/VGN-TX_Series_InstantMode_version_122.html)
[http://www.sony.net/Products/Linux/Download/VGN-TX_Series_InstantMode_version_103_110.html](http://www.sony.net/Products/Linux/Download/VGN-TX_Series_InstantMode_version_103_110.html)

if anybody installing that - please write howto

---

### Post by yanychar on 2007-03-27
> **Gzae said:**
> i think i find source of av mode player for tx series , but cant setup 
[http://www.sony.net/Products/Linux/Download/VGN-TX_Series_InstantMode_version_122.html](http://www.sony.net/Products/Linux/Download/VGN-TX_Series_InstantMode_version_122.html)
[http://www.sony.net/Products/Linux/Download/VGN-TX_Series_InstantMode_version_103_110.html](http://www.sony.net/Products/Linux/Download/VGN-TX_Series_InstantMode_version_103_110.html)

if anybody installing that - please write howto

It is just a GPL'ed part of sources for Instant Mode. All real stuff is proprietary and not provided.

---

