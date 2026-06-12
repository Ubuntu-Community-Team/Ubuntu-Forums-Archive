---
title: "400gig USB2 Disk Mounts but can't be accessed"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by drcarlos on 2007-06-19
I am new to Linux but am setting up Kubuntu (Fiesty) on my Dev machine at work and my Dell Poweredge Server at home.
I have a number of USB2 Disks I want to use and am trying to mount a 400gig Hypertec drive on my desktop machine at work (as it only has 20gig internal disk) for VMWare images.
Plugging the disk in brought nothing (the menu came up but nothing happened when I click on open in new windows) so I went into Disks and Filesystems and created a new mount point in media called 'usb2400' mounted the disk with an NTFS filesystem, with files belonging to my username (if I didn't do this koqueror kept telling me I had no access to even browse it), I have made it writeable and and enabled it at startup when the enable button is clicked it show enabled and has a partition of 372.6gb.
Once this is done I can open the disk in a new windows but cannot copy anything here i am a bit stumped does anyone have any ideas?

Cheers,

Carl.

---

### Post by renzokuken on 2007-06-19
linux cannot natively write to NTFS filesystems, so although you enabled write access, it simply cannot do it.

you need the ntfs-3g driver to do this.

in fiesty this is very easy, just run

```
sudo apt-get install ntfs-config
```

this will download and install the ntfs-3g driver and then ask you if you would like it to automatically detect and then mount any ntfs drives for you with full read/write access

---

### Post by drcarlos on 2007-06-19
Thanks will give that a go.

Carl.

---

