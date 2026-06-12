---
title: "[SOLVED] Virtual harddrive image"
date: 2008-08-07
forum: General Help
---

### Post by jleems86 on 2008-08-07
I would like to find a way to create a new file and use it as a virtual mountable hdd image (like the ones used by virtual machines and truecrypt, but without the overhead).  I'd like for it to be agnostic with respect to  the file system used in the image file (i plan on using a ext2 file system in the image file).  while i am no linux expert, i am not afraid of the command line or editing fstab, but i just can't figure out a good way to do this

---

### Post by jleems86 on 2008-08-07
I forgot to mention, while i don't mind using a fixed size for the image file, i would like it to grow and shrink as necessary

---

### Post by bodhi.zazen on 2008-08-07
Not sure what you are wanting exactly ...

LVM perhaps

Or do you want to use it with virtual machines ?

You could always use an .iso image too. You can mount .iso images on virtual machines and on the host.

---

### Post by jleems86 on 2008-08-07
LVM is not quite what i'm looking for.  i basically want to make a new file that i can use as a fake mountable drive on my host machine.  I'm not sure if iso images are what i'm looking for or not.  Can they be formatted with any kind of file system and be mounted with read-write privileges?

---

### Post by bodhi.zazen on 2008-08-07
well, iso has its own file system, but can be burned to CD or mounted as a raw image my many OS.

Your alternate is to make a raw image file, but that would depend on what kind of virtual appliance you are using (ie make a new disk in VBox / VMWARE/ KVM) and not as portable as an iso.

---

### Post by aaronanderson on 2008-08-07
What you could do is use dd to create a file and then use losetup to set it up as a block device.

For example:
dd if=/dev/zero of=virtualdisk.img bs=1024K size=1024

That will create a 1GB file, full of nulls.

The following commands will require root permission:

Create the loopback block device:
losetup /dev/loop0 virtualdisk.img

Now you can format it:
mkfs.ext3 /dev/loop0

Then mount it:
mount /dev/loop0 /mnt

In the future, you can mount the drive with 1 command:
mount -o loop virtualdisk.img /mnt

Again, all these command require root. I'm not sure if it's possible to accomplish the same thing without root perms.

---

### Post by jleems86 on 2008-08-08
raw image file sounds more like what i'm looking for, but i'm hoping to use this in my host OS as a fake external harddrive, not as the root drive of a vm.  i'm hoping to avoid the overhead of having to route everything through a virtual machine.

---

### Post by aaronanderson on 2008-08-08
I forgot to mention that it *may* be possible to grow it in the future. For example, if you want to grow it by another 1GB, you might be able to do:

dd if=/dev/zero of=tmp bs=1024K count=1024
cat virtualdisk.img tmp > newdisk.img

That should make a 2GB image. You could then use ext2resize to resize your filesystem.

I haven't tried this part, so you might need to make some modifications.

HTH.

---

### Post by jleems86 on 2008-08-08
Thanks aaronanderson, thats exactly what i'm looking for

> **aaronanderson said:**
> What you could do is use dd to create a file and then use losetup to set it up as a block device.

For example:
dd if=/dev/zero of=virtualdisk.img bs=1024K size=1024

That will create a 1GB file, full of nulls.

The following commands will require root permission:

Create the loopback block device:
losetup /dev/loop0 virtualdisk.img

Now you can format it:
mkfs.ext3 /dev/loop0

Then mount it:
mount /dev/loop0 /mnt

In the future, you can mount the drive with 1 command:
mount -o loop virtualdisk.img /mnt

Again, all these command require root. I'm not sure if it's possible to accomplish the same thing without root perms.

---

### Post by bodhi.zazen on 2008-08-08
/me wonders at the advantage of that over an .iso file ?

mount -o loop -t iso9660 filename.iso /mnt

:popcorn:

---

### Post by aaronanderson on 2008-08-08
I could be wrong but I can't edit a file with-in the ISO image. If I mount it using:
```

mount -t iso9660 -o loop temp.iso /mnt

```

I don't believe I can do:
```

touch /mnt/x

```

Aren't iso9660 filesystems read-only?

---

