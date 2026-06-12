---
title: "Ubuntu 8.10 on External HDD"
date: 2009-01-18
forum: Installation &amp; Upgrades
---

### Post by DeadRobot on 2009-01-18
Are there any tutorials for installing Ubuntu 8.10 on an external HDD?

Or do you just install it the same way you would if it was an internal hard drive?

---

### Post by Pumalite on 2009-01-18
Try this:
[http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman](http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman)

---

### Post by Herman on 2009-01-18
:) Yes, there are some good reason why someone might need to install Ubuntu in an external USB hard disk. 

Just remember though, that an external hard disk drive is much more fragile than a USB flash memory stick, if you'll be carrying it around. So if you're choosing to install it that way for the purpose of portability, just be careful. My wife tripped on the way up the stairs one day and the bag she had her external hard drive in crashed on the floor and the impact ruined a good external hard drive instantly. She lost all the files she had in it. 
Flash drives are much sturdier than hard disks.

Most external hard drive cases I've seen don't have any ventilation or cooling fans either, for running an operating system full-time. They're mostly designed as file storage devices, which probably would not need to be spinning all the time. In hot countries like the country I live in, even hard drives inside computer cases that have good cooling fans need to be monitored for temperature.

Thirdy, while Ubuntu will run quite well from an hard disk drive in an external enclosure, the USB interface is limited to a transfer speed of about 60 MBps for USB 2.0 high speed, compared to more like 133 MBps for an ATA-7 or 8 IDE hard drive, which have been around since about 2001 or 2004. Don't be disappointed if Ubuntu in your external hard disk drive isn't as fast as Windows in your internal hard disk.

Another problem I've run into with the smaller (laptop sized) 2.5" externals is they don't have their own power cord, but rely on the USB port for power. Often, a laptop or even a desktop computer might not have the power in it's USB port to spin one up, especially if it's a larger capacity USB external hard disk.

It's often a simple operation for someone with a screwdriver to open an external hard drive box and remove the hard drive from it's case, slide it into a drive bay in the computer, screw it in and plug in a SATA or an IDE cable and a power cable. Then you'd have Ubuntu running inside the computer, which is much better if you own the computer and if portability is not your goal.  :)

After having made all those points, I will still have to admit now that I do have Ubuntu Rescue Remix in an external hard disk drive, and a Knoppix install too, and I have installed Ubuntu in external hard drives quite a few times now for various reasons. There are times when we need Ubuntu in a portable device, but with a larger storage capacity than flash memory sticks can offer.

The thread our friend Pumalite has linked you to is really more targeted at USB flash memory sticks, but you can use the same info for USB external hard disk drives if you really want to.

Whatever you do, (however you decide to install it), please enjoy Ubuntu and have fun with it. :)

Regards, Herman :)

---

### Post by DeadRobot on 2009-01-18
Also, can I just go to "Create USB startup disk"?  will that work?

---

### Post by Herman on 2009-01-19
Yes, that will work perfectly well, and it's very quick and easy too. And safe.
The advantage of that is, it also has the Ubuntu installer in it like the Live CD does, so you can use it to install Ubuntu in other computers if you like. (And if the owner of the other computer agrees).

---

### Post by DeadRobot on 2009-01-19
I tried teh 'create USB startup' and when i booted from the flash drive it just said:
"Boot Error".

What should I do?

---

### Post by Herman on 2009-01-19
I don't know. It uses the Syslinux boot loader. There used to be some on-line documentation for it. I looked for it for you but now I can't find it anymore.

How were you booting it"
From your BIOS? (the MBR)?
Or, from another boot loader? (Maybe you're trying to boot the partition boot sector?)

Whichever way you're doing it, maybe try the other.
You should be able to boot it with GRUB if you have GRUB installed in your computer. If you don't, you could try Super Grub Disk. That should boot it.

Regards, Herman :)

---

