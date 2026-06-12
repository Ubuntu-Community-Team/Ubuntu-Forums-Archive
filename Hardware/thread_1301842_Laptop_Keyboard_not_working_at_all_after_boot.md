---
title: "Laptop Keyboard not working at all after boot"
date: 2009-10-26
forum: Hardware
---

### Post by Underlien on 2009-10-26
Hi

I have used ubuntu since 8.10 on my LG S900 laptop.

Back then, i had to add the line "i8042.nopnp=1 i8042.dumbkbd=1" to "Menu.lst to make the keyboard work once grub loaded the OS.

This has worked until i upgraded to 9.10 64bit.

Now i can't get it to work anymore, so i have to use a external USB keyboard to log in and actually use my computer.

The built-in touchpad works just fine.

Any idea's how i can get it to work again?

Help is greatly appreciated.

---

### Post by kbielefe on 2009-10-26
My guess is that you need to configure it as a module now.  Try creating a new file /etc/modprobe.d/i8042 with the following contents:
```
options i8042 nopnp=1 dumbkbd=1
```Then reload the i8042 module with:
```
$ sudo modprobe -r i8042
$ sudo modprobe i8042
```If that doesn't work, tell me what "uname -r" gives you and attach the output of dmesg so I can see if something recently changed in the kernel source.

---

### Post by Underlien on 2009-10-26
Hi
Thanks alot for the suggestion.

When typing in the command i get this:
FATAL: Module i8042 not found.

I'm not so hardcore in the arts of linux,  so im not sure what you want me to do, can you explain it further please?

---

### Post by kbielefe on 2009-10-26
You did it right.  That means exactly what it says.  No module by that name, could be for any number of reasons, but it's mostly because my hoping for the best case scenario didn't work out.  Attach the output of dmesg and I'll look into it in more depth when I get home from work.

---

### Post by Underlien on 2009-10-26
I hope this is the stuff you need, got it from dmesg.conf:

# dmesg - save kernel messages
#
# This task saves the initial kernel message log.

description    "save kernel messages"

start on runlevel [2345]

task
script
    savelog -q -p -c 5 /var/log/dmesg
    dmesg -s 524288 > /var/log/dmesg
    chgrp adm /var/log/dmesg
end script

---

### Post by kbielefe on 2009-10-26
Actually, I need the output of the dmesg command:
```
$ dmesg | gzip > dmesg.gz
``` and attach the dmesg.gz file.

---

### Post by Underlien on 2009-10-26
dmesg.gz attached :-)

---

### Post by kbielefe on 2009-10-26
Thanks.  For good measure, can you also attach your /etc/grub/menu.lst?

Also, try running "sudo update-grub" and rebooting.

---

### Post by Underlien on 2009-10-27
Hi again, sorry for the delay, i was at work.

The sudo grub update had no effect.

Here is the content of the grub-Menu.lst:
# sample /boot/grub/menu.lst entry for memtest86
#
# This example assumes the contents of /boot is on the root partition.
# If your /boot is on its own partition, remove /boot from the 'kernel' line.

title  memtest86+
root   (hd0,0)
kernel /boot/memtest86+.bin

title  memtest86+ (serial console 115200)
root   (hd0,0)
kernel /boot/memtest86+.bin console=ttyS0,115200n8 i8042.nomux=1 i8042.noacpi=1


The location of this file has changed since 9.04 i think.
Now its located in /usr/share/doc/memtest86+/examples

---

### Post by abeo on 2009-11-05
Hi, 
I have the same problem, my NEC VERSA E6510's keyboard can work in grub select-menu, but after that, when booting and go into X, the keyboard doesnt work any more, totally no respond. 
Im currently use ubuntu 9.10.
Any body can fix this? Please give me any instruction. Thanks.

---

### Post by Underlien on 2009-11-05
Hi

Im pretty sure it's a grub problem.

Since alot of changes was made from 1.5 to 2, the old fix does not work anymore.

Im also pretty sure that there is a fix to get the function of i8042.nopnp=1 i8042.dumbkbd=1 that worked in grub 1.5.

Any Grub Guru reading this? Please assist, would be much appreciated.

Underlien

---

### Post by abeo on 2009-11-05
Hi,

I've tried many distro before (Ubuntu ver 6.06, 7.10, 8.04, 8.10,9.04, open SUSE, KNOPPIX, SLAX ..) but none of them can makes my laptop keyboard and touch pad work. Nothing is recognized even when the system run fine with all features.

Any suggestion? 

Thanks

---

### Post by Sonema on 2009-12-25
"
 				 				**Laptop Keyboard not working at all after boot** 			
 			 			 		   		 		 		Hi

I have used ubuntu since 8.10 on my LG S900 laptop.

Back then, i had to add the line "i8042.nopnp=1 i8042.dumbkbd=1" to "Menu.lst to make the keyboard work once grub loaded the OS.

This has worked until i upgraded to 9.10 64bit.

Now i can't get it to work anymore, so i have to use a external USB keyboard to log in and actually use my computer.

The built-in touchpad works just fine.

Any idea's how i can get it to work again?

Help is greatly appreciated."


Hi!
i got same laptop and my keyboard works fine in Ubuntu 9.10. You need put those "i8042.nopnp=1 i8042.dumbkbd=1" at /etc/default/grub ,because menu.lst isnt anymore in use at new grub.

---

### Post by Underlien on 2009-12-25
Following the advice from Sonema i added i8042.nopnp=1 i8042.dumbkbd=1 to my grub on this line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.nopnp=1 i8042.dumbkbd=1"

After a reboot my keyboard works perfectly now! 

Thanks alot :D

---

### Post by zhi hao on 2010-06-02
> **Sonema said:**
> "
 				 				**Laptop Keyboard not working at all after boot** 			
 			 			 		   		 		 		Hi

I have used ubuntu since 8.10 on my LG S900 laptop.

Back then, i had to add the line "i8042.nopnp=1 i8042.dumbkbd=1" to "Menu.lst to make the keyboard work once grub loaded the OS.

This has worked until i upgraded to 9.10 64bit.

Now i can't get it to work anymore, so i have to use a external USB keyboard to log in and actually use my computer.

The built-in touchpad works just fine.

Any idea's how i can get it to work again?

Help is greatly appreciated."


Hi!
i got same laptop and my keyboard works fine in Ubuntu 9.10. You need put those "i8042.nopnp=1 i8042.dumbkbd=1" at /etc/default/grub ,because menu.lst isnt anymore in use at new grub.

Same prob, with LG E300 though. My mouse and trackpad work fine, however. Can anyone help?
Thanks.

---

### Post by travelour on 2010-06-03
I'm a newbie experiencing the same problem on 9.10 (never had problems with 8.10). It began suddenly when I was using Audacity.  
Now, I can log in, but at that point, the keyboard stops functioning (except the direction keys, one ctrl key and ALT with the F keys).  
I don't have a USB keyboard.  Anyway to fix this without one?
Thanks,
Marcus

---

