---
title: "HP Laptop dv6-6195ca + Ubuntu 11: brightness problem"
date: 2011-10-04
forum: Hardware
---

### Post by hp6195 on 2011-10-04
I am having a problem with the brightness control on my HP dv6-6195ca laptop.  I've been fiddling with this for hours now to no avail.

The F2/F3 keys are recognized in Ubuntu 11.04 and I see the popup showing the brightness increasing and decreasing, but it has no effect on the screen.

I've looked around and a lot of threads suggest working with /proc/acpi/video/VGA/LCD/brightness, but I don't have a video directory under /proc/acpi.

/proc/acpi$ ls -l
total 0
dr-xr-xr-x 3 root root 0 2011-10-04 19:06 ac_adapter
dr-xr-xr-x 3 root root 0 2011-10-04 19:06 battery
dr-xr-xr-x 4 root root 0 2011-10-04 19:06 button
-r-------- 1 root root 0 2011-10-04 19:01 event
-rw-r--r-- 1 root root 0 2011-10-04 19:06 wakeup

lspci output:

$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 6740
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
0d:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 (rev 34)
13:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
19:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)

It appears that everything is working in Ubuntu, but I suspect that the brightness setting is not being sent to the hardware. When I turn the brightness up and down, it is being registered:

Full brightness:

$ cat /sys/devices/virtual/backlight/acpi_video0/brightness
10
$ cat /sys/devices/virtual/backlight/acpi_video1/brightness
10

Lowest brightness:

$ cat /sys/devices/virtual/backlight/acpi_video0/brightness
0
$ cat /sys/devices/virtual/backlight/acpi_video1/brightness
0


Any suggestions?

---

### Post by Toz on 2011-10-09
Hello and welcome to the forums.

Have you tried booting with the kernel parameters **acpi_osi=\\"Linux\\" acpi_backlight=vendor** ?

You might be able to manually manipulate the brightness via:
```
echo "50" | sudo tee /sys/devices/virtual/backlight/acpi_video0/brightness
```
...or
```
xrandr --output LVDS --brightness 0.5
```
("xrandr -q" will help identify the name of the display if LVDS is incorrect)
...or
```
sudo setpci -s 01:00.0 F4.B=7F
```

---

### Post by Kobnar on 2011-11-11
Hey there! I'm jumping in on this one because it's really starting to nag me.

I have an HP dv6 with intel/Radion 6700M graphics and a backlight issue that I had fixed for a few blissful weeks - and then something changed and all of a sudden it doesn't work.

For those few blissful weeks, however, this is what I did:

Edit the grub config file...
```
$ sudo /etc/default/grub
```

Add the following to GRUB_CMDLINE_LINUX_DEFAULT=""...
```
acpi_osi=Linux acpi_backlight=vendor
```
Save and quit.

Reconfigure the grub bootloader...
```
$sudo update-grub
```
Reboot.

Hopefully that helps! Maybe with a bit of karma somebody will help me.

Not to hijack your thread but that's what I did and it worked for a while until some update I wasn't tracking suddenly broke it. No matter what I do now, I can't change my brightness.

Any tips?

---

### Post by Toz on 2011-11-11
@Kobnar, what do you have in your /sys/class/backlight directory?
```
ls -l /sys/class/backlight
```
...and
```
ls -l /sys/devices/virtual/backlight
```
Also, what does 
```
lsmod
```
return?

Have you tried the codes from post #2 to see if they work?

---

### Post by Kobnar on 2011-12-22
Sorry for the late reply :/ I thought I was subscribed to this thread but apparently I wasn't.

I still have no backlight control via function keys. To change the brightness, I have to manually enter:
```
echo 1000 | sudo tee /sys/class/backlight/intel_backlight/brightness
```

That drops it down to about 50% brightness. (the xrandr settings just change the color brightness and have no effect on the actual backlight.)

Preferably, I would like to get the buttons working again. I've read around and this is all apparently because HP uses a funky ACPI.

