---
title: "iPod no longer mounts in KDE/Kubuntu"
date: 2007-10-03
forum: Hardware &amp; Laptops
---

### Post by eyemou on 2007-10-03
I'm sure I am not the only one who has experienced this, but I can't quite seem to find an answer. Here is the rundown, in as much detail as possible...

I have a 5.5-gen iPod that has always automatically been detected and mounted when plugged into my desktop (Kubuntu Feisty, 7.04). No problems there, and no problems managing it via Amarok and gtkpod.

However, for some inexplicable reason, the iPod will not automount anymore. Here is the chain of events of the weird and new behavior that has transpired over the past few days.

1. I plug the iPod in, the screen lights up, and the player goes into "Do not disconnect" mode. However, Amarok cannot find the device. I look in my /media/IPOD folder, and the device is not mounted. Unable to eject the device, I unplug it and do a hard reset to convince the iPod that it is NOT connected to the PC.

2. I reboot the computer and plug the iPod in. It doesn't even light up / go into "Do not disconnect". It's as if the USB port isn't working, which is funny, as it is... I'm able to plug a USB mouse into it.

I don't have an exact cut + paste, but dmesg | tail mentioned something along the line of sense or autosense not found.

3. I install the HAL update in 'backports'.

4. Now when I plug in the iPod, it lights up, but does not mount. 'dmesg | tail' shows the following:

[FONT="Courier New"][  363.651746] sdb: Spinning up disk.....not responding...
[  712.114333] sdb : READ CAPACITY failed.
[  712.114336] sdb : status=1, message=00, host=0, driver=08
[  712.114344] sd: Current: sense key: Not Ready
[  712.114347]     Additional sense: Logical unit is in process of becoming read                    y
[  712.115588] sdb: Write Protect is off
[  712.115599] sdb: Mode Sense: 68 00 00 08
[  712.115602] sdb: assuming drive cache: write through
[  712.115756] sd 4:0:0:0: Attached scsi removable disk sdb
[  712.115835] sd 4:0:0:0: Attached scsi generic sg1 type 0[/FONT]

The device can be manually mounted ('sudo mount -t vfat /dev/sdb2 /media/IPOD'), however Amarok complains about it not having permissions to create a lockfile on the device (chmod permissions for the mountpoint are 655).

Oh, and FWIW, the device still works by itself. So at least it's not totally hosed.

There have been no hardware changes, and only one software change between the point where the device last worked, and when the troubles started. The one software update is listed above as #3 in the list. Before all of the issues began, I did intall the new Amarok (1.4.6?), in order to get album art working, but that was a few days prior, with no issues whatsoever.
 
Anyhow, I've poked around kcontrol, looking for any tool that handles automounting of media players or other USB volumes + devices, but no luck.

Any help, or further diagnostic avenues that I can pursue at this point? Could this have anything to do with the .hal-mtab & .hal-mtab-lock files in my /media/ directory?

