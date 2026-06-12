---
title: "ThinkPad wireless driver"
date: 2011-05-30
forum: Hardware
---

### Post by h.r. on 2011-05-30
Hey I just got a new ThinkPad Edge 15, and I'm trying to make the wireless work. I'm running Ubuntu 11.04. I'm not experienced with Linux. The hardware is definitely working, everything is fine in Windows.

I tried to use ndiswrapper, and I installed the windows driver successfully, but it doesn't recognise my card. ndiswrapper -l returns:

net8192ce : driver installed
	device (10EC:8176) present (alternate driver: rtl8192ce)

But iwconfig returns:

lo        no wireless extensions.
eth1      no wireless extensions

I tried installing the Realtek rtl8192ce linux driver. I followed the instructions in the readme, which just said to sudo make install and restart my system, and then my wireless manager should find the card, but to no avail. I didn't get any error messages, but the behavior of my wireless manager (the default gnome one) as well as the output of iwconfig, remains unchanged.

Any advice? Thanks.

---

### Post by jonathon6017 on 2011-05-30
> **h.r. said:**
> Hey I just got a new ThinkPad Edge 15, and I'm trying to make the wireless work. I'm running Ubuntu 11.04. I'm not experienced with Linux. The hardware is definitely working, everything is fine in Windows.

I tried to use ndiswrapper, and I installed the windows driver successfully, but it doesn't recognise my card. ndiswrapper -l returns:

net8192ce : driver installed
	device (10EC:8176) present (alternate driver: rtl8192ce)

But iwconfig returns:

lo        no wireless extensions.
eth1      no wireless extensions

I tried installing the Realtek rtl8192ce linux driver. I followed the instructions in the readme, which just said to sudo make install and restart my system, and then my wireless manager should find the card, but to no avail. I didn't get any error messages, but the behavior of my wireless manager (the default gnome one) as well as the output of iwconfig, remains unchanged.

Any advice? Thanks.

Are you sure that it is the right driver? I'm asking because I have almost the exact same card  and it works out of the box with 11.04 (previous versions I had to make the driver but it did work).

You can check this by typing
```
lspci
```
You are looking for something that says "Network controller:"

For example mine says "02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01"

---

### Post by h.r. on 2011-05-31
Here's what lspci told me:

08:00.0 Network controller: Realtek Semiconductor Co., Ltd. **RTL8188CE** 802.11b/g/n WiFi Adapter (rev 01)

The driver the Realtek website gives me for the 8188CE is for both the 8192CE/8188CE, according to the release notes.

---

### Post by h.r. on 2011-05-31
Ok so I realized what part of my problem is, I still had ndiswrapper installed. I had uninstalled the windows drivers from it, but apparently that wasn't enough.

Once I got rid of ndiswrapper, wlan0 showed up in iwconfig. The gnome network manager showed the "Enable Wireless" option for the first time, but clicking it did nothing. I tried to start it with ifconfig wlan0 up, but it wouldn't work due to a block on the rf kill switch. Here was the output of "rfkill list"

```

0: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

```

"rfkill unblock 0" did nothing, but "rfkill unblock 1", "rfkill unblock wlan", and "rfkill unblock all" each worked. I removed the soft block on phy0, and then tried to pull wlan0 up again, but it crashed the system. I tried it three times. The first time the screen just went black, the second time it froze, and the third time it showed me some sort of error log dump and then froze.

Am I doing something wrong, or is this just a bad driver? Should I keep trying? It feels strange to intentionally crash my system.

Going back to trying ndiswrapper, here's where I'm at:
I removed the realtek driver completely by its own make uninstall, and then manually removed all the relevant modules with rmmod. I reinstalled ndiswrapper, and installed the windows driver back. ndiswrapper -l gives me

```
net8192ce : driver installed
	device (10EC:8176) present
```

But iwconfig gives me nothing.

---

