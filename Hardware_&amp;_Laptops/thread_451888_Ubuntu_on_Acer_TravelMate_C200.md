---
title: "Ubuntu on Acer TravelMate C200"
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by gigahz on 2007-05-22
I'll write some lines on how I fine-tuned my install of Feisty on the Acer TravelMate C200 (no thumb scanner)

I describe using Gnome / metacity.

got ubuntu and 
**Ethernet and wireless:**
worked out of the box. The WLAN led isn't turning on, but the network i/f does.

There is a radio kill switch in /sys/class/net/eth1/acpi/power/state or something. Must be set to 1 (or press the wireless_radio button on the front) for wireless radio to work. A bit confusing that led there.

You can check the state with iwconfig, look for "radio off" something. dmesg will complain about kill switch if it is unset... Another obvious indicator is that the nm-applet list of available networks is empty (if you use networkmanager).

**Graphics acceleration:**
-nvidia Geforce G0 6200 TurboCache
Got it working by 
-(in Edgy): downloading and running automatix, and selecting/installing Nvidia driver. Booted and: Bob's your uncle.
-(in Feisty): System | Administration | Restricted drivers and selcting the nvidia restricted.

beryl worked, but I took it out to increase stability (also it seems the graphics chip gets too hot; charging it eventually it gets too hot and freezes the system for a while before the power is suddenly shut. I think this is a hardware error. In Windows it's a lot worse and it gets QUITE hot unless I tune down the settings.

**Rotating display:**
1) Got xrandr working by putting in ```
Option "RandRRotation" "on" 
```in the "Device" section of /etc/X11/xorg.conf. Soo cool and soo fast!

2a) Swiwel-display-key:
There's a swiwel key on the top of the tablet; the scancode is 0x6b.
I added this script to the System | Preferences | Session (as a new program)
```
setkeycodes 0x6b 219
xmodmap -e "keycode 219 = XF86RotateWindows"
killall metacity
```

(I have to kill metacity to make it run, EVEN IF I RELLY RUN THIS SCRIPT BEFORE METACITY in the session file. I tried adding the xmodmap to /usr/share/hotkey-setup/acer.hk, but I never got it working.)

2b)open gconf-editor and set
/apps/metacity/global_keybindings/run_command_1 to XF86RotateWindows
/apps/metacity/command1 to point to this script:

```
# swiweldisplay.sh
# Quick xrandr "swiwel display" hack
# Arno Teigseth, 2007

RANDRSTATE=`xrandr -q |grep rotation |sed s/Current\ rotation\ -\ //`

if [ "$RANDRSTATE" == "normal" ]; then
   xrandr -o right;
   xsetwacom set stylus rotate CW
   exit;
fi

if [ "$RANDRSTATE" == "right" ]; then
   xrandr -o inverted;
   xsetwacom set stylus rotate HALF
   exit;
fi

if [ "$RANDRSTATE"  == "inverted" ]; then
   xrandr -o left;
   xsetwacom set stylus rotate CCW
   exit;
fi

if [ "$RANDRSTATE" == "left" ]; then
   xrandr -o normal;
   xsetwacom set stylus rotate NONE
   exit;
fi
```

Pressing the swiwel key now rotates the screen around. This script will rotate a full 360 degrees 90 at a time, but you can edit it as you wish.

**Tuning power:**
sudo chmod +s /usr/bin/cpufreq-selector
and then adding cpu speed selector to the panel will make it possible to choose cpu speeds and governors, hopefully saving on the battery.

**Stylus: **
Got working the stylus as a mouse:
-changing /etc/X11/xorg.conf 3 places /dev/wacom to /dev/input/event
-the line Load "wacom" in xorg.conf [Module] section

now installing and running gromit is funnier.

Right-click by pressing the button on the stylus:
-installed the package wacom-tools
-added this script to the System | Preferences | Session (as a new program)
```
xsetwacom set stylus TPCButton off
xsetwacom set stylus Button1 1

