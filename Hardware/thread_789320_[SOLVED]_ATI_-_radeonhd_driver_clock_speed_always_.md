---
title: "[SOLVED] ATI - radeonhd driver clock speed always 100%"
date: 2008-05-10
forum: Hardware
---

### Post by contremaitre on 2008-05-10
Hello

I have kubuntu 7.10 and ati 3850 with radeonhd opensource driver (the only one working).

My problem is : the graphic card is always in 3D mode and never 2D mode where it should lower its clock speed...
So the heat goes up (very hot with ubuntu and cool with windows)

any solution ?

thank you

---

### Post by contremaitre on 2008-05-10
sorry for double post

---

### Post by mtbsoft on 2008-05-11
Click the Report button beneath your details to the left of the post then ask the admins to delete the post in the subsequent screen - took me a while to work that one out too!

---

### Post by bapoumba on 2008-05-11
> **contremaitre said:**
> sorry for double post, dont know how to delete it
You must have got several automatic PMs from me, lucky you :popcorn:

I was under the impression that deleting the first post of a thread would delete the whole thread. I had actually never done that before, believe it or not. So I tried, and it did delete the thread.. Sorry. I undeleted it, it is going to stay that way if you do not mind :)

---

### Post by contremaitre on 2008-05-12
> **bapoumba said:**
>  it is going to stay that way if you do not mind :)

no problem...

---

### Post by contremaitre on 2008-05-13
up

---

### Post by contremaitre on 2008-05-14
up

---

### Post by ibargureni on 2008-05-14
Hi, I don't own that specific card, but my laptop has an ati x1400 and has the same problem. To turn the card into low power mode you must write "aticonfig --set-powerstate=1" into a terminal, at least in my pc. You can see the available modes of your card with "aticonfig --lsp". 1 is the lowest power mode and 3 is the most powerful one.

I have put two icons that put the card in states 1 and 3 in my taskbar so that I can change the power state easily. This way, when I am running on battery power I switch it to 1 and the power consumption decreases dramatically.

Edit: Sorry, I didn't realize that you are using the open source driver. I suspect this technique won't work with that driver. I am using the flgrx driver.

---

### Post by contremaitre on 2008-05-15
> **ibargureni said:**
> 
Edit: Sorry, I didn't realize that you are using the open source driver. I suspect this technique won't work with that driver. I am using the flgrx driver.

Well, I tried to use the fglrx driver, but in system preference, restricted driver it says : your hardware does not need any restricted driver so I can't use auto install.

I also tried to install it myself (from ati website version 8.4) but I have a black screen at boot

---

### Post by contremaitre on 2008-05-16
Solved !

I installed kubuntu 8.04 then ati drivers thanks to envyng, and it works fine... no more heating

---

### Post by Trollslayer on 2008-05-26
> **contremaitre said:**
> Well, I tried to use the fglrx driver, but in system preference, restricted driver it says : your hardware does not need any restricted driver so I can't use auto install.

I also tried to install it myself (from ati website version 8.4) but I have a black screen at boot

I had the same problem at first with my X1250 motherboard graphics.
It seemed it has troube ldetecting the monitor display modes over a long cable (EDID issues I think), a short cable and it was fine.
Also, the updated restricted driver is now fine.

---

