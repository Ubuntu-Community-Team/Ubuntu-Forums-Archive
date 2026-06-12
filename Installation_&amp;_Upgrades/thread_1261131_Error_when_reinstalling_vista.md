---
title: "Error when reinstalling vista"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by ananbehh on 2009-09-08
I installed ubuntu on my Acer 6530G 64Bt laptop,
I would like to go back to windows vista, I have the recovery CD's so I did a full system recovery but when the system try to boot I get the following Error:
 
Grub loading stage .5.
Grub loading, please wait... 
Error 17
 
 
 
Dont know what that mean, Any Ideas..:confused::confused::confused:
 
I tried system partion in Live CD and didnt work, reformat as NTFS

---

### Post by presence1960 on 2009-09-08
GRUB is still on the MBR of your disk. You may not be able to access recovery console from the recovery CDs/DVDs. Check your documentation. If you can't access recovery console there is a work around. Go [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") to download the iso for your Vista version (32 bit or 64 bit). Burn the iso to a CD as an image. Boot from that CD and do [this]("http://ubuntuforums.org/showthread.php?t=1014708") (using instructions for Vista)

This will put vista back onto MBR and you will then be able to boot right into Vista.

---

### Post by ananbehh on 2009-09-08
I cant boot from Windows recovery !!

---

### Post by presence1960 on 2009-09-08
> **ananbehh said:**
> I cant boot from Windows recovery !!

are you referring to the recovery console iso I asked you download & burn to CD as an image?

---

### Post by ananbehh on 2009-09-08
Yes,
 
This is what I did:
Download the recovery cd===>mount it==>> Burn.
 
Then I insert the Cd in CDrom and restarted the computer. system went to ubuntu

---

### Post by presence1960 on 2009-09-08
> **ananbehh said:**
> Yes,
 
This is what I did:
Download the recovery cd===>mount it==>> Burn.
 
Then I insert the Cd in CDrom and restarted the computer. system went to ubuntu

Did you burn it as an image or a data CD?

---

### Post by ananbehh on 2009-09-08
Ok, I have no idea what is the differance between the two, just used windows to burn it
 
Can u tell me how to burn it!

---

### Post by presence1960 on 2009-09-08
> **ananbehh said:**
> Ok, I have no idea what is the differance between the two, just used windows to burn it
 
Can u tell me how to burn it!

[https://help.ubuntu.com/9.04/switching/installing-burning.html](https://help.ubuntu.com/9.04/switching/installing-burning.html)

Follow the instructions at the top for windows. you will have to download InfraRecorder. 

There is a difference between a data CD/DVD and a bootable image on a CD/DVD. You burned a data CD which only copies the iso to disk. That's why you can't boot from it.

---

### Post by ananbehh on 2009-09-08
I downlloaded the program when I try to burn I get an error "faild to intialize recorder"
 
I also have magic ISo if this helps

---

### Post by presence1960 on 2009-09-08
> **ananbehh said:**
> I downlloaded the program when I try to burn I get an error "faild to intialize recorder"
 
I also have magic ISo if this helps

I am not familiar with that program. Whatever program you use you have to burn the iso as an image to CD, just like you did with the Ubuntu iso to make the Ubuntu Live CD. And your CD/DVD drive needs to be set to boot first in the device list in BIOS when you try booting off the CD you burned.

---

