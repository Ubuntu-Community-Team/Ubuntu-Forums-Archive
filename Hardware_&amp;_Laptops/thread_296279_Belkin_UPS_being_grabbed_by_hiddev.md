---
title: "Belkin UPS being grabbed by hiddev?"
date: 2006-11-09
forum: Hardware &amp; Laptops
---

### Post by DrBob on 2006-11-09
I've been fiddling around trying to get NUT to work with my new Belkin F6H350ukUNV-DB UPS (connected via USB) on Edgy, and I've almost got there. However, when I run "sudo /lib/nut/newhidups -a belkin -u nut -DDDDD", I get the following, and it doesn't match my UPS:
```
Network UPS Tools: New USB/HID UPS driver 0.28 (2.0.4)

debug level is '5'
Checking device (0001/0000) (001/008)
- VendorID: 0001
- ProductID: 0000
- Manufacturer: unknown
- Product: unknown
- Serial Number: unknown
- Bus: 001
Trying to match device
Device does not match - skipping
Checking device (046D/0850) (001/004)
- VendorID: 046d
- ProductID: 0850
- Manufacturer: unknown
- Product: unknown
- Serial Number: unknown
- Bus: 001
Trying to match device
Device does not match - skipping
Checking device (1038/0100) (001/006)
- VendorID: 1038
- ProductID: 0100
- Manufacturer: unknown
- Product: unknown
- Serial Number: unknown
- Bus: 001
Trying to match device
Device does not match - skipping
Checking device (03EB/3301) (001/005)
- VendorID: 03eb
- ProductID: 3301
- Manufacturer: unknown
- Product: unknown
- Serial Number: unknown
- Bus: 001
Trying to match device
Device does not match - skipping
Checking device (046D/C041) (001/003)
- VendorID: 046d
- ProductID: c041
- Manufacturer: unknown
- Product: unknown
- Serial Number: unknown
- Bus: 001
Trying to match device
Device does not match - skipping
Checking device (0000/0000) (001/001)
- VendorID: 0000
- ProductID: 0000
- Manufacturer: unknown
- Product: unknown
- Serial Number: unknown
- Bus: 001
Trying to match device
Device does not match - skipping
Checking device (0000/0000) (002/001)
- VendorID: 0000
- ProductID: 0000
- Manufacturer: unknown
- Product: unknown
- Serial Number: unknown
- Bus: 002
Trying to match device
Device does not match - skipping
No appropriate HID device found
No matching USB/HID UPS found
```

It should be matching the first device listed. I've Googled around, and found out that perhaps this isn't working because that device has been grabbed by hiddev when it was first detected (and thus NUT can't get hold of it), but since I only read about that with reference to BSD, and the solution was to recompile the kernel without hiddev support, I thought it wise to ask here first. (I'm normally find with recompiling my kernel, but I don't want to do it on Ubuntu because then I'm forfeiting the advantages of packages.)

Some information:

Output of "lsusb" (UPS is the first one):
```
Bus 001 Device 008: ID 0001:0000 Fry's Electronics 
Bus 001 Device 004: ID 046d:0850 Logitech, Inc. QuickCam Web
Bus 001 Device 006: ID 1038:0100 Ideazon, Inc. Zboard
Bus 001 Device 005: ID 03eb:3301 Atmel Corp. at43301 4-port Hub
Bus 001 Device 003: ID 046d:c041 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
```

Output from "dmesg" after unplugging and re-connecting the UPS' USB connection:
```
[18053.300534] usb 1-1: USB disconnect, address 8
[18057.131910] usb 1-1: new low speed USB device using ohci_hcd and address 9
[18067.335173] usb 1-1: configuration #1 chosen from 1 choice
[18067.368130] hiddev96: USB HID v1.00 Device [MEC MEC0002] on usb-0000:00:02.0-1
```

/etc/nut/ups.conf:
```
[belkin]
driver=newhidups
port=auto
desc="Belkin Superior Series 350VA"
```

