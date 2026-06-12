---
title: "ubuntu6.06 doesnt shutdown"
date: 2006-12-10
forum: Hardware &amp; Laptops
---

### Post by fouadk on 2006-12-10
hey all, 

i am having a problem shutting down ubuntu 6.06...

the thing is that i press the shutdown button and the shutdown sequence starts and when it reachs "will now halt" it doesnt do anything, it stops forever...so i shut down the pc manually by pressing the power button

i am running ubuntu 6.06 on an AMD semptron with 256 ram and geforce4 mx440

please help me

---

### Post by lonce on 2006-12-10
It might be your motherboard and the way that Ubuntu is interfacing with it.  I have 2 ubuntu PC's at my house on different MoBo's.  One works fine with shutdown and restart.  The other will shutdown but not restart.

---

### Post by fouadk on 2006-12-10
thanks for your reply,

i didnt have that problem with 5.10

is there is a for that or i just have to leave it like that...

i dont have any problem with restart just shutdown...

thanks in advance

---

### Post by squee on 2006-12-16
I have had similar problems in the past with older versions. Every time I upgrade the kernel it doenst shutdown properly anymore. I am pretty sure it is my MoBo. I have posted here in the past and I have gotten results that work. I am still a n00b but i know that the solution is editing this line in menu.lst

kernel		/boot/vmlinuz-2.6.15-27-686 root=/dev/hda1 ro quiet splash

something to do with adding lapic and possibly deleting splash. If someone knows better please post.

---

### Post by zek725 on 2006-12-26
> **squee said:**
> I have had similar problems in the past with older versions. Every time I upgrade the kernel it doenst shutdown properly anymore. I am pretty sure it is my MoBo. I have posted here in the past and I have gotten results that work. I am still a n00b but i know that the solution is editing this line in menu.lst

kernel		/boot/vmlinuz-2.6.15-27-686 root=/dev/hda1 ro quiet splash

something to do with adding lapic and possibly deleting splash. If someone knows better please post.

procedure:
```
sudo nano /boot/grub/menu.lst
```
look for the line of the kernel mentioned by *squee* then append
```
acpi=force lapic
```
save the file and close then reboot. It will work on your next reboot.

---

### Post by fouadk on 2006-12-27
thnx alot for your help

:D :D :D

---

