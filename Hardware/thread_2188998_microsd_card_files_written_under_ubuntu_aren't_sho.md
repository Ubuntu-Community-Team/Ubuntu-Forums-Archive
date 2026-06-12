---
title: "microsd card files written under ubuntu aren't showed in windows"
date: 2013-11-20
forum: Hardware
---

### Post by jfca283 on 2013-11-20
Hi
My issue is i copy/move files from ubuntu to my microsd card. It seems fine because once done the operation i can play a mp3 file written in the card. But after ejecting the card, if i try to read it under windows, i only see folder that were created but no mp3 files. It's really strange. It's the filesystem in the card? is it ubuntu or windows the origin of the problem?
Thanks in advanced for your time and interest.

---

### Post by Bucky Ball on 2013-11-20
What are the partitions on the card formatted as? If they are EXT* Windows won't see them.

You need NTFS or FAT if you want to share.

---

### Post by jfca283 on 2013-11-20
exFAT is the system file. Windows can see the card and shows some files. But no all of them. That's what bothers me. At my house i will try read the others files under ubuntu. If ubuntu can, then it's a windows issue.

---

### Post by jfca283 on 2013-11-21
I moved some files using ubuntu to the sd card. I even unplugged it and plugged it again to see if the files were transferred. Nemo showed them.  I play one song from the sd card. So, i ejected the card. Now, under windows at my work, i only can see some files. Others are not displayed. The size available of the card indicates the capacity was reduced effectively. Is there an incompatibility between ubuntu and windows when you use a sd card? I will try using the NTFS format with the card at my house and at my work. It's really annoying the issue.

---

### Post by Bucky Ball on 2013-11-21
Ah, ha! I now remember having a problem with this on my wife's computer some time ago. It came down to how the files were named. There is a naming syntax that Ubuntu is fine with but Windows isn't. Obscure and took ages to figure out. Could you post the name of a file that you can see in Win and one you can't, please? You may be able to pick the anomaly yourself.

There's a clue. I don't think it's got anything to do with the filesystem you're using on the SD card. If Win can see some files it has no problem with it.

---

### Post by jfca283 on 2013-11-22
But songs named "04 - Lucky.mp3" is the typical case. There is no strange character in the file names. But it seems that you point is right. Other way the card would be completely unreadable. What do you recommend me? Thanks

---

### Post by ksprasad on 2013-11-22
Hi,

In windows, can you open the SDCard location in command prompt and see if it can see those files? Even i dont think, it is anything to do with the file format.


Regards,
Ksprasad

---

### Post by Bucky Ball on 2013-11-22
> **jfca283 said:**
>  "04 - Lucky.mp3"

Tried taking the spaces out? 

04-Lucky.mp3

You can see absolutely no differences in the file names of the ones that are visible and the ones that aren't? 

Have you converted these files from one format to another using Ubuntu? And if so, what software did you use to do it? Also had a situation where had to batch process a bunch of files because Win didn't like some aspect of a conversion to MP3.

---

### Post by jfca283 on 2013-11-22
There are files named "04 - xxx.mp3" which are recognised and others not. Even some movies. The files were downloaded them from a torrent website. I'm really confused.

---

### Post by Bucky Ball on 2013-11-22
> **jfca283 said:**
> The files were downloaded them from a torrent website.

Anyone's guess then. Good luck. Be aware that we do NOT support illegal activity on this forum so do NOT provide links to these torrents if they were not downloaded legally (which I'm suspecting they weren't, correct me if I'm wrong). Thanks.

---

### Post by jfca283 on 2013-11-25
Again i wrote some files using ubuntu in the sd card. Only some of them are shown. But the space used is considerably reduced. I have no idea what the problem is. Maybe it was a bad, very bad idea buying the sd card as a pendrive.

---

### Post by Bucky Ball on 2013-11-25
Um. If you put this same bunch of files on a pendrive (USB dongle) are they seen ok? Just thought I'd ask ...

---

### Post by jfca283 on 2013-11-25
Yep. I have two alternatives for answers. The first one is the card is not effectively well unplugged it. Maybe that's the reason the files are copied and using space but not appearing all in the sd card when i use windows. The second answers is the files are not copied. But it's difficult to check.

---

### Post by ksprasad on 2013-11-25
Ok. Just to make sure the files are not seen because they are hidden, can you enable the 'show hidden files' in windows and see if its shown?
That option will be under view in folder options.

Regards,
ksprasad

---

### Post by jfca283 on 2013-11-25
Nop. I enabled the show hidden files and they are not displayed. Really confusing issue.

---

### Post by jfca283 on 2013-11-27
Again i wrote some files under ubuntu. Now under windows they are not shown. No idea.

---

### Post by westie457 on 2013-11-27
Are you using the system to eject/unmount the SD card?

Or are you just pulling the card out of the slot?

Tell Windows to run a chkdsk /f on the SD card. That might help.

---

### Post by jfca283 on 2013-11-27
I tiped eject from the console under ubuntu. Even i received the message you can unplugged your device. The sd card has a capacity of 64gb. Can it be a problem that? I will run the chkdsk.

---

### Post by Bucky Ball on 2013-11-27
Well, that would mean Win can't read an SD card that size. If Ubuntu can read it but Win can't there's nothing wrong with the SD I wouldn't think.

---

### Post by jfca283 on 2013-11-27
windows found problems with the file system.

---

