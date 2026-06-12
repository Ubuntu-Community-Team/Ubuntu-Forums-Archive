---
title: "Ubuntu 9.10 won't reboot"
date: 2010-01-25
forum: Hardware
---

### Post by Siebjee on 2010-01-25
Hello guy's

When i click reboot, then my laptop does shutdown, but when it supposed to reboot it just stay's there. Blank black screen, ready to reboot but it wont.

I have to manualy cut off the power, and then boot it again.
It is starting to get very anoying. Google and other forums and irc channels couldnt help me solving this problem.

Laptop :
Asus PRO50-N
2GB ram, 200GB HDD
Ubuntu 9.10 fully updated, grub2 bootloader.

I hope any of the guy's here is able to help me solving this problem.

Kind regards, and thanks in advance,

Siebjee

---

### Post by llawwehttam on 2010-01-25
Could you try the following and post what happens for each one:

```
sudo telinit 6
```
```
sudo shutdown -r now
```
```
sudo reboot
```

---

### Post by Siebjee on 2010-01-25
```
sudo telinit 6
```
shuts down my laptop until it should do a reboot, which it doesnt do.
```
sudo shutdown -r now
```
shuts down my laptop until it should do a reboot, which it doesnt do.
```
sudo reboot
```
shuts down my laptop until it should do a reboot, which it doesnt do.

I'm still clue-less

---

### Post by Siebjee on 2010-01-25
from what i could understand what i found on the ubuntu techhelp is that it has to do something with acpi thingy's in the kernel. In the previous versions of grub you were able to edit the menu.lst and add something to a line so it should reboot. But since i got grub2 i dont have a menu.lst anymore.

_[https://answers.launchpad.net/ubuntu/+question/3857](https://answers.launchpad.net/ubuntu/+question/3857)_

Also thats for the 6.04 lst version of ubuntu, and not for the 9.10.
Also i might mention i had the same problem on this laptop with 7.10, 8.04, 8.10, 9.04 and 9.10 atm.

---

### Post by efflandt on 2010-01-25
That has always been an issue with my desktop since I bought it in 2004 (WinXP/SuSE 8.2 at that time).  It appears to shutdown, but for some reason does not reset, and just sits there with power supply on doing nothing.  So whenever something says I need to reboot, I just say no, shut it down completely myself, and then cold boot.

---

### Post by llawwehttam on 2010-01-25
Have you looked at updating your BIOS. Have a look at your computer manufacturer's website for bios updates and consider it.

---

### Post by Siebjee on 2010-01-25
Already have the newest bios of my laptop

---

### Post by Siebjee on 2010-01-27
Anyone else has a solution ?

---