/etc/nut/upsd.conf:
```
ACL KWA-PHILIP-LINUX 192.168.0.2/32
ACL all 0.0.0.0/0
ACCEPT localhost KWA-PHILIP-LINUX
REJECT all
```

/etc/nut/upsd.users:
```
[philip]
password=foo
allowfrom=KWA-PHILIP-LINUX
instcmds=all
actions=set
upsmon master
```

/etc/nut/upsmon.conf:
```
MONITOR belkin@KWA-PHILIP-LINUX 1 philip foo master
RUN_AS_USER nut
POWERDOWNFLAG /var/tmp/upsmon_powerdown
```

I hope there's enough information there, and thanks in advance for any help anybody can provide! :)

---

### Post by tejster24 on 2006-11-10
I don't have one of these, but try using **modprobe -r** to unload the hiddev driver.

If that doesn't work, provide output from **lsmod**.

Also, try a **lsusb -v** - it provides a lot more info on specific devices.

---

### Post by DrBob on 2006-11-10
"modprobe -l | grep hiddev" tells me I have no hiddev driver loaded, and "modprobe -l | grep hid" gives me a list of drivers which aren't being used by the UPS: just mouse and keyboard drivers.

Output from "modprobe -l | grep hid":
```
/lib/modules/2.6.17-10-generic/kernel/net/bluetooth/hidp/hidp.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/usb/misc/phidgetservo.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/usb/misc/phidgetkit.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/usb/input/usbhid.ko
```

Output from "lsmod":
```
Module                  Size  Used by
isofs                  43236  0 
udf                    97288  0 
binfmt_misc            16012  1 
cpufreq_userspace       6560  0 
cpufreq_stats           9312  0 
freq_table              7104  1 cpufreq_stats
cpufreq_powersave       3456  0 
cpufreq_ondemand       10928  0 
cpufreq_conservative    11272  0 
video                  22920  0 
tc1100_wmi             10632  0 
sbs                    20928  0 
sony_acpi               7704  0 
pcc_acpi               19968  0 
i2c_ec                  7808  1 sbs
hotkey                 14536  0 
dev_acpi               17540  0 
button                  9888  0 
battery                14088  0 
container               6656  0 
ac                      8328  0 
asus_acpi              21924  0 
ntfs                  109128  1 
nls_iso8859_1           6912  1 
nls_cp437               8704  2 
vfat                   17920  1 
fat                    65456  1 vfat
ext2                   83728  1 
md_mod                 96156  0 
sr_mod                 21924  0 
sbp2                   29448  0 
lp                     16584  0 
snd_usb_audio         100512  0 
snd_usb_lib            23552  1 snd_usb_audio
ipv6                  334432  19 
quickcam               82984  0 
tsdev                  11136  0 
videodev               14208  1 quickcam
snd_hwdep              14088  1 snd_usb_audio
sg                     44584  0 
snd_intel8x0           42024  0 
snd_ac97_codec        127064  1 snd_intel8x0
snd_ac97_bus            4352  1 snd_ac97_codec
snd_pcm_oss            57344  0 
snd_pcm               108168  4 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          22784  1 snd_pcm_oss
snd_seq_dummy           6020  0 
snd_seq_oss            45824  0 
snd_seq_midi           12160  0 
snd_rawmidi            34432  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event     11520  2 snd_seq_oss,snd_seq_midi
nvidia               5444468  12 
snd_seq                77344  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
irtty_sir              12032  0 
evdev                  14592  2 
sir_dev                21896  1 irtty_sir
snd_timer              31112  2 snd_pcm,snd_seq
snd_seq_device         12180  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                51088  0 
irda                  253548  2 irtty_sir,sir_dev
i2c_nforce2             9984  0 
sk98lin               212572  0 
pcspkr                  5248  0 
serio_raw              10244  0 
floppy                 76648  0 
crc_ccitt               3712  1 irda
parport_pc             43560  1 
parport                49932  2 lp,parport_pc
rt2500                229096  0 
sky2                   50436  0 
i2c_core               29312  3 i2c_ec,nvidia,i2c_nforce2
snd                    79016  12 snd_usb_audio,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14112  1 snd
snd_page_alloc         13200  2 snd_intel8x0,snd_pcm
shpchp                 49068  0 
pci_hotplug            38912  1 shpchp
usbhid                 51360  0 
ext3                  164624  1 
jbd                    74024  1 ext3
forcedeth              37644  0 
ohci1394               40776  0 
ieee1394              387704  2 sbp2,ohci1394
ehci_hcd               40456  0 
ohci_hcd               25988  0 
usbcore               167840  7 snd_usb_audio,snd_usb_lib,quickcam,usbhid,ehci_hcd,ohci_hcd
ide_generic             2944  0 
ide_cd                 39584  0 
cdrom                  43816  2 sr_mod,ide_cd
generic                 7428  0 
amd74xx                17712  0 [permanent]
sd_mod                 25728  6 
sata_nv                13572  4 
libata                 88984  1 sata_nv
scsi_mod              181424  5 sr_mod,sbp2,sg,sd_mod,libata
thermal                19472  0 
processor              38280  1 thermal
fan                     7432  0 
vesafb                 11048  0 
capability              7304  0 
commoncap              10752  1 capability
vga16fb                16656  1 
cfbcopyarea             5376  2 vesafb,vga16fb
vgastate               10368  1 vga16fb
cfbimgblt               4352  2 vesafb,vga16fb
cfbfillrect             6272  2 vesafb,vga16fb
fbcon                  45824  72 
tileblit                4736  1 fbcon
font                   10240  1 fbcon
bitblit                 8064  1 fbcon
softcursor              3968  1 bitblit
```

