---
title: "mounting problem"
date: 2009-11-13
forum: Hardware
---

### Post by qwertyp on 2009-11-13
hi guys, first of all, i am a new user ubuntu although i used some other linux distros before(pardus, fedara...)  ubuntu 9.10 is awesome but i have some problems. i searched internet and ubuntu.com and ubuntuforums.org particularly. first problem is ubuntu didn't mount my ntfs formatted 4-gb usb disk automatically. Similarly, it didn't mount my external ntfs formatted 1 tb hard disk. it has three seperate volumes. ubuntu mounts 2nd and 3rd ones but it doesn't mount 1st volume. i want ubuntu to mount all hard drives automatically. (i can mount them manually but it's very useful if it is automatically) the other problem is i had a windows 7. then i installed ubuntu. but windows 7 isn't available in grub? how can i add windows 7.(this is the first time i have ever seen a linux distro can't add windows to the grub.) thanks for help.(ps: sorry for bad english)

---

### Post by qwertyp on 2009-11-14
and another problem: this one is not about ubuntu. i plug a card into my notebook. and now i can't remove it. i used needle, toothpick, even nail clippers. but can't remove damn card.

---

### Post by Lateralis on 2009-11-14
I know that some people have experienced problems with mounting USB drives after installing/upgrading to 9.10; I was one of those people!  It appears to be a very hardware specific problem, as my laptop suffered with this problem but my home PC didn't.  The problem for my laptop was solved by updating *udev* from the proposed repository.  It may be that it helps solve your problems too, although I did that update at the beginning of last week.  I would hope that the proposed update was now in the main repositories...

As for Windows 7... As I understand it, the latest Grub (the version 2 beta which comes with Ubuntu 9.10) seems to have some issues with Windows 7.  I can't really go into details as:

a) I don't use Windows 7. :P
b) I'm still on legacy grub as I did an upgrade from 9.04 to 9.10, rather than a fresh install of 9.10.  

I daresay that someone will come along and elucidate on the problem/solution, but in the meantime you could try checking out the Grub2 documentation.  


As for the card... I have no idea!

---

