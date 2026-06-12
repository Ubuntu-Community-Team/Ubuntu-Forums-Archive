---
title: "spontaneous renumbering of md devices after hibernate"
date: 2007-03-30
forum: Hardware &amp; Laptops
---

### Post by agrimstad on 2007-03-30
My system is dapper drake, updated to the best of my knowledge, on an ASUS mobo and intel CPU, using an i386 kernel (2.6.15-28-386). The system is a desktop, not a laptop.

I have two software raid devices, both raid1. The first, md0, was created using partitions sda8 and sdb8 and was set up to mount /home. The second, md1, was created yesterday using partitions sda7 and sdb7 and was set up to mount /usr.

After the creation of the the second raid device I had several reboots and all seemed well. I put the system into hibernation last night. This morning when I woke the system up and all was not well. A bit of investigation revealed that the two raid devices had been spontaneously renumbered and now md0 had the /usr file system and md1 had the /home file system. So the recovery was only a matter of a change to fstab.

I'm planning to put my root and /var file systems on their own software raid devices in the future--/boot needs to be kept off raid because of grub limitations as far as I know--and so am a bit worried by this renumbering.

Does anyone know what is causing this? And what can be done about it? One thing I'll note is that I decided not to bother creating an /etc/mdadm/mdadm.conf file, since mdrun seemed to be working OK in discovering the raid devices. Would this config file have made any difference?

---

### Post by agrimstad on 2007-04-02
Well, it seems that hibernation is not really part of this spontaneous renumbering of md devices. It's really something related to rebooting.

I now have an /etc/mdadm/mdadm.conf file describing my meta devices. It doesn't seem to matter.

I think this is the crux of the spontaneous renumbering problem. Assume there is some existing set of md devices and the set is stable. Now create a new md and give it a number one higher than the highest existing number. If the underlying file partitions of this new meta device use lower numbers for this new md than the existing md's, after a reboot spontaneous renumbering will happen (and mdadm.conf will be ignored).

For example, suppose you have /usr mounted on /dev/md0, which uses /dev/sda7 and /dev/sdb7. Now create md1 which uses /dev/sda6 and /dev/sdb6. Even if you create mdadm.conf that reflects this situation, after a reboot md0 will be the meta device using sda6 and sdb6 and /usr won't be found.

I don't know if its related, but I'm setting the type FD on my partitions used to construct meta devices.

The workaround is to live with the renumbering and adjust /etc/fstab (and /etc/mdadm/mdadm.conf even though it seems to be mostly ignored) to the meta device numbering that something in the system demands.

---

