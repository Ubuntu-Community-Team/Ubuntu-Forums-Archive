---
title: "HP laser jet printer quit working after uninstall ImageMagick"
date: 2017-01-01
forum: Hardware
---

### Post by RogerDavis on 2017-01-01
Right after I uninstalled ImageMagick I can no longer print.  I get error message about "unplugged or turned off" in status.  I have checked this carefully, switched cable, etc.  no help.  Printer is turned on, panel on printer works.

Also, printer functions in Windoze, NOT in Ubuntu.

I found some troubleshooting info on another printer problem, Terminal output is below.  I see some odd lines, highlighted in [COLOR="#0000FF"]blue[/COLOR]

```
----------------------------
roger@roger-desktop:~$ lsmod | grep usb
usblp                  20480  0
usb_storage            69632  1 uas
usbhid                 49152  1
hid                   118784  6 hid_generic,usbhid,hid_logitech_dj,hid_logitech_hidpp
roger@roger-desktop:~$ tail -f /var/log/syslog
Jan  1 04:30:38 roger-desktop com.canonical.MediaScanner2.Extractor[1848]: Extracting metadata from /media/roger/USB DRIVE/Roger/Ebay pics/DSCF0973.JPG.
Jan  1 04:30:38 roger-desktop com.canonical.MediaScanner2.Extractor[1848]: Extracting metadata from /media/roger/USB DRIVE/Roger/Ebay pics/DSCF0972.JPG.
Jan  1 04:30:38 roger-desktop com.canonical.MediaScanner2.Extractor[1848]: Extracting metadata from /media/roger/USB DRIVE/Roger/Ebay pics/DSCF0971.JPG.
Jan  1 04:30:38 roger-desktop com.canonical.MediaScanner2.Extractor[1848]: Extracting metadata from /media/roger/USB DRIVE/Roger/Ebay pics/DSCF0970.JPG.
[COLOR="#0000FF"]Jan  1 04:32:34 roger-desktop org.gnome.Terminal[1848]: ** (gnome-terminal-server:4408): WARNING **: Unable to set locale modifiers with XSetLocaleModifiers()[/COLOR]
Jan  1 04:33:43 roger-desktop kernel: [ 1745.337019] usb 3-3: USB disconnect, device number 4
Jan  1 04:33:43 roger-desktop udev-configure-printer[4447]: remove /devices/pci0000:00/0000:00:14.0/usb3/3-3
J[COLOR="#0000FF"]an  1 04:33:43 roger-desktop systemd[1]: printer.target: Unit not needed anymore. Stopping.
Jan  1 04:33:43 roger-desktop systemd[1]: Stopped target Printer.
Jan  1 04:33:45 roger-desktop gnome-session[2014]: (gnome-software:2114): Gs-WARNING **: failed to get updates: no results to show
Jan  1 04:34:58 roger-desktop kernel: [ 1821.002133] usb 3-3: new high-speed USB device number 5 using xhci_hcd[/COLOR]
Jan  1 04:34:58 roger-desktop kernel: [ 1821.158967] usb 3-3: New USB device found, idVendor=03f0, idProduct=332a
Jan  1 04:34:58 roger-desktop kernel: [ 1821.158973] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jan  1 04:34:58 roger-desktop kernel: [ 1821.158977] usb 3-3: Product: HP Color LaserJet Pro MFP M177fw
Jan  1 04:34:58 roger-desktop kernel: [ 1821.158979] usb 3-3: Manufacturer: Hewlett-Packard
Jan  1 04:34:58 roger-desktop kernel: [ 1821.158991] usb 3-3: SerialNumber: CNG6J1J7WD
Jan  1 04:34:58 roger-desktop kernel: [ 1821.159972] usblp 3-3:1.1: usblp2: USB Bidirectional printer dev 5 if 1 alt 0 proto 2 vid 0x03F0 pid 0x332A
Jan  1 04:34:58 roger-desktop root: loading HP Device 003 005
Jan  1 04:34:59 roger-desktop python: io/hpmud/musb.c 2179: [4462] hpmud_make_usb_uri() bus=003 dev=005
Jan  1 04:34:59 roger-desktop python: io/hpmud/musb.c 2276: hpmud_make_usb_uri() uri=hp:/usb/HP_Color_LaserJet_Pro_MFP_M177fw?serial=CNG6J1J7WD bytes_read=58
Jan  1 04:34:59 roger-desktop colord[1197]: (colord:1197): Cd-WARNING **: CdMain: failed to emit DeviceAdded: failed to register object: An object is already exported for the interface org.freedesktop.ColorManager.Device at /org/freedesktop/ColorManager/devices/sysfs_Hewlett_Packard_HP_Color_LaserJet_Pro_MFP_M177fw
Jan  1 04:34:59 roger-desktop systemd[1]: Starting Automatic USB/Bluetooth printer setup (-devices-pci0000:00-0000:00:14.0-usb3-3\x2d3)...
Jan  1 04:34:59 roger-desktop systemd[1]: Reached target Printer.
Jan  1 04:34:59 roger-desktop udev-configure-printer[4483]: add /devices/pci0000:00/0000:00:14.0/usb3/3-3
Jan  1 04:34:59 roger-desktop udev-configure-printer[4483]: device devpath is /devices/pci0000:00/0000:00:14.0/usb3/3-3
[COLOR="#0000FF"]Jan  1 04:34:59 roger-desktop udev-configure-printer[4483]: MFG:Hewlett-Packard MDL:HP Color LaserJet Pro MFP M177fw SERN:- serial:CNG6J1J7WD
Jan  1 04:35:02 roger-desktop gnome-session[2014]: (gnome-software:2114): Gs-WARNING **: failed to get updates: no results to show
Jan  1 04:35:03 roger-desktop colord-sane: io/hpmud/musb.c 2093: Invalid usb_open: Permission denied
Jan  1 04:35:04 roger-desktop udev-configure-printer[4483]: IPP request 16395 failed (1280)
Jan  1 04:35:04 roger-desktop systemd[1]: udev-configure-printer@-devices-pci0000:00-0000:00:14.0-usb3-3\x2d3.service: Control process exited, code=exited status=1
Jan  1 04:35:04 roger-desktop systemd[1]: Failed to start Automatic USB/Bluetooth printer setup (-devices-pci0000:00-0000:00:14.0-usb3-3\x2d3).
Jan  1 04:35:04 roger-desktop systemd[1]: udev-configure-printer@-devices-pci0000:00-0000:00:14.0-usb3-3\x2d3.service: Unit entered failed state.
Jan  1 04:35:04 roger-desktop systemd[1]: udev-configure-printer@-devices-pci0000:00-0000:00:14.0-usb3-3\x2d3.service: Failed with result 'exit-code'.[/COLOR]
Jan  1 04:35:05 roger-desktop smartd[1010]: Device: /dev/sda [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 118 to 112
Jan  1 04:36:02 roger-desktop AptDaemon: INFO: Quitting due to inactivity
Jan  1 04:36:02 roger-desktop AptDaemon: INFO: Quitting was requested
Jan  1 04:36:02 roger-desktop org.debian.apt[1056]: 04:36:02 AptDaemon [INFO]: Quitting due to inactivity
Jan  1 04:36:02 roger-desktop org.debian.apt[1056]: 04:36:02 AptDaemon [INFO]: Quitting was requested
Jan  1 04:36:02 roger-desktop dbus[1056]: [system] Activating service name='org.debian.apt' (using servicehelper)
Jan  1 04:36:03 roger-desktop AptDaemon: INFO: Initializing daemon
Jan  1 04:36:03 roger-desktop org.debian.apt[1056]: 04:36:03 AptDaemon [INFO]: Initializing daemon
Jan  1 04:36:03 roger-desktop dbus[1056]: [system] Successfully activated service 'org.debian.apt'
Jan  1 04:36:03 roger-desktop AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Jan  1 04:36:03 roger-desktop org.debian.apt[1056]: /usr/lib/python3/dist-packages/aptdaemon/worker/pkworker.py:35: PyGIWarning: PackageKitGlib was imported without specifying a version first. Use gi.require_version('PackageKitGlib', '1.0') before import to ensure that the right version gets loaded.
Jan  1 04:36:03 roger-desktop org.debian.apt[1056]:   from gi.repository import PackageKitGlib as pk
Jan  1 04:36:03 roger-desktop org.debian.apt[1056]: 04:36:03 AptDaemon.PackageKit [INFO]: Initializing PackageKit compat layer
^C
roger@roger-desktop:~$ lsusb
Bus 002 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 001 Device 003: ID 057b:0000 Y-E Data, Inc. FlashBuster-U Floppy
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 03f0:332a Hewlett-Packard 
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
roger@roger-desktop:~$ 
roger@roger-desktop:~$ ls -l /dev/usb/lp* /dev/bus/usb/*/*
crw-rw-r--  1 root root 189,   0 Jan  1 04:04 /dev/bus/usb/001/001
crw-rw-r--  1 root root 189,   1 Jan  1 04:04 /dev/bus/usb/001/002
crw-rw-r--  1 root root 189,   2 Jan  1 04:05 /dev/bus/usb/001/003
crw-rw-r--  1 root root 189,   3 Jan  1 04:05 /dev/bus/usb/001/004
crw-rw-r--  1 root root 189, 128 Jan  1 04:04 /dev/bus/usb/002/001
crw-rw-r--  1 root root 189, 129 Jan  1 04:04 /dev/bus/usb/002/002
crw-rw-r--  1 root root 189, 130 Jan  1 04:05 /dev/bus/usb/002/003
crw-rw-r--  1 root root 189, 256 Jan  1 04:04 /dev/bus/usb/003/001
crw-rw-r--  1 root root 189, 257 Jan  1 04:05 /dev/bus/usb/003/002
crw-rw-r--+ 1 root lp   189, 260 Jan  1 04:34 /dev/bus/usb/003/005
crw-rw-r--  1 root root 189, 384 Jan  1 04:04 /dev/bus/usb/004/001
crw-rw-r--  1 root root 189, 512 Jan  1 04:04 /dev/bus/usb/005/001
crw-rw-r--  1 root root 189, 640 Jan  1 04:04 /dev/bus/usb/006/001
crw-rw----  1 root lp   180,   2 Jan  1 04:34 /dev/usb/lp2
roger@roger-desktop:~$ sudo usb_printerid /dev/usb/lp0
[sudo] password for roger: 
[COLOR="#0000FF"]Error: No such file or directory: can't open '/dev/usb/lp0'
roger@roger-desktop:~$ sudo usb_printerid /dev/usb/lp1
Error: No such file or directory: can't open '/dev/usb/lp1'[/COLOR]
roger@roger-desktop:~$ hp-info -i

HP Linux Imaging and Printing System (ver. 3.16.2)
Device Information Utility ver. 5.2

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


hp:/usb/HP_Color_LaserJet_Pro_MFP_M177fw?serial=CNG6J1J7WD

Device Parameters (dynamic data):
  Parameter                     Value(s)                                                  
  ----------------------------  ----------------------------------------------------------
  agent1-ack                    False                                                     
  agent1-desc                   Black toner cartridge                                     
  agent1-dvc                    0                                                         
  agent1-health                 0                                                         
  agent1-health-desc            Good/OK                                                   
  agent1-hp-ink                 False                                                     
  agent1-id                     0                                                         
  agent1-kind                   4                                                         
  agent1-known                  False                                                     
  agent1-level                  90                                                        
  agent1-level-trigger          0                                                         
  agent1-sku                    CF350A                                                    
  agent1-type                   1                                                         
  agent1-virgin                 False                                                     
  agent2-ack                    False                                                     
  agent2-desc                   Cyan toner cartridge                                      
  agent2-dvc                    0                                                         
  agent2-health                 0                                                         
  agent2-health-desc            Good/OK                                                   
  agent2-hp-ink                 False                                                     
  agent2-id                     0                                                         
  agent2-kind                   4                                                         
  agent2-known                  False                                                     
  agent2-level                  30                                                        
  agent2-level-trigger          0                                                         
  agent2-sku                    CF351A                                                    
  agent2-type                   4                                                         
  agent2-virgin                 False                                                     
  agent3-ack                    False                                                     
  agent3-desc                   Magenta toner cartridge                                   
  agent3-dvc                    0                                                         
  agent3-health                 0                                                         
  agent3-health-desc            Good/OK                                                   
  agent3-hp-ink                 False                                                     
  agent3-id                     0                                                         
  agent3-kind                   4                                                         
  agent3-known                  False                                                     
  agent3-level                  20                                                        
  agent3-level-trigger          0                                                         
  agent3-sku                    CF353A                                                    
  agent3-type                   5                                                         
  agent3-virgin                 False                                                     
  agent4-ack                    False                                                     
  agent4-desc                   Yellow toner cartridge                                    
  agent4-dvc                    0                                                         
  agent4-health                 0                                                         
  agent4-health-desc            Good/OK                                                   
  agent4-hp-ink                 False                                                     
  agent4-id                     0                                                         
  agent4-kind                   4                                                         
  agent4-known                  False                                                     
  agent4-level                  20                                                        
  agent4-level-trigger          0                                                         
  agent4-sku                    CF352A                                                    
  agent4-type                   6                                                         
  agent4-virgin                 False                                                     
  agent5-ack                    False                                                     
  agent5-desc                   Invalid/missing                                           
  agent5-dvc                    0                                                         
  agent5-health                 0                                                         
  agent5-health-desc            Good/OK                                                   
  agent5-hp-ink                 False                                                     
  agent5-id                     0                                                         
  agent5-kind                   0                                                         
  agent5-known                  False                                                     
  agent5-level                  100                                                       
  agent5-level-trigger          0                                                         
  agent5-sku                    CE314A                                                    
  agent5-type                   0                                                         
  agent5-virgin                 False                                                     
  back-end                      hp                                                        
  cups-printers                 ['Hewlett-Packard-HP-Color-LaserJet-Pro-MFP-M177fw']      
  cups-uri                      hp:/usb/HP_Color_LaserJet_Pro_MFP_M177fw?serial=CNG6J1J7WD
  dev-file                                                                                
  device-state                  1                                                         
  device-uri                    hp:/usb/HP_Color_LaserJet_Pro_MFP_M177fw?serial=CNG6J1J7WD
  deviceid                      MFG:Hewlett-Packard;MDL:HP Color LaserJet Pro MFP         
                                M177fwMD:ACLCL,CMD,ZJS,URF,PCLm,PJL;CLS:PRINTER;DES:HP    
                                Color LaserJet P MFP                                      
                                M177fw;FWR:R:20160525;LEDISIS:USB#ff#04#0CICID:HPLJPCLMSV1
                                V1;                                                       
  error-state                   0                                                         
  fax-uri                       hpfax:/usb/HP_Color_LaserJet_Pro_MFP_M177fw?serial=CNG6J1J
                                7WD                                                       
  host                                                                                    
  in-tray1                      1                                                         
  is-hp                         True                                                      
  panel                         0                                                         
  panel-line1                                                                             
  panel-line2                                                                             
  port                          1                                                         
  r                             0                                                         
  rg                            000                                                       
  rr                            000000                                                    
  rs                            000000000                                                 
  scan-uri                      hpaio:/usb/HP_Color_LaserJet_Pro_MFP_M177fw?serial=CNG6J1J
                                7WD                                                       
  serial                        CNG6J1J7WD                                                
  status-code                   1000                                                      
  status-desc                   Idle                                                      

Model Parameters (static data):
  Parameter                     Value(s)                                                  
  ----------------------------  ----------------------------------------------------------
  align-type                    0                                                         
  clean-type                    0                                                         
  color-cal-type                0                                                         
  copy-type                     0                                                         
  embedded-server-type          1                                                         
  fax-type                      7                                                         
  fw-download                   False                                                     
  icon                          hp_color_laserjet_cp2025.png                              
  io-mfp-mode                   1                                                         
  io-mode                       1                                                         
  io-support                    14                                                        
  job-storage                   0                                                         
  linefeed-cal-type             0                                                         
  model                         HP_Color_LaserJet_Pro_MFP_M177fw                          
  model-ui                      HP Color LaserJet Pro MFP m177fw                          
  model1                        HP Color LaserJet Pro MPF M177fw                          
  monitor-type                  0                                                         
  panel-check-type              0                                                         
  pcard-type                    0                                                         
  plugin                        1                                                         
  plugin-reason                 65                                                        
  power-settings                0                                                         
  pq-diag-type                  0                                                         
  r-type                        0                                                         
  r0-agent1-kind                4                                                         
  r0-agent1-sku                 CE311A                                                    
  r0-agent1-type                4                                                         
  r0-agent2-kind                4                                                         
  r0-agent2-sku                 CE310A                                                    
  r0-agent2-type                1                                                         
  r0-agent3-kind                4                                                         
  r0-agent3-sku                 CE313A                                                    
  r0-agent3-type                5                                                         
  r0-agent4-kind                4                                                         
  r0-agent4-sku                 CE312A                                                    
  r0-agent4-type                6                                                         
  scan-src                      3                                                         
  scan-type                     5                                                         
  status-battery-check          0                                                         
  status-dynamic-counters       0                                                         
  status-type                   10                                                        
  support-released              True                                                      
  support-subtype               2202411                                                   
  support-type                  2                                                         
  support-ver                   3.13.11                                                   
  tech-class                    ['Hbpl1']                                                 
  tech-subclass                 ['Color']                                                 
  tech-type                     4                                                         
  usb-pid                       13098                                                     
  usb-vid                       1008                                                      
  wifi-config                   3                                                         

Status History (most recent first):
  Date/Time             Code   Status Description                        User      Job ID  
  --------------------  -----  ----------------------------------------  --------  --------
  01/01/17 04:40:09     1000   Idle                                      roger     0       
[COLOR="#0000FF"]  01/01/17 04:07:35     5012   Device communication error                roger     0       [/COLOR]


Done.
roger@roger-desktop:~$ hp-makeuri <Bus>:<Device>
bash: syntax error near unexpected token `newline'
roger@roger-desktop:~$ lpinfo -v
[COLOR="#0000FF"]lpinfo: cups-deviced failed to execute.[/COLOR]
roger@roger-desktop:~$ hp-makeuri 03f0:332a

