---
title: "USB Drive there but no accessible!"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by ratovan on 2007-05-07
I had a 320Gb USB drive working with 7.04 and tried to adjust the permissions (I wanted to share it out to another machine)

Anyway,long story short, when I connect the drive now it doesn't let me access it, But I can plug it into a FC6 machine and the drive works fine.

What I did (I think) was clicked on "Computer" right click on the USB drive (called USB-HDD) and clicked on the drive tab. I then entered some parameters in the "mount options" section, but left "mount point" blank. is there somewhere where Ubuntu stores these settings so I can remove them?

Hope this makes sense.

Thanks

I originally posted this in General, but moved it here.  

Any help greatly appreciated

---

### Post by NilsE on 2007-05-07
Might be in etc/fstab

Edit that an see if there is anything odd looking for the device.

---

### Post by ratovan on 2007-05-07
> **NilsE said:**
> Might be in etc/fstab

Edit that an see if there is anything odd looking for the device.

Nothing wierd in there.

in /media I see the "USB-HDD" created but it has a big red X on it.

from a shell, I see
d------------ 76 root root 32768 1969-12-31 19:00 USB-HDD_


Any other ideas?

Like I said before, if I plug this into my Fedora machine, it works fine.
I need to figure out how to have Ubuntu "forget" it has ever seen this device and make it look like a new device again.

---

### Post by ratovan on 2007-05-07
ok, through what I can basically describe as "pure luck" the drive has reappeared.

I was able to create a new directory in /media and mount the /dev/sdx1 in it.  then the device reappeared in the COMPUTER screen.

I sitll have my permissions issues, but that's another problem for another day

---

