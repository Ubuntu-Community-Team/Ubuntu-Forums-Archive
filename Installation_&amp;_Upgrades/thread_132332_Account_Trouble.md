---
title: "Account Trouble"
date: 2006-02-18
forum: Installation &amp; Upgrades
---

### Post by modestgeek on 2006-02-18
Packard Bell Easynote H5
512MB RAM
64MB NVidia graphics card
Samsung hard drive


I installed Ubuntu yesterday, and had everything working fine, but then I realised that the partition I was going to put media files on wasn't correct. So I reinstalled Ubuntu. This was a big mistake. I am now having major issues:

I put in the new username, then the password, and then I verify. I hit enter to proceed to the next stage, but get reverted back to new user. Like this:


New username ---> Password ---> Verify password ---> New username

It goes in a circle. How do I fix this?

Thanks in advance

---

### Post by JasonL on 2006-02-18
Im guessing your trying to do the same as me, put /home on its own partition. I would like help with this too, I am just wondering if after telling it to create the user if you can select <go back> and then jump to the next step.

---

### Post by kaamos on 2006-02-18
You could have a just a little bit faulty cd. If it is not too much of a hassle, you could check the md5sum of the iso you used and burn another cd.

---

### Post by JasonL on 2006-02-18
I ordered my cd from Ship-it so I dont think it will be faulty and the cd has no scratches or anything on it.

---

### Post by cronholio on 2006-02-18
@modestgeek: Do I get that right? You installed Ubuntu once and it worked. Then you did the same again and you run into that circle during the installation process? So you cannot even install it again?

---

### Post by JasonL on 2006-02-18
I think he has tried to install it again but with /home on a different partition.

---

### Post by modestgeek on 2006-02-18
Yeah, I installed once, and it worked fine, then I deleted the partition I had for Ubuntu, and reinstalled Ubuntu on the empty part of my hard drive. The circle thing comes in when I try to install. 

I can install, but I cant log in, because no accounts have been made (this is because when I go through the circle thing about 5 times, i just press esc). I would log in as root, but in ubuntu root cannot log in from the main screen without enabling it.

---

### Post by taurus on 2006-02-18
It's your new /home partition an ext2/ext3 or a vfat (FAT32) filesystem!  Better hope it's ext2/ext3 and not vfat then...

---

