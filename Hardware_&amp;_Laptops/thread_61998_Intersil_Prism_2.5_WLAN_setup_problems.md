---
title: "Intersil Prism 2.5 WLAN setup problems"
date: 2005-09-02
forum: Hardware &amp; Laptops
---

### Post by steelsnake on 2005-09-02
I've looked for a few days now and no luck... 

Network config:
WLAN router with WEP128 enabled
Sony R505 with Intersil Prism 2.5 Wavelan rev 01

Ubuntu did detect the Prism, but something went wrong somewhere. I've probably messed it up additionally.... pleeeease help :) Ethernet works fine btw, that's how I posted this.

Anyway, here's the current diagnostic output. I've replaced the WEP key with FF, just in case anyone wonders

lspci:
0000:02:0b.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)

dmesg (relevant part, i hope):
e100: eth0: e100_probe: addr 0xe0204000, irq 9, MAC addr 08:00:46:77:D2:CE
orinoco 0.13e (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
orinoco_pci 0.13e (Pavel Roskin <proski@gnu.org>, David Gibson <hermes@gibson.dropbear.id.au> & Jean Tourrilhes <jt@hpl.hp.com>)
ACPI: PCI interrupt 0000:02:0b.0[A] -> GSI 9 (level, low) -> IRQ 9
orinoco_pci: Detected Orinoco/Prism2 PCI device at 0000:02:0b.0, mem:0xE0500000 to 0xE0500FFF -> 0xe0bae000, irq:9
Reset done.............................................................................................................................................................................................................................................;
Clear Reset...........................................................<7>ieee1394: Host added: ID:BUS[0-00:1023]  GUID[080046030143f72b]
orinoco_lock() called with hw_unavailable (dev=df4fd000)
............................................................................................................................................................................................................................................................................................<7>orinoco_lock() called with hw_unavailable (dev=df4fd000)
.<7>orinoco_lock() called with hw_unavailable (dev=df4fd000)
  Vendor: Sony      Model: MSC-U03           Rev: 1.00
  Type:   Direct-Access                      ANSI SCSI revision: 00
orinoco_lock() called with hw_unavailable (dev=df4fd000)
orinoco_lock() called with hw_unavailable (dev=df4fd000)
........<7>usb-storage: device scan complete
................................;
pci_cor : reg = 0x0 - FFFBEF34 - FFFBED40
orinoco_lock() called with hw_unavailable (dev=df4fd000)
orinoco_lock() called with hw_unavailable (dev=df4fd000)
orinoco_lock() called with hw_unavailable (dev=df4fd000)
orinoco_lock() called with hw_unavailable (dev=df4fd000)
orinoco_lock() called with hw_unavailable (dev=df4fd000)
orinoco_lock() called with hw_unavailable (dev=df4fd000)
orinoco_lock() called with hw_unavailable (dev=df4fd000)
orinoco_lock() called with hw_unavailable (dev=df4fd000)
orinoco_lock() called with hw_unavailable (dev=df4fd000)
Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
orinoco_lock() called with hw_unavailable (dev=df4fd000)
orinoco_lock() called with hw_unavailable (dev=df4fd000)
eth1: Station identity 001f:0003:0001:0004
eth1: Looks like an Intersil firmware version 1.4.3
eth1: Ad-hoc demo mode supported
eth1: IEEE standard IBSS ad-hoc mode supported
eth1: WEP supported, 104-bit key
eth1: MAC address 00:D0:59:BD:F4:3F
eth1: Station name "Prism  I"
eth1: ready
eth1: Error -110 setting multicast list.
eth1: Error -110 setting multicast list.
eth1: New link status: Association Failed (0006)
NET: Registered protocol family 17
e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
NET: Registered protocol family 10

output of lsmod:
Module                  Size  Used by
acpi_cpufreq            5892  1
speedstep_lib           4228  0
proc_intf               4100  0
freq_table              4100  1 acpi_cpufreq
cpufreq_userspace       4572  1
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
pcmcia                 21380  2
i915                   18304  1
drm                    59412  2 i915
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
ipv6                  229504  9
af_packet              20744  2
sd_mod                 16784  0
orinoco_pci             6656  0
orinoco                38284  1 orinoco_pci
hermes                  7936  2 orinoco_pci,orinoco
e100                   32384  0
mii                     4736  1 e100
yenta_socket           19584  0
pcmcia_core            53568  2 pcmcia,yenta_socket
ohci1394               31876  0
snd_intel8x0           29984  2
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
i2c_i801                8076  0
i2c_core               21264  1 i2c_i801
hw_random               5524  0
shpchp                 86116  0
usb_storage            64064  0
pci_hotplug            30512  1 shpchp
uhci_hcd               30224  0
usbcore               107384  3 usb_storage,uhci_hcd
intel_agp              20636  1
agpgart                31784  3 drm,intel_agp
floppy                 54864  0
pcspkr                  3816  0
rtc                    12216  0
md                     43856  0
dm_mod                 53116  1
evdev                   9088  0
capability              5000  0
tsdev                   7488  0
commoncap               7808  1 capability
sr_mod                 16036  0
sbp2                   22408  0
scsi_mod              119936  4 sd_mod,usb_storage,sr_mod,sbp2
ieee1394              100408  2 ohci1394,sbp2
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  2 sr_mod,ide_cd
ext3                  120968  1
jbd                    54168  1 ext3
ide_generic             1664  0
piix                    9988  1
ide_disk               18176  3
ide_core              118988  5 usb_storage,ide_cd,ide_generic,piix,ide_disk
unix                   26164  830
thermal                13576  0
processor              22708  2 acpi_cpufreq,thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb

iwconfig eth1:
eth1      IEEE 802.11-DS  ESSID:"cathouse"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.452 GHz  Access Point: 44:44:44:44:44:44
          Bit Rate:2 Mb/s   Tx-Power=15 dBm   Sensitivity:1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Encryption key:FFFF-FFFF-FFFF-FFFF-FFFF-FFFF-FF   Security mode:open
          Power Management:off
          Link Quality=0/92  Signal level=-68 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwlist eth1 encryption (key obfuscated):
eth1      2 key sizes : 40, 104bits
          4 keys available :
                [1]: FFFF-FFFF-FFFF-FFFF-FFFF-FFFF-FF (104 bits)
                [2]: off
                [3]: off
                [4]: off
          Current Transmit Key: [1]
          Security mode:open

---

