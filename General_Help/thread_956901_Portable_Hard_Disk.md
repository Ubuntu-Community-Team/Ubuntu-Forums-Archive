---
title: "Portable Hard Disk"
date: 2008-10-23
forum: General Help
---

### Post by andyturner87 on 2008-10-23
Hi, 
  I'm really new to linux and I'm having some trouble. So far its been fine, but I have this netac k200 120gb usb hard drive thing that when I connect it just starts beeping.  
  So I look at the instructions and it says for linux users go into the root and enter "mount /dev/sda /mnt".  I do this and it says its already mounted or busy.  
  I'v tried a searching online for an answer but cant seem to find what I'm looking for but I am sorry if the question has been asked before and I'v missed it.

Cheers,

Andy.

---

### Post by GuitarRocker2562 on 2008-10-23
It should automatically mount for you.

---

### Post by andyturner87 on 2008-10-23
Indeed...

---

### Post by andyturner87 on 2008-10-23
is it a problem with my usb driver?

---

### Post by david_lynch on 2008-10-23
> **andyturner87 said:**
> Hi, 
  I'm really new to linux and I'm having some trouble. So far its been fine, but I have this netac k200 120gb usb hard drive thing that when I connect it just starts beeping.  
  So I look at the instructions and it says for linux users go into the root and enter "mount /dev/sda /mnt".  I do this and it says its already mounted or busy.  
  I'v tried a searching online for an answer but cant seem to find what I'm looking for but I am sorry if the question has been asked before and I'v missed it.

Cheers,

Andy.
You didn't say what version of linux you're using, if you can provide that info it would be helpful. In any case, the instructions for linux users are lame and out of date. It should be mounted when you plug it in. Are you in a GUI environment when plugging it in? If so, the icon for the device should appear on the desktop. If that's not the case, then some helpful information can most likely be found in /var/log/messages or the output of dmesg.

---

### Post by Crossyboi on 2008-10-23
> **andyturner87 said:**
> Hi, 
  I'm really new to linux and I'm having some trouble. So far its been fine, but I have this netac k200 120gb usb hard drive thing that when I connect it just starts beeping.  
  So I look at the instructions and it says for linux users go into the root and enter "mount /dev/sda /mnt".  I do this and it says its already mounted or busy.  
  I'v tried a searching online for an answer but cant seem to find what I'm looking for but I am sorry if the question has been asked before and I'v missed it.

Cheers,

Andy.



Could you confirm whether its your computer beeping or the actual external drive, have you ever used the drive before (This way you can confirm it does work) and also, what OS did you use it on before?

It does sound like its struggling to read the files but post back :)

---

### Post by Crossyboi on 2008-10-23
> **GuitarRocker2562 said:**
> It should automatically mount for you.

Well obviously it hasn't :p

---

### Post by cyfur01 on 2008-10-23
First, I don't how to explain the beeping. If you still have the system beep enabled, you can always try disabling it by:```
sudo modprobe -r pcspkr
```
Note that **this is not a fix for the problem**, merely a weak attempt at a baind-aid to shut-up the beeping. A more proper thing to do would be to sift through /var/log/syslog* after plugging the drive in to see if it has reported some sort of error.

As for the other comment about the manual mount command, I assume your computer has at least one IDE/SATA hard drive, so your USB drive may not be /dev/sda. If you computer isn't having a critical issue, you can probably check this using **gparted**. If you have it installed, it will be under System->Administration->Partition Editor (top left of the screen), otherwise you can install it using synaptic. gparted should list all the devices on your system and let you figure out which one is your 120GB drive. Also note that you will have to use **sudo** for mounting your drive:
```
sudo mount ...
```

Sorry for the lack of an actual solution, but hopefully this will at least start you in the right direction...

---

### Post by salvador_luna on 2008-10-23
Hi.

I think I'm having the same problem when i plug my external HD (well, actually it was from a laptop that "died", and i bought a hd case to make it a usb drive).

When i plug the drive, the hd starts beeping (i'm completly sure that is the hd) and the led starts blinking really fast betwen green and red.

I think it is important to say that the hd get mounted (when i'm in luck) and then it disapears, the same time the led starts blinking with the beeping of the drive.

Any thoughts?

PD: Sorry form my english.

EDIT: Most time the HD doesn't get mounted, and this behavior occurs when i plug it in my laptop (Ubuntu 8.04.1 up to date and every thing running fine). When i plug it in my Desktop PC, almost always it works right. I tried to reproduce this in a Windows box, and the HD works fine every time, so i think that the problem is not from the drive.

---

### Post by Crossyboi on 2008-10-24
> **salvador_luna said:**
> Hi.

I think I'm having the same problem when i plug my external HD (well, actually it was from a laptop that "died", and i bought a hd case to make it a usb drive).

When i plug the drive, the hd starts beeping (i'm completly sure that is the hd) and the led starts blinking really fast betwen green and red.

I think it is important to say that the hd get mounted (when i'm in luck) and then it disapears, the same time the led starts blinking with the beeping of the drive.

Any thoughts?

PD: Sorry form my english.

EDIT: Most time the HD doesn't get mounted, and this behavior occurs when i plug it in my laptop (Ubuntu 8.04.1 up to date and every thing running fine). When i plug it in my Desktop PC, almost always it works right. I tried to reproduce this in a Windows box, and the HD works fine every time, so i think that the problem is not from the drive.

Your english is fine :P

In which case, it sounds like ubuntu is missing a driver! Only thing i can suggest is googling for a driver for the model of your external disk, also make sure its compatible with ubuntu, Some drives arent compatible!

---

### Post by salvador_luna on 2008-10-24
Ok, I'll check for a driver and, if i find something usefull i'll write again.

Thanks

---

### Post by Crossyboi on 2008-10-24
> **salvador_luna said:**
> Ok, I'll check for a driver and, if i find something usefull i'll write again.

Thanks

Ok then :)

Also look up whether the drive is compatible with ubuntu!

---

### Post by salvador_luna on 2008-10-28
Well, I didn't find anything. As I said, the hard drive works fine in a PC with Ubuntu, but not in my laptop.

Help please :)

---

