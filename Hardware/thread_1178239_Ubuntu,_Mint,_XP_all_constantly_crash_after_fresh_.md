---
title: "Ubuntu, Mint, XP all constantly crash after fresh install"
date: 2009-06-04
forum: Hardware
---

### Post by designer17 on 2009-06-04
Hello,

I built a new htpc back in December and started with a fresh install of XP.  Shortly after the computer started freezing and explorer would crash randomly.  Annoyed I decided to wipe my hard drive and install ubuntu.  Ubuntu ran better but it would periodically freeze up and randomly kick me back to the login screen.  Being a loyal Mint fan I decided to format my hd and try out the newest Mint.  The Mint install ran the worst out of all of them. Aside from freezing up allot it was nearly impossible to watch and video over the web.  It was choppy and for some reason it made my mouse possessed.  My mouse point would bounce all around the screen and I had all I could do to click where I wanted to.

Thinking maybe it was my hard drive causing all the issues I decided to use boot and nuke to completely wipe it clean and try installing xp again.  This time xp couldn't create or format partitions and gave me an error at the same spot every time. Ubuntu and Mint wouldn't install either.  They both gave me errors when they were trying to set up the partitions.  I decided to try and set the partitions up manually and still go an error.  Gparted wouldn't touch the drive. There was a yellow triangle with an exclamation mark in it next to the drive.

I tried so many different partition tools without success.  So last night I figured I'd give Windows 7 a try.  Windows 7 partition and formatted my hd and installed perfectly in about 20 minutes.  There were some missing drivers so I downloaded drivermax cause I'm lazy and the computer froze. I restarted it and shortly after it froze again.


Its obviously some sort of hardware issue. To me it sounds like my hard drives gone bad but the entire computer is less than 6 months old.

Anyone have any thoughts as to what this could be and maybe any suggestions on trying to fix it?

Thanks

---

### Post by bol0 on 2009-06-04
For me it looks like it's a faulty HDD. To check this you would have to run some of the diagnostic software like SeaTools for Seagate/Maxtor drives or Data Lifeguard for WD, depends really on you manufacturer. They're ISO images so you burn them on CD and boot from them. Because of the issues with the partitioning you mentioned I'm pretty sure it's a hard drive. I know it's only 6 mths old but sometimes this happens to the new drives as well.

---

### Post by bvanaerde on 2009-06-04
You can also test your memory.
I think memtest is included in Ubuntu's live CD, and can be selected during boot.

---

### Post by designer17 on 2009-06-04
Thanks for the reply. I actually tried SeaTools a month or so ago back when I couldn't get anything to install. I couldn't get anything from SeaTools to run.  I got an error every time. Like I said before, it appeared like a faulty hard drive to me as well but I want rule out all other possibilities before purchasing a new one.

---

### Post by designer17 on 2009-06-04
> **bvanaerde said:**
> You can also test your memory.
I think memtest is included in Ubuntu's live CD, and can be selected during boot.

I ran the memtest about a month ago and everything passed.

---

### Post by steeleyuk on 2009-06-04
I've had this before, even used to freeze in the BIOS. Almost certainly a hard disk failure.

---

### Post by designer17 on 2009-06-04
> **steeleyuk said:**
> I've had this before, even used to freeze in the BIOS. Almost certainly a hard disk failure.

Ah, I also forgot to mention that is has frozen at bios a few times as well.  I did a little research on my hard drive model and apparently this is very common with my particular model.

---

