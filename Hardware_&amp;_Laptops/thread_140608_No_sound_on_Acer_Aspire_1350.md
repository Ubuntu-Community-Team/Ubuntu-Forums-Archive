---
title: "No sound on Acer Aspire 1350"
date: 2006-03-06
forum: Hardware &amp; Laptops
---

### Post by BluntedBoyWonder on 2006-03-06
Hello all. I have been reading the threads on the other Acer laptop sound issues but they all deal with other soundcards than my Acer Aspire 1350... 

I installed Ubuntu 5.10 from the official install cd and sound worked fine. I upgraded to kernel 2.6.x and: :-# not a word from my speakers. 

I can't use alsamixer:
*alsamixer: function snd_ctl_open failed for default: No such file or directory*

and alsaconf doesn't find my card.


My lspci:
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400] Chipset Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
0000:00:07.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
0000:00:08.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 **Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)**
0000:00:11.6 Communication controller: VIA Technologies, Inc. Intel 537 [AC97 Modem] (rev 80)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

my lsmod:
Module                  Size  Used by
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
powernow_k7             8616  0
cpufreq_userspace       4444  1
cpufreq_stats           5124  0
freq_table              4484  2 powernow_k7,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
pcmcia                 24584  2
lp                     11460  0
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  6
joydev                  9280  0
mousedev               10912  1
tsdev                   7616  0
floppy                 52692  0
parport_pc             31812  1
parport                32072  2 lp,parport_pc
psmouse                26116  0
evdev                   9088  1
pcspkr                  3652  0
rtc                    11832  0
i2c_viapro              7696  0
i2c_core               19728  2 i2c_acpi_ec,i2c_viapro
via_ircc               23700  0
irda                  159804  1 via_ircc
crc_ccitt               2176  1 irda
ohci1394               30644  0
ieee1394               90936  1 ohci1394
yenta_socket           22540  1
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
via_agp                 9472  1
agpgart                32328  1 via_agp
dm_mod                 50364  1
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  2 powernow_k7,thermal
fan                     4740  0
usbhid                 30688  0
via_rhine              20356  0
mii                     5248  1 via_rhine
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104316  4 usbhid,ehci_hcd,uhci_hcd
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_disk               16128  3
ide_generic             1664  0
via82cxxx              12188  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,via82cxxx
unix                   24624  632
capability              5000  0
commoncap               6784  1 capability
vesafb                  8088  1
vgastate                8320  0
softcursor              2432  1 vesafb
cfbimgblt               2944  1 vesafb
cfbfillrect             3840  1 vesafb
cfbcopyarea             4480  1 vesafb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

None of the solutions in the other threads worked for me. I hope someone can help. 

Finally, I did download a driver package from the Realtek website and tried to install it (which failed, because alsaconf screwed up somewhere). I am afraid it might have fiddled with some of my sound settings without my knowledge. I was able to use alsamixer just fine before, for example, now it seems to have gone in a puff of smoke.

---

