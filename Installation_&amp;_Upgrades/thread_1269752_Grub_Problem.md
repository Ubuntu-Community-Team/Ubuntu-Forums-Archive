---
title: "Grub Problem"
date: 2009-09-18
forum: Installation &amp; Upgrades
---

### Post by lightzout on 2009-09-18
So i have following problem: I have installed Ubuntu 9.04 and wndows 7 installed on my laptop. when i try to start windows it just gives me a weird error message and windows won't start at all. 

Any adivce?

regards Pascal

---

### Post by raymondh on 2009-09-18
> **lightzout said:**
> So i have following problem: I have installed Ubuntu 9.04 and wndows 7 installed on my laptop. when i try to start windows it just gives me a weird error message and windows won't start at all. 

Any adivce?

regards Pascal


Pascal,

Did you install windows after ubuntu.  If so, you'll need to recover/re-install GRUB.  If not, what exactly are the error messages?

To recover grub, boot into the liveCD and in live session (try ubuntu...).  Access a terminal (applications > accessories) and type one at a time :

**sudo grub**  [COLOR="DarkRed"]you will get a grub prompt that looks like grub >[/COLOR]
**find /boot/grub/stage1**  [COLOR="DarkRed"]note what it outputs which we'll say hdX,Y[/COLOR]
**root (hdX,Y)**  [COLOR="DarkRed"]use what the previous command  result[/COLOR]
**setup (hd0)** [COLOR="DarkRed"] assuming you only have 1 HD[/COLOR]
**quit**

Good luck.  Post back errors or success.

Raymond

---

### Post by gjtoth on 2009-09-19
> **raymondhenson said:**
> Pascal,

Did you install windows after ubuntu.  If so, you'll need to recover/re-install GRUB.  If not, what exactly are the error messages?

To recover grub, boot into the liveCD and in live session (try ubuntu...).  Access a terminal (applications > accessories) and type one at a time :

**sudo grub**  [COLOR="DarkRed"]you will get a grub prompt that looks like grub >[/COLOR]
**find /boot/grub/stage1**  [COLOR="DarkRed"]note what it outputs which we'll say hdX,Y[/COLOR]
**root (hdX,Y)**  [COLOR="DarkRed"]use what the previous command  result[/COLOR]
**setup (hd0)** [COLOR="DarkRed"] assuming you only have 1 HD[/COLOR]
**quit**

Good luck.  Post back errors or success.

Raymond


This worked brilliantly for me after a bombed install of 9.10 broke my grub.  THANKS!!

---

### Post by raymondh on 2009-09-19
> **gjtoth said:**
> This worked brilliantly for me after a bombed install of 9.10 broke my grub.  THANKS!!

Excellent ... happy ubuntu-ing :)

---

### Post by raymondh on 2009-09-19
> **lightzout said:**
> So i have following problem: I have installed Ubuntu 9.04 and wndows 7 installed on my laptop. when i try to start windows it just gives me a weird error message and windows won't start at all. 

Any adivce?

regards Pascal

Am re-reading your initial post ... can you post back output (from terminal)

```
cat /boot/grub/menu.lst
```

You may have to re-map windows into thinking it is FIRST/PRIMARY in the drive.

---

### Post by Claus7 on 2009-09-19
Hello,

it seems that *raymondhenson* knows well the issue. I just wanted to add this site from *Herman*:
[http://members.iinet.net.au/~herman546/p15.html](http://members.iinet.net.au/~herman546/p15.html)

who is "guru" in the grub and dual booting issues and this site comprises a lot of helpful information, so if else fails, you can check this out as well. 

It would be also nice to write on a piece of paper the error you see while booting. That way it will be easier to find out a solution.

Regards!

---

