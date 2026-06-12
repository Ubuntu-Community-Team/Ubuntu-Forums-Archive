---
title: "Grub Loader + breezy"
date: 2005-09-04
forum: Hardware &amp; Laptops
---

### Post by L1nVx on 2005-09-04
hey i have 2 questions ...
ONE: How do i configure the grub loader so it recognizes my windwos xp.. here's the deal i had one Hard drive with xp and linux then i just deleted linux installed linux on another hard drive (hoary version i believe) put that as master and the  xp secondary and now i only can get into linux... i expectred this but i don't know how to point my loader thing to windows xp so i can choose either now... it only shows linux.

Second:  Were can i upgrade to breezy i hear you can. and it is ne.w


i found a redhat i believe site for configuring grub loader but it said in /etc there would be grub.conf... and it wasn't there so idk if my grub thing is on the other hd or if it's different on ubuntu or what.

---

### Post by void_false on 2005-09-04
I'm not sure where should your grub.conf file be because I have my /boot on a seperated partition.
Anyway, open grub.conf for editing as root. I'm not a GRUB guru but here's how I did:

```
title=WinXP
root (hd0,0)
makeactive
chainloader +1
```

Append this to the end of grub.conf file. Here how's mine look:

```
default 0
timeout 30
splashimage=(hd0,6)/grub/splash.xpm.gz

title=Ubuntu
  root (hd0, 8)
  kernel /vmlinuz root=/dev/hda9 apm=off pci=noacpi
  initrd /initrd.img

# Only in case you want to dual-boot
title=WinXP
root (hd0,0)
makeactive
chainloader +1
```

---

### Post by L1nVx on 2005-09-04
well i went from one hard drive to two hard drives with linux and xp on seperate hds.. and the one linux is on NOW isn't the original one grub loader was on... so maybe it's still on the older loader... but i can't find my grub.conf :( that's the problem it wasn't there loli reinstled my grub loader in linux so i'm gonna check again

---

### Post by L1nVx on 2005-09-04
should i MAKE a grub.conf in /etc?? ...

---

### Post by L1nVx on 2005-09-04
ugh i need to get my loader working so i can get into Windows XP at some points... but i can't find my damn grub.conf! can't anyone help me find it or something lol and then tell me how to set it up since it's on a seperate hard drive!@

---

### Post by kosmic on 2005-09-04
the file you are looking is in...

/boot/grub/menu.lst

edit the fiel menu.lst and add the Win XP partition there.

But first as root our using sudo see where win XP is.

sudo fdisk -l

and then append that drive to Grub.

To upgrade to Breezy just change the /etc/apt/sources.list to breeze where it says hoary, BUT breeze is not stable yet, if you don't want to have headeches :) don't upgrade, will save you a lot of trouble

---

### Post by L1nVx on 2005-09-04
thanks so much i think i got everything working. :) (i haven't checekd but i did everything right so it SHOULD WOrk) thanks!

---

