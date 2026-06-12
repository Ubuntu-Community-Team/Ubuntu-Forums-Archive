---
title: "KMS / nouveau incorrectly detects TV-out"
date: 2010-05-11
forum: Hardware
---

### Post by wankel on 2010-05-11
There is no TV-out on this laptop.

After a clean install of Kubuntu 10.04 / Lucid Lynx, KDE exits intermittently to the login screen; sometimes after 15 minutes, sometimes after a longer time.

A workaround seemed installing LXDE and using that instead, but the problem arises there as well, but not as often (every few hours).

Other symptoms:
TV-out is detected and activated at 1024x768
Laptop LCD (1200x800) is degraded to run at 1024x768

I have no xorg.conf or other X configuration.

There is no external monitor connected.

I found some people on other distro's with the problem, but no solution yet. I hoped it would be solved after an apt-upgrade; has anyone here the problem or a solution?

This thread runs till a month back, with no result:
[http://www.mail-archive.com/nouveau@lists.freedesktop.org/msg05364.html](http://www.mail-archive.com/nouveau@lists.freedesktop.org/msg05364.html)

Here the problem is solved by installing a 6.30 kernel:
[http://bbs.archlinux.org/viewtopic.php?pid=567438](http://bbs.archlinux.org/viewtopic.php?pid=567438)

Here's fix for a similar, but in my understanding inversed, situation, close to a year ago:
[http://git.kernel.org/?p=linux/kernel/git/anholt/drm-intel.git;a=commit;h=03d6069912babc07a3da20e715dd6a5dc8f0f867](http://git.kernel.org/?p=linux/kernel/git/anholt/drm-intel.git;a=commit;h=03d6069912babc07a3da20e715dd6a5dc8f0f867)

Here are excerpts from kern.log en kdm.log:

KDM:
```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux sandi 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=f0fb5a3f-68ad-4646-adb5-85b0bf819fcc ro quiet splash
Build Date: 23 April 2010  05:11:46PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue May 11 18:09:46 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
resize called 1024 768
QFont::fromString: Invalid description 'Serif,20,5,0,50,0'
QFont::fromString: Invalid description 'Sans Serif,10,5,0,50,0'
QFont::fromString: Invalid description 'Sans Serif,10,5,0,75,0'
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /tmp/0173653931/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
resize called 1280 800
 ddxSigGiveUp: Closing log
error: unexpectedly disconnected from boot status daemon

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux sandi 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=f0fb5a3f-68ad-4646-adb5-85b0bf819fcc ro quiet splash
Build Date: 23 April 2010  05:11:46PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue May 11 22:10:49 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
resize called 1024 768
QFont::fromString: Invalid description 'Serif,20,5,0,50,0'
QFont::fromString: Invalid description 'Sans Serif,10,5,0,50,0'
QFont::fromString: Invalid description 'Sans Serif,10,5,0,75,0'
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /tmp/0706763448/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
resize called 1280 800

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x28) [0x4a3248]
1: /usr/bin/X (0x400000+0x655ad) [0x4655ad]
2: /lib/libpthread.so.0 (0x7f09ebd2d000+0xf8f0) [0x7f09ebd3c8f0]
3: /usr/lib/xorg/modules/drivers/nouveau_drv.so (0x7f09e8c5e000+0xfc8a) [0x7f09e8c6dc8a]
4: /usr/lib/xorg/modules/drivers/nouveau_drv.so (0x7f09e8c5e000+0x6414) [0x7f09e8c64414]
5: /usr/lib/xorg/modules/libexa.so (0x7f09e7ddd000+0xa0e2) [0x7f09e7de70e2]
6: /usr/lib/xorg/modules/libexa.so (0x7f09e7ddd000+0xa1ed) [0x7f09e7de71ed]
7: /usr/bin/X (miCopyRegion+0x29d) [0x54d3ed]
8: /usr/bin/X (miDoCopy+0x44a) [0x54d8fa]
9: /usr/lib/xorg/modules/libexa.so (0x7f09e7ddd000+0x8623) [0x7f09e7de5623]
10: /usr/bin/X (0x400000+0xda3e8) [0x4da3e8]
11: /usr/bin/X (0x400000+0x2f7ac) [0x42f7ac]
12: /usr/bin/X (0x400000+0x30c3c) [0x430c3c]
13: /usr/bin/X (0x400000+0x261aa) [0x4261aa]
14: /lib/libc.so.6 (__libc_start_main+0xfd) [0x7f09eaa25c4d]
15: /usr/bin/X (0x400000+0x25d59) [0x425d59]
Segmentation fault at address (nil)

Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.


Fatal server error:
Detected GPU lockup


```

xorg.0.log:
```
(II) NOUVEAU(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
(==) NOUVEAU(0): RGB weight 888
(==) NOUVEAU(0): Default visual is TrueColor
(==) NOUVEAU(0): Using HW cursor
(II) NOUVEAU(0): Output LVDS-1 has no monitor section
(II) NOUVEAU(0): Output VGA-1 has no monitor section
(II) NOUVEAU(0): Output TV-1 has no monitor section
(II) NOUVEAU(0): EDID vendor "AUO", prod id 10100
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) NOUVEAU(0): Printing probed modes for output LVDS-1
(II) NOUVEAU(0): Modeline "1280x800"x60.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) NOUVEAU(0): Modeline "640x350"x59.8   17.50  640 664 720 800  350 353 363 366 -hsync +vsync (21.9 kHz)
(II) NOUVEAU(0): EDID for output VGA-1
(II) NOUVEAU(0): EDID for output TV-1
(II) NOUVEAU(0): Not using default mode "640x350" (unknown reason)
(II) NOUVEAU(0): Printing probed modes for output TV-1
(II) NOUVEAU(0): Modeline "720x576"x50.0   28.66  720 776 856 960  576 576 588 597 -hsync -vsync (29.9 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x50.0   54.16  1024 1064 1200 1344  768 768 777 806 -hsync -vsync (40.3 kHz)
(II) NOUVEAU(0): Output LVDS-1 connected
(II) NOUVEAU(0): Output VGA-1 disconnected
(II) NOUVEAU(0): Output TV-1 connected
(II) NOUVEAU(0): Using fuzzy aspect match for initial modes
(II) NOUVEAU(0): Output LVDS-1 using initial mode 1024x768
(II) NOUVEAU(0): Output TV-1 using initial mode 1024x768
(II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(--) NOUVEAU(0): Virtual size is 1024x768 (pitch 1024)
(**) NOUVEAU(0):  Driver mode "1024x768": 54.2 MHz (scaled from 0.0 MHz), 40.3 kHz, 50.0 Hz
(II) NOUVEAU(0): Setting screen physical size to 270 x 203
resize called 1024 768
(II) No input driver/identifier specified (ignoring)
resize called 1280 800
(II) NOUVEAU(0): EDID vendor "AUO", prod id 10100
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)

```

kernel:
```
May 11 22:10:48 sandi kernel: [   15.640288] [drm] nouveau 0000:00:12.0: Detected a VGA connector
May 11 22:10:48 sandi kernel: [   15.640549] [drm] nouveau 0000:00:12.0: Detected a TV connector
May 11 22:10:48 sandi kernel: [   15.641627] [drm] nouveau 0000:00:12.0: Setting dpms mode 3 on lvds encoder (output 0)
May 11 22:10:48 sandi kernel: [   15.641632] [drm] nouveau 0000:00:12.0: Calling LVDS script 6:
May 11 22:10:48 sandi kernel: [   15.641636] [drm] nouveau 0000:00:12.0: 0xD64E: Parsing digital output script table
May 11 22:10:48 sandi kernel: [   15.641644] [drm] nouveau 0000:00:12.0: Setting dpms mode 3 on vga encoder (output 1)
May 11 22:10:48 sandi kernel: [   15.641648] [drm] nouveau 0000:00:12.0: Setting dpms mode 3 on TV encoder (output 2)
May 11 22:10:48 sandi kernel: [   15.689790] phy1: Selected rate control algorithm 'minstrel'
May 11 22:10:48 sandi kernel: [   15.690688] Registered led device: rt73usb-phy1::radio
May 11 22:10:48 sandi kernel: [   15.690718] Registered led device: rt73usb-phy1::assoc
May 11 22:10:48 sandi kernel: [   15.690738] Registered led device: rt73usb-phy1::quality
May 11 22:10:48 sandi kernel: [   15.692107] usbcore: registered new interface driver rt73usb
May 11 22:10:48 sandi kernel: [   15.701421] rt73usb 1-1:1.0: firmware: requesting rt73.bin
May 11 22:10:48 sandi kernel: [   15.776586] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input10
May 11 22:10:48 sandi kernel: [   15.811449] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input11
May 11 22:10:48 sandi kernel: [   15.853725] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May 11 22:10:48 sandi kernel: [   16.050135] [drm] nouveau 0000:00:12.0: Load detected on output B
May 11 22:10:48 sandi kernel: [   16.050366] [drm] nouveau 0000:00:12.0: allocated 1280x800 fb: 0x49000, bo ffff880072ed5000
May 11 22:10:48 sandi kernel: [   16.050519] fb0: nouveaufb frame buffer device
May 11 22:10:48 sandi kernel: [   16.050522] registered panic notifier
May 11 22:10:48 sandi kernel: [   16.050530] [drm] Initialized nouveau 0.0.15 20090420 for 0000:00:12.0 on minor 0
May 11 22:10:48 sandi kernel: [   16.053362] vga16fb: initializing
May 11 22:10:48 sandi kernel: [   16.053370] vga16fb: mapped to 0xffff8800000a0000
May 11 22:10:48 sandi kernel: [   16.053380] vga16fb: not registering due to another framebuffer present
May 11 22:10:48 sandi kernel: [   16.059295] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
May 11 22:10:48 sandi kernel: [   16.059304] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
May 11 22:10:48 sandi kernel: [   16.059312] hda_intel: Disable MSI for Nvidia chipset
May 11 22:10:48 sandi kernel: [   16.059348] HDA Intel 0000:00:07.0: setting latency timer to 64
May 11 22:10:49 sandi kernel: [   16.080308] [drm] nouveau 0000:00:12.0: Output LVDS-1 is running on CRTC 0 using output A
May 11 22:10:49 sandi kernel: [   16.080313] [drm] nouveau 0000:00:12.0: Calling LVDS script 2:
May 11 22:10:49 sandi kernel: [   16.080317] [drm] nouveau 0000:00:12.0: 0xD6A6: Parsing digital output script table
May 11 22:10:49 sandi kernel: [   16.260074] [drm] nouveau 0000:00:12.0: Setting dpms mode 0 on lvds encoder (output 0)
May 11 22:10:49 sandi kernel: [   16.260079] [drm] nouveau 0000:00:12.0: Calling LVDS script 5:
May 11 22:10:49 sandi kernel: [   16.260083] [drm] nouveau 0000:00:12.0: 0xD644: Parsing digital output script table
May 11 22:10:49 sandi kernel: [   16.260091] [drm] nouveau 0000:00:12.0: Output LVDS-1 is running on CRTC 0 using output A
May 11 22:10:49 sandi kernel: [   16.300273] CE: hpet increasing min_delta_ns to 15000 nsec
May 11 22:10:49 sandi kernel: [   16.335311] CE: hpet increasing min_delta_ns to 22500 nsec
May 11 22:10:49 sandi kernel: [   16.335311] CE: hpet increasing min_delta_ns to 33750 nsec
May 11 22:10:49 sandi kernel: [   16.370527] [drm] nouveau 0000:00:12.0: Setting dpms mode 0 on TV encoder (output 2)
May 11 22:10:49 sandi kernel: [   16.370532] [drm] nouveau 0000:00:12.0: Output TV-1 is running on CRTC 1 using output B
May 11 22:10:49 sandi kernel: [   16.472850] Console: switching to colour frame buffer device 90x36
May 11 22:10:49 sandi kernel: [   17.050047] [drm] nouveau 0000:00:12.0: Load detected on output B
May 11 22:10:49 sandi kernel: [   17.470044] [drm] nouveau 0000:00:12.0: Load detected on output B
May 11 22:10:49 sandi kernel: [   17.473628] [drm] nouveau 0000:00:12.0: Allocating FIFO number 1
May 11 22:10:49 sandi kernel: [   17.473942] [drm] nouveau 0000:00:12.0: nouveau_channel_alloc: initialised FIFO 1
May 11 22:10:49 sandi kernel: [   17.486573] [drm] nouveau 0000:00:12.0: Setting dpms mode 3 on lvds encoder (output 0)
May 11 22:10:49 sandi kernel: [   17.486579] [drm] nouveau 0000:00:12.0: Calling LVDS script 6:
May 11 22:10:49 sandi kernel: [   17.486584] [drm] nouveau 0000:00:12.0: 0xD64E: Parsing digital output script table
May 11 22:10:49 sandi kernel: [   17.506842] [drm] nouveau 0000:00:12.0: Output LVDS-1 is running on CRTC 0 using output A
May 11 22:10:49 sandi kernel: [   17.506846] [drm] nouveau 0000:00:12.0: Calling LVDS script 2:
May 11 22:10:49 sandi kernel: [   17.506849] [drm] nouveau 0000:00:12.0: 0xD6A6: Parsing digital output script table
May 11 22:10:50 sandi kernel: [   17.680044] [drm] nouveau 0000:00:12.0: Setting dpms mode 0 on lvds encoder (output 0)
May 11 22:10:50 sandi kernel: [   17.680048] [drm] nouveau 0000:00:12.0: Calling LVDS script 5:
May 11 22:10:50 sandi kernel: [   17.680051] [drm] nouveau 0000:00:12.0: 0xD644: Parsing digital output script table
May 11 22:10:50 sandi kernel: [   17.680057] [drm] nouveau 0000:00:12.0: Output LVDS-1 is running on CRTC 0 using output A
May 11 22:10:50 sandi kernel: [   17.680276] [drm] nouveau 0000:00:12.0: Setting dpms mode 3 on TV encoder (output 2)
May 11 22:10:50 sandi kernel: [   17.750994] [drm] nouveau 0000:00:12.0: Setting dpms mode 0 on TV encoder (output 2)
May 11 22:10:50 sandi kernel: [   17.750999] [drm] nouveau 0000:00:12.0: Output TV-1 is running on CRTC 1 using output B
May 11 22:10:50 sandi kernel: [   17.814381] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:07.0/input/input12
May 11 22:11:04 sandi kernel: [   31.710036] [drm] nouveau 0000:00:12.0: Load detected on output B
May 11 22:11:04 sandi kernel: [   32.020040] [drm] nouveau 0000:00:12.0: Load detected on output B
May 11 22:11:45 sandi kernel: [   72.850048] [drm] nouveau 0000:00:12.0: Load detected on output B
May 11 22:11:55 sandi kernel: [   83.310041] [drm] nouveau 0000:00:12.0: Load detected on output B
May 11 22:11:55 sandi kernel: [   83.311404] [drm] nouveau 0000:00:12.0: Setting dpms mode 3 on TV encoder (output 2)
May 11 22:11:55 sandi kernel: [   83.330318] [drm] nouveau 0000:00:12.0: Setting dpms mode 3 on lvds encoder (output 0)
May 11 22:11:55 sandi kernel: [   83.330324] [drm] nouveau 0000:00:12.0: Calling LVDS script 6:
May 11 22:11:55 sandi kernel: [   83.330329] [drm] nouveau 0000:00:12.0: 0xD64E: Parsing digital output script table
May 11 22:11:55 sandi kernel: [   83.350585] [drm] nouveau 0000:00:12.0: Output LVDS-1 is running on CRTC 0 using output A
May 11 22:11:55 sandi kernel: [   83.350589] [drm] nouveau 0000:00:12.0: Calling LVDS script 2:
May 11 22:11:55 sandi kernel: [   83.350592] [drm] nouveau 0000:00:12.0: 0xD6A6: Parsing digital output script table
May 11 22:11:55 sandi kernel: [   83.530034] [drm] nouveau 0000:00:12.0: Setting dpms mode 0 on lvds encoder (output 0)
May 11 22:11:55 sandi kernel: [   83.530037] [drm] nouveau 0000:00:12.0: Calling LVDS script 5:
May 11 22:11:55 sandi kernel: [   83.530040] [drm] nouveau 0000:00:12.0: 0xD644: Parsing digital output script table
May 11 22:11:55 sandi kernel: [   83.530045] [drm] nouveau 0000:00:12.0: Output LVDS-1 is running on CRTC 0 using output A
May 11 22:11:56 sandi kernel: [   83.880046] [drm] nouveau 0000:00:12.0: Load detected on output B
May 11 22:11:56 sandi kernel: [   84.200224] [drm] nouveau 0000:00:12.0: Load detected on output B
May 11 22:11:56 sandi kernel: [   84.510037] [drm] nouveau 0000:00:12.0: Load detected on output B
May 11 22:11:57 sandi kernel: [   84.820034] [drm] nouveau 0000:00:12.0: Load detected on output B
May 11 22:11:57 sandi kernel: [   85.130038] [drm] nouveau 0000:00:12.0: Load detected on output B
May 11 22:11:57 sandi kernel: [   85.520030] [drm] nouveau 0000:00:12.0: Load detected on output B
May 11 22:12:32 sandi kernel: [  119.658504] wlan0: deauthenticating from 00:11:f5:ea:43:08 by local choice (reason=3)
May 11 22:12:32 sandi kernel: [  119.661192] wlan0: direct probe to AP 00:11:f5:ea:43:08 (try 1)
May 11 22:12:32 sandi kernel: [  119.663086] wlan0: direct probe responded
May 11 22:12:32 sandi kernel: [  119.663092] wlan0: authenticate with AP 00:11:f5:ea:43:08 (try 1)
May 11 22:12:32 sandi kernel: [  119.665068] wlan0: authenticated
May 11 22:12:32 sandi kernel: [  119.665093] wlan0: associate with AP 00:11:f5:ea:43:08 (try 1)
May 11 22:12:32 sandi kernel: [  119.667439] wlan0: RX AssocResp from 00:11:f5:ea:43:08 (capab=0x411 status=0 aid=1)
May 11 22:12:32 sandi kernel: [  119.667442] wlan0: associated
May 11 22:12:32 sandi kernel: [  119.681078] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
May 11 22:12:33 sandi kernel: [  120.972171] Intel AES-NI instructions are not detected.
May 11 22:12:33 sandi kernel: [  121.033709] padlock: VIA PadLock not detected.
May 11 22:12:41 sandi kernel: [  129.980036] wlan0: no IPv6 routers present
May 11 22:13:13 sandi kernel: [  161.851317] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy1
May 11 22:27:14 sandi kernel: [ 1002.204398] ACPI: Failed to switch the brightness
May 11 22:27:14 sandi kernel: [ 1002.559264] ACPI: Failed to switch the brightness
May 11 22:27:14 sandi kernel: [ 1002.809005] ACPI: Failed to switch the brightness
May 11 22:27:15 sandi kernel: [ 1003.229805] ACPI: Failed to switch the brightness
May 11 22:27:22 sandi kernel: [ 1010.510044] Clocksource tsc unstable (delta = -166228334 ns)
May 11 22:30:33 sandi kernel: [ 1202.003454] ACPI: Failed to switch the brightness
May 11 22:30:34 sandi kernel: [ 1202.146365] ACPI: Failed to switch the brightness
May 11 22:34:30 sandi kernel: [ 1438.665798] [drm] nouveau 0000:00:12.0: PFIFO_DMA_PUSHER - Ch 1
May 11 22:34:32 sandi kernel: [ 1440.666381] __ratelimit: 9 callbacks suppressed
May 11 22:34:32 sandi kernel: [ 1440.666395] Xorg[1002]: segfault at 56a0a ip 0000000000056a0a sp 00007fffc06271d8 error 14 in Xorg[400000+1be000]
May 11 22:34:32 sandi kernel: [ 1440.701271] [drm] nouveau 0000:00:12.0: nouveau_channel_free: freeing fifo 1
May 11 22:34:35 sandi kernel: [ 1443.692516] [drm] nouveau 0000:00:12.0: Failed to idle channel 1.
May 11 22:34:36 sandi kernel: [ 1444.211111] wlan0: deauthenticating from 00:11:f5:ea:43:08 by local choice (reason=3)
May 11 22:34:37 sandi kernel: [ 1445.550048] [drm] nouveau 0000:00:12.0: Load detected on output B
May 11 22:34:37 sandi kernel: [ 1445.870050] [drm] nouveau 0000:00:12.0: Load detected on output B
May 11 22:34:37 sandi kernel: [ 1445.886616] [drm] nouveau 0000:00:12.0: Allocating FIFO number 1
May 11 22:34:37 sandi kernel: [ 1445.888504] [drm] nouveau 0000:00:12.0: nouveau_channel_alloc: initialised FIFO 1
May 11 22:34:37 sandi kernel: [ 1445.907057] [drm] nouveau 0000:00:12.0: Setting dpms mode 3 on lvds encoder (output 0)
May 11 22:34:37 sandi kernel: [ 1445.907070] [drm] nouveau 0000:00:12.0: Calling LVDS script 6:
May 11 22:34:37 sandi kernel: [ 1445.907081] [drm] nouveau 0000:00:12.0: 0xD64E: Parsing digital output script table
May 11 22:34:37 sandi kernel: [ 1445.917856] [drm] nouveau 0000:00:12.0: Output LVDS-1 is running on CRTC 0 using output A
May 11 22:34:37 sandi kernel: [ 1445.917864] [drm] nouveau 0000:00:12.0: Calling LVDS script 2:
May 11 22:34:37 sandi kernel: [ 1445.917871] [drm] nouveau 0000:00:12.0: 0xD6A6: Parsing digital output script table
May 11 22:34:38 sandi kernel: [ 1446.090260] [drm] nouveau 0000:00:12.0: Setting dpms mode 0 on lvds encoder (output 0)
May 11 22:34:38 sandi kernel: [ 1446.090271] [drm] nouveau 0000:00:12.0: Calling LVDS script 5:
May 11 22:34:38 sandi kernel: [ 1446.090280] [drm] nouveau 0000:00:12.0: 0xD644: Parsing digital output script table
May 11 22:34:38 sandi kernel: [ 1446.090294] [drm] nouveau 0000:00:12.0: Output LVDS-1 is running on CRTC 0 using output A
May 11 22:34:38 sandi kernel: [ 1446.154169] [drm] nouveau 0000:00:12.0: Setting dpms mode 0 on TV encoder (output 2)
May 11 22:34:38 sandi kernel: [ 1446.154182] [drm] nouveau 0000:00:12.0: Output TV-1 is running on CRTC 1 using output B
May 11 22:34:49 sandi kernel: [ 1457.982568] [drm] nouveau 0000:00:12.0: Load detected on output B
May 11 22:34:50 sandi kernel: [ 1458.340047] [drm] nouveau 0000:00:12.0: Load detected on output B
May 11 22:35:02 sandi kernel: [ 1470.180067] [drm] nouveau 0000:00:12.0: Load detected on output B
May 11 22:35:11 sandi kernel: [ 1480.030050] [drm] nouveau 0000:00:12.0: Load detected on output B
May 11 22:35:11 sandi kernel: [ 1480.032108] [drm] nouveau 0000:00:12.0: Setting dpms mode 3 on TV encoder (output 2)
May 11 22:35:11 sandi kernel: [ 1480.060807] [drm] nouveau 0000:00:12.0: Setting dpms mode 3 on lvds encoder (output 0)
May 11 22:35:11 sandi kernel: [ 1480.060820] [drm] nouveau 0000:00:12.0: Calling LVDS script 6:
May 11 22:35:11 sandi kernel: [ 1480.060831] [drm] nouveau 0000:00:12.0: 0xD64E: Parsing digital output script table
May 11 22:35:12 sandi kernel: [ 1480.081123] [drm] nouveau 0000:00:12.0: Output LVDS-1 is running on CRTC 0 using output A
May 11 22:35:12 sandi kernel: [ 1480.081131] [drm] nouveau 0000:00:12.0: Calling LVDS script 2:
May 11 22:35:12 sandi kernel: [ 1480.081139] [drm] nouveau 0000:00:12.0: 0xD6A6: Parsing digital output script table
May 11 22:35:12 sandi kernel: [ 1480.260055] [drm] nouveau 0000:00:12.0: Setting dpms mode 0 on lvds encoder (output 0)
May 11 22:35:12 sandi kernel: [ 1480.260065] [drm] nouveau 0000:00:12.0: Calling LVDS script 5:
May 11 22:35:12 sandi kernel: [ 1480.260072] [drm] nouveau 0000:00:12.0: 0xD644: Parsing digital output script table
May 11 22:35:12 sandi kernel: [ 1480.260085] [drm] nouveau 0000:00:12.0: Output LVDS-1 is running on CRTC 0 using output A
May 11 22:35:12 sandi kernel: [ 1480.640054] [drm] nouveau 0000:00:12.0: Load detected on output B
May 11 22:35:12 sandi kernel: [ 1480.960044] [drm] nouveau 0000:00:12.0: Load detected on output B
May 11 22:35:13 sandi kernel: [ 1481.330053] [drm] nouveau 0000:00:12.0: Load detected on output B
May 11 22:35:13 sandi kernel: [ 1481.640054] [drm] nouveau 0000:00:12.0: Load detected on output B
May 11 22:35:13 sandi kernel: [ 1481.950051] [drm] nouveau 0000:00:12.0: Load detected on output B
May 11 22:35:14 sandi kernel: [ 1482.260055] [drm] nouveau 0000:00:12.0: Load detected on output B
May 11 22:35:40 sandi kernel: [ 1508.320408] wlan0: deauthenticating from 00:11:f5:ea:43:08 by local choice (reason=3)
```

---

### Post by Interruptor on 2011-04-15
I just found a workaround for this problem:
[http://nouveau.freedesktop.org/wiki/KernelModeSetting#ForcingModes-1](http://nouveau.freedesktop.org/wiki/KernelModeSetting#ForcingModes-1)

I edited */etc/default/grub* and added
**GRUB_CMDLINE_LINUX="video=DVI-I-1:1280x1024@60 video=TV-1:d"**
(do not just copy this string, read it and understand please)
run 
**$ sudo update-grub2**
and rebooted.

---

### Post by echo6 on 2011-04-23
Hmm, I'm trying to get terminal modes greater than 640x480.  I've patched my kernel with spock's fbcondecor patch, which works fine on Intel.  On any machines that have Nvidia the tty's always default to 640x480.

I think forcing the video mode as you have suggested may help, what is the best way to identify the connector?  Nothing shows in /var/log/messages or Xorg.0.log

---

### Post by Interruptor on 2011-04-23
> **echo6 said:**
> what is the best way to identify the connector?
I didn't identify it. I was feeling lucky and just assumed that it will be something like in the example. And it was :)
But all I can tell is that it's true for GeForce 5200FX, so  be ready to boot from something external to fix this system (with chroot?).

[SIZE="1"]And yesterday there was I/O errors on the hard drive (it's almost 10 years old), so right now I'm busy preparing my external drive for complete backup. Will try later.[/SIZE]

---

