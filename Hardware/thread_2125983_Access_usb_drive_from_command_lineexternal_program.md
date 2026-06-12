---
title: "Access usb drive from command line/external program without mount everytime"
date: 2013-03-15
forum: Hardware
---

### Post by Cyrebo on 2013-03-15
Hi, 

Each time i plug in my usb drive i have to open it with file manager before i can access it from the terminal or external program. I want to be able to plug and remove and be able to access it from external program or command prompt EVERYTIME. Is there some additional commands you have to put in when mounting/unmounting to enable this feature or are there other ways of doing this?

Thanks.

---

### Post by agillator on 2013-03-15
When you say 'mount', are you referring to physically plugging the drive into the computer or are you referring to using the mount command to let your computer see/access the drive's filesystem? What version of Ubuntu are you using? When you plug the USB drive into the computer do you get a message saying it has been automatically mounted?

---

### Post by Cyrebo on 2013-03-16
I'm using Kubuntu 12.10 and well I saw on some forums they say mount it to a location on the computer to fix the problem. In general i just plug it in and I get options for what i want to do (file manager etc). If i don't use file manager to browse my drive and i go to the command line and say /media/mydrive, it wil say no such file or directory but if i open the drive with file manager and use the same command it accesses it. So is there a way to bypass having to go through the file manager before i can access the drive on the command line or any program. For example, i plug in my usb drive and i want to go to let's say a program that read/writes data to my usb drive, the program won't find the files because I think it hasn't been mounted by file manager to be able to be accessed. I don't want to have to open my usb drive with file manager then go to run my program, just run my program and read/write files.

---

### Post by agillator on 2013-03-16
To Linux, everything is part of one big file system. You may be dealing with different physical items, such as thumb drives, hard drives, cds, etc., but the system accesses them all through one big file system anchored at the root directory (/). So, you plug in a thumb drive and the system recognizes that it has a piece of hardware attached, but the user cannot access it because it is not assigned a place in the file system. This is what mounting does. So, mounting is not a hardware thing, it is a system and software thing. I have never used Kubuntu so cannot speak about it. I use Xubuntu and when I plug in a usb drive, it automatically mounts it also. I am surprised Kubuntu doesn't. Perhaps another Kubuntu user can address that. To your point, if your system does not mount the device then you can and should do so through the mount command. You need to know how the device is known to the system, i.e. what device in the /dev directory. You can probably get this from seeing what device is added when you plug it in. You need to know the type of file system on the device, ext4, ntfs, etc. You need to know where you want the device mounted, i.e. what directory. Let's say the device is /dev/sg1, the filesystem is ext4, and you want to access it at /mnt/usb/, a directory which must already exist. The command, then, would be 'sudo mount -t ext4 /dev/sg1 /mnt/usb'. Now the device is mounted and you can access its contents at /mnt/usb. See the man page for mount for more information. The command 'lsusb' will also help you find out what device you plugged in. You should also learn about the fstab (/etc/fstab) file and its uses. Having said all this, if you plug it in and get options, could one of the options be to mount it?

---

### Post by Cyrebo on 2013-03-16
My usb uses a fat32 fiile system. When i plug in my device I get a pop up at the bottom right of the screen with option to open with file manager which is standard usage. From what you've explained it looks like you need to mount the usb device everytime before you can access it. Does this mean that using file manager to open the device bypasses this so you don't have to mount and umount, you can just click open with file manager and that automatically "opens" the drive for accessing then eject when you're done. If it is then I understand why I need to open the usb with file manager first before accessing it for read/write.

---

### Post by sudodus on 2013-03-16
> **Cyrebo said:**
> My usb uses a fat32 fiile system. When i plug in my device I get a pop up at the bottom right of the screen with option to open with file manager which is standard usage. From what you've explained it looks like you need to mount the usb device everytime before you can access it. Does this mean that using file manager to open the device bypasses this so you don't have to mount and umount, you can just click open with file manager and that automatically "opens" the drive for accessing then eject when you're done. If it is then I understand why I need to open the usb with file manager first before accessing it for read/write.