HP Linux Imaging and Printing System (ver. 3.16.2)
Device URI Creation Utility ver. 5.0

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

[COLOR="#0000FF"]error: Device not found[/COLOR]
roger@roger-desktop:~$ 
```
------------------------------------------------------------------------------------------

---

### Post by RogerDavis on 2017-01-01
Maybe fixed - reinstalled CUPS, seems ok at least for now.

How does ImageMagik tie into this?  Do I need it?  If I uninstall it and again reinstall CUPS will all be ok, or will I create other problems?

---

### Post by SeijiSensei on 2017-01-01
I just ran "sudo apt-get remove imagemagick" ona 14.04 Kubuntu machine and a 16.04 Server installation.  It only offered to remove the imagemagick package itself.  CUPS appears in the suggested list but not as a dependency either.
```

$ dpkg -s imagemagick
Package: imagemagick
Status: install ok installed
Priority: optional
Section: graphics
Installed-Size: 449
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: foreign
Version: 8:6.7.7.10-6ubuntu3.3
Depends: libc6 (>= 2.2.5), libmagickcore5 (>= 8:6.7.7.10), libmagickwand5 (>= 8:6.7.7.10), hicolor-icon-theme
Recommends: libmagickcore5-extra, ghostscript, netpbm
Suggests: imagemagick-doc, autotrace, cups-bsd | lpr | lprng, curl, enscript, ffmpeg, gimp, gnuplot, grads, groff-base, hp2xx, html2ps, libwmf-bin, mplayer, povray, radiance, sane-utils, texlive-base-bin, transfig, xdg-utils, ufraw-batch
```

I almost always install or remove software from the command line with apt-get.  That way you can see exactly which packages will be installed or removed as dependencies and can intervene if needed.

Anyway I'm glad that reinstalling CUPS solved your problem!

[Imagemagick]("http://www.imagemagick.org/script/index.php") is a powerful suite of command-line tools that can perform all sorts of transformations on graphical images.  I use it from time to time to rescale images or create thumbnails for my websites. If you never edit images, you're not likely to need it, but it's pretty small so it's worth keeping around just in case.  

In general most programs are pretty small.  The largest items on my workstation are the media players mpv (20 MB) and clementine (14 MB).  Unless you are really short on disk space, there is little value to be gained by removing installed programs.

---

