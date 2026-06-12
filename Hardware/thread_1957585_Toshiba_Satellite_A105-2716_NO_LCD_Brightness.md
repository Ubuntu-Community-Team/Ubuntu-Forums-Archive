---
title: "Toshiba Satellite A105-2716 NO LCD Brightness"
date: 2012-04-12
forum: Hardware
---

### Post by kjacobs on 2012-04-12
Hello group,

Have been using Xubuntu 11.10 on this Toshiba Satellite A105-2716 for a bit now and just discovered I have no control over the LCD brightness. We use the laptop in dark environments a lot and need to be able to adjust the brightness down quite a bit. I tried loading xbacklight, but it did nothing to resolve the issue. Does anyone know how to regain control of the backlight adjustment?????


Thanks.

---

### Post by Toz on 2012-04-12
I had an older Toshiba Tecra that had brightness problems. I was able to fix it by changing a brightness setting in the BIOS. I can't remember what the setting was, but my choices were "automatic" or "manual". Changing it to "manual" made the brightness keys work.

If that doesn't work, you can try some kernel parameters to see if you can get it to work. I would suggest the following:
- acpi_backlight=vendor
- acpi_osi=Linux
- acpi_osi=Linux acpi_backlight=vendor
Information on temporarily testing kernel parameters can be found here: [https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot]("https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot").

If still no luck, open a terminal window, type in the following commands, and post back the results:
```
lsmod
ls /sys/class/backlight
dmesg | grep -i acpi
sudo lspci -vnn | grep -A10 VGA
```

---

### Post by PapaGary on 2012-04-12
Googling "intel backlight control linux" brought up [this page]("http://www.lesswatts.org/tips/graphics.php") which might be helpful.

---

### Post by kjacobs on 2012-04-12
OK....thanks for the replies. I tried going into the BIOS and found a setting for power saving that had a user setting for display brightness, but that only dimmed it a little and still did not help with a manually adjustable brightness.

Here are the results from the requested commands in terminal....

