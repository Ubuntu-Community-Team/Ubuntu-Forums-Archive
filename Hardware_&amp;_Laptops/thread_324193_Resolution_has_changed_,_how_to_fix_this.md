---
title: "Resolution has changed , how to fix this?"
date: 2006-12-23
forum: Hardware &amp; Laptops
---

### Post by tdog on 2006-12-23
Hello.
I didn't know where to post this , so i thought this might be the right location . 
I have installed latest ubuntu, I have NVIDIA geforce 7 series, with 256 meg memory installed. 
I had very good resolution after installation . been working with this for weeks . 
Decided to install KUBUNTU desktop and that went ok .. 

Today , i booted my system and to my surprise , my resolution was too low, at 640 X 480 .. no matter what i did , i was not able to fix this problem
I tried to configure my card , selected my GeForce 7 series and NV driver . nothing worked. 

I was wondering , if any one can tell me how to fix this problem . ?
I am new to linux so those fancy command lines are not much help .. 

I wanted to reinstall linux, but i have scripts that are configured on my apache and I don't want to go trough reinstalling them as well as updating linux itself all the time 

thanks in advance

---

### Post by torstenaf on 2006-12-23
I also experienced this.  In my **/etc/X11/**  directory, there were multiple **xorg.conf **files backed up, including one with the correct resolutions for my laptop.  I backed up the 640x480 one, ```
mv xorg.conf xorg.conf.backup
``` and then used one of the old ones with the correct resolution of 1280x800, ```
mv xorg.conf.1 xorg.conf
```

---

### Post by tdog on 2006-12-23
Thanks. i reloged back to linux.. it seems i don't even have access to the root either .. 
i used to brows the root such as usr, etc, var , etc. now when i click on root , i see only HOME, MEDIA .. thats all i have access too.

I guess i have to reinstall ubuntu again .. 7 time a charm ;) ..
thanks for the help

---

### Post by torstenaf on 2006-12-24
Maybe I should have mentioned that you need to be the **root** user?

Also, the commands above are best done from within a terminal...

```
sudo -s
cd /etc/X11/
mv xorg.conf xorg.conf.backup
mv xorg.conf.1 xorg.conf

```

---

