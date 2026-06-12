---
title: "Howto install NVidia 6200 on Feisty?"
date: 2007-06-25
forum: Hardware &amp; Laptops
---

### Post by ttry72 on 2007-06-25
Hi all. I need some help, please. How can I install MSI's NVidia 6200 graphic card on Feisty? I have try to install according to following instructions:

----

sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nano /etc/X11/xorg.conf
---

Replaced nv by using nvidia and marked off all dri's from xorg.conf file.

After that I have installed the OS (7.04)  again and I havent done anything yet.

What  should I do now?

---

### Post by greg_g on 2007-06-25
Well, first of all, go ahead and post the contents of your xorg.conf in CODE brackets (the # button when replying).  We'll go from there.

---

### Post by kodoku on 2007-06-25
You could always just use envy and have it download and compile the driver for you.

Google "nvidia envy" and you should find the feisty deb.

---

### Post by gtr225 on 2007-06-25
I have recently installed a 6200 on my system and have found that glx-new works better.I installed nvidia-glx-new then ran: ```
sudo dpkg-reconfigure xserver-xorg
```and made sure nvidia is the selected module, setup monitor resolution, etc then ```
sudo nvidia-xconfig
``` and it should work fine. The only problem I have now is that I can't get TV-out to work and I have posted a thread here [http://ubuntuforums.org/showthread.php?t=483246](http://ubuntuforums.org/showthread.php?t=483246)

---

### Post by ttry72 on 2007-06-26
> **gtr225 said:**
> I have recently installed a 6200 on my system and have found that glx-new works better.I installed nvidia-glx-new then ran: ```
sudo dpkg-reconfigure xserver-xorg
```and made sure nvidia is the selected module, setup monitor resolution, etc then ```
sudo nvidia-xconfig
``` and it should work fine. The only problem I have now is that I can't get TV-out to work and I have posted a thread here [http://ubuntuforums.org/showthread.php?t=483246](http://ubuntuforums.org/showthread.php?t=483246)

Well, the problem was "fixed" by changing back to ATI Radeon 9200. Now it works almost perfectly. How shame that Feisty was in trouble with NVidia. Look forward the next version of Ubuntu. I am still anxious to know if someone has easy way to make it work. 

Thanks for the contribution, Cheers!

---

### Post by gtr225 on 2007-06-26
But what was too hard about running those two commands?

---

