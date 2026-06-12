---
title: "Blank Screen while installing Ubuntu 9.04 64 bit"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by kiranvarma_2000 on 2009-08-20
I am trying to install Ubuntu desktop 64bit through CD. I have connected the computer to TV through VGA.
 
I could see Ubuntu getting loaded and it goes black. TV does not get any signal.
 
However it booted to Ubuntu Live CD since that is the default.
 
Again when I hit power off button I could see the Unbuntu unloading.
 
 
Seems to be driver issue, I have got Integrated Matrox G200.
 
I have searched for many forums, I didnt find any solution to this issue.
 
I am new to Unbuntu, could someone help me with this.
 
Thanks, Kiran.

---

### Post by kiranvarma_2000 on 2009-08-20
Here is my system configuration.
 
[http://www.dell.com/downloads/global/products/pedge/en/server-poweredge-t410-specs-en.pdf](http://www.dell.com/downloads/global/products/pedge/en/server-poweredge-t410-specs-en.pdf)

---

### Post by razorboy5 on 2009-08-20
Hi
 
seems that many people are having this problem
 
also it seems that xorg.conf is the culprit not the driver
 
will post more if i find anything else useful
 
sry i'm not really pro at Ubuntu, i just try to help ppl by googling lol...;

---

### Post by presence1960 on 2009-08-20
[Boot Options]("https://help.ubuntu.com/community/BootOptions") Scroll down to the section dealing with F4. You want to try safe graphics mode when installing.

if that fails try [alternate text based installer]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

---

### Post by razorboy5 on 2009-08-21
heard alot of people saying lower the resolution see if that helps

not a permanent fix but better than nothing at the moment

---

### Post by kiranvarma_2000 on 2009-08-21
I tried safe mode and many vga combinations. TV throws warning that mode is not supported and shows list of modes. I tried all of them none works.

---

### Post by kiranvarma_2000 on 2009-08-21
I am hoping changing TV and getting a monitor would help. Any suggestions. Do you want me to lower the resolution of TV and then try to install?

---

### Post by kiranvarma_2000 on 2009-08-21
But when I tried to boot with red had linux 5 it recognizes Matrox G200 and the resolution 800*600 was automatically set and it works.

---

