---
title: "Noob theory: Is it possible to copy whole installation (settings, programs, and all)?"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by jorx on 2009-10-09
Hi everybody! 

I've got a question that excites me about the possibilities of Linux; rather then installing to another hard-drive / machine from scratch, surely it would be possible to copy an existing one? Including software, programs, settings, preferences and all? (all on the boot partition / ) 

If it is possible, let me know if there's anything more to it then just formatting a new partition and copying everything under / to it?  I've only been using kde/ubuntu/linux for about a month, haven't gotten very in-depth.


********EDIT********

I should have done more googling research first... the terms I needed to search was "clone linux install". I'm now going through material on that! Apologies for the hasty post!

---

### Post by diesch on 2009-10-09
In addition you have to

[LIST]
[*]make sure the devices/UUIDs in /etc/fstab, /boot/grub/menu.lst and /boot/grub/device.map fit your new system
[*]reinstall grub
[*]remove /etc/udev/rules.d/*persistent*.rules
[*]maybe edit /etc/X11/xorg.conf, if you have modified it in the source installation
[/LIST]

---

### Post by Villainous on 2009-10-09
You can use tools like Ghost 4 Linux to do this.  It will copy your harddrive from one disk to another, so all you do is pop the new drive into place and you should be good.

I haven't done it personally, but I've read many accounts of others doing the same thing to go from smaller harddrives to bigger ones.

---

### Post by jorx on 2009-10-09
In my case I'm running linux off of external USB2 hard-drive- so it's very portable and goes with me from machine to machine. 
And I'm in need of duplicating the whole thing onto another external USB hard-drive, so that's what the plan is!

Hm.... thanks for the advice, I'm going to look into Ghost 4 Linux, give that a go.
Thanks!

---

### Post by jorx on 2009-10-10
IT WORKS!!!
Because I only copied over the partition (into a preformatted matching partition with boot flag already said) without copying the entire drive; eg:  
copying /dev/sdd1 instead of /dev/sdd -
-it did not include the MBR (master boot record)

So I booted using live USB, ran 
'sudo grub-install --recheck --root-directory=/media/rootie' ( after mounting my partition).

The --recheck flag was necessary- I couldn't get it to work otherwise.

Now it's booting, and it's a perfect copy- I didn't even have to log into these forums!

---