# This is tap with the pen on screen. 3 is right-click, 2 is middle, 1 is normal click
xsetwacom set stylus Button2 1

# This is hover-button on the pen. 3 is right-click, 2 is middle, 1 is normal click
xsetwacom set stylus Button3 3
```

If you do not want hover-button functionality but rather like in Windows having to press the stylus button AND tap to right-click, set TPCButton to on.

**USB works**. All ports are independent root hubs :)

**Bluetooth:**
The device and the led works. The led seems to be hardwired to the device power state.

*External bluetooth soundcard:*
(Bluetooth must be on)
```
got my Jabra bluetooth headset working with for example skype and ekiga with:
installing package btsco
modprobe snd_bt_sco
hcitool scan
btsco -v <address of the device found in scan above>

``` The device showed up as /dev/dsp1, /dev/mixer1, etc. Alsa hw=1.0

try the headset with mplayer -ao alsa:device=hw=1.0 Examples/ubuntu\ Sax.ogg 

In skype etc I can use it! Scatters a bit but who cares. Try that one in windoze...

*Send/recieve with bluetooth:*
install the "bluetooth" package
sudo hciconfig hci0 inqmode 0 (don't know if it is necessary but anyway works)
'gnome-bluetooth-send' now pops up with found bluetooth devices :)

an improvement: 
gnome-bluetooth-send -d <bluetooth address> will send to the specified address WITHOUT searching.

**DVD-burner:**
Works in brasero.

**Modem:**
don't know. not even where it is connected. Might be a winmodem.

**USB-serial port:** (external equipment)
worked as /dev/ttyUSB0 etc out-of the box. 

serial support in wine:

sudo modprobe usbserial
sudo ln -b /dev/ttyUSB0 /dev/ttyS0

[[http://www.canhesaythat.com/wiki/index.php/HOWTO_Ubuntu_On_Dell_700m]](http://www.canhesaythat.com/wiki/index.php/HOWTO_Ubuntu_On_Dell_700m])


most works now, some in progress.

TO DO:
-WLAN LED
-Dlink USB-ISDN adapter
-Test/setup modem

---

### Post by MadeR on 2007-07-25
I am trying to identify the modem... nothing in lsusb or lspci.
I think it is a conexant hsf, because in windows, there is a CNXT string identifying it.

update: i tried this script: [http://linmodems.technion.ac.il/packages/scanModem.gz](http://linmodems.technion.ac.il/packages/scanModem.gz)
it tells me that 

```
PCIDEV=8086:2668
CLASS="Class 0403: 8086:2668"
NAME="Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW "
Vendor=8086
Device=2668
SUBSYS=1025:007b
SUBNAME=" Acer Incorporated [ALI] Unknown device 007b"
SUBven=1025
IRQ=16
Test="./scanModem test 8086:2668 1025:007b"
SOFT=8086:2668
SLMODEMD_DEVICE=modem:1
PORT="modem:1"
Driver=snd-intel8x0m
DRIVER_=snd_intel8x0m
KDRIVER=SND_NTEL8X0M
MPLACE=
ASOUND=
CODECp=
CODEC=
COD=
HDA=1
TST=

```


device 1025:007b is not present in modem table on the linuxant.com site.
1025 is used both for HCF and HSF modems.

```

CPU=i686,  Ubuntu 7.04 
Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007
 scanModem update of:  2007_July_16
The modem symbolic link is /dev/modem -> ttySL0

ALSAversion 1.0.13
USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1b.0	8086:2668	1025:007b	Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW 

 Modem interrupt assignment and sharing: 
 16:     875282   IO-APIC-fasteoi   uhci_hcd:usb4, ohci1394, eth0, HDA Intel, nvidia

 --- Bootup diagnostics for card in PCI slot 00:1b.0 ----
[   22.248000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   22.248000] PCI: Setting latency timer of device 0000:00:1b.0 to 64

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

8086:2668 is a High Definition Audio card, possibly hosting a soft modem.

 	A modem was not detected among the PCI devices:
