---
title: "Windows XP not being recognized by GRUB"
date: 2008-08-19
forum: General Help
---

### Post by Aspras on 2008-08-19
Hello everybody, I decided i wanted to try out Ubuntu a few days ago and thats what i did. GRUB was working normally so each time my pc started up i could choose beetween Ubuntu and my previously installed Windows XP. After realising that my sound card was not supported i decided to uninstall Ubuntu. 
Unfortunately i did that by deleting the partition i had ubuntu on using Windows XP's hard drive managing software. And also the 700mb partition where i believe GRUB was installed on. This is where all went wrong, after deleting those 2 partitions i couldnt boot into Windows XP anymore so i now have reinstalled Ubuntu (Thank god i have it) and GRUB still doesnt recognize my Windows XP. I have precious data that i need in there which i can only use with Windows XP so i have to find a way to get back in there. 
Sorry if i started this thread in the wrong section, its my first time in these forums and im also in quite a bad situation over here, any help regarding my problem will be greatly apreciated.

---

### Post by Canis familiaris on 2008-08-19
Could you post the output of:

```
gedit /boot/grub/menu.lst
```

And also

```
sudo fdisk -l
```

---

### Post by JCheung on 2008-08-19
you into the ubuntu then
in the shell type:
```

sudo geidt /boot/grub/menu.lst

```

in the menu.list file 

```

title Ubuntu ******
root  (hd0,*)
kernel  /boot/vmlinuz-*** root=UUID=**** ro quiet splash
initrd  /boot/initrd.img-****
quiet

```
this is boot the ubuntu

```

title		Microsoft Windows XP Professional        #this name is default,u can edit it
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```
this is boot the XP

if you uninstall the ubuntu
you can type:
```

root (hd0,0)
savedefault
makeactive
chainloader	+1

```

into the XP

---

### Post by Aspras on 2008-08-19
Thanks a lot for the replies, i will post what i have in my menu.lst :

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1379d1f0-06c4-41b2-82d6-790a163d388c ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1379d1f0-06c4-41b2-82d6-790a163d388c ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

And this is what i get when i do the fdisk command:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01160116

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

---

### Post by Bucky Ball on 2008-08-19
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Download, make a cd, boot from that and see if you can't fix your problem quick and easy.

---

### Post by Aspras on 2008-08-19
I used my Paragon Safe Disk to check my hard drive , it looks like my whole Windows XP got deleted when i reinstalled Ubuntu :(  . Thanks for all the support either way

---

