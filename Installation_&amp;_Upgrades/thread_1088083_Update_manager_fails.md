---
title: "Update manager fails??"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by quirijnquintus on 2009-03-05
Hi!
Recently my friend introduced me with Ubuntu and I wanted to try for myself. I wanted a dual boot so cleared space of my HDD of my laptop.
My Dvd/cd drive doesn't really work anymore (ticking sound when a cd-rom is read) So I decided to do a installation from a USBstick, which I made via my friends laptop, which runs Ubuntu.

The installation went fine and soon I had Kernel 2.6.27-7 on my system. After the first boot there are 262 updates which have to be installed. This takes a while. At 2/3 of the installed updates it suddenly restarts the system from grubloader but then this Kernel Panic occurs:
[B]
Kernel Panic - not syncing: VFS: unable to mount root fs on unknown-block (0,0)[/B]

So I turn the laptop off and on and see in the Grub loader that there is another kernel aswell: kernel 2.6.7-11

I presume this is the latest one where the updates are being installed so press enter en then the kernel panic occurs again.

Press off and on and try kernel 2.6.7-7. This version works, but on start up there is a message saying: Instal Problem: The configuration defaults for GNOME power manager have not been installed correctly.

What is happening? Can I restore Ubuntu?

[SIZE="1"]
specs.
Fujitsu Siemens Amilo laptop
1.60ghz Celeron 
512mb RAM. 
80GB HDD, in 3 partitions, on one is windowsXP, on the other some programs and the 3th and largest (42GB) was reserved for Ubuntu.[/SIZE]

---

### Post by Pumalite on 2009-03-05
If you see Grub; boot into Recovery Mode and do:
```
dpkg --configure -a
apt-get -f install
apt-get update
apt-get dist-upgrade
```
One at the time

---

### Post by quirijnquintus on 2009-03-07
THnx :)I did not quite follow your advice, but I think it worked out. I went into recovery mode of the old kernel and did dpkg repair broken packages. It installed many more updates and after that the newer kernel 2.6.7-11 worked again. The only thing is that the old kernel is still in the GrubLoader. Can this be removed?

---

### Post by Pumalite on 2009-03-07
Edit /boot/grub/menu.lst. Backup first:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
```
Edit:
```
gksudo gedit /boot/grub/menu.lst
```
You can now remove the old kernel from the list. I'd keep at least 2 kernels. You never know when you will need the other to boot.

---

### Post by Neo_The_User on 2009-03-08
> **quirijnquintus said:**
> Hi!

[B]
Kernel Panic - not syncing: VFS: unable to mount root fs on unknown-block (0,0)[/B]



I always get that error when trying to compile a kernel under 700K. Drives me insane.

---

