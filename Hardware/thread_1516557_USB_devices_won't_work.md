---
title: "USB devices won't work"
date: 2010-06-23
forum: Hardware
---

### Post by alreadytaken4536 on 2010-06-23
Hi. I'm a (former) Windows XP user and I've decided to come to the wonderful world of Linux! I posted a thread on here a while ago regarding alternate boot options (booting from a live disc). The machine I'm using doesn't have a working CD drive any more, so I had to install it with Wubi. I've got everything working fine so far, I even installed Frets on Fire and it's working SO much better than that lag fest I was having with my Windows install. I downloaded the gstreamer codecs so that I can listen to music, and I want to play some files on my mp3 player, but the thing won't show up! A few hours ago I plugged in my mp3 player, and all of the contents on it showed up and I was able to look through them. Few minutes of just looking at my stuff, and the damn thing disappeared! So I can't view my mp3 player any more, and also, I have this neat piece of hardware that lets you connect a PlayStation controller via USB, but the red light on it that represents power won't light up. I'm thinking this means none of my USB devices are going to work.

---

### Post by sgosnell on 2010-06-23
The mp3 player may have changed USB mode.  Try toggling it between MTP and MSC if you can.  You may have faulty USB ports on your computer, or a bad internal hub.  If it's a hardware problem, there isn't much you can do other than replace the bad hardware or get a new computer.

---

### Post by VH-BIL on 2010-06-23
Did you try rebooting the computer and the mp3 player?

---

### Post by alreadytaken4536 on 2010-06-23
> **VH-BIL said:**
> Did you try rebooting the computer and the mp3 player?
Haven't rebooted yet, but I'll try.

Also, something I forgot to add. The filesystem on this particular player is FAT32. Not sure if that makes a difference.

---

### Post by VH-BIL on 2010-06-23
A reboot should solve this.

Fat file systems a standard for portable devices.

---

### Post by alreadytaken4536 on 2010-06-23
> **VH-BIL said:**
> A reboot should solve this.

Fat file systems a standard for portable devices.
Ok, I rebooted. My player showed up long enough for me to grab something and move it to my music folder, but disappeared again shortly thereafter, and my playstation adapter still won't work.

---

### Post by VH-BIL on 2010-06-24
The mp3 player might unmount itself for power management. When it does, to get it back you can try:
```
sudo mount /dev/sda /media/usb -t vfat -o umask=0
```

---

### Post by alreadytaken4536 on 2010-06-24
> **VH-BIL said:**
> The mp3 player might unmount itself for power management. When it does, to get it back you can try:
```
sudo mount /dev/sda /media/usb -t vfat -o umask=0
```
Interesting. My mp3 player is fully charged at about the time it disconnects. I'll see what this does.

mount: mount point /media/usb does not exist

Oh I suppose I have to change that last part to PHILIPS then don't I.

OH, I plugged it in again and Ubuntu gave me this. "Unable to load GoGear Aria. Error initializing camera: -60: Could not lock the device"

---

### Post by VH-BIL on 2010-06-24
You can create a mount point anywhere. If you want to use that mount point you can create it via:
```
sudo mkdir /media/usb
```

---

