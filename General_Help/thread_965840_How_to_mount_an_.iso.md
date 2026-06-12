---
title: "How to mount an .iso"
date: 2008-10-31
forum: General Help
---

### Post by baz8771 on 2008-10-31
Hey guys, when i had windows, i made a .iso of a game with alcohol 120 and backed it up on my external hard drive, now i want to mount/install it on ubuntu.  Are there any GUI programs that i can use... ive seen the command for mounting, but i cant figure out how to make it work, can someone maybe explain it to me real quick? the iso is on my desktop.

---

### Post by alienprdkt on 2008-10-31
[here you go ]("http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html")

[http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html](http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html)

---

### Post by alienprdkt on 2008-10-31
sorry double post

---

### Post by tobbakko on 2008-11-23
Hi didn't know where to put this, hope that somebody could help. Can't mount iso-files in Ubuntu 8.10. I have tried with daemon-tools in Windows and there in works fine.

I have tried commands like: 
sudo mount name.iso /media/isoimage/ -t iso9660 -o loop

I'am trying to mount Fallout 3, iso-file (5,5 GB)

Error message:

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
missing codepage or other error
In some cases useful info is found in syslog - try dmesg | tail or so

---

### Post by SPr on 2008-11-23
What does dmesg|tail say?

The error complains about the wrong fs type. Have you tried it without the -t option?

---

### Post by tobbakko on 2008-11-23
Thank's for the fast reply, it works!!!

"That it was that simple"

---

### Post by SPr on 2008-11-23
You're welcome.

---

### Post by dvergur on 2009-06-16
I couldn't find any thread addressing my problem but this one comes pretty close so I'll just piggyback on this one. I had the same problem as that other guy but just like him skipping the t option helped a little, now I can mount it but it only shows 30 or so MB worth of files out of 5.6GB. I had this problem before but it was a long time ago and now I can't for the life of me find the solution again. I would love some help or directions to help.

---

### Post by ciprian.topala on 2009-06-16
have you tried to use an application like gmount-iso?

---

### Post by dvergur on 2009-06-16
Yes, I used gmount-iso but it returns the same error as the terminal did with the t option.

---

### Post by t4ggs on 2009-06-16
install Gmount from the add/remove software

---

### Post by dvergur on 2009-06-16
Well, as my last post indicated I already have it up and working but it won't open this file.
I know for a fact that there is a solution to this problem as I've had to deal with it before, last time I just had to change the mount command or something. But all my google efforts have proven fruitless.

---

### Post by dandnsmith on 2009-06-16
when using **mount**
put the options before the device and mount point
mount -t iso -o loop ...

---

### Post by dvergur on 2009-06-16
I should really be more concise, I'm just wasting everybody's time. My command was
$sudo mount -o loop /home/dvergur/rld-sim3/rld-sim3.iso /mnt/iso/
It was
$sudo mount -o loop -t iso9660(,udf) /home/dvergur/rld-sim3/rld-sim3.iso /mnt/iso/
before with less success with the bracketed item. I stopped using the t option since it was causing some problems.
With the former command I'm only seeing two folders holding 30MBs of files.
The last time I had this problem it was also involving some game. I'm getting the feeling it has something to do with an inherited write protection or something, I have nothing to support this feeling though.

---

### Post by petrasflorin on 2010-10-12
I had the same problem
I just used sudo mount isoimage.iso /home/petrasflorin/isofolder -o loop
That did the trick. Find it easier to use than GMount-Iso , gonna use this now.

---

### Post by sepo on 2010-10-12
Sometimes -instead of mounting the file- I find useful to right click on the .iso file-> open with Archive mounter.
This will 'mount' the image for you...then you can explore it from the Places menu, from your desktop or from the /home/you/.gvfs/youriso/ folder.

Seeya
Sepo

---

