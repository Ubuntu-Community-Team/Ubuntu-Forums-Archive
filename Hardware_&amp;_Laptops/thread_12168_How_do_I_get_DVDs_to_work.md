---
title: "How do I get DVDs to work"
date: 2005-01-22
forum: Hardware &amp; Laptops
---

### Post by apoc on 2005-01-22
:update: I have followed the guide at [www.ubuntuguide.org](www.ubuntuguide.org).

:update2: I tried to change the preferences in mplayer for the DVD link, instead of /dev/dvd i typed /media/cdrom0 (wich appears to be where it is when I go into the dvd from the icon on the desktop) however it will then play without sound, and give a warning about memory.

Totem:
When I press "play disk" it says I'm missing some modules.

Xine:
One error just says (/dev/dvd)
another says "there is no input plugin available to handle 'dvd:/'. Maybe MRL syntax is wrong or file/stream source dosn't exist."

Mplayer:
Couldn't open DVD device: /dev/dvd

If I go into the dvd from the icon on my desktop and opens one of the files with mplayer it does indeed play what seems to be a random part of the movie (with sound).. it seems to me that a fix sould be easy then. I just can see what I need to do.

---

### Post by jakeslife on 2005-01-22
This is a problem that many people new to linux have, and it's also well documented. The direct URL to help you is [http://ubuntuguide.org/#dvdplayback](http://ubuntuguide.org/#dvdplayback), but it also includes many other things I'm sure you'd like as well.

Another good read: [http://catb.org/~esr/faqs/smart-questions.html](http://catb.org/~esr/faqs/smart-questions.html)

---

### Post by apoc on 2005-01-22
Thanks, I'll look at that right away

:edit: I see I forgot to mention that I have already followed the guide at [www.ubuntuguide.org](www.ubuntuguide.org), and installed the codecs ect. and the symbolic link.

And if you think I asked my question in the wrong forum direct me to the right one, thanks. I've been working on getting linux to work for about a week now, and belive me, I have googled quite alot. But agin, if I'm not allowed to ask questions here, direct me to people/place that accerly wishes to help..

Thanks but it didn't help me.

---

### Post by jakeslife on 2005-01-22
I don't believe I said you couldn't ask questions in this forum, I just find a lot that people don't do their research before they ask questions, and like you said yourself, you didn't mention that you had followed the guide at ubuntuguide.org. Without this bit of info, it appeared that you hadn't yet seen that site, or the many threads on this forum that deal with DVD and playing them in various media players (threads in both the Hardware Support and Software Support sections).

I also never said that you were asking the wrong forum or posting in the wrong thread--the reason I posted that link (which I post for a lot of people) is that common sense is rarely common (also note that your name is not in that sentence, hence it is not directed solely at you).

Okay, so first things first, you followed the guide. Did everything install properly? What media player are you trying to play them in? 

> Totem:
When I press "play disk" it says I'm missing some modules.

Did you try installing those modules? 

> Xine:
One error just says (/dev/dvd)
another says "there is no input plugin available to handle 'dvd:/'. Maybe MRL syntax is wrong or file/stream source dosn't exist."

No plugin available..which usually means that the software doesn't support it. (a library/plugin issue--see above)

> Mplayer:
Couldn't open DVD device: /dev/dvd

Are you able to mount your DVD device and see the files on it, or is your computer not even recognizing your drive? If this is the case, then you need to check your fstab file (search the forum for this...there are a lot of helpful threads) to make sure that's taken care of. 

I would try to troubleshoot whether it's a software or hardware issue, then go from there.

---

### Post by apoc on 2005-01-22
> Are you able to mount your DVD device and see the files on it, or is your computer not even recognizing your drive? If this is the case, then you need to check your fstab file (search the forum for this...there are a lot of helpful threads) to make sure that's taken care of.

Yes, I am even able to play single files from the dvd in mplayer.

I'm fairly sure that mplayer just dosn't know where to look the right place, however the most odd thing is that if I edit the path for dvd in mplayer to /media/cdrom0 I can play the dvd without sound and some frame error.

And no the problem is software I'm sure, since I bootet windows ad watched the movie like normal..
> 
Okay, so first things first, you followed the guide. Did everything install properly? What media player are you trying to play them in?

Yes it did install correctly. I'm trying all of the ones I mentioned in the first post.

maybe its the symbolic link that is wrong, how could I control that it is correctly ?

---

### Post by jakeslife on 2005-01-22
> And no the problem is software I'm sure, since I bootet windows ad watched the movie like normal.. 

Windows and Linux recognize hardware in different ways, but if you are able to mount and access the drive it's not hardware.

If you have to change your path to /media/cdrom0 in order to get something to work, then chances are it's not set up in fstab correctly, and if it plays with no sound, that's most likely a software issue as well (unless your system has no sound obviously).

---

### Post by apoc on 2005-01-23
Could you spot the error if I posted the content of the ftstab file ?, I remember editing that file to get my windows disk shown.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/hda1       /mnt/windows_c    ntfs    umask=0222      0       0
/dev/hda5       /mnt/windows_d    ntfs    umask=0222      0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
```

I'm positive that /media/cdrom0 is my DVD drive.

I uncomented the floppy0 since I dont have a floppy drive, and it seemed to work..

---

### Post by apoc on 2005-01-23
[SOLVED]

I found a command that could show me symbolic links.

```
sudo find . -type l -print | xargs ls -l
```

Among others in the /dev folder it found.

```
lrwxrwxrwx    1 root     root            3 2005-01-23 17:08 ./cdrom -> hdd
lrwxrwxrwx    1 root     root            3 2005-01-23 17:08 ./dvd -> hdd
```

That appeard to be wrong ones I have created. because the file browser shows /media/cdrom0 when I browse a DVD disk in my DVD drive.

I deleted the above two symbolic links with

```
sudo rm ./cdrom
sudo rm ./dvd
```

Then created a new one

```
sudo ln -sf /media/cdrom0 /dev/dvd
```

Apperently the problem I had with sound was the particular disk standard seleced sound was not supported by my system.

---

