---
title: "Usb pendrive woes"
date: 2005-03-14
forum: Hardware &amp; Laptops
---

### Post by RadixLecti on 2005-03-14
Hi... I have a problem with my pendrive, well a few, actually.

1. About 50% of the time, what I put on the pendrive, doesn't stay there. I thought this was because I was going from a Linux environment to a windows one, but after installing mepis on the other comp (and having tried Ubuntu and Xandros on that one aswell), the problem persisted. At other times, the files are accessible from the Ubuntu-comp, and completely invisible at the other comp, no matter what OS is running.

2. After moving a folder to the pendrive, I cant remove it. I've tried changing the rights to the folder (right-click -> properties and so on), but they change right back... even when I'm logged on as root. I've finally managed to remove the folder, but it took some doing, and I don't remember exactly what doing it took. Is it supposed to be this way?

3. On the pendrive, there's now a .Trash-folder, which is also unremovable. Inside that folder, there's a new .Trash.. and inside that... ad infinitum.  How many folders within folders does the darn pendrive have a use for? 

[edit]

4. I've tried moving individual files (.mp3's) to the pendrive, and tried to remove them (right-klick, move to garbage). When I do, a kopy of the original shows up. I remove that, same way. ANOTHER copy shows up, which is unremovable unless I login to ubuntu as root. 

[/edit]

I'm running Warty, and my pendrive is a TwinMOS Mobile disk III, Usb 2.0, 128 mb 
(currently at 106 megs of free space, is that due to the infinite amount of .Trash-folders?)

Does anyone have an answer to what's going on?

Thanks.

---

### Post by lorap on 2005-03-14
hi friend!
i'd the same problem with my usb cdrom.
donno if it's good in your case but that's what i've done to solve this difficulty:
create new directory say "/media/pendrive"
after what go to the "/mount/fstab" & add this line:"/dev/sr0  /mount/pendrive udf,vfat.noauto,user,rw,0 0"
but look as your hard drive's line's defined to be more sure(i'm not sure about "udf")
tha's all
hope it'd help you friend.
have a good luck!
pavel

---

### Post by Juergen on 2005-03-14
1. and maybe 2. sound as if you're not correctly umounting the drive.

Be sure to 'umount' or right-click/eject your pendrive before you pull it out - otherwise the files might not be written to it, only to the in-memory buffers.

Maybe even the .Trash problem is a result of this. 
Try to format or even re-partition your usb-stick to get it to a 'clean' starting state and start to use it correctly ;-)

---

### Post by RadixLecti on 2005-03-14
Hi.. 

As far as I know, I have been using the bugger correctly (trying to unmount, but it doesn't want to, saying it's busy)...

How would I go about reformatting a Usb pendrive?

And thanks for the quick input, guys. Much appreciated.

---

### Post by lorap on 2005-03-14
i'll try to find the answer to this question once i get home:-)
i'm at work working in windows :-)
pavel

---

### Post by RadixLecti on 2005-03-14
Thanks, Pavel, but I think I've solved that part... well, I used XP. Reinstalled it on the laptop and removed the .Trash from there. (no priviledges needed). ;)

A general question... are folders portable from linux to windows? Or does one have to move just the files if one wants to move files from linux to win?

---

### Post by alastair on 2005-03-14
If you use a filesystem (e.g. FAT) that both OS's can use, folders are "portable".

If not, you can use an archive like ZIP (man zip/unzip) and transfer a directory structure (and files).

---

### Post by Juergen on 2005-03-15
> As far as I know, I have been using the bugger correctly (trying to unmount, but it doesn't want to, saying it's busy)...You have to umount to be sure the files are really written to your pendrive.

If it says it's busy, try to close all nautilus windows. 
For me famd stops to watch the drive only with all (even the unrelated) windows closed.

---

### Post by RadixLecti on 2005-03-15
[QUOTE=Juergen]You have to umount to be sure the files are really written to your pendrive.

If it says it's busy, try to close all nautilus windows. 
For me famd stops to watch the drive only with all (even the unrelated) windows closed.[/QUOTE]
 Thanks, Juergen, that helped.

---

### Post by lorap on 2005-03-16
hi!
have you solved this problem?
sometimes it does help,but sometimes not.
pavel

---

### Post by RadixLecti on 2005-03-16
[QUOTE=lorap]hi!
have you solved this problem?
sometimes it does help,but sometimes not.
pavel[/QUOTE]
 Hi, pavel. 
Yeah, it seems to work now. The only question left is the suggestion that I reformat my pendrive. How I would go about doing that is a mystery to me. ;)

---

### Post by Juergen on 2005-03-17
Desn't just ```
mkfs -t vfat /dev/sda1
```work?

---

### Post by mirtux on 2005-03-17
[QUOTE=Juergen]You have to umount to be sure the files are really written to your pendrive.

If it says it's busy, try to close all nautilus windows. 
For me famd stops to watch the drive only with all (even the unrelated) windows closed.[/QUOTE]

Sorry but for me the unmount problem remains.... i'm not using gnome so i don't have any gnome-related window opened...

MC

---

### Post by Juergen on 2005-03-17
> Sorry but for me the unmount problem remains.... i'm not using gnome so i don't have any gnome-related window opened...
You can find out what is blocking you by doing a```
/bin/fuser -uvm /media/sda1
```or something like that.
To find out ***why*** it is still looking there would be the next problem... ;)

---

### Post by mirtux on 2005-03-17
Well.... it seems nothing is blocking or using that device. Neither becoming root the problem is resolved!

MC

---

### Post by Juergen on 2005-03-17
I don't understand your last sentence, you can umount it as root? Or not?

Did you try the 'fuser'-stuff as root?

---

### Post by mirtux on 2005-03-17
Ok, sorry. I've managed to have **fuser** running well and i've seen i have **famd** running. How is possible to wipe out it without killing everytime i insert the usb pen?

Thanks,
MC

---

### Post by mirtux on 2005-03-17
Ok... it seems that disabling **famd** is useful not to get again this problem ( i used rcconf). But is** famd** necessary to other programs?

Regards,
MC

---

### Post by Juergen on 2005-03-18
It's the **F**ile **A**lteration **M**onitor **D**emon that notifies your file-browser windows (et al.) that the contents of the dir they are showing has changed.
Without it you have to refresh them manually sometimes to see the actual content.

It seems famd is built with DNotify. If so, it's a known bug or 'by design' as MS would say :) (look at fam's TODO)

If you don't want to disable it, you could try to
- build it without DNotify, it then starts polling. A bit less efficient, I suppose.
- give it a timeout in it's config, and start it via inetd instead of running it permanently

If you get it to work reliably in either of these ways, a small note here would help many people, I think... :)

---

### Post by mirtux on 2005-03-18
Unfortunately now i'm not able to test it. I'll rest without famd.
However many thanks for your help and advice!

Regards,
MC

---

