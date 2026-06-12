---
title: "how do I restore my system..."
date: 2005-06-24
forum: Hardware &amp; Laptops
---

### Post by dlpfmVfH on 2005-06-24
I have a dualboot windows mce with Ubuntu...
Windows is at the master drive hd0,0
ubuntu is at the slave drive hd1,0

now my problem is that my windows doesn't boot anymore failure of some dll...
(windows..yeah woopie)

 But I need a new working windows, and want to reinstall windows...
without losing my ubuntu hd..and conf...

is this possible...

reinstalling windows xp...without touching grub / mbr...
or do I need to install windows xp and then change back to grub....
and ad ubuntu ....??

---

### Post by nictuku on 2005-06-24
Here's what I did. Be aware that this can be dangerous and if you don't know what you're doing you shouldn't try it all.

1) Save your current boot sector

While in Ubuntu, run the following command:

# dd if=/dev/hda of=/root/bootsec.raw bs=512 count=1

2) Go and install Windows.

It will brake your GRUB boot. Remember not to delete the Linux filesystem when creating the windows file system during the install.

3) Recover your old boot sector:

Boot using the Ubuntu installation CD. Mount your hard disk (if you don't know how, maybe you should not be trying this), then run:

# dd if=<mount-point>/root/bootsec.raw of=/dev/hda

4) Boot and enter ubuntu. Edit /boot/grub/menu.lst and setup the Windows partition boot.


Add something like:

 title          Windows 95/98/NT/2000
 root           (hd0,3)
 makeactive
 chainloader    +1

That would work if your Windows XP is at "/dev/hda4". You can find that by running:

#fdisk -l /dev/hda


NOTE: I used /dev/hda, but that is only my case. Yours can be /dev/hdb, or /dev/sda or something like that.

I hope it helped.

- Yves Junqueira

---

### Post by dlpfmVfH on 2005-06-24
[QUOTE=nictuku]Here's what I did. Be aware that this can be dangerous and if you don't know what you're doing you shouldn't try it all.

1) Save your current boot sector

While in Ubuntu, run the following command:

# dd if=/dev/hda of=/root/bootsec.raw bs=512 count=1

2) Go and install Windows.

It will brake your GRUB boot. Remember not to delete the Linux filesystem when creating the windows file system during the install.

3) Recover your old boot sector:

Boot using the Ubuntu installation CD. Mount your hard disk (if you don't know how, maybe you should not be trying this), then run:

# dd if=<mount-point>/root/bootsec.raw of=/dev/hda

4) Boot and enter ubuntu. Edit /boot/grub/menu.lst and setup the Windows partition boot.


Add something like:

 title          Windows 95/98/NT/2000
 root           (hd0,3)
 makeactive
 chainloader    +1

That would work if your Windows XP is at "/dev/hda4". You can find that by running:

#fdisk -l /dev/hda


NOTE: I used /dev/hda, but that is only my case. Yours can be /dev/hdb, or /dev/sda or something like that.

I hope it helped.

- Yves Junqueira[/QUOTE]
 Ok, I understand the method of use...
except for the mount points....
My mountpoints...are:

/dev/hda is my former windows xp that doesn't work. (on master hd..0,0)
/dev/hdb is my ubuntu disk...it is a separate hd...(on slave hd 1,0)

to get mbr copied:
dd if=/dev/hda of=/root/bootsec.raw bs=512 count=1

so the mount point to get mbr back would be:
dd if=/dev/hda/root/bootsec.raw of=/dev/hdb

am I correct??

---

### Post by nictuku on 2005-06-24
[QUOTE=aboe]Ok, I understand the method of use...
except for the mount points....
My mountpoints...are:

/dev/hda is my former windows xp that doesn't work. (on master hd..0,0)
/dev/hdb is my ubuntu disk...it is a separate hd...(on slave hd 1,0)

to get mbr copied:
dd if=/dev/hda of=/root/bootsec.raw bs=512 count=1

so the mount point to get mbr back would be:
dd if=/dev/hda/root/bootsec.raw of=/dev/hdb

am I correct??[/QUOTE]
 
First of all, one notice. That lines are not "mount points". Those are backup and restore of boot sectors.

You won't change those. As I presume you are using the primary disk as your boot device (check your BIOS, most usually it is), you will run the dd's in /dev/hda only.

Now, when editing grub's menu.lst, you will only have to change the line pointing to Windows:

```

 title Windows 95/98/NT/2000
root (hd1,0)
makeactive
chainloader +1

```


Please note that grub's "hd1,0" means linux' hdb1. It's important to know wheter your Windows is really in hdb1, or hdb2 or something like that. Check using fdisk -l /dev/hdb. Usually it will be in /dev/hd?1.

I should warn again that you should be cautious. Make backups of your data into a CD. That won't hurt and can be very useful.

---

### Post by dlpfmVfH on 2005-06-24
but wait,, my grub menu.lst is fine..it has already found windows...on (hd0,0)

and that 's is the drive I want to reinstall windows xp.. on...
the only problem is hd(0,0) also has the grub mbr..on it...when I install windows xp it will remove grub from mbr...I want to have grub mbr back...

that is the main idea...

---

### Post by nictuku on 2005-06-24
I'm starting to think you are not really getting the idea :-).

backup your mbr:

dd if=/dev/hda of=/root/bootsec.raw bs=512 count=1

install windows

boot to ubuntu install cd

Pass a few screens until it finish the steps of detecting hardware.

Go to the second console and mount your old linux:

# mkdir /mnt
# mount /dev/hdb1 /mnt

restore you mbr:

dd if=/mnt/root/bootsec.raw of=/dev/hda

I repeat. You might lose all your data if you don't know what you're doing...

---

### Post by dlpfmVfH on 2005-06-25
ok thanks, I did the backup...
now trying to install windows xp...
hope it all goes well

thanks

---

