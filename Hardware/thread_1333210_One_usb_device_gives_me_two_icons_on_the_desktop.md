---
title: "One usb device gives me two icons on the desktop"
date: 2009-11-21
forum: Hardware
---

### Post by balteo on 2009-11-21
Hello,

I have the following question: How come when I plug in **one** of my usb keys on jaunty, it automatically places **two icons on the desktop**. Note I have reformatted the key in ext3 and this does not make any difference.

Here is a relevant part of a **lsusb -v**:

```

Bus 001 Device 006: ID 13fe:1a20 Kingston Technology Company Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x13fe Kingston Technology Company Inc.
  idProduct          0x1a20 
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              200mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0


```It is not so much an annoyance I am trying to fix but rather I am just curious about this as I am studying devices drivers and usb.

Can anyone please help?

Thanks in advance,

J.

---

### Post by renkinjutsu on 2009-11-21
maybe there are actually two partitions on your USB drive (one that's hidden?)

let's see what "mount" spits out at your in the terminal

---

### Post by balteo on 2009-11-21
Thanks for your quick reply!

-Two partitions? Good point! I have recreated a unique msdos partition on the key and still it shows two icons on the desktop: One labelled: "media 1.5 MB" and another one "media 1.0 GB".

-mount? Here it is:

```
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-16-generic/volatile type tmpfs (rw,mode=755)
/dev/sda1 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/julien/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=julien)
/dev/sdb1 on /media/usb0 type ext3 (rw,noexec,nodev,sync,noatime)
/dev/sdc on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
```
Julien.

---

### Post by balteo on 2009-11-21
After an extensive google search I came upon those two threads:
[http://ubuntuforums.org/showthread.php?t=444889](http://ubuntuforums.org/showthread.php?t=444889)
[http://ubuntuforums.org/showthread.php?t=442009](http://ubuntuforums.org/showthread.php?t=442009)

There seems to be a problem with Kingston usb keys...

My question now reformulates as follows:
[B]Where do I have to look to in order to find this bug? Which driver? Which source file?
[/B] 
Any further clue very welcome.

Julien.

---

### Post by renkinjutsu on 2009-11-22
It might be that Kingston devices have an extra partition in them that handles windows optimizations and stores drivers and such.. I think the only way to stop it from mounting would be to delete that partition.. You probably won't need it anyway, and it's only 1.5MB

---

### Post by Tahakki on 2009-11-22
Some USB sticks, rather than two partitions, have two actual physical chips on them. I have one just like you described. I think I put a bootloader in the 1.5MB one, as it was the same size as a floppy.

---

### Post by balteo on 2009-11-22
> **Tahakki said:**
> Some USB sticks, rather than two partitions, have two actual physical chips on them. I have one just like you described. I think I put a bootloader in the 1.5MB one, as it was the same size as a floppy.
I came up to the same conclusion upon investigation.
Thanks,
J.

---

### Post by IcarusR on 2009-11-22
I have the same situation with 2 Integral usb sticks. They are 2GB & have two partitions, probably two chips. 
One is 1.9 GB & the other is 2 Mb. I can not 'get rid' of the small partition. Just live with it.
The small partition had encryption software in it for windows.

---

### Post by Tahakki on 2009-11-23
Yeah, some use it for password access to the stick. Rendered useless as Linux'll just read anyway. :P

---

### Post by HeadHunter00 on 2009-11-23
It happens to me too. It's just the usb itself.

---