I've given the output of "sudo lsusb -v" as an attachment, since it's very long. (So long I had to compress it before the board allowed me to attach it, even.)

---

### Post by fignew on 2006-11-12
I just got a new belkin UPS, and have been unable to get nut fully working... However, I have noticed one thing.

when you cat /dev/bus/usb/.usbfs/devices

You'll get alot of text, however with a sharp eye you will spot something similar to this:  

```
T:  Bus=04 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=050d ProdID=0551 Rev= 0.01
S:  Manufacturer=Belkin
S:  Product=UPS
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr= 20mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=248ms

```

You will notice that "Vendor=050d ProdID=0551" is present. Let's look at the output of /lib/nut/newhidups -a belkin -u nut -DDDD

under VendorID and ProductID the value 050d or 0551 is nowhere to be seen!

Could this mean that nut is not looking in the right place?

my 2 cents... :-k

---

### Post by DrBob on 2006-11-13
Output of "cat /dev/bus/usb/.usbfs/devices":
```
T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0001 ProdID=0000 Rev= 1.00
S:  Manufacturer=MEC
S:  Product=MEC0002
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
```

As you can see, the vendor and product IDs are exactly the same as they are everywhere else in my system (and quite worryingly low). However, I've tested the UPS under Windows XP with the provided software and it works fine, so I can't argue.

I think the answer has to be with stopping hiddev (usbhid driver) getting hold of the UPS. Is there some kind of a list of "banned" devices for it?

---

### Post by fignew on 2006-11-13
I fixed mine by adding
```
# Belkin
SYSFS{idVendor}=="050d", SYSFS{idProduct}=="0551", RUN+="/etc/hotplug/usb/libhidups"
```
to /etc/udev/rules.d/025_nut-usbups.rules

Now I'm trying to get upsd to work with knutclient

---

### Post by DrBob on 2006-11-13
I've already done that, and it did no good. I've just moved the rule up in the file, and will try again. If that doesn't work, I'll add some debug statements to /etc/hotplug/usb/libhidups, and see if it's being passed the right device (or even being called).

---

