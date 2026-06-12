---
title: "Error No Operating System"
date: 2010-03-10
forum: Hardware
---

### Post by Sumo74 on 2010-03-10
Have searched and searched, and nothing seems to work. I cannot get my grub to load, because my BIOS can't read my Operating system. I know they are still there, I can see the partitions and everything off my Ubuntu Live CD (Which I am running right now). I say somewhere, that install-mbr to /dev/sda (the entire drive) would take care of it. It didn't. Instead, now all I get is MBR 1fa: and I can't type a command or nothing.

Really lost, thought it was something simple, but I guess I am wrong. Hopefully you all can help. Don't want to loose all my files, and distros (Don't have a flash drive to load Ubuntu off it, and so I can't take my files and save them to a disc, nor can I reload my openSUSE live cd disc, because I blanked it after I installed it *facepalm*)

---

### Post by Sumo74 on 2010-03-11
Sorry for the bump, but I really need help with this one.

---

### Post by Phrea on 2010-03-11
I have no cure for your problem, but you can at least backup your files via a live cd. I'd say that's your first priority before fiddling with that system.

---

### Post by pricetech on 2010-03-11
No form of repair should be attempted without backing up your stuff.  You'll need to get some form of removable media to do that.  A small investment if your stuff is worth anything to you.

---

### Post by Sumo74 on 2010-03-11
That's my fear. I know I can just reload Ubuntu, but I don't have any removable devices, nor the resources to get one right now. I got 30gbs of files, so a flash drive won't do (Easiest cheapest route), and since I am running off the live cd, I can't save them to DVD (I have a bunch of those, a shame I can't use them). So basically you all are saying reload Ubuntu? I might just try it on my openSUSE partition since it don't have any of my media, and it is what is causing the problems (Atleast I hope). If that don't work, then I will just have to say goodbye to all my media and get reload the whole HDD.

Edit: I fixed it. openSUSE's bootloader was the problem. Uploaded Ubuntu to it's own partition, and setting openSUSE to no bootloader took care of it, so no data lost, and everything is working fine, thank you all.

---

### Post by pricetech on 2010-03-12
Glad you dodged the bullet.  I guess an external hard drive, or at least some form of backup solution, just got bumped up your list of things to save for.

---

