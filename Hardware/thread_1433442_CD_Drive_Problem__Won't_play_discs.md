---
title: "CD Drive Problem:  Won't play discs"
date: 2010-03-19
forum: Hardware
---

### Post by slutke55 on 2010-03-19
I am having problems playing DVDs and CDs on my 9.10.  I had this problem before when I had Ubuntu mounted as an application on top of Vista, but after I went to a full partition, the solution I had found got lost in the reinstall.  If I remember correctly, it was one line of code in terminal that fixed the problem.  Basically, I can put a DVD in the drive and it is recognized by Open Mediaplayer.  As soon as I try to play it, the player's window opens, and then immediately closes.  Also, the CD must be ejected with sudo eject (the button doesn't work anymore).  The drive appears to be mounted, but when I ran a dmesg | tail it said that sr0 had logical error 202206.  Any help is appreciated.  Like I said, last time I just had to punch one line of code into terminal and it fixed everything (should have written it down)

---

### Post by PRC09 on 2010-03-19
Not sure about the error info and button but you will need the following to play most multi-media formats.Hope this helps.....  





[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by sam.reader on 2010-03-19
Did you your CD/DVD drive on some other PC.
Try to run it on one of your friend's pc and check if the same problem persists.
I have a feeling that the problem is with your hardware.
Let me know the result if you do this.

---

### Post by wojox on 2010-03-19
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

