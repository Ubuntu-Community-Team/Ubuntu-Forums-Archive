---
title: "Triple Boot with Grub?"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by lambono on 2008-12-30
Hello,
I currently dual boot windows xp and ubuntu using the grub boot loader. 

I would like to install a second copy of windows xp and was hoping someone could explain the best way to do this....? 

I had planned to make a new partition to install Windows and then reconfigure grub.
Should the following instructions (from [http://sreejithemk.wordpress.com/2008/06/02/recovering-ubuntu-after-windows-installation/?referer=sphere_related_content/](http://sreejithemk.wordpress.com/2008/06/02/recovering-ubuntu-after-windows-installation/?referer=sphere_related_content/)) be sufficient to get Grub working with the is 3 operating systems?? 

   1. Insert the Live CD and boot from it
   2. After ubuntu is loaded, open a terminal
   3. Now, type sudo grub-install /dev/sda
   4. Done. The GRUB will be installed to the MBR
   5. Reboot the PC

Thanks very much for your advice!

---

### Post by SuperSonic4 on 2008-12-30
I believe you have to edit grub to show both XP editions, just back up sensitive data as a precaution.

The simplest method would be to install ubuntu last.

---

### Post by caljohnsmith on 2008-12-30
> **lambono said:**
> 

   1. Insert the Live CD and boot from it
   2. After ubuntu is loaded, open a terminal
   3. Now, type [COLOR="Blue"]sudo grub-install /dev/sda[/COLOR]
   4. Done. The GRUB will be installed to the MBR
   5. Reboot the PC


Unfortunately that grub-install command will not work as you have it written if you run it from the Live CD; you would need to mount your Ubuntu partition and use the --root-directory=/media/Ubuntu_partition" option with that command so that the Grub that gets installed to the MBR will point to the Ubuntu partition for its boot files. But you don't need to use the grub-install command if you all ready have Grub's boot files present in Ubuntu's /boot/grub directory; to restore Grub to your MBR, I would instead recommend doing:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,2), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
And then you should get your Grub menu back on start up. All that would be left to do is add your new XP partition to the Grub menu, and if you need help with that, let me know. Otherwise good luck and let us know how it goes.

---

### Post by lambono on 2008-12-30
Hi,
Thanks very much for the replies! 
How do I add add the new XP partition to the Grub menu?

Cheers,
Lambono

---

### Post by caljohnsmith on 2008-12-30
To add you new XP partition to the Grub menu, first open your Grub menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And then add:
```
title Windows XP
root (hd0,X)
chainloader +1
```
And change X to be the XP partition number minus one. Thus sda1 is (hd0,0), sda2 is (hd0,1), sda3 is (hd0,2), etc.

---

### Post by lambono on 2008-12-31
Thats great, Thanks.

Sorry for the Windows question but this is the best place to get help... :)

Am I able to install windows on an end partition of my drive (i.e is not part to the 2Gig boot sector)?

Cheers

---

