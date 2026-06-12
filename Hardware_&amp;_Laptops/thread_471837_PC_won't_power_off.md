---
title: "PC won't power off"
date: 2007-06-12
forum: Hardware &amp; Laptops
---

### Post by ethernet on 2007-06-12
Hello. I'm running Ubuntu 7.04. I go to shut down but it doesn't work. I'm just left with the Ubuntu logo on screen and have to hold down the power button to power off. I have the same problem with openSUSE 10.2 but this only happened now and again. Ubuntu seems to do it every time I boot. Come on! I've jumped ship to Ubuntu and I don't want to go back!

My motherboard is the Gigabyte GA-8I915P Duo Pro. I'm guess it's the cause of the problem. Any tips to investigate/improve the situation?

Many thanks.

---

### Post by neorou on 2007-06-12
I had a similar problem and the problem ended up being my power supply. It was a short or something, once it's on, it stays on...

If you have additional daughter cards it might be a good idea to unplug them one by one to see if they're the ones causing the shutdown to not work.

Did you do a web search on your motherboard and all of its related problems? Does it do the same thing with XP?

---

### Post by zek725 on 2007-06-12
> **ethernet said:**
> Hello. I'm running Ubuntu 7.04. I go to shut down but it doesn't work. I'm just left with the Ubuntu logo on screen and have to hold down the power button to power off. I have the same problem with openSUSE 10.2 but this only happened now and again. Ubuntu seems to do it every time I boot. Come on! I've jumped ship to Ubuntu and I don't want to go back!

My motherboard is the Gigabyte GA-8I915P Duo Pro. I'm guess it's the cause of the problem. Any tips to investigate/improve the situation?

Many thanks.

this might do the trick. [http://ubuntuforums.org/showpost.php?p=1933984&postcount=5](http://ubuntuforums.org/showpost.php?p=1933984&postcount=5)

---

### Post by ethernet on 2007-06-12
Thanks for all the replies.

zek725, I've added that text to menu.lst but it doesn't seem to have done the job. I have a Jeantech PSU.

neorou, I used to run XP and Vista RC2. No problem powering off there, I hate to say.

---

### Post by energiya on 2007-06-12
Take a look in the systemlog and see what part of the shutdown hangs.

---

### Post by as182005 on 2007-06-13
Hi,

I had a similar problem. I "solved" the problem, by unplugging my s-video cable from my graphics card. 

If you have such a cable connected to your graphics card you may give it a try.

---

