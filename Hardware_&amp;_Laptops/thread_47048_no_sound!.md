---
title: "no sound!"
date: 2005-07-07
forum: Hardware &amp; Laptops
---

### Post by vkkim on 2005-07-07
I have a Panasonic Let's Note R3 laptop and have no sound, although another R3 user in this forum has said her sound worked out of the box.  I am a complete newbie with GNU/Linux.  Help!

---

### Post by Shinitenshi on 2005-07-07
Well when i installed ubuntu i had some sound but on some programs it dint really work. so i installed libsdl1.2debian-esd  and everything works now. 

I am not sure if this is whats wrong with yours.

---

### Post by vkkim on 2005-07-07
I tried installing libsdl1.2debian-esd per your suggestion to no avail... someone please help!

---

### Post by vkkim on 2005-07-10
anybody?

---

### Post by varunus on 2005-07-12
What sound card is in the laptop?  Also, post the output of "lspci" and "lsmod".

---

### Post by manicka on 2005-07-12
Also check that your volumes aren't muted. Right click on volume icon in panel and choose 'Open Volume Control'

---

### Post by 89c51 on 2005-07-12
have you tried the latest alsa 1.0.9 (if i remember well)

---

### Post by vkkim on 2005-07-13
> **varunus]What sound card is in the laptop?  Also, post the output of "lspci" and "lsmod".[/QUOTE]

I'm not sure what sound card I have installed, but lspci returns:

0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Registers (rev 02)
0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process Registers (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 855GME GMCH Host-to-AGP Bridge (Virtual PCI-to-PCI) (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
0000:02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:04.0 Network controller: Intel Corp.: Unknown device 4223 (rev 05)
0000:02:05.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev 88)
0000:02:05.1 System peripheral: Ricoh Co Ltd: Unknown device 0575

and lsmod returns:

Module                  Size  Used by
button                  6480  0
ehci_hcd               32708  0
uhci_hcd               32816  0
ipw2200               133100  0
8139too                25856  0
cisco_ipsec           394732  0
nls_utf8                1952  0
nls_cp437               5600  0
vfat                   13824  0
fat                    41760  1 vfat
sd_mod                 17776  0
usb_storage            71936  0
scsi_mod              127552  2 sd_mod,usb_storage
ipv6                  257888  6
speedstep_centrino      7892  1
proc_intf               3908  0
freq_table              4004  1 speedstep_centrino
cpufreq_userspace       4348  1
cpufreq_ondemand        6140  0
cpufreq_powersave       1632  0
pcmcia                 22244  2
video                  15972  0
sony_acpi               5928  0
pcc_acpi               11008  0
i915                   19552  1
drm                    65172  2 i915
battery                 9988  4
container               4320  0
ac                      4676  3
af_packet              21992  4
yenta_socket           21344  0
pcmcia_core            57984  2 pcmcia,yenta_socket
arc4                    1728  0
ieee80211_crypt_wep     5220  0
firmware_class          9984  1 ipw2200
ieee80211              36388  1 ipw2200
ieee80211_crypt         5960  2 ieee80211_crypt_wep,ieee80211
8139cp                 20416  0
mii                     4896  2 8139too,8139cp
snd_intel8x0           32352  1
snd_ac97_codec         74144  1 snd_intel8x0
snd_pcm_oss            52132  0
snd_mixer_oss          19680  1 snd_pcm_oss
snd_pcm                94696  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25060  1 snd_pcm
snd                    55012  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10016  1 snd
snd_page_alloc          9732  2 snd_intel8x0,snd_pcm
i2c_i801                8364  0
i2c_core               22320  1 i2c_i801
hw_random               5300  0
usbcore               119000  4 ehci_hcd,uhci_hcd,usb_storage
shpchp                 99172  0
pci_hotplug            33488  1 shpchp
intel_agp              22140  1
agpgart                33608  3 drm,intel_agp
rtc                    12472  0
pcspkr                  3496  0
md                     47440  0
evdev                   9344  1
joydev                  9664  0
dm_mod                 59420  1
tsdev                   7520  0
capability              4648  0
commoncap               7712  1 capability
psmouse                21320  0
mousedev               11288  1
parport_pc             37252  0
lp                     11144  0
parport                36744  2 parport_pc,lp
ide_cd                 41700  0
cdrom                  40220  1 ide_cd
ext3                  137256  1
jbd                    60536  1 ext3
mbcache                 8356  1 ext3
ide_generic             1312  0
piix                   10340  1
ide_disk               20416  3
ide_core              129356  5 usb_storage,ide_cd,ide_generic,piix,ide_disk
unix                   28276  1079
thermal                13320  0
processor              22452  2 speedstep_centrino,thermal
fan                     4388  0
fbcon                  37504  0
font                    8192  1 fbcon
bitblit                 5472  1 fbcon
vesafb                  6724  0
cfbcopyarea             3808  1 vesafb
cfbimgblt               2912  1 vesafb
cfbfillrect             3488  1 vesafb

[QUOTE=manicka]Also check that your volumes aren't muted. Right click on volume icon in panel and choose 'Open Volume Control'[/QUOTE]

First thing I did.   said:**
> have you tried the latest alsa 1.0.9 (if i remember well)

I'm not quite sure how to do that, but I do have alsa-base 1.0.8-4ubuntu4 installed in synaptics, if that helps.

Thank you everyone that has tried helping so far... I really like Ubuntu and this sound problem is really getting on my nerves  ](*,)

