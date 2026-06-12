---
title: "Making Grub boot into windows by default.... (Solved)"
date: 2005-11-27
forum: General Help
---

### Post by TrueDego on 2005-11-27
Ive read through the Menu.lst for a little while now and I still dont get what I have to do to get Windows to be the default that grub loads into if no one selects an opition.  Also here is my Menu.lst file and if anyone can tell me how to change the  file so i can overwrite it please let me know.   Thanks!!! 


```
title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

---

### Post by ozorba on 2005-11-27
[QUOTE=TrueDego]Ive read through the Menu.lst for a little while now and I still dont get what I have to do to get Windows to be the default that grub loads into if no one selects an opition.  Also here is my Menu.lst file and if anyone can tell me how to change the  file so i can overwrite it please let me know.   Thanks!!![/QUOTE]

Find the followings in your /boot/grub/menu.lst 
```

title Ubuntu, kernel 2.6.12-9-386
root (hd0,1)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash
initrd /boot/initrd.img-2.6.12-9-386
savedefault
boot

```
and change it as below (Note the first entry should be Windows):
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1


title Ubuntu, kernel 2.6.12-9-386
root (hd0,1)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash
initrd /boot/initrd.img-2.6.12-9-386
savedefault
boot

title Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro single
initrd /boot/initrd.img-2.6.12-9-386
boot

title Ubuntu, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by aysiu on 2005-11-27
Can I respectfully disagree?
If you plop Windows into the "automagically generated" section, the next time you have an updated kernel in Ubuntu, the Windows entry will either disappear altogether or get bumped back down (so as not to be the default).

It's better to find the part in the very beginning that says ```
default 0
``` and change it to be ```
default 4
``` I've circled this part of the /boot/grub/menu.lst in red.

---

### Post by TrueDego on 2005-11-27
Ive tried to change the Default # but it wont let me.  If i compy everything and try change it and attempt to overwrite the file to the orginal menu.lst it wont let me.

---

### Post by Xian on 2005-11-27
Open the file with admin rights from a terminal:

$ sudo gedit /boot/grub/menu.lst

---

### Post by Bachstelze on 2005-11-27
sudo is your friend :p Run : 

sudo gedit /boot/grub/menu.lst

---

### Post by Roman27 on 2005-11-27
[QUOTE=aysiu]If you plop Windows into the "automagically generated" section, the next time you have an updated kernel in Ubuntu, the Windows entry will either disappear altogether or get bumped back down (so as not to be the default).[/QUOTE]

Thank you very much for this tid-bit.  I was wondering why my Microsoft Windows XP option disappeared after I updating the kernel.

---

### Post by TrueDego on 2005-11-27
Changing the Default # to 4 fixed the problem and the Sudo code allowed me to change it.  Thanks so much guys.  If you have this problem, this is how you fix it!!!!!

---

### Post by shane2peru on 2005-11-27
Oh, I missed that coding, that is why my windows disappeared after my kernel upgrade.  I will have to change that number.  Luckily I played around with my menu.lst before, and knew how to add it back in.  Now if I could only get ubuntu up and running correctly again, I would be happy!

Shane

---

### Post by shane2peru on 2005-12-09
[QUOTE=aysiu]Can I respectfully disagree?
If you plop Windows into the "automagically generated" section, the next time you have an updated kernel in Ubuntu, the Windows entry will either disappear altogether or get bumped back down (so as not to be the default).

It's better to find the part in the very beginning that says ```
default 0
``` and change it to be ```
default 4
``` I've circled this part of the /boot/grub/menu.lst in red.[/QUOTE]
Would this always be ```
default 4
``` or if you have other things booting would/could it change it to say for example.. ```
default 6
```  and is this respective to the amount of options given.  
1. Ubuntu *kernel version*
2. Ubuntu *kernel version*
3. Mem test thing
4.  Windows XP Home

So if I wanted to default into option 2 would it be ```
default 2
```?

Thanks.

Shane

---

### Post by shane2peru on 2005-12-10
Ok, I did find this to be true.  They are numbered something like this even though the numbers are not there:
0  Ubuntu Kernel a.a.a.a
1  Ubuntu Kernel a.a.a.a failsafe
2  Ubuntu Kernel b.b.b.b
3  Ubuntu Kernel b.b.b.b failsafe
4  Mem Test
Other Operating Systems:
5 Windows XP Home

When I changed it to: ```
default 4
``` it defaulted to Mem Test.  So I need to change mine to 5.  Just in case anyone needs to know!

Shane

---

### Post by Gray. on 2005-12-10
Actually, I think that the line 'Other Operating Systems:' is counted as a line so it would be 5 and Windows XP Home would be 6.

---

### Post by shane2peru on 2005-12-10
You are right my friend Gray.  I would have never guessed that the line - Other Operating Systems would have counted.  I guess it is a line count and not a boot option choice.  Thanks!

Shane

---

### Post by aysiu on 2005-12-10
[QUOTE=shane2peru]I guess it is a line count and not a boot option choice. [/QUOTE] It's any entry that has the word *title* in the beginning.

---

### Post by Raval on 2006-11-06
> **aysiu said:**
> It's any entry that has the word *title* in the beginning.

It did for me

---

