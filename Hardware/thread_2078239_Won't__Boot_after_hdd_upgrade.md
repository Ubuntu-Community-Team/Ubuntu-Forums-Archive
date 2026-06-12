---
title: "Won't  Boot after hdd upgrade"
date: 2012-10-30
forum: Hardware
---

### Post by coliny on 2012-10-30
wubi install of 12.04 was working ok until I cloned my hdd to new drive.

W7 works fine with new drive but Lubuntu just says 'device not found' (the old hdd) when I try to run it from boot menu. Safe mode lubuntu does not start either.

The Ubuntu folder is there on C:\ when I look in w7.

How do I get it to recognise the new hdd ?

---

### Post by bcbc on 2012-10-30
When you select Lubuntu it says that immediately? Or do you see the: *Try (hd0,0): wubildr* message first.

---

### Post by coliny on 2012-10-30
It says it imediately, then says press a key to continue, but freezes & I have to reboot.

---

### Post by bcbc on 2012-10-30
> **coliny said:**
> It says it imediately, then says press a key to continue, but freezes & I have to reboot.

You mentioned 'safe mode lubuntu' doesn't work either. So does that mean you get to see the grub menu?

---

### Post by coliny on 2012-10-30
don't know the grub menu

recovery mode displays a lot of text then says 
ALERT! /dev/disk/by-uuid/da....... does not exist. Dropping to shell !.
Busybox v1.18.5
Enter 'help' for a list of commands.

---

### Post by bcbc on 2012-10-30
ah okay...

Try this:
[http://ubuntuforums.org/showpost.php?p=12323440&postcount=8](http://ubuntuforums.org/showpost.php?p=12323440&postcount=8)

> So, hit 'c' to get to a grub prompt. Then enter:
Code:
search -s -f -n /ubuntu/disks/root.disk
probe --set=diskuuid -u $root
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=UUID=$diskuuid loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot

Once you've booted, run:
Code:
sudo update-grub

---

### Post by coliny on 2012-10-30
Sorry I don't now how to get to grub menu.

When I type help it gives me list of commands but not the ones you want me to execute !

---

### Post by bcbc on 2012-10-30
When you select Lubuntu (from the Windows boot manager), immediately hold down the SHIFT key. That should pop the grub menu. Then hit 'c' to get to the grub prompt where you can enter those commands.

---

### Post by coliny on 2012-10-30
OK got the grub prompt

the search command returned error: no such device.
checked in w7 and found the path is /ubuntu/disks/boot/root.disk
tried search on the path but still get error: no such device

will resume tomorow, thanks

---

### Post by bcbc on 2012-10-30
> **coliny said:**
> OK got the grub prompt

the search command returned error: no such device.
checked in w7 and found the path is /ubuntu/disks/boot/root.disk
tried search on the path but still get error: no such device

will resume tomorow, thanks
That doesn't seem standard, but if that's what it is, then just substitute /ubuntu/disks/boot/root.disk everywhere in those instructions.

---

### Post by coliny on 2012-10-31
Success :)

At the first try it failed. Checked for root.disk with w7 & found it had just now created it at 
/ubuntu/disks/root.disk

Maybe I mis-typed one of the commands. Repeated proceedure with above path and it worked.

Many thanks
Colin

---

