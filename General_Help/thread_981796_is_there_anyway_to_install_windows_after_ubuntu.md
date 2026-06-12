---
title: "is there anyway to install windows after ubuntu?"
date: 2008-11-14
forum: General Help
---

### Post by EnGorDiaz on 2008-11-14
ok i tryed to install windows after ubuntu (luckily i had supergrubdisk)thew... anyway is there anyway i can do this i got a disk error when i restarted

---

### Post by mikewhatever on 2008-11-14
Installing Windows after Ubuntu overwrites GRUB part from the MBR. You should reinstall grub to fix that, and supergrub disk is a good tool to do that.

---

### Post by EnGorDiaz on 2008-11-14
im having some trouble i have installed windows correctly but it wont show up on my grub list ive reinstalled grub and i have supergrubdisk i have about 3 partitions one fat32 ntfs and ext3 grub only boots into ext3 i want to add the ntfs partition to the list on my grub

---

### Post by Zhukov on 2008-11-14
> **EnGorDiaz said:**
> im having some trouble i have installed windows correctly but it wont show up on my grub list ive reinstalled grub and i have supergrubdisk i have about 3 partitions one fat32 ntfs and ext3 grub only boots into ext3 i want to add the ntfs partition to the list on my grub

Can you list the partition within Ubuntu?

Best regards!

---

### Post by TeXtonyx on 2008-11-14
Have you added something like the following entry to menu.lst?
gksudo gedit /boot/grub/menu.lst

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
chainloader	+1

Well your root probably isn't (hd0,0) which means your first drive,
first partition. So,  sudo fdisk -l , displays your partitions and
you can read the location of your Windows NTFS partition. It might
be (hd0,2) = sda3 (notice the partition number is one higher)
so your root entry uses the report from sudo fdisk -l (small L)

If you installed Windows last it overwrote grub in the MBR, so you
would need to reinstall grub so that it resides in the MBR. The 
advice given assumes you have a working grub and you just need to
fix your menu.lst which grub uses to provide your menu boot options.

---

### Post by d-man97 on 2008-11-14
Boot into Ubuntu using your floppy.

Find out the device names for your linux /boot partition (assuming it is separate from / partition) and your Windows partition.
On my system, I boot from /dev/sda5, and Windows would be on /dev/sdb1.

As I found out after swapping master/slave, Grub uses the drive you boot from as (hd0), instead of the actual master drive. So, assuming you boot from the master HD:
/dev/sda is (hd0,X) where X is partition number starting with 0.
/dev/sdb is (hd1,X) etc.

In my case /dev/sda5 is (hd0,4) and /dev/sdb1 is (hd1,0).

Now, open a terminal window:
```
$ sudo grub
```
This opens the grub console. (Quite easy once you play around with it.)
Now, in the grub console:
```
grub> root (hd0,4)  # Might not need this step, but do it just to be sure.
grub> setup (hd0)
grub> quit
```
Be sure to replace (hd0,4) with your linux /boot partition and (hd0) with the drive you want grub installed on!

That's it for grub. Now, in order to use grub for Linux & windows, you need to tell grub about Windows.
```
$ gksu gedit /boot/grub/menu.lst
```

If there isn't a Windows section commented out for you, create one:
> title Windoze
root (hd1,0)  # Be sure to replace this with yours!
makeactive
chainloader +1

A couple notes:
1) Do not put the windows section inside the automagic list, or else it will get wiped when update manager runs update-grub.

2) If you put it first, and the option 'default' is set to 'default 0', then windows will be loaded by default, since it is in the list first (item 0). To make your current Linux kernel load, use 'default 1' (where 0 is windows).

3) By default, grub hides the menu and loads the default after 3 seconds. Comment out 'hiddenmenu' to get the menu to come up everytime, and change the 'timeout' setting to your preference.

All-in-all, grub and menu.lst are pretty basic programs/scripts. You should get it easy enough.

If you end up using the grub menu, check out StartUp-Manager (sudo apt-get install startupmanager), you can give a custom resolution and GUI-like skin to the menu for easier use and better "effects". Grub skins are easily found with Google.

---

### Post by EnGorDiaz on 2008-11-14
> **TeXtonyx said:**
> Have you added something like the following entry to menu.lst?
gksudo gedit /boot/grub/menu.lst

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
chainloader	+1

Well your root probably isn't (hd0,0) which means your first drive,
first partition. So,  sudo fdisk -l , displays your partitions and
you can read the location of your Windows NTFS partition. It might
be (hd0,2) = sda3 (notice the partition number is one higher)
so your root entry uses the report from sudo fdisk -l (small L)

If you installed Windows last it overwrote grub in the MBR, so you
would need to reinstall grub so that it resides in the MBR. The 
advice given assumes you have a working grub and you just need to
fix your menu.lst which grub uses to provide your menu boot options.

thanks for yourhelp the thing that i think i got wrong was (hd0,2) thats must ve the partition sector

---

### Post by EnGorDiaz on 2008-11-14
im also installing osx86 on my machine which might be i think (hd0,3) which is the fat32

---

### Post by overdrank on 2008-11-14
Please do not create multiple threads on the same subject. Threads merged :)

---

### Post by mikewhatever on 2008-11-14
> **EnGorDiaz said:**
> im having some trouble i have installed windows correctly but it wont show up on my grub list ive reinstalled grub and i have supergrubdisk i have about 3 partitions one fat32 ntfs and ext3 grub only boots into ext3 i want to add the ntfs partition to the list on my grub

Thread subject: im trying to install windows after ubuntu.:confused:

Can a mode rename the thread, please.

---

### Post by d-man97 on 2008-11-14
As yet another note on this, grub can use the uuid of the partition in many places that the (hd0,0) nomenclature is used.

For your linux menu entry, for sure:
title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		8e585091-addf-444a-9c7d-2d5ed2906e27
kernel		/vmlinuz-2.6.27-7-generic root=/dev/mapper/dereksbox-root ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

For windows, you could try:
title		Windows
uuid		<UUID-of-partition>
makeactive
chainloader	+1

Apparently anywhere grub lists "root (hdX,#)", it can be replaced with "uuid <uuid>".

Using this, you can swap hard drives around, and do basically anything other than re-partition, and it will always find the correct partition.

---

### Post by EnGorDiaz on 2008-11-15
i just want to say thnx to all the ppl who helped me archieve this :)

---

### Post by overdrank on 2008-11-15
> **EnGorDiaz said:**
> i just want to say thnx to all the ppl who helped me archieve this :)

Glad to hear and I have moved to the same thread that you started with :)

---

