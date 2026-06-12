---
title: "NOt a laptop but it is hardware I guess"
date: 2009-01-15
forum: Hardware
---

### Post by aldea911 on 2009-01-15
I am a n00b. I just upgraded from 7.1 to 8.04 and I am not bale to use a usb stick. I tried many things that I could  find, [http://ubuntuforums.org/showthread.php?t=787523](http://ubuntuforums.org/showthread.php?t=787523) is the only thing that worked. I am able to get the items into the folder, but I click on the icon for the usb drive, it says that it can not mount, even though mounted in other place, i umount it, but still nothing. This is what I am getting. Thank you, please forgive if posted in wrong area. 
aldea911@paraspace:~$ dmesg | tail -n 50
[   48.411824] sd 2:0:0:0: Attached scsi generic sg3 type 0
[   53.186489] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   53.237182] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   53.288556] Linux agpgart interface v0.102
[   53.390593] agpgart: Detected VIA PM266/KM266 chipset
[   53.397665] agpgart: AGP aperture is 64M @ 0xe8000000
[   53.791992] irda_init()
[   53.792035] NET: Registered protocol family 23
[   53.846979] input: Power Button (FF) as /devices/virtual/input/input2
[   53.859950] ACPI: Power Button (FF) [PWRF]
[   53.860242] input: Power Button (CM) as /devices/virtual/input/input3
[   53.875922] ACPI: Power Button (CM) [PWRB]
[   53.876213] input: Sleep Button (CM) as /devices/virtual/input/input4
[   53.891886] ACPI: Sleep Button (CM) [SLPB]
[   56.264822] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[   56.264978] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   56.466822] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   57.510275] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input6
[   57.544718] parport_pc 00:0b: reported by Plug and Play ACPI
[   57.544772] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   61.161323] lp0: using parport0 (interrupt-driven).
[   61.275100] Adding 650592k swap on /dev/sda5.  Priority:-1 extents:1 across:650592k
[   61.892980] EXT3 FS on sda1, internal journal
[   63.690963] ip_tables: (C) 2000-2006 Netfilter Core Team
[   64.414081] No dock devices found.
[   66.788256] ppdev: user-space parallel port driver
[   67.051756] audit(1232049115.081:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4928 profile="/usr/sbin/cupsd" namespace="default"
[   68.968758] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   68.968772] apm: overridden by ACPI.
[   69.883813] NET: Registered protocol family 10
[   69.884739] lo: Disabled Privacy Extensions
[   71.055660] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   73.529241] Bluetooth: Core ver 2.11
[   73.530753] NET: Registered protocol family 31
[   73.530763] Bluetooth: HCI device and connection manager initialized
[   73.530771] Bluetooth: HCI socket layer initialized
[   73.653213] Bluetooth: L2CAP ver 2.9
[   73.653224] Bluetooth: L2CAP socket layer initialized
[   73.682843] Bluetooth: RFCOMM socket layer initialized
[   73.682892] Bluetooth: RFCOMM TTY layer initialized
[   73.682895] Bluetooth: RFCOMM ver 1.8
[   74.433561] NET: Registered protocol family 17
[   77.247048] [drm] Initialized drm 1.1.0 20060810
[   77.275362] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   77.276161] [drm] Initialized savage 2.4.1 20050313 on minor 0
[   77.277150] mtrr: base(0xe2000000) is not aligned on a size(0x5000000) boundary
[   77.277948] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   77.277984] agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode
[   77.278036] agpgart: Putting AGP V2 device at 0000:01:00.0 into 0x mode
[   87.990094] eth0: no IPv6 routers present

---

### Post by electrogeist on 2009-01-15
Unfortunately there is nothing USB-related in the dmesg output you posted.

---

### Post by aldea911 on 2009-01-16
I followed everything it said to use :
dmesg | tail -n 50
I can use nautilis like the other post said to use, but in computer, I am not able to click on the usb icon.  
is how I got it. What else must I do to get info on usb issues?
the other command from the other post said to try 

tail -n 100 ~/.xsession-errors

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
SESSION_MANAGER=local/paraspace:/tmp/.ICE-unix/5824
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
Shutdown failed or nothing to shut down.
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192
Window manager warning: Failed to read saved session file /home/aldea911/.metacity/sessions/default0.ms: Failed to open file '/home/aldea911/.metacity/sessions/default0.ms': No such file or directory


Tracker version 0.6.6 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority
starting HAL detection for ac adaptors...none found
E: shm.c: shm_open() failed: Permission denied
11
Throttle level is 0
Initializing nautilus-share extension
evolution-alarm-notify-Message: Setting timeout for 14833 1232064000 1232049167
evolution-alarm-notify-Message:  Thu Jan 15 17:00:00 2009

evolution-alarm-notify-Message:  Thu Jan 15 12:52:47 2009

seahorse nautilus module initialized

** (nautilus:5968): WARNING **: Unable to add monitor: Not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
  PID TTY          TIME CMD
 5948 ?        00:00:00 pulseaudio
  PID TTY          TIME CMD
evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1232064000
evolution-alarm-notify-Message: alarm.c:246: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86399 1232150400 1232064001
evolution-alarm-notify-Message:  Fri Jan 16 17:00:00 2009

evolution-alarm-notify-Message:  Thu Jan 15 17:00:01 2009


IF there are any other commands that I can use to get help, PLEASE let me know. Thank you.

---

### Post by aldea911 on 2009-01-16
And when I try to move stuff over I get 
There was an error copying the file into /mnt/wd_drive.
Error opening file '/mnt/wd_drive/Gemini & NB Riders - Have You Ever.mp3': Permission denied

So I can kind of mount it but not able to move anything

---

### Post by electrogeist on 2009-01-16
Ok sounds like you just have permissions problems!

Open up a terminal and 

$ cd /mnt
$ ls -la *

you'll see a directory listing, see line with your usb drive (wd_drive).  The part that looks something like "drwxr-x---" are the permissions, and you probably want to read up on those.  

To give Read, Write, and eXecute permissions to the User & Group you can type

$ sudo chmod ug+rwx wd_drive

and enter your password (for the administrative sudo)
 
 
If that doesn't do it and your name is not on the line you can change ownership to yourself:

$ sudo chown YOURNAME wd_drive

---

