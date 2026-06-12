---
title: "[SOLVED] multi-boot/grub"
date: 2008-07-14
forum: General Help
---

### Post by ACanuck on 2008-07-14
Hi,
I recently installed a bunch of different distros(Ubuntu, kubuntu, xubuntu, Linux Mint, and more to come :P) to play around with, and the grub menu is kinda getting crowded and confused.

I was wondering how I could go about editing it? So I could possibly remove all the memtest and recovery options and rename the others, because IIRC kubuntu is also listed as Ubuntu, idk about xubuntu, can't remember, and I plan on having another actual Ubuntu installed(so I can fiddle around with it and not break my main ubuntu :P).



Oh, and another question on the side kinda related. All these are one one drive, seperate partitions. All these partitions are the same size.. so, when I go to Computer I see 4 different volumes named the same. How would I go about changing the names of them? Rename doesn't work. I get "Operation not supported by backend" when I try.


Thanks.

---

### Post by justleen on 2008-07-14
you can edit the menu.list

```
 cp /boot/grub/menu.lst /boot/grub/menu.lst_org
   sudo gedit /boot/grub/menu.lst

```

as for the disks, you can edit fstab to mount them on a different mountpoint, or give them another label with e2label (the drive show up under their label by default. Mind you need to reboot after applying a label before its visible)

---

### Post by mcduck on 2008-07-14
(By the way, there really isn't much need to have separate installs for Ubuntu, Kubuntu and Xubuntu. The are all one and same OS, and you can install all the different desktop environments you want & select which one you wish to use from the login screen..)

---

### Post by ACanuck on 2008-07-14
I tried that once, and I managed to mess it all up and couldn't seem to get rid of kde or xfce after lol I am a bit of a n00b :o Just find it neater for me to have them all seperate to play with :)

And, silly question, but, each of them have that menu file right? So, do I do that to all of them? Or just one? If one, which? And how would I change which is the default to boot too? Right now it seems the last one installed always gets to be that special one.

And could you by any chance give me an example of what one would type with e2label, I see man says "e2label device [ new-label ]" but I am not exactly clear from that(again, I am a n00b heh). When I right click on them and go to properties they say "Mount Point: /media/disk" and such. So, would I type "e2label /media/disk Ubuntu" to label that one as Ubuntu? Or what?

Still a Windows user, just trying to play with Linux more and more till the day comes I throw my XP disk away :o Though, for the time being I can't, game I play doesn't like running in Wine! Well, it doesn't even run properly on vista.. then again, what does? lol

Think its time someone*cough*me*cough* buys a Linux For Dummies book lol

Thanks :)

---

### Post by mcduck on 2008-07-14
Unless you tell the installer to not install Grub, every time you install a new version it will rewrite the mbr. So yes, the last one you installed is most likely the one that's managing the Grub menu now. So that's also where you need to edit the menu.lst file.

For the labe, it's asking for _device_ name, not mount point. So this would be something like /dev/sda2. you can run  "sudo fdisk -l" to list all your disks, partitions and their device names.

---

### Post by lswb on 2008-07-14
Take a look at this web site:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by ACanuck on 2008-07-14
Thank you all for your help! :)

---

