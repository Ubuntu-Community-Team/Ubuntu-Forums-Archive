---
title: "CD Burner"
date: 2004-11-14
forum: Hardware &amp; Laptops
---

### Post by Hat on 2004-11-14
I've searched around and read many things on CD burning being iffy in Ubuntu Linux, but I've yet to hear anything about the CD burner not being recognized. Ubuntu recognizes my old HP CD-Writer Plus 8200 as a CD-Rom drive, but not as a burner (or at least, I don't think it does). When I try to burn a CD in Nautilus, the only option in the pull down menu is to write to a "File Image", which just puts an ISO on my hard drive. Is there a way to get it to recognize my CD burner?

(Oh, and I'm new to this whole Linux thing, so go easy on me =)).

---

### Post by adbak on 2004-11-14
When you pop a blank CD in, Nautilus (the file explorer) should open up to the burn:/// directory.  You should be able to just drag and drop files for a data CD.  If you want to burn an ISO onto a CD, then find the file, right click, and left click Burn to CD.

Audio CDs are something that Nautilus can't currently handle, but there are other programs out there.  I don't make audio CDs, but there's K3b, but that's for KDE, GnomeToaster, CDRecord, and I'm sure a bazillion others, I just don't know them.

---

### Post by Hat on 2004-11-15
That's just the thing, Nautilus doesn't pop up when I insert a blank CD. It doesn't realize that my CD burner is actually more than a CD-rom drive. I can manually go to Nautilus' burn, but when I try to burn a data CD (I'm not concerned with audio), the only option it gives me is to write a ISO to the hard drive. Is there anyway to configure my CD burner or make Nautilus recognize it?

---

### Post by Magneto on 2004-11-16
[QUOTE=Hat]That's just the thing, Nautilus doesn't pop up when I insert a blank CD. It doesn't realize that my CD burner is actually more than a CD-rom drive. I can manually go to Nautilus' burn, but when I try to burn a data CD (I'm not concerned with audio), the only option it gives me is to write a ISO to the hard drive. Is there anyway to configure my CD burner or make Nautilus recognize it?[/QUOTE]
 modprobe usb-storage

see if that works - the driver for your writer is underneath that module it should be included in the ubuntu default - everything else is

---

### Post by Hat on 2004-11-17
I typed that in in a root terminal, and nothing happened (or at least, nothing as far as I can tell).

---

### Post by Magneto on 2004-11-17
[QUOTE=Hat]I typed that in in a root terminal, and nothing happened (or at least, nothing as far as I can tell).[/QUOTE]
 type lsmod and post the output
type  dmesg 
and post the output

---

### Post by Hat on 2004-11-17
lsmod gives me:
```
Module                  Size  Used by
nls_cp437               6016  0
isofs                  33976  0
udf                    79876  0
usb_storage            59200  0
scsi_mod              115148  1 usb_storage
proc_intf               3968  0
freq_table              4356  0
cpufreq_userspace       5336  0
cpufreq_powersave       2048  0
ipv6                  230020  8
af_packet              20872  2
tulip                  42528  0
crc32                   4608  1 tulip
snd_intel8x0m          18632  2
snd_intel8x0           33068  3
snd_ac97_codec         59268  2 snd_intel8x0m,snd_intel8x0
snd_pcm_oss            48168  0
snd_mixer_oss          16640  4 snd_pcm_oss
snd_pcm                85540  3 snd_intel8x0m,snd_intel8x0,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd_page_alloc         11144  3 snd_intel8x0m,snd_intel8x0,snd_pcm
snd_mpu401_uart         7296  1 snd_intel8x0
snd_rawmidi            23232  1 snd_mpu401_uart
snd_seq_device          7944  1 snd_rawmidi
snd                    50660  14 snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  4 snd
uhci_hcd               29328  0
usbcore               104292  4 usb_storage,uhci_hcd
pci_hotplug            30640  0
hw_random               5652  0
intel_agp              20512  1
agpgart                31784  2 intel_agp
analog                 10784  0
gameport                4736  2 snd_intel8x0,analog
floppy                 54996  0
pcspkr                  3816  0
rtc                    12216  0
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
parport_pc             32064  1
lp                     10436  0
parport                37320  2 parport_pc,lp
tsdev                   7168  0
evdev                   9088  0
ide_cd                 38276  0
cdrom                  35872  1 ide_cd
mousedev               10124  1
psmouse                17800  0
ext3                  109544  1
jbd                    54552  1 ext3
ide_generic             1664  0
piix                   12576  1
ide_disk               16768  3
ide_core              125272  5 usb_storage,ide_cd,ide_generic,piix,ide_disk
unix                   25904  734
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb
```

---

### Post by Hat on 2004-11-17
and dsmeg gives me (splitting into several parts since it's too long):
```
 entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 0183fbff 00000000 00000000 00000000
CPU: After vendor identify, caps:  0183fbff 00000000 00000000 00000000
CPU: L1 I cache: 16K, L1 D cache: 16K
CPU: L2 cache: 128K
CPU: After all inits, caps:        0183fbff 00000000 00000000 00000040
CPU: Intel Celeron (Mendocino) stepping 05
Enabling fast FPU save and restore... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
enabled ExtINT on CPU#0
ESR value before enabling vector: 00000000
ESR value after enabling vector: 00000000
Using local APIC timer interrupts.
calibrating APIC timer ...
..... CPU clock speed is 400.0831 MHz.
..... host bus clock speed is 66.0805 MHz.
checking if image is initramfs...it isn't (ungzip failed); looks like an initrd
Freeing initrd memory: 4116k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xfb2d0, last bus=1
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20040816
ACPI: Interpreter disabled.
Linux Plug and Play Support v0.97 (c) Adam Belay
PnPBIOS: Scanning system for PnP BIOS support...
PnPBIOS: Found PnP BIOS installation structure at 0xc00fbc50
PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xbc80, dseg 0xf0000
pnp: 00:0c: ioport range 0x800-0x87f has been reserved
pnp: 00:0c: ioport range 0x3f0-0x3f1 has been reserved
PnPBIOS: 17 nodes reported by PnP BIOS; 17 recorded by driver
PCI: Probing PCI hardware
PCI: Probing PCI hardware (bus 00)
PCI: Transparent bridge - 0000:00:1e.0
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
Cannot allocate resource for EISA slot 4
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 1024 buckets, 8Kbytes
TCP: Hash tables configured (established 16384 bind 32768)
NET: Registered protocol family 8
NET: Registered protocol family 20
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4116 blocks [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 204k freed
vesafb: probe of vesafb0 failed with error -6
thermal: Unknown symbol acpi_processor_set_thermal_limit
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
```

---

### Post by Hat on 2004-11-17
dmesg continued...
```
ICH0: IDE controller at PCI slot 0000:00:1f.1
ICH0: chipset revision 1
ICH0: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
hda: Maxtor 5T020H2, ATA DISK drive
Using anticipatory io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 40021632 sectors (20491 MB) w/2048KiB Cache, CHS=39704/16/63, UDMA(33)
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
hdc: Hewlett-Packard CD-Writer Plus 8200a, ATAPI CD/DVD-ROM drive
hdd: LTN403L, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
Adding 499928k swap on /dev/hda5.  Priority:-1 extents:1
EXT3 FS on hda1, internal journal
input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
mice: PS/2 mouse device common for all mice
hdc: ATAPI 32X CD-ROM CD-R/RW drive, 4096kB Cache, UDMA(33)
Uniform CD-ROM driver Revision: 3.20
ts: Compaq touchscreen protocol output
hdd: ATAPI 40X CD-ROM drive, 120kB Cache, UDMA(33)
parport: PnPBIOS parport detected.
```

---

### Post by Hat on 2004-11-17
```
[PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
lp0: using parport0 (interrupt-driven).
Capability LSM initialized
device-mapper: 4.1.0-ioctl (2003-12-10) initialised: [email]dm@uk.sistina.com[/email]
md: md driver 0.90.0 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
cdrom: open failed.
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.8.1-3-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a National Semiconductor PC87306
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected an Intel i810 Chipset.
agpgart: Maximum main memory to use for agp memory: 148M
agpgart: AGP aperture is 64M @ 0xd8000000
hw_random hardware driver 1.0.0 loaded
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x1001
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
uhci_hcd 0000:00:1f.2: Intel Corp. 82801AB USB
PCI: Setting latency timer of device 0000:00:1f.2 to 64
uhci_hcd 0000:00:1f.2: irq 10, io base 0000d000
uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
PCI: Setting latency timer of device 0000:00:1f.5 to 64
intel8x0_measure_ac97_clock: measured 49190 usecs
intel8x0: clocking to 48000
PCI: Setting latency timer of device 0000:00:1f.6 to 64
Linux Tulip driver version 1.1.13 (May 11, 2002)
eth0: Lite-On PNIC-II rev 37 at 0xc000, 00:C0:F0:63:C0:B2, IRQ 5.
NET: Registered protocol family 17
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02cc0c0(lo)
IPv6 over IPv4 tunneling driver
eth0: no IPv6 routers present
acpi: Unknown symbol acpi_processor_unregister_performance
acpi: Unknown symbol acpi_processor_register_performance
SCSI subsystem initialized
Initializing USB Mass Storage driver...
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
udf: registering filesystem
attempt to access beyond end of device
hdc: rw=0, want=68, limit=4
attempt to access beyond end of device
hdc: rw=0, want=1252, limit=4
attempt to access beyond end of device
hdc: rw=0, want=1028, limit=4
UDF-fs: No partition found (1)
attempt to access beyond end of device
hdc: rw=0, want=68, limit=4
isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
UDF-fs: No VRS found
ISO 9660 Extensions: Microsoft Joliet Level 3
ISOFS: changing to secondary root
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
end_request: I/O error, dev hdc, sector 64
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x34
end_request: I/O error, dev hdc, sector 729296
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
end_request: I/O error, dev hdc, sector 728272
...
(these error messages continue for a long time)
...
isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16

```
And that's the end of it...

---

### Post by Magneto on 2004-11-17
okay your kernel sees the drive
what happens from the commandline? 
have you tried another burning app? cdrecord? k3b?
try cdrecord or a frontend like k3b  k3b is similar to nero

---

### Post by Hat on 2004-11-17
I tried cdrecord, and am not quite sure about it. I tried it out, and the help files told me to try "cdrecord -scanbus" to find my burner. I did this under root, and it gave me a bunch of output, most notably: "cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver."

By the way, thanks for having the patience to work with me here - I'm new to Linux, so I'm unfamiliar with how everything works...

Although, I have to ask - is it hopeless yet?

---

### Post by Magneto on 2004-11-18
[QUOTE=Hat]I tried cdrecord, and am not quite sure about it. I tried it out, and the help files told me to try "cdrecord -scanbus" to find my burner. I did this under root, and it gave me a bunch of output, most notably: "cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver."

By the way, thanks for having the patience to work with me here - I'm new to Linux, so I'm unfamiliar with how everything works...

Although, I have to ask - is it hopeless yet?[/QUOTE]
 nah its not hopeless :)
im gonna get my hp8200 out now and see what happens

---

### Post by Magneto on 2004-11-18
okay- the drive works fine with nautilus but......
The drive is used in ide-scsi mode
so

1.) You need to tell grub that you want the device called hdc to be used with ide-scsi 

```
 sudo nano -w /boot/grub/menu.lst

```
Scroll down in the file until you see this line
```
## ## End Default Options ##

```
Now the next entry is the default instructions for your computer to boot and in the first area after End default options that you  see a line like this
```
kernel          /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro single

```

Add this " hdc=ide-scsi"
So the line should now look like

```
kernel          /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro single
 hdc=ide-scsi
```

Now press Control + o to save the file and Control + x to exit

reboot

after your system has rebooted type 
```
modprobe ide-scsi
```

load a blank cd in the 8200 and open nautilus- type burn:/// in the location bar and the write cd options should be active

---

### Post by Hat on 2004-11-20
(Sorry about this delayed reply, I lost internet access for about 2 days)

Alright, I added the line to the grub file, however when I enter the modprobe line (either in a root terminal or using sudo) nothing happens. It just immediately gives me the next prompt for input. When I enter it in a non-root terminal or not using sudo, it gives me messages regarding "Operation not permitted."

In the end though, nothing has changed. I still only get "File Image" under the "Write disc to:" menu under burn:///

---

### Post by Magneto on 2004-11-20
[QUOTE=Hat](Sorry about this delayed reply, I lost internet access for about 2 days)

Alright, I added the line to the grub file, however when I enter the modprobe line (either in a root terminal or using sudo) nothing happens. It just immediately gives me the next prompt for input. When I enter it in a non-root terminal or not using sudo, it gives me messages regarding "Operation not permitted."

In the end though, nothing has changed. I still only get "File Image" under the "Write disc to:" menu under burn:///[/QUOTE]
 works for me without any problem just by plugging it in - your problem is the ide cdrom driver is loading before it can be configured as a cdwriter there are many posts about this on the internet

what do you get when you modprobe ide-scsi 
then type dmesg
 your drive should be setup as /dev/sr0

---

### Post by jrasmussen0 on 2005-04-29
I was able to change my /boot/grub/menu.lst to this:
# kopt=root=/dev/hda1 ro hdd=ide-scsi

My cd writer happens to be hdd while my cd reader is hdc.

I then had to add 'ide-scsi' to the last line of /etc/modules

Now I can run 'sudo cdrecord -scanbus'  and runing 'sudo cdrecord -dev 2,0,0 image.iso' worked after creating the iso image through Nautilus.

I'm hoping that if the 'ide-scsi' line is in /etc/modules at boot time, then Nautilus will work.

[QUOTE=Magneto]okay- the drive works fine with nautilus but......
The drive is used in ide-scsi mode
so

1.) You need to tell grub that you want the device called hdc to be used with ide-scsi 

```
 sudo nano -w /boot/grub/menu.lst

```
Scroll down in the file until you see this line
```
## ## End Default Options ##

```
Now the next entry is the default instructions for your computer to boot and in the first area after End default options that you  see a line like this
```
kernel          /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro single

```

Add this " hdc=ide-scsi"
So the line should now look like

```
kernel          /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro single
 hdc=ide-scsi
```

Now press Control + o to save the file and Control + x to exit

reboot

after your system has rebooted type 
```
modprobe ide-scsi
```

load a blank cd in the 8200 and open nautilus- type burn:/// in the location bar and the write cd options should be active[/QUOTE]

---

### Post by waool5000 on 2005-10-10
:p

---