A strange side-effect of all this is that if I leave my computer sitting for about 10 minutes, the screen goes blank and there's no way for me to get it back without unplugging it and closing the lid to force the power manager to kick it into sleep. (upon immediately opening the lid, the brightness is reset and I can see my screen again)

---

### Post by dansk on 2012-02-20
Just thought I'd bump this up.  I'm using Lubuntu 11.10 on an HP dv6-6195ca and having the same problems as the other fine people in this thread.  Anyone had any insight into this recently?

---

### Post by dansk on 2012-03-07
Just an update:

I'm having precisely the same issues as everyone else here, in the same order as them.  Adding the 'acpi_backlight=vendor' line in grub fixed the problem for me for about two days, but inexplicably quit working.

Echoing brightness values directly to /sys/class/backlight/intel_backlight/brightness works, but it's clumsy and I'd rather find a permanent fix for this.

is there any way to find out exactly what output is coming from the function keys?

---

### Post by Toz on 2012-03-08
> **dansk said:**
> Just an update:

I'm having precisely the same issues as everyone else here, in the same order as them.  Adding the 'acpi_backlight=vendor' line in grub fixed the problem for me for about two days, but inexplicably quit working.

Echoing brightness values directly to /sys/class/backlight/intel_backlight/brightness works, but it's clumsy and I'd rather find a permanent fix for this.

is there any way to find out exactly what output is coming from the function keys?

What is your current kernel command line?
```
cat /proc/cmdline
```
Have you tried these variations?
- acpi_osi=
- acpi_osi=Linux
- acpi_osi="Linux"
- acpi_osi=Linux acpi_backlight=vendor
- acpi_osi= acpi_backlight=vendor

---

### Post by dansk on 2012-03-08
> **Toz said:**
> What is your current kernel command line?
```
cat /proc/cmdline
```

BOOT_IMAGE=/boot/vmlinuz-3.0.0-16-generic root=UUID=be44ff56-60d6-40dd-9013-8036b48a58b5 ro quiet splash acpi_osi=Linux vt.handoff=7

> 
Have you tried these variations?
- acpi_osi=
- acpi_osi=Linux
- acpi_osi="Linux"
- acpi_osi=Linux acpi_backlight=vendor
- acpi_osi= acpi_backlight=vendor
I tried all of them and no dice.

---

### Post by Toz on 2012-03-08
> BOOT_IMAGE=/boot/vmlinuz-3.0.0-16-generic root=UUID=be44ff56-60d6-40dd-9013-8036b48a58b5 ro quiet splash acpi_osi=Linux vt.handoff=7
Try again with **acpi_backlight=vendor** and post back the results of the following commands:
```
cat /proc/cmdline
lsmod
ls /sys/class/backlight
sudo lspci -vnn | grep -A10 VGA
cat /var/log/syslog | grep -i acpi
```

EDIT: Can you also try these two parameters?
- **acpi_osi=\\"Linux\\"**
- **acpi_osi=\\"Linux\\" acpi_backlight=vendor**

---

### Post by dansk on 2012-03-08
> **Toz said:**
> Try again with **acpi_backlight=vendor** and post back the results of the following commands:
cat /proc/cmdline
```
BOOT_IMAGE=/boot/vmlinuz-3.0.0-16-generic root=UUID=be44ff56-60d6-40dd-9013-8036b48a58b5 ro quiet splash acpi_backlight=vendor vt.handoff=7
```

