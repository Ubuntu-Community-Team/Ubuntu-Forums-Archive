---
title: "fstab PSP ?"
date: 2006-04-28
forum: Hardware &amp; Laptops
---

### Post by tioneb on 2006-04-28
HI,
I have trouble to mount my PSP correctly I can see it and all but I can't write or delete on it.
my fstab for PSP
```
/dev/sdb1 /media/psp/ VFAT rw,users,noatime,noauto,shortname=win95,check=s 0 0 
```

my folder /media/psp has these permissions: ME:users

did somebody succeed to mount a PSP correctly ?

ubuntu Dapper

---

### Post by tioneb on 2006-04-28
up!

---

### Post by tioneb on 2006-04-29
up ?

---

### Post by tioneb on 2006-05-02
up again ? Does anybody know a hint on that?

---

### Post by mips on 2006-05-02
sudo mkdir /media/psp
sudo cp /etc/fstab /etc/fstab_backup 
edit /etc/fstab

/dev/sdb1 /media/psp/ vfat umask=000 0 0

---

### Post by tioneb on 2006-05-04
already done but it doesn't work 
I tried th umask the gid the uid and different possiblities to get the correct rights
but even with the automatic detection I can't write on it (with root privileges)
... under MS I can

---

### Post by mips on 2006-05-04
I dunno, tried googling for Linux PSP ?

---

### Post by siorai on 2006-05-04
I've never even put anything in my fstab specific to my PSP. It just automounts in Gnome, but as a 465MB Removable Drive.

I do have a line for USBFS (I think that's what it is), but since I'm at work I can't post that for you. If you haven't found it by then, I'll post what I have when I get home from work.

---

### Post by siorai on 2006-05-05
Here's my fstab line that deals with USB:

usbfs  /proc/bus/usb  usbfs  defaults  0  0

But thinking about it, when I was using Breezy, I didn't even have that line in there and my PSP automounted fine.

---

### Post by tioneb on 2006-05-05
I really start to think something is wrong with the card itself ... I'll have a look when I'll have time but I'm deeply pissed off to get back to XP just for transfereing to it after encoding under Linux :'(

---

