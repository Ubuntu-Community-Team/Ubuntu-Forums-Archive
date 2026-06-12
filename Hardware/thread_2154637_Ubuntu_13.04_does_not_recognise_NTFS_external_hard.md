---
title: "Ubuntu 13.04 does not recognise NTFS external hard drive"
date: 2013-06-15
forum: Hardware
---

### Post by cr15t1 on 2013-06-15
Hello,

I can't make Ubuntu 13.04 to recognise my external NTFS hard drive. In 12.04 LTS there was no problem with exactly the same hard. I aloso have another external HDD, but ext4, no problems.

Thank you in advance for you help.

---

### Post by DeathByDenim on 2013-06-15
Does it show up if you open a terminal and type
```
lsusb
```
(That's assuming you're using USB to connect the drive.)

If so, what does it say when you try to mount it manually?
```
mkdir testmnt
sudo mount /dev/sdX1 testmnt

```
You need to replace the X above with the letter corresponding to your drive. Likely either 'c' or 'd'.

---

### Post by cr15t1 on 2013-06-15
lsub result is 

:~$ lsusb
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 002 Device 004: ID 14cd:6116 Super Top M6116 SATA Bridge
Bus 002 Device 003: ID 05c8:021e Cheng Uei Precision Industry Co., Ltd (Foxlink)

As for the secon one... see below

dumitru@dumitru-HP-Pavilion-g6-Notebook-PC:~$ sudo mount /dev/sdc1 testmnt
mount: special device /dev/sdc1 does not exist
dumitru@dumitru-HP-Pavilion-g6-Notebook-PC:~$ sudo mount /dev/sdd1 testmnt
mount: special device /dev/sdd1 does not exist
dumitru@dumitru-HP-Pavilion-g6-Notebook-PC:~$ 

Thanks a lot for your help and I hope I'll have further answers

---

### Post by sum1nil on 2013-06-15
Hi, you'll want to find out what device it is odds are it is scdd or scde. Making a mistake here will not matter you'll just. get an error message. Mkdir my 'drive'. Type 'mount -t NTFS -o rw /dev/sdX(where X is d. or c or whatever) ./drive.  There. should be no feedback. Mount.  'drive'and get your goodies.  Read 'Man fstab' for a more permanenant solution. Best wishes.

---

### Post by cr15t1 on 2013-06-16
The result of 'sudo mount -t NTFS -o rw /dev/sdd' or'sudo mount -t NTFS -o rw /dev/sdc' is

Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

---

### Post by user_of_gnomes on 2013-06-16
Just to be on the safe side: did you try a different USB cable?

---

### Post by cr15t1 on 2013-06-16
Yas, just now. No difference.
10x

---

### Post by DeathByDenim on 2013-06-17
Well that's odd. I must have guessed wrong for the letter. I figured it would be either 'c' or 'd', but apparently not. In any case, you drive seems to be detected by lsusb, so that's good. Could you post the output of this command?
```
ls /dev | grep "[sh]d[a-z][1-9]"
```
It will show you all of the attached hard drives. There should be entries like sda1, sda2, etc. Those are for your internal hard drive, but there should be others. Maybe sdb?
In that case, use 'b' instead of 'X' in
```
mkdir testmnt
sudo mount /dev/sdX1 testmnt
```
If you get no error, you should be able to access your files in the testmnt directory.

---

### Post by cr15t1 on 2013-06-17
yes is sdb1

but after 
sudo mount /dev/sdX1 testmnt
nothing happens, just that I'm unable to write any other command in the terminal, see below

sudo mount /dev/sdX1 testmnt

