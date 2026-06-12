---
title: "How do I creae dual boot with XP when ubuntu is already installed?"
date: 2008-09-24
forum: General Help
---

### Post by colobix on 2008-09-24
Hi
I know I can do this by creating a fresh ntfs partition and install windows on that one, but how can I do that, and add xp to grub after ubuntu?
I also have the alternative to use my other hard driver for winxp so i can install it right to that disk, but with ubuntu on one hdd and xp on another, what happens to grub then?
Will grub add windows at the end of the list automaticly or will my pc boot directly to xp and delete ubuntu from the grub menu?

Thanks in advance.

---

### Post by Elfy on 2008-09-24
Whichever way you do it - xp will overwrite grub and you will need to reinstall grub; you should be able to do so with your buntu livecd or supergrub.

Both are detailed here - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by tehforum on 2008-09-24
Hi forestpixie, I have ubuntu 7.10 installed on my computer right now. But I do not know how to partition the hard drive, so you can install Windows on there.

Would you please advise me on how to partition my hard drive, and what to do after that (I presume you just put in the windows xp installation cd).

Thanks.

---

### Post by colobix on 2008-09-24
So I have to do this the hard way nomater what I do?
It would b easier if i could do it from windows since it overwrites everything.
Is there any progrm in windows i can use to reinstall and edit grub?
If so this won't b a problem.

---

### Post by Elfy on 2008-09-24
Well it's not hard and only takes a few minutes, the hard bit will be installing xp and the necessary drivers for your hardware ;)

I am not sure whether there is a way to install grub in windows, although I _think_ I've seen something. If I remember I'll post it.

@tehforum - you need to resize your buntu partition, I think preferably from the left, so that there is space for xp to install, once it is installed then you will need to reinstall grub as above.

---

### Post by kokkus on 2008-09-24
Tehforum, that's out of topic, create a new thread.

Yes colobix, it does.
Download it here (its free) [http://www.download.com/1770-2001_4-0.html?query=recover+grub&tag=srch&searchtype=downloads](http://www.download.com/1770-2001_4-0.html?query=recover+grub&tag=srch&searchtype=downloads)

Install winxp on your 2nd hdd or as you said create a fresh partition on the same hdd and install windows on it.
Now you can run Windows and download the grub recovery program I gave you the link for and you're done.

---

### Post by colobix on 2008-09-24
Thank you so much guys.
forestpixie, can you plz tell me step by step how to do the grub thing incase it won't work from windows with that program?

---

### Post by caljohnsmith on 2008-09-24
Colobix, if you install Windows to your other HDD, it won't overwrite the MBR (master boot record) of you Ubuntu drive that presumably has Grub in the MBR. If you do install Windows to a different partition of the same HDD as Ubuntu, then as forestpixie pointed out, it will overwrite Grub in the MBR. In order to restore Grub back to the MBR, you can use the Super Grub Disk that kokkus gave a link to, or you can easily restore Grub with your Live CD with the following simple steps:
```
sudo grub
grub> find /boot/grub/stage1
```
That should return your Ubuntu partition in the form of (hdX,Y), for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
So whether you install Windows to its own HDD or a partition on your Ubuntu HDD is entirely up to you, because it is easy to restore Grub if it does get overwritten with the Windows MBR. Let us know how it goes or if you need more specifics. :)

---

### Post by Ms_Angel_D on 2008-09-24
Links to complete tutorials with Pics can be found here

[http://ubuntuforums.org/showthread.php?t=904645](http://ubuntuforums.org/showthread.php?t=904645)

---

### Post by colobix on 2008-09-24
hank you SO MUCH guys,

---

