---
title: "can not mount cdrom0"
date: 2005-01-11
forum: Hardware &amp; Laptops
---

### Post by smb2004 on 2005-01-11
i have just recently installed ubuntu and i'm updtadateing with all the programs i want/need.  i need to apt-get libtool and g++, but when i do terminal askes for my warty install disk.  i can't seem to mount the install cd on cdrom0(but i can mount others).  i can however on my dvd drive, cdrom1.  why is this?  when i try to manually mount the drive it says:

matt@mattlinuxbox:~ $ sudo mount /media/cdrom
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       or too many mounted file systems
matt@mattlinuxbox:~ $

is there anyway to either mount it, point terminal to read cdrom1 when trying to apt-get install g++, or just download g++ and install manually somehow.  thanks!
~matt

---

### Post by hashimoto on 2005-01-11
Maybe you are missing the fstab entry for cdrom0 or it misses the supermount option. The latter was the case with my bros Mandrake just yestarday evening (though I don't recall if supermount is something MDK specific).

BR
Hashimoto

---

### Post by smb2004 on 2005-01-11
there is an enrty in fstab:

/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto

and i dont know about supermount, what is it.  i've fooled around with other linux distro's but am still learning.

this is what terminal askes for when i try to sudo apt-get install g++

After unpacking 14.5MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Media Change: Please insert the disc labelled
 'Ubuntu 4.10 _Warty Warthog_ - Preview amd64 Binary-1 (20041020)'
in the drive '/cdrom/' and press enter

---

### Post by smb2004 on 2005-01-11
i got it.  im not sure how.  i gave it another try and it worked. wierd.  i still think all linux distros should come with libtool and g++ anyway.  thanks!
~matt

---

### Post by Philodox on 2005-03-02
[QUOTE=smb2004]i have just recently installed ubuntu and i'm updtadateing with all the programs i want/need.  i need to apt-get libtool and g++, but when i do terminal askes for my warty install disk.  i can't seem to mount the install cd on cdrom0(but i can mount others).  i can however on my dvd drive, cdrom1.  why is this?  when i try to manually mount the drive it says:

matt@mattlinuxbox:~ $ sudo mount /media/cdrom
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       or too many mounted file systems
matt@mattlinuxbox:~ $

is there anyway to either mount it, point terminal to read cdrom1 when trying to apt-get install g++, or just download g++ and install manually somehow.  thanks!
~matt[/QUOTE]
 I'm having the same problem with my installation, I've installed using-expert custom and I'm running from the console.  

I can't use apt-get to get new packages, and I am unable to mount the installation cd.



*edit* I've managed to get around the problem by unmounting the cdrom, mounting another disc, and then remounting the ubuntu cd.  I'm sure this isn't the   technical solution, but it seems to work.

---

