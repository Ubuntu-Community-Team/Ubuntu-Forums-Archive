---
title: "Anywhere I can find &quot;vmlinuz-2.6.28-11-generic&quot; for download?"
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by Lupusceleri on 2009-05-30
Hey there,

I'm attempting to install Kubuntu Jaunty on a fakeRAID striping setup, using the guide here: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

So far it worked (I can read the RAID disk, installed, etc).. but.

I get a GRUB 15 error when I try to boot it up. AKA: it can't find file.

After lots of trial & error, I found out that the file /boot/vmlinuz-2.6.28-11-generic is missing from the harddisk.. and therefore GRUB can't find it to boot with.

Is there anywhere I can separately download this file and paste it to my /boot/ or am I better off just trying a reinstall?

---

### Post by Lupusceleri on 2009-05-30
Nevermind, just going to format and try again with automatic grub install. If that fails, well, I'll have two regular disks.

---

### Post by Lupusceleri on 2009-05-30
Fixed.

For some reason, if you install without GRUB ubiquity conveniently forgets to install the kernels to your /boot folder or partition. That causes GRUB to error because it can't find essential files to boot. :D Also, ubiquity will not install GRUB on your disk correctly so you indeed have to redo it manually as the guide says.

Additions to aforementioned guide (in original post):

- You'll need to install Ubuntu twice. Once **with GRUB** to your raiddisk, after ubiquity is done installing you copy the contents of your /boot folder (minus /boot/grub) to a flashdrive or whatever place you can access that is not on your raiddisk.

- Second time you install Ubuntu (clear the partition content!) you **don't install GRUB** just like the guide says.

- After step 9-k you copy the earlier gotten contents of the /boot directory (NOT the /boot/grub/ directory as well!), if you happen to have any identically named files do not overwrite.

- When editing menu.lst, make sure that the Linux-choice lines refer to /boot/vmlinuz-2.6.28-11-generic and /boot/initrd.img-2.6.28-11-generic rather than just those two paths without /boot/ (or even without numbers).

---