---

### Post by strandlooper on 2005-07-14
To get alsa 1.0.9 - just change to Breezy (Unofficial Ubuntu 5.04 Starter Guide) - install as usual - change back to Hoary.

Good luck

---

### Post by vkkim on 2005-07-24
I kinda feel uncomfortable upgrading to Breezy, as I find this warning on the Unofficial Ubuntu Starter Guide: Warning! This is still in it's development stage. Only use it for experimental purposes. Doing this might break your entire system.

Is there anything else that I could try before doing this?  Or will alsa 1.0.9 fix all my problems?

---

### Post by vkkim on 2005-07-28
Somebody Please Help!!!

---

### Post by OneSeventeen on 2005-07-28
I'm also getting problems listening to stuff, vlc tells me:
```

oss error: cannot open audio device (/dev/dsp)

```

---

### Post by netsyd on 2005-07-28
[QUOTE=OneSeventeen]I'm also getting problems listening to stuff, vlc tells me:
```

oss error: cannot open audio device (/dev/dsp)

```[/QUOTE]

Why would it have you using OSS? (Open Sound System) I thought Ubuntu specifically used alsa? 

Is it specific programs or do you get no sound for anything...


**vkkim**  ----------

```
Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
``` This is your audio controller eg. sound card. 

Try to start alsamixer and unmute and open all the faders until the sound is heard (hopefully). Then you can close them individually until you find the one(s) that make the difference... ](*,)

---

### Post by vkkim on 2005-07-28
[QUOTE=netsyd]**vkkim**  ----------

```
Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
``` This is your audio controller eg. sound card. 

Try to start alsamixer and unmute and open all the faders until the sound is heard (hopefully). Then you can close them individually until you find the one(s) that make the difference... ](*,)[/QUOTE]

Believe me I've already tried that WAY too many times...

---

### Post by vkkim on 2005-08-03
Ok, so yesterday I reformatted my computer and reinstalled a clean Ubuntu Hoary system for other reasons, but my sound is still gone.  Which still baffles me because someone else with my same machine said that it worked out of the box.

Can someone **please** help me?!  ](*,)

---

### Post by ubuntu_demon on 2005-08-03
[QUOTE=vkkim]Ok, so yesterday I reformatted my computer and reinstalled a clean Ubuntu Hoary system for other reasons, but my sound is still gone.  Which still baffles me because someone else with my same machine said that it worked out of the box.

Can someone **please** help me?!  ](*,)[/QUOTE]
 Does sound work when you boot your computer with a knoppix cd or ubuntu live cd ?

also you should check this page out :
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

---

### Post by vkkim on 2005-08-04
[QUOTE=ubuntu_demon]Does sound work when you boot your computer with a knoppix cd or ubuntu live cd ?

also you should check this page out :
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)[/QUOTE]

For some reason, Knoppix won't boot on my computer (perhaps because I'm using an external drive through an IDE to USB enclosure) and no sound when I boot using the live cd either.

---

### Post by ubuntu_demon on 2005-08-04
[QUOTE=vkkim]For some reason, Knoppix won't boot on my computer (perhaps because I'm using an external drive through an IDE to USB enclosure) and no sound when I boot using the live cd either.[/QUOTE]
 did  you have sound prior to your ubuntu install ? in windows maybe ?

---

### Post by vkkim on 2005-08-04
[QUOTE=ubuntu_demon]did  you have sound prior to your ubuntu install ? in windows maybe ?[/QUOTE]

Yes, in Windows XP.

---

### Post by ubuntu_demon on 2005-08-04
did you follow this page : [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems) ?

---

### Post by vkkim on 2005-08-04
I don't really understand what to do after reading it, although I did try installing the snd-intel8x0 ALSA module, to no avail.

---