kenneth@kenneth-Satellite-A105:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  4 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek   254163  1 
lib80211_crypt_ccmp    12789  2 
joydev                 17393  0 
snd_hda_intel          24262  3 
snd_hda_codec          91859  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
pcmcia                 39822  0 
snd_pcm                80435  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
ipw2200               146148  0 
i915                  509519  2 
libipw                 46701  1 ipw2200
snd_seq_midi_event     14475  1 snd_seq_midi
tifm_7xx1              12937  0 
psmouse                73673  0 
cfg80211              172427  2 ipw2200,libipw
tifm_core              15040  1 tifm_7xx1
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
serio_raw              12990  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
lib80211               14570  3 lib80211_crypt_ccmp,ipw2200,libipw
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
binfmt_misc            17292  1 
drm_kms_helper         32889  1 i915
snd                    55902  16 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   192194  3 i915,drm_kms_helper
soundcore              12600  1 snd
i2c_algo_bit           13199  1 i915
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
sky2                   49317  0 
kenneth@kenneth-Satellite-A105:~$ ls /sys/class/backlight
intel_backlight
kenneth@kenneth-Satellite-A105:~$ dmesg | grep -i acpi
[    0.000000]  BIOS-e820: 000000003f7dfffc - 000000003f7fffc0 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f7fffc0 - 000000003f800000 (ACPI NVS)
[    0.000000] ACPI: RSDP 000e5010 00014 (v00 TOSINV)
[    0.000000] ACPI: RSDT 3f7f8e57 00034 (v01 TOSINV RSDT_000 00000100 ABCD 00010200)
[    0.000000] ACPI: FACP 3f7ffb30 00074 (v01 TOSINV FACP_000 00000100 0000 00010200)
[    0.000000] ACPI: DSDT 3f7f94a0 06683 (v01 TOSINV SONOMA   00001004 INTL 02002036)
[    0.000000] ACPI: FACS 3f7fffc0 00040
[    0.000000] ACPI: MCFG 3f7ffbc0 0003C (v01 INSYDE MCFG_000 30303030 0000 30303030)
[    0.000000] ACPI: SSDT 3f7f9045 00237 (v01  PmRef  Cpu0Ist 00003000 INTL 20030522)
[    0.000000] ACPI: SSDT 3f7f8e8b 001BA (v01  PmRef  Cpu0Cst 00003001 INTL 20030522)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.017225] ACPI: Core revision 20110413
[    0.017319] ACPI: Forced DSDT copy: length 0x06683 copied locally, original unmapped
[    0.021582] ACPI: setting ELCR to 0200 (from 0c20)
[    0.028861] PM: Registering ACPI NVS region at 3f7fffc0 (64 bytes)
[    0.032343] ACPI: bus type pci registered
[    0.035173] ACPI: EC: Look up EC in DSDT
[    0.040118] ACPI: Interpreter enabled
[    0.040125] ACPI: (supports S0 S3 S4 S5)
[    0.040149] ACPI: Using PIC for interrupt routing
[    0.040359] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.064835] ACPI: Power Resource [PFA1] (off)
[    0.065243] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.072127] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    0.072135] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.072494] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.074654] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.076267] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.076516] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.076599] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.076701] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.076818]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.076822]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.076825] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.100250] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 *11)
[    0.100310] ACPI: PCI Interrupt Link [LNKB] (IRQs 10) *11
[    0.100368] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 *11)
[    0.100426] ACPI: PCI Interrupt Link [LNKD] (IRQs 10) *5
[    0.100484] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.100542] ACPI: PCI Interrupt Link [LNKF] (IRQs 10) *0, disabled.
[    0.100600] ACPI: PCI Interrupt Link [LNKG] (IRQs 6) *11
[    0.100658] ACPI: PCI Interrupt Link [LNKH] (IRQs 5 *10)
[    0.101326] PCI: Using ACPI for IRQ routing
[    0.113146] pnp: PnP ACPI init
[    0.113182] ACPI: bus type pnp registered
[    0.116630] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.116767] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.120308] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.120359] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active)
[    0.120454] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.120635] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.120709] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.120787] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.128123] pnp 00:08: Plug and Play ACPI device, IDs SYN1903 SYN1900 SYN0002 PNP0f13 (active)
[    0.128188] pnp: PnP ACPI: found 9 devices
[    0.128191] ACPI: ACPI bus type pnp unregistered
[    0.128195] PnPBIOS: Disabled by ACPI PNP
[    0.165077] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    0.165186] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    0.165300] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    0.272307] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.276425] ACPI: AC Adapter [AC] (off-line)
[    0.280115] ACPI: Lid Switch [LID0]
[    0.280184] ACPI: Power Button [PWRB]
[    0.280258] ACPI: Power Button [PWRF]
[    0.280341] ACPI: Fan [FAN1] (off)
[    0.280351] ACPI: acpi_idle registered with cpuidle
[    0.370139] ACPI: Thermal Zone [TZCR] (50 C)
[    0.376566] ACPI: Thermal Zone [TZVR] (0 C)
[    0.384404] ACPI: Thermal Zone [TZVL] (0 C)
[    0.392363] ACPI: Thermal Zone [TZCL] (37 C)
[    0.392406] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.402057] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[    0.496418] ACPI: Battery Slot [BAT1] (battery present)
[    0.562030] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[   18.271870] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   19.588677] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 6
kenneth@kenneth-Satellite-A105:~$ sudo lspci -vnn | grep -A10 VGA
[sudo] password for kenneth: 
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Toshiba America Info Systems Device [1179:ff10]
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at d0000000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at e000 [size=8]
	Memory at a0000000 (32-bit, prefetchable) [size=256M]
	Memory at d0080000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [d0] Power Management version 2
	Kernel driver in use: i915
	Kernel modules: intelfb, i915