### Post by Yellow Pasque on 2011-05-31
Let's try the latest driver directly from the kernel staging tree (this is generally a better idea than relying on chipset manufacturers' linux support pages):
```
cd ~
wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2011-05-30.tar.bz2
tar -xjf compat-wireless-2011-05-30.tar.bz2
cd compat-wireless-2011-05-30
./scripts/driver-select rtlwifi
sudo make install
```
Let us know if there are build errors.
EDIT: If no build errors and module installs/loads properly, then we'll have to check dmesg to see why you're not getting an interface.

---

### Post by jonathon6017 on 2011-05-31
> **h.r. said:**
> Ok so I realized what part of my problem is, I still had ndiswrapper installed. I had uninstalled the windows drivers from it, but apparently that wasn't enough.

Once I got rid of ndiswrapper, wlan0 showed up in iwconfig. The gnome network manager showed the "Enable Wireless" option for the first time, but clicking it did nothing. I tried to start it with ifconfig wlan0 up, but it wouldn't work due to a block on the rf kill switch. Here was the output of "rfkill list"

```

0: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

```

"rfkill unblock 0" did nothing, but "rfkill unblock 1", "rfkill unblock wlan", and "rfkill unblock all" each worked. I removed the soft block on phy0, and then tried to pull wlan0 up again, but it crashed the system. I tried it three times. The first time the screen just went black, the second time it froze, and the third time it showed me some sort of error log dump and then froze.

Am I doing something wrong, or is this just a bad driver? Should I keep trying? It feels strange to intentionally crash my system.

Going back to trying ndiswrapper, here's where I'm at:
I removed the realtek driver completely by its own make uninstall, and then manually removed all the relevant modules with rmmod. I reinstalled ndiswrapper, and installed the windows driver back. ndiswrapper -l gives me

```
net8192ce : driver installed
	device (10EC:8176) present
```

But iwconfig gives me nothing.

I can't believe you are having so many issues before 11.04 (when my wireless didn't work out of the box) all I had to do was make the driver and then install it. If the compatwireless drivers don't work I would suggest doing a fresh install and using the 8188ce linux Realtek drivers.

---

### Post by h.r. on 2011-05-31
Temüjin, I ran the commands you gave me. It didn't have any errors, but at the end it told me:

```
Now run:

sudo make unload to unload all: wireless, bluetooth and ethernet modules
sudo make wlunload to unload wireless modules
sudo make btunload to unload bluetooth modules

Run sudo modprobe driver-name to load your desired driver.
If unsure reboot.

```

Do I need to do any of this? I did reboot. Currently iwconfig doesn't show the wireless.

And thanks jonathon6017, that sounds like good advice. I have been messing around with things a bit, so maybe a fresh install will fix my problem if this doesn't work.

Is the ndiswrapper route generally considered worse than running a linux driver?

---

### Post by Yellow Pasque on 2011-05-31
If the latest 8192/8188ce git isn't working, then it's a bug that needs resolved. This isn't Windows where a fresh install magically fixes stuff. Also, it's confusing whether or not you still have ndiswrapper stuff on your system. Try this:
```
sudo modprobe -r rtl8192ce
sudo modprobe rtl8192ce
```
Then look at dmesg:
```
dmesg | tail -n 30
```

---

### Post by h.r. on 2011-05-31
```
~$ dmesg | tail -n 30
[ 1562.428626] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 1562.428632] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[ 1562.428637] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 1562.428643] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[ 1562.428648] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 1562.428654] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[ 1562.428659] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 1562.428665] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[ 1562.428670] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 1562.428676] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[ 1562.428680] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 1562.428686] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[ 1562.428691] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 1562.428697] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[ 1562.428702] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 1562.428708] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[ 1562.428713] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 1562.428719] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[ 1562.428724] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 1562.428729] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[ 1562.428734] cfg80211: Disabling freq 2484 MHz
[ 1562.428742] cfg80211: Regulatory domain changed to country: EC
[ 1562.428746] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1562.428751] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1562.428757] cfg80211:     (5170000 KHz - 5250000 KHz @ 20000 KHz), (300 mBi, 1700 mBm)
[ 1562.428763] cfg80211:     (5250000 KHz - 5330000 KHz @ 20000 KHz), (300 mBi, 2300 mBm)
[ 1562.428769] cfg80211:     (5735000 KHz - 5835000 KHz @ 20000 KHz), (300 mBi, 3000 mBm)
[ 1562.455702] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[ 1562.456559] rtlwifi: wireless switch is on
[ 1562.504202] <30>udev[2130]: renamed network interface wlan%d to wlan0

```

