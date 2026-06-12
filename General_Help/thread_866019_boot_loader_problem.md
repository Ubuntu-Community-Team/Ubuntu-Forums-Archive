---
title: "boot loader problem"
date: 2008-07-21
forum: General Help
---

### Post by chriskin on 2008-07-21
my laptop has Ubuntu 8.04 and Windows Vista on two partitions and i used a third one to install another linux OS

at first i put Linux Mint but once i formated the partition as i did not like it, there was a boot loader problem making all OS's unreachable
the same happened with debian once i tried it and formatted the partition after i had problems running it, and the same thing happens with fedora now.

on top of that, i cannot boot on ubuntu as fedora put its own boot loader and it seems that it doesn't recognise ubuntu, i tried to make it do so, but the commands to open the grub menu are different from ubuntu 

anyway, i want to delete fedora now, but i need a way to do so avoiding the boot loader problem :S

---

### Post by Potatoj316 on 2008-07-21
I am going to assume you can only boot into fedora for this answer.  To fix your problem boot into the Ubuntu live CD environment with your Ubuntu live CD.  Then use GParted from the System menu to delete the fedora partition and resize other partitions to fill the space.  Now open a terminal and install GRUB with the commands explained here.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by chriskin on 2008-07-21
i MAY be able to load ubuntu after all as i was helped in another thread for that

can you tell me how i can make the ubuntu boot loader the default one ?

---

### Post by chriskin on 2008-07-21
i am in ubuntu once more :D
(why is there the need for different commands on fedora and ubuntu anyway? :P) 

now, all i need is to make the ubuntu based boot loader default

---

### Post by Potatoj316 on 2008-07-21
Which bootloader are you using now and do you have more than 1? (i dont think you can have more than 1, I might be wrong)

---

### Post by chriskin on 2008-07-21
since i have fedora as well, once i open the pc fedora uses its own bood loader, having a fedora sign on half of the screen and is all blue etc etc

---

### Post by Potatoj316 on 2008-07-21
Is fedora gone?  If so it would probably be easiest to just install GRUB based on the link I gave you earlier.

---

### Post by chriskin on 2008-07-21
i still have fedora, and i want to keep it for some days (until i delete it) so that i can show it to a friend

anyway thanks :D

i will find some way to make this one default, there is no rush now that i can enter ubuntu

---

### Post by Potatoj316 on 2008-07-21
If you end up installing GRUB before you get rid of fedora you will have to edit the menu.lst file in /boot/grub so that you dont have the fedora option anymore.  To do this type (terminal) ```
sudo gedit /boot/grub/menu.lst 
```
Then you can scroll to the bottom to move/delete/add grub menu options

---