### Post by ubuntu_demon on 2005-08-04
[QUOTE=vkkim]I don't really understand what to do after reading it, although I did try installing the snd-intel8x0 ALSA module, to no avail.[/QUOTE]
 just read it slowly. If you don't understand just run the commands and post the output. (I'm not really an expert on this topic but I wanna try to help you)

---

### Post by Lambert on 2005-08-04
I had sound on some apps not not all on a thinkpad. I followed this and it corrected my problems. Not sure if it will help your situation.

[http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly)

---

### Post by shinjimx on 2005-08-04
Thanks for all of your advices. I'm new on Linux too, installed Ubuntu on a Toshiba Satellite 1730 (Cirrus Logic Crystal 4281 soundcard) and it didn't sound after the installation, I used the libsdl1.2debian-alsa and after a reboot it worked (dunno if that will help you vkkim). ¡Saludos desde Mexico!  :grin:  (greetings from Mexico)

---

### Post by vkkim on 2005-08-12
[QUOTE=ubuntu_demon]just read it slowly. If you don't understand just run the commands and post the output. (I'm not really an expert on this topic but I wanna try to help you)[/QUOTE]

lspci -v:
```
0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
        Subsystem: Matsushita Electric Industrial Co., Ltd.: Unknown device 8338        Flags: bus master, fast devsel, latency 0
        Memory at e4000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <available only to root>

0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Registers (rev 02)
        Subsystem: Matsushita Electric Industrial Co., Ltd.: Unknown device 8338        Flags: bus master, fast devsel, latency 0

0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process Registers (rev 02)
        Subsystem: Matsushita Electric Industrial Co., Ltd.: Unknown device 8338        Flags: bus master, fast devsel, latency 0

0000:00:01.0 PCI bridge: Intel Corp. 855GME GMCH Host-to-AGP Bridge (Virtual PCI-to-PCI) (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 32
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32

0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02) (prog-if 00 [VGA])
        Subsystem: Matsushita Electric Industrial Co., Ltd.: Unknown device 8338        Flags: bus master, fast devsel, latency 0, IRQ 9
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Memory at e0000000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Capabilities: <available only to root>

0000:00:02.1 Display controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
        Subsystem: Matsushita Electric Industrial Co., Ltd.: Unknown device 8338        Flags: fast devsel
        Memory at f0000000 (32-bit, prefetchable) [disabled] [size=128M]
        Memory at e0080000 (32-bit, non-prefetchable) [disabled] [size=512K]
        Capabilities: <available only to root>

0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Matsushita Electric Industrial Co., Ltd.: Unknown device 8338        Flags: bus master, medium devsel, latency 0, IRQ 9
        I/O ports at 1820 [size=32]

0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Matsushita Electric Industrial Co., Ltd.: Unknown device 8338        Flags: bus master, medium devsel, latency 0, IRQ 11
        Memory at e0100000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=03, sec-latency=32
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: e0200000-e02fffff

0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
        Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Matsushita Electric Industrial Co., Ltd.: Unknown device 8338        Flags: bus master, medium devsel, latency 0, IRQ 9
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 1810 [size=16]
        Memory at 50000000 (32-bit, non-prefetchable) [size=1K]

0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
        Subsystem: Matsushita Electric Industrial Co., Ltd.: Unknown device 8338        Flags: medium devsel, IRQ 9
        I/O ports at 1880 [size=32]

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
        Subsystem: Matsushita Electric Industrial Co., Ltd.: Unknown device 8346        Flags: bus master, medium devsel, latency 0, IRQ 9
        I/O ports at 1c00 [size=256]
        I/O ports at 1840 [size=64]
        Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
        Memory at e0100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
        Subsystem: Matsushita Electric Industrial Co., Ltd.: Unknown device 834b        Flags: medium devsel, IRQ 9
        I/O ports at 2400 [size=256]
        I/O ports at 2000 [size=128]
        Capabilities: <available only to root>

0000:02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Matsushita Electric Industrial Co., Ltd.: Unknown device 8338        Flags: bus master, medium devsel, latency 32, IRQ 3
        I/O ports at 3000 [size=256]
        Memory at e0201000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:02:04.0 Network controller: Intel Corp.: Unknown device 4223 (rev 05)
        Subsystem: Intel Corp.: Unknown device 1002
        Flags: bus master, medium devsel, latency 32, IRQ 7
        Memory at e0200000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:02:05.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev 88)
        Subsystem: Matsushita Electric Industrial Co., Ltd.: Unknown device 8338        Flags: bus master, VGA palette snoop, medium devsel, latency 248, IRQ 10        Memory at 50001000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=ff, secondary=ff, subordinate=ff, sec-latency=248
        I/O window 0: fffffffc-ffffffff
        I/O window 1: fffffffc-ffffffff
        16-bit legacy interface ports at fffd

0000:02:05.1 System peripheral: Ricoh Co Ltd: Unknown device 0575
        Subsystem: Matsushita Electric Industrial Co., Ltd.: Unknown device 8338        Flags: medium devsel, IRQ 5
        Memory at e0201400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

``` 

