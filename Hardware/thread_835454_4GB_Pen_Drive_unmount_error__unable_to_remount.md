---
title: "4GB Pen Drive unmount error / unable to remount"
date: 2008-06-20
forum: Hardware
---

### Post by angelsguitar on 2008-06-20
Hi. I have a 4GB Pen Drive that, ocassionally, gives the following problems.  First, when I open nautilus to check its contents, I notice that it hangs for a while, like reading or scaning the drive.  Then, when it finally shows its contents, I try to write something on the drive, and everything seems to work alright.  But when I try to unmount it, it gives the following error:

An application is preventing the volume 'ANGEL4GB' from being unmounted

After a while, it unmounts automatically, but when I take it out and put it in the USB slot again, the computer does not detect it.  Running lsusb just hangs (I have to press Crtl+Z to cancel the operation).  Also, if I try to connect any other USB PenDrive after all this has happened, it is not detected.

This only happens with this 4GB Pen Drive and another 16 GB Pen drive I sent back after buying it (I thought the drive was defective); I have another 2 GB PenDrive that works without problems.

Anyone has an idea of what is happening? Can it be due to an incompatible pen drive? Thanks for your help in advance.

---

### Post by Odrodzona-Sarmacja on 2008-06-21
Do "sudo mount -a" after connecting your hd and see if it helps any.

---

### Post by angelsguitar on 2008-06-21
> **Odrodzona-Sarmacja said:**
> Do "sudo mount -a" after connecting your hd and see if it helps any.

I did "sudo mount -a" on the terminal, but nothing.  Still the same problem.  Thanks, though.

---

### Post by angelsguitar on 2008-06-21
> **angelsguitar said:**
> Hi. I have a 4GB Pen Drive that, ocassionally, gives the following problems.  First, when I open nautilus to check its contents, I notice that it hangs for a while, like reading or scaning the drive.  Then, when it finally shows its contents, I try to write something on the drive, and everything seems to work alright.  But when I try to unmount it, it gives the following error:

An application is preventing the volume 'ANGEL4GB' from being unmounted

After a while, it unmounts automatically, but when I take it out and put it in the USB slot again, the computer does not detect it.  Running lsusb just hangs (I have to press Crtl+Z to cancel the operation).  Also, if I try to connect any other USB PenDrive after all this has happened, it is not detected.

This only happens with this 4GB Pen Drive and another 16 GB Pen drive I sent back after buying it (I thought the drive was defective); I have another 2 GB PenDrive that works without problems.

Anyone has an idea of what is happening? Can it be due to an incompatible pen drive? Thanks for your help in advance.

Running dmesg | grep usb returns a lot of things, but the one that caught my attention was "device not accepting address 5, error -110" and a couple of other similar errors. Anyway, here's the complete output after reconnecting the pendrive:

angelsguitar@Toshiba:~$ dmesg | grep usb
[ 27.237325] usbcore: registered new interface driver usbfs
[ 27.237357] usbcore: registered new interface driver hub
[ 27.269208] usbcore: registered new device driver usb
[ 28.884773] usb usb1: configuration #1 chosen from 1 choice
[ 29.044687] usb usb2: configuration #1 chosen from 1 choice
[ 29.160664] usb usb3: configuration #1 chosen from 1 choice
[ 833.437903] usb 3-3: new high speed USB device using ehci_hcd and address 2
[ 833.579115] usb 3-3: configuration #1 chosen from 1 choice
[ 833.701178] usbcore: registered new interface driver libusual
[ 833.749648] usbcore: registered new interface driver usb-storage
[ 833.750083] usb-storage: device found at 2
[ 833.750086] usb-storage: waiting for device to settle before scanning
[ 838.748389] usb-storage: device scan complete
[ 909.223131] usb 3-3: USB disconnect, address 2
[ 916.812977] usb 3-4: new high speed USB device using ehci_hcd and address 3
[ 916.954266] usb 3-4: configuration #1 chosen from 1 choice
[ 916.981067] usb-storage: device found at 3
[ 916.981072] usb-storage: waiting for device to settle before scanning
[ 921.980344] usb-storage: device scan complete
[ 1054.329063] usb 3-4: USB disconnect, address 3
[ 1171.666965] usb 1-2: new full speed USB device using ohci_hcd and address 2
[ 1171.876646] usb 1-2: configuration #1 chosen from 1 choice
[ 1171.903045] usb-storage: device found at 2
[ 1171.903050] usb-storage: waiting for device to settle before scanning
[ 1176.902301] usb-storage: device scan complete
[ 1263.197853] usb 1-2: USB disconnect, address 2
[ 1273.119967] usb 3-3: new high speed USB device using ehci_hcd and address 5
[ 1273.259126] usb 3-3: configuration #1 chosen from 1 choice
[ 1273.288048] usb-storage: device found at 5
[ 1273.288054] usb-storage: waiting for device to settle before scanning
[ 1278.287335] usb-storage: device scan complete
[ 1374.680913] usb 3-3: reset high speed USB device using ehci_hcd and address 5
[ 1390.230929] usb 3-3: device not accepting address 5, error -110
[ 1390.342892] usb 3-3: reset high speed USB device using ehci_hcd and address 5
[ 1405.892903] usb 3-3: device not accepting address 5, error -110
[ 1405.948918] usb 3-3: USB disconnect, address 5
[ 2475.021997] usb 3-3: new high speed USB device using ehci_hcd and address 6
[ 2490.572024] usb 3-3: device not accepting address 6, error -110
[ 2490.683987] usb 3-3: new high speed USB device using ehci_hcd and address 7
[ 2506.234005] usb 3-3: device not accepting address 7, error -110
[ 2506.345964] usb 3-3: new high speed USB device using ehci_hcd and address 8
[ 2516.773957] usb 3-3: device not accepting address 8, error -110
[ 2516.885917] usb 3-3: new high speed USB device using ehci_hcd and address 9
[ 2527.313904] usb 3-3: device not accepting address 9, error -110

