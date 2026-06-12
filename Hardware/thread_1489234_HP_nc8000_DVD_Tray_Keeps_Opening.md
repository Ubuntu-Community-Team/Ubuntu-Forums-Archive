---
title: "HP nc8000 DVD Tray Keeps Opening"
date: 2010-05-20
forum: Hardware
---

### Post by bbking67 on 2010-05-20
My system is an old HP nc8000 (Compaq) laptop.

After installing Ubuntu 10.4 LTS everything was fine.  I followed some instructions to install my Novatel wireless adapter which, after some flailing about, worked.  I'm no Linux whiz...

In any case after I got the Novatel working, my DVD drive keeps popping open randomly (usually after a few seconds).

If I reboot into CMOS setup it works fine or if I boot something off the disc.. however as soon as Ubuntu loads from the hard disc it wants to constantly eject the disc.

I'm thinking about re-installing... but a quick fix would be nicer!

HELP!!!!

---

### Post by tgalati4 on 2010-05-20
After booting up, open a terminal:

dmesg | tail -100

Look for messages related to the DVD drive.

There's a youtube video of someone rigging up a baby's cradle to a DVD drive tray.  So random DVD tray motion can be useful.

---

### Post by phillips321 on 2010-05-21
check for a process running the following commands

```
watch eject -T
```

I usually add this to init on mates machines when they stupidly give me root access. (Only way i know to teach them!)

---

