---
title: "Kernel panic caused by external USB optical drive"
date: 2016-06-06
forum: Hardware
---

### Post by John Jason Jordan on 2016-06-06
Xubuntu 14.04, up to date on System76 Bonobo Extreme, about a year and a half old. Xubuntu has always been rock solid.

A couple months ago I bought a USB 3.0 external DVD drive from Amazon: [http://tinyurl.com/hq2wctd]("http://tinyurl.com/hq2wctd"). The drive generally works fine, but occasionally I try to play a DVD that is not in perfect shape, and the drive ends up endlessly seeking, even long after I have killed the software that was accessing the drive (e.g., VLC). I am unable to eject the media, so the only solution is to disconnect the drive. Sometimes this works, but other times the computer locks up tight and I get flashing lights, e.g., a kernel panic. 

I have other USB 3.0 drives, including a 4TB external drive, and they never cause problems. If I accidentally unplug one while data is being written the worst that happens is that I get corrupted data. Unplugging a USB device should not cause a kernel panic.

I have scoured the forums for possible solutions, but have found nothing. I really need some suggestions. Even if your suggestion is not the solution, it might jog other minds into thinking of possibilities. I am at my wits end here!

---

### Post by DuckHook on 2016-06-07
> **John Jason Jordan said:**
> Unplugging a USB device should not cause a kernel panic.Actually, this is not so.

Consider: USB devices, and especially storage devices, access system memory directly and hook directly into the guts of the kernel. Simply pulling the cord when the kernel is counting on the device's continued presence for its operating equilibrium is like pulling the guts out of a living thing. The real surprise is that the kernel handles a HDD disconnect so well; not that it panics in the case of your DVD. Corrupted data should be the least of the damage. This is why Linux has the convention of mounting/unmounting: doing so tells the kernel that the storage device is no longer available&#8213;precisely to avoid kernel panics.

The next time your DVD hangs, do:```
ps -eF
```...and look for any process involving USB storage. In addition to shutting down VLC, try killing any residual process that is accessing the DVD drive. [This]("http://ubuntuforums.org/showthread.php?t=1503332") thread shows you how to kill a process. This is initially going to involve some detective work, but you will know that you've got the right process once the act of killing it stops activity on the drive. Then unmount the drive before pulling the cord.

As a general rule, when something hangs or misbehaves in any OS (not just Linux) we should try an elegant powerdown before pulling the plug. The above steps are designed to do that.

---

