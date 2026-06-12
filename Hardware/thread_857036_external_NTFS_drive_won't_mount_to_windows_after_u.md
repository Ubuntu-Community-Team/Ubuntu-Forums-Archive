---
title: "external NTFS drive won't mount to windows after ubuntu"
date: 2008-07-12
forum: Hardware
---

### Post by zero777zero on 2008-07-12
I'm dual booting hardy heron and vista. i've used my seagate NTFS external hard drive for several months on Vista. after using it for about a week on ubuntu it will no longer work with vista, vista wants to "format" it. i unmount whenever i shut it off and it still works fine with ubuntu. now how do i get it to work with vista without reformatting?

---

### Post by PmDematagoda on 2008-07-12
Try and run ntfsfix on the drive by installing ntfsprogs with:-
```
sudo apt-get install ntfsprogs
```
and then:-
```
sudo ntfsfix /location/of/drive
```
then see if the drive now works properly.

---

### Post by matt$2 on 2008-07-12
Your description is very hard to follow.
An NTFS drive doesn't 'MOUNT TO WINDOWS'.

You used your seagate NTFS external hard drive on vista, or 
you used vista on your seagate NTFS external hard drive?

it still works fine with ubuntu, but how do you get it to work with vista without reformatting???  Is that without vista reformatting the instance of ubuntu, or the other way around??

Clear concise meaningful text would help alot.

I have some ideas, but they may have nothing to do with what you're trying to ask about.

---

### Post by Daelyn on 2008-07-12
> **zero777zero said:**
> I'm dual booting hardy heron and vista. i've used my seagate NTFS external hard drive for several months on Vista. after using it for about a week on ubuntu it will no longer work with vista, vista wants to "format" it. i unmount whenever i shut it off and it still works fine with ubuntu. now how do i get it to work with vista without reformatting?

Apart from the great tip of running the ntfsfix program from ubuntu;
~ What happens if you try running a check disk on it in vista? 
~ If you go in to Control panel / admin tools / computer management / disk manager. Is it listed in there as a recognized partition etc?

---

### Post by Daelyn on 2008-07-12
> **matt$2 said:**
> Your description is very hard to follow.
An NTFS drive doesn't 'MOUNT TO WINDOWS'.

You used your seagate NTFS external hard drive on vista, or 
you used vista on your seagate NTFS external hard drive?

it still works fine with ubuntu, but how do you get it to work with vista without reformatting???  Is that without vista reformatting the instance of ubuntu, or the other way around??

Clear concise meaningful text would help alot.

I have some ideas, but they may have nothing to do with what you're trying to ask about.

I saw no problem understanding what he wrote. And, I can't see him using Vista on a external HDD very easily. I'm sure this ain't the case :P

---

### Post by matt$2 on 2008-07-12
I saw no problem understanding what he wrote. And, I can't see him using Vista on a external HDD very easily. I'm sure this ain't the case :P


Good you can speak cryptic.  I can't

---

### Post by PmDematagoda on 2008-07-12
This is meant to be a support thread, so let's try and keep it that way without commenting about the style in which people post.

---

### Post by zero777zero on 2008-07-12
thanks for the responses, no my external drive DOES NOT have an OS on it nor is it partitioned in anyway.

PmDematagoda, if i run that code will it have any risk of losing data on my hard drives?

and just in case i wasnt clear, the NTFS drive reads/writes fine in ubuntu, but once i unmounth and go back to Vista, it will not work with vista.

---

### Post by matt$2 on 2008-07-13
ok Now I get it.  The ntfs partition on the external hard drive can't be mounted by Windows after having been mounted and unmounted by ubuntu.

Now I'm at a disadvantage by not having used these ntf3g tools at all yet.  I doubt hugely if you'll damage or lose data, but I haven't tried it.

How about saving the content of the partition not only to be safe but to then format your ntfs partition to fat32.  Then return it to the newly formatted fat32 partition.  Then definitely no problems.

I suspect your going to tell me it's a 500 Gig hard drive or partition size and it's too big to do.  it is a way around it though.

---

### Post by PmDematagoda on 2008-07-13
> **zero777zero said:**
> PmDematagoda, if i run that code will it have any risk of losing data on my hard drives?


There shouldn't be any risk of that.

---

### Post by zero777zero on 2008-07-14
> **PmDematagoda said:**
> Try and run ntfsfix on the drive by installing ntfsprogs with:-
```
sudo apt-get install ntfsprogs
```
and then:-
```
sudo ntfsfix /location/of/drive
```
then see if the drive now works properly.

one more question, the name of my hard drive would be "931NTFS", so the second line of code would be "sudo ntfsfix /931NTFS"?

---

### Post by PmDematagoda on 2008-07-14
> **zero777zero said:**
> one more question, the name of my hard drive would be "931NTFS", so the second line of code would be "sudo ntfsfix /931NTFS"?

No, that is your drive's label, not your drive's device location in /dev which can be obtained with:-
```
sudo fdisk -l
```

---

### Post by zero777zero on 2008-08-01
Disk /dev/sdc: 750.1 GB, 750156374016 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       91201   732572001    7  HPFS/NTFS

^apparently "/dev/sdc" or "/dev/sdc1" is what i want, so i tried the following. neither result looks optimistic

BOX:~$ sudo ntfsfix /dev/sdc1
Refusing to operate on read-write mounted device /dev/sdc1.
BOX:~$ 

legato777@legatoBOX:~$ sudo ntfsfix /dev/sdc
Mounting volume... Error opening partition device: Device or resource busy.
Failed to startup volume: Device or resource busy.
FAILED
Attempting to correct errors... Error opening partition device: Device or resource busy.
FAILED
Failed to startup volume: Device or resource busy.
Volume is corrupt. You should run chkdsk.
legato777@legatoBOX:~$

---

### Post by fogster74 on 2008-08-22
Hi there,

I have a similar problem and have started a separate thread - it's here: [http://ubuntuforums.org/showthread.php?p=5645488](http://ubuntuforums.org/showthread.php?p=5645488)

Someone has suggested a possible fix - I'll try it over the next couple of days and report back on how I get on. My issue may have been caused by hibernating Windows and then booting into Ubuntu (doh!).

Steve

---

### Post by Mazin on 2008-08-22
> **zero777zero said:**
> 
BOX:~$ sudo ntfsfix /dev/sdc1
Refusing to operate on read-write mounted device /dev/sdc1.
BOX:~$ 

legato777@legatoBOX:~$ sudo ntfsfix /dev/sdc
Mounting volume... Error opening partition device: Device or resource busy.
Failed to startup volume: Device or resource busy.
FAILED
Attempting to correct errors... Error opening partition device: Device or resource busy.
FAILED
Failed to startup volume: Device or resource busy.
Volume is corrupt. You should run chkdsk.
legato777@legatoBOX:~$

You can't run ntfsfix on a hard drive that you're currently using.  Right-click on the hard drive's icon and Unmount it first.  Then run "sudo ntfsfix /dev/sdc1".  What ntfsfix does is mark the hard drive to tell Windows that it should be checked at boot.

---

### Post by marcelo_gomes on 2008-08-26
I had the same problem with ntfsfix.
I've worked it out as said Mazin said, only doing it via terminal, since Dolphin couldn't unmount the device

sudo umount /dev/sda1

just change sda1 to your device name and that will probably be it.

---