---

### Post by jonathon6017 on 2011-06-02
I just mentioned the fresh install because I seen cases like this where a user will install multiple wireless drivers and they will interfere with each other and lead to the card still not working no matter what

---

### Post by rigel4 on 2011-06-02
> **h.r. said:**
> Hey I just got a new ThinkPad Edge 15, and I'm trying to make the wireless work. I'm running Ubuntu 11.04. I'm not experienced with Linux. The hardware is definitely working, everything is fine in Windows.

I tried to use ndiswrapper, and I installed the windows driver successfully, but it doesn't recognise my card. ndiswrapper -l returns:

net8192ce : driver installed
    device (10EC:8176) present (alternate driver: rtl8192ce)

But iwconfig returns:

lo        no wireless extensions.
eth1      no wireless extensions

I tried installing the Realtek rtl8192ce linux driver. I followed the instructions in the readme, which just said to sudo make install and restart my system, and then my wireless manager should find the card, but to no avail. I didn't get any error messages, but the behavior of my wireless manager (the default gnome one) as well as the output of iwconfig, remains unchanged.

Any advice? Thanks.

I have a Lenovo R500 Thinkpad , Works out of the box.

---

### Post by h.r. on 2011-06-05
> **rigel4 said:**
> I have a Lenovo R500 Thinkpad , Works out of the box.

Good for you, but unfortunately it didn't for me.

Temüjin, did you glean any information from the dmesg that i posted?

---

### Post by Yellow Pasque on 2011-06-15
No, I didn't see any errors/issues, but maybe you need to go back a little further:
```
dmesg | tail -n 100
```

---