------------------------------------------------
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 6200 TurboCache (rev a1)
06:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)
06:06.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
06:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
------------------------------------------------
 with USB and bridge devices not displayed.
 Please provide any independent information available on your modem.
```

---

### Post by MadeR on 2007-07-26
update
modem is conexant hsf as stated in [http://www.linuxant.com/drivers/hsf/index.php](http://www.linuxant.com/drivers/hsf/index.php) 

HDA (High Definition Audio) Modems
 only under 2.6.16 or newer kernels 
** HDA VENDOR ID 14F12BFA** HDA VENDOR ID 14F12C06

I tried to install 2.6.20-16-generic  hsfmodem_7.60.00.09full_k2.6.20_16_generic_ubuntu_i386.deb.zip   
but module crashes:

```

[   23.048000] cnxthsf_NVM_Open: cannot create instance 0-HDA-14f12bfa:1025007b-1: err=256 will retry later..
[   23.072000] BUG: unable to handle kernel paging request at virtual address ffee7000
[   23.072000]  printing eip:
[   23.072000] f8ec15a0
[   23.072000] *pde = 00004067
[   23.072000] Oops: 0000 [#1]
[   23.072000] SMP
[   23.072000] Modules linked in: hsfhda(F) hsfserial hsfengine(P) hsfosspec pcmcia irda snd_hda_intel snd_hda_codec parport_pc parport snd_pc
m_oss snd_mixer_oss crc_ccitt snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi yenta_socket rsrc_nonstatic snd_seq_midi_event snd_se
q snd_timer snd_seq_device pcmcia_core ipw2200 tifm_7xx1 tifm_core nvidia(P) ieee80211 ieee80211_crypt iTCO_wdt snd soundcore serio_raw psmous
e i2c_core iTCO_vendor_support snd_page_alloc af_packet intel_agp agpgart shpchp pci_hotplug evdev tsdev ext3 jbd mbcache sg usbhid hid sr_mod
 cdrom sd_mod generic ata_generic ohci1394 ieee1394 tg3 ata_piix libata scsi_mod ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tilebli
t font bitblit softcursor vesafb capability commoncap
[   23.072000] CPU:    0
[   23.072000] EIP:    0060:[<f8ec15a0>]    Tainted: PF     VLI
[   23.072000] EFLAGS: 00010282   (2.6.20-16-generic #2)
[   23.072000] EIP is at hsfengine744_+0x2060/0x271c [hsfengine]
[   23.072000] eax: 00000000   ebx: c0000000   ecx: 9c5edf57   edx: 3f447000
[   23.072000] esi: ffee7000   edi: f1f3f9f4   ebp: c1b53c24   esp: c1b53bdc
[   23.072000] ds: 007b   es: 007b   ss: 0068
[   23.072000] Process modprobe (pid: 3368, ti=c1b52000 task=dfb7b560 task.ti=c1b52000)
[   23.072000] Stack: 00000000 00000000 c0000000 00000000 00000000 00000000 00240000 00000000
[   23.072000]        00000000 00000000 00000000 000f69b0 deadaffe 6e55a180 f724d440 f7e5bb80
[   23.072000]        f7e49108 f7e5bbac c1b53c54 f8eba8c5 f725a8c0 00000001 f7e5bb84 f7e5bbac
[   23.072000] Call Trace:
[   23.072000]  [<f8eba8c5>] hsfengine1550_+0x85/0xb0 [hsfengine]
[   23.072000]  [<f8eba4dd>] hsfengine519_+0x1d/0x40 [hsfengine]
[   23.072000]  [<f8e9446b>] cnxthsf_ComCtrl_Open+0x6b/0x1b0 [hsfengine]
[   23.072000]  [<f8bec529>] cnxthsf_cnxt_serial_add+0x239/0x4e0 [hsfserial]
[   23.072000]  [<c02ec74d>] __sched_text_start+0x2fd/0xa90
[   23.072000]  [<c01f1094>] vsnprintf+0x2f4/0x5f0
[   23.072000]  [<f8beb8b0>] cnxt_event_handler+0x0/0x320 [hsfserial]
[   23.072000]  [<f8d1825e>] cnxthwhda_probe+0x12e/0x1a0 [hsfhda]
[   23.072000]  [<f8d18130>] cnxthwhda_probe+0x0/0x1a0 [hsfhda]
[   23.072000]  [<f8cb8624>] conexant_init+0x64/0xe0 [snd_hda_codec]
[   23.072000]  [<f8cacc8f>] snd_hda_build_controls+0x6f/0x90 [snd_hda_codec]
[   23.072000]  [<f8b9f64a>] azx_probe+0x6ba/0x8c0 [snd_hda_intel]
[   23.072000]  [<c01b8015>] sysfs_dirent_exist+0x45/0x70
[   23.072000]  [<f8b9e6d0>] azx_send_cmd+0x0/0x120 [snd_hda_intel]
[   23.072000]  [<f8b9e7f0>] azx_get_response+0x0/0x170 [snd_hda_intel]
[   23.072000]  [<f8b9ed50>] azx_get_wallclock+0x0/0x10 [snd_hda_intel]
[   23.072000]  [<f8b9ed60>] azx_get_linkpos+0x0/0x10 [snd_hda_intel]
[   23.072000]  [<c01fb963>] pci_match_device+0x13/0xc0
[   23.072000]  [<f8b9ef90>] azx_probe+0x0/0x8c0 [snd_hda_intel]
[   23.072000]  [<c01fba86>] pci_device_probe+0x56/0x80
[   23.072000]  [<c0257aa6>] really_probe+0x66/0x190
[   23.072000]  [<c0257c19>] driver_probe_device+0x49/0xc0
[   23.072000]  [<c0257dee>] __driver_attach+0x9e/0xa0
[   23.072000]  [<c0256f7b>] bus_for_each_dev+0x3b/0x60
[   23.072000]  [<c0257944>] driver_attach+0x24/0x30
[   23.072000]  [<c0257d50>] __driver_attach+0x0/0xa0
[   23.072000]  [<c025730b>] bus_add_driver+0x7b/0x1a0
[   23.072000]  [<c01fbc54>] __pci_register_driver+0x74/0xc0
[   23.072000]  [<c014422d>] sys_init_module+0x15d/0x1ba0
[   23.072000]  [<c0107a5d>] sys_mmap2+0xcd/0xd0
[   23.072000]  [<c01031f0>] sysenter_past_esp+0x69/0xa9
[   23.072000]  =======================
[   23.072000] Code: 50 bc 48 31 c0 c7 c2 41 d2 ae 0f c7 c2 01 97 9e 4b 89 e2 89 da 31 c2 81 c7 b4 f9 63 d0 c7 c2 f4 f5 44 3f 21 f2 81 cf 50 9
9 b3 f1 <8a> 06 89 f7 89 c1 ff c1 89 c1 29 c1 c7 c2 f1 fb ad 40 c7 c7 db
[   23.072000] EIP: [<f8ec15a0>] hsfengine744_+0x2060/0x271c [hsfengine] SS:ESP 0068:c1b53bdc

```

what can I do?

I think this topic I found in the Linuxant FAQ about HSF modem maybe the reason:

I have an ACPI-based machine and the driver is crashing or not loading. 
 It might be necessary to recompile a generic kernel from ftp.kernel.org with the latest ACPI (and perhaps also KACPID kernel lost interrupt) patches from [http://sf.net/projects/acpi/](http://sf.net/projects/acpi/) 
Alternatively you could try the 2.6 development kernel, which has better ACPI support. However we cannot guarantee that the drivers will work with development kernels since they are constantly evolving.

---

### Post by MadeR on 2008-03-23
Update:

to make the wifi work, add in /etc/modprobe.d/options the line
```
options ipw2200 led=1
```

---

