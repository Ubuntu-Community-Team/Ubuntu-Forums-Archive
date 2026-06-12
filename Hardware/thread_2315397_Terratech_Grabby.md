---
title: "Terratech Grabby"
date: 2016-02-28
forum: Hardware
---

### Post by lenberman on 2016-02-28
Not sure if this should be under Multimedia software, but ...

I have a Terratech Grabby.  I want to use it on Kubuntu 15.10.  It is shown by lsusb:
    Bus 001 Device 010: ID 0ccd:0096 TerraTec Electronic GmbH 

However, it doesn't function.  I'm not sure exactly what to post so please let me know.  Thanks for any help.

I am running 
    Linux foobar 4.2.0-27-generic #32-Ubuntu SMP Fri Jan 22 04:49:08 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

When I plug it in,  syslog shows (I've highlighted some suspicious messages)

[INDENT]Feb 28 11:37:50 foobar systemd-udevd[358]: seq 3950 '/devices/pci0000:00/0000:00:14.0/usb1/1-7' is taking a long time
Feb 28 11:38:30 foobar kernel: [ 3560.767259] usb 1-7: 2:1: cannot get min/max values for control 2 (id 2)
Feb 28 11:38:30 foobar kernel: [ 3560.767707] usb 1-7: USB disconnect, device number 12
Feb 28 11:38:31 foobar kernel: [ 3561.007061] usb 1-7: new high-speed USB device number 13 using xhci_hcd
Feb 28 11:38:31 foobar kernel: [ 3561.142550] usb 1-7: New USB device found, idVendor=0ccd, idProduct=0096
Feb 28 11:38:31 foobar kernel: [ 3561.142552] usb 1-7: New USB device strings: Mfr=2, Product=1, SerialNumber=0
Feb 28 11:38:31 foobar kernel: [ 3561.142553] usb 1-7: Product: TerraTec Grabby
Feb 28 11:38:31 foobar kernel: [ 3561.142554] usb 1-7: Manufacturer: TerraTec Electronic GmbH
Feb 28 11:38:31 foobar kernel: [ 3561.143026] em28xx: New device TerraTec Electronic GmbH TerraTec Grabby @ 480 Mbps (0ccd:0096, interface 0, class 0)
Feb 28 11:38:31 foobar kernel: [ 3561.143028] em28xx: Video interface 0 found: isoc
Feb 28 11:38:32 foobar kernel: [ 3562.206409] em28xx #0: em28xx_init_dev: em28xx_write_reg failed! retval [-5]
[COLOR="#FF0000"]Feb 28 11:38:32 foobar kernel: [ 3562.206430] em28xx: probe of 1-7:1.0 failed with error -5[/COLOR]
[/INDENT]

Strangely (to me at least) after a while, I get the following in syslog
[INDENT]Feb 28 11:37:50 foobar systemd-udevd[358]: seq 3950 '/devices/pci0000:00/0000:00:14.0/usb1/1-7' is taking a long time
Feb 28 11:38:30 foobar kernel: [ 3560.767259] usb 1-7: 2:1: cannot get min/max values for control 2 (id 2)
Feb 28 11:38:30 foobar kernel: [ 3560.767707] usb 1-7: USB disconnect, device number 12
Feb 28 11:38:31 foobar kernel: [ 3561.007061] usb 1-7: new high-speed USB device number 13 using xhci_hcd
Feb 28 11:38:31 foobar kernel: [ 3561.142550] usb 1-7: New USB device found, idVendor=0ccd, idProduct=0096
Feb 28 11:38:31 foobar kernel: [ 3561.142552] usb 1-7: New USB device strings: Mfr=2, Product=1, SerialNumber=0
Feb 28 11:38:31 foobar kernel: [ 3561.142553] usb 1-7: Product: TerraTec Grabby
Feb 28 11:38:31 foobar kernel: [ 3561.142554] usb 1-7: Manufacturer: TerraTec Electronic GmbH
Feb 28 11:38:31 foobar kernel: [ 3561.143026] em28xx: New device TerraTec Electronic GmbH TerraTec Grabby @ 480 Mbps (0ccd:0096, interface 0, class 0)
Feb 28 11:38:31 foobar kernel: [ 3561.143028] em28xx: Video interface 0 found: isoc
Feb 28 11:38:32 foobar kernel: [ 3562.206409] em28xx #0: em28xx_init_dev: em28xx_write_reg failed! retval [-5]
[COLOR="#FF0000"]Feb 28 11:38:32 foobar kernel: [ 3562.206430] em28xx: probe of 1-7:1.0 failed with error -5[/COLOR]
Feb 28 11:39:01 foobar CRON[4901]: (root) CMD (  [ -x /usr/lib/php5/sessionclean ] && /usr/lib/php5/sessionclean)
Feb 28 11:39:50 foobar systemd-udevd[358]: seq 3950 '/devices/pci0000:00/0000:00:14.0/usb1/1-7' killed
Feb 28 11:40:12 foobar kernel: [ 3662.147067] usb 1-7: 2:1: cannot get min/max values for control 2 (id 2)
Feb 28 11:40:12 foobar kernel: [ 3662.147288] usb 1-7: USB disconnect, device number 13
Feb 28 11:40:12 foobar kernel: [ 3662.386926] usb 1-7: new high-speed USB device number 14 using xhci_hcd
Feb 28 11:40:12 foobar kernel: [ 3662.522442] usb 1-7: New USB device found, idVendor=0ccd, idProduct=0096
Feb 28 11:40:12 foobar kernel: [ 3662.522444] usb 1-7: New USB device strings: Mfr=2, Product=1, SerialNumber=0
Feb 28 11:40:12 foobar kernel: [ 3662.522445] usb 1-7: Product: TerraTec Grabby
Feb 28 11:40:12 foobar kernel: [ 3662.522446] usb 1-7: Manufacturer: TerraTec Electronic GmbH
Feb 28 11:40:12 foobar kernel: [ 3662.522906] em28xx: New device TerraTec Electronic GmbH TerraTec Grabby @ 480 Mbps (0ccd:0096, interface 0, class 0)
Feb 28 11:40:12 foobar kernel: [ 3662.522908] em28xx: Video interface 0 found: isoc
Feb 28 11:40:12 foobar kernel: [ 3662.522926] em28xx: chip ID is em2860
Feb 28 11:40:12 foobar kernel: [ 3662.647339] em2860 #0: EEPROM ID = 1a eb 67 95, EEPROM hash = 0x77daab95
Feb 28 11:40:12 foobar kernel: [ 3662.647340] em2860 #0: EEPROM info:
Feb 28 11:40:12 foobar kernel: [ 3662.647341] em2860 #0:        AC97 audio (5 sample rates)
Feb 28 11:40:12 foobar kernel: [ 3662.647341] em2860 #0:        500mA max power
Feb 28 11:40:12 foobar kernel: [ 3662.647342] em2860 #0:        Table at offset 0x06, strings=0x229e, 0x346a, 0x0000
Feb 28 11:40:12 foobar kernel: [ 3662.647343] em2860 #0: Identified as Terratec Grabby (card=67)
Feb 28 11:40:12 foobar kernel: [ 3662.647344] em2860 #0: analog set to isoc mode.
Feb 28 11:40:12 foobar kernel: [ 3662.647408] em2860 #0: Registering V4L2 extension
Feb 28 11:40:12 foobar systemd-udevd[358]: worker [4879] terminated by signal 9 (Killed)
Feb 28 11:40:12 foobar systemd-udevd[358]: worker [4879] failed while handling '/devices/pci0000:00/0000:00:14.0/usb1/1-7'
[COLOR="#FF0000"]Feb 28 11:40:12 foobar systemd-udevd[4943]: Process '/usr/sbin/alsactl -E HOME=/var/run/alsa restore 1' failed with exit code 99.[/COLOR]
Feb 28 11:40:13 foobar kernel: [ 3663.038835] saa7115 7-0025: saa7113 found @ 0x4a (em2860 #0)
Feb 28 11:40:13 foobar mtp-probe: checking bus 1, device 14: "/sys/devices/pci0000:00/0000:00:14.0/usb1/1-7"
Feb 28 11:40:13 foobar mtp-probe: bus: 1, device: 14 was not an MTP device
Feb 28 11:40:13 foobar systemd-udevd[4943]: Process '/usr/sbin/alsactl -E HOME=/var/run/alsa restore 1' failed with exit code 99.
Feb 28 11:40:13 foobar kernel: [ 3663.810163] em2860 #0: Config register raw data: 0x50
Feb 28 11:40:13 foobar kernel: [ 3663.834081] em2860 #0: AC97 vendor ID = 0x83847652
Feb 28 11:40:13 foobar kernel: [ 3663.846103] em2860 #0: AC97 features = 0x6a90
Feb 28 11:40:13 foobar kernel: [ 3663.846104] em2860 #0: Sigmatel audio processor detected (stac 9752)
Feb 28 11:40:14 foobar mtp-probe: checking bus 1, device 14: "/sys/devices/pci0000:00/0000:00:14.0/usb1/1-7"
Feb 28 11:40:14 foobar mtp-probe: bus: 1, device: 14 was not an MTP device
Feb 28 11:40:14 foobar systemd-udevd[4943]: Process '/usr/sbin/alsactl -E HOME=/var/run/alsa restore 1' failed with exit code 99.
Feb 28 11:40:14 foobar rtkit-daemon[1710]: Supervising 2 threads of 1 processes of 1 users.
Feb 28 11:40:14 foobar rtkit-daemon[1710]: Successfully made thread 5022 of process 1709 (n/a) owned by '1000' RT at priority 5.
Feb 28 11:40:14 foobar rtkit-daemon[1710]: Supervising 3 threads of 1 processes of 1 users.
Feb 28 11:40:16 foobar kernel: [ 3666.244827] em2860 #0: V4L2 video device registered as video0
Feb 28 11:40:16 foobar kernel: [ 3666.244829] em2860 #0: V4L2 VBI device registered as vbi0
Feb 28 11:40:16 foobar kernel: [ 3666.244831] em2860 #0: V4L2 extension successfully initialized
[/INDENT]


When I try vlc I get
[INDENT]Your input can't be opened:
VLC is unable to open the MRL 'v4l2:///dev/vbi0'. Check the log for details.
Your input can't be opened:
VLC is unable to open the MRL 'v4l2:///dev/vbi0'. Check the log for details.
Your input can't be opened:
VLC is unable to open the MRL 'v4l2:///dev/vbi0'. Check the log for details.
Your input can't be opened:
VLC is unable to open the MRL 'v4l2:///dev/vbi0'. Check the log for details.
v/vbi0'. Check the log for details
[/INDENT]

Running vlc from the terminal, it outputs these messages (which I believe is the log)

[INDENT][00007f4dd4002a48] v4l2 access error: not a video capture device
[00007f4ddc000d18] core input error: open of `v4l2:///dev/vbi0' failed
[00007f4dd4002e98] v4l2 demux error: not a video capture device
[/INDENT]

---

