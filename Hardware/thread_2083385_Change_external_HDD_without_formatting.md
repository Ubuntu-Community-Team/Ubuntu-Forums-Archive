---
title: "Change external HDD without formatting?"
date: 2012-11-12
forum: Hardware
---

### Post by JrBcnChz on 2012-11-12
I have a 500GB seagate portable external HD that I use for photo/video/music storage. I got the HD when my laptop was still a MAC (I know, i know...) so now when it's in my 12.04 laptop I can Read files but I can't copy anything to the hard drive or even rename/move things. Is there a way to "break in" to my external? I have hundreds of movies and thousands of pictures, but A) I can't add to the remaining 100GB or so of space, and B) can't copy files out of the HD to back up elsewhere.

The message it gives me, for ex. is that I cannot copy to the selected location because I am not the owner.

The user profile I had on my Mac, which no longer exists, is the owner.

I have a 3rd gen 13" macbook, 4gb ram, 2.4mhz intel processor, running 64-bit ubuntu 12.04 desktop.

---

### Post by grahammechanical on 2012-11-12
Have you tried opening the Ubuntu file Manager (Nautilus) with administrator permissions?

```
gksudo nautilus
```

I do not know it that will override the file permissions on the external hard disk but you at least will not be using nautilus as a standard user. which is the normal case in Ubuntu.

Regards.

---

### Post by JrBcnChz on 2012-11-12
Noob tho I be, I did actually try to use nautilus but that didn't make a difference. I think i'm stuck keeping this drive as-is, as an unchangeable drive, like a finalized burned cd... oh well, add it to the list of bumps in the road on the way to ubuntu paradise, right behind "accidentally delete my home folder while trying to move something into it with the terminal" (had a file with a space in the name). Compared to that one, at least, my external drive really isn't an issue...

---

