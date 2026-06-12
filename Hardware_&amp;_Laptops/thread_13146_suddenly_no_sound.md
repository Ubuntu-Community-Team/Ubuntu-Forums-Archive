---
title: "suddenly no sound"
date: 2005-01-29
forum: Hardware &amp; Laptops
---

### Post by ubuntu_demon on 2005-01-29
Hi,

suddenly sound doesn't work anymore at all. I use ubuntu warty + backports.

In windows XP my sound does work!

when I used dmesg these are the relevant lines I found :

AC'97 0 analog subsections not ready
ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 201
ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 201
PCI: Setting latency timer of device 0000:00:1f.5 to 64

this is my lspci :

0000:00:00.0 Host bridge: Intel Corp. 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 82865G/PE/P PCI to AGP Controller (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801BA/CA/DB/EB/ER Hub interface to PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corp. 82801EB/ER (ICH5/ICH5R) LPC Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801EB/ER (ICH5/ICH5R) Ultra ATA 100 Storage Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV20 [GeForce3 Ti 200] (rev a3)
0000:02:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:02:04.0 RAID bus controller: VIA Technologies, Inc. VT6410 ATA133 RAID controller (rev 06)
0000:02:05.0 Ethernet controller: 3Com Corporation 3c940 10/100/1000Base-T [Marvell] (rev 12)


this is my lsmod :

Module                  Size  Used by
proc_intf               3968  0
freq_table              4356  0
cpufreq_userspace       5336  0
cpufreq_powersave       2048  0
button                  6936  0
ac                      5132  0
battery                 9740  0
ipv6                  230020  10
smbfs                  61048  3
sk98lin               167960  1
ohci1394               32004  0
snd_intel8x0           33068  1
snd_ac97_codec         59268  1 snd_intel8x0
snd_pcm_oss            48168  0
snd_mixer_oss          16640  2 snd_pcm_oss
snd_pcm                85540  2 snd_intel8x0,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd_page_alloc         11144  2 snd_intel8x0,snd_pcm
gameport                4736  1 snd_intel8x0
snd_mpu401_uart         7296  1 snd_intel8x0
snd_rawmidi            23232  1 snd_mpu401_uart
snd_seq_device          7944  1 snd_rawmidi
snd                    50660  9 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  2 snd
hw_random               5652  0
ehci_hcd               27780  0
sn9c102                48392  0
videodev                9856  1 sn9c102
tsdev                   7168  0
usblp                  12032  0
joydev                  9536  0
usbhid                 28864  0
uhci_hcd               29328  0
usbcore               104292  7 ehci_hcd,sn9c102,usblp,usbhid,uhci_hcd
shpchp                 87276  0
pciehp                 83948  0
pci_hotplug            30640  2 shpchp,pciehp
intel_agp              20512  0
intel_mch_agp          10000  1
agpgart                31784  3 intel_agp,intel_mch_agp
nls_cp437               6016  1
ntfs                   88660  1
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
nvidia               4821428  12
parport_pc             32064  1
lp                     10436  0
parport                37320  2 parport_pc,lp
evdev                   9088  0
sbp2                   22408  0
ieee1394              100536  2 ohci1394,sbp2
ide_cd                 38276  0
mousedev               10124  1
psmouse                17800  0
sr_mod                 15780  0
scsi_mod              115148  2 sbp2,sr_mod
cdrom                  35872  2 ide_cd,sr_mod
ext3                  109544  1
jbd                    54552  1 ext3
ide_generic             1664  0
piix                   12576  1
ide_disk               16768  4
ide_core              125272  4 ide_cd,ide_generic,piix,ide_disk
unix                   25904  726
fan                     4236  0
thermal                13200  0
processor              17712  1 thermal
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb

---

### Post by Traxis on 2005-02-02
I have the same problem. Did you figure out what was wrong? Maybe it could help me work out a solution as well.

---

### Post by jamaas on 2005-02-02
Sorry, another one with the same problem, desperate to find a solution..... !  Can anyone help us diagnose this?

Thanks


Jim

[QUOTE=Traxis]I have the same problem. Did you figure out what was wrong? Maybe it could help me work out a solution as well.[/QUOTE]

---

### Post by Mr_Radarkontakt on 2005-02-02
I have sound problem too. Strange it's happening on the same day for all of us..


//Mr Radarkontakt


Edit: Got it working. Found it in this thread: [http://ubuntuforums.org/showthread.php?t=10625&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=10625&page=1&pp=10)

"Another thing to try would be stay in your ubuntu and do a sudo /etc/init.d/alsa stop.
And then delete that file and the start alsa again w/ sudo /etc/init.d/alsa start. That would work as well. "
The file is /var/lib/alsa/asound.state

Now the sound works perfectly  =D>

---

### Post by ubuntu_demon on 2005-02-04
[QUOTE=Mr_Radarkontakt]I have sound problem too. Strange it's happening on the same day for all of us..


//Mr Radarkontakt


Edit: Got it working. Found it in this thread: [http://ubuntuforums.org/showthread.php?t=10625&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=10625&page=1&pp=10)

"Another thing to try would be stay in your ubuntu and do a sudo /etc/init.d/alsa stop.
And then delete that file and the start alsa again w/ sudo /etc/init.d/alsa start. That would work as well. "
The file is /var/lib/alsa/asound.state

Now the sound works perfectly  =D>[/QUOTE]
 thnx that worked !


does anybody have an idea what's the cause of this problem ?

---

