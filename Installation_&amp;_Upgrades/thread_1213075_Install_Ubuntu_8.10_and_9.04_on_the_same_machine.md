---
title: "Install Ubuntu 8.10 and 9.04 on the same machine"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by Nittalope on 2009-07-14
Hi everybody, I just bought a Acer Aspire 6530 with Vista preloaded.
Wanted to install Ubuntu and so decided for 9.04, CD installation.
Everything worked fine, I've got 2 hard drives, both of 500 Giga, decided to use the first as installations device and the second as data storage.
Installed Ubuntu without problems, I left the NTFS partitions Vista has, re-sized the Vista installation's one to 75 Giga and then created with the space available ext4 partitions for Ubuntu 9.04 and for other 2 linux distros (just in case, to try something different...) and left a 192 giga partition as home (ext4). Then installed in one of the 2 partitions available Kubuntu 9.04.
Ubuntu worked great, I could use almost everything, sound is great... but cannot use skype (no mic working... but it's another thread), and so I decided to try the old one, my good 8.10 (that's working great and my Travelmate 290... love it!). I wanted to install in the Kubuntu's partition, since I decided definetively for Gnome over KDE (for now)... but when the installation starts (after choosing language, keymap, timezone, mounting, user...) it says that it cannot delete existing system files... probably because of ext4. So I formatted the partition to ext3 with gparted... same thing, then I tried to install Kubuntu 9.04, but formatting the partition as ext2 and then installing 8.10 again... same again!
So I formatted again the partition (always the same one) as fat32 (hoping to delete all the files... sigh) and tried installing again, and again the same problem. Tried a lot of things (now I've got ntfs Vista partiotion, ext4 Ubuntu 9.04 partition, ext3, hopefully, Ubuntu 8.10 partition, fat32 partition to install Xp (needed to test applications), ext3 partition for wathever, and ext4 /home partition.

So... the question is: is it possibile to install Ubuntu 8.10 and 9.04 on the same machine?
And, if it is, why I cannot achieve this?

Thanxs!

---

### Post by ajgreeny on 2009-07-14
It is normally easy, even on the same disk, never mind same machine, but I note you have /home on an ext4 partition.  Your story was a bit convoluted and difficult to follow, but if you are trying to share the /home with both distros I wonder if that is breaking your attempts to install 8.10, as I don't think that version of ubuntu is enabled for ext4.  Try with different 8.10 /home to the 9.04 /home if you have not already done so, and you may find it works OK.

If I have misunderstood, I'm sorry, but your story as I said was long and complicated and I may have missed the point somewhere along the way.  However, to sum up,  yes it is very possible to have two or more linux distros on the same disk or machine with ease.  Try to keep their /homes separate, however, or you may run into configuration difficulties.  By all means have a shared /data partition, but keep the configuration for each distro separate.  You may just as well keep /home in the root partition of each distro, as the config folders and files are not huge, but set the /data partition to mount automatically at boot-up by editing /etc/fstab in each distro.

---

### Post by Nittalope on 2009-07-15
Well, you were right... 
It was just necessary not to map /home to the ext4 partition and everything's working fine, but: now I've got another problem!

Grub doesn't seem to recognize the 9.04 partition and so I cannot launch the 9.04 installation at boot time... always because of the ext4, I think...

So now I'll try to run 9.04 live and to recovery my old grub entries...

(Sorry, I know I am a bit confusing... too many words...)

**[Update] Ok, copied grub files from 9.04 installation to 8.10 and everything's working again.**

---

