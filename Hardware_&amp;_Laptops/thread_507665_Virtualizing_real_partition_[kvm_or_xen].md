---
title: "Virtualizing real partition [kvm or xen]"
date: 2007-07-23
forum: Hardware &amp; Laptops
---

### Post by dhmo on 2007-07-23
I have searched here and elsewhere but I couldn't locate any information how I can virtualize an OS (WindowsXP/2003) that resides on its own partition.

I do know VMWare can handle this [see [http://ubuntuforums.org/showthread.php?t=481523](http://ubuntuforums.org/showthread.php?t=481523) as well as elsewhere], but I'd like to do it using kvm or xen. (Actually I'd prefer **kvm**)

I have pepared the Windows installation (which is at **/dev/sda4** ) so that it has a different hadrware profile for virtualization.

The only thing I need is the steps (or the command) to run it from withing Ubuntu.

Could someone help.

---

### Post by tgm4883 on 2007-07-23
Don't know how you do it in Ubuntu, the only way I know of is using the vmware software to convert it.

---

### Post by kandresen on 2008-03-30
I do use qemu/kvm with direct disk access, however there are a few gotcha's. 

Qemu connects to disks, not partitions! 
It is thus totally ok to use
qemu -hda /dev/sda     # disk sda
but not
qemu -hda /dev/sda1   # first partition on sda

Now, if the current operating system reside on sda1, you may not give the disk exclusively to qemu... Thus this will fail. If you have two disks however, you can select to not touch one of the disks with the underlaying operating system and dedicate the disk to Qemu - I frequently have done this with external disks. 

That said, I myself have created encrypted virtual disks using cryptsetup. 

cryptsetup -c aes-cbc-essiv:sha256 luksFormat /dev/<partition_for_encryption>

then every time I want to use Qemu using:
cryptsetup luksOpen /dev/<partition_for_encryption> qemu

qemu -hda /dev/mapper/qemu

---

### Post by tgm4883 on 2008-03-30
> **kandresen said:**
> I do use qemu/kvm with direct disk access, however there are a few gotcha's. 

Qemu connects to disks, not partitions! 
It is thus totally ok to use
qemu -hda /dev/sda     # disk sda
but not
qemu -hda /dev/sda1   # first partition on sda

Now, if the current operating system reside on sda1, you may not give the disk exclusively to qemu... Thus this will fail. If you have two disks however, you can select to not touch one of the disks with the underlaying operating system and dedicate the disk to Qemu - I frequently have done this with external disks. 

That said, I myself have created encrypted virtual disks using cryptsetup. 

cryptsetup -c aes-cbc-essiv:sha256 luksFormat /dev/<partition_for_encryption>

then every time I want to use Qemu using:
cryptsetup luksOpen /dev/<partition_for_encryption> qemu

qemu -hda /dev/mapper/qemu

Thanks for registering and helping.  Please note the date of the last post though.  You are replying to a thread that is almost a year old.

---

### Post by john8_36 on 2008-04-11
That's okay.  It's still useful to the rest of us  (Although I'm guessing that by now dhmo has given up or moved on).

---

