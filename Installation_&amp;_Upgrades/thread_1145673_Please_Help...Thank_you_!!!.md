---
title: "Please Help...Thank you !!!"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by stormypenny on 2009-05-01
I have an older Dell using Windows XP. I just installed Ubuntu 8.10. I log in using my User Name and Passord. Then the screen goes black. The round ball stop rotating. What is wrong and how do I fix it. I am a newbie...

Thanks in advance.

SP

---

### Post by abn91c on 2009-05-01
what model? if it has an intel 845 video card do this press ctr+alt+f1, then at the command prompt run this commands```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
``` then startx

---

### Post by stormypenny on 2009-05-01
How do I get to the command prompt?

Thanks,
Sp

---

### Post by abn91c on 2009-05-01
> **stormypenny said:**
> How do I get to the command prompt?

Thanks,
Sp
press [COLOR="Red"]ctr[/COLOR][COLOR="Blue"] alt[/COLOR] and[COLOR="Green"] f1[/COLOR] keys at same time
after you enter the commands it will ask for your password enter it then run them one at a time, select [COLOR="green"]yes[/COLOR] when asked "do you want to continue" or similar prompt

---

### Post by stormypenny on 2009-05-01
Sorry, I am a newbie. At what point do I hit those keys? What stage of the start up? Because I partioned the hard drive, I get a choice of windows or Ubuntu. I pick Ubuntu and hit enter. Then???

Thanks so much.
SP

---

### Post by abn91c on 2009-05-01
> **stormypenny said:**
> Sorry, I am a newbie. At what point do I hit those keys? What stage of the start up? Because I partioned the hard drive, I get a choice of windows or Ubuntu. I pick Ubuntu and hit enter. Then???

Thanks so much.
SP
yes Ubuntu when you get to the blank screen you should be able to do it

---

### Post by sailthesea on 2009-05-01
When you are booted into Ubuntu as far as it goes anyway, then do the above You should get somewhere Looks like your upgrade didn't quite complete

---

