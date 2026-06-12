---
title: "initramfs shell - /dev/Mango-root does not exist"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by MartinHansell on 2009-02-05
Heeeeeelllllllllpppppp?#@@!@#%^&%&#!!

I upgraded from intrepid kernel 2.6.27-9 to 11 yesterday and the whole thing just died on me...  It was part of the standard upgrades, but for some reason only a partial upgrade could be performed.

Now when I try to boot I get the dreaded following...

Gave up waiting for root device.....etc
ALERT! (sounds serious)..-root does not exist.  Drooping to hell!

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)

then the cursor flashes like so...
(initramfs)_

so.... am I completely screwed?

I tried to reinstall using the Oct live cd for 8.10, but all that did was make it faster to reach hell.  I got as far as changing to system root (from live cd root) to use apt-get and install lvm2 so that my lv's would be recognized by the system, but bash did not think apt-get was installed, even though it was there, plain as day in /etc.  So i got stuck there.

A side effect of this is that when i try to boot in recovery mode the system shows that it cannot "enumerate" any usb device.  i guess that's just a hardware-failure-symptom of the bootroot failure?

Any ideas where do i go from here?
Many thanks....
Martin

---

### Post by alterKrieg on 2009-02-23
Same problem here.  I'm booting ubuntu from a USB because the CD drive on the comp is shot.  I made a live USB from unetbootin and tried most every variation of install I can come up with.  So far, attempting to boot to anything besides puppy linux yields this same boot error.

I tried manually having the comp initialize the kernel but it told me that my kernel was corrupted.  Is there something in this process causing this?

Any help would  be great.

---

