---
title: "[SOLVED] Optical Drive Issues After Edgy Upgrade"
date: 2007-02-08
forum: Hardware &amp; Laptops
---

### Post by mocoloco on 2007-02-08
Since upgrading to Edgy a few months back my two optical drives have both had issues.  The drives are
SAMSUNG DVD-ROM SD-616
LG CD-RW CED-8080B

Both will read CDs fine. My DVD-ROM drive will not read DVDs and locks up on trying to read one, and no CTRL+ALT+(Backspace|F1-F5) or anything will respond and I have to poweroff.
The CD-RW simply won't burn, it asks for a blank disc when one is already inserted.
Both drives worked fine under Dapper and under WinXP so I know the hardware's ok.  I first had installed Edgy fresh (I love having a /home partition :) ) and after noticing the issue and not finding a solution I reinstalled Dapper, thinking that upgrading from Dapper hopefully it wold keep the same hardware setup and no screwups would occur, but alas they did.
I've been able to use DVD and CDR on my laptop so I've not taken time to look at it until now but I really don't know what else to do to troubleshoot.  If I boot with a Dapper live or Knoppix I can burn discs but booting an Edgy (K/X)Ubuntu the same issue occurs with the burner.
What's really crazy is if I boot with an Edgy live DVD everything works fine, although it is noticably slower than with a CD which makes me think it's still not using the right driver or something.
Using the excelent app hardinfo (not the one in the repos but a newer version from autopackage) it says the DVD-ROM's drive is "Generic mmc2 DVD-ROM".  The CD-R shows no driver info.  I would like to compare drivers to what dapper loads for these driver but don't know where to look.  Thanks in advance.

---

### Post by mocoloco on 2007-03-20
Update on this, I upgraded to Feisty (which is very cool by the way) and still have the same issue with these drives.  I decided to do some testing and installed PCLinuxOS 0.93 on a second hard drive, and it seems to detect both drives fine, I can read DVDs and write to CDs.
I tried copying lines from /etc/fstab but that was a no go.  Is there something in the PCLOS install I can compare to find out what to change under Ubuntu, some other config file or module that's being loaded?
I've googled for answers and just don't know enough about Linux harware drivers and modules to be able to trouble shoot this.  
Thanks to anyone who can point me in the right direction.

---

### Post by mocoloco on 2007-09-06
Just closing off my thread.  I solved this a while back, for the DVD drive I hadn't installed libdvdcss2, and the optical drive thing turned out to be an issue with Nautilus CD Burner, not the drive.  I can burn with Gnomebaker.

---

