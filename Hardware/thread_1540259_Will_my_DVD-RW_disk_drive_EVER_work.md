---
title: "Will my DVD-RW disk drive EVER work??"
date: 2010-07-27
forum: Hardware
---

### Post by fallenshadow on 2010-07-27
I have been using Ubuntu since 8.04 and am currently on 10.04. My disk drive still does not work!!

I have a DVD-ROM drive that works but my DVD-RW only reads and writes CDs. :P

I don't have much info on it except this:

Make: LG
Type: DVD-RW with lightscribe technology. 
(but its listed as DVD-RAM writer)

I presume its because a driver has not been developed for it but I want to bring it to their attention that it only partially works.

---

### Post by cascade9 on 2010-07-27
It shouldnt be a driver issue...it could be incompatible for some reason, and its also possible that you have a worn out burning laser.

---

### Post by fallenshadow on 2010-07-27
> its also possible that you have a worn out burning laser.

Nope its not anything like that because I can burn CDs.

---

### Post by cascade9 on 2010-07-27
Thing might have changed, but I know that CDs and DVDs used to have different burning lasers. 

> [FONT=Verdana][SIZE=1]                    The CD and DVD burners use different hardware as well as                     different laser types and frequencies. [/SIZE][/FONT]

[http://www.digitalfaq.com/guides/media/dvd-formats.htm](http://www.digitalfaq.com/guides/media/dvd-formats.htm)

---

### Post by jerenept on 2010-07-27
this happened with me.... my DVD-RAM burner only supports DVD's; CD's are not recognised (even in Windows with drivers).

EDIT: mine is an LG HL-DT-ST DVD-RAM-GSA-H50N, if this helps.

---

### Post by fallenshadow on 2010-07-28
I found my model number:

DVD-RAM GSA-H20L

I don't think its a problem with the burning lasers... this drive has been rarely used.

This looks interesting: (its from my hardware list in terminal)

> capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram

Seems like dvd-rw is not listed, even though it is a DVD-RW drive.

---

### Post by cascade9 on 2010-07-29
I get the same readout (well, minus DVD-Ram) 

```
capabilities: removable audio cd-r cd-rw dvd dvd-r
```

Odd that I dont get DVD-RW as well, and as I've never tried a RW I dont know for sure if it would work. DVD-Rs work fine here though.

---

