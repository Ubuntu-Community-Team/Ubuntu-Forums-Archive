---
title: "How to appoint a certain device name to a device?"
date: 2008-09-24
forum: General Help
---

### Post by shadowcaster00 on 2008-09-24
I want to mount my built-in SD card reader as /home. So I add a line in fstab to mount /dev/sdc as /home.  However, the card reader would not be /dev/sdc if there is an usb drive present.  I can't specify UUID because sometimes I'll change the SD card.

Can I assign a specific device name to a device?  More specifically, assign /dev/sdc to my built-in SD card reader.

---

### Post by Pro-reason on 2008-09-24
You're talking about mount points, rather than device names.

You can mount anything at any location with the ”mount” command (see “man mount”).  To have things consistently mount at a certain point, edit your /etc/fstab file.

Editing /etc/fstab will not work for your purposes, because you want to have various different devices (SD cards) mount at the same point.

Each SD card is a different device.  The reader is just a glorified cable that connects them to your computer.

---

### Post by Vivaldi Gloria on 2008-09-24
> **Pro-reason said:**
> Each SD card is a different device.  The reader is just a glorified cable that connects them to your computer.

+1

You can appoint a certain device name to a card. Do you always use the same card?

---

### Post by Pro-reason on 2008-09-24
> **Vivaldi Gloria said:**
> +1

You can appoint a certain device name to a card. Do you always use the same card?

He said he sometimes changed the card.

It's not possible to assign a /dev/*xxx* name to anything.  It is done automatically, and depends on how things are physically connected to your machine.

It is not possible to assign a UUID either, but they are at least unique to each device/partition.  

You can assign a volume label.  It is like UUID but better.

If you want to use different cards, but have them always all recognised as being the same thing, there is no 100% reliable way of doing that.

Hmm, on second thoughts, you could give them all the same volume label, and then mount them according to that label.  That should work, though it would cause problems if you ever connected more than one at once.

---

### Post by Vivaldi Gloria on 2008-09-24
> **Pro-reason said:**
> He said he sometimes changed the card.

Sorry I missed that.

> It's not possible to assign a /dev/*xxx* name to anything.

I can think of a few ways to do it. 

**1)** To begin with you can simply use the name

```
/dev/disk/by-uuid/<???numbers???>
```

**2)** You can also write an [[COLOR="Sienna"]udev[/COLOR]]("http://www.archive.org/details/HampshireLinuxUserGroup_udev") rule. 

**3)** Or you can even use [[COLOR="Sienna"]hal[/COLOR]]("http://www.mythic-beasts.com/~mark/random/hal/").

---

### Post by unutbu on 2008-09-24
shadowcaster00, perhaps you can do this:

Stick an SD card in the card reader.
Run
```

blkid

```
This will show you the UUID of the SD card. Copy it down.

Unmount the SD card.
Pop in a different SD card.
Run
```

sudo tune2fs -U UUID /dev/sdXY
```
(changing UUID to the UUID of the first card and changing /dev/sdXY to the device name of the home partition on the SD card)

The tune2fs command will set the UUID on the second card to the same UUID as the first.

Repeat for every SD card.

Now you can edit /etc/fstab and mount the SD cards at /home by specifying the partition by UUID.

---

