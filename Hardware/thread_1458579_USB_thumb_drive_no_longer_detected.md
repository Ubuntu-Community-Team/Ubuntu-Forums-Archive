---
title: "USB thumb drive no longer detected"
date: 2010-04-20
forum: Hardware
---

### Post by blittle on 2010-04-20
Hello,

my issue is this:

I ahe a Dell Inspiron 1501 that dual boots to Ubuntu 9.10 and Windows Vista. I was using Windows for an app that doesn't work well in Ubuntu when at one pint, Windows goes into sleep mode while my Sony microvault 8 GB drive was still inserted. I didn't think anything of it as I shut the machine down later. The next night, Windows tells me that the USB device cannot be read or detected. I inserted the drive again in Windows, the same issue. Rebooted to Ubuntu and there was no error, just no mounting of disk.

Crap like this only happens to me when using Windows and there seems to be a lot of apps out there for file recovery; not disk recovery. Does anyone know of any Linux solutions to recovering a USB thumb drive that is no longer detected? The thumb drive lights up detecting that it still takes power.

Thanks is advance.

---

### Post by dabl on 2010-04-20
When the thumb drive is connected, run ```
sudo fdisk -lu
``` and see if it is detected.  If yes, then you could potentially mount it manually, and copy off your data.

Another approach (with it connected), run Gparted and if it shows up, right-click it and choose "check", and see if is fixed.

And then there's Super Grub Disk ....

After/if you've salvaged your data, I would use "dd" to restore it to its original brain-dead configuration, then use Gparted to make a new partition table and format it.

---

### Post by blittle on 2010-04-20
Cool. Will try later this evening. I have gparted because that was used to make my partions in the first place.

Thanks

---

