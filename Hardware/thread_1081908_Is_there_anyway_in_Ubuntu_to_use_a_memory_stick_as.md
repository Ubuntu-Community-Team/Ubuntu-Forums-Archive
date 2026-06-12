---
title: "Is there anyway in Ubuntu to use a memory stick as virtual RAM?"
date: 2009-02-27
forum: Hardware
---

### Post by Macfunky on 2009-02-27
I only read about this yesterday as windows vista has a program called readyboot that allows this. I thought it was an interesting idea and i was wondering can you do this in Ubuntu as well?

---

### Post by albandy on 2009-02-27
yes, but ensure your stick is faster than the your HD.

you can do something like this:

1.- Put your stick, it probably will be mounted in /media/disk
2.- Type in a console: sudo dd if=/dev/zero of=/media/disk/swapfile bs=1024 count=1310720
this will make a file about 1GB 
3.- when created type sudo mkswap /media/disk/swapfile
4.- Stop your HD swap by typing sudo swapoff -a
5.- Start your pendrive swap: sudo swapon /media/disk/swapfile

---

### Post by Macfunky on 2009-02-27
I read that my stick has to be fast alright. What kind of speeds are we talking about for it to be sufficient for the job?

---

### Post by albandy on 2009-02-27
Simply test if your computer runs faster using it

---

### Post by davidsrsb on 2009-02-27
USB Flash is slow to write, so I doubt that you will see any improvement. When a sector has been used, writing just one byte means copying the modified sector to a new part of the memory, remapping and erasing the whole original block. Normal ram is very cheap, any PC too old to take cheap ram is not going to have a true usb-2.0 port

---

### Post by Macfunky on 2009-02-27
Points taken. I have a descent spec laptop that is sufficient. I also have an older desktop (it does have usb 2.0). I understand what you are all saying but would it be quicker for a usb to act as the swap instead of a hard drive (provided its a a good speed flash stick and a 7200rpm hard drive)? Just would be curious if i could get anything more out of my old (older really. Its not that bad) desktop. I have already upgraded the ram to as much as the motherboard supports

---

