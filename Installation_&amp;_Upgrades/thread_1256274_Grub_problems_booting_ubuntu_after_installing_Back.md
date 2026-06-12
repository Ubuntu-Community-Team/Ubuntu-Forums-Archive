---
title: "Grub problems booting ubuntu after installing Backtrack"
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by SilvaRizla on 2009-09-02
I've installed Backtrack 4 alongside Vista and Ubuntu, and it has provided its own grub menu, but when I try to boot ubuntu I get an error 15 file not found.  Backtrack and vista boot fine.  Here is my grub menu:

```
splashimage=f52aa9ac-17a9-4a7d-9d07-75a4d05aeb82/boot/grub/splash.xpm.gz

title		Backtrack 4, kernel 2.6.29.4
uuid		f52aa9ac-17a9-4a7d-9d07-75a4d05aeb82
kernel		/boot/vmlinuz-2.6.29.4 root=UUID=f52aa9ac-17a9-4a7d-9d07-75a4d05aeb82 ro quiet splash 
initrd		/boot/initrd.img-2.6.29.4
quiet

title		Backtrack 4, kernel 2.6.29.4 (recovery mode)
uuid		f52aa9ac-17a9-4a7d-9d07-75a4d05aeb82
kernel		/boot/vmlinuz-2.6.29.4 root=UUID=f52aa9ac-17a9-4a7d-9d07-75a4d05aeb82 ro  single
initrd		/boot/initrd.img-2.6.29.4

title		Backtrack 4, memtest86+
uuid		f52aa9ac-17a9-4a7d-9d07-75a4d05aeb82
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista
root		(hd0,2)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Kubuntu 9.04, kernel 2.6.28-14-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=589194c0-17df-4f0e-8f8c-dc2cf7249a3e ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Kubuntu 9.04, kernel 2.6.28-14-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=589194c0-17df-4f0e-8f8c-dc2cf7249a3e ro single 
initrd		/boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Kubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=589194c0-17df-4f0e-8f8c-dc2cf7249a3e ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Kubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=589194c0-17df-4f0e-8f8c-dc2cf7249a3e ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Kubuntu 9.04, memtest86+ (on /dev/sda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot

```

Backtrack is located on sda1
Swap is sda2
Vista is located on sda3
Sda4 is an extended partition
   Ubuntu is located under sda4 on sda5

I have a script uuid's - this is the output

```

extended partitions do not have uuids and are not mountable:
sda4 = extended partition

swap spaces (virtual memory) do have uuids:
UUID (sda2 => swap) = e9734580-10ef-47d8-ba4f-61f692682c6e

regular partitions (primary or logical) also have uuids:
UUID (sda1 => /) = f52aa9ac-17a9-4a7d-9d07-75a4d05aeb82
UUID (sda2 => ) = e9734580-10ef-47d8-ba4f-61f692682c6e
UUID (sda3 => /media/OS) = A0F2FEFAF2FED40E
UUID (sda5 => /media/Kubuntu) = 589194c0-17df-4f0e-8f8c-dc2cf7249a3e

``` 

Can someone please tell me how to fix my boot loader to boot all OS's? Is it possible to reinstate my original Kubuntu grub and manually add backtrack to it? Menu.lst still exists on sda5 under /boot/grub/ Thanks

**************************For those looking to fix the same issue I made some mistakes trying to update grub to be able to boot an ext4 drive, to save you doing the same, here is how I got it working*******************************

First I reinstated my original Kubuntu boot loader which doesn't have a Backtrack entry

```


You will need a LIVE cd if you are going to recover an Ubuntu Box.Download Ubuntu Jaunty, Karmic whatever you want.Open the system with Live CD (I assume you are using Ubuntu Live CD).Press Alt+F2 and enter gnome-terminal command.And continue by entering :

$sudo fdisk -l

This will show your partition table.Here is my table to understand it better :

/dev/sda1 29 8369 66999082+ 83 Linux
/dev/sda2 * 8370 13995 45190845 7 HPFS/NTFS
/dev/sda3 13996 14593 4803435 5 Extended
/dev/sda5 13996 14593 4803403+ 82 Linux swap / Solaris

Now i will mount Linux (sda1 here), i have no external boot partition as you can see.(IF YOU HAVE external one, do not forget to mount it! )

$sudo mount /dev/sda1 /mnt
$sudo mount --bind /dev /mnt/dev
$sudo mount --bind /proc /mnt/proc

The following command is optional (it copies resolv.conf)

$sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

Now chroot into the enviroment we made :

sudo chroot /mnt

After chrooting, you do not need to add sudo before your commands because from now, you will run commands as root.

You may want to edit /etc/default/grub file to fit your system (timeout options etc)

#nano -w /etc/default/grub

Play with the options if you want.(But do not forget to give grub-update command if you saved it ;) )

Now install/recover Grub2 via :

#grub-install /dev/sda

command.However you may get errors with that code like me.If so please use this command :

#grub-install --recheck /dev/sda

Now you can exit the chroot, umount the system and reboot your box :

#exit
$sudo umount /mnt/dev
$sudo umount /mnt/proc
$sudo umount /mnt
$sudo reboot


```

