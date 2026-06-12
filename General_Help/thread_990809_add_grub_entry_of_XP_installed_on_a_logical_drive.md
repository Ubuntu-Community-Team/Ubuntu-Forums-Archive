---
title: "add grub entry of XP installed on a logical drive"
date: 2008-11-23
forum: General Help
---

### Post by younus_malik on 2008-11-23
i have four OS installed on my m1530

Vista (first primary)
OS X (second primary)
XP (logical drive)

and my adorable Ubuntu in the last logical drive

what i really want is to run windows XP through Ubuntu's Grub menu. XP works fine when i select Vista from grub menu and then choose xp however i want to go straight to xp if its possible. please help. also is it possible to map my media button to boot with a particular os i want?

thanks

---

### Post by dexter on 2008-11-23
You have to add an entry for XP in /boot/grub/menu.lst. You can open and edit the file using```
sudo gedit /boot/grub/menu.lst
```. You will need to add something like this
```

title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```
(hd0,0) will have to be changed. hd0 stands for the harddrive where xp is installed, the second 0 points to the partition that holds xp.

---

### Post by cdtech on 2008-11-23
To boot to a default OS, just change the default order within the "/boot/grub/menu.lst". It's set to the first OS listed (0).

---

### Post by Nepherte on 2008-11-23
> **cdtech said:**
> To boot to a default OS, just change the default order within the "/boot/grub/menu.lst". It's set to the first OS listed (0).
or change the line
```
default    0
```
to the number of the entry you want to be default
```
default    x
```
Remember that grub starts counting from 0. So if you want the fourth entry, you'd have to replace x with 3 (Though this doesn't really apply to the topic starter's question).

[QUOTE=dexter]You have to add an entry for XP in /boot/grub/menu.lst. You can open and edit the file using[/QUOTE]
For graphical applications, use gksudo instead:
```
**gksudo** gedit /boot/grub/menu.lst
```

---

### Post by younus_malik on 2008-11-23
thanks everyone for your replies.

unfortunately that didn't help. the problem is that windows xp is on extended partition and i believe that some of the info is kept on primary partition.

please see attached image. i did try to add an entry using  (hd0,3) & (hd0,4) but unfortunately both entries didn't work.

please help...

---

### Post by caljohnsmith on 2008-11-23
Because you have XP on a logical partition, that means its boot files must be in one of the primary partitions, which in your case would be Vista's partition. It is possible to boot XP directly from the logical partition if you move your XP boot files into the XP partition, and then modify the boot.ini file to point to the correct partition. If you want some help with that, please post the following:
```
sudo mkdir /mnt/sda1 /mnt/sda5
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sda5 /mnt/sda5
ls -l /mnt/sda1 /mnt/sda5
```
And we can work from there if you want. :)

---

### Post by younus_malik on 2008-11-23
here is the result

---

### Post by caljohnsmith on 2008-11-23
OK, your XP boot files are indeed in your Vista partition. How about doing:
```
sudo mkdir /mnt/sda1 /mnt/sda5
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sda5 /mnt/sda5
sudo mv /mnt/sda1/boot.ini /mnt/sda1/ntldr /mnt/sda1/NTDETECT.COM /mnt/sda5
gksudo gedit /mnt/sda5/boot.ini
```
And then change your boot.ini to use the following partition number:
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)[COLOR="Red"]partition(3)[/COLOR]\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)[COLOR="Red"]partition(3)[/COLOR]\WINDOWS="Microsoft Windows XP" /fastdetect /NoExecute=OptIn
```
So just modify the partition numbers as shown above, but nothing else. Next open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And change your Windows XP entry to be:
```
title Windows XP
root (hd0,4)
chainloader +1
```
Next reboot, and let me know exactly what happens when you try and boot Windows XP from Grub. It is likely you will need to do a few more steps to actually get it fully working, but I need to know first what happens when you boot XP after following the above steps. Also, do you have a Windows Vista or XP Install CD? You might need that for a few commands.

---

### Post by younus_malik on 2008-11-23
error:

"windows could not be started because the following file is missing or corrupt:

<windows root>\system32\ntoskrnl.exe

please reinstall a copy of the above file."

---

### Post by caljohnsmith on 2008-11-23
Let's make sure everything went OK, so please post:
```
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt/sda5
ls -l /mnt/sda5
cat -A /mnt/sda5/boot.ini

```

---

### Post by younus_malik on 2008-11-23
It works!!!!!

wow!!

your post is perfect!...

it was a fault on my end. i am so happy and thank you so much for your help. i think i can run xp in ubuntu using VirtualBox as well. i saw one post somewhere and hopefully i will find it again. 

Thanks again man! :popcorn:

---

### Post by caljohnsmith on 2008-11-23
That's great news, I'm glad it didn't take any extra effort to get it working. Cheers and have fun with all your OSes. :)

---

### Post by younus_malik on 2008-11-23
Just for the sake of future visitors:

Sand Lee has an outstanding tutorial to boot an existing XP from ubuntu.

here is the link:

[http://ubuntuforums.org/showthread.php?t=769883](http://ubuntuforums.org/showthread.php?t=769883)

---

### Post by EnGorDiaz on 2008-11-23
try the link in my sig:)

---

