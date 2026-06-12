---
title: "Error 21"
date: 2006-01-15
forum: Installation &amp; Upgrades
---

### Post by DirtDawg on 2006-01-15
Soooooo, I finally decided to try installing Ubuntu on my Windows machine on a seperate hard drive. Everything was working great until I was prompted to remove the CD. When Ubuntu tried to reboot to install the remaining packages, it got to GRUB then complained of "Error 21", then froze. Now I can't get into either Windows or Linux. 

I found a thread that talked about changing settings in BIOS to:
Primary Master: Type=user, Mode=LBA
Primary Slave: Type=Auto, Mode=Auto

But in BIOS, I couldn't find that exact setup. I found a configure HD option, but it only allows me to change Primary Master to 'Auto' or 'Off' and the Primary slave to 'Auto' from 'off'. I'm hesitant to do this as I don't understand it. 

Any help would be enormously appreciated as my girlfriend will tear my guts out if I screwed up the Windows system.

Many thanks

EDIT: PS: I began writing this under a previous thread ([http://www.ubuntuforums.org/showthread.php?t=117947)](http://www.ubuntuforums.org/showthread.php?t=117947)), but it will likely not be easily found under its title and I need help!

---

### Post by HJThis on 2006-01-15
Hello,DirtDawg

I had the same problem so what i did was
just as you just said.

but i made everything LBA & all was
fine this was on a Dell

Best of luck

---

### Post by HJThis on 2006-01-15
Hey,DirtDawg

I found this for you have a look i pray it is of help

[http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html](http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html)

hmm sorry i think that is the info you found

Best of luck

---

### Post by DirtDawg on 2006-01-15
Thank you. 

I did find that page, but I was panicking (call me colnol panic, HAR!). I just turned the thing on Auto and all was well. Now the X window system is broken, but I know I've seen posts about this before, so I should be able to figure it out. Whew.

Thanks again.

---

### Post by HJThis on 2006-01-16
Hi,DirtDawg

Glad you got it going 

now i hope you find the info on the X thing

Best of luck

---

