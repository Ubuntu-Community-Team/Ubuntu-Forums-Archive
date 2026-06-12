---
title: "[SOLVED] udev rules"
date: 2008-09-03
forum: General Help
---

### Post by sonic_275 on 2008-09-03
Hi,

Since my upgrade to hardy, the rules in folder /etc/udev/rules.d/ aren't applied when I connect my Palm Pilot.

Before this upgrade, I synced my Palm Pilot with my usb cradle. I had designed an udev rule, starting automatically a command-line jpilot-sync as I pushed the Hotsync button.

Since this upgrade, as I push the Hotsync button, getting the handheld to be detected by the kernel, devices /dev/ttyusb0 and /dev/ttyusb1 are created without difficulty, but the udevd dameon doesn't apply the rules in /etc/udev/rules.d/ Actually, they aren't even read, the `stat` command confirms the last access date isn't modified after device connection or diconnection, neither is it at boot time. I'm completely sure this wasn't the case on gutsy...

I can still synch my Palm manually using the device /dev/ttyusbx. My problem is that I can't to any automatic synch. Other side-effect, the symbolic link /dev/pilot is never created (it's on of the rules from /etc/udev/rules.d/)

The creation of devices /dev/ttyusb0 and /dev/ttyusb1 shows udev still works a minima, and the command `sudo udevmonitor -e` logs Palm connections and disconnections. But it isn't read as I (dis)connect a mouse or an other usb device, which seems to indicate this problem isn't specific to my handheld ou handhelds in general.

Has anything changed in udev behavior on Hardy ? Couldn't find anything like that in my searches. Or is this a problem on my system config ?

Thanks for your help.

---

### Post by sonic_275 on 2008-09-05
Up ?

---

### Post by Vivaldi Gloria on 2008-09-05
I don't know much about your problem but at least I'll bump it up.

> **sonic_275 said:**
>  Has anything changed in udev behavior on Hardy ? 

Yes. I remeber comparing udev rules of Hardy to those of Gutsy. Some rules were changed. Unfortunately I don't remember more.

> the symbolic link /dev/pilot is never created 

There is a rule for that in 60-symlinks.rules. 

```
# Create /dev/pilot symlink for Palm Pilots
KERNEL=="ttyUSB*", ATTRS{product}=="Palm Handheld*|Handspring *|palmOne Handheld", \
					SYMLINK+="pilot"
```

Don't you have it?

If you want you can also try a command like

```
udevtest /block/sda
```

to find out what udev does with your device. It may help you. Unfortunately you need to use the sysfs (i.e. /sys) name of the device. 

> I had designed an udev rule, starting automatically a command-line jpilot-sync as I pushed the Hotsync button.

I'm curious about it. Can you paste it?

---

### Post by sonic_275 on 2008-09-08
> **Vivaldi Gloria said:**
> Yes. I remeber comparing udev rules of Hardy to those of Gutsy. Some rules were changed. Unfortunately I don't remember more.

My problem isn't that the udev rules have changed, it's that /etc/udev/rules.d/ doesn't seem to be read by udevd anymore...

>  There is a rule for that in 60-symlinks.rules. Don't you have it?

Yes, I have it, but as any other rule in the folder, it isn't applied when my Palm is connected.

> If you want you can also try a command like

```
udevtest /block/sda
```

to find out what udev does with your device. It may help you. Unfortunately you need to use the sysfs (i.e. /sys) name of the device. 

Not sure about what's the right path to use. Tried out that one :