Well, it mounts and opens the partition. This is often the most convenient way to do it, and in some other flavours of Ubuntu this is done automatically (even if you don't open it with the file manager). You can change the ***label*** of the usb fat32 partition to make it easier to identify. For example, use gparted to do it, or in a terminal window, you can do set the label with gparted. Install gparted with
```
sudo apt-get install gparted
``` Most operations with gparted are risky, and you should backup your system before doing it, but 'only' changing the label is simple and safe.

---

### Post by Cyrebo on 2013-03-16
> **sudodus said:**
> Well, it mounts and opens the partition. This is often the most convenient way to do it, and in some other flavours of Ubuntu this is done automatically (even if you don't open it with the file manager). You can change the ***label*** of the usb fat32 partition to make it easier to identify. For example, use gparted to do it, or in a terminal window, you can do set the label with gparted. Install gparted with
```
sudo apt-get install gparted
``` Most operations with gparted are risky, and you should backup your system before doing it, but 'only' changing the label is simple and safe.

I don't understand what you mean by changing the "label", does this change the label on the device or the partition on linux. What if i was to plug another device where this label is located, what happens then?

---

### Post by sudodus on 2013-03-16
> **Cyrebo said:**
> I don't understand what you mean by changing the "label", does this change the label on the device or the partition on linux. What if i was to plug another device where this label is located, what happens then?

It changes the label of the partition (in this case with the FAT32 file system). This belongs to the USB drive, and will be seen by linux as well as Windows (and probably MacOS), whereever you plug in this USB drive.

The label will be used when mounting. Now the label might be 3454-47B3 and the FAT32 partition will be mounted at /media/3454-47B3. If you change the label to USBDATA-1, it will mount at /media/USBDATA-1, which helps you identify it in the file browser and with terminal window commands too.

---

### Post by schragge on 2013-03-16
There are ways to make removable drives automatically mounted on plug-in, but they are non-trivial and involve fiddling with either [udev]("http://manpages.ubuntu.com/manpages/precise/en/man7/udev.7.html") rules or [/etc/fstab]("http://manpages.ubuntu.com/manpages/precise/en/man5/fstab.5.html") or both. If you're looking for a simple way to mount your USB drive from command-line then you can try to manually invoke [udisks]("http://manpages.ubuntu.com/manpages/precise/en/man1/udisks.1.html") (this is what the file manager does for you when you're clicking on the drive icon). Do it like this: ```
udisks --mount /dev/[COLOR=blue]sdb1[/COLOR]
``` Obviously, you will need to replace [COLOR=blue]sdb1[/COLOR] with device name of your drive. If you don't know the device name, but know the label, change the command above to ```
udisks --mount `blkid -L [COLOR=blue]label[/COLOR]`
``` You can display all devices and their labels with ```
sudo blkid -o list -c /dev/null
``` 
Alternatively to using *udisks*, you can install and use [pmount]("http://manpages.ubuntu.com/manpages/precise/en/man1/pmount.1.html"). It gets invoked like this:
```
pmount /dev/[COLOR=blue]sdb1[/COLOR]
``` or ```
pmount `blkid -L [COLOR=blue]label[/COLOR]`
```When you're done with the drive, unmount it with
```
eject [COLOR=blue]label[/COLOR]
``` or ```
eject [COLOR=blue]sdb1[/COLOR]
```

---

### Post by Cyrebo on 2013-03-16
> **schragge said:**
> There are ways to make removable drives automatically mounted on plug-in, but they are non-trivial and involve fiddling with either [udev]("http://manpages.ubuntu.com/manpages/precise/en/man7/udev.7.html") rules or [/etc/fstab]("http://manpages.ubuntu.com/manpages/precise/en/man5/fstab.5.html") or both. If you're looking for a simple way to mount your USB drive from command-line then you can try to manually invoke [udisks]("http://manpages.ubuntu.com/manpages/precise/en/man1/udisks.1.html") (this is what the file manager does for you when you're clicking on the drive icon). Do it like this: ```
udisks --mount /dev/[COLOR=blue]sdb1[/COLOR]
``` Obviously, you will need to replace [COLOR=blue]sdb1[/COLOR] with device name of your drive. If you don't know the device name, but know the label, change the command above to ```
udisks --mount `blkid -L [COLOR=blue]label[/COLOR]`
``` You can display all devices and their labels with ```
sudo blkid -o list -c /dev/null
``` 
Alternatively to using *udisks*, you can install and use [pmount]("http://manpages.ubuntu.com/manpages/precise/en/man1/pmount.1.html"). It gets invoked like this:
```
pmount /dev/[COLOR=blue]sdb1[/COLOR]
``` or ```
pmount `blkid -L [COLOR=blue]label[/COLOR]`
```When you're done with the drive, unmount it with
```
eject [COLOR=blue]label[/COLOR]
``` or ```
eject [COLOR=blue]sdb1[/COLOR]
```

Thanks for the suggestion but when i eject and plug in again, i still have to mount it. I want to just plug it in and have it be accessible by any program. The udisks commands worked and I was able to access the device without going into file manager but I want to be able to do that after i eject and plug it in again.

---

### Post by Cyrebo on 2013-03-16
> **sudodus said:**
> It changes the label of the partition (in this case with the FAT32 file system). This belongs to the USB drive, and will be seen by linux as well as Windows (and probably MacOS), whereever you plug in this USB drive.

The label will be used when mounting. Now the label might be 3454-47B3 and the FAT32 partition will be mounted at /media/3454-47B3. If you change the label to USBDATA-1, it will mount at /media/USBDATA-1, which helps you identify it in the file browser and with terminal window commands too.

I don't know if i wanna mess around with device identity and things yet because I can't really risk the data on the device as I don't have a back up or means to back right now. Thanks for the suggestion though.

---

### Post by sudodus on 2013-03-16
> **Cyrebo said:**
> I don't know if i wanna mess around with device identity and things yet because I can't really risk the data on the device as I don't have a back up or means to back right now. Thanks for the suggestion though.

You are welcome :-)

Of course, take the steps forward at a pace, that is right for you. And it is a good idea to get a good backup system and routine before messing around with the system.

---

### Post by agillator on 2013-03-16
In answer to one of your questions and to perhaps clear up some confusion, any time you plug in a removable device it must be mounted, period. When you remove it, it is unmounted. Actually you should unmount it first, then remove it to prevent file system corruption. Once you plug the device in and then mount it, it will stay mounted until you unmount and unplug it. Mounting is a temporary thing and only lasts while the device is plugged in and available to the system. You have been given a number of options to actually do the mounting, including the most basic: using the mount command. So do not confuse yourself. Plug it in and mount it. Once it is mounted, access will be allowed to users/programs according to permissions. That is a different subject but one you probably need to check.

---

