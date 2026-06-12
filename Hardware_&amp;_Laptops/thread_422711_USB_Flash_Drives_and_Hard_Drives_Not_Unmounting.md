---
title: "USB Flash Drives and Hard Drives Not Unmounting"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by jbarry on 2007-04-25
I have just Installed Fiesty in a Lenovo R52 Laptop. And I must say everything nice and good except for one thing (or maybe I'll find more things, but whatever). when I plug-in USB drives they are mounted without problems, but when I unmount/eject them the icon the desktop would disappear then a msg box will appear telling me that it cannot unmount the device. then nautilus would open a window of the drive and the icon in the desktop would reappear.

I have tried different kinds of flash drives and HD the same problem.

If I would just pull them out, then a msg would say that i did an unsafe thing and I must use the eject command to eject USB devices.

Anybody have a similar problem? Anybody have any ideas how to solve this?

thanks

---

### Post by mac.ryan on 2007-04-25
Just trying to guess here... among others it might depend also from:[LIST]
[*]not enough privileges to unmount the drive
[*]some processes still actively using the disk[/LIST]to test if it is case 1, you cold try to issue:

```
sudo umount /media/<devicename>
```to test if it is case 2 (better: a gnome application still accessing the media) you could try:

```
 bash /etc/init.d/gdm stop
```

(this will quit your gnome session!)
and once in the tty you can try:

```
eject /media/<devicename>
```

---

### Post by highenergy on 2007-04-25
Hi,

I have tried unmounting my usb HD and got the same result as you. I have a desktop computer. I think it's a feisty/edgy bug.

regards
H.E.

---

### Post by mac.ryan on 2007-04-25
BTW... do you have beagle configured to look into your removable drives? If yes, please see: [https://bugs.launchpad.net/beagle/+bug/59512](https://bugs.launchpad.net/beagle/+bug/59512)

---

### Post by stimpsonjcat on 2007-04-25
it's a [bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/63090"). workaround: [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/99538/comments/6]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/99538/comments/6")

---

### Post by jbarry on 2007-04-25
Thanks to All who posted...

The Bug Workaround Worked :) 

I just don't know what functionality is lost due to not having the 10-storage-policy thing.

---

### Post by Incompetnce on 2007-04-25
I have a siilar problem; the drive ejects/unmounts fine, but the little red light still flashes. no matter how long i leave it. and if i just pull out my USB stick some data is randomly lost. doesnt seem to necessarily be the last thing i put on there...
I dont want to experiment too much with this for fear of damaging my memory stick thinger...

will try workaround now...

---

### Post by Incompetnce on 2007-04-25
No. That workaround didn't help. The little light is still flashing, but Ubuntu seems to think the drive has been unmounted. Any ideas?

---

### Post by Incompetnce on 2007-04-26
Even shutting down my computer before removing my flash drive seems to have corrupted data on it.

Does anyone have any suggestions as to how to sort this out?

---

### Post by mac.ryan on 2007-04-26
I personally manage to overcome the difficulties via sudo: either "sudo umount" or "sudo eject" work, but I am unable to tell you when you should use one or the other... I simply try one and eventually try the other if the first didn't make the trick.

If my understanding of mount params is correct, I would limit the risk of data loss issuing the "**sync**" parameter: this way the data would immediately be flashed to the key, without delays.

---

### Post by pbeck on 2007-04-28
I can certainly confirm that I'm having this problem too. There seem to be a couple of workarounds including using
sudo umount /media/device
or
sudo eject /media/device

although for me these do not turn off the external hard drive, which seems a bit sketchy. Hopefully this issue will be resolved soon.

---

### Post by Incompetnce on 2007-04-29
The disc unmounts fine, but then the light does not stop flashing. what is this sync parameter?

---

### Post by mac.ryan on 2007-04-30
> **Incompetnce said:**
> what is this sync parameter?

sync eliminate the writing buffer, so that data are flashed (almost) as soon as they appear in userspace. However, umount should flush the write buffer automatically, so even if the light still flashes, the writing should have been completed the moment the drive is unmounted.

For extra security, before to umount you could run

```
sync
```

in a terminal (it also flushes the buffers).

---

### Post by red_five on 2007-05-06
Here's a possible workaround for Nautilus; it's a script that can be executed by Nautilus on the Eject command, along with an addition to the /etc/sudoers file to allow ejects without a password.

[https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/63090/comments/39]("https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/63090/comments/39")

I've added the script, but I don't have my thumb drive handy right now, so I can't test it yet.

---

