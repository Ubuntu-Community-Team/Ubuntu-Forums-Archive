---
title: "HELP! 8.04 install partition does not exist"
date: 2008-08-21
forum: General Help
---

### Post by Bandolin on 2008-08-21
I have a P4 standard desktop with Win XP and Ubuntu 7.10. When I boot I get the choice of booting up in Ubuntu or Windows. I wanted to upgrade to 8.04, so I choose the 10 Gb Ubuntu partition that had 7.10 installed on it. Everything seemed to go well. But now when I reboot I get the message:
Error 22: No such partition

I can't get into Linux or Windows! It won't recognize any partition.

I desperately need help. Please tell me there's a solution to this which involves getting my Windows XP back.

---

### Post by Elfy on 2008-08-21
Boot with the livecd and post the result of 

```
sudo fdisk -l
```

---

### Post by Bandolin on 2008-08-21
I get the following. Keep in mind I'm on my laptop so I'm actually retyping everything I see in the terminal window. Sorry about the presentation, the forum took out all my spacing.

ubuntu@ubuntu:~$ sudo fdisk -l
Warning: ignoring extra data in partition table 5

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24421 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7eb87eb8

Device   Boot Start End Blocks Id System
/dev/dsa1 * 2 24321 195350400 5 Extended
/dev/sda5 2 1942 15591051 7 HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 Bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ea47d13

Device Boot Start End Blocks Id System
/dev/dsa1 * 1 7012 56323858+ 7 HPFS/NTFS
/dev/sda2 7013 8228 9767520 83 Linux
/dev/sda3 8229 8352 996030 82 Linux swap /Solaris
/dev/sda4 8353 9729 11060752+ 83 Linux
ubuntu@ubuntu:~$

---

### Post by Bandolin on 2008-08-21
With the Live CD when I go to Places I can see my Win XP drive. Everything seems to be there. So, I didn't lose the data. How can I get the boot to work again?

---

### Post by Elfy on 2008-08-21
Ok then we are going to need to be a bit careful here then;

You will need to check again as you have sda on both drives - and we need to know which is which - you have sda1 for both drives and while I imagine that the second is sdb I want to make sure.

We can check the menu list, but to do so I want to mount it - but need to know what to mount :)

Does the desktop not connect to the net, best thing is to do this from there while connected.

---

### Post by Bandolin on 2008-08-21
I can't get my desktop to connect. I've been spending my time while waiting for replies to connect. I've gone through all the help files but nothing seems to get me onto my wireless connection.

I click network, enter my pass phrase and it just spins and then nothing. I've gone to trouble shooting and it asks to check the hardware by System>Preferences>Hardware Information. But when I do that there is no Hardware Information listed under preferences.

---

### Post by Elfy on 2008-08-21
Run the command again with the livecd booted so you can doublecheck - I'm expecting the 80Gb to show

> Disk /dev/sdb: 80.0 GB, 80026361856 Bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ea47d13

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 7012 56323858+ 7 HPFS/NTFS
/dev/sdb2 7013 8228 9767520 83 Linux
/dev/sdb3 8229 8352 996030 82 Linux swap /Solaris
/dev/sdb4 8353 9729 11060752+ 83 Linux

---

### Post by Bandolin on 2008-08-21
Yes that is exactly what it shows.

Oh, and I've managed to connect to the internet. Yay!

---

### Post by Elfy on 2008-08-21
Ok - do these

```
sudo mkdir /media/disk1
sudo mkdir /media/disk2
```

and then 

```
sudo mount -t ext3 /dev/sdb2 /media/disk1
sudo mount -t ext3 /dev/sdb4 /media/disk2
```

Check that they have mounted ok - run ```
df -h
``` you should see both at the bottom of the list.

Now run ```
ls /media/disk1
ls /media/disk2
```

Which of disk1 or 2 has boot in the ls output.

---

### Post by Bandolin on 2008-08-21
Disk 1.
bin   cdrom  etc   initrd      lib         media  opt   root  srv  tmp  var
boot  dev    home  initrd.img  lost+found  mnt    proc  sbin  sys  usr  vmlinuz

Disk 2
bandolin  lost+found

---

### Post by Elfy on 2008-08-21
Ok - now run this - 

```
gedit /media/disk1/boot/grub/menu.lst
```

It should open your menu list - I know you can't post it and if you were to type it...

Check these specific lines - I will post mine and highlight the bits I need to see for yours - bear in mind that the kernel lines will probably look different - also I don't have windows so I need to know what all of that looks like as well

```
<snip>
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=ccf8f1c4-97d0-4544-a0ee-04088d5d67a9 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
[COLOR="Red"]# groot=(hd0,0)[/COLOR]

<snip>

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
[COLOR="#ff0000"]root		(hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ccf8f1c4-97d0-4544-a0ee-04088d5d67a9 ro quiet vga=771 splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet


```

---

