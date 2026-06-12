---
title: "Need help with Neoware CA2 Neolinux"
date: 2008-12-14
forum: Hardware
---

### Post by Lanrat on 2008-12-14
I know that this question is not directly Ubuntu related but after I finish this I do plan on installing Xubnuntu.

I recently got a Neoware CA2 thin-client at a swap-me. It runs Neolinux 3.0 and Linux Kernel 2.4. Unfortunately I do not know the password. when it boots up it auto logs in as guest. I want to reset the root/operator password so that I can reset the device. (I know I can just wipe the 32MB HD, but i want to try neolinux out first)

I have looked online for more information on this device but since HP bought Neoware it is hard to find any.

But I did find this:
1) Restart the NeoLinux appliance.
2) On power on hold down the Shift key.
3) From the LILO Boot Menu type "software single" and press Enter.
4) After about 15 seconds press Alt/F2.
5) From bash# type "factory_reset" and press Enter.
6) Type /sbin/reboot and press Enter.

I have tried both shift and alt when but lilo just continues to load as if I was doing nothing.

I also thought I could boot the device off a usb drive and mount the drive and reset the password with that. The HD has 3 partitions, 1 1mb "writable" partition, 1 100kb blank partition and a third 24mb system partition. all are ext2. the first two are easily mountable, but the password is contained in the third partition. When I try to mount it I get this message

```
mount: wrong fs type, bad option, bad superblock on /dev/hda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

I have tried specifying the file system type and using an alternate superblock to mount, i still get the same error.
I made an image of the hard drive to mount on another computer, i get the same error.

Can anyone help me with getting this device reset or become root/operator so that I can reset it?

Thanks!

---

### Post by Lanrat on 2008-12-16
Bump.

---

### Post by Lanrat on 2008-12-17
comon, is there any way to force this filesystem to mount? or re-build it so that it is mountable?

---

