---
title: "USB drive uses new device after reconnection"
date: 2007-04-10
forum: Hardware &amp; Laptops
---

### Post by halfmanhalfpint on 2007-04-10
I have a some USB2 disk drives connected to a machine running Ubuntu 6.06.
I want these to be able to swap out these drives  for storage off-site - am using Amanda to
backup onto these drives.  I umnount the device, power off disk, swap with an identical drive 
and power disk on again.
Problem is, it will usually use a new device when I power on again.  I have to reboot so 
I don't have to keep editing /etc/fstab e.g. 

/dev/sdd1       /disk/DailySet2     ext3    defaults        0       5

when I power on again, it is device /dev/sdc1.
Is there anyway to release a USB device so it will re-use it?

Michael

---

### Post by kidders on 2007-04-10
Hi there,

I *think* I understand your problem. It sounds as though you can't predict the /dev node names of your USB devices, and are tired of having to reconfigure your box, every time you decide to use a new hard disk.

The /dev nodes & aliases assigned to devices (particularly USB ones) can be fairly arbitrary, often depend on irrelevant things like the order in which you connect them, and can sometimes change after system updates. Normally, people solve this by using filesystem UUIDs instead. Of course, since you're presumably rotating storage devices, and probably formatting them on a regular basis, filesystem-specific information is of no help to you. (Hopefully I have your problem right.)

If I had this problem, I would solve it with **udev**, which dynamically manages the contents of /dev...[LIST]
[*]Imagine what you would *like* to see happen ... for example, you might want your USB disks to appear at /dev/backup.
[*]Try to identify some information that is unique to the devices you most commonly use, such as a manufacturer name, a product UID, etc.
[*]Create a new set of udev rules.[/LIST]There's plenty of help & advice available on udev around, but essentially, the job boils down to something like this. Imagine you wanted to make a new rule for a new digital camera...[LIST=1]
[*]Plug in the device, and let Ubuntu do its usual thing with it. Let's say udev adds it at /dev/sdc.
[*]Do a **udevinfo -a -p /sys/block/sdc**, and take a look through the device tree for something practical to use to identify the device in the future. Let's say you choose **ATTRS{product}=="Sony DSC"**.
[*]If you hadn't done so already, you would create a place to put custom rules, eg /etc/udev/rules.d/40-halfmanhalfpint.rules, being very careful to set up permissions & ownership correctly.
[*]Add something like **KERNEL=="sd[a-z]*", ATTRS{product}=="Sony DSC", SYMLINK+="backup%k"** as a new rule. (It's absolutely essential that any rules you create be syntactically correct, sensible, and that you understand them fully.)
[*]Unplug the device, do a **udevcontrol reload_rules**, and you're done.[/LIST]By creating several rules, you can have all your USB disks appear at predictable places in /dev. In my example, anything and everything that was a serial block device identifying itself as "Sony DSC" would wind up at /dev/backup, with additional symlinks (/dev/backup1, dev/backup2, ...) for each detected partition. Of course, if you were to plug more than one of them in at any one time, you'd run into problems!

Anyhow, the end result would be that you could create (and then ignore forever) a line in /etc/fstab pointing to /dev/backup1, that would always work, no matter which device you plugged in, and when you connected it. Whether you would like all your hard disks appearing in the same place (in /dev), or simply want them to be called sensible, predictable things (eg /dev/daily1-1, dev/daily2-1, dev/daily3-1, ...) is entirely up to you.

Hopefully this is what you're looking for. Apologies for the long-winded explanation, but I hope it points you in the right direction. Step 1: Read up on udev!

---

