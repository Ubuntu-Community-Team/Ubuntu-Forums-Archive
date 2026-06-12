---
title: "Reporting 0 space when writing to CD-RW"
date: 2009-07-10
forum: Hardware
---

### Post by ssalman on 2009-07-10
[FONT=Times New Roman][SIZE=3]Hello,[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]I've been trying to get my head around this problem for few weeks now with no result. I'm trying to burn some data files on a CD-RW, with no luck, I've used brand new discs, wiped (both Ubuntu & WinXP erased) discs, even different speeds & manufacturers, and all have the same problem: reporting 0 free space on an empty CD-RW. Still, CD-R works great![/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Any one encountered this issue? Any idea how to solve it?[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]Below is the error I get. [/SIZE][/FONT][FONT=Times New Roman][SIZE=3]Appreciate the help![/SIZE][/FONT]
 
> Blank CD-RW Disc: 0 bytes of free space
Please choose another CD or DVD or insert a new one.
The size of the project is too large for the desc even with the overburn otion.

---

### Post by ssalman on 2009-07-12
update:

after reading some related suggestions on this forum, I tried to write files to an image first and then to burn the image onto the DR-RW, but with no luck. problem presists although the image was only 409Mb.

any ideas?

---

### Post by Mister.Vash on 2009-07-13
Does the disk mount on insertion?  You might need to umount it prior to burning it.

Also, have you tried erasing/reformatting the disk first, maybe with a different application that one you are currently using.  Here are two that you could try:
[http://ubuntuforums.org/showthread.php?t=172388](http://ubuntuforums.org/showthread.php?t=172388)

If that doesn't do anything, do you get any errors in your log files when you first insert the disc?

---

### Post by ssalman on 2009-07-13
I checked the syslog (below) and you are right there are few error messages. I then tried k3b & GenomeBaker: k3b did not recognize the CD, while GenomeBaker was able to burn the CD-RW finally!!

Thanks for the help, however I still can't understand the problem! is this a known bug? is there some logic behind all of this?

```
[  742.018940] cdrom: This disc doesn't have any tracks I recognize!
[  742.152696] end_request: I/O error, dev sr0, sector 0
[  742.152709] __ratelimit: 6 callbacks suppressed
[  742.152717] Buffer I/O error on device sr0, logical block 0
[  742.154223] end_request: I/O error, dev sr0, sector 0
[  742.154232] Buffer I/O error on device sr0, logical block 0

```

---

