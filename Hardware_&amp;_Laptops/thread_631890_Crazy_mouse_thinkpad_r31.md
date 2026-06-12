---
title: "Crazy mouse thinkpad r31"
date: 2007-12-04
forum: Hardware &amp; Laptops
---

### Post by darkstr2o4 on 2007-12-04
I just upgraded from dapper to gusty and when I use my mouse every so often it act erratically.  I have checked my /boot/grub/menu.lst file for **i8042.nomux=1** and it reads:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a1822164-88b6-4478-b7e0-3cd51de249bb ro quiet splash  i8042.nomux=1
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

I have also noticed that there is no boot splash screen when starting up, the screen just stays dark. when i run sudo update-grub I recieve the following output:

aslan@narnia:~$ sudo gedit /boot/grub/menu.lst
aslan@narnia:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Any help would be greatly appreciated!

---

### Post by nat6138 on 2007-12-05
Care to explain how the mouse moves erratically? Meaning it just jumps around the screen?

---

### Post by darkstr2o4 on 2007-12-05
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=108377&amp;highlight=r31+mouse](http://ubuntuforums.org/showthread.php?t=108377&amp;highlight=r31+mouse) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				it usually moves to the upper right corner of the screen. In addition to moving erratically, it also clicks on things when no action has been taken. Usually it ends up clicking on the button to power down the computer/ log off or the date and time bringing up the calendar. In some instances it also moves the task bar from the top of the screen to the bottom.

---

### Post by nat6138 on 2007-12-05
I've had the same problem, using a Thinkpad T30. 

It usually happens when I try to use the quick launcher. It starts moving the bar around.

Haven't really figured out what to do about it.

---

### Post by darkstr2o4 on 2007-12-05
I have no idea why, but it seems to be working fine now. I just turned it off for a while and now the mouse is acting normally. However, the boot splash still is missing.

---

### Post by nat6138 on 2007-12-05
For the splash, you could try:

sudo gedit /etc/usplash.conf

See if it is the correct resolution, if it isn't change it. See what happens when you reboot.

---

### Post by darkstr2o4 on 2007-12-05
The values were incorrect however, this did not remedy the issue.

---

### Post by darkstr2o4 on 2007-12-05
Well... thanks for your help i fixed the problem. what needed to be done after changing the values was **sudo dpkg-reconfigure usplash**. Now its there! Thanks for all your help on these issues!

:)

---

### Post by apos on 2007-12-25
The problems you described is solved for a long time. But I know by myself how tricky it is to find the necessary informations ;)

Add the kernel boot parameter "i8042.nomux=1" in the "/boot/grub/menu.lst" and your trackpoint will work as expected.
Additional tip for Thinkpad R31: add "irqpoll" kernel boot parameter keep the USB/Ethernet bus crashing.

See https ___ wiki _dot_ blue-it _dot_ org/Thinkpad_R31

Happy new year.

---

### Post by gastoncs on 2008-03-26
hi APOS I have the same problem with the tackpoint, do we just add this to the page i8042.nomux=1 because I did that but did not work.

Add the kernel boot parameter "i8042.nomux=1" in the "/boot/grub/menu.lst"

---

