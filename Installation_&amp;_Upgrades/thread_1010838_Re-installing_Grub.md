---
title: "Re-installing Grub"
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by nathand28 on 2008-12-14
Today, whenever I tried to boot Ubuntu, the Grub error 25 came up. After some googling, I found this was a problem with the menu.lst, and I had to use a liveCD. So I tried to boot the CD, and got an error along the lines of *ata1.00 error UNC*.
***This error doesn't matter though*, because I left it to boot, and after about 10 mins it booted ok.**
So I used [this]("http://ubuntuforums.org/newthread.php?do=newthread&f=333") tutorial by Catlett. Whenever I tried the command
```

find /boot/grub/stage1

```
in the grub shell, I got the error 15, file not found. So, I went to that folder, and the only file I found was the device map. 
**So, the real questions are, is there supposed to be files in the grub folder, and how do I fix error 25 ?**
Any help is appreciated.

---

### Post by bulldog on 2008-12-14
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
This will get you a grub> prompt 
```
sudo grub
```
This will return a location which you have to use in the next command.
```
find /boot/grub/stage1
```
Enter the location given by the previous command in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.

---

### Post by northern lights on 2008-12-14
An idea would be to let the [Supergrubdisk]("http://www.supergrubdisk.org/") work its magic.

---

### Post by nathand28 on 2008-12-14
> **bulldog said:**
> 
```
find /boot/grub/stage1
```

Whenever I use this command, the error 15 and file isn't found comes up.

(EDIT) Changed 17 to 15.

---

### Post by bulldog on 2008-12-14
Take a look at this amazing site,and you can find almost anything there's to know,about grub and errors.

[http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible](http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible)

---

### Post by caljohnsmith on 2008-12-14
It sounds to me like you are having hardware problems, because for one thing, a Grub error 25 is:
[QUOTE=Grub Manual]**Error 25** : Disk read error
This error is returned if there is a disk read error when trying to probe or read data from a particular disk.[/QUOTE]
Also, the fact that booting the Live CD also produced an error lends more credence to the idea you are probably having a hardware problem. Were you able to boot the Live CD previously with no problems, like when you originally installed Ubuntu? You could run a RAM test just to rule out the possibility it is your RAM by running the "test memory" option from the Live CD. You could also run some tests on your HDD to check its health, but the fact you have problems with your Live CD too would suggest that your HDD might be just fine and the problem is elsewhere.

---

### Post by nathand28 on 2008-12-14
I've tried the Live CD and Live USB, but the error doesn't really matter, because it boots anyway.
The real question might be, why is there no files in the /boot/grub folder?

---

