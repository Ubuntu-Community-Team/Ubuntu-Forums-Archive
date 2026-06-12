---
title: "External USB Drive auto-mounted but unable to read contents in 16.04"
date: 2016-12-27
forum: Hardware
---

### Post by markhamjoseph on 2016-12-27
Hi All,

I've got a weird problem on one of my ubuntu computers, of which i have 3. All 3 have ubuntu 16.04 installed.

When I attach a USB drive, I get the following message in nautilus: 

This location could not be displayed. 
You do not have the permissions necessary to view the contents of 400Gb-Partition

lsblk output

joseph@Inspiron-3521:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 465.8G  0 disk 
&#9500;&#9472;sda1   8:1    0   350M  0 part 
&#9500;&#9472;sda2   8:2    0     3G  0 part 
&#9500;&#9472;sda3   8:3    0 454.7G  0 part /
&#9500;&#9472;sda4   8:4    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0   7.8G  0 part [SWAP]
sdb      8:16   0 465.8G  0 disk 
&#9500;&#9472;sdb1   8:17   0  50.1G  0 part 
&#9500;&#9472;sdb2   8:18   0     1K  0 part 
&#9500;&#9472;sdb3   8:19   0 413.7G  0 part /media/joseph/400Gb-Partition
&#9492;&#9472;sdb5   8:21   0     2G  0 part 
sr0     11:0    1  1024M  0 rom 


syslog output ( dunno if this helps )

Dec 27 08:57:59 Inspiron-3521 kernel: [10977.187879] usb 3-4: new high-speed USB device number 8 using xhci_hcd
Dec 27 08:57:59 Inspiron-3521 kernel: [10977.316740] usb 3-4: New USB device found, idVendor=14cd, idProduct=6116
Dec 27 08:57:59 Inspiron-3521 kernel: [10977.316745] usb 3-4: New USB device strings: Mfr=1, Product=3, SerialNumber=2
Dec 27 08:57:59 Inspiron-3521 kernel: [10977.316748] usb 3-4: Product: USB Mass Storage Device
Dec 27 08:57:59 Inspiron-3521 kernel: [10977.316750] usb 3-4: Manufacturer: Generic     
Dec 27 08:57:59 Inspiron-3521 kernel: [10977.316752] usb 3-4: SerialNumber: 116AC2101219
Dec 27 08:57:59 Inspiron-3521 kernel: [10977.317151] usb-storage 3-4:1.0: USB Mass Storage device detected
Dec 27 08:57:59 Inspiron-3521 kernel: [10977.317273] scsi host11: usb-storage 3-4:1.0
Dec 27 08:57:59 Inspiron-3521 mtp-probe: checking bus 3, device 8: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-4"
Dec 27 08:57:59 Inspiron-3521 mtp-probe: bus: 3, device: 8 was not an MTP device
Dec 27 08:58:00 Inspiron-3521 kernel: [10978.316464] scsi 11:0:0:0: Direct-Access        Mass  Storage Device        PQ: 0 ANSI: 0
Dec 27 08:58:00 Inspiron-3521 kernel: [10978.317238] sd 11:0:0:0: Attached scsi generic sg2 type 0
Dec 27 08:58:00 Inspiron-3521 kernel: [10978.317370] sd 11:0:0:0: [sdb] 976773166 512-byte logical blocks: (500 GB/466 GiB)
Dec 27 08:58:00 Inspiron-3521 kernel: [10978.317507] sd 11:0:0:0: [sdb] Write Protect is off
Dec 27 08:58:00 Inspiron-3521 kernel: [10978.317513] sd 11:0:0:0: [sdb] Mode Sense: 03 00 00 00
Dec 27 08:58:00 Inspiron-3521 kernel: [10978.317655] sd 11:0:0:0: [sdb] No Caching mode page found
Dec 27 08:58:00 Inspiron-3521 kernel: [10978.317660] sd 11:0:0:0: [sdb] Assuming drive cache: write through
Dec 27 08:58:00 Inspiron-3521 kernel: [10978.365413]  sdb: sdb1 sdb2 < sdb5 > sdb3
Dec 27 08:58:00 Inspiron-3521 kernel: [10978.366573] sd 11:0:0:0: [sdb] Attached SCSI disk
Dec 27 08:58:01 Inspiron-3521 kernel: [10979.237877] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
Dec 27 08:58:01 Inspiron-3521 udisksd[2539]: Mounted /dev/sdb1 at /media/joseph/50Gb-Partition on behalf of uid 1001
Dec 27 08:58:01 Inspiron-3521 kernel: [10979.306234] EXT4-fs (sdb3): recovery complete
Dec 27 08:58:01 Inspiron-3521 kernel: [10979.306374] EXT4-fs (sdb3): mounted filesystem with ordered data mode. Opts: (null)
Dec 27 08:58:01 Inspiron-3521 udisksd[2539]: Mounted /dev/sdb3 at /media/joseph/400Gb-Partition on behalf of uid 1001
Dec 27 08:58:01 Inspiron-3521 gnome-session[16221]: (nautilus:21281): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed
Dec 27 08:58:01 Inspiron-3521 gnome-session[16221]: (nautilus:21281): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed
Dec 27 08:58:01 Inspiron-3521 gnome-session[16221]: (nautilus:21275): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed
Dec 27 08:58:01 Inspiron-3521 gnome-session[16221]: (nautilus:21275): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed
Dec 27 08:58:01 Inspiron-3521 gnome-session[16221]: (nautilus:21275): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed
Dec 27 08:58:01 Inspiron-3521 gnome-session[16221]: (nautilus:21275): GLib-GObject-WARNING **: invalid (NULL) pointer instance
Dec 27 08:58:01 Inspiron-3521 gnome-session[16221]: (nautilus:21275): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed
Dec 27 08:58:01 Inspiron-3521 gnome-session[16221]: (nautilus:21281): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed
Dec 27 08:58:01 Inspiron-3521 gnome-session[16221]: (nautilus:21281): GLib-GObject-WARNING **: invalid (NULL) pointer instance
Dec 27 08:58:01 Inspiron-3521 gnome-session[16221]: (nautilus:21281): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed
Dec 27 08:58:01 Inspiron-3521 dbus[833]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Dec 27 08:58:01 Inspiron-3521 systemd[1]: Starting Hostname Service...
Dec 27 08:58:01 Inspiron-3521 dbus[833]: [system] Successfully activated service 'org.freedesktop.hostname1'
Dec 27 08:58:01 Inspiron-3521 systemd[1]: Started Hostname Service.
Dec 27 08:58:02 Inspiron-3521 gnome-session[16221]: (gnome-software:16458): Gs-WARNING **: failed to get updates: no results to show
Dec 27 08:59:10 Inspiron-3521 dbus[833]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Dec 27 08:59:10 Inspiron-3521 systemd[1]: Starting Hostname Service...
Dec 27 08:59:10 Inspiron-3521 dbus[833]: [system] Successfully activated service 'org.freedesktop.hostname1'
Dec 27 08:59:10 Inspiron-3521 systemd[1]: Started Hostname Service.

