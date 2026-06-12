---
title: "Deletion and reinstallation of partitions help (newbie)"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by HolyMythos on 2009-08-22
So, yesterday I had installed Ubuntu. Unfortunately, I didn't allocate enough space for the partition and I ran out. I didn't want to deal with resizing partitions on my own since this is my first time doing anything, and I was told to just reinstall Ubuntu. Unfortunately, I thought it would overwrite the other Ubuntu partition, which it didn't. I allocated a lot more space this time for my new Ubuntu, but again it was used up almost instantly, probably because I was importing files from Windows.

Now I'm left with some problems and questions. I want to reinstall Ubuntu for the last time, while deleting the old Ubuntu's. Only problem is, one of the Ubuntu's are my primary boot OS. How can I change the primary boot OS from Ubuntu to vista? And if I change that, I'll be able to delete the Ubuntu partitions and install Ubuntu again with no problem, right?

Basically, I really, really, really want to know how to make Vista my primary boot OS rather than Ubuntu.

I also do NOT have the Vista installation CD.

---

### Post by stlsaint on 2009-08-22
ok dont worry all will be well...first off as long as you have ubuntu installed with Grub...and unless you change your settings wing BUM you will have to select which OS to use...first post results of this.... sudo gedit /boot/gub/menu.lst  

also im thinking that you can just format both partitions using Gparted and resize them to the final size you want then re-install!! post for any issues you run into!!

---

### Post by running_rabbit07 on 2009-08-22
To get rid of the two Ubuntu installs,

1. Boot the LiveCD into the boot disk without making changes option and go to System>Administration>Partition Editor.

2. Delete both Ubuntu partitions and if there are more than one SWAP partitions, delete the second one.

3. After the partitioning is done. close the program and click the Install Ubuntu icon on the desktop.

Before I give any more steps can you tell me how much space the Ubuntu partitions are using?

---

### Post by HolyMythos on 2009-08-22
> **running_rabbit07 said:**
> To get rid of the two Ubuntu installs,

1. Boot the LiveCD and go to System>Administration>Partition Editor.

2. Delete both Ubuntu partitions and if there are more than one SWAP partitions, delete the second one.

3. After the partitioning is done. close the program and click the Install Ubuntu icon on the desktop.

Before I give any more steps can you tell me how much space the Ubuntu partitions are using?

My first Ubuntu only had 2.3gb, I didn't know I had to manually add more space during installation. My second one had 8gb, I thought it would be enough considering I thought it would get rid of the old partition. My next one is probably gonna have a good 30gb. If I delete the Ubuntu's, and install another one, will I still get the grub menu when I startup my computer, making Vista selectable?

---

### Post by nhanquy on 2009-08-22
1. Load LiveCD
2. Use "Partition Editor" to delete all unwanted partitions ( unused Ubuntu,.... ) - "Apply" it!
3. Use LiveCD again to install Ubuntu (this time Ubuntu will install on the unallocated space of the disk.
4. Reboot PC ( take out the CD)
5. PC should come up with Ubuntu as default and your Windows would be in the selection list also.
6. Go and edit /boot/grub/menu.lst to select Windows as your default OS. (should be easy but read GRUB manual before going to do it!)

---

### Post by Shazaam on 2009-08-22
1. On the Ubuntu livecd is a program called "Partition Editor" (gparted). You can run that to add/delete/resize partitions. Do NOT delete any NTFS or FAT partitions found.
2. Open menu.lst (letter L) as root...
```
gksudo gedit /boot/grub/menu.lst
```
and count your kernel entries (including Windows). In this example...
```
## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-15-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-15-generic root=/dev/sda6 ro quiet splash vga=771 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-15-generic root=/dev/sda6 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```
Windows is #4. Go here...
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0
```
and change the 0 to whatever number Windows is then save the file.

---

### Post by HolyMythos on 2009-08-22
> **Shazaam said:**
> 1. On the Ubuntu livecd is a program called "Partition Editor" (gparted). You can run that to add/delete/resize partitions. Do NOT delete any NTFS or FAT partitions found.
2. Open menu.lst (letter L) as root...
```
gksudo gedit /boot/grub/menu.lst
```and count your kernel entries (including Windows). In this example...
```
## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-15-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-15-generic root=/dev/sda6 ro quiet splash vga=771 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-15-generic root=/dev/sda6 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, memtest86+
root        (hd0,5)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd1,0)
savedefault
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

```Windows is #4. Go here...
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0
```and change the 0 to whatever number Windows is then save the file.

What do you mean open menu.lst as root? I put in the code you told me in a terminal and I got a blank notepad type window.

---

### Post by nhanquy on 2009-08-22
> **HolyMythos said:**
> What do you mean open menu.lst as root? I put in the code you told me in a terminal and I got a blank notepad type window.

$sudo -i

....

#<your editor> /boot/grub/menu.lst

---

### Post by HolyMythos on 2009-08-22
> **nhanquy said:**
> $sudo -i

....

#<your editor> /boot/grub/menu.lst

I did that and still got a blank menu.lst

---

### Post by running_rabbit07 on 2009-08-22
> **HolyMythos said:**
> My first Ubuntu only had 2.3gb, I didn't know I had to manually add more space during installation. My second one had 8gb, I thought it would be enough considering I thought it would get rid of the old partition. My next one is probably gonna have a good 30gb. If I delete the Ubuntu's, and install another one, will I still get the grub menu when I startup my computer, making Vista selectable?

Yes, you will get the dual boot option.
			 		   		 		 		To get rid of the two Ubuntu installs,

1. Boot the LiveCD into the boot disk without making changes option and go to System>Administration>Partition Editor.

2. Delete both Ubuntu partitions and the SWAP partitions. 

3. Click on and resize your NTFS partition to fill the unallocated space where the Ubuntus were.

4. Close the partition editor and click on the Install icon on the desktop and start the process again. You don't have to use 30 gigs but if you have the space go for it.

5. In the install partitioner you can drag the slider to give the installer 30 gigs.

6. Let the installer do it's thing and you will have a complete installation in 20 to 30 minutes. Grub will install itself and you will have a dual boot system.

---

### Post by HolyMythos on 2009-08-22
> **running_rabbit07 said:**
> Yes, you will get the dual boot option.
                                                  To get rid of the two Ubuntu installs,

1. Boot the LiveCD into the boot disk without making changes option and go to System>Administration>Partition Editor.

2. Delete both Ubuntu partitions and the SWAP partitions. 

3. Click on and resize your NTFS partition to fill the unallocated space where the Ubuntus were.

4. Close the partition editor and click on the Install icon on the desktop and start the process again. You don't have to use 30 gigs but if you have the space go for it.

5. In the install partitioner you can drag the slider to give the installer 30 gigs.

6. Let the installer do it's thing and you will have a complete installation in 20 to 30 minutes. Grub will install itself and you will have a dual boot system.

Alright, as long as I get grub to work after deletion and reinstallation then I'm happy. Now it's time to start it up and see if I screw it all up lol

---

### Post by running_rabbit07 on 2009-08-22
> **HolyMythos said:**
> Alright, as long as I get grub to work after deletion and reinstallation then I'm happy. Now it's time to start it up and see if I screw it all up lol

I think you'll do fine.

---

### Post by HolyMythos on 2009-08-22
> **running_rabbit07 said:**
> I think you'll do fine.

Alright, did it and everything works fine. Haven't loaded Ubuntu yet, I was more scared of Vista not loading right, but it did. Thank god. Thanks guys for all the help!

---

