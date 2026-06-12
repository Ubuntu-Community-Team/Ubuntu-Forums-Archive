---
title: "FIX: Fuzzy screen in 7.10 for ATI IGP 34x cards"
date: 2008-03-07
forum: Hardware &amp; Laptops
---

### Post by Helix. on 2008-03-07
Hello

I do not think anybody has started a thread on how to fix this. All I could find was people asking how to fix it. So, here's how I did it.

I know this works on hp pavilion ze5400. It most likely will work on other laptops with a ATI IGP 340m.

You need:
Ubuntu 7.10 / Any distro with the "fuzzy screen"
Ubuntu 7.04 LiveCD

It's quite simple: all you need to do is copy drivers to your xorg driver folder.

**Boot in recovery mode, or use the "vesa" driver!** You need to be able to see what your doing. :)

Once in recovery mode (or where you can actually see the screen,) open Synaptic. Search "xorg", then lock all packages that begin with "xorg-driver".

Put the livecd in your cd drive, then issue these commands:

```
sudo mkdir /mnt/ubuntu
sudo mount /media/cdrom0/casper/filesystem.squashfs /mnt/ubuntu -t squashfs -o loop
```

*Note: /media/cdrom0 may vary

This will make a new directory in /mnt called ubuntu, then it will mount the actual liveCD image to ubuntu.

Next, we need to make a backup of the xorg drivers. 

```
sudo cp -r /usr/lib/xorg/modules/drivers /usr/lib/xorg/modules/olddrivers
```

Then remove the driver folder...

```
sudo rm -r /usr/lib/xorg/modules/drivers
```

Then, copy the drivers from the Ubuntu 7.04 liveCD to the drivers folder.
```
sudo cp -r /mnt/ubuntu/usr/lib/xorg/modules/drivers /usr/lib/xorg/modules/
```

Your done! Reboot, and be amazed! :guitar:
Make sure you remove the liveCD after reboot, so it won't start up.

In case it doesn't work, do this:
```
sudo rm -r /usr/lib/xorg/modules/drivers
sudo cp -r /usr/lib/xorg/modules/drivers/olddrivers /usr/lib/xorg/modules/drivers
```

This is my first tutorial, so if you see anything wrong, tell me. :)

---

