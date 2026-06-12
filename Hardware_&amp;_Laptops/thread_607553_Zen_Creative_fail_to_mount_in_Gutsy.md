---
title: "Zen Creative fail to mount in Gutsy"
date: 2007-11-09
forum: Hardware &amp; Laptops
---

### Post by SaihtamRent on 2007-11-09
Hi all, I am running a Kubuntu on Gutsy 

My laptop is a Toshiba M45 S331.

I own a Creative Zen V device, which I would like to connect to using amarok. I managed to do that with my former Suse 10.1 and 10.2, but I fail to do this using Gutsy. 

Here is the point : 

I can access the device using Gnomad2 (MTP connection works)
I recompiled amarok with mtp support enabled (I am not sure It was necessary) but still, amarok is not able to detect the device !!

My problem is : I cannot see how to mount the device: 
Here is the dmesg corresponding to the Creative plug 
[ 2155.712000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
```
[ 2160.736000] usb 5-2: USB disconnect, address 6
[ 2179.492000] usb 5-2: new high speed USB device using ehci_hcd and address 9
[ 2179.628000] usb 5-2: configuration #1 chosen from 1 choice
```

And now, I would like to mount it. How can I do ?

Thanks, 

Cheers.

---

### Post by SaihtamRent on 2007-11-10
I solved it. 

Actually I there is nothing to do... I am a bit ashamed, but to connect the Device in amarok, just click "connect" under the device tab. No need to get through the preference->device configuration panel. Actually the latter does not show that amarok is able to detect the device. I guess this is an amarok bug, or something like that. Still, a simple "connect" does the trick (no need for libmtp install which is already installed or amarok re-compilation, this was for old amarok versions).

---

