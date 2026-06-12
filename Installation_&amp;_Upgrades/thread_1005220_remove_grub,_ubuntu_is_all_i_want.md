---
title: "remove grub, ubuntu is all i want"
date: 2008-12-08
forum: Installation &amp; Upgrades
---

### Post by NAWSE on 2008-12-08
i just want to use ubuntu, and i want it to boot directly after i turn my laptop on. the grub is bothering me a lot. and there have been instances where the grub didn't boot (error 15). so i don't want any loaders or whatsoever in the picture. heard you can boot without need of a bootloader if you want to stick to one OS?

thanks in advance

---

### Post by lisati on 2008-12-08
You'll probably need *something* to load Ubuntu. If it wasn't for the occasional "Error 15" I'd suggest you do the following:

From the terimal, enter ```
sudo gedit /boot/grub/menu.lst
```
Then look for the line which reads > #hiddenmenu and remove the "#".
Then edit the "timeout" line to have a small number, save the file, and reboot. (Don't make the timeout zero unless you don't mind not being able to boot in with "recovery" mode)

---

### Post by NAWSE on 2008-12-08
oh you mean i will still get the error 15? and what do i do when i get one?

---

### Post by NAWSE on 2008-12-08
also, i started getting that error only after installing opensuse, and messing with the grub and boot options and everything. earlier i had ubuntu-vista dual boot with grub but i had no problems at all. its only after messing so much up and reformatting the hard disk(and hardy reinstallation), that error 15 came up for the first time ever. what went wrong? i just want a surity that ubuntu will boot for sure, when i turn my laptop on. i don't always carry a dvd or live-cd to repair.

---

### Post by lisati on 2008-12-08
The "Grub error 15" usually means that there's some problem locating your copy of Ubuntu. 

Some places it is dealt with include:
[http://ubuntuforums.org/showthread.php?t=1003827](http://ubuntuforums.org/showthread.php?t=1003827)
[http://ubuntuforums.org/showthread.php?t=1004074](http://ubuntuforums.org/showthread.php?t=1004074)
[http://ubuntuforums.org/showthread.php?t=883257](http://ubuntuforums.org/showthread.php?t=883257)

Hope one of the above helps.

---

### Post by caljohnsmith on 2008-12-08
Do you get the Grub error 15 before seeing a Grub menu, or before seeing the text "press ESC to see menu," or do you get it after selecting an OS in the Grub menu? If you would like a hand sorting out the problem, how about opening a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo xxd  -l  2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
So replace "sda" above with each of your drives. Note "-l" is a lowercase L, not a one. And finally, for each command above that returns "eb48", please post:
```
sudo xxd -s 1049 -l 2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
And replace sda with the drives that previously returned "eb48". That will greatly clarify what your setup is like.

---

