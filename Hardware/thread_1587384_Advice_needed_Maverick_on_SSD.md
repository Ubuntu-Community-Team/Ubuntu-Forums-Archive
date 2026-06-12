---
title: "Advice needed: Maverick on SSD"
date: 2010-10-03
forum: Hardware
---

### Post by schmickey on 2010-10-03
I just installed the 10.10 RC on my Acer 1830T which has an Intel X25-M 80GB (generation 2) SSD in it.  It seems to be working well, but I need to know how to alter my "fstab" file correctly to work with the SSD.

I have read that "noatime" and "discard" flags need to be set but I'm not sure exactly were to put these flags and having tried it once and rendered my Ubuntu install unbootable, I come seeking precise advice.  I've just re-installed 10.10 and have all updates.

Below is my current "fstab" in it's entirety:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=9571d6a6-1b60-4466-9b58-d7d31023842b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=077bdb22-6c6d-4082-8f5b-34400842d8d4 none            swap    sw              0       0

I'm assuming I should place the discard and noatime flags after the "errors=remount-ro" with commas to separate the flags.  Correct?  And only for the entry that concerns the first UUID (root).

---

### Post by IcarusR on 2010-10-03
> after the "errors=remount-ro" with commas

Yes that's correct.

Loads of stuff on optimising ssd on the net.

Lot of suggestions here
[http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment]("http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment")

More links here
[http://ubuntuforums.org/showthread.php?t=1463870]("http://ubuntuforums.org/showthread.php?t=1463870")

People say to mount swap file, temp files & logs to ram disk to minimise write to the ssd.

---

### Post by schmickey on 2010-10-03
@IcarusR:
Thanks for the reply and links.  I'm told the discard flag needs to be set to enable TRIM for the SSD which is built into the new kernel. I'm curious why the installer didn't set that flag during install.

Maybe in a future release it will be automatic.  Seems to me that it should be a default for installing to an SSD.. at least, for an Intel SSD (I know nothing about the other brands).

---

### Post by piemonkey on 2010-10-12
> **IcarusR said:**
> People say to mount swap file... to ram disk to minimise write to the ssd.

Correct me if I'm wrong, but isn't a swap file used like overflow ram? So if you mount a swap file as a ram disk, you'll just waste time swapping out things from memory to yet more memory, and moving them back when needed.

---

### Post by eyelessfade on 2010-10-29
> **piemonkey said:**
> Correct me if I'm wrong, but isn't a swap file used like overflow ram? So if you mount a swap file as a ram disk, you'll just waste time swapping out things from memory to yet more memory, and moving them back when needed.

Yeah, better just to remove the swap. Of cause if you are out of ram, your also out of luck. I have 12GB ram on my computer so I have removed swap a long time ago.

---

### Post by schmickey on 2010-10-29
Thanks for the tips.  I reduced swappiness to 1 and directed the browser cache to a tmpfs (ram).  The purpose being to reduce small-file writes to the SSD which is what reduces their lifespan.

After applying a number of other tweaks as well, this is the fastest Linux machine I've ever used.  Boots to desktop in 8 seconds and shuts down to power-off in 3 seconds.  Amazing.

---

### Post by solnyshok on 2010-10-29
I confirm that. I have Toshiba Portege R630 with Meerkat x64 on the same SSD with i5-450m, 4GB RAM. Same boot and shutdown times. Hibernation is pretty quick too, but not faster than reboot. Still I use it, because it protect my work session against power failure.

They need to rethink the whole concept of bootsplash. There is no time for animations anymore.

---

### Post by schmickey on 2010-10-30
I implemented all the tweaks and adjustments shown in the thread below.  They've made a real difference in performance and should increase endurance in the long run.

[Tuning Solid State Drives for Linux]("http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/")

Be sure to read all three pages there.

---