lsmod
```
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  8 
speedstep_lib          13195  0 
parport_pc             36962  0 
ppdev                  17113  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_idt      70553  1 
joydev                 17693  0 
arc4                   12529  2 
radeon               1016475  0 
ttm                    76805  1 radeon
uvcvideo               72711  0 
snd_hda_intel          33390  2 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
videodev               92992  1 uvcvideo
snd_hwdep              13668  1 snd_hda_codec
v4l2_compat_ioctl32    17083  1 videodev
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
btusb                  18600  2 
bluetooth             166112  23 bnep,rfcomm,btusb
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73882  0 
serio_raw              13166  0 
iwlagn                314257  0 
mac80211              462046  1 iwlagn
i915                  571221  2 
rts_pstor             445246  0 
cfg80211              199630  2 iwlagn,mac80211
drm_kms_helper         42558  2 radeon,i915
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm                   236290  5 radeon,ttm,i915,drm_kms_helper
mei                    41480  0 
i2c_algo_bit           13423  2 radeon,i915
wmi                    19256  1 hp_wmi
video                  19412  1 i915
hp_accel               21880  0 
lis3lv02d              19888  1 hp_accel
input_polldev          13896  1 lis3lv02d
acpi_call              12748  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ahci                   26002  2 
libahci                26861  1 ahci
xhci_hcd               82820  0 
r8169                  52788  0 

```

ls /sys/class/backlight
```
intel_backlight
```

sudo lspci -vnn | grep -A10 VGA

```
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device [103c:3388]
    Flags: bus master, fast devsel, latency 0, IRQ 52
    Memory at c0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 6000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915
--
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Whistler XT [AMD Radeon HD 6700M Series] [1002:6740] (rev ff) (prog-if ff)
    !!! Unknown header type 7f
    Kernel driver in use: radeon
    Kernel modules: fglrx, radeon

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:3388]
    Flags: bus master, fast devsel, latency 0, IRQ 41
    I/O ports at 4000 [size=256]
    Memory at c0404000 (64-bit, prefetchable) [size=4K]
    Memory at c0400000 (64-bit, prefetchable) [size=16K]
```

cat /var/log/syslog | grep -i acpi

