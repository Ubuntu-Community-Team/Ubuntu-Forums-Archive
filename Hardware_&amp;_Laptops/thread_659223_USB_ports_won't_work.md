---
title: "USB ports won't work"
date: 2008-01-05
forum: Hardware &amp; Laptops
---

### Post by edgranholm on 2008-01-05
Hello everyone, I'm a brand new linux user thanks to a nasty crash.  I'm really liking Ubuntu so far, but I have a problem... none of my usb ports work.  I'm not really convinced it's linux's fault, though.  After my computer crashed (wouldn't boot up past the windows logo screen) I installed my wife's version of windows temporarily just to get my files off the computer.  Everything was going fine until I go to try to hook stuff up to the usb ports.  Nothing will happen when I do.  Luckily, I had a PCMCIA card that had 2 usb ports on it that worked.  However, they were supposed to be 2.0 usb, but would only run at 1.1 usb.  

So, after spending hours upon hours of getting my files off my computer, I formatted it and put Ubuntu 7.10 on it with no problems at all, other than the usb ports not working, and the sound being not quite right.  

The computer is an Acer Aspire 5100.  

Any ideas as to what the problem might be?  I'll gladly provide more information if needed.  

Thanks!

---

### Post by Yellow Pasque on 2008-01-05
Let's make sure your system recognizes the usb controllers. Run the following:
```
sudo update-pciids
sudo lspci
```
Copy/paste the output from the lspci command here so we can get an idea of what hardware you have.

Then, do an lsmod command and make sure the USB module is loaded. You should see a line like this:
```
usbcore               144432  4 usbhid,ehci_hcd,ohci_hcd
```

What do you mean when you say that the ports do not work? Do devices even receive power? If so, try plugging them in and running the lsusb command.

I'd also suggest checking in your BIOS to make sure all USB ports are enabled and USB 2.0 support is enabled.

---

### Post by Yellow Pasque on 2008-01-05
One other thing:
Have you updated to the latest BIOS?

---

### Post by edgranholm on 2008-01-05
Here's the lspci
```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:02.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)

```

and here's the lsmod
```
Module                  Size  Used by
ipv6                  317192  10 
wlan_wep                8576  1 
af_packet              28172  4 
fglrx                 765588  34 
rfcomm                 47656  2 
l2cap                  28672  11 rfcomm
bluetooth              63876  4 rfcomm,l2cap
ppdev                  11272  0 
powernow_k8            16608  1 
cpufreq_conservative     9608  0 
cpufreq_stats           8160  0 
cpufreq_userspace       6048  0 
cpufreq_ondemand       10896  1 
freq_table              6464  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       3072  0 
container               6400  0 
sbs                    21520  0 
video                  21140  0 
dock                   12264  0 
button                 10400  0 
battery                12424  0 
ac                      7304  0 
parport_pc             41896  0 
lp                     15048  0 
parport                44172  3 ppdev,parport_pc,lp
joydev                 13440  0 
snd_hda_intel         337192  1 
pcmcia                 46232  0 
snd_pcm_oss            50048  0 
snd_mixer_oss          20096  2 snd_pcm_oss
snd_pcm                94344  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            36864  0 
snd_seq_midi           11008  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi
snd_seq                62496  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
yenta_socket           30220  1 
rsrc_nonstatic         14208  1 yenta_socket
snd_timer              27272  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia_core            46628  3 pcmcia,yenta_socket,rsrc_nonstatic
sdhci                  21004  0 
i2c_piix4              11020  0 
snd                    69288  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mmc_core               33416  1 sdhci
soundcore              10272  2 snd
wlan_scan_sta          16640  1 
ath_rate_sample        15616  1 
psmouse                45596  0 
pcspkr                  4608  0 
serio_raw               9092  0 
snd_page_alloc         12560  2 snd_hda_intel,snd_pcm
i2c_core               30208  1 i2c_piix4
ath_pci               105392  0 
wlan                  225736  5 wlan_wep,wlan_scan_sta,ath_rate_sample,ath_pci
shpchp                 38300  0 
pci_hotplug            36612  1 shpchp
k8temp                  7680  0 
ath_hal               219888  3 ath_rate_sample,ath_pci
evdev                  13056  6 
ext3                  146576  1 
jbd                    69360  1 ext3
mbcache                11272  1 ext3
ide_cd                 35488  0 
cdrom                  41768  1 ide_cd
ide_disk               20352  3 
8139cp                 28032  0 
8139too                31232  0 
mii                     7424  2 8139cp,8139too
ehci_hcd               40076  0 
atiixp                  7824  0 [permanent]
ide_core              141200  3 ide_cd,ide_disk,atiixp
ohci_hcd               25092  0 
ata_generic             9988  0 
libata                138928  1 ata_generic
scsi_mod              172856  1 libata
usbcore               161584  3 ehci_hcd,ohci_hcd
thermal                16528  0 
processor              36232  2 powernow_k8,thermal
fan                     6920  0 
fuse                   52528  1 
apparmor               47008  0 
commoncap               9472  1 apparmor
```

and here's what I get with the lsusb command
```
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000 
```


I couldn't see anywhere in my bios that said whether the usb ports were enabled or not.  I think my bios version is 2.0.  I'll go check and confirm this or not though.  If my bios is out of date, where should I go to get an update for it?

---

### Post by Yellow Pasque on 2008-01-06
Go here: [http://support.acer-euro.com/drivers/notebook/as_5100.html](http://support.acer-euro.com/drivers/notebook/as_5100.html)
I would definitely recommend updating the BIOS because I was looking through the release notes of the different BIOS versions and saw some USB issues that were fixed.

---

### Post by edgranholm on 2008-01-06
Thanks for the link!  I was having trouble finding that.

Do I get the XP version?  I didn't notice anything that said Linux.

If that's what I get, how do I install it with Linux?  (sorry for my noobness:redface:)

---

