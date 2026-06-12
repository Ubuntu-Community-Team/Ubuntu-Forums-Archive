---
title: "Can't Install Ubuntu or Windows"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by MisterKinkel on 2009-03-13
Hello everyone,

I have had successful installations of both Ubuntu and Windows on my 300GB Maxtor internal HDD, and recently I have attempted to completely repartition my drive to do clean installs of both operating systems. But when I tried to reinstall them, they either froze or had an error trying to copy a file. I have used these CDs for dozens of installs, so I know for a fact that there aren't any errors on them. I was just playing Starcraft a day before I used my CD drive, so I'm pretty sure that it is also fully functional.

What the hell is going on? Mind you, this hard drive has worked flawlessly with these operating systems before. Any help would be wonderful, as I am suffering from some serious Ubuntu withdrawal!

**_SOLVED:_**

**It turns out that it was my CD drive that was causing all the trouble, so I installed everything from my USB flash drive.**

---

### Post by scphan on 2009-03-13
it might help to post what the computer said about it ;)  

sorry if you don't mind me asking what do you mean by repartition the drive? is it just only because you want a clean reinstall of the OS's?

---

### Post by Hobgoblin on 2009-03-13
If you boot from the live CD, does the partition editor see any partitions?

I would also try running the memtest option from the liveCD for a couple of hours.

---

### Post by scphan on 2009-03-13
> **Hobgoblin said:**
> If you boot from the live CD, does the partition editor see any partitions?

I would also try running the memtest option from the liveCD for a couple of hours.
same for the windows cd (xp, optional), did it see any partitions?

[http://www.cyberwalker.com/article/614/45]("http://www.cyberwalker.com/article/614/45")

---

### Post by scphan on 2009-03-13
here's another link for reformatting the drive with windows xp disk >>

[http://askbobrankin.com/reformat_hard_drive_under_xp.html]("http://askbobrankin.com/reformat_hard_drive_under_xp.html")

whichever cd you want to use is fine

---

### Post by MisterKinkel on 2009-03-13
Sorry about that rather vague post. Allow me to clarify.

Yes, GParted did show my hard drive, and I attempted to format a 100GB partition into NTFS, with success. I then rebooted into Windows (I wanted to install Windows before Ubuntu, to avoid issues) and when it was starting up, it was having trouble reading a file. (This file changes every time I get to this step) When I got to this point, I says that that only thing I can do is restart the computer. So I complied.

But when I restarted, I decided to test my luck with Ubuntu. I threw in the CD, and hit "Install Ubuntu on this computer." It loaded, and got all the way through the 7 step GUI, into the actual installation of the operating system. The first time I tried this, it froze at 24%. Second time 75%. Should I try it again, maybe it will get all the way to 100%! :D

I did a whole bunch of other things too. I removed 1GB of RAM and tried installing. I hit F6 on the install screen for Ubuntu and typed in "noacpi," but I really have no idea why I tried that. I also tried installing Ubuntu on my 80GB SATA HDD, with it freezing at 54%. I'm really starting to think something is wrong with my CD drive, so that is what I'll look at next.

So here I am, without an OS. This stinks.

---

### Post by MisterKinkel on 2009-03-13
> **Hobgoblin said:**
> If you boot from the live CD, does the partition editor see any partitions?

I would also try running the memtest option from the liveCD for a couple of hours.

I'll try this right now, thanks for your help.

---

### Post by MisterKinkel on 2009-03-13
> **scphan said:**
> same for the windows cd (xp, optional), did it see any partitions?

[http://www.cyberwalker.com/article/614/45]("http://www.cyberwalker.com/article/614/45")

> **scphan said:**
> here's another link for reformatting the drive with windows xp disk >>

[http://askbobrankin.com/reformat_hard_drive_under_xp.html]("http://askbobrankin.com/reformat_hard_drive_under_xp.html")

whichever cd you want to use is fine

The Windows setup doesn't even get to that step, but thank you for the information.

---

### Post by MisterKinkel on 2009-03-13
Now I can't even get the Live CD to start, with this error spamming my screen:

[  290.133014] Buffer I/O error on device sr0, logical block 329019

I'll lurk around the forums for a little while longer, and then I'm going to bed.

---

### Post by scphan on 2009-03-13
here's something similar, haven't read it myself completely, hope it'll help

[http://forum.compiz-fusion.org/showthread.php?t=6717]("http://forum.compiz-fusion.org/showthread.php?t=6717")

i got that from googling "Buffer I/O error on device"
also try googling "live cd Buffer I/O error on device"

---

### Post by cariboo on 2009-03-13
I would suggest trying another CD-Rom drive.

Jim

---