(Oh, and if it helps any, this iPod has never seen iTunes -- Mac or Win. Some of the problems/solutions I've found online seem to hinge on that... someone using it with iTunes, and running into issues in Linux...)

I hope I've provided enough info., and have exhausted everything I could think of before asking...

Any insight GREATLY appreciated.

---

### Post by eyemou on 2007-10-03
Update: Partway there.

I plugged in the iPod and opened up "Disks & Filesystems" and manually added the device, with the following settings:

Type: VFAT
...mount point: /media/IPOD (my normal mount point)
...by name: /dev/sdb2

And under "Security and Safety", I set the device as writeable, and assigned ownership to my user account uid, and the users group.

Still no iPod icon on the desktop, but that's no huge deal.

As far as I can tell, it works... Still, it's a little puzzling. Perhaps something will be fixed with the next Kubuntu release...

---

### Post by tgalati4 on 2007-10-04
I lost my iPod auto mount in the latest Dapper kernel update.  I am running:

Linux hpubuntu 2.6.15-29-386 #1 PREEMPT Mon Sep 24 17:18:25 UTC 2007 i686 GNU/Linux

Error messages from (>banshee --debug)
Debug: [10/4/2007 2:00:56 PM] (Testing device for DAP support) - /org/freedesktop/Hal/devices/storage_serial_Apple_iPod_000A2700120417F0
Debug: [10/4/2007 2:00:56 PM] (DAP has not been added) - /org/freedesktop/Hal/devices/storage_serial_Apple_iPod_000A2700120417F0
Debug: [10/4/2007 2:00:58 PM] (Testing device for DAP support) - /org/freedesktop/Hal/devices/volume_uuid_D3CB63579816629B
Debug: [10/4/2007 2:00:58 PM] (DAP has not been added) - /org/freedesktop/Hal/devices/volume_uuid_D3CB63579816629B

---

### Post by byourg on 2007-10-07
I'm having the same problem, the box comes up the mount the usb drive but nothing happens.

Here is the dmesg list:

```
[17180213.488000] SCSI device sde: 4001425 512-byte hdwr sectors (2049 MB)
[17180213.488000] sde: Write Protect is off
[17180213.488000] sde: Mode Sense: 03 00 00 00
[17180213.488000] sde: assuming drive cache: write through
[17180213.492000] SCSI device sde: 4001425 512-byte hdwr sectors (2049 MB)
[17180213.492000] sde: Write Protect is off
[17180213.492000] sde: Mode Sense: 03 00 00 00
[17180213.492000] sde: assuming drive cache: write through
[17180213.492000]  sde: sde1
[17180213.496000] sd 1:0:0:0: Attached scsi removable disk sde
[17180213.496000] sd 1:0:0:0: Attached scsi generic sg4 type 0
[17180213.500000]   Vendor: SanDisk   Model: U3 Cruzer Micro   Rev: 3.21
[17180213.500000]   Type:   CD-ROM                             ANSI SCSI revision: 02
[17180213.500000]  1:0:0:1: Attached scsi generic sg5 type 5
[17180213.512000] usb-storage: device scan complete
[17180213.636000] sr0: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[17180213.636000] sr 1:0:0:1: Attached scsi CD-ROM sr0
[17180213.888000] cdrom: This disc doesn't have any tracks I recognize!
[17180213.948000] cdrom: This disc doesn't have any tracks I recognize!
```

and for my Ipod:

```

[17180417.784000] usb 4-6: new high speed USB device using ehci_hcd and address 5
[17180417.932000] usb 4-6: configuration #1 chosen from 2 choices
[17180417.932000] scsi2 : SCSI emulation for USB Mass Storage devices
[17180417.932000] usb-storage: device found at 5
[17180417.932000] usb-storage: waiting for device to settle before scanning
[17180422.936000]   Vendor: Apple     Model: iPod              Rev: 2.70
[17180422.936000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[17180422.936000] SCSI device sde: 2037248 512-byte hdwr sectors (1043 MB)
[17180422.936000] sde: Write Protect is off
[17180422.936000] sde: Mode Sense: 64 00 00 08
[17180422.936000] sde: assuming drive cache: write through
[17180422.940000] SCSI device sde: 2037248 512-byte hdwr sectors (1043 MB)
[17180422.940000] sde: Write Protect is off
[17180422.940000] sde: Mode Sense: 64 00 00 08
[17180422.940000] sde: assuming drive cache: write through
[17180422.940000]  sde: sde1
[17180422.944000] sd 2:0:0:0: Attached scsi removable disk sde
[17180422.944000] sd 2:0:0:0: Attached scsi generic sg4 type 0
[17180422.944000] usb-storage: device scan complete
```

anybody know a way to fix this?

---

### Post by tgalati4 on 2007-10-08
Not a fix, but a work-around:

Places-->Computer-->Double-click on iPod icon and it mounts.

This assumes that your iPod is not corrupt.  Normally no errors will show up in dmesg--but it doesn't mount automatically.

Somehow iPod automounting broke with the HAL or some other recent update (on or around 3 Oct 07).

Make sure your /etc/fstab has something similar:  (be sure to modify to reflect your device location)

/dev/sda3       /media/ipod     hfsplus rw,user,[COLOR="Red"]auto[/COLOR]  0       0

For you FAT32 formatted iPods:

/dev/sda3       /media/ipod     vfat rw,user,[COLOR="Red"]auto[/COLOR]  0       0


It could be something as simple as the recent kernel update that clobbered the fstab file and recreated it without the ipod entry.

Note to self:

>sudo cp /etc/fstab /etc/fstab_bak

---

### Post by sinaen on 2007-10-11
it doesnt show up in the computer section and i can mount the ipod 
but thats with sudo mount /dev/sdf2 /media/ipod -t vfat so that doesnt give me user rights... to copy or transfer files in amarok etc

---

