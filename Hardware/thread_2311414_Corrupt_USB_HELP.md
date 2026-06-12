---
title: "Corrupt USB HELP"
date: 2016-01-27
forum: Hardware
---

### Post by Jacob_Collins on 2016-01-27
Alright so I'm going to tell the story from the truth
I thought it would be a good idea to full format my USB, I thought it was done so I unplugged and realised that it wasn't formatted(I am new to Linux)
Now whenever I plug in my USB, my Linux computer doesn't notice it at all. I have a blue light that comes on whenever my USB is connected to my computer and the blue light is on but if i go to Files, it doesn't show my USB :( plz help :)

---

### Post by sudodus on 2016-01-27
Welcome to the Ubuntu Forums :-)

Are there any files that you need to save on the USB drive? (I guess not, but I ask anyway.)

Is it a USB pendrive (flash drive) or a USB hard disk drive or a USB SSD?

You can create a new partition table and new partitions with or without file systems on a mass storage device (for example a USB drive or an internal drive) with ***gparted***. If the drive is 'too corrupted' you may need to wipe the first megabyte for it to work. These operations can be done automatically with ***mkusb***.

***gparted*** is already available in the Ubuntu desktop iso files, and are ready to use when you run a live system (booted from a DVD disk or USB pendrive). You can also install it into an installed system via the ***Ubuntu Software Center*** or the terminal window command line

```
sudo apt-get install gparted
```

***mkusb*** can be installed from a PPA

```
sudo add-apt-repository universe  # only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb
```

See this link for more details: [mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

---

### Post by Jacob_Collins on 2016-02-08
Thanks, but now my whole computers stuffed XD
(Not because of usb)

---

