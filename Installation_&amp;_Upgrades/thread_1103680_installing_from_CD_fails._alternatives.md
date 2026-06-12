---
title: "installing from CD fails. alternatives?"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by misterloogs on 2009-03-22
I'm trying to install Ubuntu on a Dell 2650 laptop using a CD with the iso burned onto it. The install procedure starts, but the CD drive konks out midway, and no further progress is made (the CD drive sounds like it's stuck, and I'm 99% sure it was wrecked a while ago).

What are my alternatives? I wanted to try booting off of a thumb drive that had the iso on it, but I'm not sure if that's possible. When I restart the machine and go to the BIOS setup, these are the boot options presented:
  CD-ROM Drive
  Floppy Devices
  Hard Drive
  Cardbus NIC
  Onboard NIC
Do any of the above correspond to the USB drive? I'm open to other options; just that booting off of a USB drive seemed the easiest to try.

---

### Post by crusaderbond on 2009-03-23
If you copied the mbr from the cd, and put the contents of the cd on your thumb drive, it might work, emphasis on the might. I would recommend scavenging up an old cd drive, or borrowing one for installation purposes.

---

### Post by misterloogs on 2009-03-26
Thanks for the reply.

What exactly is the mbr?

Also, if I were to try to boot from the thumb drive, which boot option should I move to the top of the list (see original post)?

In case the thumb drive option does not work, I will find another CD drive. Will I need to replace the built-in CD drive with it (i.e. disconnect the old one and put the other one it its place), or can I somehow use an external CD drive and boot off of that instead, given the boot options presented to me (again, see original post)? Any suggestions are appreciated as I am very new to all this.

---

### Post by misterloogs on 2009-03-30
I'm having difficulty preparing my USB stick so I can try booting off of it. I'm using the instructions on [https://help.ubuntu.com/8.10/installation-guide/i386/boot-usb-files.html]("https://help.ubuntu.com/8.10/installation-guide/i386/boot-usb-files.html") - "Copying the files - the easy way" - and the very first command I try is failing:
```

$ zcat ~/boot.img.gz > /media/disk
bash: /media/disk: Is a directory

```
A couple of things about this:
1) Is /media/disk likely to be what I'm supposed to use for the target, as opposed to something that lives under /dev? I plopped a small text file on my USB drive and found that I could read it from /media/disk. I also search for the file under /dev using the 'find' command, but it wasn't found.
2) If I need to add a partition on /media/disk to get the above command do work, how do I do so? I'm running the command on a system running Linux.

---

### Post by Mark Phelps on 2009-03-31
> **misterloogs said:**
> Thanks for the reply.

What exactly is the mbr?

The Master Boot Record.  You will be modifying it when you install Ubuntu.

> 
Also, if I were to try to boot from the thumb drive, which boot option should I move to the top of the list (see original post)?
 
I don't see an entry in your boot list for USB.  So, you won't be able to boot from USB.

> 
Will I need to replace the built-in CD drive with it (i.e. disconnect the old one and put the other one it its place)
Most probably.  To connect an external CD Drive, you would plug it into an USB port -- and then, you would need to be able to boot from USB, an option that's not in your list.

And, you can't replace the builtin CD drive with ANY drive, you need to replace it with the same make and model, or another one that is compatible with your laptop.

---

