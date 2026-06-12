---
title: "Grub error 22, box won't boot"
date: 2005-10-04
forum: Hardware &amp; Laptops
---

### Post by gnicezw on 2005-10-04
Hi, noobi here. 
Installed ubuntu and love it. / was mounted on /dev/hda8 , i deleted /dev/hda5 (empty partition) and have since found out that i should have updated fstab before rebooting. / is now on /dev/hda7 and i'm sure /boot and /swap will also have diffferent mount points. 
I have a suse install on /dev/hda4 that wasn't affected by the partition change and still boots. I can mount /dev/hda7 (ubuntu / partition) from SuSe. what changes can i make to my ubuntu install to make it bootable?
Alternatively is there anything else i can do to recover the system. I tried booting from the ubuntu install c.d but it wouldn't let me proceed without overwritting the current install or setting a fresh one :( mayb i missed something. Please help
thanks

---

### Post by tonym on 2005-10-04
Edit /etc/fstab and /boot/grub/menu.lst

---

### Post by gnicezw on 2005-10-04
Thank you, i don't understand the boot process very well. I edited the menu.lst  in /boot of my suse install, added an entry for ubuntu and when i selected that at boot-time it worked. - thankyou very much. 
next question; How do i get my machine to boot from the boot partition in ubuntu and not the one in suse. I think what i'm trying to do is to get grub to load the config from /boot/grub/menu.Ist in /dev/hda11(ubuntu /) and not /dev/hda12(suse /)
thanks

---

### Post by gnicezw on 2005-10-04
found an answer, it was pretty staight forward actually, - grub-install. thanks for all your help.  .
cheers mate. :)

---

