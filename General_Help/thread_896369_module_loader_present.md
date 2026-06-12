---
title: "module loader present"
date: 2008-08-21
forum: General Help
---

### Post by Exxentrix on 2008-08-21
So, a little background first. I ****** around with ubuntu a little, ordered the CDs and everything. It was fun, but I still wanted OSX and was still stuck using XP. One day, my XP got a virus. It died quickly. So I decided to reformat my drive. But I found my XP disc in shambles. So, I found the only boot disc I could find, Ubuntu 7.04. That was 2 weeks ago, Ubuntu is going great except for some issues.
My main issue was installing Beryl. Nvidia drivers were just not working for it! When I tried to set it as my desktop manager or something, everything would blink then it would go back to not-beryl. So i tried to do something with my drivers, following instructions on [this]("http://kmandla.wordpress.com/2007/05/12/howto-troubleshoot-nvidia-drivers-with-the-ubuntu-704-desktop-cd/") site, which involved turning off my GDM. I ****** up I guess,because when I was finished and attempted to restore GDM, I got an error informing me that my X wasn't running correctly, and an option to view the error. This was the error text:

X Window System Version 7.2.0
Release Date: 22 January 2007
X protocol version 11, Revision 0, Release 7.2
Build Operating System:Linux Ubuntu
Current Operating System:Linux linuxbox 2.6.20-17-generic #2 SMP Thu Jul 10 00:05:43 UTC 2008 i686
Build date: 13 June 2008
       Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
       To make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==)default setting,
         (++) from command line, (!!) notice, (||) informational,
         (ww)warning, (EE)error, (NI)not Implemented, (??)unknown
(==)Log file: "/var/log/xorg/1.0.log", time: Thu aug 21 00:53:46 2008
(==)Using config file: "/etc/x11/xorg.conf
                              <Ok>

Please help me fix this and if you have the time, my other problem with beryl.
But mostly this as it makes my PC unusable.
Thanks!

---

### Post by Exxentrix on 2008-08-21
Please help, I'd really like to be able to use my computer again. I'm posting this from a REALLY crappy computer owned by a roommate who doesn't know jack about computers so it's an ANCIENT Dell.

---

### Post by Exxentrix on 2008-08-21
ohh, I accidentally forgot to scroll down, I feel really stupid. Here is the rest of the error and what I believe to be the part that explains the problem.

(EE) Failed to load module "Nvidia"(module does not exist, 0)
(EE) No drivers available

fatal server error:
No screens found

---

### Post by Exxentrix on 2008-08-21
oh my god please someone help

---

### Post by qstraza on 2008-08-21
Why do u want to use beryl? I got tired of it, it its buggie. On starters it is uber fun, but later on, it gets annoying, never the less, thats just my opinion.

If i uderstand you right, now u cannot log in to X in any way?

I hope u backed up the xorg.conf, check if nvidia-xconfig did a backup, confs are in /etc/X11/


and maybe this command, if everythings fails
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by Exxentrix on 2008-08-21
> **qstraza said:**
> Why do u want to use beryl? I got tired of it, it its buggie. On starters it is uber fun, but later on, it gets annoying, never the less, thats just my opinion.

If i uderstand you right, now u cannot log in to X in any way?

I hope u backed up the xorg.conf, check if nvidia-xconfig did a backup, confs are in /etc/X11/


and maybe this command, if everythings fails
```

sudo dpkg-reconfigure xserver-xorg

```
I've been trying at the backed up xorg.confs and they just aren't working. I did the sudo dpkg-reconfigure xserver-xorg and It's brought me to a disturbing screen about my video card. I really just need to reset my xorg.conf. Now, it will boot up, but when it gets past the login screen, the screen turns white and that's all.

---

### Post by qstraza on 2008-08-21
Well what did u do at the first place? What caused this error?

You could replace all occurrences of "nvidia" with "vesa" in xorg.conf (if you have nvidia) but is not a long term solution.

Im really out of ideas, especially if backed-up  xorg.conf doesnt work.

If i were you i would just reinstall the ubuntu, put your /home on separate partition, this makes your life better;)

EDIT:
i noticed this:
> (EE) Failed to load module "Nvidia"(module does not exist, 0)

Maybe module name in xorg.conf have to be in lower case, its just a wild guess tough...so "nvidia" insted of "Nvidia"
try it, cant harm you any more than it already did:p

---

### Post by Exxentrix on 2008-08-21
> **qstraza said:**
> Well what did u do at the first place? What caused this error?

You could replace all occurrences of "nvidia" with "vesa" in xorg.conf (if you have nvidia) but is not a long term solution.

Im really out of ideas, especially if backed-up  xorg.conf doesnt work.

If i were you i would just reinstall the ubuntu, put your /home on separate partition, this makes your life better;)

EDIT:
i noticed this:


Maybe module name in xorg.conf have to be in lower case, its just a wild guess tough...so "nvidia" insted of "Nvidia"
try it, cant harm you any more than it already did:p
Okay, that brings another problem. How do I edit my xorg.conf? Especially from the command screen after you kill GDM.

---

### Post by qstraza on 2008-08-21
> **Exxentrix said:**
> Okay, that brings another problem. How do I edit my xorg.conf? Especially from the command screen after you kill GDM.

```
 sudo pico /etc/X11/xorg.conf 
```

I prefer pico, but if you use any other, use it, otherwise, after changing the file press "CTRL+x" then it will ask you if you want changes to be saved, u type in "y" and hit enter. Thats it.

than ```
startx
```

---

