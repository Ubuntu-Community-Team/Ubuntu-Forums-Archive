---
title: "Very slow boot after installing a new 11.04"
date: 2011-05-16
forum: Hardware
---

### Post by Neologist on 2011-05-16
Hey, guys.
My notebook, which used to boot in ~25s, is now taking almost 5 minutes to boot. Here's the interesting parts of the dmesg output:


> [    5.041723] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[    5.041904] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    5.337224] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.339238] ata2.00: ATAPI: HL-DT-STDVDRAM GT30N, 1.01, max UDMA/100
[    5.342855] ata2.00: configured for UDMA/100
[    5.347953] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GT30N     1.01 PQ: 0 ANSI: 5
[    5.352057] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.352062] cdrom: Uniform CD-ROM driver Revision: 3.20
[    5.352192] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.352257] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    6.451423] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   28.366231] Adding 3905532k swap on /dev/sda5.  Priority:-1 extents:1 across:3905532k 
[   30.304659] <30>udev[362]: starting version 167
[   36.217519] Linux video capture interface: v2.00
[   36.233720] uvcvideo: Found UVC 1.00 device Video WebCam (04f2:b044)
[   36.275363] cfg80211: Calling CRDA to update world regulatory domain
[   36.289655] input: Video WebCam as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/input/input6
[   36.289778] usbcore: registered new interface driver uvcvideo
[   36.289781] USB Video Class driver (v1.0.0)
[   37.223422] type=1400 audit(1305601207.469:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=608 comm="apparmor_parser"
[   37.223433] type=1400 audit(1305601207.469:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=594 comm="apparmor_parser"
[   37.224219] type=1400 audit(1305601207.473:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=608 comm="apparmor
_parser"
[   37.224230] type=1400 audit(1305601207.473:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=594 comm="appar
mor_parser"
[   37.224665] type=1400 audit(1305601207.473:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=594 comm="apparmor_pars
er"
[   37.224729] type=1400 audit(1305601207.473:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=608 comm="apparmor_parser"
[   37.238930] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
[   37.238960] intel ips 0000:00:1f.6: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   37.239716] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[   38.390222] lp: driver loaded but no devices found


[   51.415874] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   52.787242] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   70.171478] ppdev: user-space parallel port driver
[   71.384752] type=1400 audit(1305601241.645:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=916 comm="apparmor_parser"
[   71.385468] type=1400 audit(1305601241.649:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=916 comm="apparmor_parser"
[   71.385905] type=1400 audit(1305601241.649:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=916 comm="apparmor_parser"
[   71.442649] type=1400 audit(1305601241.705:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=920 comm="apparmor_parser"
[   71.469405] type=1400 audit(1305601241.733:12): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=915 comm="apparmor_parser"
[   71.745121] type=1400 audit(1305601242.009:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=919 comm="apparmor_parser"
[   71.745133] type=1400 audit(1305601242.009:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=911 comm="apparmor_parser"
[   71.745926] type=1400 audit(1305601242.009:15): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=919 comm="apparmor_parser"
[   71.745940] type=1400 audit(1305601242.009:16): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=911 comm="apparmor_parser"
[   74.273713] type=1400 audit(1305601244.537:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=917 comm="apparmor_parser"
[   83.773014] tg3 0000:01:00.0: irq 43 for MSI/MSI-X
[   83.801292] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   84.084283] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   84.644718] tg3 0000:01:00.0: eth0: Link is down
[   85.644265] tg3 0000:01:00.0: eth0: Link is up at 100 Mbps, full duplex
[   85.644269] tg3 0000:01:00.0: eth0: Flow control is on for TX and on for RX
[   85.644429] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   95.962926] eth0: no IPv6 routers present
[  100.591927] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[  124.520500] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[  185.057967] wlan0: authenticate with 00:23:cd:c1:f2:0e (try 1)
[  185.059976] wlan0: authenticated
[  185.059998] wlan0: associate with 00:23:cd:c1:f2:0e (try 1)
[  185.062390] wlan0: RX AssocResp from 00:23:cd:c1:f2:0e (capab=0x431 status=0 aid=1)
[  185.062394] wlan0: associated
[  185.062738] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  185.062842] cfg80211: Calling CRDA for country: BR
[  185.067311] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  185.067316] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)

[  185.067385] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  185.067388] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  185.067391] cfg80211: Disabling freq 2484 MHz
[  185.067395] cfg80211: Regulatory domain changed to country: BR
[  185.067398] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  185.067401] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  185.067404] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  185.067407] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  185.067410] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  185.067413] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  195.099691] wlan0: no IPv6 routers present
[  223.523488] wlan0: deauthenticating from 00:23:cd:c1:f2:0e by local choice (reason=3)
[  223.595780] cfg80211: All devices are disconnected, going to restore regulatory settings
[  223.595789] cfg80211: Restoring regulatory settings
[  223.595810] cfg80211: Calling CRDA to update world regulatory domain
[  223.603177] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  223.603189] cfg80211: World regulatory domain updated:
[  223.603193] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  223.603199] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  223.603205] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  223.603211] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  223.603216] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  223.603222] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Notice that these three lines are kind of suspects:

EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
eth0: no IPv6 routers present
wlan0: no IPv6 routers present

I've tried to do everything that's recommended here: [http://askubuntu.com/questions/39316/slow-boot-after-clean-install-of-natty](http://askubuntu.com/questions/39316/slow-boot-after-clean-install-of-natty)

But nothing solved it. I've seen these same three lines of the output reported, but they were never affecting the time of boot.

I'm new in the community and I don't know if here's the right place to post it. Could anyone move it if it's in the wrong place, please?

---

### Post by root45 on 2011-05-17
I'm having the same issue as you. I think it might be tied to your CD drive (at least, I hope it is, because then we have something in common).

I recommend installing the program bootchart (sudo apt-get install bootchart) and rebooting. Then if you check /var/log/bootchart you can see a picture of your boot.

[This is mine]("http://i.imgur.com/Gzdw7.png"). Notice the only processor intensive part is cdrom_id? I unplugged my DVD drive SATA cable and [this is what happens]("http://i.imgur.com/25zFO.png") without it.

I actually found this post because "Uniform CD-ROM driver Revision: 3.20" appeared in my dmesg.

So maybe this is also your problem?

---

### Post by lithopsian on 2011-05-17
Yes, dmesg isn't necessarily going to show you what it really slow, just give you messages that may be from perfectly good processes.  Use bootchart.

---

### Post by Neologist on 2011-05-18
Thank you for the tip, guys!

Here's the output of bootchart: [http://i.imgur.com/S53Ox.png](http://i.imgur.com/S53Ox.png)

I have no idea of what's happening. =/

---

### Post by Neologist on 2011-05-19
I forgot to say:

I only get a slow boot on my laptop when I'm turning it on for the first time in hours. If I reboot or turn off and then on quickly, boot takes no more than 30 seconds.

---

### Post by lithopsian on 2011-05-21
Doesn't look so bad.  Except for ureadahead!  I don't think ureadahead is actually the problem.  Rather something else is making disk access extremely slow, something that doesn't show on bootchart.  I haven't a clue what it is but it kicks in about when the root disk is mounted.  Some form of BIOS disk check utility?

---

### Post by Neologist on 2011-05-26
Erm... that's weird. After formatting Natty several times, the slow boot remained persistant. Then I just installed GNOME 3, and now my system boots in no more than 30 seconds.

I suppose it means that it's not a disk problem, but something related to Unity. :confused:

Well, the problem it's not solved at all, as I'm not able to have a regular boot on Ubuntu 11.04 as it is, originally. So I'm not going to mark the thread as "solved", unless someone ask me to.

I'm having a good time with GNOME 3, but I still want to know what's wrong with my Natty on its default.

Thank you guys for helping me!

---

### Post by Nesaskewatch on 2011-05-26
I have a similar issue and find if I hold down the control key it boots fine.  I am hoping the next kernel is a bit more robust.  Natty is the buggiest release I have seen so far...

---

### Post by Neologist on 2011-05-27
I think I spoke too soon, 'cause now - after two days of regular booting - it's taking about 5 minutes to boot, again. =/

> I have a similar issue and find if I hold down the control key it boots fine.

Seriously? And how did you find out about that? :confused:
I'll try that on the next time, thank you.

---

