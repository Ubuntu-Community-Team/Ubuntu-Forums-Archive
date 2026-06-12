---
title: "Assignment of /dev/sda to USB drive"
date: 2015-07-22
forum: Hardware
---

### Post by bench on 2015-07-22
I have Ubuntu installed in EFI boot mode on a Mac Mini (not sure whether this is relevant to the question or not).

When I boot the Mac Mini without the USB drive attached, the internal hard drive is assigned the device name /dev/sda.  If I then plug a USB drive in, this is assigned to /dev/sdb.  All good so far.

However, when I reboot the machine with the USB drive connected, the two device nodes switch over and the USB device gets /dev/sda before the internal hard drive, which then gets /dev/sdb.  I can see this happening the syslog/dmesg.

I've read that the kernel and/or GRUB determine the device names/order on boot?

Does anyone know why this happens and how to stop it happening?  I would like my internal hard drive to remain on /dev/sda. The USB drive is to remain plugged in permanently and the machine will be accessed remotely so I can simply unplug it each time I reboot.

I know it doesn't matter from a technical point of view but from a consistency point of view I don't like it.

Thanks

---

### Post by dino99 on 2015-07-22
i've never met that case, but maybe check the device order into uefi (usually the internal device(s) get the first letter(s), then the external, but your uefi seems having an other rule) . A work around can be using 'label' for the device instead of the default naming

---

### Post by weatherman2 on 2015-07-22
Out of curiosity, why is it important for the internal drive to remain /dev/sda ?  Why does it matter?  You should be able to reference partitions using UUID and not worry about device IDs.

---

### Post by oldfred on 2015-07-22
I do not know Mac, but similar issue on my PC.
Related to SATA port order.
I had first drive in first port, but skipped a port or two. Then flash drive when plugged in was sde, but on reboot was sdb.
While booting from sdc or sdd worked as UUID were used, I did have to be very careful in any command using device setting like /dev/sdb.

Check SATA ports order of drive.

---

### Post by bench on 2015-07-23
> **weatherman2 said:**
> Out of curiosity, why is it important for the internal drive to remain /dev/sda ?  Why does it matter?  You should be able to reference partitions using UUID and not worry about device IDs.

Actually, as you rightly say it doesn't matter what the internal drive is named - as it is mounted using UUID. What does matter, is what the external drive is named. The external drive is a 2TB Seagate USB drive encrypted with Truecrypt. I'm not sure if I can even mount the encrypted volume using UUID, as apparently none is exposed until after the volume is mounted by Truecrypt. If I automate the mounting of the Truecrypt volume, I need to know 100% the device name of the disk. It would be nice if UUID was an option...

---

### Post by weatherman2 on 2015-07-23
> **bench said:**
> Actually, as you rightly say it doesn't matter what the internal drive is named - as it is mounted using UUID. What does matter, is what the external drive is named. The external drive is a 2TB Seagate USB drive encrypted with Truecrypt. I'm not sure if I can even mount the encrypted volume using UUID, as apparently none is exposed until after the volume is mounted by Truecrypt. If I automate the mounting of the Truecrypt volume, I need to know 100% the device name of the disk. It would be nice if UUID was an option...

You should be able to use the UUID with Truecrypt. The unmounted partition would have a known UUID, wouldn't it?  I believe all partitions do.

 FYI, UUIDs get symlinked to their device IDs at boot time in /dev/disk/by-uuid/.  If the UUID is (random example):

```
f7480d9c-cda4-4fd0-801f-75ef5d11ba64
```

then you could mount it - if it were an unencrypted conventional partition - with:

```
sudo mount /dev/disk/by-uuid/f7480d9c-cda4-4fd0-801f-75ef5d11ba64 /mnt
```

/dev/disk/by-uuid/f7480d9c-cda4-4fd0-801f-75ef5d11ba64 is a symlink to a device ID like /dev/sda1 .

If for some reason Truecrypt doesn't like the link /dev/disk/by-uuid/f7480d9c-cda4-4fd0-801f-75ef5d11ba64 and would insist on, say, /dev/sda1 instead, it would be fairly easy to write a little script to figure out what f7480d9c-cda4-4fd0-801f-75ef5d11ba64's real device ID is (using the link in /dev/disk/by-uuid/ ) before you attempt to mount it with Truecrypt.

---

### Post by bench on 2015-07-30
> **weatherman2 said:**
> You should be able to use the UUID with Truecrypt. The unmounted partition would have a known UUID, wouldn't it?  I believe all partitions do.

 FYI, UUIDs get symlinked to their device IDs at boot time in /dev/disk/by-uuid/.  If the UUID is (random example):

```
f7480d9c-cda4-4fd0-801f-75ef5d11ba64
```

then you could mount it - if it were an unencrypted conventional partition - with:

```
sudo mount /dev/disk/by-uuid/f7480d9c-cda4-4fd0-801f-75ef5d11ba64 /mnt
```

/dev/disk/by-uuid/f7480d9c-cda4-4fd0-801f-75ef5d11ba64 is a symlink to a device ID like /dev/sda1 .

If for some reason Truecrypt doesn't like the link /dev/disk/by-uuid/f7480d9c-cda4-4fd0-801f-75ef5d11ba64 and would insist on, say, /dev/sda1 instead, it would be fairly easy to write a little script to figure out what f7480d9c-cda4-4fd0-801f-75ef5d11ba64's real device ID is (using the link in /dev/disk/by-uuid/ ) before you attempt to mount it with Truecrypt.

Sorry for the delay...

The partition on the external drive is encrypted with Truecrypt, until the partition is decrypted by mounting it with the truecrypt program, the system sees it as an empty disk with no partitions. No UUID is created for the partition in /dev/disk/by-uuid/ until after it is decrypted and mounted, you have to use the kernel supplied /dev/sdb1 (for example), in order to decrypt the partition and mount it.

---

### Post by weatherman2 on 2015-07-30
OK - another way to do it is to track your USB drive's serial number, then figure out which drive it is (/dev/sda ? /dev/sdb ?).  Then if you find out it's, say, /dev/sdb, mount the partition as /dev/sdb1.   There are probably a few ways to get your hard drive's serial number in a script.  One way that comes to mind is the lshw command.

```
sudo lshw -C disk
```

and parse that; it gives you both serial number and logical name (/dev/sda etc).

---