```
$ udevtest /bus/usb-serial/devices/ttyUSB1/
This program is for debugging only, it does not run any program,
specified by a RUN key. It may show incorrect results, because
some values may be different, or not available at a simulation run.

parse_file: reading '/etc/udev/rules.d/05-options.rules' as rules file
parse_file: reading '/etc/udev/rules.d/05-udev-early.rules' as rules file
parse_file: reading '/etc/udev/rules.d/20-names.rules' as rules file
parse_file: reading '/etc/udev/rules.d/30-cdrom_id.rules' as rules file
parse_file: reading '/etc/udev/rules.d/40-basic-permissions.rules' as rules file
parse_file: reading '/etc/udev/rules.d/40-permissions.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-fuse.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-hplip.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-libmtp7.rules' as rules file
parse_file: reading '/etc/udev/rules.d/50-bluez-pcmcia-support.rules' as rules file
parse_file: reading '/etc/udev/rules.d/50-libpisock9.rules' as rules file
parse_file: reading '/etc/udev/rules.d/50-xserver-xorg-input-wacom.rules' as rules file
parse_file: reading '/etc/udev/rules.d/55-hpmud.rules' as rules file
parse_file: reading '/etc/udev/rules.d/60-persistent-input.rules' as rules file
parse_file: reading '/etc/udev/rules.d/60-persistent-storage-tape.rules' as rules file
parse_file: reading '/etc/udev/rules.d/60-persistent-storage.rules' as rules file
parse_file: reading '/etc/udev/rules.d/60-symlinks.rules' as rules file
parse_file: reading '/etc/udev/rules.d/61-persistent-storage-edd.rules' as rules file
parse_file: reading '/etc/udev/rules.d/65-dmsetup.rules' as rules file
parse_file: reading '/etc/udev/rules.d/70-persistent-cd.rules' as rules file
parse_file: reading '/etc/udev/rules.d/70-persistent-net.rules' as rules file
parse_file: reading '/etc/udev/rules.d/75-cd-aliases-generator.rules' as rules file
parse_file: reading '/etc/udev/rules.d/75-persistent-net-generator.rules' as rules file
parse_file: reading '/etc/udev/rules.d/80-programs.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-alsa.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-brltty.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-hdparm.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-hplj10xx.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-hwclock.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-ifupdown.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-pcmcia.rules' as rules file
parse_file: reading '/etc/udev/rules.d/90-modprobe.rules' as rules file
parse_file: reading '/etc/udev/rules.d/95-hal.rules' as rules file
parse_file: reading '/etc/udev/rules.d/95-pilot.rules' as rules file
parse_file: reading '/etc/udev/rules.d/95-udev-late.rules' as rules file
import_uevent_var: import into environment: 'DRIVER=visor'
udevtest: looking at device '/devices/pci0000:00/0000:00:02.2/usb3/3-1/3-1.4/3-1.4:1.0/ttyUSB1' from subsystem 'usb-serial'
udevtest: run: 'socket:/org/freedesktop/hal/udev_event'
udevtest: run: 'socket:/org/kernel/udev/monitor'
```

> I'm curious about it. Can you paste it?

Here are the rule and the associated scripts :

```
$ cat /etc/udev/rules.d/95-pilot.rules 
KERNEL=="ttyUSB*", SYSFS{product}=="Palm Handheld*|Handspring *|Ordinateur de poche Palm*", \
DEVPATH=="/class/tty/ttyUSB[13]", RUN+="/home/user/bin/palm-sync-root "

$ cat /home/user/bin/palm-sync-root
#!/bin/sh
/bin/su - user /home/user/bin/palm-sync

$ cat /home/user/bin/palm-sync
#!/bin/sh
jpilot-sync > /dev/null || exit
#(other personnal stuff going on here, transforming my personnal calendar into iCal format and publishing it to a remote server)
```

---

### Post by Vivaldi Gloria on 2008-09-08
> **sonic_275 said:**
> My problem isn't that the udev rules have changed, it's that /etc/udev/rules.d/ doesn't seem to be read by udevd anymore...

Hmm. I don't know what you can do. But trying

```
sudo update-rc.d udev default
```

wouldn't hurt. 


> Not sure about what's the right path to use. Tried out that one :

