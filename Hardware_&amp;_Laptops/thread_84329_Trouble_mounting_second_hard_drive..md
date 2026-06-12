---
title: "Trouble mounting second hard drive."
date: 2005-10-30
forum: Hardware &amp; Laptops
---

### Post by Darrin on 2005-10-30
I have a second internal drive which I reformated using system>administration>disks. Heres the info:
Device: /dev/hdb5
File System: vfat
Access path: /boot
Status: accessible.

I change the access path to: /media/backup, but when I click on OK, and launch the disk utility again, the access path is back to /boot. 

Im trying to make it mounted on boot up, so I can write and read to it in either ubuntu or windows. Which I assume is [doing it this way.]("http://ubuntuguide.org/#mountunmountfat") Doesnt seem to work. 

Once again I call on you ubuntu users to bail me out. ;)

---

### Post by aysiu on 2005-10-30
If you want it mounted at bootup, you should follow these directions:

[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

---

### Post by Darrin on 2005-10-30
[QUOTE=aysiu]If you want it mounted at bootup, you should follow these directions:

[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)[/QUOTE]

I did try that but after entering the first command this is what the response was:
[COLOR="Blue"]mkdir: cannot create directory `/media/backup': File exists[/COLOR]
Maybe it has something to do with this problem? I change the access path to: /media/backup, but when I click on OK, and launch the disk utility again, the access path is back to /boot.

---

### Post by Darrin on 2005-10-30
I figured out what I did wrong now. Sorry, Im slow at this. Im determined to figure this out. I really want to not have to use windows. Im learning something new everyday.

---

### Post by aysiu on 2005-10-30
Well, it can't create the directory if it already exists (mkdir = make directory).
Okay, start off like this. Forget administration > system > disks. Open a terminal and do everything from the terminal from now on; that's the easiest way for me to help you. ```
sudo umount /media/backup
sudo cp /etc/fstab /etc/fstab_backup_2
sudo nano /etc/fstab
``` Delete whatever line that has references to /media/backup or /dev/hdb5. Delete them. Get them out of there. Then, add this line instead ```
/dev/hdb5       /media/backup  vfat    iocharset=utf8,umask=000   0       0
``` Type Control-X (to save), y (to say, yes, you want to save), Enter (to finish with nano). Then you'll be back in the regular terminal. Type ```
sudo mount -a
exit
``` Now open up Nautilus (the file browser) and browse to the /media/backup directory. Anything there?

**Note**: Follow these directions *exactly* as I give them. If you have questions as to what a command does, ask what it does, but don't do something else.

---

### Post by aysiu on 2005-10-30
[QUOTE=Darrin]I figured out what I did wrong now. Sorry, Im slow at this. Im determined to figure this out. I really want to not have to use windows. Im learning something new everyday.[/QUOTE] Yikes! After I typed all that? Well, I'm glad it all worked out for you.

---

### Post by Darrin on 2005-10-30
[QUOTE=aysiu]Yikes! After I typed all that? Well, I'm glad it all worked out for you.[/QUOTE]

I appreciate all that typing. Knowing me Im sure I will have to come back to this thread in the future. So much Im learning right now, I hope I can retain it. ;) 

Thanks again for all your help on this issue and all the others you have helped me out with before and will again Im sure. Much appreciated. :D

---

### Post by aysiu on 2005-10-30
[QUOTE=Darrin]I appreciate all that typing. Knowing me Im sure I will have to come back to this thread in the future. So much Im learning right now, I hope I can retain it. ;) 

Thanks again for all your help on this issue and all the others you have helped me out with before and will again Im sure. Much appreciated. :D[/QUOTE] Well, such is the way of these forums. Go and do likewise. It's a friendly and helpful place here--that's why I use Ubuntu.

---

### Post by Darrin on 2005-10-30
[QUOTE=aysiu]It's a friendly and helpful place here--that's why I use Ubuntu.[/QUOTE]
Thats why I havent given up on it. ;)  Great people and tons of helpful information throughout the website.

---

