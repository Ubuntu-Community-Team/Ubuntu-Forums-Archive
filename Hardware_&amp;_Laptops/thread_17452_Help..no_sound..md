---
title: "Help..no sound."
date: 2005-02-28
forum: Hardware &amp; Laptops
---

### Post by Campitor on 2005-02-28
I've been surfing the posts and I havent been able to get a solution for my problem.  I also am a more complicated case because  I dont even know what kind of a sound card I have.  I'll post most of the info ubuntu-guru's request

output of lspci:

0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0b.0 VGA compatible controller: Matrox Graphics, Inc. MGA 2164W [Millennium II]
0000:00:0c.0 Ethernet controller: 3Com Corporation 3c595 100BaseTX [Vortex]

output of lsmod:
Module                  Size  Used by
proc_intf               3968  0
freq_table              4356  0
cpufreq_userspace       5336  0
cpufreq_powersave       2048  0
ipv6                  230148  10
af_packet              20872  2
3c59x                  36776  0
uhci_hcd               29328  0
usbcore               104292  3 uhci_hcd
pci_hotplug            30640  0
intel_agp              20512  1
agpgart                31784  1 intel_agp
analog                 10784  0
gameport                4736  1 analog
floppy                 54996  0
pcspkr                  3816  0
rtc                    12216  0
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
ide_floppy             16896  1
parport_pc             32064  1
lp                     10436  0
parport                37320  2 parport_pc,lp
ide_cd                 38276  0
tsdev                   7168  0
evdev                   9216  0
cdrom                  35872  1 ide_cd
mousedev               10124  1
psmouse                17800  0
ext3                  109672  2
jbd                    54552  1 ext3
ide_generic             1664  0
piix                   12576  1
ide_disk               16768  5
ide_core              125272  5 ide_floppy,ide_cd,ide_generic,piix,ide_disk
unix                   26160  978
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb

now...when I type
 %> sudo alsamixer M  

alsamixer: function snd_ctl_open failed for default: No such file or directory

In my hardware browser, my sound card is not recognized.  Is there any way I can find the type of sound card I have so I can check if alsa is compatible?

thanks for your help and if you need more info, let me know.

Camp.

---