Normally it should spit out a lot more lines. There is really something wrong (provided that the path is right). Also try

```
sudo udevcontrol --start_exec_queue
sudo udevcontrol --reload_rules
```

and then connecting the palm pilot.

To be honest if I were in your shoes than I'd have installed a clean hardy by now. 


> Here are the rule and the associated scripts :

Thanks mate.

---

### Post by sonic_275 on 2008-09-08
> **Vivaldi Gloria said:**
> Hmm. I don't know what you can do. But trying

```
sudo update-rc.d udev default
```

wouldn't hurt. 

```
$ sudo update-rc.d udev defaults
 System startup links for /etc/init.d/udev already exist.
```

> Normally it should spit out a lot more lines. There is really something wrong (provided that the path is right). Also try

```
sudo udevcontrol --start_exec_queue
sudo udevcontrol --reload_rules
```

Didn't seem to do a thing.
Thanks for your help anyway.

Here is what I get on syslog as my Palm is connected ; hard for me to identify the problem :

```
Sep  8 19:29:41 SI3-ACB kernel: [2271421.035180] usb 3-1.4: new full speed USB device using ehci_hcd and address 39
Sep  8 19:29:41 SI3-ACB udevd[2720]: msg_queue_insert: seq 3546 queued, 'add' 'usb'
Sep  8 19:29:41 SI3-ACB kernel: [2271421.144419] usb 3-1.4: configuration #1 chosen from 1 choice
Sep  8 19:29:41 SI3-ACB kernel: [2271421.145343] visor 3-1.4:1.0: Handspring Visor / Palm OS converter detected
Sep  8 19:29:41 SI3-ACB kernel: [2271421.145481] usb 3-1.4: Handspring Visor / Palm OS converter now attached to ttyUSB1
Sep  8 19:29:41 SI3-ACB kernel: [2271421.145533] usb 3-1.4: Handspring Visor / Palm OS converter now attached to ttyUSB2
Sep  8 19:29:41 SI3-ACB udevd-event[15004]: udev_rules_get_name: rule applied, '3-1.4' becomes 'bus/usb/003/039'
Sep  8 19:29:41 SI3-ACB udevd-event[15004]: udev_db_get_device: no db file to read /dev/.udev/db/\x2fdevices\x2fpci0000:00\x2f0000:00:02.2\x2fusb3\x2f3-1\x2f3-1.4: No such file or directory
Sep  8 19:29:41 SI3-ACB udevd-event[15004]: udev_node_add: creating device node '/dev/bus/usb/003/039', major=189, minor=294, mode=0664, uid=0, gid=20
Sep  8 19:29:41 SI3-ACB udevd-event[15004]: name_index: creating index: '/dev/.udev/names/bus\x2fusb\x2f003\x2f039/\x2fdevices\x2fpci0000:00\x2f0000:00:02.2\x2fusb3\x2f3-1\x2f3-1.4'
Sep  8 19:29:41 SI3-ACB udevd-event[15004]: pass_env_to_socket: passed 319 bytes to socket '/org/freedesktop/hal/udev_event', 
Sep  8 19:29:41 SI3-ACB udevd-event[15004]: pass_env_to_socket: passed -1 bytes to socket '/org/kernel/udev/monitor', 
Sep  8 19:29:41 SI3-ACB udevd-event[15004]: udev_event_run: seq 3546 finished with 0
Sep  8 19:29:41 SI3-ACB udevd[2720]: udev_event_run: seq 3546 forked, pid [15004], 'add' 'usb', 0 seconds old
Sep  8 19:29:41 SI3-ACB udevd[2720]: msg_queue_insert: seq 3547 queued, 'add' 'usb_endpoint'
Sep  8 19:29:41 SI3-ACB udevd[2720]: udev_done: seq 3546, pid [15004] exit with 0, 0 seconds old
Sep  8 19:29:41 SI3-ACB udevd-event[15007]: udev_rules_get_name: no node name set, will use kernel name 'usbdev3.39_ep00'
Sep  8 19:29:41 SI3-ACB udevd-event[15007]: udev_db_get_device: no db file to read /dev/.udev/db/\x2fdevices\x2fpci0000:00\x2f0000:00:02.2\x2fusb3\x2f3-1\x2f3-1.4\x2fusb_endpoint\x2fusbdev3.39_ep00: No such file or directory
Sep  8 19:29:41 SI3-ACB udevd-event[15007]: udev_node_add: creating device node '/dev/usbdev3.39_ep00', major=254, minor=30, mode=0664, uid=0, gid=20
Sep  8 19:29:41 SI3-ACB udevd-event[15007]: name_index: creating index: '/dev/.udev/names/usbdev3.39_ep00/\x2fdevices\x2fpci0000:00\x2f0000:00:02.2\x2fusb3\x2f3-1\x2f3-1.4\x2fusb_endpoint\x2fusbdev3.39_ep00'
Sep  8 19:29:41 SI3-ACB udevd-event[15007]: pass_env_to_socket: passed 285 bytes to socket '/org/freedesktop/hal/udev_event', 
Sep  8 19:29:41 SI3-ACB udevd-event[15007]: pass_env_to_socket: passed -1 bytes to socket '/org/kernel/udev/monitor', 
Sep  8 19:29:41 SI3-ACB udevd-event[15007]: udev_event_run: seq 3547 finished with 0
Sep  8 19:29:41 SI3-ACB udevd[2720]: udev_event_run: seq 3547 forked, pid [15007], 'add' 'usb_endpoint', 0 seconds old
Sep  8 19:29:41 SI3-ACB udevd[2720]: msg_queue_insert: seq 3548 queued, 'add' 'usb'
Sep  8 19:29:41 SI3-ACB udevd[2720]: udev_done: seq 3547, pid [15007] exit with 0, 0 seconds old
Sep  8 19:29:41 SI3-ACB udevd-event[15009]: run_program: '/sbin/modprobe -Q usb:v0830p0060d0100dc00dsc00dp00icFFisc00ip00'
Sep  8 19:29:41 SI3-ACB NetworkManager: <debug> [1220894981.441942] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_830_60_303056354141473431543450'). 
Sep  8 19:29:41 SI3-ACB udevd[2720]: udev_event_run: seq 3548 forked, pid [15009], 'add' 'usb', 0 seconds old
Sep  8 19:29:41 SI3-ACB udevd[2720]: msg_queue_insert: seq 3549 queued, 'add' 'usb-serial'
Sep  8 19:29:41 SI3-ACB udevd[2720]: msg_queue_insert: seq 3550 queued, 'add' 'tty'
Sep  8 19:29:41 SI3-ACB udevd[2720]: msg_queue_insert: seq 3551 queued, 'add' 'usb-serial'
Sep  8 19:29:41 SI3-ACB udevd[2720]: msg_queue_insert: seq 3552 queued, 'add' 'tty'
Sep  8 19:29:41 SI3-ACB udevd[2720]: msg_queue_insert: seq 3553 queued, 'add' 'usb_endpoint'
Sep  8 19:29:41 SI3-ACB udevd[2720]: msg_queue_insert: seq 3554 queued, 'add' 'usb_endpoint'
Sep  8 19:29:41 SI3-ACB udevd[2720]: msg_queue_insert: seq 3555 queued, 'add' 'usb_endpoint'
Sep  8 19:29:41 SI3-ACB udevd[2720]: msg_queue_insert: seq 3556 queued, 'add' 'usb_endpoint'
Sep  8 19:29:41 SI3-ACB udevd-event[15009]: run_program: '/sbin/modprobe' returned with status 1
Sep  8 19:29:41 SI3-ACB udevd-event[15009]: pass_env_to_socket: passed 344 bytes to socket '/org/freedesktop/hal/udev_event', 
Sep  8 19:29:41 SI3-ACB udevd-event[15009]: pass_env_to_socket: passed -1 bytes to socket '/org/kernel/udev/monitor', 
Sep  8 19:29:41 SI3-ACB udevd-event[15009]: udev_event_run: seq 3548 finished with -1
Sep  8 19:29:41 SI3-ACB udevd[2720]: udev_done: seq 3548, pid [15009] exit with 1, 0 seconds old
Sep  8 19:29:41 SI3-ACB udevd-event[15011]: pass_env_to_socket: passed 213 bytes to socket '/org/freedesktop/hal/udev_event', 
Sep  8 19:29:41 SI3-ACB udevd-event[15011]: pass_env_to_socket: passed -1 bytes to socket '/org/kernel/udev/monitor', 
Sep  8 19:29:41 SI3-ACB udevd-event[15011]: udev_event_run: seq 3549 finished with 0
Sep  8 19:29:41 SI3-ACB udevd[2720]: udev_event_run: seq 3549 forked, pid [15011], 'add' 'usb-serial', 0 seconds old
Sep  8 19:29:41 SI3-ACB udevd-event[15012]: pass_env_to_socket: passed 213 bytes to socket '/org/freedesktop/hal/udev_event', 
Sep  8 19:29:41 SI3-ACB udevd-event[15012]: pass_env_to_socket: passed -1 bytes to socket '/org/kernel/udev/monitor', 
Sep  8 19:29:41 SI3-ACB udevd-event[15012]: udev_event_run: seq 3551 finished with 0
Sep  8 19:29:41 SI3-ACB NetworkManager: <debug> [1220894981.539361] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_830_60_303056354141473431543450_if0'). 
Sep  8 19:29:41 SI3-ACB udevd[2720]: udev_event_run: seq 3551 forked, pid [15012], 'add' 'usb-serial', 0 seconds old
Sep  8 19:29:41 SI3-ACB udevd-event[15013]: udev_rules_get_name: no node name set, will use kernel name 'usbdev3.39_ep81'
Sep  8 19:29:41 SI3-ACB udevd-event[15013]: udev_db_get_device: no db file to read /dev/.udev/db/\x2fdevices\x2fpci0000:00\x2f0000:00:02.2\x2fusb3\x2f3-1\x2f3-1.4\x2f3-1.4:1.0\x2fusb_endpoint\x2fusbdev3.39_ep81: No such file or directory
Sep  8 19:29:41 SI3-ACB udevd-event[15013]: udev_node_add: creating device node '/dev/usbdev3.39_ep81', major=254, minor=31, mode=0664, uid=0, gid=20
Sep  8 19:29:41 SI3-ACB udevd-event[15013]: name_index: creating index: '/dev/.udev/names/usbdev3.39_ep81/\x2fdevices\x2fpci0000:00\x2f0000:00:02.2\x2fusb3\x2f3-1\x2f3-1.4\x2f3-1.4:1.0\x2fusb_endpoint\x2fusbdev3.39_ep81'
Sep  8 19:29:41 SI3-ACB udevd-event[15013]: pass_env_to_socket: passed 305 bytes to socket '/org/freedesktop/hal/udev_event', 
Sep  8 19:29:41 SI3-ACB udevd-event[15013]: pass_env_to_socket: passed -1 bytes to socket '/org/kernel/udev/monitor', 
Sep  8 19:29:41 SI3-ACB udevd-event[15013]: udev_event_run: seq 3553 finished with 0
Sep  8 19:29:41 SI3-ACB udevd[2720]: udev_event_run: seq 3553 forked, pid [15013], 'add' 'usb_endpoint', 0 seconds old
Sep  8 19:29:41 SI3-ACB udevd-event[15014]: udev_rules_get_name: no node name set, will use kernel name 'usbdev3.39_ep02'
Sep  8 19:29:41 SI3-ACB udevd-event[15014]: udev_db_get_device: no db file to read /dev/.udev/db/\x2fdevices\x2fpci0000:00\x2f0000:00:02.2\x2fusb3\x2f3-1\x2f3-1.4\x2f3-1.4:1.0\x2fusb_endpoint\x2fusbdev3.39_ep02: No such file or directory
Sep  8 19:29:41 SI3-ACB udevd-event[15014]: udev_node_add: creating device node '/dev/usbdev3.39_ep02', major=254, minor=32, mode=0664, uid=0, gid=20
Sep  8 19:29:41 SI3-ACB udevd-event[15014]: name_index: creating index: '/dev/.udev/names/usbdev3.39_ep02/\x2fdevices\x2fpci0000:00\x2f0000:00:02.2\x2fusb3\x2f3-1\x2f3-1.4\x2f3-1.4:1.0\x2fusb_endpoint\x2fusbdev3.39_ep02'
Sep  8 19:29:41 SI3-ACB udevd-event[15014]: pass_env_to_socket: passed 305 bytes to socket '/org/freedesktop/hal/udev_event', 
Sep  8 19:29:41 SI3-ACB udevd-event[15014]: pass_env_to_socket: passed -1 bytes to socket '/org/kernel/udev/monitor', 
Sep  8 19:29:41 SI3-ACB udevd-event[15014]: udev_event_run: seq 3554 finished with 0
Sep  8 19:29:41 SI3-ACB udevd[2720]: udev_event_run: seq 3554 forked, pid [15014], 'add' 'usb_endpoint', 0 seconds old
Sep  8 19:29:41 SI3-ACB udevd-event[15015]: udev_rules_get_name: no node name set, will use kernel name 'usbdev3.39_ep86'
Sep  8 19:29:41 SI3-ACB udevd-event[15015]: udev_db_get_device: no db file to read /dev/.udev/db/\x2fdevices\x2fpci0000:00\x2f0000:00:02.2\x2fusb3\x2f3-1\x2f3-1.4\x2f3-1.4:1.0\x2fusb_endpoint\x2fusbdev3.39_ep86: No such file or directory
Sep  8 19:29:41 SI3-ACB udevd-event[15015]: udev_node_add: creating device node '/dev/usbdev3.39_ep86', major=254, minor=33, mode=0664, uid=0, gid=20
Sep  8 19:29:41 SI3-ACB udevd-event[15015]: name_index: creating index: '/dev/.udev/names/usbdev3.39_ep86/\x2fdevices\x2fpci0000:00\x2f0000:00:02.2\x2fusb3\x2f3-1\x2f3-1.4\x2f3-1.4:1.0\x2fusb_endpoint\x2fusbdev3.39_ep86'
Sep  8 19:29:41 SI3-ACB udevd-event[15015]: pass_env_to_socket: passed 305 bytes to socket '/org/freedesktop/hal/udev_event', 
Sep  8 19:29:41 SI3-ACB udevd-event[15015]: pass_env_to_socket: passed -1 bytes to socket '/org/kernel/udev/monitor', 
Sep  8 19:29:41 SI3-ACB udevd-event[15015]: udev_event_run: seq 3555 finished with 0
Sep  8 19:29:41 SI3-ACB udevd[2720]: udev_event_run: seq 3555 forked, pid [15015], 'add' 'usb_endpoint', 0 seconds old
Sep  8 19:29:41 SI3-ACB udevd-event[15016]: udev_rules_get_name: no node name set, will use kernel name 'usbdev3.39_ep07'
Sep  8 19:29:41 SI3-ACB udevd-event[15016]: udev_db_get_device: no db file to read /dev/.udev/db/\x2fdevices\x2fpci0000:00\x2f0000:00:02.2\x2fusb3\x2f3-1\x2f3-1.4\x2f3-1.4:1.0\x2fusb_endpoint\x2fusbdev3.39_ep07: No such file or directory
Sep  8 19:29:41 SI3-ACB udevd-event[15016]: udev_node_add: creating device node '/dev/usbdev3.39_ep07', major=254, minor=34, mode=0664, uid=0, gid=20
Sep  8 19:29:41 SI3-ACB udevd-event[15016]: name_index: creating index: '/dev/.udev/names/usbdev3.39_ep07/\x2fdevices\x2fpci0000:00\x2f0000:00:02.2\x2fusb3\x2f3-1\x2f3-1.4\x2f3-1.4:1.0\x2fusb_endpoint\x2fusbdev3.39_ep07'
Sep  8 19:29:41 SI3-ACB udevd-event[15016]: pass_env_to_socket: passed 305 bytes to socket '/org/freedesktop/hal/udev_event', 
Sep  8 19:29:41 SI3-ACB udevd-event[15016]: pass_env_to_socket: passed -1 bytes to socket '/org/kernel/udev/monitor', 
Sep  8 19:29:41 SI3-ACB udevd-event[15016]: udev_event_run: seq 3556 finished with 0
Sep  8 19:29:41 SI3-ACB udevd[2720]: udev_event_run: seq 3556 forked, pid [15016], 'add' 'usb_endpoint', 0 seconds old
Sep  8 19:29:41 SI3-ACB udevd[2720]: udev_done: seq 3549, pid [15011] exit with 0, 0 seconds old
Sep  8 19:29:41 SI3-ACB udevd[2720]: udev_done: seq 3551, pid [15012] exit with 0, 0 seconds old
Sep  8 19:29:41 SI3-ACB udevd[2720]: udev_done: seq 3553, pid [15013] exit with 0, 0 seconds old
Sep  8 19:29:41 SI3-ACB udevd[2720]: udev_done: seq 3554, pid [15014] exit with 0, 0 seconds old
Sep  8 19:29:41 SI3-ACB udevd[2720]: udev_done: seq 3555, pid [15015] exit with 0, 0 seconds old
Sep  8 19:29:41 SI3-ACB udevd[2720]: udev_done: seq 3556, pid [15016] exit with 0, 0 seconds old
Sep  8 19:29:41 SI3-ACB udevd-event[15017]: udev_rules_get_name: no node name set, will use kernel name 'ttyUSB1'
Sep  8 19:29:41 SI3-ACB udevd-event[15017]: udev_db_get_device: no db file to read /dev/.udev/db/\x2fdevices\x2fpci0000:00\x2f0000:00:02.2\x2fusb3\x2f3-1\x2f3-1.4\x2f3-1.4:1.0\x2fttyUSB1\x2ftty\x2fttyUSB1: No such file or directory
Sep  8 19:29:41 SI3-ACB udevd-event[15017]: udev_node_add: creating device node '/dev/ttyUSB1', major=188, minor=1, mode=0664, uid=0, gid=20
Sep  8 19:29:41 SI3-ACB udevd-event[15017]: name_index: creating index: '/dev/.udev/names/ttyUSB1/\x2fdevices\x2fpci0000:00\x2f0000:00:02.2\x2fusb3\x2f3-1\x2f3-1.4\x2f3-1.4:1.0\x2fttyUSB1\x2ftty\x2fttyUSB1'
Sep  8 19:29:41 SI3-ACB udevd-event[15017]: pass_env_to_socket: passed 269 bytes to socket '/org/freedesktop/hal/udev_event', 
Sep  8 19:29:41 SI3-ACB udevd-event[15017]: pass_env_to_socket: passed -1 bytes to socket '/org/kernel/udev/monitor', 
Sep  8 19:29:41 SI3-ACB udevd-event[15017]: udev_event_run: seq 3550 finished with 0
Sep  8 19:29:41 SI3-ACB udevd[2720]: udev_event_run: seq 3550 forked, pid [15017], 'add' 'tty', 0 seconds old
Sep  8 19:29:41 SI3-ACB udevd-event[15020]: udev_rules_get_name: no node name set, will use kernel name 'ttyUSB2'
Sep  8 19:29:41 SI3-ACB udevd-event[15020]: udev_db_get_device: no db file to read /dev/.udev/db/\x2fdevices\x2fpci0000:00\x2f0000:00:02.2\x2fusb3\x2f3-1\x2f3-1.4\x2f3-1.4:1.0\x2fttyUSB2\x2ftty\x2fttyUSB2: No such file or directory
Sep  8 19:29:41 SI3-ACB udevd-event[15020]: udev_node_add: creating device node '/dev/ttyUSB2', major=188, minor=2, mode=0664, uid=0, gid=20
Sep  8 19:29:41 SI3-ACB udevd-event[15020]: name_index: creating index: '/dev/.udev/names/ttyUSB2/\x2fdevices\x2fpci0000:00\x2f0000:00:02.2\x2fusb3\x2f3-1\x2f3-1.4\x2f3-1.4:1.0\x2fttyUSB2\x2ftty\x2fttyUSB2'
Sep  8 19:29:41 SI3-ACB udevd-event[15020]: pass_env_to_socket: passed 269 bytes to socket '/org/freedesktop/hal/udev_event', 
Sep  8 19:29:41 SI3-ACB udevd-event[15020]: pass_env_to_socket: passed -1 bytes to socket '/org/kernel/udev/monitor', 
Sep  8 19:29:41 SI3-ACB udevd-event[15020]: udev_event_run: seq 3552 finished with 0
Sep  8 19:29:41 SI3-ACB udevd[2720]: udev_event_run: seq 3552 forked, pid [15020], 'add' 'tty', 0 seconds old
Sep  8 19:29:41 SI3-ACB udevd[2720]: udev_done: seq 3550, pid [15017] exit with 0, 0 seconds old
Sep  8 19:29:41 SI3-ACB udevd[2720]: udev_done: seq 3552, pid [15020] exit with 0, 0 seconds old
Sep  8 19:29:41 SI3-ACB NetworkManager: <debug> [1220894981.605875] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_830_60_303056354141473431543450_if0_serial_usb_1'). 
Sep  8 19:29:41 SI3-ACB NetworkManager: <debug> [1220894981.611402] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_830_60_303056354141473431543450_if0_serial_usb_2'). 
```

