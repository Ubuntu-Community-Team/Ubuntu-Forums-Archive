---
title: "GRUB Error"
date: 2008-09-14
forum: General Help
---

### Post by putnam120 on 2008-09-14
I have recently tried to install Ubunto 8.04 onto my portable hard drive. However, things didn't work out so well (I am currently using the live CD). 

When I tried to boot back into Windows I keep getting an MBR error message or something like that. 
After searching form and google I found a solution but they didnt seem to help since i still have the problem. 

So far I have tried 
```
sudo apt-get install ms-sys
```

but keep getting this error message
```
E: Couldn't find package ms-sys
```

Does anyone know how to get around this problem?
I don't know if it helps or not but I am trying to access Windows Vista.

---

### Post by TeoBigusGeekus on 2008-09-14
Would this be of any help?
[http://ge.ubuntuforums.com/showthread.php?t=891118]("http://ge.ubuntuforums.com/showthread.php?t=891118")

---

### Post by putnam120 on 2008-09-14
Thanks. I'm going to try downloading the Vista Recovery CD. Hopefully that will work.

---

### Post by putnam120 on 2008-09-14
The CD kind of worked. 
For some reason, I can now boot either Ubuntu or Vista as long as I have the external hard drive connected to my laptop. However, if it is not then I still get the same error message as before.

---

### Post by caljohnsmith on 2008-09-14
> **putnam120 said:**
> The CD kind of worked. 
For some reason, I can now boot either Ubuntu or Vista as long as I have the external hard drive connected to my laptop. However, if it is not then I still get the same error message as before.
So are you getting the Grub menu on start up now where you can choose Vista or Ubuntu? If that is true, what's happening is that Grub is installed to the master boot record (MBR) of your internal drive, which you boot on startup, but Grub's system files (like menu.lst) are located on your external drive. Thus when you disconnect the external HDD you can no longer boot. If this is your case, probably the best solution would be to put a Windows boot loader back in the MBR, and then use a program like EasyBCD so you can set up your Vista boot loader to boot either Vista or Ubuntu. See these links for EasyBCD:

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

And to put Windows back in the MBR, you can run:
```
bootrec /fixmbr
```
from the Vista Recovery CD you downloaded. Let me know how it goes, or if you need more info/details.

---

### Post by DOSIX on 2008-09-14
boot in with the external hard drive, then go to a terminal and put fdisk -l
once you do that, there should be a column that says active, and underneath one of those entries, there should be a star under the windows hard drive (usually /dev/sda
locate the active one, which should be /dev/sda, and type at a terminal
sudo grub-install /dev/sda

that should work, i had the same problem on my flash drive ubuntu install.

---

### Post by putnam120 on 2008-09-14
```
bootrec /fixmbr
```
Am I correct in assuming that after booting from the CD I the command prompt and enter this code?

Also is EasyBCD a program that I run from inside Vista or Ubuntu?

---

### Post by caljohnsmith on 2008-09-14
> **putnam120 said:**
> ```
bootrec /fixmbr
```
Am I correct in assuming that after booting from the CD I the command prompt and enter this code?
Yes. :)

---

### Post by putnam120 on 2008-09-14
Thanks a bunch! Now I can boot Vista and Ubuntu (from the HDD) with no problems.

---

