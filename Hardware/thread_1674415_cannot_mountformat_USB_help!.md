---
title: "cannot mount/format USB help!"
date: 2011-01-23
forum: Hardware
---

### Post by dokyounder on 2011-01-23
Hi all,

I'm trying to get my usb formatted. I was installing Ubuntu to it, but for some error the installation had stopped. and because the installation was on its halfway when it was interrupted, it's neither bootable nor usable.

The problem is, when I plug it in, I can't access the files inside(if there's any). nothing tells me the usb's been plugged in except Disk Utility. I can see it in Disk Utility, but when I try to format it says "Error formatting drive. The device is busy. Details: A job is pending on /dev/sdb"
[IMG]http://featherfiles.aviary.com/2011-01-23/b773f0d2345342618d5e98d305afb3dc.png[/IMG]

I don't know if it'll help but here's what appears when I do "sudo lsof /dev/sdb"
> lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/wubi/.gvfs
      Output information may be incomplete.
lsof: status error on /dev/sdb: No such file or directory
lsof 4.81


How can I fix this problem? I don't care for the content inside the usb, I just want to format the whole thing.
any suggestions please?

---

### Post by Bucky Ball on 2011-01-23
The drive sounds like it is still open by the device busy message. Is it possible to 'unmount' the drive somehow? Does it show up in Gparted? No icon on the desktop? If there is you could right click and 'safely remove drive'. That would shut it.

---

### Post by dokyounder on 2011-01-23
no, it's not. there's no icon on the desktop. I can't do anything about it.

---

### Post by Bucky Ball on 2011-01-23
On the screen you posted there is an option: Safe Removal, at the top right of that page. Close the drive with that, unplug the drive then plug back in and see what you get. If the 'Safe Removal' option doesn't work, open a terminal (Applications>Accessories>Terminal) and paste this in:

```
sudo umount /dev/sdb1 
```

---

### Post by dokyounder on 2011-01-23
safe removal make it disappear from the list. It's clean, it doesn't give any message. I guess that's working.
but when I plug it back in and try sudo umount, it gives me this.

umount: /dev/sdb1: not mounted

---

### Post by Bucky Ball on 2011-01-23
You do not need the umount command as you have safely removed the drive already. It seems the system is just not picking it up when you plug in.

Plug it in and try this instead:

```
 sudo mount /dev/sdb1
```If there is an error post it back here. ;)

Also, System>Admin (but could be Preferences)>Removable Drives and Media, and make sure that is set up to pick up USB drives.

---

### Post by dokyounder on 2011-01-23
I tried that too. It gives me this.

mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab

---

### Post by Bucky Ball on 2011-01-23
Also, System>Admin (but could be Preferences)>Removable Drives and  Media, and make sure that is set up to pick up USB drives.

The drive is unformatted as in it has no partitions or filesystem on it ... it is totally empty?

---

### Post by dokyounder on 2011-01-23
it is set to pick up USBs, and I have absolutely no problem with other usb devices. the usb that's not working now used to work fine. Like I said, I was installing Ubuntu on it, and it was half way through before it stopped because of some error. 
From the screenshot you can see it's got 3 partitions, and since I was installing Ubuntu, possibly some filesystem too.

---

### Post by Bucky Ball on 2011-01-23
As you don't have a complete install as the install died half way through I would be tempted to delete the lot and start again.

---

### Post by dokyounder on 2011-01-23
How do I delete it? I tried to format it, but it wouldn't work.

---

### Post by dokyounder on 2011-01-23
how do I delete whatever's in the usb when I can't even access? 
I tried formatting, but it wouldn't work.

oops double post. sorry

---

