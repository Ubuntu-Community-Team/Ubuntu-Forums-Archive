---
title: "Camera problem"
date: 2008-06-23
forum: Hardware
---

### Post by _Nicko_ on 2008-06-23
Hi all!
I think I've made a huuuge mistake. If someone can give me a hint, I will be very grateful!

The first important thing is that I just started using ubuntu, so I'm not good at it.

I have a Genius P7545 digital camera that I wanted to use in ubuntu. It was detected as a USB drive, but it couldn't be mounted, so I was not able to browse the camera through the file system or transfer pictures.

I found some commands on this forum and I made the mistake of using them to manually mount the camera.

Created a new mount point: sudo mkdir /mnt/camera
Mounted the camera: $ sudo mount /dev/sda1 /mnt/camera -t vfat -o umask=000

Now my camera is completely messed up. It doesn't turn on any more and it's not detected by the computer either. Not even in windows. 

Do you think something happened to the camera's memory? In fact I think it did, I don't see any other alternative.

What can be done in this situation? The camera is still in the warranty period, but I would prefer not taking it to a service.

Any help will be appreciated. 
Thanks a lot!

---

### Post by matt.taylor on 2008-06-23
If there is a reset button on your camera that's a first try, but if you have everything on a SD Card or another type of card take it out first.

I have never had any problems with Mounting things in Ubuntu (Mainly my iPod Touch).

You can always try the unmonunt command line, while the camera is plugged in. (Im sure somone will post)

---

### Post by pmlxuser on 2008-06-23
have you tried unmount it.
possibly i would also delete all the mount points I created

$sudo umount /sudo mount /dev/sda1 /mnt/camera -t vfat -o umask=000
$sudo rm  /mnt/camera

restart computer ans see what happens

---

### Post by prshah on 2008-06-23
> **_Nicko_ said:**
> 
Created a new mount point: sudo mkdir /mnt/camera
Mounted the camera: $ sudo mount /dev/sda1 /mnt/camera -t vfat -o umask=000


These commands don't even _touch_ your camera. There is nothing in these commands that refers to your camera. Bad luck, looks like something else is wrong!

---

### Post by matt.taylor on 2008-06-23
> **prshah said:**
> These commands don't even _touch_ your camera. There is nothing in these commands that refers to your camera. Bad luck, looks like something else is wrong!

I think its possible it might have "touched" the camera, it depends on how the camera talks to ubuntu i spose.

But the fact the camera will not even turn on anymore is a bit of a grey area

---

### Post by prshah on 2008-06-23
> **matt.taylor said:**
> I think its possible it might have "touched" the camera


The only way it could have touched the camera is if he was running a system _without_ a hard disk drive, eg. live CD only. The primary hard disk drive will take sda device, not the camera. He would have got an error trying that mount command, because, as likely as not, sda1 would already have been mounted.

---

