---
title: "Can someone help me interpret this??"
date: 2010-01-13
forum: Hardware
---

### Post by hortstu on 2010-01-13
So intel has this download to allow the capacity of hard drives larger than 137GB to be recognized by the windows operating system.

I'm trying to figure out if this is going to be an issue on my 100% linux laptop. Intel doesn't seem to have this update available for linux. Will I be able to use a HD larger than 137GB without partitioning it or should I just stick with a 100 or 120?

Thanks

---

### Post by MyR on 2010-01-13
This is not an issue with any modern operating system.

---

### Post by lisati on 2010-01-13
> **MyR said:**
> This is not an issue with any modern operating system.

+1. My laptop (which I've had over a year) handles over 137Gb without a problem.

---

### Post by hortstu on 2010-01-13
> This is not an issue with any modern operating system.

OK well I didn't think it was the operating system so much as the BIOS that was the limiting factor.  The computer was buil in the middle of 2005 and the last BIOS update was also from then.  Are you telling me that I can go as big as I want with the hard drive?

---

### Post by roadtripdave on 2010-01-13
Pretty much yes as long as your using linux, Win 2000 Service Pack 3 or later or Win XP Service Pack 1 or later... Since your 100% linux.. no worries, go as big as you want.

Info Link [http://www.intel.com/support/motherboards/desktop/sb/CS-020811.htm#sizelimit]("http://www.intel.com/support/motherboards/desktop/sb/CS-020811.htm#sizelimit")

---

### Post by Sef on 2010-01-13
> OK well I didn't think it was the operating system so much as the BIOS that was the limiting factor. The computer was buil in the middle of 2005 and the last BIOS update was also from then. Are you telling me that I can go as big as I want with the hard drive?

Yes.  That problem was resolved around 2002/3.

---

### Post by hortstu on 2010-01-16
Well I recieved a 160 gb hd today and installed it.  It only shows up as 137 so apparently it doesn't matter if it is linux or xp.  

If it all shows up in gparted I will try to split it into 80 and 80 or something and make use of the whole drive.

Thanks for any help again.

---

### Post by Vakman on 2010-01-16
> **hortstu said:**
> Well I recieved a 160 gb hd today and installed it.  It only shows up as 137 so apparently it doesn't matter if it is linux or xp.  

If it all shows up in gparted I will try to split it into 80 and 80 or something and make use of the whole drive.

Thanks for any help again.

It does not matter. You still have a 160GB drive.
Manufacturers like WD or Seagate sell the drive based on the fact that 1GB=1000MB & 1MB=1000kb as examples.
Hard drives are formatted like this: 1GB=1024MB & 1MB=1024kb. So really, you are losing nothing.
The space you are getting sounds about correct.

---

### Post by JackRock on 2010-01-17
Linux or Windows does not limit the hard drive space to any current technology (any more).  If it WERE the bios that limits the amount of HDD space it recognizes, it wouldn't matter what operating system you had.

But, as it is, any current operating system will recognize well over 1TB, much less 137gb.

---

### Post by pirateghost on 2010-01-17
there is, however, a chance that the LBA setting in BIOS is wrong.  a 160gb drive should show up as 149gb

---

### Post by falconindy on 2010-01-17
> **Thisislaw said:**
> It does not matter. You still have a 160GB drive.
Manufacturers like WD or Seagate sell the drive based on the fact that 1GB=1000MB & 1MB=1000kb as examples.
Hard drives are formatted like this: 1GB=1024MB & 1MB=1024kb. So really, you are losing nothing.
The space you are getting sounds about correct.
No, it's not correct. 

160GB * 1000 ^ 3 / 1024 ^ 3 = ~149GiB

137gb is the barrier of LBA disk addressing, not the amount of space on a 160GB (not GiB) drive.

OP: It's not that you can't read a partition larger than 137GB, it's that you can't read PAST the 137GB marker on a drive. Splitting a 160GB drive into 2 pieces would leave you with 80GB and 57GB partitions. You need to find yourself a BIOS update for your motherboard.

---

### Post by JackRock on 2010-01-17
> **pirateghost said:**
> there is, however, a chance that the LBA setting in BIOS is wrong.  a 160gb drive should show up as 149gb

Yes, and that seems it might be the case here, per falconindy's post.  My statement was just saying that it wouldn't matter these days if it was Windows or Linux, since the OS-specific limitations are beyond almost all commercially available hard drives.

---

### Post by hortstu on 2010-01-17
> **JackRock said:**
> Linux or Windows does not limit the hard drive space to any current technology (any more).  If it WERE the bios that limits the amount of HDD space it recognizes, it wouldn't matter what operating system you had.

But, as it is, any current operating system will recognize well over 1TB, much less 137gb.

Well then it must be the BIOS because I'm running hardy heron and I'm still seeing only 137.

> there is, however, a chance that the LBA setting in BIOS is wrong. a 160gb drive should show up as 149gb

I'm pretty sure after all the reading I've done that this 137 thing is normal with the computer or the BIOS that I have.  I think you're right about the LBA setting... 

[QUOTE=falconindy]You need to find yourself a BIOS update for your motherboard.[/QUOTE]

but that would require a BIOS update and this system has the most current update.  That was however back in 2005.  They just didn't make one for this motherboard I guess.

---

### Post by gabo.cr on 2010-01-17
I know the BIOS will recognize only a certain amount of space, doesn't matter how big the HD is.
The OS will do whatever the BIOS says about the HD.

---