### Post by h.r. on 2011-06-15
```
[    2.147870] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.148993] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    2.149004] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    2.149013] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.149930] ata1.00: configured for UDMA/100
[    2.150146] scsi 0:0:0:0: Direct-Access     ATA      HITACHI HTS72323 EC2Z PQ: 0 ANSI: 5
[    2.150282] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.150293] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.150331] sd 0:0:0:0: [sda] Write Protect is off
[    2.150334] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.150365] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.154542] Refined TSC clocksource calibration: 2294.786 MHz.
[    2.154553] Switching to clocksource tsc
[    2.202531] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    2.214305]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    2.214726] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.335251] hub 2-1:1.0: USB hub found
[    2.335337] hub 2-1:1.0: 6 ports detected
[    2.406623] usb 1-1.5: new high speed USB device using ehci_hcd and address 3
[    2.606526] usb 2-1.2: new low speed USB device using ehci_hcd and address 3
[    2.870190] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.872138] ata5.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[    2.872151] ata5.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    2.872159] ata5.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.872170] ata5.00: ATAPI: HL-DT-STDVDRAM GT33N, LE02, max UDMA/66
[    2.874375] ata5.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[    2.874387] ata5.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    2.874395] ata5.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.874408] ata5.00: configured for UDMA/66
[    2.876287] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GT33N     LE02 PQ: 0 ANSI: 5
[    2.879212] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.879223] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.879411] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    2.879522] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    3.198023] ata6: SATA link down (SStatus 0 SControl 300)
[    3.205285] input: Dell Dell USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input3
[    3.205497] generic-usb 0003:413C:3012.0001: input,hidraw0: USB HID v1.11 Mouse [Dell Dell USB Optical Mouse] on usb-0000:00:1d.0-1.2/input0
[    3.205655] usbcore: registered new interface driver usbhid
[    3.205657] usbhid: USB HID core driver
[    3.614854] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   16.548990] <30>udev[359]: starting version 167
[   16.551391] Adding 7963644k swap on /dev/sda6.  Priority:-1 extents:1 across:7963644k 
[   16.599302] lp: driver loaded but no devices found
[   16.607402] <30>udev[373]: renamed network interface eth0 to eth1
[   16.608174] Linux video capture interface: v2.00
[   16.614139] uvcvideo: Found UVC 1.00 device Integrated Camera (04f2:b257)
[   16.615904] input: Integrated Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input4
[   16.615982] usbcore: registered new interface driver uvcvideo
[   16.615984] USB Video Class driver (v1.0.0)
[   16.647227] Disabling lock debugging due to kernel taint
[   16.650104] [drm] Initialized drm 1.1.0 20060810
[   16.654695] type=1400 audit(1308169998.485:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=451 comm="apparmor_parser"
[   16.655412] type=1400 audit(1308169998.489:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=451 comm="apparmor_parser"
[   16.655934] type=1400 audit(1308169998.489:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=451 comm="apparmor_parser"
[   16.657528] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   16.661677] Non-volatile memory driver v1.3
[   16.682459] usbcore: registered new interface driver ndiswrapper
[   16.733601] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.733607] i915 0000:00:02.0: setting latency timer to 64
[   16.743920] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   16.753676] i915 0000:00:02.0: irq 42 for MSI/MSI-X
[   16.753681] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   16.753683] [drm] Driver supports precise vblank timestamp query.
[   16.782262] thinkpad_acpi: ThinkPad ACPI Extras v0.24
[   16.782265] thinkpad_acpi: http://ibm-acpi.sf.net/
[   16.782267] thinkpad_acpi: ThinkPad BIOS 8HET30WW(1.12), EC unknown
[   16.782269] thinkpad_acpi: Lenovo ThinkPad E520, model 1143CTO
[   16.785310] thinkpad_acpi: detected a 8-level brightness capable ThinkPad
[   16.787467] acer-wmi: Acer Laptop ACPI-WMI Extras
[   16.850566] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   16.858342] Registered led device: tpacpi::thinklight
[   16.858357] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one.
[   16.858432] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[   16.859568] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input5
[   16.905510] Console: switching to colour frame buffer device 170x48
[   16.905536] fb0: inteldrmfb frame buffer device
[   16.905537] drm: registered panic notifier
[   16.943514] acpi device:40: registered as cooling_device4
[   16.943692] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   16.943782] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   16.943998] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   16.944312] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   16.944370] HDA Intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   16.944401] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   17.215777] r8169 0000:02:00.0: eth1: link down
[   17.215931] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   17.296691] Synaptics Touchpad, model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd000b3/0x340000/0xa0400
[   17.296709] serio: Synaptics pass-through port at isa0060/serio1/input0
[   17.329176] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   17.449670] type=1400 audit(1308169999.281:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=833 comm="apparmor_parser"
[   17.450491] type=1400 audit(1308169999.281:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=833 comm="apparmor_parser"
[   17.451029] type=1400 audit(1308169999.285:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=833 comm="apparmor_parser"
[   17.453651] type=1400 audit(1308169999.285:8): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=834 comm="apparmor_parser"
[   17.453810] type=1400 audit(1308169999.285:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi" pid=837 comm="apparmor_parser"
[   17.454342] type=1400 audit(1308169999.285:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi///usr/sbin/mysqld" pid=837 comm="apparmor_parser"
[   17.454525] type=1400 audit(1308169999.285:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=836 comm="apparmor_parser"
[   17.803072] ppdev: user-space parallel port driver
[   21.275916] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   21.928435] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   22.106497] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input8

```

---

### Post by h.r. on 2011-06-15
I did try a lot of different things, is it possible i have remnants of old drivers or something lying around that conflict?

---