Any help or suggestion on this matter is really appreciated. Thanks.

---

### Post by Odrodzona-Sarmacja on 2008-06-21
I would check bios for usb settings.

---

### Post by AJB2K3 on 2008-06-21
I get this from time to time.
Only real solution I found is a full restart.

---

### Post by angelsguitar on 2008-06-21
> **Odrodzona-Sarmacja said:**
> I would check bios for usb settings.

I checked the BIOS and the only USB setting I saw was "USB Legacy Support".  It was enabled (the description said that it should be enabled for systems that are not aware of USB devices - old systems like DOS and Unix) but I changed it to disable; let's see how it goes.

I would also look if there are any BIOS updates, but, in the meantime, is there any other USB setting I should look for?

---

### Post by angelsguitar on 2008-06-21
> **angelsguitar said:**
> I checked the BIOS and the only USB setting I saw was "USB Legacy Support".  It was enabled (the description said that it should be enabled for systems that are not aware of USB devices - old systems like DOS and Unix) but I changed it to disable; let's see how it goes.

I would also look if there are any BIOS updates, but, in the meantime, is there any other USB setting I should look for?

Changed the setting, but still the same problem.  Any ideas?

---

### Post by agas on 2008-06-21
I have same, when sudo 

-----------------------------------
agas@agas-home:~$ sudo mount -a
[sudo] password for agas: 
mount: mount point udf,iso9660 does not exist
mount: mount point auto does not exist
mount: mount point 0 does not exist
mount: mount point 0 does not exist
mount: mount point 0 does not exist
mount: mount point 0 does not exist
mount: unknown filesystem type '0'
mount: mount point 0 does not exist
mount: mount point 0 does not exist
mount: mount point ntfs-3g does not exist
ntfs-3g: Failed to access volume '/dev/hdb2': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.
ntfs-3g: Failed to access volume '/dev/hdb1': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.
ntfs-3g: Failed to access volume '/dev/sdb2': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.
mount: mount point /media/sda9 does not exist
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sdd1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdd1 /media/rw -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdd1 /media/rw ntfs-3g force 0 0
ntfs-3g: Failed to access volume '/dev/sdd2': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
ntfs-3g: Failed to access volume '/dev/hdc1': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.
ntfs-3g: Failed to access volume '/dev/hdb5': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.
agas@agas-home:~$ /sbin/mount.ntfs-3g--help
bash: /sbin/mount.ntfs-3g--help: No such file or directory
agas@agas-home:~$ /sbin/mount.ntfs-3g --help

ntfs-3g 1.2216 external FUSE 27 - Third Generation NTFS Driver

Copyright (C) 2006-2008 Szabolcs Szakacsits
Copyright (C) 2005-2007 Yura Pakhuchiy

Usage:    ntfs-3g <device|image_file> <mount_point> [-o option[,...]]

Options:  ro (read-only mount), force, remove_hiberfile, locale=,
          uid=, gid=, umask=, fmask=, dmask=, streams_interface=.
          Please see the details in the manual.

Example:  ntfs-3g /dev/sda1 /mnt/win -o force

Ntfs-3g news, support and information:  [http://ntfs-3g.org](http://ntfs-3g.org)
agas@agas-home:~$ 
------------------------
so upset with those..

---

### Post by smo0th on 2008-06-21
try ```
sudo mount -t vfat /dev/sdb1 -o force
``` or ```
sudo umount /dev/sdb1
``` depending on the case.

---

### Post by angelsguitar on 2008-06-22
OK, I found some info on a site named Linux USB ([http://www.linux-usb.org/]("http://www.linux-usb.org/")) about the "device not accepting address XXX" message I get.  I tried appending the "noapic" option to the kernel instruction on menu.lst and rebooted. Well, the usb drive worked well with it, but I lost my wireless connection (it would just hang in there unable to connect to my router).  A couple of times my laptop even froze on bootup.

I believe the problem is with my BIOS and its APIC settings.  I noticed that my laptop gives this message when booting:

```
MP-BIOS bug: 8254 timer not connected to IO-APIC 
```

The problem is I cannot use the "noapic" solution because I would loose my network connection and my system becomes unstable.

Is there any other workaround to this?

---

### Post by angelsguitar on 2008-09-01
Well, believe it or not, still looking for a good fix to this...

At least I found something [here]("http://ubuntuforums.org/showthread.php?t=89266") that seems to be the cause, and offers a quick fix. Rather old, but seems to work so far, although not the ideal solution.

Seems that the problem is a BIOS related issue with the way it handles usb 2.0 high speed transfers.  This seems to affect ATI chipsets with the SB400 models (not sure if there are others).  I checked for a BIOS update but still nothing.  So disabling the ehci_hcd module (and/or blacklisting it) provides a quick and temporary fix, at the cost of losing high speed transfer.

The thing is that this only happens with Ubuntu; I tried a couple of other distros: OpenSuse 11, Mandriva 2008.1, Fedora 9, 64 Studio (based on Debian-etch) and pendrive works without problems.  But with those distros I had other problems, like no sound and/or printing problems.  So I'll stick with Ubuntu for now, and hope for the best on the updates.

Does anybody know if there's a bug report filed for this?

---