```
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-16-generic root=UUID=be44ff56-60d6-40dd-9013-8036b48a58b5 ro quiet splash acpi_backlight=vendor vt.handoff=7
Mar  8 17:27:55 KEVLAP kernel: [    0.000000]  BIOS-e820: 000000009cebf000 - 000000009cfbf000 (ACPI NVS)
Mar  8 17:27:55 KEVLAP kernel: [    0.000000]  BIOS-e820: 000000009cfbf000 - 000000009cfff000 (ACPI data)
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 HPQOEM)
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: XSDT 000000009cffe120 00094 (v01 HPQOEM SLIC-MPC 00000001      01000013)
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: FACP 000000009cffc000 000F4 (v04 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: DSDT 000000009cfec000 0C553 (v01 HP     INSYDE   00000000 MSFT 01000013)
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: FACS 000000009cf6c000 00040
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: ASF! 000000009cffd000 000A5 (v32 HP     INSYDE   00000001 MSFT 01000013)
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: HPET 000000009cffb000 00038 (v01 HP     INSYDE   00000001 MSFT 01000013)
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: APIC 000000009cffa000 0008C (v02 HP     INSYDE   00000001 MSFT 01000013)
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: MCFG 000000009cff9000 0003C (v01 HP     INSYDE   00000001 MSFT 01000013)
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: SLIC 000000009cfeb000 00176 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: SSDT 000000009cfea000 0051F (v01 HP     INSYDE   00001000 MSFT 01000013)
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: BOOT 000000009cfe8000 00028 (v01 HP     INSYDE   00000001 MSFT 01000013)
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: ASPT 000000009cfe5000 00034 (v07 HP     INSYDE   00000001 MSFT 01000013)
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: SSDT 000000009cfe4000 0090C (v01 HP     INSYDE   00003000 INTL 20100806)
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: SSDT 000000009cfe3000 00996 (v01 HP     INSYDE   00003000 INTL 20100806)
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: SSDT 000000009cfe2000 002DA (v01 HP     INSYDE   00003000 INTL 20100806)
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: SSDT 000000009cfe1000 0035D (v01 HP     INSYDE   00003000 INTL 20100806)
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: SSDT 000000009cfdb000 024A1 (v01 HP     INSYDE   00001000 INTL 20100806)
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] enabled)
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] enabled)
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x06] enabled)
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: IRQ0 used by override.
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: IRQ2 used by override.
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: IRQ9 used by override.
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Mar  8 17:27:55 KEVLAP kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-16-generic root=UUID=be44ff56-60d6-40dd-9013-8036b48a58b5 ro quiet splash acpi_backlight=vendor vt.handoff=7
Mar  8 17:27:55 KEVLAP kernel: [    0.006755] ACPI: Core revision 20110413
Mar  8 17:27:55 KEVLAP kernel: [    0.946108] PM: Registering ACPI NVS region at 9cebf000 (1048576 bytes)
Mar  8 17:27:55 KEVLAP kernel: [    0.947778] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Mar  8 17:27:55 KEVLAP kernel: [    0.947780] ACPI: bus type pci registered
Mar  8 17:27:55 KEVLAP kernel: [    0.996792] ACPI: EC: Look up EC in DSDT
Mar  8 17:27:55 KEVLAP kernel: [    0.998612] ACPI: Executed 1 blocks of module-level executable AML code
Mar  8 17:27:55 KEVLAP kernel: [    1.051622] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Mar  8 17:27:55 KEVLAP kernel: [    1.052136] ACPI: SSDT 000000009ce70798 00727 (v01  PmRef  Cpu0Cst 00003001 INTL 20100806)
Mar  8 17:27:55 KEVLAP kernel: [    1.052624] ACPI: Dynamic OEM Table Load:
Mar  8 17:27:55 KEVLAP kernel: [    1.052627] ACPI: SSDT           (null) 00727 (v01  PmRef  Cpu0Cst 00003001 INTL 20100806)
Mar  8 17:27:55 KEVLAP kernel: [    1.083832] ACPI: SSDT 000000009ce71a98 00303 (v01  PmRef    ApIst 00003000 INTL 20100806)
Mar  8 17:27:55 KEVLAP kernel: [    1.084355] ACPI: Dynamic OEM Table Load:
Mar  8 17:27:55 KEVLAP kernel: [    1.084358] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20100806)
Mar  8 17:27:55 KEVLAP kernel: [    1.099651] ACPI: SSDT 000000009ce6fd98 00119 (v01  PmRef    ApCst 00003000 INTL 20100806)
Mar  8 17:27:55 KEVLAP kernel: [    1.100132] ACPI: Dynamic OEM Table Load:
Mar  8 17:27:55 KEVLAP kernel: [    1.100135] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20100806)
Mar  8 17:27:55 KEVLAP kernel: [    1.135163] ACPI: Interpreter enabled
Mar  8 17:27:55 KEVLAP kernel: [    1.135168] ACPI: (supports S0 S3 S4 S5)
Mar  8 17:27:55 KEVLAP kernel: [    1.135194] ACPI: Using IOAPIC for interrupt routing
Mar  8 17:27:55 KEVLAP kernel: [    1.146265] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Mar  8 17:27:55 KEVLAP kernel: [    1.146661] ACPI: ACPI Dock Station Driver: 1 docks/bays found
Mar  8 17:27:55 KEVLAP kernel: [    1.146666] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Mar  8 17:27:55 KEVLAP kernel: [    1.146986] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
Mar  8 17:27:55 KEVLAP kernel: [    1.156325] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Mar  8 17:27:55 KEVLAP kernel: [    1.156461] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Mar  8 17:27:55 KEVLAP kernel: [    1.156493] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Mar  8 17:27:55 KEVLAP kernel: [    1.156527] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
Mar  8 17:27:55 KEVLAP kernel: [    1.156558] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
Mar  8 17:27:55 KEVLAP kernel: [    1.156602] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG0._PRT]
Mar  8 17:27:55 KEVLAP kernel: [    1.156686]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Mar  8 17:27:55 KEVLAP kernel: [    1.156723]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
Mar  8 17:27:55 KEVLAP kernel: [    1.156724] ACPI _OSC control for PCIe not granted, disabling ASPM
Mar  8 17:27:55 KEVLAP kernel: [    1.160221] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
Mar  8 17:27:55 KEVLAP kernel: [    1.160271] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 *3 4 5 6 10 11 12 14 15)
Mar  8 17:27:55 KEVLAP kernel: [    1.160318] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 *4 5 6 10 11 12 14 15)
Mar  8 17:27:55 KEVLAP kernel: [    1.160367] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 *10 11 12 14 15)
Mar  8 17:27:55 KEVLAP kernel: [    1.160413] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
Mar  8 17:27:55 KEVLAP kernel: [    1.160458] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 *5 6 10 11 12 14 15)
Mar  8 17:27:55 KEVLAP kernel: [    1.160503] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *10 11 12 14 15)
Mar  8 17:27:55 KEVLAP kernel: [    1.160547] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 10 *11 12 14 15)
Mar  8 17:27:55 KEVLAP kernel: [    1.161000] PCI: Using ACPI for IRQ routing
Mar  8 17:27:55 KEVLAP kernel: [    1.176091] pnp: PnP ACPI init
Mar  8 17:27:55 KEVLAP kernel: [    1.176103] ACPI: bus type pnp registered
Mar  8 17:27:55 KEVLAP kernel: [    1.176512] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Mar  8 17:27:55 KEVLAP kernel: [    1.176560] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
Mar  8 17:27:55 KEVLAP kernel: [    1.176587] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
Mar  8 17:27:55 KEVLAP kernel: [    1.176682] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
Mar  8 17:27:55 KEVLAP kernel: [    1.176721] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
Mar  8 17:27:55 KEVLAP kernel: [    1.176828] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
Mar  8 17:27:55 KEVLAP kernel: [    1.176861] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
Mar  8 17:27:55 KEVLAP kernel: [    1.176915] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
Mar  8 17:27:55 KEVLAP kernel: [    1.176970] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
Mar  8 17:27:55 KEVLAP kernel: [    1.177025] pnp 00:09: Plug and Play ACPI device, IDs SYN1e47 SYN1e00 SYN0002 PNP0f13 (active)
Mar  8 17:27:55 KEVLAP kernel: [    1.177209] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
Mar  8 17:27:55 KEVLAP kernel: [    1.178255] pnp 00:0b: Plug and Play ACPI device, IDs HPQ0004 (active)
Mar  8 17:27:55 KEVLAP kernel: [    1.178334] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
Mar  8 17:27:55 KEVLAP kernel: [    1.178351] pnp: PnP ACPI: found 13 devices
Mar  8 17:27:55 KEVLAP kernel: [    1.178352] ACPI: ACPI bus type pnp unregistered
Mar  8 17:27:55 KEVLAP kernel: [    1.292278] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Mar  8 17:27:55 KEVLAP kernel: [    1.293015] ACPI: AC Adapter [AC] (on-line)
Mar  8 17:27:55 KEVLAP kernel: [    1.294848] ACPI: Lid Switch [LID]
Mar  8 17:27:55 KEVLAP kernel: [    1.294910] ACPI: Power Button [PWRB]
Mar  8 17:27:55 KEVLAP kernel: [    1.294946] ACPI: Power Button [PWRF]
Mar  8 17:27:55 KEVLAP kernel: [    1.294973] ACPI: acpi_idle yielding to intel_idle
Mar  8 17:27:55 KEVLAP kernel: [    1.309573] ACPI: Thermal Zone [THRM] (56 C)
Mar  8 17:27:55 KEVLAP kernel: [    1.309594] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Mar  8 17:27:55 KEVLAP kernel: [    1.339043] ACPI: Battery Slot [BAT0] (battery present)
Mar  8 17:27:55 KEVLAP kernel: [    9.085155] acpi_call: Module loaded successfully
Mar  8 17:27:55 KEVLAP kernel: [    9.435000] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
Mar  8 17:27:55 KEVLAP kernel: [    9.486010] ACPI: Video Device [PEGP] (multi-head: yes  rom: no  post: no)
Mar  8 17:27:55 KEVLAP kernel: [    9.486655] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Mar  8 17:27:58 KEVLAP kernel: [   13.530581] acpi_call: Calling \_SB.PCI0.PEG0.PEGP._OFF
Mar  8 17:27:58 KEVLAP kernel: [   13.531681] acpi_call: Call successful: 0x0
```
> EDIT: Can you also try these two parameters?
- **acpi_osi=\\"Linux\\"**
- **acpi_osi=\\"Linux\\" acpi_backlight=vendor**

