---
title: "Just got WoTLK...can't copy...please help!"
date: 2008-11-13
forum: General Help
---

### Post by LifeIsFlimsy on 2008-11-13
When I installed World of Warcraft and the Burning crusade, I followed a website that I googled and copied the files off of the CD onto a new folder I made, etc, and been playing ever since. Now, when I try to do that with this new expansion Wrath of the Lich King, I don't have the permission to copy the files off the Dvd. Why is that? I am the administrator of this computer.

---

### Post by daleus on 2008-11-13
Save yourself the hassle mate, get a friends copy from a windows machine on a memory stick, dvd's etc and just copy it straight onto your machine and run wow.exe

Don't even bother installing it, as that will surely fail.

---

### Post by idon10 on 2008-11-13
Here is how i was able to get it to work:

# sudo su
# umount /media/Lich King
# mount sr0 /mnt -o unhide
# cd /mnt
# cp *.* /WoTLK
# mkdir /WoTLK/DirectX
# cd DirectX
# cp *.* /WoTLK/DirectX
# cd /WoTLK
# wine Installer.exe

make sure you do this all as root and
BANG! After install you should be able to login!

---

### Post by LifeIsFlimsy on 2008-11-14
I actually just downloaded the expansion from the WoW website. Thanks for the replies folks!

---

