---
title: "can't install grub in MBR during installation or restoring it via live cd"
date: 2008-08-25
forum: General Help
---

### Post by tuxfire on 2008-08-25
hello, I tried to install gentoo and i got an error during the grub installation stage, same for sabayon, same for ubuntu. The error seems refered to the installing in MBR (master boot record) as I tried to setup it manually with a live cd using the method:

root(hdx,x)
setup(hdx)
quit

but nothing, it accepts root command but says impossible to mount volume at the second istruction. MBR looks like write-protected but I have not a function in my bios like the antivirus or something to lock a part of a drive or similar stuff.
Now i'm freezed, can't install anything

plz help
Thank you

---

### Post by prince_niceguy on 2008-08-25
Login into live cd and go to partition editor, Now click on the first partition and see what are flags set on it. Try unsetting those.

Also, are you using windows or doing dual boot?

---

### Post by jpaulb on 2008-08-25
I have run into a situation like that a few times. I had to dig out an old DOS disk and and do fdisk /mbr.

i do not know linux command for the same thing

---

### Post by tuxfire on 2008-08-29
ok, solved...

thanks for your advices but the problem was not in MBR but in the partition. I tried to install encrypted ubuntu for example and i needed to choose a /boot partition (compulsory) so with the ubuntu's install manager i formatted it in ext3. Now the strangeness... with gparted it was an ext3 ok... but using fdisk -l was a swap/solaris! Grub failed to install itself because it couldn't mount the /boot partition (saw as a swap) and due to this it didn't refresh its first stage in MBR! (keeping the current configuration, it's right!). So i cancelled the partition, recreated it and formatted with gparted. Why this? A bug into the ubuntu's installer? Maybe because i could have touched that/those partitions with fedora o sabayon installer? I can't remember very well Dunno... :confused:

---

