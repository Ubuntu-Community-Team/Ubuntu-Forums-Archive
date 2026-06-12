---
title: "Unable to boot"
date: 2006-11-22
forum: Hardware &amp; Laptops
---

### Post by buco55 on 2006-11-22
Today I have deleted every file on my computer using the toshiba recovery conslole(I have a Toshiba Tecra A1). There were two partitions - one windows xp and the other ubuntu (the newest one). After the deletion of the partitions when I tried to boot up my widnows a got a black screen and all over the screen it said GRUB.
What can I do in order to restore winodws back to my laptop? I really need my laptop back so please help me as soon as possibile.

---

### Post by an.echte.trilingue on 2006-11-22
It sounds like you deleted it.  I think you need to reinstall windows from the CDs that came with your computer.

---

### Post by Peepsalot on 2006-11-22
You deleted all your files and you are wondering why your machine won't boot? :-? 
If I understand you correctly, you're going to need to completely reinstall.

---

### Post by LDRoamer on 2006-11-22
You can try booting from your windows cd and using the fix mbr command. I think the grub configuration gets loaded on the linux partition and if you deleted the information off that partition then you may have deleted the configuration that tells it what to load (and so it won't load anything). You can also boot from a windows flopy and run a similar command (I think its  "fdisk /mbr"). If you do some googling around on removing grub, restoring windows etc. you should get some direction on this.

If you actually deleted all the files off your windows partition as well as your linux one then your only option is to reload windows (because you will have deleted it).

---

### Post by buco55 on 2006-11-22
Just to get things clearer - I have deleted every possible partition on my hard drive (both the windows one and the ubuntu one). When my computer starts up I only get a message from Toshiba (which is standard) and then I receive a  black screen with white text on it saying GRUB and a blinking cursor.
That is all that there is.
There is no windows instaled or Ubuntu or anything.
The real problem comes when I reformat the whole drive again and reinstal windows. When the system restarts after the instalation I still get the same black screen with white text.
Also I only have 3 recovery CD's that include windows xp but I don't have a seperate windows instal cd.
Is there a way that I can go arround this and somehow delete or remove the GRUB loader so that when I instal windows from the recovery CD's it will boot up?
Or should I try instaling Ubuntu and then try to instal windows (as I can boot from a cd)?

---

### Post by an.echte.trilingue on 2006-11-27
Use the FIXMBR command on your windows recovery CDs.

---

### Post by drphilngood on 2006-11-27
You can also download the [Gag Boot Loader]("http://gag.sourceforge.net/") which should detect your new Windows install and allow you to boot into it.  However, it would be better and quicker if you can follow an.echte.trilingue´s instructions.

---

