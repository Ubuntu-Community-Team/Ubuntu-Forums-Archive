---
title: "PCMCIA Compact Flash adapter"
date: 2006-06-18
forum: Hardware &amp; Laptops
---

### Post by Tycho on 2006-06-18
Hello,

I have just installed ubuntu on my laptop(inspiron 8200) and am running into problems when using my compact flash card from my camera.

I have a pqi branded pcmcia compact flash adapter that I use to access the flash card with. When I insert the flash card into the adapter I see the following in the nautilus "Computer" location.

[IMG]http://home.earthlink.net/~tycho316/images/computer.png[/IMG]

The entry titled "EOS_DIGITAL" is the compact flash card from my camera. When I double click on that entry to get at the pictures I get the following error message.

[IMG]http://home.earthlink.net/~tycho316/images/error.png[/IMG]

Does anyone know how to make this work as expected?

---

### Post by Tycho on 2006-06-19
I have something working but it still isn't working quite right.

I decided to make it look as much like a cdrom as i could.
[LIST]
[*]I created a directory /media/flash0 and made links named /media/flash and /flash that point to it.
[*]Added "/dev/hde1       /media/flash0   auto    user,noauto,rw  0       0" to /etc/fstab.
[*]Added "/dev/hde1" to /etc/pmount.allow
[/LIST]

There is now a flash0 entry in my nautilus computer location at all times. When I insert the flash card the "EOS_DIGITAL" entry appears but doesn't work properly. I need to double click the flash0 entry to access the drive. The computer also appears to be caching reads and possibly writes to the disk but I would like to just be able to pull the card out without unmounting it first.

I assume there must be an easy way to simply mark the drive as removeable and everything should just work but I don't see where that is done.

---

### Post by revilot on 2006-07-04
I'd like to find a solution to this as well.

---

### Post by trueg on 2006-08-08
I have the exact same problem with 6.06 on a Dell Latitude D810 with a Kodak PCMCIA CF adapter.  I was able to get it mounted manually with the following...

added to my /etc/fstab
/dev/hda1       /media/cf       vfat    defaults,user,noaudo    0       0

to mount
sudo mount /dev/hda1 /media/cf (/media/cf already exists)

My CF cards comes up as hda1 not hde1 (my laptop has serial hard drives).  I have to unmount it manually.

In nautilaus it comes up as CANON DC, but I get the same error as you when I try and access it.

---

