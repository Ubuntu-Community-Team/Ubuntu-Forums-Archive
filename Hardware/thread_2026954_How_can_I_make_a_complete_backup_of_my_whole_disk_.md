---
title: "How can I make a complete backup of my whole disk including MBR and partition tables?"
date: 2012-07-16
forum: Hardware
---

### Post by El Potro on 2012-07-16
Hiya people,

I need help with this.

I have this netbook, which has a Windows 7 and Ubuntu 10.04 along with a recovery tool in another partition (in fact, this is a program in that holds images of the other partitions, and you can restore them by using it).

I'd like to backup the whole hard disk, completely. I mean, I want to be able to recover the exact structure of files, the exact mbr, grub, partition tables, etc by copying them back if I need it. What is the right procedure? Do I need to make an image of the disk? How can this be done?

This should be possible. Can someone can point me in the right direction?

Thank you very much in advance.

---

### Post by Shadius on 2012-07-16
Hmmm...sounds like you're looking to clone your HDD. Check out [Clonezilla]("http://clonezilla.org/") or [G4L (Ghost 4 Linux)]("http://sourceforge.net/projects/g4l/"). I've used both before to clone my HDD.

---

### Post by NikTh on 2012-07-16
Hi , 
there are lot of tools out there that doing this job , or argue that. e.g [**[COLOR=Red]partimage[/COLOR]**]("http://www.partimage.org/Main_Page") or [[COLOR=Red]**CloneZilla**[/COLOR]]("http://clonezilla.org/"). 

IMO the best tool for this job is already included to Ubuntu(linux) , in fact its compilation of 2 tools . dd command & gzip , but these commands (especially dd) are for little advanced users. 
dd command can wipe of you disk ( in case of mistake) and you will not notice. 
So , try to take a look on 2 above tools , and if someone advanced user wants to guide you through dd & gzip , ok. But i am little afraid to guide you through this .. cause i am limited by English language knowledge. 
Thanks

---

### Post by Shadius on 2012-07-16
> **NikTh said:**
> Hi , 
there are lot of tools out there that doing this job , or argue that. e.g [**[COLOR=Red]partimage[/COLOR]**]("http://www.partimage.org/Main_Page") or [[COLOR=Red]**CloneZilla**[/COLOR]]("http://clonezilla.org/"). 

IMO the best tool for this job is already included to Ubuntu(linux) , in fact its compilation of 2 tools . dd command & gzip , but these commands (especially dd) are for little advanced users. 
dd command can wipe of you disk ( in case of mistake) and you will not notice. 
So , try to take a look on 2 above tools , and if someone advanced user wants to guide you through dd & gzip , ok. But i am little afraid to guide you through this .. cause i am limited by English language knowledge. 
Thanks

Even though I've never used the **dd** command, I've found a helpful [link]("http://www.debianhelp.co.uk/ddcommand.htm"). It does seem a little on the more advanced side though. Choose whichever you feel most comfortable using. There are lots of tools out there.

---