I cannot copy or delete files unless from the CLI as root.

Any ideas because this is driving me nuts!

---

### Post by sudodus on 2016-12-27
I think this is an issue with permissions. ***If you tell us what file system it is***, we can suggest a method to mount it. I can guess from the syslog output, that it is a linux **ext** file system, but please confirm.

You can list the file system with the following command line:

```
sudo lsblk -f
```

Please put the output of the commands within [noparse]```
tags
```[/noparse] to make it easier to read: Click on the red button **[COLOR="#FF0000"]Go Advanced[/COLOR]**, mark the text and click on the **#** icon above the editing window (or do it manually), like this:

[noparse]```

your output line 1
line 2
line 3
...

```[/noparse]

Notice that you can mark (press the left button while moving the cursor) and paste (press the middle button or wheel to paste) from a terminal window to the editing box of Ubuntu Forums.

---

### Post by markhamjoseph on 2016-12-27
```


joseph@Inspiron-3521:~$ sudo lsblk -f
[sudo] password for joseph: 
NAME   FSTYPE LABEL           UUID                                 MOUNTPOINT
sda                                                                
&#9500;&#9472;sda1 vfat   DELLUTILITY     4A94-68C5                            
&#9500;&#9472;sda2 vfat   OS              5433-CC56                            
&#9500;&#9472;sda3 ext4                   03a321de-0f68-4412-acb2-150a7da3cc64 /
&#9500;&#9472;sda4                                                             
&#9492;&#9472;sda5 swap                   7c00657d-cb6f-4f8d-b858-159dde12fb82 [SWAP]
sdb                                                                
&#9500;&#9472;sdb1 ext4   50Gb-Partition  cd0510ca-dd88-4d52-94e8-52b81596a74f 
&#9500;&#9472;sdb2                                                             
&#9500;&#9472;sdb3 ext4   400Gb-Partition 457015f3-9a84-4212-bcb5-9a3a7befd2d4 
&#9492;&#9472;sdb5 swap                   9cf800ad-e7e5-45c2-a182-58dd7f628a94 
sr0                                                                
joseph@Inspiron-3521:~$ 






```

---

### Post by sudodus on 2016-12-27
So you want to mount /dev/sdb1 and /dev/sdb3 so that they can be managed without using sudo.

These are linux ext4 partitions, which makes it possible the control the permissions individually for directories and files. 

- If they belong to other operating systems, you should not tamper with them, because it might damage those operating systems.

- Otherwise, if those partitions are 'only' storage for you current operating system (running in /dev/sda3), you can change owner with ***chown*** and/or change permissions with ***chmod*** of the directories (and the content recursively) to make things more convenient.

---

### Post by markhamjoseph on 2016-12-27
Thanks sudodus. But this is a usb hard-disk which on other ubuntu pcs is automounted with no issues at all.

What I cannot understand is why on this particular pc the external usb disk is mounted with user and group 1000 and doesn't allow me to see/write/read it as a normal user.

In other words, I would like ubuntu to auto-mount with no intervention from my part.

Joseph

---

### Post by sudodus on 2016-12-27
```
ls -l
``` will list the names of the user and group for each file and directory.

```
ls -ln
``` will list the numbers of the user and group for each file and directory.

Maybe directories and ownership were created with another owner ID than yours in the problematic computer (if your user ID is not 1000). If this is the case you can either fix the user part of it, or the permissions part of it. Remember to take it easy with the ownership and permissions if the drive is used as a system disk by another operating system. Maybe it is easier to login as user 1000 (which is usually the first user, created when the operating system was installed).

---

