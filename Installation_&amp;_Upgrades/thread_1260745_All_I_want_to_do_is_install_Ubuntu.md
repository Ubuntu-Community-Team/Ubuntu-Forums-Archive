---
title: "All I want to do is install Ubuntu"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by KcAV on 2009-09-07
I want to run multiple OSs on a netbook; Windows XP is now running on the netbook.

Is it possible to install Ubuntu Remix directly from the web without downloading it to local computer? 

If I downloaded ubuntu-9.04-netbook-Remix-i386.img to netbook how should I install it? I have a USB hard drive that I can attach to the netbook, but I do not want to lose data stored on it. Is there a way to use the hard drive to install Ubuntu to the netbook without losing data now on the external USB hard drive?

KC

---

### Post by Mighty_Joe on 2009-09-08
> **KcAV said:**
> 
Is it possible to install Ubuntu Remix directly from the web without downloading it to local computer? 


Not that I know of.  How about buying another [USB Flash Drive]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820141524")?  They're cheap enough (I know some of our community live in places where hardware is not so cheap).

---

### Post by KcAV on 2009-09-08
I bought a USB Flash drive and it wasn't expensive. I downloaded Drive Image, unzipped Ubuntu, and install Ubuntu on the Flash drive. I set the BIOS boot sequence to first look for a removable drive, and when I booted the system it found the Flash drive and booted from it.  :P  

Now what should I do? 

My goal is to run multiple OSs. I have Windows XP running in primary partition C, and the data is being stored in logical partition D.  I don't want to interfer with this.  I want Ubuntu to become an item on opersting system menu. I have a feeling if proceed with the install Ubuntu will write over the MBR and clobber Windows XP that is running nicely.

   How large a partition should I create for Ubuntu?
   What file format should I use?
   Where should I store Ubuntu's pagefile?
   What file format should I use for Ubuntu's data partition?
   How can I specify the directory to install Ubuntu?



KC

---

### Post by Mighty_Joe on 2009-09-10
> **KcAV said:**
> I have a feeling if proceed with the install Ubuntu will write over the MBR and clobber Windows XP that is running nicely.

Actually the opposite is true.  Linux plays nice with Windows. If you install Windows after Linux, Windows will disable the Linux boot loader (GRUB, LILO)

> **KcAV said:**
> 
   How large a partition should I create for Ubuntu?
   What file format should I use?
   Where should I store Ubuntu's pagefile?
   What file format should I use for Ubuntu's data partition?
   How can I specify the directory to install Ubuntu?


The answers to your questions can be found in the [installation documentation]("https://help.ubuntu.com/9.04/installation-guide/i386/index.html") or by searching the forum.  There's no one-size-fits-all answers.  You'll have to do some reading and make a decision according to your particular situation.

---

