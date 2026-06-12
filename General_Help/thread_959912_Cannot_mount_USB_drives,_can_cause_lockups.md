---
title: "Cannot mount USB drives, can cause lockups"
date: 2008-10-26
forum: General Help
---

### Post by svriderpokey on 2008-10-26
My eee can no longer mount USB drives.  If I plug one in, nothing happens.  If I try to mount it @ the command line or if I try to open Places>Computer my whole system locks up.  Ctrl Alt BackSpace does nothing at all. 

I don't know if it's related, but If I go to Places>Computer with no USBs pluged in, there is an Icon for "USB Drive"

I'm pretty sure it broke when I tried the following commands to reduce disk writes to my SSD.
```
sudo rm -f /etc/mtab
sudo ln -s proc/mounts /etc/mtab
```

The suggested fix is:
```
sudo rm etc/mtab
cp /proc/mounts /etc/mtab
```

but this is not working for me.

The other clue to this (if it's not already blatantly obvious) is that I have absolutely no idea what I'm doing.

---

### Post by Thanh-BKK on 2008-10-26
Hi :)

Have you tried the command "lsusb"..? Try it, the USB drive may just "magically" mount itself after that.

I have this issue (and a few other people, too) since updating to the 2.6.24-21-generic kernel, now USB drives connected to USB 2.0 hubs are no longer mounting, but doing a "lsusb" somehow mounts them (respectively tells the kernel to "go and look if something's there!")

Weirdly, if a USB 1.1 hub is used, the devices will mount fine, and so they will when you plug them directly into a MoBo USB socket. Just not through a 2.0 hub. I filed that bug at launchpad.

Problem with laptops is that many of the onboard USB sockets are nevertheless "hub" sockets, so it may be the case with the Eee-PC.

Best regards......

Thanh

---

### Post by svriderpokey on 2008-10-26
It lists it under "Places" in the Gnome menu, but it is not mounted.

lsusb shows it, but still not mounted.

Here goes

---

### Post by svriderpokey on 2008-10-26
OK, so I hovered over the icon, and the tooltip says "mount" so I clicked the icon and nothing happened other than the menus went away.  Good news is no system lockup, but bad news is now the Gnome menu will not open. It does nothing at all.
EDIT: the whole gnome panel does nothing at all. it is completely unresponsive to clicks or hovering.  The clock has not even changed time.  It still shows 8 minutes ago.

---