dmesg:
```
cache hash table entries: 131072 (order: 7, 524288 bytes)
Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Memory: 901916k/917504k available (1436k kernel code, 14984k reserved, 754k data, 224k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 1183.74 BogoMIPS (lpj=591872)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: afe9f9ff 00000000 00000000 00000000 00000180 00000000
CPU: After vendor identify, caps: afe9f9ff 00000000 00000000 00000000 00000180 00000000
CPU: L1 I cache: 32K, L1 D cache: 32K
CPU: L2 cache: 2048K
CPU: After all inits, caps: afe9f9ff 00000000 00000000 00000040 00000180 00000000
CPU: Intel(R) Pentium(R) M processor 1.20GHz stepping 08
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
ACPI: Looking for DSDT in initrd... not found!
ACPI: setting ELCR to 0200 (from 0aa8)
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4300k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xfd972, last bus=3
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using PIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
PCI: Transparent bridge - 0000:00:1e.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: Embedded Controller [EC0] (gpe 28)
ACPI: PCI Interrupt Link [LNKA] (IRQs *9)
ACPI: PCI Interrupt Link [LNKB] (IRQs *9)
ACPI: PCI Interrupt Link [LNKC] (IRQs 9) *0, disabled.
ACPI: PCI Interrupt Link [LNKD] (IRQs *3)
ACPI: PCI Interrupt Link [LNKE] (IRQs *5)
ACPI: PCI Interrupt Link [LNKF] (IRQs *7)
ACPI: PCI Interrupt Link [LNKG] (IRQs 10) *0, disabled.
ACPI: PCI Interrupt Link [LNKH] (IRQs *11)
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 9 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to bjorn.helgaas@hp.com
** so I can fix the driver.
Simple Boot Flag at 0x41 set to 0x1
audit: initializing netlink socket (disabled)
audit(1123673574.349:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
i8042.c: Detected active multiplexing controller, rev 1.1.
serio: i8042 AUX0 port at 0x60,0x64 irq 12
serio: i8042 AUX1 port at 0x60,0x64 irq 12
serio: i8042 AUX2 port at 0x60,0x64 irq 12
serio: i8042 AUX3 port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
PCI: setting IRQ 9 as level-triggered
ACPI: PCI interrupt 0000:00:1f.6[B] -> GSI 9 (level, low) -> IRQ 9
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
Cannot allocate resource for EISA slot 1
Cannot allocate resource for EISA slot 2
Cannot allocate resource for EISA slot 3
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 8192 buckets, 64Kbytes
TCP: Hash tables configured (established 262144 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
 LAN SMDM PWRB  LID
ACPI: (supports S0 S3 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4300KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
ACPI: Processor [CPU0] (supports 8 throttling states)
ACPI: Thermal Zone [TZC] (55 C)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
ICH4: IDE controller at PCI slot 0000:00:1f.1
PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 9
ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 9 (level, low) -> IRQ 9
ICH4: chipset revision 3
ICH4: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:DMA, hdb:pio
Probing IDE interface ide0...
hda: TOSHIBA MK4025GASL, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 78140160 sectors (40007 MB), CHS=65535/16/63, UDMA(100)
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
Probing IDE interface ide1...
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (458 pages freed)
Restarting tasks... done
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 1622524k swap on /dev/hda5.  Priority:-1 extents:1
EXT3 FS on hda1, internal journal
lp: driver loaded but no devices found
mice: PS/2 mouse device common for all mice
Synaptics Touchpad, model: 1
 Firmware: 5.9
 Sensor: 57
 new absolute packet format
 Touchpad has extended capability bits
 -> multifinger detection
 -> palm detection
input: SynPS/2 Synaptics TouchPad on isa0060/serio4
ts: Compaq touchscreen protocol output
ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 9 (level, low) -> IRQ 9
PCI: Setting latency timer of device 0000:00:1f.5 to 64
intel8x0_measure_ac97_clock: measured 49352 usecs
intel8x0: clocking to 48000
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: dm-devel@redhat.com
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
input: PC Speaker
Real Time Clock Driver v1.12
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected an Intel 855 Chipset.
agpgart: Maximum main memory to use for agp memory: 816M
agpgart: Detected 8060K stolen memory.
agpgart: AGP aperture is 128M @ 0xe8000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 9
ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 9 (level, low) -> IRQ 9
uhci_hcd 0000:00:1d.0: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: irq 9, io base 0x1820
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
PCI: setting IRQ 11 as level-triggered
ACPI: PCI interrupt 0000:00:1d.7[D] -> GSI 11 (level, low) -> IRQ 11
ehci_hcd 0000:00:1d.7: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller
PCI: Setting latency timer of device 0000:00:1d.7 to 64
ehci_hcd 0000:00:1d.7: irq 11, pci mem 0xe0100000
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
PCI: cache line size of 32 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
hw_random hardware driver 1.0.0 loaded
8139too Fast Ethernet driver 0.9.27
ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 3
PCI: setting IRQ 3 as level-triggered
ACPI: PCI interrupt 0000:02:01.0[A] -> GSI 3 (level, low) -> IRQ 3
eth0: RealTek RTL8139 at 0x3000, 00:0b:97:2c:8c:f6, IRQ 3
eth0:  Identified 8139 chip type 'RTL-8101'
8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
ieee80211_crypt: registered algorithm 'NULL'
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 0.19
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 7
PCI: setting IRQ 7 as level-triggered
ACPI: PCI interrupt 0000:02:04.0[A] -> GSI 7 (level, low) -> IRQ 7
ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
Linux Kernel Card Services
  options:  [pci] [cardbus] [pm]
ieee80211_crypt: registered algorithm 'WEP'
ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 10
PCI: setting IRQ 10 as level-triggered
ACPI: PCI interrupt 0000:02:05.0[A] -> GSI 10 (level, low) -> IRQ 10
Yenta: CardBus bridge found at 0000:02:05.0 [10f7:8338]
Yenta: ISA IRQ mask 0x0030, PCI irq 10
Socket status: 30000006
NET: Registered protocol family 17
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
eth1: duplicate address detected!
ACPI: AC Adapter [AC] (on-line)
[drm] Initialized drm 1.0.0 20040925
ACPI: PCI interrupt 0000:00:02.0[A] -> GSI 9 (level, low) -> IRQ 9
[drm] Initialized i915 1.2.0 20040405 on minor 0: Intel Corp. 82852/855GM Integrated Graphics Device
[drm] Initialized i915 1.2.0 20040405 on minor 1: Intel Corp. 82852/855GM Integrated Graphics Device (#2)
mtrr: base(0xe8020000) is not aligned on a size(0x300000) boundary
ACPI: Battery Slot [BATA] (battery present)
ACPI: Power Button (FF) [PWRF]
ACPI: Lid Switch [LID]
ibm_acpi: ec object not found
ACPI: Video Device [GRFX] (multi-head: yes  rom: no  post: no)
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
cs: IO port probe 0x0100-0x04ff: excluding 0x360-0x367 0x4d0-0x4d7
cs: IO port probe 0x0800-0x08ff: clean.
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
uhci_hcd 0000:00:1d.0: remove, state 1
usb usb1: USB disconnect, address 1
uhci_hcd 0000:00:1d.0: USB bus 1 deregistered
ehci_hcd 0000:00:1d.7: remove, state 1
usb usb2: USB disconnect, address 1
ehci_hcd 0000:00:1d.7: USB bus 2 deregistered
Stopping tasks: ==================================================================================================================================================================================|
Back to C!
ACPI: PCI interrupt 0000:00:02.0[A] -> GSI 9 (level, low) -> IRQ 9
ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 9 (level, low) -> IRQ 9
ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 9 (level, low) -> IRQ 9
PCI: Setting latency timer of device 0000:00:1f.5 to 64
ACPI: PCI interrupt 0000:02:01.0[A] -> GSI 3 (level, low) -> IRQ 3
PCMCIA: socket f565c82c: *** DANGER *** unable to remove socket power
psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Restarting tasks... done
8139too Fast Ethernet driver 0.9.27
ACPI: PCI interrupt 0000:02:01.0[A] -> GSI 3 (level, low) -> IRQ 3
eth0: RealTek RTL8139 at 0x3000, 00:0b:97:2c:8c:f6, IRQ 3
eth0:  Identified 8139 chip type 'RTL-8101'
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 0.19
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ACPI: PCI interrupt 0000:02:04.0[A] -> GSI 7 (level, low) -> IRQ 7
ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 9 (level, low) -> IRQ 9
uhci_hcd 0000:00:1d.0: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: irq 9, io base 0x1820
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.7[D] -> GSI 11 (level, low) -> IRQ 11
ehci_hcd 0000:00:1d.7: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller
PCI: Setting latency timer of device 0000:00:1d.7 to 64
ehci_hcd 0000:00:1d.7: irq 11, pci mem 0xe0100000
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
PCI: cache line size of 32 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
PCMCIA: socket f565c82c: *** DANGER *** unable to remove socket power
eth1: duplicate address detected!
ACPI: Power Button (FF) [PWRF]
ACPI: Lid Switch [LID]
ipw2200: Fatal error
ipw2200: Start IPW Error Log Dump:
ipw2200: Status: 0x001000C0, Config: 00000142
ipw2200: Start IPW Event Log Dump:
mtrr: base(0xe8020000) is not aligned on a size(0x300000) boundary
mtrr: base(0xe8020000) is not aligned on a size(0x300000) boundary
mtrr: base(0xe8020000) is not aligned on a size(0x300000) boundary
mtrr: base(0xe8020000) is not aligned on a size(0x300000) boundary
mtrr: base(0xe8020000) is not aligned on a size(0x300000) boundary
mtrr: base(0xe8020000) is not aligned on a size(0x300000) boundary
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: disabled on user request.
mtrr: base(0xe8020000) is not aligned on a size(0x300000) boundary
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: disabled on user request.
cs: IO port probe 0x0100-0x04ff: excluding 0x360-0x367 0x4d0-0x4d7
cs: IO port probe 0x0800-0x08ff: clean.
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
mtrr: base(0xe8020000) is not aligned on a size(0x300000) boundary
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: disabled on user request.
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: disabled on user request.
mtrr: base(0xe8020000) is not aligned on a size(0x300000) boundary
cs: IO port probe 0x0100-0x04ff: excluding 0x360-0x367 0x4d0-0x4d7
cs: IO port probe 0x0800-0x08ff: clean.
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
``` 

