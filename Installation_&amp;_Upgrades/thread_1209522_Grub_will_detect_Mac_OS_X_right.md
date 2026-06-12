---
title: "Grub will detect Mac OS X right?"
date: 2009-07-10
forum: Installation &amp; Upgrades
---

### Post by DartheTater on 2009-07-10
Dumb newbie question, but Grub will detect Mac OS X right? I have the universal version of OS X that will install on all X86 machines. I do not have a mac. I have 4 hard drives.

I want to install XP, Vista, Mac OS X, Super Ubuntu, and maybe Xbuntu. FYI it's for fun. :P
XP and Vista would be on a drive each. Then OS X on it's own drive and the Ubuntu(s) on the last hard drive.

The best way would be to install them in the order listed right? That way Grub will setup a nice boot menu? 

Alternately is there some freeware bootloader that I can use that will detect these OSs without a hassle? 

Currently I have XP and Win2k and a boot menu from Windows. The boot sector on this drive should stay intact right? Grub won't over-write it will it? (Ubuntu will be installed on another hard drive). 

Any help would be appreciated.

---

### Post by csabo2 on 2009-07-10
i've not seen it done. I've always used the mac boot loader :)


[http://ossism.com/2008/12/23/how-to-dual-boot-osx-leopard-1056-and-ubuntu-810/](http://ossism.com/2008/12/23/how-to-dual-boot-osx-leopard-1056-and-ubuntu-810/)

---

### Post by DartheTater on 2009-07-10
Thanks csabo, I might try that. I remember it having a 2 OS limit. I could be totally wrong about that. 

Hmm. I just thought of something. If I can't get Grub to work, or any other booter, or if it's too much of a hassle, I guess I could just hard boot (F11). Then Disk 1 will have the 2 windows referenced (Disk 1 and 2), Disk 3 will have Mac, and Disk 4 Will have the Ubuntus (with Grub showing just the Ubuntus). I could do this I guess by installing the OSs with the other hard drives disconnected. That way no messing with boot sectors I guess.

---

### Post by jrox717 on 2009-07-10
I have had good experiences with Smart BootManager. From their webiste: 
>  Smart BootManager is an os independent BootManager which has easy to use interface and many other features. The main goals of SBM are to be absolutely OS independent, flexible and full-featured. It has all of the features needed to boot a variety of OS. 
[http://sourceforge.net/projects/btmgr/](http://sourceforge.net/projects/btmgr/)

---

### Post by raymondh on 2009-07-10
I use Darwin on my 3-boot (XP, OSX, Jaunty).  Darwin is the first to load allowing me the 3 OS choices.  It will boot both OSX and XP.  If I choose Jaunty, GRUB takes over with Jaunty and XP.

---

### Post by csabo2 on 2009-07-10
> **jrox717 said:**
> I have had good experiences with Smart BootManager. From their webiste: 

[http://sourceforge.net/projects/btmgr/](http://sourceforge.net/projects/btmgr/)

Didn't know this was around. Thanks!

---

