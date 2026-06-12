---
title: "Installation help"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by james1991 on 2009-08-06
hi im trying to install Ubuntu desktop 9.04 from a CD but i keep geting "I/O Boot Error"
it doesn't say why just promts me to reboot. i tryed to check the dick same thing i have no idea what to do. my computer specs are:
[SIZE=2][U][B]
OS[/B][/U]
Windows XP Home Edition Service Pack 3 (build 2600)
[U][B]
Processor[/B][/U]
[/SIZE][SIZE=2]2.30 gigahertz AMD Phenom 9600 Quad-Core
512 kilobyte primary memory cache
2048 kilobyte secondary memory cache
64-bit ready
Multi-core (4 total)
Not hyper-threaded[/SIZE]
[U][B]
Motherboard[/B][/U]
[SIZE=2]Board:  ALiveNF7G-FullHD R3.0
Bus Clock: 200 megahertz
BIOS: American Megatrends Inc. P1.10 04/11/2008[/SIZE]
[U][B]
Hard Drives[/B][/U]
[SIZE=2]500.11 Gigabytes Usable Hard Drive Capacity
454.91 Gigabytes Hard Drive Free Space

Optiarc DVD RW AD-7170A [CD-ROM drive]

ST3250310AS [Hard drive] (250.06 GB) -- drive 0, [SMART]("http://www.belarc.com/smart.html") Status: Healthy
ST3250310AS [Hard drive] (250.06 GB) -- drive 1, [SMART]("http://www.belarc.com/smart.html") Status: Healthy
[/SIZE]

_**Ram**_
[SIZE=2]3328 Megabytes Usable Installed Memory

Slot 'DIMM0' has 2048 MB
Slot 'DIMM1' is Empty
Slot 'DIMM2' has 2048 MB
Slot 'DIMM3' is Empty[/SIZE]

_**Display**_
[SIZE=2]NVIDIA GeForce 9800 GT [Display adapter]
Hanns.G HB175 [Monitor] (17.2"vis, s/n 825BC3NA02387, June 200[/SIZE]

P.S. sorry if its to much informationo i didn't know what you needed

---

### Post by NotJustANewbie on 2009-08-06
This could be a number of problems... I/O means Input/Output.
Therefore, I would recommend burning the ISO again at a lower speed (lets say x2 or x4 speed).
Before you do that though, when does its give this error? Once it is installed? Or before you install? At which point does it say this?

---

### Post by james1991 on 2009-08-06
At the start up screen when ever i select a link, after it starts to load

---

### Post by stlsaint on 2009-08-06
yes this can be from many reasons...last time i encountered the same error while trying to use ubuntu christian edition and all i did was burn the same iso at a lower speed like as mentioned above!

---

### Post by NotJustANewbie on 2009-08-06
> **stlsaint said:**
> yes this can be from many reasons...last time i encountered the same error while trying to use ubuntu christian edition and all i did was burn the same iso at a lower speed like as mentioned above!

Yeah :)
So try at a lower speed.. can you post the result please, I'm quite interested to see what happens.

EDIT: Btw, nice computer spec ;)

---

### Post by james1991 on 2009-08-06
i try it at x1 x2 and x4 and still same result. if it helps any a number pops up in the top left corner when the error msg comes up. 104200ef
and thank you its my baby im saving up to install liquid cooling so i can overclock safely (safety first lol)

---

### Post by NotJustANewbie on 2009-08-06
Okay, what you need to do is check the md5sum with the burned image on 1x or 2x cd. If it is different, then you need to check it with the .iso you downloaded on the hard disk. If this is different, then you need to redownload the image from ubuntu.com and check the md5sum on the harddrive.
Once you have the same md5sum as the official md5sum on your harddrive, burn it to cd at 2x and try to install again.

---

### Post by james1991 on 2009-08-06
ok hate to sound uneducated but i had no idea what you just said....

---

### Post by Raygreen on 2009-08-06
I don't know if this will help, but I had problems on this computer getting Ubuntu 9.04 to load, I had burnt the disk 3 times. It loaded fine on 2 other computers, and I could run it on this computer from the CD, it would just error when I tried to put it on the computer as the only operation system. 

I don't know if your trying to get it to dual boot with Windows or running it with Wubi inside Windows?

What finally worked for me, was going all the way back to Ubuntu 7.10 and that loaded then I upgraded up to 9.04. I could not get Ubunutu 8.10 to work either. But by upgrading from 7.10 to 8.04 then 8.10 then 9.04 I am now functioning at the most up to date version. Hope this helps some.

---

### Post by Partyboi2 on 2009-08-06
> **james1991 said:**
> ok hate to sound uneducated but i had no idea what you just said....
Check the md5sum's of the download iso. See [[COLOR=Blue]here[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM").

---

### Post by james1991 on 2009-08-06
ok the md5sum's are differnt the one i downloaded is the same as the one on the web site but the cd has a different one what do i do?

---

### Post by NotJustANewbie on 2009-08-06
Ok, you now need to burn the correct md5sum on to cd and it should work... make sure you use a low speed again - 4x should be okay :)

---

### Post by Partyboi2 on 2009-08-06
> **james1991 said:**
> ok the md5sum's are differnt the one i downloaded is the same as the one on the web site but the cd has a different one what do i do?
Try using a different burning program like [[COLOR=Blue]imgburn[/COLOR]]("http://www.imgburn.com/") and as mentioned burn at x4 or less.

---

### Post by james1991 on 2009-08-14
ok, i tried different burning program at different speeds and then i got the CD from ubuntu and still same problem!
help plz

---

### Post by presence1960 on 2009-08-14
> **james1991 said:**
> ok, i tried different burning program at different speeds and then i got the CD from ubuntu and still same problem!
help plz

try the [alternate text based installer]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

---

### Post by andycourgette on 2009-09-20
I got the same error code when trying to install 9.04 and 8.04. The CD runs smoothly on a different computer. I did the CD check option and it did not encounter no errors.

I will try the text-based installer and if that doesn't work install 7.10 as was suggested. 

I will post here if there is any luck. :popcorn:

---

### Post by Partyboi2 on 2009-09-20
> **andycourgette said:**
> I got the same error code when trying to install 9.04 and 8.04. The CD runs smoothly on a different computer. I did the CD check option and it did not encounter no errors.

I will try the text-based installer and if that doesn't work install 7.10 as was suggested. 

I will post here if there is any luck. :popcorn:
Gutsy 7.10 has reached its end of life, you would be better of trying to install a later release.

---

### Post by andycourgette on 2009-09-20
> **Raygreen said:**
> **What finally worked for me, was going all the way back to Ubuntu 7.10 and that loaded then I upgraded up to 9.04. I could not get Ubunutu 8.10 to work either. But by upgrading from 7.10 to 8.04 then 8.10 then 9.04 I am now functioning at the most up to date version. Hope this helps some.**

I am referring to the solution earlier posted by Raygreen (see quote); installing 7.10 and then upgrade the whole way to 9.04. If I could install 9.04 or 8.04 I would. However, I get an I/O error (104200ef) when I run the installation CD, both for 8.04 and 9.04. I am now trying with the alternate 9.04 CD.

---

### Post by andycourgette on 2009-09-20
Alternate distribution solved the problem for me!

---

### Post by presence1960 on 2009-09-20
Glad you got it working!

The alternate text based installer usually works where the Live CD will not. It is a more powerful installer anyway, as it has support for more options than the Live CD. It isn't as pretty as the Live Cd and you can't run a Live session but in my opinion that is not needed. I want an installer to install and have support for the things one may need such as RAID & LVM.

---

