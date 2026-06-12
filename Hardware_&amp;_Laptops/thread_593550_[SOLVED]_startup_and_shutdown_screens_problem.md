---
title: "[SOLVED] startup and shutdown screens problem"
date: 2007-10-27
forum: Hardware &amp; Laptops
---

### Post by razinjap on 2007-10-27
Hi, I dunno, if this is a right place to post my problem, but lets try.
I had Ubuntu on my laptop for nearly a year and everything was cool before tft matrix got changed...
Now I see startup screen (which is supposed to show a progress bar and the Ubuntu logo) in about 10 colors and just in the corner of the screen and nasty lines and stripes instead of shutdown screen.
All the rest works fine but this stuff is very annoying.
Could someone help with advice?
Just in case I have RV350 (Mobility Radeon 9600 M10).

---

### Post by in-dust-rial on 2007-10-27
so you are useing gusty, right?

... well it seems like a lot of users have this problem, and the solution is wide speared.
( this is a kind reminder of the search options )

usplash resolution is MAYBE wrong detected!!!


do this stuff:
sudo vim /etc/usplash.conf
update-initramfs -u -k `uname´   
.end of stuff

i am not quite sure about the syntax of the second command, but you can search for the solution, if it does not work.

.xio

---

### Post by nick_h on 2007-10-27
```
sudo update-initramfs -u -k `uname -r`
```
for the second command.

---

### Post by razinjap on 2007-10-28
thank you for your kindness =) but i'm well aware of this trick. It helps only with resolution of the startup screen but doesn't fix the rest of the problem. Any other suggestions? =)

---

### Post by razinjap on 2007-10-28
oh, and...:)  yes, now i'm using 7.10 but it started with 7.04 after the tft matrix was changed.

---

### Post by jenhsun on 2007-10-28
> **razinjap said:**
> Hi, I dunno, if this is a right place to post my problem, but lets try.
I had Ubuntu on my laptop for nearly a year and everything was cool before tft matrix got changed...
Now I see startup screen (which is supposed to show a progress bar and the Ubuntu logo) in about 10 colors and just in the corner of the screen and nasty lines and stripes instead of shutdown screen.
All the rest works fine but this stuff is very annoying.
Could someone help with advice?
Just in case I have RV350 (Mobility Radeon 9600 M10).

go to [www.getdeb.net](www.getdeb.net) and try to find a deb called startupmanager
and please report your result to everyone.

---

### Post by razinjap on 2007-10-29
here is the result... =(
the drop down menu in start-up manager does not have the option with the native resolution of my screen which is 1280x856. 
is there any way to put it manually?

---

### Post by jenhsun on 2007-10-30
> **razinjap said:**
> here is the result... =(
the drop down menu in start-up manager does not have the option with the native resolution of my screen which is 1280x856. 
is there any way to put it manually?

I think you can just use 1024X768
I used to play with the startupmanager...but crash my startup screen.
By the way, it's just a screen startup, system use generic graphic card driver, not your "ATI" or "Nvidia" to load the startup until you have your login screen.

---

### Post by razinjap on 2007-10-30
i crashed the startup screen also. =)
sorry, guys, i gave up and installed the 7.04. 
now it works fine and the problem is somehow fixed by the magic of Ubuntu i guess. =)
thanks for help.

---

