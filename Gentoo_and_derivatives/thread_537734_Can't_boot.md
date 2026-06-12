---
title: "Can't boot"
date: 2007-08-29
forum: Gentoo and derivatives
---

### Post by happysmileman on 2007-08-29
Ok I've finally gotten it to load the kernel and boot, by booting it from the Ubuntu GRUB file with

```
title		Gentoo
kernel		(hd0,4)/boot/gentoo root=/dev/sda3
```

After copying my gentoo kernel image to /boot/gentoo on my Ubuntu drive (hd0,4) is Ubuntu drive "/dev/sda3" is my root gentoo partition.

Upon trying this it starts to boot, then says something about having no NFS server and being unable to load sda3, (I can take down the error message if you need it, probably should've done it when it happened first)

Any ideas? If not I'll take down the error message next time I reboot

---

### Post by Bachstelze on 2007-08-29
Are the drivers for your ATA/SCSI chipset as well as for your root filesystem compiled in-kernel (and not as modules) ?

---

### Post by happysmileman on 2007-08-29
> **HymnToLife said:**
> Are the drivers for your ATA/SCSI chipset as well as for your root filesystem compiled in-kernel (and not as modules) ?

I think so, I'm pretty sure I did compile them, any way to check?

In modules, I only have ntfs, rfs modules, some video ones, and one call scsi_wait_scan.ko

So anything else is compiled into kernel

---

### Post by happysmileman on 2007-08-29
Error message is that it can't load FS from NFS server

Directly after that it seems to load /dev/sda, so the problem appears to be that it tries to load the root filesystem before that drive is loaded properly.

After pushing any button it goes to kernel panic.

---

### Post by Bachstelze on 2007-08-30
Can you post your fstab ?

---

### Post by happysmileman on 2007-08-30
> **HymnToLife said:**
> Can you post your fstab ?

```
# NOTE: If your BOOT partition is ReiserFS, add the notail option to opts.
/dev/sda1		/boot		ext2		defaults,noatime	1 2
/dev/sda3		/		ext3		noatime		0 1
/dev/sda2		none		swap		sw		0 0

/dev/cdrom		/mnt/cdrom	auto		noauto,user	0 0

# glibc 2.2 and above expects tmpfs to be mounted at /dev/shm for 
# POSIX shared memory (shm_open, shm_unlink).
# (tmpfs is a dynamically expandable/shrinkable ramdisk, and will
#  use almost no memory if not populated with files)
shm			/dev/shm	tmpfs		nodev,nosuid,noexec	0 0

```

---

### Post by happysmileman on 2007-08-30
Ok the problem looks to be that it tries to load /dev/sda3 as the root partition before it's actually recognised by boot process, when looking at the full loading process (not using "quiet" as a boot option) I can see that a few seconds AFTER it says it can't load root FS it loads sda.

So I need to get it to try load the root partition and all after they get seen by the boot process, any way to do this.

Sorry if it's badly worded, I can try rephrase if you don't understand, but basically it tries to mount sda3 as / BEFORE it actually loads /dev/sda and therefore it appears to try mount a partition that doesn't exist.

Any help would be very much appreciated (gentoo really is good for learning about Linux, though so far I've just been learning about the GRUB mostly :P)

---

### Post by rsambuca on 2007-08-30
You are missing the root line from your grub!

You need:

title="whatever"
root (hd0,4)
kernel /boot/kernel-2.6-etc root=/dev/sda3

I also note that your hd0,4 doesn't correspond to sda3 either EDIT: Oh, I see you copied the kernel over.  Ignore this last line!
Also, you might have to change the hd0,4 on the root line to correspond to the gentoo partition.

---

### Post by happysmileman on 2007-08-30
> **rsambuca said:**
> You are missing the root line from your grub!

You need:

title="whatever"
root (hd0,4)
kernel /boot/kernel-2.6-etc root=/dev/sda3

I also note that your hd0,4 doesn't correspond to sda3 either EDIT: Oh, I see you copied the kernel over.  Ignore this last line!
Also, you might have to change the hd0,4 on the root line to correspond to the gentoo partition.

Doesn't make any difference, still same problem

---

### Post by rsambuca on 2007-08-30
did you try putting root (hd0,2)?

---

### Post by reckless2k2 on 2007-08-30
hey i've been there before. 3 day install and fstab error so i can't boot. have fun with gentoo. ha. 

go ahead and flame me now. hello.....it is an ubuntu forum. hahaha.

---

### Post by happysmileman on 2007-08-30
> **rsambuca said:**
> did you try putting root (hd0,2)?

It's not on hd0... That's why I had to copy kernel over and boot from hd0,4 which is Ubuntu.

It's on an external drive that GRUB won't recognise.

---

### Post by rsambuca on 2007-08-30
try adding ro as a boot option.

---

### Post by happysmileman on 2007-08-30
> **rsambuca said:**
> try adding ro as a boot option.

No difference when i tried

```
kernel /boot/gentoo ro root=/dev/sda3
```

or

```
kernel /boot/gentoo root=/dev/sda3 ro
```

---

### Post by rsambuca on 2007-08-30
Sorry, no more ideas here.  My gentoo install worked first time, so I never really had to fiddle with this part of it.

---

### Post by happysmileman on 2007-08-30
> **rsambuca said:**
> Sorry, no more ideas here.  My gentoo install worked first time, so I never really had to fiddle with this part of it.

No bother, I'm sure someone can help

---

### Post by happysmileman on 2007-08-31
Any ideas at all, I'm sure this can't be that rare a problem, it's with a Philips 250GB hard-drive so I doubt I'm the only one

---

### Post by rsambuca on 2007-08-31
did you try hd(1,2)?

---

### Post by happysmileman on 2007-08-31
> **rsambuca said:**
> did you try hd(1,2)?

Yeah, but then gave up after accepting GRUB just wouldn't accept hd1, this no longer appears to be a GRUB problem, it appears to load the kernel fine now, but it tries to load /dev/sda3 before sda3 is even recognised.

---

### Post by rsambuca on 2007-08-31
Perhaps it would work if you use the UUID instead of /dev/sda3, since the UUID will remain constant?

---

### Post by happysmileman on 2007-08-31
> **rsambuca said:**
> Perhaps it would work if you use the UUID instead of /dev/sda3, since the UUID will remain constant?

So does /dev/sda3 as long as I keep the external drive plugged in if I understand correctly, if not an error would be expected... I could try it though, will next time I reboot.

EDIT: Do I just need to do root=UUID=hhdafanblfkj(whatever) or do I need to also do it in /etc/fstab.

And are the UUID's the same on Ubuntu and Gentoo or is it just randomly given by distro?

---

### Post by rsambuca on 2007-08-31
ls /dev/disk/by-uuid/ -alh

---

### Post by happysmileman on 2007-08-31
> **rsambuca said:**
> ls /dev/disk/by-uuid/ -alh

yeha I found that, but is it just root=UUID=meh in GRUB
Or do I also need to change /etc/fstab.

And I assume the results of that command in Ubuntu work in Gentoo as well?

---

### Post by happysmileman on 2007-08-31
That doesn't work, same problem.

It's trying to mount the root filesystem BEFORE detecting the external drive, I need to get it to somehow detect the external drive before it tries to mount the root filesystem, any help at all would be appreciated.

But since I can't actually get it to DO anything without it loading the root filesystem maybe it just will never work *sigh*.

EDIT: After a lot of googling I've seen something saying that I should set up an initrd to load the SCSI drive, however any tutorials I've seen are either outdated or confusing, I'm still looking but a link or some basic instructions would be useful

---

### Post by rsambuca on 2007-08-31
I found a few sites that show you how to create an initrd image so that you will be able to boot from a device that isn't recognized.

[http://www.opennet.ru/docs/HOWTO/Kernel-HOWTO-11.html](http://www.opennet.ru/docs/HOWTO/Kernel-HOWTO-11.html)

[http://www.lissot.net/partition/ramdisk.html](http://www.lissot.net/partition/ramdisk.html)

[http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html#MKINITRD](http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html#MKINITRD)

Please let me know if you get this to work as i am very interested!

---

### Post by happysmileman on 2007-08-31
I'm in way over my head here, I have no idea how to do any of this even after reading those and 2 others

---

### Post by rsambuca on 2007-08-31
I don't really know enough to help you out here either.  I am sure you would have better success in the gentoo forums.  I could probably help you out if you installed onto your regular drive, but this external usb thing has got me stumped.

---

### Post by happysmileman on 2007-09-01
I DID IT... But two problems that forums can't help me with.

1: The only way I can get it to work is by running "sleep 15", not a problem, but ironic considering I installed Gentoo for it's speed (though mainly it's configurability and to learn so that's ok)

2: My external drive appears to be starting to fail, every once in a while the light turns off and I have to switch it off and on again, I can't really use that for an OS, though it only really seems to happen while Ubuntu is loading so mayeb that does something

---

### Post by Bachstelze on 2007-09-01
> **happysmileman said:**
> 2: My external drive appears to be starting to fail, every once in a while the light turns off and I have to switch it off and on again, I can't really use that for an OS, though it only really seems to happen while Ubuntu is loading so mayeb that does something

Maybe that's where the whole problem comes from, though I've never tried Gentoo on an external drive. An initrd might solve it, too.

---

### Post by happysmileman on 2007-09-01
> **HymnToLife said:**
> Maybe that's where the whole problem comes from, though I've never tried Gentoo on an external drive. An initrd might solve it, too.

Yeha an initrd DID solve it (by running a "sleep 15" to wait for drive to load, thankfully nothing hard), I can now boot to gentoo (though i forget my root password *sheepish smile*, I'll fix it some other day)

---