Back in a moment with those.

---

### Post by dansk on 2012-03-08
Back.  Neither of those options changed anything.

---

### Post by Toz on 2012-03-09
I'm not sure about a permanent fix - you might want to create a bug report on launchpad and have one of the devs look at it. Its probably somehow related to the fact that this system has a discrete video card.

As a workaround, you could create an automated script that manages the brightness by directly manipulating the contents of /sys/class/backlight/intel_backlight/brightness (as you noted above) and assigning that script to the brightness function keys. Here is a sample script you could use:

1. Get the upper brightness limit:
```
cat /sys/class/backlight/intel_backlight/max_brightness
```

2. Create the script:
```
sudo gedit /usr/local/bin/br
```

3. Copy/Paste the following code:
```

#!/bin/bash
# /usr/local/bin/br
# wrapper script to change brightness values
# make script executable

# constants - edit as required
UPPER=7
LOWER=0
INCREMENT=1
DECREMENT=1

# current value
CURRENT=`cat /sys/class/backlight/intel_backlight/brightness`
NEW=$CURRENT

case $1 in
	up)
		if [ $(($CURRENT+$INCREMENT)) -le $UPPER ]; then
			NEW=$(($CURRENT+$INCREMENT))
		fi
	;;
	down)
		if [ $(($CURRENT-$DECREMENT)) -ge $LOWER ]; then
			NEW=$(($CURRENT-$DECREMENT))
		fi
	;;
	*)
	;;
esac

# set the new brightness value 
echo $NEW > /sys/class/backlight/intel_backlight/brightness

exit 0
```
...making sure that you change the value of **UPPER** to the result from step 1 and the values of **INCREMENT** and **DECREMENT** as required.

