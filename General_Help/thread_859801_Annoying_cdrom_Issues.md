---
title: "Annoying cdrom Issues"
date: 2008-07-14
forum: General Help
---

### Post by !nkubus on 2008-07-14
My both Dvd Drives are acting really lazy. They start at an ok speed but slow speed, then the speed decrease over time until they hangs forever.

Ex burning a simple audio CD can take about 4hours, it starts a 22+ x and when the cd is done the speed is about 0.02x with brasero,

Same thing happens in about every application, K9copy starts encoding ok but just take about 4 days to complete his task.

Here is some information that could help:

**fstab**:
```

/dev/scd0   /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1   /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

```
[B]
ls -l /dev | grep scd[/B]
```

lrwxrwxrwx  1 root   root           4 2008-07-14 18:58 cdrom -> scd1
lrwxrwxrwx  1 root   root           4 2008-07-14 18:58 cdrom1 -> scd0
lrwxrwxrwx  1 root   root           4 2008-07-14 18:58 cdrw1 -> scd0
lrwxrwxrwx  1 root   root           4 2008-07-14 18:58 dvd -> scd1
lrwxrwxrwx  1 root   root           4 2008-07-14 18:58 dvd1 -> scd0
lrwxrwxrwx  1 root   root           4 2008-07-14 18:58 dvdrw1 -> scd0
brw-rw----+ 1 root   cdrom    11,   0 2008-07-14 18:57 scd0
brw-rw----+ 1 root   cdrom    11,   1 2008-07-14 18:57 scd1
lrwxrwxrwx  1 root   root           4 2008-07-14 18:58 sr0 -> scd0
lrwxrwxrwx  1 root   root           4 2008-07-14 18:58 sr1 -> scd1

```

** /etc/udev/rules.d/70-persistent-cd.rules**
```

# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# DVD_SOHD-16P9S (pci-0000:00:0f.1-scsi-1:0:1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:1:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:1:0", SYMLINK+="dvd", ENV{GENERATED}="1"
# DVDRW_SOHW-1693S (pci-0000:00:0f.1-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:0:0", SYMLINK+="cdrw1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:0:0", SYMLINK+="dvd1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:0:0", SYMLINK+="dvdrw1", ENV{GENERATED}="1"

```

**sudo lshw -C disk** 
```

*-disk                  
       description: ATA Disk
       product: Maxtor 6L300R0
       vendor: Maxtor
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: BAJ4
       serial: L61RX69H
       size: 279GiB (300GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000cef36
  *-cdrom:0
       description: DVD writer
       product: DVDRW SOHW-1693S
       vendor: LITE-ON
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: KS09
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
          logical name: /media/cdrom0
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted
  *-cdrom:1
       description: DVD reader
       product: DVD SOHD-16P9S
       vendor: LITE-ON
       physical id: 0.1.0
       bus info: scsi@3:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: FS09
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=open

```


Any help would be appreciated. I'm kind of lost.

Thanks a lot :)

---

### Post by mc4man on 2008-07-14
all of what you posted is fine. you could run  ```
sudo hdparm -i /dev/scd0
``` and..../scd1 to ck. on whether dma is enabled. (pretty much the only thing hdparm is good for)
you could also grep your logs for DMA and see if anything unusual turns up. EX.  ```
grep ' DMA' /var/log/syslog
```

In all probability if the slowdown is confined to when burning is taking place it's because the buffer is being emptied and not refilled. At that point burning will slow to a crawl.
If that's the case I wouldn't know what you could do, I don't use any linux apps for burning. Maybe try creating an .iso and using the built-in cd/dvd creator to burn.

---

### Post by !nkubus on 2008-07-15
Things are getting worse, my CD just won't mount after a while

**grep ' DMA' /var/log/syslog**
```

Jul 15 18:42:32 frank-desktop kernel: [    0.000000]   DMA             0 ->     4096
Jul 15 18:42:32 frank-desktop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jul 15 18:42:32 frank-desktop kernel: [    0.000000]   DMA zone: 0 pages reserved
Jul 15 18:42:32 frank-desktop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Jul 15 18:46:32 frank-desktop kernel: [    0.000000]   DMA             0 ->     4096
Jul 15 18:46:32 frank-desktop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jul 15 18:46:32 frank-desktop kernel: [    0.000000]   DMA zone: 0 pages reserved
Jul 15 18:46:32 frank-desktop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0


```

I've been seeing a lot of threads with cdrom issues with hardy but non of them were really resolved.

---

### Post by !nkubus on 2008-07-16
What I don't understand is why CD/DVD are now detected as SCSI drives instead if IDE.

Is there a way to come back to the old way of managing cdroms wich was working flawlessly before?

---

