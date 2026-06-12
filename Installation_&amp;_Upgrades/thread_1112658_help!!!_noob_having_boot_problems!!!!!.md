---
title: "help!!! noob having boot problems!!!!!"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by Tbaja on 2009-03-31
Hey guys i looked through the forums and cant quite find the answer to my question. I have acquired a Dell optiplex 260 with a 40gig hd, 512megs ram basicaly a stock comp with a pentium 4, it had windows xp profesional but i dont have the code and i hate windows. i partitioned the HD with a complete ubuntu os (no more windows) but when i turn on the pc it will not boot. the dell start up screen comes on and it says loading grub, then nothing but a blank screen. if i hit f12 while in the dell screen i can choose boot from hard drive and then it boots fine .....why is this and i know very little about the terminal but have tried a few things like removing compiz but it didnt work. please help

---

### Post by zvacet on 2009-04-01
Why don´t you set up your BIOS to boot from hard disc?I believe that F12 is just one time option.You can remove compiz and packages related to it from synaptic.You will find synaptic under **sys>admin<synaptic package manager.**

---

### Post by Tbaja on 2009-04-01
i think i have it set? i went in to setup (f2) and changed the order in which it boots unless there is another way of doing it?

---

### Post by Tbaja on 2009-04-01
the order for boot is hard drive, cd rom, floppy i have tried everything i can think of...i tried changing the image from 1mb to 8mb in the bios. i really am lost everything goes good till after the splash screen then it goes blank. i still can go to f12 and boot up manually from the hd....why wont it do it on its own????

---

### Post by upchucky on 2009-04-01
he said its loading grub and goes blank screen, he needs to be told how to fix grub mbr and menu.lst

boot the ubuntu live cd then download this,

[http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055) 

then do this

```
sudo bash ~/Desktop/boot_info_script*.sh
```

post the results here and someone will be able to tell you exactly what to do to get grub working.

---