4. Save the file and make it executable:
```
sudo chmod +x /usr/local/bin/br
```

5. Test it out via:
```
br up
```
...and
```
br down
```

If it works, simply assign those commands to the brightness hotkeys.

EDIT: Forgot one thing. Run this command so that you have write access to the brightness file as a regular user:
```
sudo chmod 666 /sys/class/backlight/intel_backlight/brightness
```

You can make this permanent by adding:
```
chmod 666 /sys/class/backlight/intel_backlight/brightness
```
...to **/etc/rc.local** before the *exit 0* command.

---

### Post by dansk on 2012-03-09
Awesome, thank you for your help!  I'll file a bug report, but for the time being that script will do just fine for me.

---

### Post by dansk on 2012-03-09
Sorry, back with another issue: chmod isn't running on startup and changing the permissions for /sys/class/backlight/intel_backlight/brightness.  I have other entries in rc.local that are working fine, so I'm not sure why this isn't.  Thoughts?


```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo '\_SB.PCI0.PEG0.PEGP._OFF' > /proc/acpi/call
chmod 666 /sys/class/backlight/intel_backlight/brightness

exit 0
```

---

### Post by Toz on 2012-03-09
Try:
```
/bin/chmod 777 /sys/class/backlight/intel_backlight/brightness
```
...instead.

---

### Post by dansk on 2012-03-09
No such luck, it's still saying permission denied.

---

### Post by Toz on 2012-03-09
Are you able to change the permissions manually after you've logged in? What does the following return?
```
ls -l /sys/class/backlight/intel_backlight/*
```

---

### Post by dansk on 2012-03-09
> **Toz said:**
> Are you able to change the permissions manually after you've logged in? What does the following return?
```
ls -l /sys/class/backlight/intel_backlight/*
```