aplay -l:

```
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
``` 

lspnp -v

```
lspnp: /proc/bus/pnp not available
``` 

Also, I don't understand the "sudo modprobe" command on that wiki page...

Thank you so much for trying to help me...

---

### Post by mo_x on 2005-08-12
The output from lspci and lsmod seems ok. Have you connected your speakers to the right output connector? Check again if anything is muted with alsamixer.

---

### Post by vkkim on 2005-08-12
[QUOTE=mo_x]The output from lspci and lsmod seems ok. Have you connected your speakers to the right output connector? Check again if anything is muted with alsamixer.[/QUOTE]

I am using a laptop, so I can't really connect any speakers... and I always check alsamixer.  I learned my lesson a looong time ago  ;-)

---

### Post by Tiede on 2005-08-17
ok. I gathered from the post above that alsamixer shows you your card and doesn't give you any errors...
try this in a terminal and tell us what happens:
```
 esd 
```

After, do this:
```
 killall esd 
```
and give us the outputs of:
```
 lsof /dev/snd/*
lsof /dev/dsp 
```
Hopefully we'll get this thing working soon!

---

### Post by vkkim on 2005-08-17
[QUOTE=Tiede]ok. I gathered from the post above that alsamixer shows you your card and doesn't give you any errors...[/QUOTE]

