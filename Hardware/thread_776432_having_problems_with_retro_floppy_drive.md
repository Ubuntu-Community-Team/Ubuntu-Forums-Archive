---
title: "having problems with retro floppy drive"
date: 2008-04-30
forum: Hardware
---

### Post by 900donuts on 2008-04-30
hi heres my problem

i've got the 5.25" floppy version of secret of monkey island :popcorn: (its on 8 360k disks) and I've been trying to use my 5.25"/3.5" floppy combo drive to load the game on to my computer so i can install it with dosbox 

but when i try to  mount the the floppy i get an error telling me that i have to specify the file system type :(

what do i do :confused:

---

### Post by jimv on 2008-04-30
Just download it.  It's abandon-ware...which means you can download it for free.

[http://www.abandonia.com/en/games/19](http://www.abandonia.com/en/games/19)

---

### Post by 900donuts on 2008-04-30
the problem is what if i find a game on 5.25" floppies that is not abandon ware

---

### Post by jimv on 2008-04-30
What you could do is go through your floppies and see which ones are available on that site.  It could be that they all are.

OK, I also did some research on the floppy issue.  Try mounting it with this command:

> sudo mount -t msdos /dev/fd0 /media/floppy0

---

### Post by 900donuts on 2008-04-30
i'm asking for how to get my floppy drive working not taking the easy way out and use the internet

EDIT: i'll try that

besides i'm getting some "no go" text where the download button should be and how do i know its not just a demo?

---

### Post by 900donuts on 2008-04-30
i'm getting a can't read super block message 

THEORY: perhaps the disk is older than ms-dos file system

---

### Post by jimv on 2008-04-30
I just did some more googling, and it seems like its either a problem with the disk or the drive isn't supported (driver issues).  I suppose you could try another disk to see if that works.

---

### Post by 900donuts on 2008-05-01
i found a page that may hold the answer here
[http://episteme.arstechnica.com/eve/forums/a/tpc/f/24609792/m/304005907731](http://episteme.arstechnica.com/eve/forums/a/tpc/f/24609792/m/304005907731)
i don't know if the floppies are toast but i figure that even if the data is damaged the computer would still recognize that there is a floppy in the drive i'm gonna have to pull the drive out and look at it this weekend

---