---

### Post by unutbu on 2008-09-08
I do not know how to solve your udev problem -- I had a similar problem with a udev camera script: [http://ubuntuforums.org/showthread.php?t=818960&highlight=fun+udev](http://ubuntuforums.org/showthread.php?t=818960&highlight=fun+udev)

However, note that Hardy uses relatime as a default mount option. (See [http://lwn.net/Articles/244829/](http://lwn.net/Articles/244829/)). This may make checking atimes an unreliable method of checking if the udev rule file is getting read. Instead perhaps add something like
```

env > ~/udev.out

```
to your ~/bin/palm-sync-root script. Check the contents of udev.out to make sure your PATH is sufficient too. (For example, is jpilot-sync in the PATH?)

---

### Post by sonic_275 on 2008-09-09
> **unutbu said:**
> However, note that Hardy uses relatime as a default mount option. (See [http://lwn.net/Articles/244829/](http://lwn.net/Articles/244829/)). This may make checking atimes an unreliable method of checking if the udev rule file is getting read.

Oops, didn't know about that. I never guessed there could be a problem in my rule since the rule didn't seem to be even read.

Thanks to your advice, I made further tests and figured out what was wrong : since upgrade to hardy, no device matches the ```
DEVPATH=="/class/tty/ttyUSB[13]"
``` in my rule.

Instead, I put ```
DEVPATH=="*/tty/ttyUSB[13]"
``` and it now works again.

Problem solved, thank you.

---

