---
title: "Tape Drive Compatiblity"
date: 2006-11-22
forum: Hardware &amp; Laptops
---

### Post by kdepa on 2006-11-22
Hello,

I am trying to find out if my tape drives are compatible with ubuntu.  I can't seem to find any information on google.  The types of drives I have are:

Iomega Ditto 800

HP Colorado T3000

They both connect via the floppy port in my server.

Are they compatible? If so, what software should I use?

Thanks!

---

### Post by christhemonkey on 2006-11-22
IT would seem like they are vaguely supported yes.

> Iomega Ditto 800 Insider

    Works with Travan TR1, TR2, or DC2120 tapes

The HP Colorado T3000, i have no idea about.
Try it and find out!

For reference see this page:
[http://www.linux.com/howtos/Ftape-HOWTO.shtml#toc15](http://www.linux.com/howtos/Ftape-HOWTO.shtml#toc15)

Actually, upon further looking, it is not included in the repositories anymore, but was for breezy, which probably means it was superseeded by something better.

I'll go back to google-ing it!


EDIT:

It would seem tob lets you backup data to an from tape drives, an that tape drives in them selves.

This page seems very helpful:
[http://www.linuxtapecert.org/](http://www.linuxtapecert.org/)

There is a nice kde app for tape drives, kdat:
> KDat is a tar-based tape archiver. It is designed to work with multiple archives on a single tape.

Main features are:

 * Simple graphical interface to local filesystem and tape contents.
 * Multiple archives on the same physical tape.
 * Complete index of archives and files is stored on local hard disk.
 * Selective restore of files from an archive.
 * Backup profiles for frequently used backups.



---

### Post by kdepa on 2006-11-22
Yeah, I am trying to find what superceded it, but with no luck.  I'm on edgy eft.

---

### Post by kdepa on 2006-11-22
It looks like amanda supports the floppy tape driver, but I can't tell if I need to install ftape in addition to amanda to make it work...

---

### Post by christhemonkey on 2006-11-22
Amanda is in the edgy repositories so i imagine it wont!

I would suggest trying the kdat utility, as a nice GUI interface.

As it seems that the actual support for these tape backup drives is in the kernel, and loaded with kernel modules.
So the best thing might just be to plug one in an check the output of ```
dmesg | tail 
```
(also make sure in user preferences that you can access tape drives as i seem to remember that default users cant do this already for some reason)

---

### Post by kdepa on 2006-11-22
I have edgy installed as a server, so I have no GUI available.  The only thing listed in dmesg that *may* be the tape drive is 

```
FDC 0 is a post-1991 82077
```  I have looked at the entire output of dmesg (dmesg | less), and that's all that shows.

---

### Post by christhemonkey on 2006-11-23
Ah, ok.

And FDC stands for **F**loppy **D**rive **C**ontroller, i think.

Try installing the amanda software.



Also, couuld you please give the output of these commands?
```
ls /dev/ | grep nst0
ls /dev/rmt/ | grep 0mn

```

---

