---
title: "USB Backup Hard Drive - how do I create the right to write on the drive ?"
date: 2007-06-28
forum: Hardware &amp; Laptops
---

### Post by davegahan on 2007-06-28
Bought myself a nice 500GB USB drive, on to which I dumped all my former windows files . Connected to my Ubuntu laptop I can read the files, but i cannot write to the drive - I get the message I do not have permission to write to the drive.

How can I get myself the permission to write to the drive ?

---

### Post by elsaturnino on 2007-06-29
Is it automatically mounted or are you doing the mounting by hand? read-write is an option you specify at mount time although i believe it is usually the default.

---

### Post by geraldm on 2007-06-29
Identify the USB bus and device number with
lsusb
The permissions for the drive are in the file
/proc/bus/usb/BBB/DDD
where BBB is the bus and DDD is the device number.

These are usually set when the device is discovered, by scripts in
/etc/udev/rules.d/XXX-permissions.rules (for those using udev)
There ought to be an easy configuration script, but I do not know of
it.
Gerald

---

### Post by skyttan on 2007-08-20
If the drive is not read-only I have an easy guide for you. :)

1) Open terminal (by basic: Applications -> Accessories -> Terminal)
2) Write 'sudo nautilus' (without the quotes) and enter password if asked for. 
Here sudo means you want to do the task as the root (have all the power the system can give you) and nautilus is the windows manager in Gnome.
3) Browse to the drive you want to write on and right-click on it, choose Properties and then the Permissions tag.
Here you choose who and how people on your computer can access the files. Really smart I think (but irritating some times) way to control access at your files. I use it much with Samba when sharing so only me with my password can access my docs.
4) Finish it by choosing you as owner (if you can) or else give your group or everybody read and write access. You may need to do this with every single directory on the drive to access them as well.

Hope this helped! :D

---

### Post by MacD on 2007-08-21
I'm having the same problem with a USB hard drive which I just reformatted to FAT32 with gparted (because I couldn't delete the trash).  I want to be able to read and write to this drive from Windows and Linux machines and when I delete files I want them to be gone for good.

When I try to set permissions with gksudo nautilus, the changes are reverted immediately.

I see a lot of threads on this topic... talking about fstab entries etc, but I'm reluctant to go there.

Any simple way to do this?

Format the drive as FAT32 on a windows machine?

---

