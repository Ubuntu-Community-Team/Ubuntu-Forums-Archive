---
title: "USB Harddisk will not unmount through interface"
date: 2007-05-10
forum: Hardware &amp; Laptops
---

### Post by PleegWat on 2007-05-10
Hi,

I've got an issue with my external USB harddisk. 

My desktop computer, with ubuntu feisty, is always on. I've got an external harddisk (brand targa according to the case, prolific and samsung according to the hardware information, so that's probably what's inside).

It is detected fine, and mounts automatically. However when I'm done with it, and want to turn it off, it doesn't seem to be possible to do that via the interface. the right-click menu on the desktop or panel icon only gives an eject option, which gives an error message. Using the eject command in the terminal, I only get error messages as well. However, using the following umount command

```
sudo umount /media/NDAS400
```

unmounts the drive successfully, and if I then turn off the drive I do not get any errors.

So, how do I reconfigure this thing so the interface will offer an unmount option, rather than an eject one?

---

### Post by Burnspot on 2007-05-10
As far as I know and have read, this is a bug with Feisty. Many have reported the same problem and I get the same with my USB HDD.

---

### Post by slartibartfast42 on 2007-05-28
I got the same problem, here's how I solved it:

I've activated the feisty-backports repository in system's administration tool software sources (sorry, I don't know what's it called in english, I'm using Ubuntu in german language). When calling the Update tool afterwards, I get some HAL related packets available for updating. After conducting the update and rebooting the machine I'm now abel to unmount my USB harddisks via rightclick and choosing "dimount volume" (again, I'm not sure if that's the correct name of the menue's target in english Ubuntu).

Seems, that the disks are dismounted correctly.

Bye,
Slartibartfast

---

### Post by slartibartfast42 on 2007-05-28
Ok, I just realized, that by using my solution mentioned above the harddisk will be unmounted but not powered off :-( .

Bye,
Slartibartfast

---

