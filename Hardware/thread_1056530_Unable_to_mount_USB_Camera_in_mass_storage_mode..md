---
title: "Unable to mount USB Camera in mass storage mode."
date: 2009-01-31
forum: Hardware
---

### Post by walkeraj on 2009-01-31
I can't seem to read files off of my camera, which has a 1GB SD card in it.  I keep getting the "wrong fs type bad option bad superblock" message.  Here's the relevant tail off of /var/log/messages when I plug it in:

```

Jan 31 21:29:25 machine kernel: [116110.420063] usb 4-3: new high speed USB device using ehci_hcd and address 15
Jan 31 21:29:25 machine kernel: [116110.564088] usb 4-3: configuration #1 chosen from 2 choices
Jan 31 21:29:25 machine kernel: [116110.585520] scsi5 : SCSI emulation for USB Mass Storage devices
Jan 31 21:29:30 machine kernel: [116115.585672] scsi 5:0:0:0: Direct-Access     CASIO    DIGITAL_CAMERA   1.00 PQ: 0 ANSI: 0 CCS
Jan 31 21:29:30 machine kernel: [116115.601196] sd 5:0:0:0: [sdb] 2012160 512-byte hardware sectors (1030 MB)
Jan 31 21:29:30 machine kernel: [116115.602277] sd 5:0:0:0: [sdb] Write Protect is off
Jan 31 21:29:30 machine kernel: [116115.623522] sd 5:0:0:0: [sdb] 2012160 512-byte hardware sectors (1030 MB)
Jan 31 21:29:30 machine kernel: [116115.624621] sd 5:0:0:0: [sdb] Write Protect is off
Jan 31 21:29:30 machine kernel: [116115.625086]  sdb: sdb1
Jan 31 21:29:30 machine kernel: [116115.628869] sd 5:0:0:0: [sdb] Attached SCSI removable disk
Jan 31 21:29:30 machine kernel: [116115.629288] sd 5:0:0:0: Attached scsi generic sg1 type 0
Jan 31 21:29:31 machine kernel: [116116.513365] UDF-fs: No partition found (1)
Jan 31 21:29:31 machine kernel: [116116.652992] ISOFS: Unable to identify CD-ROM format.

```

---

### Post by taurus on 2009-01-31
What is the output when you run this command from a terminal?

```
sudo fdisk -l
```

---

### Post by walkeraj on 2009-01-31
Here's the listing for the camera drive.

```

Disk /dev/sdb: 1030 MB, 1030225920 bytes
4 heads, 3 sectors/track, 167680 cylinders
Units = cylinders of 12 * 512 = 6144 bytes
Disk identifier: 0x000dab2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              21      167680     1005958+   6  FAT16


```

---

### Post by taurus on 2009-01-31
See if you can mount it by hand from a terminal with

```
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1
df -h
```

---

### Post by walkeraj on 2009-01-31
That seemed to work.  So what is this, a hotplug problem?
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             55720220   8850404  44061656  17% /
tmpfs                   516492         0    516492   0% /lib/init/rw
varrun                  516492       140    516352   1% /var/run
varlock                 516492         0    516492   0% /var/lock
udev                    516492      2796    513696   1% /dev
tmpfs                   516492         0    516492   0% /dev/shm
lrm                     516492      2004    514488   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sdb1              1005680     68896    936784   7% /media/sdb1

# cd /media/sdb1/
# ls
apps  dcim  indx0001.tmp

```

---

### Post by taurus on 2009-01-31
Or maybe the automount.  When you are done with it, don't just unplug it.  Make sure you unmount it first before you unplug it.

```
sudo umount /media/sdb1
df -h
```

---

### Post by walkeraj on 2009-01-31
```

/media# umount sdb1/
/media# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              54G  8.5G   43G  17% /
tmpfs                 505M     0  505M   0% /lib/init/rw
varrun                505M  140K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M  2.8M  502M   1% /dev
tmpfs                 505M     0  505M   0% /dev/shm
lrm                   505M  2.0M  503M   1% /lib/modules/2.6.27-11-generic/volatile

```

---

### Post by walkeraj on 2009-01-31
So I've established that it can be mounted manually, where do I go from here?  I'm still familiarizing myself with hotplug and automounting.

---

### Post by taurus on 2009-01-31
Do you have another USB device that you can plug into your machine to see if it's automounted?

Otherwise, I guess you just have to mount it by hand when you plug your camera into your machine.

---

### Post by walkeraj on 2009-01-31
I have a thumbdrive that mounts perfectly well.

```

Jan 31 23:04:54 machine kernel: [121839.524928] usb 4-3: new high speed USB device using ehci_hcd and address 18
Jan 31 23:04:54 machine kernel: [121839.668080] usb 4-3: configuration #1 chosen from 1 choice
Jan 31 23:04:54 machine kernel: [121839.708065] scsi8 : SCSI emulation for USB Mass Storage devices
Jan 31 23:04:59 machine kernel: [121844.713533] scsi 8:0:0:0: Direct-Access     Kingmax  USB2.0 FlashDisk 0.00 PQ: 0 ANSI: 2
Jan 31 23:04:59 machine kernel: [121844.735616] sd 8:0:0:0: [sdc] 15794176 512-byte hardware sectors (8087 MB)
Jan 31 23:04:59 machine kernel: [121844.736199] sd 8:0:0:0: [sdc] Write Protect is off
Jan 31 23:04:59 machine kernel: [121844.745566] sd 8:0:0:0: [sdc] 15794176 512-byte hardware sectors (8087 MB)
Jan 31 23:04:59 machine kernel: [121844.747707] sd 8:0:0:0: [sdc] Write Protect is off
Jan 31 23:04:59 machine kernel: [121844.747725]  sdc:
Jan 31 23:04:59 machine kernel: [121844.882199] sd 8:0:0:0: [sdc] Attached SCSI removable disk
Jan 31 23:04:59 machine kernel: [121844.882437] sd 8:0:0:0: Attached scsi generic sg1 type 0

```

> **taurus said:**
> Otherwise, I guess you just have to mount it by hand when you plug your camera into your machine.

I'm sorry, but that *can't* be an acceptable solution.  Since it can be mounted manually, it's obviously a problem somewhere else that I can fix.  I just don't know where to go.

---

### Post by walkeraj on 2009-02-01
Anyone else have any ideas on where I should look to try and fix this?  It affects other USB mass-storage devices as well, but not all of them.  Is this a HAL configuration thing?  Any help would be appreciated.

---

### Post by baltho on 2009-07-27
Hi folks,

Same problem with a Kodak CX4230. No joy with mounting it as a filesystem yet, but the following seems to remove the "could not lock device" f-spot error: 
I created an /etc/udev/rules.d/99-kodak_camera.rules (as root, of course) with this in it:
 
BUS=="usb", SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0535", KERNEL=="sd?1", NAME="%k", SYMLINK="kodak-cx4230"

(All one line, btw).

The idVendor and idProduct magic numbers I found with "lsusb -v | less", sniffing through the output until I found the Vendor and Product numbers and removing the "0x" from the front of them. Thought I'd need to fiddle with groups and permissions, but it just worked! 

Hope this helps: I was searching here myself for a while before I found the solution....

---

