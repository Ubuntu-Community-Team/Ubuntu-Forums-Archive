---
title: "Loud CD/DVD: slowing the spin rate?"
date: 2005-04-14
forum: Hardware &amp; Laptops
---

### Post by tora201 on 2005-04-14
Hello, just wondering if anybody has had the problem whereby their DVD/CD drive is spinning at full tilt when playing divx/dvds. 

It is really annoying. I have tried all the media programs. My player is a standard dvd/cd burner.  

Is there any way to slow down the spin rate when playing movies?

Thanks in advance.

Zane Ritchie

---

### Post by heimo on 2005-04-14
Three different approaches.
 
```

hdparm -E [speed] [cdrom device] 
setcd -x [speed] [cdrom device]
echo current_speed:4 > /proc/ide/[cdrom device]/settings

``` 
speed can probably be one of 1 2 4 8 16
cdrom device can probably be /dev/cdrom or /dev/dvd
 
 
Source:
[http://web.njit.edu/all_topics/Prog_Lang_Docs/html/mplayer/cd-dvd.html]("http://web.njit.edu/all_topics/Prog_Lang_Docs/html/mplayer/cd-dvd.html")
 
 
EDIT: You need to be root to do that (prefix commands with sudo)

---

### Post by skwid on 2005-04-14
[QUOTE=heimo]Three different approaches.
 
```

hdparm -E [speed] [cdrom device] 
setcd -x [speed] [cdrom device]
echo current_speed:4 > /proc/ide/[cdrom device]/settings

``` 
speed can probably be one of 1 2 4 8 16
cdrom device can probably be /dev/cdrom or /dev/dvd
 
 
Source:
[http://web.njit.edu/all_topics/Prog_Lang_Docs/html/mplayer/cd-dvd.html]("http://web.njit.edu/all_topics/Prog_Lang_Docs/html/mplayer/cd-dvd.html")
 
 
EDIT: You need to be root to do that (prefix commands with sudo)[/QUOTE]
 Hey, I've seen the same problem and that got me all fixed up....  

Thanks heimo...

---

### Post by tora201 on 2005-04-14
Heimo, thanks very much.
I will try that and let you know. Once this problem is ironed out, everything looks perfect! Cheers mate,

Zane

Update: Got it going! You need to change the spin rate to x4. Also, I enabled the DMA and read ahead cache, according to the link posted by Heimo. -- thanks!! Silence is golden. :razz:  

done as root: (for 4 speed)
hdparm -E 4 /dev/scd0 <---my cdrom device

and for prefetch cache:
echo file_readahead:2000000 > scd0/settings

This sets prefetched file reading to 2MB, which helps with scratched CD-ROMs. If you set it to too high, the drive will continuously spin up and down, and will dramatically decrease the performance. It is recommended that you also tune your CD-ROM drive with hdparm:

The below enables DMA access, read-ahead, and IRQ unmasking (read the hdparm man page for a detailed explanation)
 
hdparm -d1 -a8 -u1 (path to your cdrom device)

---