### Post by fignew on 2006-11-13
Under the udev rules, instead of defining the vendor and and product ID (They are essentially blank for you), I think you're going to have to define "Fry's Electronics" under a different identifier (you're going to have to look that up.)

Also What is MEC?

Additionally when reading the NUT docs on the NUT website, I do not remember seeing your UPS listed under the newhidups driver. Could be mistaken though.

---

### Post by DrBob on 2006-11-13
I'll look into changing my udev rule, thanks. :)

A little Wikipediaing leads me to think that MEC is the [Mitsubishi Electric Corporation]("http://en.wikipedia.org/wiki/Mitsubishi_Electric_Corporation"), which apparently manufacture UPSs, and I suppose manufacture them for Belkin.

As far as I understand, the newhidups driver will work with any UPS which identifies itself as such, and I know at least some Belkin UPSs are supported (and they're unlikely to have a radically different protocol between series). I'm not sure, though. :(

---

### Post by DrBob on 2006-11-18
Here's my /etc/udev/nut-usbups.rules file, and it still isn't working. :(

```
# udev rules for the NUT USB drivers

ACTION!="add", GOTO="nut-usbups_rules_end"

# Belkin Superior Series
SYSFS{manufacturer}=="MEC", SYSFS{product}=="MEC0002", RUN+="/etc/hotplug/usb/libhidups"
SUBSYSTEM!="usb_device", GOTO="nut-usbups_rules_end"
# MGE UPS SYSTEMS - usbhid-ups
SYSFS{idVendor}=="0463", SYSFS{idProduct}=="ffff", RUN+="/etc/hotplug/usb/libhidups"
SYSFS{idVendor}=="0463", SYSFS{idProduct}=="0001", RUN+="/etc/hotplug/usb/libhidups"
# APC - usbhid-ups
SYSFS{idVendor}=="051d", SYSFS{idProduct}=="0002", RUN+="/etc/hotplug/usb/libhidups"
# Powerware - bcmxcp_usb
SYSFS{idVendor}=="0592", SYSFS{idProduct}=="0002", RUN+="/etc/hotplug/usb/libhidups"
# Tripp Lite - tripplite_usb
SYSFS{idVendor}=="09ae", SYSFS{idProduct}=="0001", RUN+="/etc/hotplug/usb/libhidups"
LABEL="nut-usbups_rules_end"

```

/etc/hotplug/usb/libhid.usermap:

```
# This file is installed by the Network UPS Tools package.
#
# Sample entry (replace 0xVVVV and 0xPPPP with vendor ID and product ID respectively) :
# libhidups      0x0003      0xVVVV   0xPPPP    0x0000       0x0000       0x00         0x00            0x00            0x00            0x00               0x00               0x00000000
#
# usb module         match_flags idVendor idProduct bcdDevice_lo bcdDevice_hi bDeviceClass bDeviceSubClass bDeviceProtocol bInterfaceClass bInterfaceSubClass bInterfaceProtocol driver_info
#
# MGE UPS SYSTEMS units
libhidups      0x0003      0x0463   0xffff    0x0000       0x0000       0x00         0x00            0x00            0x00            0x00               0x00               0x00000000
libhidups      0x0003      0x0463   0x0001    0x0000       0x0000       0x00         0x00            0x00            0x00            0x00               0x00               0x00000000
# APC units
libhidups      0x0003      0x051d   0x0002    0x0000       0x0000       0x00         0x00            0x00            0x00            0x00               0x00               0x00000000
# Powerware USB 
libhidups      0x0003      0x0592   0x0002    0x0000       0x0000       0x00         0x00            0x00            0x00            0x00               0x00               0x00000000
# Tripp Lite
libhidups      0x0003      0x09ae   0x0001    0x0000       0x0000       0x00         0x00            0x00            0x00            0x00               0x00               0x00000000
# Belkin Superior Series
libhidups      0x0003      0x0001   0x0000    0x0000       0x0000       0x00         0x00            0x00            0x00            0x00               0x00               0x00000000

```

---

