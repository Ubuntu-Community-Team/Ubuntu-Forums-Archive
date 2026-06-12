---
title: "Adding a second internal hard drive"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by LordBenjamen on 2009-07-29
I'm kinda a noob to linux but i'm really starting to love it.. i've already filled my 250g hard drive up and i've been trying to add another 250g hd from my old computer.. I've managed to get gparted and format the drive.. its formated to EXT3 with disk label /dev/sda but i can't figure out how to get it so i can use it.. if someone can help me i'd be very grateful.. thanks.. i'm not very good with ubuntu so i might need a some deep explaining..

---

### Post by merlinus on 2009-07-29
You need to create a mountpoint for it, e.g. /media/sda, and then add an entry in /etc/fstab.

For example:

/dev/sda1 /media/sda ext3 relatime 0 0

---

### Post by LordBenjamen on 2009-07-29
when you add it to /etc/fstab, where exactly do you put it?

---

### Post by merlinus on 2009-07-29
```
gksudo gedit /etc/fstab
```

add the line to the end of the file.

---

### Post by themusicalduck on 2009-07-29
I find that after reformatting a drive I need to reboot until the drive will appear. You don't really need to edit fstab unless you want to mount the drive in a specific location or have it mount automatically on startup.

Just reboot and see if it appears, you might need to set permissions to allow write access which you can do with the command

```
sudo chown *username*:*username* -R /media/*diskname*
```

---

