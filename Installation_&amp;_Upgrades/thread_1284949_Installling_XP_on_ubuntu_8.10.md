---
title: "Installling XP on ubuntu 8.10"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by dmadhawie on 2009-10-07
Hi all,

I have installed ubuntu 8.10 in my computer. It is the only OS running currently on my computer. Now I am interested in installing Windows XP as well.

When I try to boot from an XP cd, it runs up to the level where it says press any key to boot from cd. When I press some key it shows the black screen, but the welcome screen does not appear. I'm sure that it is not a problem with the cd as well.

I tried many solutions those were given, but almost all of them require to boot xp from cd. 

Can anyone please help me to solve this problem? I would like to maintain both ubuntu and XP, but it is not a matter even if I lose ubuntu at XP installation, I can reinstall it after XP installation.

Your help is highly appreciated.

Thanks

Madhawie

---

### Post by dstew on 2009-10-07
Do other CD's boot from that drive? Maybe the drive optics are dirty, or the drive is otherwise faulty. Are you sure the XP disk is a CD (i.e., is it a DVD?) Is the disk dirty, or damaged? I assume the disk boots fine in other drivers.

---

### Post by dmadhawie on 2010-09-24
Hi, 
thanks a lot for the reply. The problem was due to the formatting of my file system. I had formatted it to ext3 in installing ubuntu and when I tried to install XP i could not mount it. It was solved when I reformatted the file system to NTFS. :)
Thanks!

---

### Post by mörgæs on 2010-09-24
If you still are using 8.10, it is time to switch to a newer version. 8.10 is unsupported and thus a security threat.

---

### Post by grahammechanical on 2010-09-24
Are you trying to run this CD from within Ubuntu? Is the BIOS set to allow booting from CD?

Do not take my word for it but are you not doing things the wrong way around? As I understand it MS Windows must be installed on the first part of the hard disc. Bill Gates does not believe in the existence of other Operating Systems, so Windows will not install after Ubuntu. If it does install it will wipe out your Ubuntu installation.  In my opinion.

I suggest that you use a Ubuntu Live CD to format the hard disc to a Windows format, Install Windows, then install Ubuntu, which has been taught how to co-exist with other Operating Systems.

regards

---

