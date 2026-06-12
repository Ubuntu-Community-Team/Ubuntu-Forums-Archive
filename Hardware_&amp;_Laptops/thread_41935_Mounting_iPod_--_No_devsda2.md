---
title: "Mounting iPod -- No /dev/sda2"
date: 2005-06-15
forum: Hardware &amp; Laptops
---

### Post by FalcTH on 2005-06-15
Hello, I recently got an iPod and I have been fiddling about with Ubuntu to get it working my favourite OS. 

I have a problem where I can plug it in and nothing happens,  
sudo tail -f /var/log/syslog gives me

Jun 15 17:01:48 localhost kernel: ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[000a2700141d0b5d]
Jun 15 17:01:48 localhost kernel: ieee1394: Node changed: 0-00:1023 -> 0-01:1023

when I plug it in, I run gtkpod and slick Sync and all I get is: 
iPod directory structure must be present before synching to the iPod can be performed.

I can't mount the iPod in the terminal because I simply don't know how to; I have followed the Wiki ([https://wiki.ubuntu.com//IPodHowto](https://wiki.ubuntu.com//IPodHowto)) but still absolutely no luck.
I have run DMESG and everything looks fine and repeatative with it plugged in and the same output when its disconnected.

I do an ls /dev/sda* and ls: /dev/sda*: No such file or directory
so I don't know if I should be using /dev/sda2 >_>

If you need more information, just tlel me what tp type and i'll paste it. XP
thanks in adance.

---

### Post by gnomeza on 2005-06-16
Hmm, if you have a Mac formatted iPod the relevant partition is /dev/sda3 rather than /dev/sda2.

But as you say, you appear to have no /dev/sda devices at all!?

Looks like you're trying t connect it via Firewire, have you tried connecting it via USB instead?

Something along the lines of
```
Attached scsi removable disk sda at scsi1, channel 0, id 0, lun0
``` should appear in dmesg output.

---

### Post by FalcTH on 2005-06-16
Yeah, i'm trying to use Firewire seeing as its much much faster for me.

I tried USB and it works! but its kinda slow since it ain't firewire...  :roll: 
But I have time so its good anyway. :D
I'll go into more the why the Firewire isn't working and sue USB for now.

thanks a lot!

---

