---
title: "Ubuntu fails to mount fat32 partitions"
date: 2006-07-08
forum: Hardware &amp; Laptops
---

### Post by andburg on 2006-07-08
Hi guys, new user here, got 2 drives, a 160gb drive with a 20gb linux partition, and 140gb for file storage in windows, and a 40gb windows system drive. ubuntu give these errors

windows system drive:
error: device /dev/hda1 is not removable

error: could not execute pmount

windows file storage drive:
error: device /dev/hdb1 is not removable

error: could not execute pmount

now im not particularly bothered about the windows system drive but i want to be able to access the files on the file storage drive.

Any help would be much appreciated, i have searched and found a manual mount procedure but got the same fault doing it manually

andy

---

### Post by parkash on 2006-07-08
Could you post what have you done "manually"? I mean, in a console?
Also, what version of ubuntu are you using?

Finally, you could give me the output of "$cat /proc/partitions"

---

### Post by andburg on 2006-07-08
i did it a week or so ago so dont know exactly what i did but it was done in a console, im a complete linux newb, 

all i get when typing in $cat /proc/partitions is permission denied, 

im running ubunto 6.0.6

the account im using has full priveledges aswell

---

### Post by parkash on 2006-07-08
Try $sudo cat /proc/partitions

As an advice, you should try to do the most you can on a terminal/console... So you learn a little more about linux.

---

### Post by pepejeria on 2006-07-08
I have the same issue, I cant access the windows drive

cat /proc/partitions results in this:

major minor  #blocks  name

   3    64  156290904 hdb
   3    65          1 hdb1
   3    66   29439081 hdb2
   3    69  125570560 hdb5
   3    70    1277104 hdb6
   8     0  160836480 sda
   8     1  160834716 sda1
 253     0   29439081 dm-0
 253     1  125570560 dm-1
 253     2    1277104 dm-2
 253     3  160834716 dm-3

sda is the windows disk

---

### Post by parkash on 2006-07-08
What happens when you do this?

$sudo mkdir /windows; sudo mount /dev/sda1 /windows -o umask=0000

---

### Post by Neobuntu on 2006-07-08
I've noticed that Ubuntu (by default) doesn't pop up a pre-setup icon for Windows partitions. 

(I'm a fan of currently running a dual boot with Windows/Ubuntu so that one can compare exact same hardware and spend ZERO more dollars on Windows. This way NO DATA of your MS Windows is abandoned and I think that gets more eyes on Ubuntu which is overall better.)

Also, USB Flash drives (universally FAT format) DO AUTOMATICALLY pop up and just work with click and drag just by inserting them.

Remember, a novice could delete things (on a Windows partition) and then blame Ubuntu.

Yet, if you are carefull, all you need to do is press the ATL and F2 key together and then run the file manager as super user:

gksudo nautilus 

(you will need to know your admin/user password)
(This will now be in the drop down list for the Alt-F2 "Run Application" for your future convenience.)

Then you may notice your Windows partition is accessable under the main /tmp folder. My Dapper (Ubuntu 6.06) auto set-up one is "/tmp/disks-conf-hda1". If it's locked out (as it should be) the you are not running as user, and tring to acess "System" files.

Of course, you can make up a folder called /windows under say, /mnt or /media (as sudo admin) if you wish. Then simply run the "Disks" utility (click partitions) off the menu, to change it. Keep things simple unless you have very special needs.

---

### Post by parkash on 2006-07-08
Indeed there's no popup or wizard or anything like that...  Nevertheless through the Dapper installation you can configure your windows partitions to be mounted at boot time...  And there's always the option of manually configuring "/etc/fstab" to get the partitions mounted at boot time with restrictive permissions when you need to.

--Edit > I'd rather use text mode for my configuration ;) There are little graphical tools that I prefer i.e. Synaptic.

---

### Post by andburg on 2006-07-08
sorry guys was away, result of $sudo cat /proc/partitions

major minor  #blocks  name

   3     0   40146624 hda
   3     1   40143568 hda1
   3    64  156290904 hdb
   3    65  138576658 hdb1
   3    66   16956607 hdb2
   3    67          1 hdb3
   3    69     755023 hdb5
 253     0   40143568 dm-0
 253     1  138576658 dm-1
 253     2   16956607 dm-2
 253     3     755023 dm-3


hth

---

### Post by andburg on 2006-07-08
fixed it!!!!

created directories as /windows and /files, then set the mount location as them in disk manager!!!

woohoo

---

### Post by andburg on 2006-07-08
right so now i can 1 time mount the drives, but i dont have write access and they dont appear on reboot, how can i do this?

---

### Post by parkash on 2006-07-09
For that you must edit your 

/etc/fstab

file.

That part is not very friendly as you should edit it correctly or else your box won't boot anymore.

There is a great handbook out there... Maybe it helps:

[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=8](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=8)

:)

---

### Post by andburg on 2006-07-09
> **parkash said:**
> For that you must edit your 

/etc/fstab

file.

That part is not very friendly as you should edit it correctly or else your box won't boot anymore.

There is a great handbook out there... Maybe it helps:

[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=8](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=8)

:)

shows me how to understand it but not how to edit it???

anyone tll me how i can do this?

---

### Post by parkash on 2006-07-09
It's guidelines so you'll know what to put into the file...

How to edit it.. is simple:

```

$sudo nano -w /etc/fstab

```

---

### Post by Neobuntu on 2006-07-18
OK look, for the advanced geek with time on your hands then go for it. It's your system.

The question is why are we doing this? 

So you want to access your Windows partition and you want to do it with user permissions? Are you sure? Fine if you are but hold on.

Why are we accessing the Windows (NTFS for example) partition? Usually, one wants access to there old files (Docs, presentations etc..)

What you need to know with the NTFS Window (XP default) file system is that Ubuntu has no problem reading it and MAY not have a problem writing to it, depending on Microsoft's whim.

So back up and ask your self how many ways there are to skin a cat? 

First if you take files from XP (NTFS) and not back again, then there's no problem. Why not just run your file manager of choice as sudo? This way, one just finds the Windows partition (in Dapper) and grabs what you want. I think it's in the /tmp directory.


Yet, it comes down to this. If you just want to grab files from XP/NTFS (old fat32 and/or Win98 works fine both ways) then maybe there's a faster solution than even changing Ubuntu settings.

One could network seperate computers but that's WAY more settings. 

Second, one could configure Ubuntu as were saying to "see" the NTFS partition. 

Third (given you may want to stay away from writing to a NTFS partition,) perhaps it is easiest (faster) to use a USB Flash Drive or external USB hardrive?

These portable storage solutions are formated with FAT or FAT32 so they may be read and written to, by PC's, Mac's and Ubuntu with click and drag ease. The time it takes to copy to, and then move over, is FAR less than messing with any settings.

So unless you are trying an advanced and tricky method of running select Windows programs; IN PLACE via WINE (still not as good as native) then just be aware and keep it short and simple (KISS).

If you are a geek with time on your hands then disreguard my opionion altogether :)

---

