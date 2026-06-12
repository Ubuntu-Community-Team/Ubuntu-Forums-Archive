---
title: "usb/mp3"
date: 2005-07-01
forum: Hardware &amp; Laptops
---

### Post by souraka on 2005-07-01
hi all i have problem with my mp3 player 
i can not delete files from the mp3 or add some 
each time i try i have this error" you are not aloowed to etc..."

is anyone know hoh to resolve it??


the first time i connected it to my pc everything was ok and i could add some music int it but now no way to make anything

please help

---

### Post by vsantos on 2005-07-01
Hi!

I'm new to Ubuntu, but I believe that has something to do with your /etc/fstab.
Check if '...,rw,users' is in the flags column, corresponding to your mp3 device/mount point line...

Regards,
Vasco

---

### Post by N'Jal on 2005-07-01
Yes it does sound like a permissions error. Try what souraka suggests

type 

sudo gedit /etc/fstab 

into the terminal this will allow you to see what the permissions for the mp3 player are.

---

### Post by souraka on 2005-07-02
ok thanks i try what you said  this is the result:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


dont understand wihc part talk about the mp3 player... :|



NO BODY FOR THIS ??  ](*,)

---

### Post by zeca_pedra on 2005-07-11
Well I have the very same problem as souraka and I've tried all the possible solutions that I've found on this and other foruns. The only difference is that instead of a MP3 player mine is a pendrive.
Everything was working great until a few days ago.
Now, no matter what I do, I always get a «this is a read-only device» and I can't add, delete, format... let's face it: I can't do anything useful with that pendrive!!!
The problem gets bigger since the pendrive doesn't have a lock/unlock switch...

Now, should I say goodbye to this pendrive or there will be a solution for this problem? Please, give me some hope... :) 

PS - I've noticed that this error appears also in winXP because I've tried it today on a PC at work  :grin:  Oh, well, maybe it's time to say goodbye to the pendrive

---

### Post by souraka on 2005-07-12
ok i have something maybe

i try first to follow instruction here
[http://wiki.ubuntu-fr.org/installation/mount_fstab?s=usb+mount](http://wiki.ubuntu-fr.org/installation/mount_fstab?s=usb+mount)

after that i format mkfs etc....

and everything seems to work i can add or delete songs the only problem i have now is that my mp3 player refuse to play (like it is batery less) but i put new batery so i dont understand
i don't know if you can try it for yours let me know

schusssss

---

### Post by DancingSun on 2005-07-12
I don't use a pen drive, and I don't know French.  That being said, you mentioned you followed the how-to and format it into mkfs?  Doing a quick searching I don't see where mkfs is mentioned in the how-to.  What I suspect is that, you might have formatted the MP3 player's storage into a format that it can't understand.

---

### Post by souraka on 2005-07-13
ok can i try another way to format then and so wich one?

---

### Post by DancingSun on 2005-07-13
[QUOTE=souraka]ok can i try another way to format then and so wich one?[/QUOTE]
Well, I would try formatting as FAT32, as this format is read/writeable by both Linux and Windows.

I don't know what file system formats does your MP3 player supports, so this is kind of a shot in the dark.  But if the MP3 player supports Windows, then FAT32 is likely the format it uses.  The other possibility is NTFS, if that's the case then you won't be able to write to the media, since Linux doesn't support write operations to NTFS file systems.

BTW, what kind of MP3 player do you have? Some product info might help.

---

### Post by souraka on 2005-07-14
its good in fat32 
i try to format it again it seems to be good now but i would try several times to be sure (with linux and windows) but for now i can play music with it add some and delete (format only) 
if you have more info which can help using it correctly i'd like to have it  :razz: 

thanks for your help

---

### Post by DancingSun on 2005-07-14
Do you mean that you can add mp3 files but cannot delete them the normal way and have to reformat the MP3 device?  Is there any error message?

---

### Post by souraka on 2005-07-14
yes exactly
but i have no error message its just that when i delete files the storage dont move so  i can add somme but when i remove some nothing seems to happend in the storage of my mp3 player so i need to be sure of the song i put in it  ](*,) 

could be hard

---

### Post by DancingSun on 2005-07-14
Maybe you just need to refresh Nautilus (ctrl-r)?

---