kenneth@kenneth-Satellite-A105:~$ 


Hopefully this gibberish makes sense to someone....heehee.

---

### Post by Toz on 2012-04-12
Were you able to try the kernel parameters and did they make a difference?

And, what do these commands return?
```

cat /sys/class/backlight/intel_backlight/actual_brightness
cat /sys/class/backlight/intel_backlight/max_brightness

```

---

### Post by kjacobs on 2012-04-13
OK...I read up and tried the grub commands at bootup...
- acpi_backlight=vendor
- acpi_osi=Linux
- acpi_osi=Linux acpi_backlight=vendor

Nothing changed with any of these attempts.

Here is the results from the other commands....

kenneth@kenneth-Satellite-A105:~$ cat /sys/class/backlight/intel_backlight/actual_brightness
0
kenneth@kenneth-Satellite-A105:~$ cat /sys/class/backlight/intel_backlight/max_brightness
1
kenneth@kenneth-Satellite-A105:~$

---

### Post by Toz on 2012-04-14
> **kjacobs said:**
> OK...I read up and tried the grub commands at bootup...
- acpi_backlight=vendor
- acpi_osi=Linux
- acpi_osi=Linux acpi_backlight=vendor

Nothing changed with any of these attempts.

Here is the results from the other commands....

kenneth@kenneth-Satellite-A105:~$ cat /sys/class/backlight/intel_backlight/actual_brightness
0
kenneth@kenneth-Satellite-A105:~$ cat /sys/class/backlight/intel_backlight/max_brightness
1
kenneth@kenneth-Satellite-A105:~$

Actual brightness is 0 and max_brightness is 1. This is not good. Can you try booting with the **acpi_backlight=vendor** paramater again and while booted with that parameter, post back the results of these commands:
```

cat /proc/cmdline
ls /sys/class/backlight
cat /sys/class/backlight/intel_backlight/actual_brightness
cat /sys/class/backlight/intel_backlight/max_brightness
cat /proc/acpi/video/GFX0/LCD/brightness

```

And, what is your bios brightness setting currently set at?

---

### Post by kjacobs on 2012-04-14
The system bios is kind of strange. There is no LCD Brightness setting except under the battery save......that is presently set for USER SETTING and BRIGHT, which is the lowest setting.

Here are the result of the commands with acpi_backlight=vendor running at bootup...

kenneth@kenneth-Satellite-A105:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.0.0-17-generic root=UUID=8b999d7f-1acc-4c83-a963-48df2932bf51 ro acpi_backlight=vendor quiet splash vt.handoff=7
kenneth@kenneth-Satellite-A105:~$ ls /sys/class/backlight
intel_backlight
kenneth@kenneth-Satellite-A105:~$ cat /sys/class/backlight/intel_backlight/actual_brightness
1
kenneth@kenneth-Satellite-A105:~$ cat /sys/class/backlight/intel_backlight/max_brightness
1
kenneth@kenneth-Satellite-A105:~$ cat /proc/acpi/video/GFX0/LCD/brightness
cat: /proc/acpi/video/GFX0/LCD/brightness: No such file or directory
kenneth@kenneth-Satellite-A105:~$ 


As a side note.....I also have an HP Compaq nx6110 with the same xubuntu 11.10 on it and the brightness controls work fine. It does not dim all the way, but gets noticeably darker....

---

### Post by Toz on 2012-04-14
Hmmm. Is there a bios update available for this laptop? 

There is some information located in this bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/81401]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/81401") that indicates that some sort of brightness control is available with bios version 5.50 (the bug report is old, but it might still yield some useful information).

---

### Post by kjacobs on 2012-04-14
I may have to look into the BIOS update option. But, it is going to have to wait until after the theater shows were are using it for, for obvious reasons....LOL. We are using it for theater lighting control for 5 more shows, then I will check it out at that point. Thanks so far for the input....will check in after the shows.

Ken

---

