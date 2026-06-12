---
title: "Ubuntu duel boot vista"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by cantar on 2009-02-24
Okie so heres the deal, i had a bootsector virus that messed up my vista and the dell vista reinstall so i installed Ubuntu64 on my other drive till i got a new copy of vista, now i have installed vista on the first hard drive keeping the ubuntu drive free because i was able to recover files from my vista drive to my other one. the problem is now that vista is installed it doesnt see my ubuntu drive (this might because i used ext3 or whatever it was called) but i also cant boot Into ubuntu because theres no duel boot manager poping up. any ideas on how to fix it without losing the stuff on the ubuntu drive?. (i guess i could always unplug the vista drive and boot into it if i had to apply the change there)

---

### Post by chmbrs on 2009-02-24
are they both installed on one hdd? 

you can boot ubuntu live cd and install grub to your hdd with winblows. it would detect winblows and ubuntu and create dualboot for you. to install grub:

[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html#Installing-GRUB-using-grub_002dinstall](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html#Installing-GRUB-using-grub_002dinstall)

its a little advanced but you should manage.

i also heard of supergrub or something you can google it.

if you have winblows installed then install ubuntu it should automatically find winblows os and add it to grub menu. why even use winblows????????????????????

---

### Post by cantar on 2009-02-24
No Hd01= 250 gig hd with windows vista fresh install
Hd02 - 500 gig hd with Ubuntu

basicly i just need to some how repire the bootloader to see ubuntu

edit: hopfuly though windows or the ubuntu install disk or another downloadable program that i can put on a cd

---

### Post by chmbrs on 2009-02-24
i think thats very hard to do. im a newbie too so i cant help you with that. but what i know is if they were both on one hdd it would be much easier. 

the bios is set to boot from a hdd that vista is on. if you change the bios to boot from the ubuntu hdd it will work. however theres no way im aware of to pick between hdd to boot from. you can pick different os installed on hdd. you get me. youd have to switch the active booting hdd in the bios everytime to switch between vista and ubuntu.

if theyre on one hdd youll have a dual boot menu. ubuntu and winblows and you just pick which one

---

### Post by cantar on 2009-02-24
i was able to duel boot for about 3 days using differnt hard drives but i think ubuntu has to be installed Last dunno ill try disabling the vista hd from bios booting into ubuntu try to recover my files maybe burn them then reinstall ubuntu on the other drive. thanks anyways

---

### Post by chmbrs on 2009-02-24
if you change hdd in bios you should be able to boot ubuntu no problem. 
then just switch it back for winblows 

thatll work for now. when you have you files just install ubuntu over wblows and youll have dual boot. then you can just format other drive.

---

### Post by Mark Phelps on 2009-02-25
With two drives, you can choose either of the following:
1) Boot into the Vista drive and use the Vista boot loader to select either Vista or Ubuntu
2) Boot into the Ubuntu drive and use GRUB to select either Vista or Ubuntu.

I have a multi-drive system and am doing the latter because, I learned the hard way not to mess with the Vista installation.

To do that, do the following:
1) Change your boot order in the BIOS to select the Ubuntu drive
2) If GRUB is not already loaded into the MBR of the Ubuntu drive, boot from a LiveCD and install GRUB to that drive
3) Boot from GRUB into Ubuntu and add a stanza for the Vista selection to /boot/grub/men.lst file

---

