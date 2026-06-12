---
title: "ubuntu terminal command to lock and unlock harddrive?"
date: 2007-06-07
forum: Hardware &amp; Laptops
---

### Post by beanman25 on 2007-06-07
Im pretty new to this, but understand most of the terminal. does anyone know this command?

---

### Post by 444 on 2007-06-07
hdparm --security-help

Says it's expermental and dangerous though...

---

### Post by beanman25 on 2007-06-07
is there anyway to unlock a specific one?

---

### Post by Pixtu on 2007-06-07
Are you talking in general, or do you have a specific problem?

---

### Post by beanman25 on 2007-06-07
I need to unlock it for more space. I added it, but cant access it cause its locked. its the e drive

---

### Post by jfinkels on 2007-06-07
> **beanman25 said:**
> I need to unlock it for more space. I added it, but cant access it cause its locked. its the e drive

What do you mean "added it" and "cant access it"? Do you mean that you mounted it and can't access it?

---

### Post by beanman25 on 2007-06-07
it put it in as the primary slave, but everytime i try to access it, it says it is locked.

---

### Post by jfinkels on 2007-06-07
> **beanman25 said:**
> it put it in as the primary slave, but everytime i try to access it, it says it is locked.

When you say 'access', do you mean mount? What is the output of this command:
```
sudo fdisk -l
```

---

### Post by beanman25 on 2007-06-07
Disk /dev/hda: 10.2 GB, 10204766208 bytes
255 heads, 63 sectors/track, 1240 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1182     9494383+  83  Linux
/dev/hda2            1183        1240      465885    5  Extended
/dev/hda5            1183        1240      465853+  82  Linux swap / Solaris

Disk /dev/hdd: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        2434    19551073+  83  Linux
steve@steve-desktop:~$ 


I think its mounted, but truthfully im not 100% sure

---

### Post by jfinkels on 2007-06-07
> **beanman25 said:**
> Disk /dev/hda: 10.2 GB, 10204766208 bytes
255 heads, 63 sectors/track, 1240 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1182     9494383+  83  Linux
/dev/hda2            1183        1240      465885    5  Extended
/dev/hda5            1183        1240      465853+  82  Linux swap / Solaris

Disk /dev/hdd: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        2434    19551073+  83  Linux
steve@steve-desktop:~$ 


I think its mounted, but truthfully im not 100% sure

To mount a hard drive, first make a "mountpoint" which is the directory where you want the files to be placed.
```
sudo mkdir /media/mydrive
```

Now type the following to mount it:```
sudo mount /dev/hdd1 /media/mydrive
```

Now you can browse the files there in nautilus (the file manager) if you want:```
nautilus /media/mydrive
```

If you want to unmount the drive, type the following: ```
sudo umount /media/mydrive
```

---

### Post by beanman25 on 2007-06-07
so where it says mydrive i would put e: or :e and keep the hdd 1 stuff the same? sorry for the large amount of questions. you guys have been a great help.

---

### Post by jfinkels on 2007-06-07
> **beanman25 said:**
> so where it says mydrive i would put e: or :e and keep the hdd 1 stuff the same? sorry for the large amount of questions. you guys have been a great help.

You're going to have to drop your notions of "drive letters". In the Linux world, every part of the computer system is contained in one large directory hierarchy. Looks like this:```

/
--/bin
--/boot
--/dev
--/home

```
etc. etc.

Your physical drives are all under the directory "/dev". In your case, the drive you want to access is at "/dev/hdd" and the partition is called '1', so the partition is located at "/dev/hdd1".

You can type all the commands exactly as I've given them. However, this partition may already be mounted! I don't know. Can you post the output of this command:```
ls /media
```

---

### Post by Pixtu on 2007-06-07
Seems like your thinking in Windows terms.

Yes, you can use your own 'name' for mydrive but not normally just a letter such as 'e'. Also you could get into trouble with the colon ':'. Use 'mydrive' or 'mydata'.

---

### Post by beanman25 on 2007-06-07
steve@steve-desktop:~$ ls /media
cdrom  cdrom0  disk

i think cdrom0 is the one i need to unlock.

---

### Post by jfinkels on 2007-06-07
> **beanman25 said:**
> steve@steve-desktop:~$ ls /media
cdrom  cdrom0  disk

i think cdrom0 is the one i need to unlock.

I'm afraid "unlock" doesn't mean anything to me, sorry. Why don't you tell me specifically what you want to do.

But I believe the hard drive (your "E:" drive in Windows, or here "/dev/hdd1") is already mounted...take a look in /media/disk. You can browse it using the graphical file manager, nautilus, by typing the following:```
nautilus /media/disk
```

---

### Post by beanman25 on 2007-06-07
its  letting me view it, but i cant save any data on it.  it always is blocked.

---

### Post by beanman25 on 2007-06-07
id rather not waste another topic space for this question, I have a dell digital jukebox 20gb mp3 player. would i have to do anything specific to get ubuntu to recognize it?

---

### Post by jfinkels on 2007-06-07
> **beanman25 said:**
> id rather not waste another topic space for this question, I have a dell digital jukebox 20gb mp3 player. would i have to do anything specific to get ubuntu to recognize it?

OOOhhhh, you're talking about an mp3 player....now that's a horse of a different color.

You should definitely make a new thread, title it clearly, and describe your problem in detail.

---

### Post by beanman25 on 2007-06-07
this is for a harddrive, should i make a new topic about the mp3 player? This topic is about a harddrive.

---

### Post by jfinkels on 2007-06-07
> **beanman25 said:**
> this is for a harddrive, should i make a new topic about the mp3 player? This topic is about a harddrive.

Oh. Yes. And make sure to be VERY clear about your problem and your hardware (that includes following the rules of syntax and style for the English language!).

---

### Post by jfinkels on 2007-06-07
Can you post the output of this command:```
ls -l /media
```

---

### Post by beanman25 on 2007-06-07
steve@steve-desktop:~$ ls -l /media
total 8
lrwxrwxrwx 1 root root    6 2007-06-04 14:49 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-06-04 14:49 cdrom0
drwxr-xr-x 3 root root 4096 2007-06-05 18:56 disk

---

### Post by 444 on 2007-06-07
I'm guessing something got mounted as root and has that root-only-access 'lock' icon on it... ? For linux-formatted drives you run the chown/chmod command to let anybody access.
Like:
sudo mount /dev/hdd1 /media/disk
sudo chmod a+rwx /media/disk
Will let anybody read and write the disk.

---

### Post by beanman25 on 2007-06-07
steve@steve-desktop:~$ sudo mount /dev/hdd1 /media/disk
Password:
mount: /dev/hdd1 already mounted or /media/disk busy
mount: according to mtab, /dev/hdd1 is already mounted on /media/disk
steve@steve-desktop:~$ sudo chmod a+rwx /media/disk


the second one does nothing.

---

### Post by 444 on 2007-06-08
Well after running the second one run 'nautilus /media/disk' and you should be able to do stuff like create new folders.

---

### Post by dfreer on 2007-06-10
Also... Is this an NTFS formatted drive you are trying to reach? the more information you can give us the better we can help you.

---

