---
title: "VA250D Hi-Grade Notebook, HELP!!!!!!!"
date: 2008-06-19
forum: Hardware
---

### Post by lushden1988 on 2008-06-19
I have put it twice in the hope it show on the page if not click the first link to see my specs according to CPU-Z.

[img]http://i274.photobucket.com/albums/j...ipcat/cpuz.jpg[/img]


I am having trouble getting sound through headphones, and enabling the 3d desktop (my graphics card and accelerator)

Also i have my screen settings to 1440x900 resolution, but on the page where i sign in its completely different and its too stretched, so also how do i change this page as well to 1440x900.

My laptop is the Hi-Grade VA250D

[http://www.orfik.com/datoteke/Image/...50D-43_WEB.JPG](http://www.orfik.com/datoteke/Image/...50D-43_WEB.JPG)

Thats the link to my laptop.

But i dont have vista i have xp.

Please help people i have changed from ubuntu to mandriva to fedora so on and so on but i love ubuntu the most and cannot part from it

Cheers any advice i will be grateful on.

Oh all my drivers aparently are via i think my screen is via chrome9.

and sound is via hd vt82xx.

I think i am not sure lol

This is what i got told on Yahoo Answers.

[http://answers.yahoo.com/question/in...9160834AAQ8fkz](http://answers.yahoo.com/question/in...9160834AAQ8fkz)

Its the one i choose as best answer, but upon doing what the person said i didn't succeed, i dont think what he told me was very correct

What i really need is step by step how to guide please

Cheers again

---

### Post by lushden1988 on 2008-06-19
Sorry this is my specs

[http://i274.photobucket.com/albums/jj276/Shipcat/cpuz.jpg?t=1213886516](http://i274.photobucket.com/albums/jj276/Shipcat/cpuz.jpg?t=1213886516)

---

### Post by lushden1988 on 2008-06-19
SOMEONE HELP PLEASE ITS DRIVING ME MENTAL ](*,)

:popcorn:

---

### Post by veradotbash on 2008-12-28
Hi, I have a Hi-Grade VA250D laptop and I removed vista from it to dual boot Ubuntu and Win Xp. If you will send me details of your Bios setup particularly the page referring to the drives; DMA,UDMA, Smart Monitoring,32 bit addressing etc. What is enabled or disabled here is very important to this computer. There is also a known bug with the pheonixBios. I can help you. I will get right back to you after you send the details. Bon Courage. Vera

---

### Post by davidryderuk on 2009-02-13
Hi Vera, I also have the Hi-Grade VA250D and have found that the sound works after following the instructions shown in the link below, particularly post 4 (I tested it in intrepid after installing the build-essential package).

[http://ubuntuforums.org/showthread.php?t=556217](http://ubuntuforums.org/showthread.php?t=556217)

One point i was stuck on is the fan however, which never switches off in ubuntu and is quite irritating. As you seem to have explored the bios settings more than me (which haven't really been changed from their default on my computer) i was wondering if you know of any fix to this problem. The settings in my bios are shown below.

**Boot time diagnostic screen**  Disabled
**Frame Buffer size**   256Mb
**Display Device Selection**  LCD+CRT
**Local Bus IDE adaptor**  Both
**Legacy USB Support**  Enabled
**Lan Boot control** Disabled
**No Execute Mode Mem Protection** Enabled


**Type:** Auto
**LBA Format**
**Total sectors:** 156301488
**Maximum Capacity:** 80026MB
**Multi Sectors Transfers:** 16 Sectors
**LBA Mode control:** Enabled
**32 Bit I/O:** Enabled
**Transfer Mode:** FPIO 4/DMA 2
**Ultra DMA Mode:** Mode 5
**Smart Monitoring:** Enabled

Edit: I have now got fan control after using the dsdt file in the first link below. The instructions for getting ubuntu to use the dsdt file are shown in the second link below. 
[http://xoomer.virgilio.it/paolo.minazzi/dsdt.dsl](http://xoomer.virgilio.it/paolo.minazzi/dsdt.dsl)
[http://forums.linuxmint.com/viewtopic.php?f=42&t=20719](http://forums.linuxmint.com/viewtopic.php?f=42&t=20719)

:-)

---