```
-r--r--r-- 1 root root 4096 2012-03-09 20:32 /sys/class/backlight/intel_backlight/actual_brightness
-rw-r--r-- 1 root root 4096 2012-03-09 20:47 /sys/class/backlight/intel_backlight/bl_power
-rw-r--r-- 1 root root 4096 2012-03-09 20:32 /sys/class/backlight/intel_backlight/brightness
lrwxrwxrwx 1 root root    0 2012-03-09 20:47 /sys/class/backlight/intel_backlight/device -> ../../card1-LVDS-1
-r--r--r-- 1 root root 4096 2012-03-09 20:32 /sys/class/backlight/intel_backlight/max_brightness
lrwxrwxrwx 1 root root    0 2012-03-09 20:32 /sys/class/backlight/intel_backlight/subsystem -> ../../../../../../../class/backlight
-r--r--r-- 1 root root 4096 2012-03-09 20:47 /sys/class/backlight/intel_backlight/type
-rw-r--r-- 1 root root 4096 2012-03-09 20:32 /sys/class/backlight/intel_backlight/uevent
```

No problems changing the permissions manually:

```
-rw-rw-rw- 1 root root 4096 2012-03-09 20:49 brightness
```

---

### Post by Toz on 2012-03-09
Thats odd. Maybe its a timing issue related to the previous command. Try delaying the command:
```
(sleep 5 && /bin/chmod 777 /sys/class/backlight/intel_backlight/brightness) &
```
...try playing around with the value 5 to see when it takes effect. 

What does that previous command do? Disable the discrete card?

---

### Post by dansk on 2012-03-10
Yeah, you're right, it was conflicting with the previous command for some reason.  (And yes, the other one switches off the discrete card.)  I swapped the order of them and voila, the brightness script is working.  I have no idea why that worked.

---

### Post by r omar on 2012-03-23
Hello all,

Today is my first day with Ubuntu.. Totally newbie.. I face the same problem, except that editing the value in /sys/class/backlight/acpi_video0/brightness did not fix the problem. My laptop is an HP like dansk, but there is a difference with the directory name I have under /sys/class/backlight. In fact, I have 3 directories; acpi_vidoe0, acpi_vidoe1, and acpi_vidoo2. I tried modifying the brightness file in each of them with no luck.

I also tried to modify the booting option in Grub (used acpi_backlight=vendor), but this did not work as well, besides, with acpi_backlight=vendor enabled, all directories under /sys/class/backlight disappeared.

I really appreciate your help. The screen is too bright on my eyes right now. I am not used to this, and I actually started to develop some headache because of it :)

---

### Post by Toz on 2012-03-23
Hello r omar and welcome to the forums.

What is the exact model of the notebook? Post back the result of this command:
```
sudo dmidecode -s system-product-name
```

Also, those backlight directories don't look right. _Without_ the acpi_backlight=vendor parameter, can you post back:
```
ls /sys/class/backlight
```
...(copy/paste from the terminal back here).

And finally, also helpful would be:
```
sudo lspci -vnn | grep -A10 VGA
```

and the contents of **/var/log/dmesg**

---

### Post by r omar on 2012-03-23
Hi Toz,

Thanks for your prompt reply. It gave me a lot of energy to become more patient with Ubuntu :)

The good news is that I fixed the problem... Apparently, it was because of another modification I'd done in the booting options.. I added "nomodeset" this morning because I was getting a black screen during startup, and I was advised by some other thread to put nomodeset to fix this. By removing nomodeset (and removing acpi_backlight as well), I am now back to the state where modifying /sys/class/backlight/intel_backlight/brightness actually changes the brighness. And yes, now I have an intel_backlight directory like the other fellows.

And for the record, my laptop is "HP Pavilion g6 Notebook PC", maybe this'll help other people in case they own the same model... Thanks to the dmidecode utility I learnt today from Toz.

Thanks again Toz. I appreciate your help.

---

