---
title: "gutsy nvidia quadro nvs 140m"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by bobotoes on 2007-10-20
I'm thinking about getting a laptop with an nvidia quadro nvs 140m graphics card. Will this card work "out of the box" with gutsy? Are the restricted drivers stable and is the 3D acceleration good? Does compiz work? I prefer to do everything through the ubuntu repositories.

---

### Post by patterbt on 2007-10-21
The answer to your question is no, the quadro will not work "out of the box".  I have a brand new dell latitude D630 with a quadro NVS 135M and the only way I can even get the video to work at all on the live CD is to boot into safe mode.  (Safe mode uses the "vesa" driver).  

I have heard that you can get it working by downloading and installing the proprietary Nvidia driver; but I have not tried this yet (as the laptop is my work laptop) since I am running off the live CD.  I don't know if there is a list somewhere of "out of the box" supported video cards.  Perhaps someone else will know this.

---

### Post by GoGoGadgetFeet on 2007-11-11
I'm running the livecd on a Dell Latitude D630 right now (trying to make a case for my company letting me use Ubuntu instead of WinXP).  I chose "start or install Ubuntu", but I had to manually kill gdm and restart it in order to get to the desktop.

$ ps -A | grep gdm
8386 ?              00:00:00 gdm
$ sudo kill -9 8386
$ sudo /etc/init.d/gdm start

And then the desktop comes up with the correct resolution using the free nv driver.

If you were to install Ubuntu, I'm fairly sure that the restricted drivers manager would install both the nvidia driver and the bcm43xx firmware for you.  There's a slight chance that you'd have to use the above trick the first time you start up.  If I try it, I'll let you know.

-Richard

---

### Post by KC9EVP on 2007-11-13
I was able to get my T61 working, mind you it was not"out of the box". I had to install in safe graphics mode. After installing Ubuntu, the restricted drivers app found the updated nVidia driver. After installing and rebooting, I got it all operational including compiz fusion. Hope this helps.

---