### Post by bbking67 on 2010-05-21
ckarson@nc8000:~$ dmesg|tail -100
[   22.287955] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   22.287957] [drm]   Encoders:
[   22.287960] [drm]     CRT1: INTERNAL_DAC1
[   22.287962] [drm] Connector 1:
[   22.287963] [drm]   DVI-D
[   22.287965] [drm]   HPD1
[   22.287968] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[   22.287970] [drm]   Encoders:
[   22.287972] [drm]     DFP1: INTERNAL_TMDS1
[   22.287974] [drm] Connector 2:
[   22.287976] [drm]   LVDS
[   22.287978] [drm]   DDC: 0x6c 0x6c 0x6c 0x6c 0x6c 0x6c 0x6c 0x6c
[   22.287981] [drm]   Encoders:
[   22.287982] [drm]     LCD1: INTERNAL_LVDS
[   22.287984] [drm] Connector 3:
[   22.287986] [drm]   S-video
[   22.287988] [drm]   Encoders:
[   22.287990] [drm]     TV1: INTERNAL_DAC2
[   22.296294] type=1505 audit(1274451514.177:9):  operation="profile_load" pid=1888 name="/usr/bin/evince"
[   22.517938] Bluetooth: Core ver 2.15
[   22.552970] NET: Registered protocol family 31
[   22.552975] Bluetooth: HCI device and connection manager initialized
[   22.552979] Bluetooth: HCI socket layer initialized
[   22.556768] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   22.557246] usbcore: registered new interface driver btusb
[   22.689298] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:00/LNXVIDEO:00/input/input6
[   22.689526] ACPI: Video Device [C0CF] (multi-head: yes  rom: no  post: no)
[   22.775656] type=1505 audit(1274451514.653:10):  operation="profile_load" pid=1888 name="/usr/bin/evince-previewer"
[   22.789733] tpm_inf_pnp 00:0c: Found C197 with ID IFX0101
[   22.789776] tpm_inf_pnp 00:0c: TPM found: config base 0xe0, data base 0x1400, chip version 0x0006, vendor id 0x15d1 (Infineon), product id 0x0006 (SLD 9630 TT 1.1)
[   22.983774] type=1505 audit(1274451514.861:11):  operation="profile_load" pid=1888 name="/usr/bin/evince-thumbnailer"
[   23.029854] irda_init()
[   23.029873] NET: Registered protocol family 23
[   23.039799] parport_pc 00:05: reported by Plug and Play ACPI
[   23.039850] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   23.056631] Bluetooth: L2CAP ver 2.14
[   23.056635] Bluetooth: L2CAP socket layer initialized
[   23.061152] Detected unconfigured HP nc8000 family SMSC IrDA chip, pre-configuring device.
[   23.061157] Setting up Intel 82801 controller and SMSC device
[   23.061174] Detected Chip id: 0x5a, setting up registers...
[   23.061316] found SMC SuperIO Chip (devid=0x5a rev=00 base=0x004e): LPC47N227
[   23.061332] smsc_superio_flat(): fir: 0x130, sir: 0x2f8, dma: 03, irq: 5, mode: 0x0e
[   23.061347] SMsC IrDA Controller found
[   23.061349]  IrCC version 2.0, firport 0x130, sirport 0x2f8 dma=3, irq=5
[   23.061404] smsc_ircc_set_sir_speed(), Setting speed to: 9600
[   23.061416] No transceiver found. Defaulting to Fast pin select
[   23.079172] ppdev: user-space parallel port driver
[   23.100397] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.100402] Bluetooth: BNEP filters: protocol multicast
[   23.138062] lp0: using parport0 (interrupt-driven).
[   23.169064] Bridge firewalling registered
[   23.193056] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   23.193981] IrDA: Registered device irda0
[   23.197043] yenta_cardbus 0000:02:06.3: CardBus bridge found [103c:088c]
[   23.280659] Bluetooth: SCO (Voice Link) ver 0.6
[   23.280663] Bluetooth: SCO socket layer initialized
[   23.345215] [drm] fb mappable at 0x98040000
[   23.345219] [drm] vram apper at 0x98000000
[   23.345221] [drm] size 5913600
[   23.345223] [drm] fb depth is 24
[   23.345225] [drm]    pitch is 5632
[   23.345773] yenta_cardbus 0000:02:06.3: ISA IRQ mask 0x0038, PCI irq 10
[   23.345777] yenta_cardbus 0000:02:06.3: Socket status: 30000006
[   23.345782] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #08 to #0c
[   23.345794] yenta_cardbus 0000:02:06.3: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x5fff
[   23.345799] pcmcia_socket pcmcia_socket2: cs: IO port probe 0x4000-0x5fff: clean.
[   23.346376] yenta_cardbus 0000:02:06.3: pcmcia: parent PCI bridge Memory window: 0x90000000 - 0x903fffff
[   23.346380] yenta_cardbus 0000:02:06.3: pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x2dffffff
[   23.360768] fb0: radeondrmfb frame buffer device
[   23.360773] registered panic notifier
[   23.360783] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
[   23.370949] vga16fb: initializing
[   23.370955] vga16fb: mapped to 0xc00a0000
[   23.370962] vga16fb: not registering due to another framebuffer present
[   23.423060] psmouse serio5: ID: 10 00 64
[   23.791011] Bluetooth: RFCOMM TTY layer initialized
[   23.791018] Bluetooth: RFCOMM socket layer initialized
[   23.791021] Bluetooth: RFCOMM ver 1.11
[   23.873326] Console: switching to colour frame buffer device 175x65
[   23.924226] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   23.925946] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   23.926674] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   23.927314] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   23.928198] pcmcia_socket pcmcia_socket2: cs: IO port probe 0x100-0x3af: clean.
[   23.929901] pcmcia_socket pcmcia_socket2: cs: IO port probe 0x3e0-0x4ff: clean.
[   23.931509] pcmcia_socket pcmcia_socket2: cs: IO port probe 0x820-0x8ff: clean.
[   23.932296] pcmcia_socket pcmcia_socket2: cs: IO port probe 0xc00-0xcf7: clean.
[   23.933147] pcmcia_socket pcmcia_socket2: cs: IO port probe 0xa00-0xaff: clean.
[   23.934272] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   24.457971] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: clean.
[   24.459680] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: clean.
[   24.461775] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[   24.462416] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[   24.463274] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[   26.687421] input: PS/2 Generic Mouse as /devices/platform/i8042/serio4/serio5/input/input7
[   27.788767] ttyS2: LSR safety check engaged!
[   27.794422] ttyS0: LSR safety check engaged!
[   33.900029] eth1: no IPv6 routers present
[   38.148055] end_request: I/O error, dev fd0, sector 0
[   38.184061] end_request: I/O error, dev fd0, sector 0

