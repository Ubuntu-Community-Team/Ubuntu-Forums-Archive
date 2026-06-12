---
title: "temperature not registering"
date: 2009-04-19
forum: Hardware
---

### Post by disparais on 2009-04-19
I'm somewhat new to using Ubuntu - my boyfriend convinced me to try it as a lightweight alternative to Vista - so he may know his ****, but I still don't know anything about it (and he doesn't live nearby). I don't know what information I'm supposed to provide here or how to do it. As a disclaimer.

My laptop's not reading the temperature. It consistently says it's 0 degrees, and it eventually becomes so hot I can't use it. About forty-five minutes into a class, it just needs to go off because I can't tolerate it anymore.

Where do I start to fix it?

---

### Post by 67GTA on 2009-04-19
Give us a little info, and we might be able to help. What is the brand/model? Open a terminal and post the output of these commands.

```
lspci
```

```
dmesg | grep acpi
```

```
cat /proc/acpi/thermal_zone/THRM/state

```

---

### Post by disparais on 2009-04-20
The laptop is a Compaq C700 series.

and the commands you gave me:

```
sunshine@Kamiakin:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

```
sunshine@Kamiakin:~$ dmesg | grep acpi
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    3.600378] pata_acpi 0000:00:1f.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.600421] pata_acpi 0000:00:1f.1: setting latency timer to 64
[    3.600438] pata_acpi 0000:00:1f.1: PCI INT B disabled
[   13.530758] acpi device:17: registered as cooling_device2
```

```
sunshine@Kamiakin:~$ cat /proc/acpi/thermal_zone/THRM/
statecat: /proc/acpi/thermal_zone/THRM/state: No such file or directory
```

---

### Post by disparais on 2009-04-20
Oops. I know I blew the last one and typed the wrong thing, but when I retried it with the correct command, the error was still the same.

---

### Post by 67GTA on 2009-04-20
The last command failed because your temp settings aren't being recognized, so the folder we were querying didn't exist. First lets try to install lm-sensors to see if there is a temp sensor for your laptop. Open a terminal and run ```
sudo apt-get install lm-sensors
``` Once it is done, run ```
sudo sensors-detect
``` You will have to hit "enter" each time it asks as it probes for missing modules for your hardware. The default answer is yes for each one until the very last. It will ask if you want it to write to /etc/modules. The default here is "no". You want to type "yes" and hit enter. The /etc/modules file lists modules not included in the kernel by default that need to be loaded at each boot. Now go to Menu>System>Administration>Services. Click the unlock button and enter your password. Then look for "Hardware Monitor (lm-sensors)" and make sure the box is checked. Now reboot and rerun the commands I posted ealier to see if anything has changed.

---

### Post by disparais on 2009-04-20
Nothing's changed. I'm still getting the message that the directory doesn't exist.

---

### Post by 67GTA on 2009-04-20
That may mean we will have to get our hands dirty:( What version of Ubuntu are you running? Post the output of ```
lsmod
``` from a terminal.

---

### Post by disparais on 2009-04-20
I'm running Ibex.

```
sunshine@Kamiakin:~$ lsmod
Module                  Size  Used by
ipv6                  263972  10 
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18944  1 
fat                    57376  1 vfat
i915                   38656  2 
drm                    86056  3 i915
af_packet              25728  4 
binfmt_misc            16904  1 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
rfcomm                 44560  0 
l2cap                  30464  6 bnep,rfcomm
bluetooth              61924  6 sco,bnep,rfcomm,l2cap
ppdev                  15748  0 
acpi_cpufreq           15500  1 
cpufreq_userspace      11396  0 
cpufreq_powersave       9856  0 
cpufreq_stats          13188  0 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  1 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
container              11520  0 
sbs                    19464  0 
pci_slot               12680  0 
sbshc                  13440  1 sbs
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
coretemp               14080  0 
parport_pc             39332  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
ath_pci                99096  0 
wlan                  211952  1 ath_pci
ath_hal               198864  1 ath_pci
snd_hda_intel         384176  2 
arc4                    9984  2 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
ecb                    10880  2 
snd_seq_dummy          10884  0 
crypto_blkcipher       25476  1 ecb
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
psmouse                45200  0 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ath5k                 117380  0 
snd_timer              29960  2 snd_pcm,snd_seq
serio_raw              13444  0 
evdev                  17696  11 
mac80211              226344  1 ath5k
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                 10624  0 
led_class              12164  1 ath5k
video                  25232  0 
snd                    63268  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
output                 11008  1 video
cfg80211               50200  2 ath5k,mac80211
soundcore              15328  1 snd
ac                     12292  0 
wmi                    14504  0 
battery                18436  0 
iTCO_wdt               18596  0 
button                 14224  0 
intel_agp              33724  1 
agpgart                42184  3 drm,intel_agp
iTCO_vendor_support    11652  1 iTCO_wdt
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
ata_generic            12932  0 
sd_mod                 42392  5 
crc_t10dif              9984  1 sd_mod
ata_piix               24708  0 
8139cp                 27520  0 
sg                     39732  0 
usb_storage            82624  1 
libusual               30356  1 usb_storage
ahci                   37132  2 
pata_acpi              12160  0 
8139too                31616  0 
ehci_hcd               43788  0 
mii                    13440  2 8139cp,8139too
libata                178208  4 ata_generic,ata_piix,ahci,pata_acpi
scsi_mod              155212  5 sr_mod,sd_mod,sg,usb_storage,libata
dock                   16656  1 libata
uhci_hcd               30864  0 
usbcore               149488  5 usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 
```

---

### Post by 67GTA on 2009-04-21
Sorry for the delay. Have you tried looking in your Bios to see if there are any acpi/fan settings? If so, they might be conflicting with Ubuntu's power settings. I think you can hit F1 on Compaqs when the computer starts up to access the Bios. If not, you might have a buggy DSDT. I wrote a how to here: [http://ubuntuforums.org/showthread.php?t=1036051 ]("http://ubuntuforums.org/showthread.php?t=1036051")If that scares you, you could email me a copy of your dsdt.dat from the second command in the howto, and I will look at it for you.

---

### Post by disparais on 2009-04-24
There actually is no fan-related settings in the BIOS. It was one of the first things I looked for. ]:

---

### Post by 67GTA on 2009-04-24
If your DSDT file isn't causing it, you might need to file a bug report on your laptop model.

---

### Post by disparais on 2009-04-25
I installed Jackalope today, actually, and it solved it. I can get a reading of the temperature now, and all the problems that I had with Ibex aren't an issue now anymore, either.

=/

So who knows.

Thank you for the help.

---