^[[B^[[B^[[A^[[A^[[A^[[D^[[D^[[D




^[[A^[[A^[[A^[^[^[

---

### Post by cr15t1 on 2013-06-17
by the way, when closing the terminal it said that There is still a process running in this terminal. Closing the terminal will kill it.

---

### Post by DeathByDenim on 2013-06-18
Well that's really odd. I was hoping for an error message at least...
Can you try unplugging the drive, then replug it and try to mount it again?
Then in another terminal, you can type
```
dmesg
```
That will show you a lot of information about what your system is currently doing. Additionally, you can take a look at the file /var/log/syslog. Maybe some errors will show up there relating to sdb. You could also post the output of dmesg and the file /var/log/syslog here. You can save the output of dmesg by typing:
```
dmesg > dmesg.log
```
That will create a file called dmesg.log

---

### Post by cr15t1 on 2013-06-18
[   16.346897] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWMC] (Node f7436330), AE_AML_BUFFER_LIMIT (20121018/psparse-537)
[   16.346995] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node f7436450), AE_AML_BUFFER_LIMIT (20121018/psparse-537)
[   16.408746] Linux video capture interface: v2.00
[   16.537115] [drm] Initialized drm 1.1.0 20060810
[   16.592335] microcode: CPU1 sig=0x20655, pf=0x10, revision=0x2
[   16.595046] microcode: CPU2 sig=0x20655, pf=0x10, revision=0x2
[   16.597955] microcode: CPU3 sig=0x20655, pf=0x10, revision=0x2
[   16.601140] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   16.849724] i915 0000:00:02.0: setting latency timer to 64
[   16.851188] i915 0000:00:02.0: irq 45 for MSI/MSI-X
[   16.851213] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   16.851218] [drm] Driver supports precise vblank timestamp query.
[   16.851663] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   16.851670] vgaarb: transferring owner from PCI:0000:00:02.0 to PCI:0000:01:00.0
[   16.863459] lp: driver loaded but no devices found
[   16.888710] uvcvideo: Found UVC 1.00 device HP Webcam-101 (05c8:021e)
[   16.903100] input: HP Webcam-101 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input8
[   16.903311] usbcore: registered new interface driver uvcvideo
[   16.903317] USB Video Class driver (1.1.1)
[   16.977002] kvm: disabled by bios
[   17.113339] VGA switcheroo: detected Optimus DSM method \_SB_.PCI0.P0P3.PEGP handle
[   17.113391] nouveau 0000:01:00.0: enabling device (0004 -> 0007)
[   17.120391] cfg80211: Calling CRDA to update world regulatory domain
[   17.145502] fbcon: inteldrmfb (fb0) is primary device
[   17.303977] cfg80211: World regulatory domain updated:
[   17.303980] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.303985] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.303989] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.303993] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.303996] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.304000] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.646927] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   17.652605] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   17.703380] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x240000/0xa0400, board id: 1680, fw id: 706145
[   17.752464] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   17.943060] Console: switching to colour frame buffer device 170x48
[   17.953349] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   17.953352] i915 0000:00:02.0: registered panic notifier
[   17.971892] acpi device:01: registered as cooling_device4
[   17.972498] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   17.972647] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input10
[   17.973819] ACPI Warning: For \_SB_.PCI0.P0P3.PEGP._DOD: Return Package has no elements (empty) (20121018/nspredef-463)
[   17.973879] ACPI: Video Device [PEGP] (multi-head: yes  rom: yes  post: no)
[   17.974014] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:08/LNXVIDEO:01/input/input11
[   17.974237] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   17.974678] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   17.985768] nouveau  [  DEVICE][0000:01:00.0] BOOT0  : 0x0d9100a1
[   17.985781] nouveau  [  DEVICE][0000:01:00.0] Chipset: GF119 (NVD9)
[   17.985789] nouveau  [  DEVICE][0000:01:00.0] Family : NVD0
[   17.989294] nouveau  [   VBIOS][0000:01:00.0] checking PRAMIN for image...
[   18.037482] nouveau  [   VBIOS][0000:01:00.0] ... signature not found
[   18.037491] nouveau  [   VBIOS][0000:01:00.0] checking PROM for image...
[   18.037565] nouveau  [   VBIOS][0000:01:00.0] ... signature not found
[   18.037573] nouveau  [   VBIOS][0000:01:00.0] checking ACPI for image...
[   18.179849] input: HDA Intel MID HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   18.180096] input: HDA Intel MID Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   18.180323] input: HDA Intel MID Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   18.493273] Bluetooth: Core ver 2.16
[   18.493320] NET: Registered protocol family 31
[   18.493325] Bluetooth: HCI device and connection manager initialized
[   18.493342] Bluetooth: HCI socket layer initialized
[   18.493350] Bluetooth: L2CAP socket layer initialized
[   18.493367] Bluetooth: SCO socket layer initialized
[   18.498168] nouveau  [   VBIOS][0000:01:00.0] ... appears to be valid
[   18.498177] nouveau  [   VBIOS][0000:01:00.0] using image from ACPI
[   18.498502] nouveau  [   VBIOS][0000:01:00.0] BIT signature found
[   18.498510] nouveau  [   VBIOS][0000:01:00.0] version 75.19.21.00.07
[   18.499415] nouveau  [ DEVINIT][0000:01:00.0] adaptor not initialised
[   18.499424] nouveau  [   VBIOS][0000:01:00.0] running init tables
[   18.535809] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.535818] Bluetooth: BNEP filters: protocol multicast
[   18.535835] Bluetooth: BNEP socket layer initialized
[   18.637928] nouveau  [     PFB][0000:01:00.0] RAM type: DDR3
[   18.637940] nouveau  [     PFB][0000:01:00.0] RAM size: 1024 MiB
[   18.637948] nouveau  [     PFB][0000:01:00.0]    ZCOMP: 0 tags
[   18.652859] init: avahi-cups-reload main process (875) terminated with status 1
[   18.670295] Bluetooth: RFCOMM TTY layer initialized
[   18.670321] Bluetooth: RFCOMM socket layer initialized
[   18.670325] Bluetooth: RFCOMM ver 1.11
[   18.683970] vga_switcheroo: enabled
[   18.684162] [TTM] Zone  kernel: Available graphics memory: 423198 kiB
[   18.684166] [TTM] Zone highmem: Available graphics memory: 1960354 kiB
[   18.684170] [TTM] Initializing pool allocator
[   18.684179] [TTM] Initializing DMA pool allocator
[   18.684204] mtrr: no more MTRRs available
[   18.684210] nouveau  [     DRM] VRAM: 1024 MiB
[   18.684214] nouveau  [     DRM] GART: 512 MiB
[   18.684221] nouveau  [     DRM] BIT BIOS found
[   18.684227] nouveau  [     DRM] Bios version 75.19.21.00
[   18.684234] nouveau  [     DRM] TMDS table version 2.0
[   18.684239] nouveau  [     DRM] DCB version 4.0
[   18.684244] nouveau  [     DRM] DCB outp 00: 02000300 00000000
[   18.684249] nouveau  [     DRM] DCB conn 00: 00000000
[   18.686314] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   18.686321] [drm] No driver support for vblank timestamp query.
[   18.686329] nouveau  [     DRM] ACPI backlight interface available, not registering our own
[   18.686774] nouveau  [     DRM] 1 available performance level(s)
[   18.686783] nouveau  [     DRM] 1: core 270MHz shader 540MHz memory 405MHz
[   18.686789] nouveau  [     DRM] c: core 270MHz shader 540MHz memory 405MHz
[   18.704457] nouveau  [     DRM] MM: using COPY0 for buffer copies
[   18.705572] nouveau 0000:01:00.0: No connectors reported connected with modes
[   18.705579] [drm] Cannot find any crtc or sizes - going 1024x768
[   18.770949] nouveau  [     DRM] allocated 1024x768 fb: 0x60000, bo eff7fa00
[   18.771126] nouveau 0000:01:00.0: fb1: nouveaufb frame buffer device
[   18.771137] [drm] Initialized nouveau 1.1.0 20120801 for 0000:01:00.0 on minor 1
[   18.839738] ppdev: user-space parallel port driver
[   18.995400] type=1400 audit(1371559408.058:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=895 comm="apparmor_parser"
[   18.996673] type=1400 audit(1371559408.058:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=895 comm="apparmor_parser"
[   20.421995] r8169 0000:03:00.0 eth0: link down
[   20.422006] r8169 0000:03:00.0 eth0: link down
[   20.422053] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.542942] init: failsafe main process (810) killed by TERM signal
[   21.437517] intel ips 0000:00:1f.6: i915 driver attached, reenabling gpu turbo
[   21.738504] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.045636] type=1400 audit(1371559411.114:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1039 comm="apparmor_parser"
[   22.045756] type=1400 audit(1371559411.114:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1042 comm="apparmor_parser"
[   22.045968] type=1400 audit(1371559411.114:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=1039 comm="apparmor_parser"
[   22.046478] type=1400 audit(1371559411.114:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1042 comm="apparmor_parser"
[   22.046663] type=1400 audit(1371559411.114:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=1041 comm="apparmor_parser"
[   22.046811] type=1400 audit(1371559411.114:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1042 comm="apparmor_parser"
[   22.047148] type=1400 audit(1371559411.114:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper//chromium_browser" pid=1041 comm="apparmor_parser"
[   22.049189] type=1400 audit(1371559411.118:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=1040 comm="apparmor_parser"
[   22.049664] type=1400 audit(1371559411.118:15): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=1040 comm="apparmor_parser"
[   22.050741] type=1400 audit(1371559411.118:16): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1045 comm="apparmor_parser"
[   22.192048] r8169 0000:03:00.0 eth0: link up
[   22.192061] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   25.626809] NET: Registered protocol family 24
[   35.871796] ip_tables: (C) 2000-2006 Netfilter Core Team
[   48.636803] audit_printk_skb: 36 callbacks suppressed
[   48.636808] type=1400 audit(1371559437.746:29): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/2230/cmdline" pid=2173 comm="dbus-daemon" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[   48.657279] type=1400 audit(1371559437.766:30): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/2236/cmdline" pid=2173 comm="dbus-daemon" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[   48.658318] type=1400 audit(1371559437.766:31): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/2237/cmdline" pid=2173 comm="dbus-daemon" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[   48.664011] type=1400 audit(1371559437.774:32): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/2239/cmdline" pid=2173 comm="dbus-daemon" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[   48.695303] type=1400 audit(1371559437.806:33): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/2232/cmdline" pid=2173 comm="dbus-daemon" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[   48.882856] type=1400 audit(1371559437.994:34): apparmor="DENIED" operation="mount" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/run/user/guest-jD2357/gvfs/" pid=2256 comm="gvfsd-fuse" fstype="fuse.gvfsd-fuse" srcname="gvfsd-fuse" flags="rw, nosuid, nodev"
[   49.856602] type=1400 audit(1371559438.966:35): apparmor="DENIED" operation="open" parent=2123 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/etc/compizconfig/unity.ini" pid=2267 comm="compiz" requested_mask="c" denied_mask="c" fsuid=199 ouid=0
[   59.960013] type=1400 audit(1371559449.086:36): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/2092/stat" pid=2337 comm="bamfdaemon" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[   59.960063] type=1400 audit(1371559449.086:37): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/1166/stat" pid=2337 comm="bamfdaemon" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[   81.133114] type=1400 audit(1371559470.294:38): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/2092/stat" pid=2337 comm="bamfdaemon" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[   81.133169] type=1400 audit(1371559470.294:39): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/1166/stat" pid=2337 comm="bamfdaemon" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[  163.042994] type=1400 audit(1371559552.330:40): apparmor="DENIED" operation="open" parent=2764 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/sys/kernel/pid_max" pid=2765 comm="ps" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[  163.043626] type=1400 audit(1371559552.330:41): apparmor="DENIED" operation="open" parent=2764 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/1/stat" pid=2765 comm="ps" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[  163.043655] type=1400 audit(1371559552.330:42): apparmor="DENIED" operation="open" parent=2764 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/2/stat" pid=2765 comm="ps" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[  163.043681] type=1400 audit(1371559552.330:43): apparmor="DENIED" operation="open" parent=2764 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/3/stat" pid=2765 comm="ps" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[  163.043706] type=1400 audit(1371559552.330:44): apparmor="DENIED" operation="open" parent=2764 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/4/stat" pid=2765 comm="ps" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[  163.043731] type=1400 audit(1371559552.330:45): apparmor="DENIED" operation="open" parent=2764 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/5/stat" pid=2765 comm="ps" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[  163.043756] type=1400 audit(1371559552.330:46): apparmor="DENIED" operation="open" parent=2764 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/6/stat" pid=2765 comm="ps" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[  163.043780] type=1400 audit(1371559552.330:47): apparmor="DENIED" operation="open" parent=2764 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/7/stat" pid=2765 comm="ps" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[  163.043805] type=1400 audit(1371559552.330:48): apparmor="DENIED" operation="open" parent=2764 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/8/stat" pid=2765 comm="ps" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[  163.043831] type=1400 audit(1371559552.330:49): apparmor="DENIED" operation="open" parent=2764 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/9/stat" pid=2765 comm="ps" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[ 2380.907055] audit_printk_skb: 351 callbacks suppressed
[ 2380.907066] type=1400 audit(1371561773.630:167): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/2092/stat" pid=2337 comm="bamfdaemon" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[ 2380.907227] type=1400 audit(1371561773.634:168): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/1166/stat" pid=2337 comm="bamfdaemon" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[ 2381.055053] systemd-hostnamed[2944]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 2381.342489] type=1400 audit(1371561774.070:169): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/2092/stat" pid=2337 comm="bamfdaemon" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[ 2381.342543] type=1400 audit(1371561774.070:170): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/1166/stat" pid=2337 comm="bamfdaemon" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[ 5440.565275] type=1400 audit(1371564838.034:171): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/2092/stat" pid=2337 comm="bamfdaemon" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[ 5440.565399] type=1400 audit(1371564838.034:172): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/1166/stat" pid=2337 comm="bamfdaemon" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[ 5465.853071] type=1400 audit(1371564863.362:173): apparmor="DENIED" operation="open" parent=3403 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/sys/kernel/pid_max" pid=3404 comm="ps" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[ 5465.853448] type=1400 audit(1371564863.362:174): apparmor="DENIED" operation="open" parent=3403 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/1/stat" pid=3404 comm="ps" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[ 5465.853461] type=1400 audit(1371564863.362:175): apparmor="DENIED" operation="open" parent=3403 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/2/stat" pid=3404 comm="ps" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[ 5465.853474] type=1400 audit(1371564863.362:176): apparmor="DENIED" operation="open" parent=3403 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/3/stat" pid=3404 comm="ps" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[ 5465.853485] type=1400 audit(1371564863.362:177): apparmor="DENIED" operation="open" parent=3403 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/5/stat" pid=3404 comm="ps" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[ 5465.853496] type=1400 audit(1371564863.362:178): apparmor="DENIED" operation="open" parent=3403 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/7/stat" pid=3404 comm="ps" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[ 5465.853506] type=1400 audit(1371564863.362:179): apparmor="DENIED" operation="open" parent=3403 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/8/stat" pid=3404 comm="ps" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[ 5465.853517] type=1400 audit(1371564863.362:180): apparmor="DENIED" operation="open" parent=3403 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/9/stat" pid=3404 comm="ps" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[ 5465.853527] type=1400 audit(1371564863.362:181): apparmor="DENIED" operation="open" parent=3403 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/10/stat" pid=3404 comm="ps" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[ 5465.853538] type=1400 audit(1371564863.362:182): apparmor="DENIED" operation="open" parent=3403 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/11/stat" pid=3404 comm="ps" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[ 8543.410464] audit_printk_skb: 330 callbacks suppressed
[ 8543.410470] type=1400 audit(1371567945.690:293): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/2092/stat" pid=2337 comm="bamfdaemon" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[ 8543.410522] type=1400 audit(1371567945.690:294): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/1166/stat" pid=2337 comm="bamfdaemon" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[ 8543.477301] systemd-hostnamed[3625]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 8543.696017] type=1400 audit(1371567945.978:295): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/2092/stat" pid=2337 comm="bamfdaemon" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[ 8543.696073] type=1400 audit(1371567945.978:296): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/1166/stat" pid=2337 comm="bamfdaemon" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[10538.266233] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[10538.266242] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[10538.512743] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[10538.512756] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[10538.608177] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[10538.608187] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[10538.735742] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[10538.735758] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[10538.832298] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[10538.832311] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[10538.959197] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[10538.959208] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[10539.054928] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[10539.054938] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[10539.150259] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[10539.150268] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[10539.271065] atkbd serio0: Unknown key released (translated set 2, code 0xab on isa0060/serio0).
[10539.271075] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[21655.329447] type=1400 audit(1371581077.938:297): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/2092/stat" pid=2337 comm="bamfdaemon" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[21655.329560] type=1400 audit(1371581077.938:298): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/1166/stat" pid=2337 comm="bamfdaemon" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[21673.734343] type=1400 audit(1371581096.374:299): apparmor="DENIED" operation="open" parent=4952 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/sys/kernel/pid_max" pid=4953 comm="ps" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[21673.734708] type=1400 audit(1371581096.374:300): apparmor="DENIED" operation="open" parent=4952 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/1/stat" pid=4953 comm="ps" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[21673.734720] type=1400 audit(1371581096.374:301): apparmor="DENIED" operation="open" parent=4952 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/2/stat" pid=4953 comm="ps" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[21673.734731] type=1400 audit(1371581096.374:302): apparmor="DENIED" operation="open" parent=4952 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/3/stat" pid=4953 comm="ps" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[21673.734742] type=1400 audit(1371581096.374:303): apparmor="DENIED" operation="open" parent=4952 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/5/stat" pid=4953 comm="ps" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[21673.734753] type=1400 audit(1371581096.374:304): apparmor="DENIED" operation="open" parent=4952 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/7/stat" pid=4953 comm="ps" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[21673.734764] type=1400 audit(1371581096.374:305): apparmor="DENIED" operation="open" parent=4952 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/8/stat" pid=4953 comm="ps" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[21673.734774] type=1400 audit(1371581096.374:306): apparmor="DENIED" operation="open" parent=4952 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/9/stat" pid=4953 comm="ps" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[21673.734785] type=1400 audit(1371581096.374:307): apparmor="DENIED" operation="open" parent=4952 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/10/stat" pid=4953 comm="ps" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[21673.734797] type=1400 audit(1371581096.374:308): apparmor="DENIED" operation="open" parent=4952 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/11/stat" pid=4953 comm="ps" requested_mask="r" denied_mask="r" fsuid=199 ouid=0
[24698.943206] audit_printk_skb: 327 callbacks suppressed
[24698.943212] type=1400 audit(1371584126.270:418): apparmor="DENIED" operation="mkdir" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/run/user/guest-jD2357/" pid=2367 comm="indicator-sessi" requested_mask="c" denied_mask="c" fsuid=199 ouid=199
[24698.943322] type=1400 audit(1371584126.270:419): apparmor="DENIED" operation="mkdir" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/run/user/guest-jD2357/" pid=2367 comm="indicator-sessi" requested_mask="c" denied_mask="c" fsuid=199 ouid=199
[24698.943405] type=1400 audit(1371584126.270:420): apparmor="DENIED" operation="mkdir" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/run/user/guest-jD2357/" pid=2367 comm="indicator-sessi" requested_mask="c" denied_mask="c" fsuid=199 ouid=199
[24698.943501] type=1400 audit(1371584126.270:421): apparmor="DENIED" operation="mkdir" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/run/user/guest-jD2357/" pid=2367 comm="indicator-sessi" requested_mask="c" denied_mask="c" fsuid=199 ouid=199
[24856.120489] usb 2-1.2: new high-speed USB device number 4 using ehci-pci
[24856.213790] usb 2-1.2: New USB device found, idVendor=14cd, idProduct=6116
[24856.213798] usb 2-1.2: New USB device strings: Mfr=1, Product=3, SerialNumber=2
[24856.213805] usb 2-1.2: Product: USB 2.0  SATA BRIDGE   
[24856.213810] usb 2-1.2: Manufacturer: Super Top   
[24856.213815] usb 2-1.2: SerialNumber: M6116018VF16
[24856.261197] Initializing USB Mass Storage driver...
[24856.261392] usbcore: registered new interface driver usb-storage
[24856.261398] USB Mass Storage support registered.
[24856.283513] scsi4 : usb-storage 2-1.2:1.0
[24856.283673] usbcore: registered new interface driver ums-cypress
[24857.279392] scsi 4:0:0:0: Direct-Access     WDC WD32 00BEVT-00A0RT0        PQ: 0 ANSI: 0
[24857.280941] sd 4:0:0:0: Attached scsi generic sg2 type 0
[24857.283026] sd 4:0:0:0: [sdb] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[24857.283751] sd 4:0:0:0: [sdb] Write Protect is off
[24857.283762] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[24857.284491] sd 4:0:0:0: [sdb] No Caching mode page present
[24857.284500] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[24857.289046] sd 4:0:0:0: [sdb] No Caching mode page present
[24857.289055] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[24857.298692]  sdb: sdb1
[24857.301345] sd 4:0:0:0: [sdb] No Caching mode page present
[24857.301355] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[24857.301363] sd 4:0:0:0: [sdb] Attached SCSI disk
[24864.651152] usb 2-1.2: reset high-speed USB device number 4 using ehci-pci
[24904.586547] usb 2-1.2: USB disconnect, device number 4
[24904.592962] sd 4:0:0:0: [sdb] Unhandled error code
[24904.592973] sd 4:0:0:0: [sdb]  
[24904.592979] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[24904.592991] sd 4:0:0:0: [sdb] CDB: 
[24904.592994] Read(10): 28 00 25 42 d6 af 00 00 08 00
[24904.593017] end_request: I/O error, dev sdb, sector 625137327
[24904.593027] Buffer I/O error on device sdb1, logical block 312568632
[24904.593034] Buffer I/O error on device sdb1, logical block 312568633
[24904.593040] Buffer I/O error on device sdb1, logical block 312568634
[24904.593046] Buffer I/O error on device sdb1, logical block 312568635
[24904.594282] Buffer I/O error on device sdb1, logical block 312568632
[24904.594295] Buffer I/O error on device sdb1, logical block 312568633
[24904.594304] Buffer I/O error on device sdb1, logical block 312568634
[24904.594312] Buffer I/O error on device sdb1, logical block 312568635
[24904.594351] Buffer I/O error on device sdb1, logical block 0
[24904.594359] Buffer I/O error on device sdb1, logical block 1
[24917.768863] usb 2-1.2: new high-speed USB device number 5 using ehci-pci
[24917.862093] usb 2-1.2: New USB device found, idVendor=14cd, idProduct=6116
[24917.862103] usb 2-1.2: New USB device strings: Mfr=1, Product=3, SerialNumber=2
[24917.862109] usb 2-1.2: Product: USB 2.0  SATA BRIDGE   
[24917.862114] usb 2-1.2: Manufacturer: Super Top   
[24917.862119] usb 2-1.2: SerialNumber: M6116018VF16
[24917.862788] scsi5 : usb-storage 2-1.2:1.0
[24918.859840] scsi 5:0:0:0: Direct-Access     WDC WD32 00BEVT-00A0RT0        PQ: 0 ANSI: 0
[24918.861707] sd 5:0:0:0: Attached scsi generic sg2 type 0
[24918.862489] sd 5:0:0:0: [sdb] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[24918.863229] sd 5:0:0:0: [sdb] Write Protect is off
[24918.863240] sd 5:0:0:0: [sdb] Mode Sense: 03 00 00 00
[24918.863835] sd 5:0:0:0: [sdb] No Caching mode page present
[24918.863840] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[24918.867721] sd 5:0:0:0: [sdb] No Caching mode page present
[24918.867731] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[24918.875393]  sdb: sdb1
[24918.877844] sd 5:0:0:0: [sdb] No Caching mode page present
[24918.877850] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[24918.877853] sd 5:0:0:0: [sdb] Attached SCSI disk
[24926.555138] usb 2-1.2: reset high-speed USB device number 5 using ehci-pci
dumitru@dumitru-HP-Pavilion-g6-Notebook-PC:~$

---

### Post by DeathByDenim on 2013-06-18
Well, this doesn't look too good:
```
[24904.592962] sd 4:0:0:0: [sdb] Unhandled error code
 [24904.592973] sd 4:0:0:0: [sdb] 
 [24904.592979] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
 [24904.592991] sd 4:0:0:0: [sdb] CDB: 
 [24904.592994] Read(10): 28 00 25 42 d6 af 00 00 08 00
 [24904.593017] end_request: I/O error, dev sdb, sector 625137327
 [24904.593027] Buffer I/O error on device sdb1, logical block 312568632
 [24904.593034] Buffer I/O error on device sdb1, logical block 312568633
 [24904.593040] Buffer I/O error on device sdb1, logical block 312568634
 [24904.593046] Buffer I/O error on device sdb1, logical block 312568635
 [24904.594282] Buffer I/O error on device sdb1, logical block 312568632
 [24904.594295] Buffer I/O error on device sdb1, logical block 312568633
 [24904.594304] Buffer I/O error on device sdb1, logical block 312568634
 [24904.594312] Buffer I/O error on device sdb1, logical block 312568635
 [24904.594351] Buffer I/O error on device sdb1, logical block 0
[24904.594359] Buffer I/O error on device sdb1, logical block 1
```

Could you try this commands to check if it at least can read the partition table for the drive?
```
sudo fdisk -l /dev/sdb
```

You can also query the health of the drive, but for that you need to install smartmontools:
```
sudo apt-get install smartmontools
```
And then run:
```
sudo smartctl --all /dev/sdb
```

---

### Post by cr15t1 on 2013-06-19
It takes some time, but in the end the result of fdick:
Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbad1641c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   625137344   312568641    7  HPFS/NTFS/exFAT

---

### Post by cr15t1 on 2013-06-19
As for smartctl, here is the result

dumitru@dumitru-HP-Pavilion-g6-Notebook-PC:~$ sudo smartctl --all /dev/sdb
smartctl 5.43 2012-06-30 r3573 [i686-linux-3.8.0-25-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Scorpio Blue Serial ATA
Device Model:     WDC WD3200BEVT-00A0RT0
Serial Number:    WD-WX81A20X0429
LU WWN Device Id: 5 0014ee 0021ce769
Firmware Version: 01.01A01
User Capacity:    320,072,933,376 bytes [320 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed Jun 19 21:28:43 2013 EEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (10800) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 127) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x7037)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       7
  3 Spin_Up_Time            0x0027   185   178   021    Pre-fail  Always       -       1733
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       364
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       125
 10 Spin_Retry_Count        0x0032   100   100   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       179
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       58
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       2163
194 Temperature_Celsius     0x0022   116   098   000    Old_age   Always       -       31
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   051    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

---

### Post by DeathByDenim on 2013-06-19
Hmm, I'm running out of ideas now. It's strange that fdisk takes so long. That should really be instantaneous...
The health of the drives seems to check out according to smartctl: "SMART overall-health self-assessment test result: PASSED"

It has never done a self-test yet though. You can try to test the drive using this command:
```
sudo smartctl -t short /dev/sdb
```
This will run a short test on the drive that should take less then ten minutes. It will tell you how when it's going to be finished when you run the command. You can then see the result of that test by typing:
```
sudo smartctl -l selftest /dev/sdb
```

 Alternatively, you can run a long test, but that will take several hours and I don't think that's worth it.

Finally, a last idea is that the file system might be slightly damaged. Since your drive is formatted as an NTFS drive, I assume you also use it under Windows every now and then? If so, you can let Windows check the drive using
```
chkdsk X: /f
```
where you have to substitute 'X' by whatever letter Windows assigned to the drive.

---

### Post by cr15t1 on 2013-06-20
Here is the result of 
sudo smartctl -t short /dev/sdb
Copyright (C) 2002-12 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

Smartctl: Device Read Identity Failed: Unknown error

A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.

---

### Post by Mark Phelps on 2013-06-20
You're not including the filesystem type in your mount command -- which, if I recall, will not work for non-Linux filesystems.

You should try mounting your device in the /media part of the filesystem, as follows:

> sudo mkdir /media/testmnt
sudo mount -t ntfs-3g /dev/sdX1 /media/testmnt

---

### Post by cr15t1 on 2013-06-21
No result after 10 min for *sudo mount -t ntfs-3g /dev/sdb1 /media/testmnt *
And as usual... there is still a process... when closing the trminal

---

### Post by DeathByDenim on 2013-06-21
Well, from what I can tell, your drive is having issues, but it's rather odd that it worked in 12.04. I can only think of one way to test that. You can make a live-CD (or usb stick) with the 12.04 and boot from that and see if your drive is recognized then. If that works, then it must be some bug in 13.04 and otherwise the problem lies with the drive.

Were you able to test the drive under Windows in combination with chkdsk by the way?

---

### Post by cr15t1 on 2013-06-22
Once again, the drive works perfect under Windows, but when runing chkdisk it said *Windows has checked the file system and found no problems*.

Supplimentary informations:
I saved all my data on my windows laptop, then I formated the drive (NTFS).
Same thing, Ubuntu 13.04 don't show me anything. The disk utility seems to see the drive, but trying to create a new partition on it says

[I]Error creating partition on /dev/sdb: Command-line `parted --align optimal --script "/dev/sdb" "mkpart primary ext2 1MiB 320072933375b"' exited with non-zero exit status 1: Error: You requested a partition from 1049kB to 320GB.
The closest location we can manage is 31.7kB to 31.7kB.
 (udisks-error-quark, 0)[/I]

---

### Post by DeathByDenim on 2013-06-22
Hmm, that's really strange. I'm afraid I've ran out of ideas now...
It may very well be a bug in Ubuntu 13.04 then. You may want to consider filing a bug report at [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

Or does anybody else have an idea?

---

### Post by jp734 on 2013-06-23
I had the same problem and my work around it is to start the gnome disk utility as root. Opened terminal and typed "sudo palimpsest" and mounted the drive from there. It had something to do with "FUSE". Not sure what "FUSE" is but since I hardly used the external drive anyways, I can deal with temp solution.

---

### Post by cr15t1 on 2013-06-24
Another error trying to format de drive:
[I]
Error synchronizing after initial wipe: Timed out waiting for object (udisks-error-quark, 0)[/I]

---

### Post by cr15t1 on 2013-07-16
Once again checked in Ubuntu 11.04. The HDD works perfect.

---

### Post by dannyboy79 on 2013-07-16
i've been seeing more and more people complain of problems with NTFS in more recent versions of ubuntu. maybe the ntfs-3g layer has some regression in it? if your files aren't over 4GB, and you need to access files from both linux and windows I would use FAT32. I've never trusted linux writing to NTFS. OR setup samba and share the files over a network

---