right.

[QUOTE=Tiede]try this in a terminal and tell us what happens:
```
 esd 
```[/QUOTE]

```
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd/socket
This socket already exists indicating esd is already running.
Exiting...
``` 

[QUOTE=Tiede]After, do this:
```
 killall esd 
```
and give us the outputs of:
```
 lsof /dev/snd/*
lsof /dev/dsp 
```
Hopefully we'll get this thing working soon![/QUOTE]

lsof /dev/snd/*
```
COMMAND    PID   USER   FD   TYPE DEVICE SIZE NODE NAME
mixer_app 5342 victor   35u   CHR  116,0      5573 /dev/snd/controlC0
``` 

lsof /dev/dsp returns nothing.

---

### Post by Tiede on 2005-08-22
there is your problem... The output of *both* lsof /dev/dsp and /dev/snd/* should be nothing.
The mixer_app is controlling your card.

---

### Post by vkkim on 2005-08-22
[QUOTE=Tiede]there is your problem... The output of *both* lsof /dev/dsp and /dev/snd/* should be nothing.
The mixer_app is controlling your card.[/QUOTE]

So how would I fix that?  I don't even know what a "mixer_app" is...

---

### Post by vkkim on 2005-08-29
A little help?

I tried killing the mixer_app, and although now both lsof /dev/dsp and /dev/snd/* are blank, there's still no sound...

---

### Post by tuxrtfm on 2005-08-31
I have the same sound device.  After opening the volume control goto edit - prefences and select exteranal amplifier then close box.  Check the Control tab and mke sure that exernal amp is NOT checked then while play some sort of music file slowly raise the pcm slide under the playback tab.

Good-Luck

---

### Post by vkkim on 2005-08-31
[QUOTE=tuxrtfm]I have the same sound device.  After opening the volume control goto edit - prefences and select exteranal amplifier then close box.  Check the Control tab and mke sure that exernal amp is NOT checked then while play some sort of music file slowly raise the pcm slide under the playback tab.

Good-Luck[/QUOTE]
 Someone already pointed this method out, and it hasnt done anything for me yet... :(

Thanks anyway.

---

### Post by vkkim on 2005-09-05
Can somebody please help?

---

### Post by Tiede on 2005-09-06
Sorry vkkim, I've been out for a while... I see your sound problem is still nowhere to be fixed. Try this. After killing everything, reload esd. I just want to make sure everything is alright, because your computer says one instance of esd was running before. So killall esd, killall mixer_app, check lsof /dev/snd/* and lsof /dev/dsp. And then do this:
```
esd
```
You should hear about five little bell-like short sounds as esd starts... If it does not, post the output over here and I'll see what I can do.

---

### Post by Tiede on 2005-09-06
here is a great link for troubleshooting alsa I found. Sounds promising...
[Trouble Shooting AlsaOpenscrOrg](http://alsa.opensrc.org/index.php?page=TroubleShooting)

---

### Post by vkkim on 2005-09-06
[QUOTE=Tiede]Sorry vkkim, I've been out for a while... I see your sound problem is still nowhere to be fixed. Try this. After killing everything, reload esd. I just want to make sure everything is alright, because your computer says one instance of esd was running before. So killall esd, killall mixer_app, check lsof /dev/snd/* and lsof /dev/dsp. And then do this:
```
esd
```
You should hear about five little bell-like short sounds as esd starts... If it does not, post the output over here and I'll see what I can do.[/QUOTE]

Alright, lsof /dev/snd/* and lsof /dev/dsp don't print anything, but esd gives:

```
Audio device open for 44.1Khz, stereo, 16bit failed 
Trying 44.1Khz, 8bit stereo. 
Audio device open for 44.1Khz, stereo, 8bit failed 
Trying 48Khz, 16bit stereo. 
``` 

and then nothing happens.

Thanks for coming back!  This sound problem is really pissing me off...

---

### Post by vkkim on 2005-09-06
[QUOTE=Tiede]here is a great link for troubleshooting alsa I found. Sounds promising...
[Trouble Shooting AlsaOpenscrOrg](http://alsa.opensrc.org/index.php?page=TroubleShooting)[/QUOTE]
 I ran through the troubleshooting list but nothing changed... (I think I already did this a while ago)

Thanks anyway.

---

### Post by Tiede on 2005-09-06
make sure you are in the audio group

Also, there seem to be some issues with Timidity, esd, and aRts when using the latest alsa-modules. Which version are you using?

EDIT: If you are desperate, you can recompile esd with --enable-alsa=no, but then you won't hear the system sounds... So it's only if you REALLY are desperate  :-|

---

### Post by vkkim on 2005-09-06
[QUOTE=Tiede]make sure you are in the audio group

Also, there seem to be some issues with Timidity, esd, and aRts when using the latest alsa-modules. Which version are you using?

EDIT: If you are desperate, you can recompile esd with --enable-alsa=no, but then you won't hear the system sounds... So it's only if you REALLY are desperate  :-|[/QUOTE]
 I'm using alsa 1.0.8.

What do you mean by "make sure you are in the audio group"?

---

### Post by Tiede on 2005-09-06
Make sure that your permissions allow you to access the sound card, sometimes it is only set for root access -I know, stupidm but that's Linux for ya!- and it won't play on any other account until it is there. I am on a Warty Live CD right now, running on top of Windows XP (berk!) so I cannot tell you the exact path, it is somewhere in the System menu in Hoary, I believe.

---

### Post by i_netguru on 2005-09-06
Hey!

has anbody faced with this problem? CDRom is getting mounted and is being played - only if it is an audoio cd. If it contains mp3 then it says plugins o be loadd. WHat plugns & where o be installed. Pl. help.regards

---

### Post by vkkim on 2005-09-06
[QUOTE=Tiede]Make sure that your permissions allow you to access the sound card, sometimes it is only set for root access -I know, stupidm but that's Linux for ya!- and it won't play on any other account until it is there. I am on a Warty Live CD right now, running on top of Windows XP (berk!) so I cannot tell you the exact path, it is somewhere in the System menu in Hoary, I believe.[/QUOTE]
 Oh I see, that was part of the troubleshooting guide--I'm in.

---

### Post by Tiede on 2005-09-06
[QUOTE=i_netguru]Hey!

has anbody faced with this problem? CDRom is getting mounted and is being played - only if it is an audoio cd. If it contains mp3 then it says plugins o be loadd. WHat plugns & where o be installed. Pl. help.regards[/QUOTE]
 Follow [This guide](http://ubuntuguide.org/#codecs) to fix it.

---

### Post by vkkim on 2005-09-07
Bump, again, since I ran out of things to write...

---

### Post by manicka on 2005-09-08
[QUOTE=i_netguru]Hey!

has anbody faced with this problem? CDRom is getting mounted and is being played - only if it is an audoio cd. If it contains mp3 then it says plugins o be loadd. WHat plugns & where o be installed. Pl. help.regards[/QUOTE]
 [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

---

### Post by vkkim on 2005-09-16
Bump!

---

### Post by Tiede on 2005-09-21
vkkim, I have been trying for a while to find out what solutions would work for you, but most of the ones I found, you already tried them, and the other ones,well... I don't trust them. Hence, I havce only one suggestion left. If you would consider upgrading to breezy and try it again, and then file a bug...
You can also check [ these pages from the wiki ](https://wiki.ubuntu.com/FindPage?action=fullsearch&titlesearch=1&value=soundcard) maybe they might do something.
Sorry, but that's all I have for now.

---

### Post by hub on 2005-09-30
[QUOTE=tuxrtfm]I have the same sound device.  After opening the volume control goto edit - prefences and select exteranal amplifier then close box.  Check the Control tab and mke sure that exernal amp is NOT checked then while play some sort of music file slowly raise the pcm slide under the playback tab.
Good-Luck[/QUOTE]

Hi have the same sound card on a laptop Gateway GB3525 (Intel 82801DB-ICH4).
I wasn't able to find a way to have sound on Hoary til your post
Thank you very very much!
:D

---

### Post by hub on 2005-09-30
However I am using esd as my sound system.
I have just notice that when i switch to alsa i've got no sound at all. (and xmms returns an error type "everything works normally but you've got no sound" (thanks for noticing me...)).

---

### Post by Tiede on 2005-10-21
Well, that must be because esd is clogging up the sound server. Try this in a terminal:
```
killall esd
``` and then try to play something using alsa.

---

### Post by protenniser on 2007-09-19
Hi,

I don't know either you have solved your problem or not and I am not a GURU either but. I had very similar experience with sound on feisty fawn had very similar outputs in the console. And here is the solution:

First do you dual boot?
I am, with Xp and I think that the problem was that. I have muted the sound from xp and restarted my computer with ubuntu. After that whatever I did, there was no sound. All restartings haven't helped. However I reboot from xp again and unmute the sound in xp and restarted with ubuntu. And wadaaaa, there was all the sound!
I know it is really silly but may help you.

---

### Post by $teve on 2007-12-02
> **protenniser said:**
> Hi,

I don't know either you have solved your problem or not and I am not a GURU either but. I had very similar experience with sound on feisty fawn had very similar outputs in the console. And here is the solution:

First do you dual boot?
I am, with Xp and I think that the problem was that. I have muted the sound from xp and restarted my computer with ubuntu. After that whatever I did, there was no sound. All restartings haven't helped. However I reboot from xp again and unmute the sound in xp and restarted with ubuntu. And wadaaaa, there was all the sound!
I know it is really silly but may help you.

this worked for me! thanks. can anyone explain why windows sound affects sound in ubuntu?

---

### Post by Phkillah on 2008-06-04
because the card stores its state (mute or not; volume level) at its hardware level

---

### Post by jojojo on 2008-06-30
I am new to Ubuntu. I was also unable to get the sound from my laptop/notebook speaker out.

The numerous tips given on the Internet only helped partially.

This is what I did and how I got it to work. Hope it helps everyone who has similar problems.

1. On the toolbar at the top of the Ubuntu screen, next to the time display, there is a speaker icon. Right-mouse click it, and choose "Open Volume Control".

2. Go to "Edit" and then "Preferences". This takes you to the Volume Control Preferences box. Here, tick all the boxes for all the track options provided ("Master", "Master Mono", etc., but especially "Headphone Jack Sense" and "External Amplifier").

3. Now close that box, and go back to the Volume Control box. 

4. Click on the "Playback" tab. Make sure none of the playback tracks ("Master", "Master Mono", "Headphone", etc.) is muted. If any is muted, unmute it. Make sure none of the volume buttons are down bottom. Make sure they are up.

5. Go to the "Switches" tab. This is the essential bit I found that made it all work. Untick these two boxes: "External Amplifier" and "Headphone Jack Sense". Now, you can close the Volume Control box.

6. Now go and play your music from your music application like RhythmBox. You should hear sound now from your laptop/notebook speaker.

Good luck to you all :)

---

