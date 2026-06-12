---
title: "(initramfs) issue"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by BAMF1501 on 2009-09-11
Ok when i go to select install ubuntu when booting from disc i get the try live disc or install i tried both but never got to main desktop just shows this 

(initramfs) unable to find a medium containing a live file system

what does that mean ?? how do i fix

---

### Post by BAMF1501 on 2009-09-24
would anyone know what this problem is it is only with live cd's ??

---

### Post by rreese6 on 2009-09-24
yes, run the CD check from the menu
seems like your cd is corrupted.
try burning another one from the ISO
using a slower speed 4x-8x.
then run the cd check again

---

### Post by BAMF1501 on 2009-09-27
i tried burning at slower speed still wont boot into it or any alternative no more only a alternative of 9.04 i have ;(

---

### Post by stlsaint on 2009-09-27
try redownloading the iso again and check the [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") then again burn at slowest speed as possible. Also are you using a livecd or only alternate cd?

---

### Post by presence1960 on 2009-09-27
> **stlsaint said:**
> try redownloading the iso again and check the [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") then again burn at slowest speed as possible. Also are you using a livecd or only alternate cd?

+1

if the checksum does not match exactly the iso is no good. it wont matter if you burn it at 1x.

---

### Post by BAMF1501 on 2009-09-27
correct the md5sum is incorrect should be 

5e0cc74559ea578fc19c39563f77f4fc *karmic-alternate-i386.iso


mine shows up as 
cbf48cc3d25b9b90fd1eaef96cb9bae5

i guess jsut download till i get correct one /?

---

### Post by presence1960 on 2009-09-27
> **BAMF1501 said:**
> correct the md5sum is incorrect should be 

5e0cc74559ea578fc19c39563f77f4fc *karmic-alternate-i386.iso


mine shows up as 
cbf48cc3d25b9b90fd1eaef96cb9bae5

i guess jsut download till i get correct one /?

try using a torrent download.

---

### Post by BAMF1501 on 2009-09-27
i tried downloading again and got correct md5sum ;0 


5e0cc74559ea578fc19c39563f77f4fc 

GONNA SEE IF ITS BOOTS PROPERLLY THEN WILL REPLY BACK WITH RESULTS THANKS GUYS!!

---

### Post by stlsaint on 2009-09-27
if issue is solved please mark thread as SOLVED! can simply add a tag and np on help....its what the community is for...pass it on!!

---

### Post by BAMF1501 on 2009-09-27
Nope its not :( it still says cannot detect cdrom during installation wth :( that was on a daily build and same with 8.10 disc that i got from ubuntu store

---

### Post by presence1960 on 2009-09-27
is your machine capable of booting from USB? If so why not use [unetbootin]("http://unetbootin.sourceforge.net/") to create a bootable USB version of the Live CD?

---

### Post by BAMF1501 on 2009-09-27
i tried that before and could never get working :(

---

### Post by MatthiasHeil on 2009-11-01
This is a terrible problem that has kept me from putting Ubuntu on my Netbook for weeks now - I've tried everything, even adding "all_generic_ide floppy=off irqpoll" suggested by (and apparently working for) many, does not solve the issue that seems to be a kernel problem.

Anybody who has got the answer, please post it here!

---

### Post by Stormspace on 2009-11-03
I have the same issue on mine. I'm going to try an alternate install CD tonight since it seems to be the live CD stuff that's crapping out.

---

### Post by PorcelainMouse on 2009-11-03
Yes, I think a corrupt download is what happened to me, too.

---

