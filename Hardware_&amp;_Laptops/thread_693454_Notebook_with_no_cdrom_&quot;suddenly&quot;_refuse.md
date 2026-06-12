---
title: "Notebook with no cdrom &quot;suddenly&quot; refuses to boot"
date: 2008-02-11
forum: Hardware &amp; Laptops
---

### Post by hajuu on 2008-02-11
Hey guys,

I picked up a very very small dell laptop the other day for free.. It had a copy of ubuntu on it (breezy) which I upgraded to dapper drake.. The upgrade process went fine, I restarted the machine to make sure and everything booted A-OK..

After this I started installing alot of software.. I noticed in synaptic that dbus as well as HAL (hardware abstraction layer) and possibly something else. However I figured that it probably knew what it was doing better than I did, so I allowed it to proceed...

 Everything went well apparently, so I restarted to check that everything was OK, but now the machine wont boot.. I have no idea whats wrong, I get about 20 or so segment fault messages at boot and im dropped down to a busybox shell, saying that hda1 doesn't exist (which is the device it is currently booting off, the ONLY device)

The kicker is that the laptop doesn't have any kind of support for removable media, so I cant exactly just reinstall or use a bootdisk.. It does support network booting, but it seems extraordinarilly complex.

If anyone can give me some advice on how to maybe skip init.d or something at boot (grub console?) it would be really appreciated.

Thanks,
Hajuu

---