### Post by Yellow Pasque on 2011-06-15
I should have been more specific:
```
sudo modprobe -r rtl8192ce
sudo modprobe rtl8192ce
dmesg | tail -n 100
```

---

### Post by h.r. on 2011-06-15
I decided to reinstall ubuntu from scratch, just in case there were leftovers of ndiswrapper or something lying around. I retraced my steps, and this time it didn't crash when i tried to turn the wireless on, it just didn't work. progress! Here's the output:

make
make install
reboot
rfkill unblock all
ifconfig wlan0 up
ifconfig

```
eth0      Link encap:Ethernet  HWaddr f0:de:f1:61:51:de  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:40 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8784 (8.7 KB)  TX bytes:8784 (8.7 KB)

wlan0     Link encap:Ethernet  HWaddr ec:55:f9:c2:26:f8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

sudo modprobe -r rtl8192ce
sudo modprobe rtl8192ce
dmesg | tail -n 100

```
[   15.575912] fb0: inteldrmfb frame buffer device
[   15.575917] drm: registered panic notifier
[   15.620739] acpi device:40: registered as cooling_device4
[   15.621075] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   15.621185] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   15.621433] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   15.621477] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   15.621541] HDA Intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   15.621572] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.692250] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   15.692254] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.692257] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   15.692259] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.692262] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   15.692265] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.692267] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   15.692270] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.692272] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   15.692274] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.692276] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   15.692279] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.692281] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   15.692284] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.692286] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   15.692288] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.692291] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   15.692293] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.692295] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   15.692298] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.692300] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   15.692303] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.692305] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   15.692308] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.692310] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   15.692313] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.692315] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   15.692480] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   15.696528] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   15.697064] rtlwifi: wireless switch is on
[   15.784444] r8169 0000:02:00.0: eth0: link down
[   15.784576] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.812451] type=1400 audit(1308183234.666:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=797 comm="apparmor_parser"
[   15.813508] type=1400 audit(1308183234.666:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=801 comm="apparmor_parser"
[   15.814911] type=1400 audit(1308183234.666:7): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=802 comm="apparmor_parser"
[   15.815531] type=1400 audit(1308183234.670:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=798 comm="apparmor_parser"
[   15.816251] type=1400 audit(1308183234.670:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=801 comm="apparmor_parser"
[   15.816305] type=1400 audit(1308183234.670:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=798 comm="apparmor_parser"
[   15.816815] type=1400 audit(1308183234.670:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=798 comm="apparmor_parser"
[   15.954201] Synaptics Touchpad, model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd000b3/0x340000/0xa0400
[   15.954209] serio: Synaptics pass-through port at isa0060/serio1/input0
[   15.987369] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   16.807723] ppdev: user-space parallel port driver
[   17.488724] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   17.947787] psmouse serio2: ID: 10 00 64
[   18.490446] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   20.615391] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   20.790380] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input8
[   59.069719] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   65.446722] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   74.125748] rtl8192ce 0000:08:00.0: PCI INT A disabled
[   82.328470] cfg80211: Calling CRDA to update world regulatory domain
[   82.338375] cfg80211: World regulatory domain updated:
[   82.338377] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   82.338380] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   82.338382] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   82.338383] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   82.338385] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   82.338386] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   82.351878] rtl8192ce 0000:08:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   82.351890] rtl8192ce 0000:08:00.0: setting latency timer to 64
[   82.366207] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   82.366210] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   82.366211] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   82.366213] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   82.366214] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   82.366216] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   82.366218] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   82.366219] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   82.366220] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   82.366222] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   82.366224] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   82.366225] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   82.366227] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   82.366228] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   82.366230] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   82.366231] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   82.366233] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   82.366234] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   82.366236] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   82.366237] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   82.366239] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   82.366240] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   82.366242] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   82.366243] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   82.366245] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   82.366247] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   82.366248] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   82.366391] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   82.366562] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   82.367341] rtlwifi: wireless switch is on

```

---

