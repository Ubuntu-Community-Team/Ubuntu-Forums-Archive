---
title: "Grub Assistance"
date: 2006-01-21
forum: Installation &amp; Upgrades
---

### Post by kaptainlange on 2006-01-21
Hi there, thanks ahead of time for any assistance.

I've been running an Ubuntu desktop for sometime now, and just recently decided that I wanted to reinstall Windows for a program I wished to use.  Not wanting to clobber grub on the primary disks boot sector nor lose Ubuntu to an XP format, I removed my primary drive and set my secondary to master.  I installed XP on there with no problem and got everything set up.  Now I reinstalled the primary drive i had before set everything back up properly as far as master/slave goes and now I want to set my grub boot loader to load windows off the second drive.  It won't boot however.

My XP grub entry looks like this:

root (hd1,0)
makeactive
chainloader +1

It just hangs whenever I try to boot it.

I can verify the XP installation is running just fine at the moment, as taking the drive out and boot off the second drive produces no problems.  Is it even possible for me to do this, or am I going to have to swap the drives and install grub on my windows disk just so i can boot both.

---

### Post by lha on 2006-01-21
Try to add
```
map (hd0) (hd1)
map (hd1) (hd0)
```
above
```
chainloader +1
```

---

### Post by kaptainlange on 2006-01-21
Thank you much, that did the trick.

---

### Post by patbuntu on 2006-01-22
This is exactly what I am trying to do, can you explain in more detail please?
What exactly do I add, and which file do I need to add it to?

Ta

-Pat

---

### Post by lha on 2006-01-23
[QUOTE=patbuntu]This is exactly what I am trying to do, can you explain in more detail please?
What exactly do I add, and which file do I need to add it to?

Ta

-Pat[/QUOTE]

Backup your menu.lst. (The file that contains boot menu settings.)
```
cd /boot/grub
sudo cp menu.lst menu-lst_backup
```

Open the file with gedit
```
sudo gedit menu.lst
```
and find following lines:
```
title Windows XP
root (hd1,0)
makeactive
chainloader +1
```
and change it to
```
title Windows XP
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

---

### Post by patbuntu on 2006-01-23
Thanks very much, works perfectly :) 

Cheers

-Pat

---