---

### Post by bbking67 on 2010-05-21
how do i check for such a process?

I did a ps -A and I didn't see that command... is that the best way?

---

### Post by tgalati4 on 2010-05-21
Perhaps the DVD drive is sharing an interrupt:

Post the output of:

cat /proc/interrupts

---

### Post by bbking67 on 2010-05-21
Here is the output of cat /proc/interrupts

ckarson@nc8000:~$ cat /proc/interrupts
           CPU0       
  0:     127142    XT-PIC-XT        timer
  1:        392    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  3:          3    XT-PIC-XT      
  4:          3    XT-PIC-XT      
  5:          3    XT-PIC-XT      
  6:          7    XT-PIC-XT        floppy
  7:          1    XT-PIC-XT        parport0
  8:          0    XT-PIC-XT        rtc0
  9:       2556    XT-PIC-XT        acpi
 10:      13662    XT-PIC-XT        ehci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3, uhci_hcd:usb4, ohci1394, yenta, yenta, yenta, radeon
 11:      10500    XT-PIC-XT        ipw2200, Intel 82801DB-ICH4, eth0
 12:     103513    XT-PIC-XT        i8042
 14:      35067    XT-PIC-XT        ata_piix
 15:          0    XT-PIC-XT        ata_piix
NMI:          0   Non-maskable interrupts
LOC:          0   Local timer interrupts
SPU:          0   Spurious interrupts
PMI:          0   Performance monitoring interrupts
PND:          0   Performance pending work
RES:          0   Rescheduling interrupts
CAL:          0   Function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
THR:          0   Threshold APIC interrupts
MCE:          0   Machine check exceptions
MCP:          6   Machine check polls
ERR:          0
MIS:          0

---

### Post by bbking67 on 2010-05-21
So I reinstalled the o/s from scratch (formatted the disc) and the problem went away... until I copied  usb_modeswitch.rules into /etc/udev/rules.d/.  This is to make my u998 Novatel 3G wireless dongle work.

[http://ubuntuforums.org/showthread.php?t=1477361&highlight=u998](http://ubuntuforums.org/showthread.php?t=1477361&highlight=u998)

as soon as that went in the dvd started popping out.

weird.

---

### Post by tgalati4 on 2010-05-21
Well, I presume the usb_modeswitch.rules is a text file.  Any clues inside?  It sounds like the 3G dongle wakes up and that causes the DVD to initialize.  Strange indeed.  Does the behavior change if you use a different USB port?

Perhaps you can blacklist the module that loads the DVD.  I presume you don't need it as often as the network.

---

### Post by bbking67 on 2010-05-22
Well I am running out of options... I might try another distribution to see what happens.  I don't think disabling or blacklisting the dvd-rom is a feasible solution.

The text file is in the link I provided... my theory is that the Novatel wireless is a mass storage device as well as a serial wireless device.  Somehow this makes configuration more difficult in Linux, so the text file tries to Eject the mass storage device and can't distinguish between it and other mass storage devices.  I don't know... just a bullshit theory.

I haven't got much experience with Linux so it is difficult for me to understand what is going on.

There is a line that says 

RUN+="/usr/bin/eject /dev/sr0"

I am going to remove it and see if the Novatel device will continue to work... and it does.  Thanks for the help... time will tell if this is a permanent solution. I think I have to manually eject the Novatel's mass storage and possibly boot with the Novatel installed, but I can live with that.  Maybe if Novatel writes a proper driver/interface then it wouldn't be an issue.

---

### Post by tgalati4 on 2010-05-22
Well /dev/sr0 is another device name for cdrom/dvd.  Not sure why you would need that in the script rules.  Try commenting it out with a # in front of it.  There doesn't appear to be reason to eject the sr0 device--unless it was a work-around to free up resources needed by the 3G dongle.  It's a mystery.

Also there are switches to explore for the eject command:

man eject

Send an email to Novatel and describe your experiences.  With enough feedback, companies will get on top of linux instead of ignore us.

---

