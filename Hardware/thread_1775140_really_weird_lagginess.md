---
title: "really weird lagginess"
date: 2011-06-04
forum: Hardware
---

### Post by nerdy_kid on 2011-06-04
This just started happening to me.

I was reading a wikipedia article, when suddenly my entire system got so laggy it was almost unusable.  htop showed compiz at about 60% of one of my cores, Xorg was at about 40%, and several other programs showed at least twice as high CPU.  Restarting Unity/Compiz did nothing except seg fault, so I logged out and back it -- same issue.  I killed X and dropped to the console, but the console was extremely laggy as well -- running htop showed htop using 30% CPU.  I rebooted, no change.  I shut the system off completely, and started it back up and everything worked as normal.  Then, after a resume, the problem happened again -- process using at least twice the CPU they normally used, with everything (including console) almost unusable.  I reversed some changes I made weeks ago to initramfs's config to get my nvidia card to display plymouth, think that maybe somehow uvesafb was messing something up -- no change.

There was an security update for xserver two days before this all started happening, but other then that, nothing core has been updated.  I had been messing with qemu emulation, so I uninstalled all related packages, no change.  I hope you guys can help, I'm kinda stuck lol

lspci:
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600M GT] (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

```

lsmod:
```

Module                  Size  Used by
snd_hrtimer            12680  1 
rfcomm                 38125  8 
binfmt_misc            13213  1 
sco                    17779  2 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
vboxnetadp             13348  0 
vboxnetflt             27855  0 
vboxdrv               238410  2 vboxnetadp,vboxnetflt
parport_pc             32111  0 
ppdev                  12849  0 
sha256_generic         20911  2 
cryptd                 19801  0 
aes_i586               16956  4 
aes_generic            38023  1 aes_i586
dm_crypt               22463  1 
nvidia               9766978  64 
joydev                 17322  0 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
btusb                  18160  2 
bluetooth              65565  9 rfcomm,sco,bnep,l2cap,btusb
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
b44                    35301  0 
snd_seq                51291  3 snd_seq_midi,snd_seq_midi_event
dell_wmi               12601  0 
ssb                    45942  1 b44
sparse_keymap          13666  1 dell_wmi
dell_laptop            13515  0 
dcdbas                 14054  1 dell_laptop
snd_timer              28659  3 snd_hrtimer,snd_pcm,snd_seq
lib80211_crypt_tkip    17203  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
wl                   2642531  0 
r852                   17878  0 
sm_common              16737  1 r852
nand                   49822  2 r852,sm_common
nand_ids                8547  1 nand
psmouse                73312  0 
snd                    55295  14 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nand_ecc               13070  1 nand
mtd                    26720  2 sm_common,nand
serio_raw              12990  0 
soundcore              12600  1 snd
lib80211               14570  2 lib80211_crypt_tkip,wl
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
sdhci_pci              13623  0 
firewire_ohci          31504  0 
video                  18951  0 
firewire_core          56138  1 firewire_ohci
sdhci                  22720  1 sdhci_pci
crc_itu_t              12627  1 firewire_core

```

I'll post my Xorg log and dmesg as soon as the problem happens again.  Please let me know if there are any more logs I can provide!

---

### Post by nerdy_kid on 2011-06-05
bump

---

### Post by nerdy_kid on 2011-06-06
just happened again, nothing in any logs.  However, I put the system into single user mode (sudo telinit S) and found that kworker was using 60% of one of my cores.  Did some googling, and it seems kworker handles ACPI wakeup calls from the BIOS...

If anyone can help me get to the bottom of this it would be great!

---

### Post by nerdy_kid on 2011-06-06
my laptop actually might have been overheating, I cleaned a haunted house's worth of dust out of the cooling system, so maybe that will fix everything.

---