And then I added this to my menu.lst as a pointer to Backtracks grub which I knew booted BackTrack

```


title		Backtrack 4
configfile	(hd0,0)/boot/grub/menu.lst


```

---

### Post by stlsaint on 2009-09-02
have you considered re-isntalling Grub to (hd0) as the system bootloader? should any problems arise yu can add stanzas to menu.lst to include other OS.
see [here]("http://ubuntuforums.org/showthread.php?t=224351") for directions.

---

### Post by SilvaRizla on 2009-09-02
> **stlsaint said:**
> have you considered re-isntalling Grub to (hd0) as the system bootloader? should any problems arise yu can add stanzas to menu.lst to include other OS.
see [here]("http://ubuntuforums.org/showthread.php?t=224351") for directions.

I have and still am considering it but I don't want to take this step just yet incase I mess it up, I think I may have to though as I have just realized Backtrack 4 is based up Intrepid so probably doesn't support ext4 booting wich is my ubuntu filesystem

---

### Post by stlsaint on 2009-09-02
yep you may want to go ahead and reinstall grub...that link i sent should be enough if not there are grub and grub/mbr links in my sig that will go more in depth.

---

### Post by SilvaRizla on 2009-09-02
Well, I cocked that up! Couldn't boot ANY Linux OS

Using vista I managed to find some instructions on how to reinstate my previous GRUB from Ubuntu

```


You will need a LIVE cd if you are going to recover an Ubuntu Box.Download Ubuntu Jaunty, Karmic whatever you want.Open the system with Live CD (I assume you are using Ubuntu Live CD).Press Alt+F2 and enter gnome-terminal command.And continue by entering :

$sudo fdisk -l

This will show your partition table.Here is my table to understand it better :

/dev/sda1 29 8369 66999082+ 83 Linux
/dev/sda2 * 8370 13995 45190845 7 HPFS/NTFS
/dev/sda3 13996 14593 4803435 5 Extended
/dev/sda5 13996 14593 4803403+ 82 Linux swap / Solaris

Now i will mount Linux (sda1 here), i have no external boot partition as you can see.(IF YOU HAVE external one, do not forget to mount it! )

$sudo mount /dev/sda1 /mnt
$sudo mount --bind /dev /mnt/dev
$sudo mount --bind /proc /mnt/proc

The following command is optional (it copies resolv.conf)

$sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

Now chroot into the enviroment we made :

sudo chroot /mnt

After chrooting, you do not need to add sudo before your commands because from now, you will run commands as root.

You may want to edit /etc/default/grub file to fit your system (timeout options etc)

#nano -w /etc/default/grub

Play with the options if you want.(But do not forget to give grub-update command if you saved it ;) )

Now install/recover Grub2 via :

#grub-install /dev/sda

command.However you may get errors with that code like me.If so please use this command :

#grub-install --recheck /dev/sda

Now you can exit the chroot, umount the system and reboot your box :

#exit
$sudo umount /mnt/dev
$sudo umount /mnt/proc
$sudo umount /mnt
$sudo reboot

```

Now to add backtrack to it....

---

### Post by SilvaRizla on 2009-09-03
I'm still pulling my hair out on this one, I've added this to my menu.lst but no joy

```


title	BackTrack 4
rootnoverify	(hd0,0)
kernel	(hd0,0)/boot/vmlinuz rw root=/dev/sda1
initrd	(hd0,0)/boot/splash.initrd
boot


```

---

### Post by stlsaint on 2009-09-03
boot into livecd go [here]("http://sourceforge.net/projects/bootinfoscript/") and download the boot script to your desktop. this will tell us some info about where your boot files are on your hdd. after you download the script to your desktop run it via terminal:

sudo bash ~/Desktop/boot_info_script*.sh

this will put a RESULTS.txt on your desktop. post that txt file here so we can further help you.

---

### Post by stlsaint on 2009-09-03
> **SilvaRizla said:**
> I'm still pulling my hair out on this one, I've added this to my menu.lst but no joy

```


title	BackTrack 4
rootnoverify	(hd0,0)
kernel	(hd0,0)/boot/vmlinuz rw root=/dev/sda1
initrd	(hd0,0)/boot/splash.initrd
boot


```


doesnt seem right stanza to add but the boot script will tell us more.

---

### Post by SilvaRizla on 2009-09-03
Its ok I got it sorted late last night, when I installed Grub 2 in the hope that would boot the ext4 of Ubuntu and it cocked everything up, Grub stored a backup of the original menu.lst from BackTrack, so I deleted menu.lst (the new b0rked one) and renamed menuold.lst (not the exact name but you get the idea) to menu.lst.  I then added this section to the menu.lst of ubuntu (the currently booting one).

```


title		Backtrack 4
configfile	(hd0,0)/boot/grub/menu.lst


```

This obviously directed grub to the grub menu stored on the backtrack drive which I knew booted backtrack but not much else so I just removed the entries from the OS's that didn't work

---

### Post by stlsaint on 2009-09-03
GREAT! congrats...please mark thread as resolved or solved.

---

