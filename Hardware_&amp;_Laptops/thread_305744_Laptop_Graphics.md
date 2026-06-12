---
title: "Laptop Graphics"
date: 2006-11-23
forum: Hardware &amp; Laptops
---

### Post by davebradford on 2006-11-23
Just installed Egdy on my old laptop! Run's great apart from the graphics, everything is fine and looks ok but my main problem is scolling in windows where i get a lot of lag, i'm using an old laptop with onboard graphics S3 i think it's called. Does anybody know if i can find these S3 drivers for linux? Or if anyone can suggest a fix using stock drivers i'm all ears!

Dave

---

### Post by zgornel on 2006-11-24
Check /etc/X11/xorg.conf, Section Device and see what Driver it uses. Old models of the S3 are supported by the X server natively. Specs of the laptop ? Might wanna take a look here [http://www.die.net/doc/linux/man/man4/s3virge.4.html](http://www.die.net/doc/linux/man/man4/s3virge.4.html) (for old virge cards)

---

### Post by davebradford on 2006-11-25
on inspection of my xorg.conf file, i find the following section:

Section "Device"
                  Indentifer                "Generic Video Card"
                  Driver                      "vesa"
                  BusID                      "PCI:1:0:0"
EndSection

Does this mean it has not found my graphics card and is using a different driver? How can i get it to detect the card from my laptop which is an S3? I can get a display which works fine, but scrolling is very choppy like on a fresh install of windows xp without graphics card drivers!! LOL!

Thanks guys :)

---

### Post by houstonbofh on 2006-11-25
S3 is a company.  (Well, was a company)  You need to know what chipset it is.  Then check [http://www.die.net/doc/linux/man/man4/](http://www.die.net/doc/linux/man/man4/) when you know.

---

### Post by zgornel on 2006-11-26
Watch in the results of *lspci*, it should be there.

---

### Post by davebradford on 2006-11-26
i found out that i have an S3 ProSavage DDR in my laptop, i edited xorg.conf and replaced vesa, for "savage" worked straight away! Full graphic's acceleration!!! Love it!! Thanks so much guys, the ubuntu community rocks!!!!!

---

### Post by houstonbofh on 2006-11-26
> **davebradford said:**
> i found out that i have an S3 ProSavage DDR in my laptop, i edited xorg.conf and replaced vesa, for "savage" worked straight away! Full graphic's acceleration!!! Love it!! Thanks so much guys, the ubuntu community rocks!!!!!
The only thing we ask is that you spend some time sharing the knowledge you now have.  And the fact that armed with the chipset type you did not need anymore help shows you have a lot of knowledge to share. :D

---

