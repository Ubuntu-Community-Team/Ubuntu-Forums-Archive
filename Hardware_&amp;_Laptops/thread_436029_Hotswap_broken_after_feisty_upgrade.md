---
title: "Hotswap broken after feisty upgrade"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by MxGB on 2007-05-07
I use the hotswap utility to start and stop UltraBay swappable drives on my ThinkPad laptop. Since I upgraded to Feisty the app no longer works, reporting this error: ```
'hotswap: opening IDE device failed: No such file or directory'.
```I am working on the assumption that this is caused by Feisty renaming my IDE devices from hd* to sd*.

Unfortunately this is a great inconvenience because I swap drives regularly and reboot rarely. Does anyone know how I can either program udev to create symlinks to all sd* devices in the form /dev/hd* or even better (if it causes no side-effects) get the kernel to use the old naming method.


I've read quite a lot of threads where people have had similar problems with their fstab and replies advising 'search the forums', but my afternoon of forum searching and googling has yielded nothing. Why does the kernel now name IDE devices like SCSI devices?

---

### Post by Martin on 2007-05-09
Hi, post the contents of your fstab in your next post and I'm pretty sure someone will point out where the problem lies. Needless to say after suggesting this it wil have nothing to do with your fstab :). I don't know how hotswap on ibm laptops works but it might use USB in which case your problem might be similar to the others that people are experiencing when trying to connect ext. usb drives. If that is the case the fstab will help and the problem may well be easily fixed.

---

### Post by Rescue9 on 2007-05-11
I'm reading that Ubuntu switched to the new PATA interface that makes everything look like SCSI as far as the /dev/sdX. That being said.... the scsiadd program crashed completely. I tried using it to unmount my optical drive and it unmounted everything; no command would work and had to do a hard reboot.

That being said... I don't think the hotswap program is going to work either since it's IDE. I'd like to get more information on this though as it's definitely needed.

lets just BUMP this up to see if it gets more attention.

---

### Post by MxGB on 2007-05-29
Yay! A recent kernel update has solved the problem. It seems the kernel has reverted to using hdx for IDE devices, so except for another fstab change it's back to normal.

Another issue I had with VMware (not being able to bridge to a live IDE disk) which was caused by the same issue is also fixed.

---

### Post by armalite on 2007-06-06
> **MxGB said:**
> Yay! A recent kernel update has solved the problem. It seems the kernel has reverted to using hdx for IDE devices, so except for another fstab change it's back to normal.

Another issue I had with VMware (not being able to bridge to a live IDE disk) which was caused by the same issue is also fixed.

To me, this update caused only mayhem. Hotswap still doesn't work. This is what happened:

Long time ago my laptop had hda & hdc, with hdc a cdrom swappable bay. System hard locked by throwing out the cdrom, but using hotswap utility (and gnome-hotswap-applet) did the trick.

After some time in Feisty development, drives became sda & sdc. That was fine, hotswap applet stopped working but at this time no hard lockups when ejecting the cdrom drive (not disk, the drive itself since it's a bay). Using the simple command as root: 

echo 0 0 0 > /sys/class/scsi_host/host1/scan

That did the trick to let recognize the cdrom when reinserted in the bay. 

Now, sda & sdc are again hda & hdc. The funny thing is that hotswap doesn't work for me, so i can't rescan the drive. 

I have to inspect how to resolve this issue... :mad:

---

### Post by floflooo on 2007-10-16
Thanks armalite, your method works great

```

sudo su -
echo 0 0 0 > /sys/class/scsi_host/host1/scan

```

Now if that could be automated... I don't see any trace of ACPI event when I insert my cdrom bay. Maybe because, the device it considered a SCSI device? Is there a way to detect  a new SCSI device??

---

### Post by armalite on 2007-10-17
I just tried today with Gutsy. I found something really interesting, now when i reinstert the drive bay, the drive is recognized correctly. Wonderful!

Some months ago i tried using Gutsy, there were some improvements because kernel 2.6.22 got some new modules: bay and dock. Besides, there were no uevents, nor acpi events, so I had to manually force rescan the drive as stated above in this thread. I read at that time on some kernel upstream changelogs that bay module had some good patches that gone in the right direction, implementing ACPI events. These patches eventually found their way down to Gutsy :)

Today i tried to eject and insert the drive and voilà, everything worked. Ok, the kernel (specifically, dmesg) complaints when i eject the drive with the same messages it used to write with the 2.6.20 kernel, but no hard locks, no visible problems, so it should be ok, the pc doesn't explode and i'm fine with it. When i reinsert the drive, there seems to be an ACPI event and it actually does soft port reset and a rescan. This works and when i insert a cdrom it is recognized correctly.

[quote="Armalite"]Now, sda & sdc are again hda & hdc. The funny thing is that hotswap doesn't work for me, so i can't rescan the drive.[/quote]

This is obviously an old entry, because it is many months now that Feisty has sda/b/c drives even if they are Parallel ATA drives. IMHO, since hotswap does really work as intended, i really hope it will never rollback to hda/b/c.

---

