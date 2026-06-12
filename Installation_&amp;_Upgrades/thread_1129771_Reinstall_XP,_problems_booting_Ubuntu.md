---
title: "Reinstall XP, problems booting Ubuntu"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by Macamba on 2009-04-19
Hi,

The other day I had to install XP again. As I had to format the partition, my boot loader was lost. I put it back using the Ubuntu Live CD, but after reboot I got an 'Error 17: Cannot mount selected partition'.

This is what I did:

1 Boot Ubunut from CD
2 Opened a terminal, performed a 
```
sudo fdisk -l
```
The result was:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6375    51207156    7  HPFS/NTFS
/dev/sda2            6376       25497   153597465    6  FAT16
/dev/sda3           25498       91201   527767380    f  W95 Ext'd (LBA)
/dev/sda5           25498       31871    51199123+   7  HPFS/NTFS
/dev/sda6           31872       38245    51199123+   7  HPFS/NTFS
/dev/sda7           38246       44619    51199123+   7  HPFS/NTFS
/dev/sda8           44620       46186    12586896   83  Linux
/dev/sda9           46187       57080    87506023+  83  Linux
/dev/sda10          57081       57367     2305296   82  Linux swap / Solaris
/dev/sda11          57368       70115   102398278+   7  HPFS/NTFS
/dev/sda12          70116       82863   102398278+   7  HPFS/NTFS
/dev/sda13          82864       91201    66974953+   7  HPFS/NTFS

```
3 Next I performed a 
```
sudo grub
```
4 And to be sure I had the correct partition, I performed
```
grub> fdisk -l
```
with the result
```
find /boot/grub/stage1
 (hd0,7)
grub> 
```
5 Next I instructed Grub where my Ubuntu partition is by entering 
```
root (hd0,7)
setup (hd0)
quit
```
6 So far as instructed by the book. To be absolutely sure, I tried to find menu.lst by entering
```
sudo gedit /boot/grub/menu.lst
```
This was the result:
```
## ## End Default Options ##

title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,10)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=bf978112-024f-4cd6-95d4-8bc32588e26f ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,10)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=bf978112-024f-4cd6-95d4-8bc32588e26f ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,10)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=bf978112-024f-4cd6-95d4-8bc32588e26f ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,10)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=bf978112-024f-4cd6-95d4-8bc32588e26f ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,10)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```
And I noticed 
```
title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,10)
```
7 Then I restarted my system. The boot menu came up fine. I can boot Windoze. But when I choose to boot Linux I get
```
Error 17: Cannot mount selected partition
```

Do I get this error because I'm trying to boot from my Swap partition? How can I change (hd0,10) to (hd0,7) when I can not write menu.lst (because it is part of a file system I have no write access to)?

Macamba

---

### Post by Herman on 2009-04-19
If you're doing it from the Ubuntu Live CD, you just need to mount your hard disk installed Ubuntu and then,
```
gksudo gedit /media/disc/boot/grub/menu.lst
```
Where: the mount point in /media is called 'disc', it could be something else like 'disc0, or 'disc1', if so, please replace 'disc' with whatever the name of the mount point really is.

---

### Post by Macamba on 2009-04-19
When I look at the output I got when I performed 
```
sudo fdisk -l
```
I got
```
/dev/sda8           44620       46186    12586896   83  Linux
/dev/sda9           46187       57080    87506023+  83  Linux
/dev/sda10          57081       57367     2305296   82  Linux swap / Solaris

```

I know my operating system is on 
```
/dev/sda8  
```

Would I need to perform
```

gksudo gedit /media/disc7/boot/grub/menu.lst
```

I tried that, and I got an empty screen.

Or should I mount (explicit) the root partition. I looked around, and could not find out how to do it.

Macamba

---

### Post by coffeecat on 2009-04-19
> **Macamba said:**
> [/code]I know my operating system is on 
```
/dev/sda8  
```

OK. What you need to do is in the live session, go to the Places menu and find the sda8 partition. Click on it and a Nautilus window should open.

> **Macamba said:**
> Would I need to perform
```

gksudo gedit /media/disc7/boot/grub/menu.lst
```I tried that, and I got an empty screen.

That assumes that sda8 has been mounted on /media/disc7, which would only happen if you create such a mountpoint and mount from the terminal.

> **Macamba said:**
>  Or should I mount (explicit) the root partition.

Yes. Having mounted sda8 from the Places menu, have a look at the Nautilus window that has opened. There's a little icon like a pen over a notebook to the left of the address bar - now probably showing the path in icons. Click on that and the path will change to something like:

```
/media/something
```Now, substituting for whatever 'something' is:

```
gksudo gedit /media/something/boot/grub/menu.lst
```

---

### Post by Macamba on 2009-04-19
Thanks Herman and Coffecat. I will try your suggestions.

---

### Post by Herman on 2009-04-19
Sorry, I was assuming you already knew how to mount your file system or else how did you get all the info you posted in your first post?

Here's a link that will show you how to mount a file system in the Live CD, [Click-Icon Mounting]("http://users.bigpond.net.au/hermanzone/p10.htm#Click-Icon_Mounting"). That's 'the new way'.

The old fashioned way was to mount the file system with a 'mount' command at the command line, or edit /etc/fstab, but we had to make a 'mount point' first, in /media usually. Here's how us old timers used to do it, [Mounting Filesystems with the mount command]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop") - Traditional olde reliable method.

So, there should be a directory, (folder) in your /media directory and when you open it, it should have your Ubuntu files from your hard disk inside it. We call that directory the 'mount point'.
If we made it ourselves by the old method, we would have though up our own name for it, so we would remember which one it is. With the new way of doing things though, it could be just calld 'disc' or 'disc1' or something like that, because it gets named automatically.

How did you get the info you put in your first post?  :D

---

### Post by Herman on 2009-04-19
Of course, you could always boot with a [Super Grub Disk]("http://www.supergrubdisk.org/") if you want to do it an even easier way. :D

---

### Post by Macamba on 2009-04-19
> **Herman said:**
> How did you get the info you put in your first post?  :D

Wow, I impressed an old hand :D.

Actually, the very hard way, as I can not save what I do anyplace. By remembering what I searched for before, researching, and redoing, and finally, regurgitating what I did to you (pant pant). 

Sad to say, now I stumbled upon a ```
Error 15: File not found
```

So let me reiterate what I did (what coffeecat prescribed):
I opened menu: Places -> Computer, double clicked '12.9 G Media', which is the fancy name for my SD8 partition, containing my root.

Next I executed:
```
ubuntu@ubuntu:~$ cd /
ubuntu@ubuntu:/$ ls media
disk  carydisk

```

Now I know SD8 is mounted, as disk ;)

Then I performed
```
gksudo gedit /media/disk/boot/grub/menu.lst
```
and got menu.lst filled in (compared to empty files, pretending to be /media/disk/boot/grub/menu.lst).

Next I made a safety copy of menu.lst (to menu.lst.org), and went back to the original menu.lst, and performed a 'search-n-replace' of (hd0,10) to (hd0,8 ).

And while writing this I notice what I did wrong. I had to replace it with (hd0,7). So now I'm going to change that. When successful I will come by to report that.

Macamba

---

### Post by Macamba on 2009-04-19
8)

It works. Thanks for your help, Herman and coffeecat.

---

### Post by Herman on 2009-04-19
:D Very good, Macamba! You are on the road to success! Well done! 

Regards, Herman :)

---

### Post by coffeecat on 2009-04-19
Excellent. Good luck!

---

