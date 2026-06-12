---
title: "[SOLVED] hard drive question"
date: 2008-09-09
forum: General Help
---

### Post by devin0 on 2008-09-09
I have one 20gb hard drive with windows installed on it and another one that is 30gb with ubuntu installed on it. Right now if I want to switch operating systems I switch the hard drives out. Is there a way to set it up  so that both hard drives are installed and I can choose what operating system boots?

---

### Post by oilchangeguy on 2008-09-09
> **devin0 said:**
> I have one 20gb hard drive with windows installed on it and another one that is 30gb with ubuntu installed on it. Right now if I want to switch operating systems I switch the hard drives out. Is there a way to set it up  so that both hard drives are installed and I can choose what operating system boots?

i did this, i set the windows drive to master, and the ubuntu drive to slave. and grub picked up on both and i was able to choose which os i wanted to boot.

---

### Post by ronnielsen1 on 2008-09-09
> i did this, i set the windows drive to master, and the ubuntu drive to slave. and grub picked up on both and i was able to choose which os i wanted to boot. 
Ubuntu was on your slave drive and grub still came up over MBR?

---

### Post by oilchangeguy on 2008-09-09
> **ronnielsen1 said:**
> Ubuntu was on your slave drive and grub still came up over MBR?

yep

---

### Post by wolfen69 on 2008-09-09
have both set as master and most BIOS's have a quick boot option like F12, where you can quickly choose which one to boot to. if you do not have a quick boot option, just go into the BIOS and change it there. much quicker than physically swapping them out.

---

### Post by lukjad on 2008-09-09
I would just install XP first, then install Ubuntu over it. You can then choose which OS to load at each bootup.

---

### Post by eggdeng on 2008-09-09
Configure the Ubuntu disk as master and the W*nd*ws as slave. Boot into Ubuntu and, from a terminal, run
```
sudo cp /boot/grub/menu/list /boot/grub/menu/list.backup
```
This is just to have a backup in case of trouble. Now run
```
gksudo /boot/grub/menu/list
```
Add the lines (assuming that XP is on the first partition of the second HDD)
```
title		Microsoft Windows XP
root		(hd1,0)
savedefault
makeactive
chainloader	+1
```
just below the paragraph that says > Other operating systems
Save and reboot and GRUB should offer you the opportunity to boot into either system.

---

### Post by devin0 on 2008-09-09
OK im going to try eggdeng's meathod. Lets say I screw something up I can still just plug in my windows hard drive and it will still boot right?

---

### Post by eggdeng on 2008-09-09
Yes. GRUB is on your Ubuntu disk so you won't be making any changes to the W*nd*ws install.

---

### Post by ronnielsen1 on 2008-09-09
> yep
Impressed.

---

### Post by devin0 on 2008-09-11
Ok I got it all set up thanks everyone :)

---

