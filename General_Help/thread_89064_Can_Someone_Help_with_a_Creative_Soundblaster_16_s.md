---
title: "Can Someone Help with a Creative Soundblaster 16 soundcard?"
date: 2005-11-11
forum: General Help
---

### Post by vanillalisterine on 2005-11-11
I'm relatively new to Ubuntu (I've used Redhat 9 for a few months and then switched when my cousin was telling me about how much better Ubuntu was...), and I'm not sure how to get my soundcard working.  I got this from terminal, though:

[   44.307822] EISA bus registered
[   44.324493] ACPI: Interpreter disabled.
[   44.324533] pnp: PnP ACPI: disabled
[   44.338267] audit: initializing netlink socket (disabled)
[   44.339448] isapnp: Scanning for PnP cards...
[   44.449134] pnp: SB audio device quirk - increasing port range
[   44.449497] isapnp: Card 'Creative ViBRA16C PnP'
[   44.449511] isapnp: 1 Plug & Play card detected total
[   44.566180] EISA: Probing bus 0 at eisa.0
[   44.566251] EISA: Detected 0 cards.
[   44.779595] input: AT Translated Set 2 keyboard on isa0060/serio0
[   46.040019] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[  105.939177] Disabled Privacy Extensions on device c02eb280(lo)
[ 2109.537251] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).

Any help would be appreciated; thanks!

---

### Post by nszabolcs on 2005-11-11
use lspci to see whether your card is detected.
use lsmod to see whether sb16 module is loaded. (if not then use modprobe)

i think all the alsa stuff should be in the default ubuntu kernel, so your card should work fine.
(supported sound cards: [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/))

---

### Post by vanillalisterine on 2005-11-12
what is lspci?  ...when i ran it, it gave me:
root@germane:/home/acy# lspci
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0f.0 PCI bridge: Digital Equipment Corporation DECchip 21152 (rev 03)
0000:00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)
0000:02:09.0 Serial controller: 5610 56K FaxModem 56K FaxModem Model 5610 (rev 01)


root@germane:/home/acy# lsmod
Module                  Size  Used by
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
apm                    19308  1
ipv6                  217408  6
af_packet              20232  2
tsdev                   7616  0
analog                 10528  0
ns558                   5508  0
gameport               14472  3 analog,ns558
rtc                    11832  0
pcspkr                  3652  0
floppy                 52692  0
i2c_piix4               8336  0
i2c_core               19728  1 i2c_piix4
pci_hotplug            24628  0
intel_agp              21276  1
agpgart                32328  1 intel_agp
dm_mod                 50364  1
evdev                   9088  0
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
processor              23100  0
usbhid                 30688  0
3c59x                  37544  0
mii                     5248  1 3c59x
uhci_hcd               28048  0
usbcore               104188  3 usbhid,uhci_hcd
ide_disk               16128  4
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_generic             1664  0
piix                    9476  1
ide_core              125268  4 ide_disk,ide_cd,ide_generic,piix
unix                   24624  597
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
...I don't think sb16 is here....

So um...I'm still a little confused... :oops:

---

### Post by nszabolcs on 2005-11-12
[QUOTE=vanillalisterine]what is lspci?[/QUOTE]

lspci does the same as the system/preferences?/devices? gnome application (sorry i'm not in front of an ubuntu box right now, but you can find it somwhere in the menus), it lists informations about your hardware and AFAIK your sound card should be there (a line sais "audio controller: sound blaster") either it's a PCI slot card or integrated on the motherboard.

if the card is not listed then it's either disabled in the bios or not detected by the linux kernel.

---

