---
title: "Problems installing Ubuntu 9.04 (Help)"
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by bloodytanga on 2009-07-20
Hi there, some days ago I finally decided to give ubuntu a shot because I was very interested in everything it offers. So I decided to download it an install it as my onely OS. I downloaded it from the official website an burned it into a CD-R. But here comes the problem, every time i run the CD it appears the first menu in which you select the language and then chosse if you want to try it, install it, etc. so i choose langage, choose to install it (or try it, or check if the cd is wreong, anything I press gives me the same result) so it appears a black screen in which after some seconds appears two error codes:

[12.192007]ate3: SRST failed (errno=-16)
[22.204007]ate3: SRST failed (errno=-16)

After that happens the loading image from Ubuntu starts and after some seconds a black screen with both errors appears and in the buttom says:
BusyBox v1.10.2 (Ubuntu 1:1.10.2-2 Ubuntu7) built-in shell (ash)

So I could never install it or try it in my computer. I checked if the disck was right on other computers I have at home and it works just fine. Could someone help me out?

My computer has:
Campo    Valor
Asus K8V-MX
AMD Sempron, 1600 MHz (8 x 200) 2600+
512MB RAM
Campo    Valor
nVIDIA GeForce FX 5500
ATA HDS728080PLAT20

---

### Post by presence1960 on 2009-07-20
[boot options]("https://help.ubuntu.com/community/BootOptions")

or [alternate CD]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

---

### Post by bloodytanga on 2009-07-20
so what should I change to make it work?

---

### Post by presence1960 on 2009-07-20
> **bloodytanga said:**
> so what should I change to make it work?

I would try safe graphics mode first. If all else fails you can download the alternate text based installer and use that.

But did you...

MD5SUM the iso you downloaded prior to burning the image to CD? [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

Did you burn the CD at the slowest possible speed (4x is perfect)?

After you boot the Live CD did you choose "check disk for defects"?

---

### Post by bloodytanga on 2009-07-20
yes, i did all that and besides i checked the CD with other 2 computers in which it forcked perfectly fine, now i'll try the safe graphics and tell you what happens

---

### Post by bloodytanga on 2009-07-20
so, i tried the secure graphic mode and the same happened... I'll try the alternate cd then

---

### Post by bloodytanga on 2009-07-20
nothing happened witth the alternate cd, i mean it couldnt mount the cd or something like that

---

### Post by redspider on 2009-07-20
is the architecture correct? i686 or i383 or x86 or other options.
make sure boot from disk is enabled in BIOS. usually on of the F keys in the first splash screen . usually f1 or f2.
more information as long as its not case sensitive is always better.
what do you mean wouldn't mount?

---

### Post by bloodytanga on 2009-07-20
the boot from disck is enabled in BIOS, I know cause i always have to format my computer... when y used the alternate it said that the disc couldn't be read or mounted or something like that, what you mean by the architecture being right?

---

### Post by Sef on 2009-07-20
> what you mean by the architecture being right?

Do you have an architecture that Ubuntu is made for, e.g., i386, AMD64?  

> when y used the alternate it said that the disc couldn't be read or mounted or something like that,

A couple of ideas, if all has checked out ok:

1) Bad CDs - get some new ones

2) Bad CD drive

If you put the alternate cd in another computer does it boot up?  (Don't install on the other computer, just check that it boots into it.)

---

### Post by bloodytanga on 2009-07-20
how do I know if the architecture is made for ubuntu?

---

### Post by presence1960 on 2009-07-20
> **bloodytanga said:**
> how do I know if the architecture is made for ubuntu?

you want to match your CPU with the correct Ubuntu. if you have a 64 bit capable CPU then you want AMD64 Ubuntu. otherwise x86 is what you want.

---

### Post by bloodytanga on 2009-07-20
and how do i know which ubuntu i am downloading?

---

### Post by presence1960 on 2009-07-20
> **bloodytanga said:**
> and how do i know which ubuntu i am downloading?

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Under custom options choose 32 bit or 64 bit

---

### Post by bloodytanga on 2009-07-20
thanx, i hadn'r realize about that, I hope it works now

---

### Post by bloodytanga on 2009-07-20
same hapened

---

