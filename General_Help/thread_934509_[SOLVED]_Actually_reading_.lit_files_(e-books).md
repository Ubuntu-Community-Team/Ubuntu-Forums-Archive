---
title: "[SOLVED] Actually reading .lit files (e-books)?"
date: 2008-09-30
forum: General Help
---

### Post by E-Cecilia on 2008-09-30
I've been *trying* to find a program that allows me to convert .lit files to some other readable format on Linux. I haven't had any luck yet...

Is there, maybe, someone who like me has been through all the trouble and knows sth. that may help the situation here?

---

### Post by techstop on 2008-09-30
This thread?

[http://ubuntuforums.org/showthread.php?t=49232](http://ubuntuforums.org/showthread.php?t=49232)

---

### Post by E-Cecilia on 2008-09-30
Well, I've already been to the old posts, but I couldn't make any of the programs work (probably my fault, though). I did try several times with each... I even installed a program called "Calibre," but I haven't figured out how to open it. Have you heard about it? :(

---

### Post by E-Cecilia on 2008-11-25
Okay, I managed to make it work.
I attached the instructions that did work for me.

---

### Post by graphius on 2009-02-12
OK, just a small nit pick,
here is the file as an open document, not the propriety microsoft...

:P

---

### Post by Cannaregio on 2009-02-19
Call me weird, but I quite like the lit format and do  not want to convert it.

I would like to use it better in GNU/linux, see 

[here]("http://ubuntuforums.org/showpost.php?p=6387593&postcount=35") for an older explanation.



I now managed to install MSreadersetup.exe through wine on a small ATOM netbook in order to have at hande, and read, my (huge) collection of lit books.



I had to use fedora instead of ubuntu for my HP dot netbook because of the infamous wifi problems with the Atheros AR24R2x, but I noticed that the installation didn't work out unless you also copy, inside the MSReader subdirectory, in .wine/drive_C/Program files, the "real" msvcirt.dll.



Once you do that, you can ignore the activation crap and just follow the instructions  [in the previous post]("http://ubuntuforums.org/showpost.php?p=6387593&postcount=35") in order to create your library index.



Enjoy!

---

### Post by ak331 on 2009-08-09
I tried the method described and it did not work. although I could install the msreader using msreadersetup from microsoft. I tried to add lit files in the command line but it did not work. Finally i copied the lit files in the MSreader folder in C: directory and presto it showed up in the library and can be read without any problems. these files have to be in the msreader folder for reader to recognize the lit files.

---

### Post by CyberMeg22 on 2010-05-30
Does anyone know where I can get This? I get a 404. I need the libtommath in order to then go to Calibre . See: [http://f241vc15.wordpress.com/2008/05/06/reading-e-books-in-linux/](http://f241vc15.wordpress.com/2008/05/06/reading-e-books-in-linux/)

The instruction is** first this:**
wget [http://ace-host.stuart.id.au/russell/files/debian/sarge/libtommath/libtommath_0.37-1_i386.deb](http://ace-host.stuart.id.au/russell/files/debian/sarge/libtommath/libtommath_0.37-1_i386.deb)
sudo dpkg -i libtommath_0.37-1_i386.deb

**Then**: 
wget [http://ace-host.stuart.id.au/russell/files/debian/sarge/libtommath/libtommath_0.37-1_i386.deb](http://ace-host.stuart.id.au/russell/files/debian/sarge/libtommath/libtommath_0.37-1_i386.deb)
sudo dpkg -i libtommath_0.37-1_i386.deb**and finally**:
wget [http://ace-host.stuart.id.au/russell/files/debian/sarge/****/****_1.8-1_i386.deb](http://ace-host.stuart.id.au/russell/files/debian/sarge/****/****_1.8-1_i386.deb)
sudo dpkg -i ****_1.8-1_i386.debAnyone?
Tx, CyberMeg22

---

### Post by CyberMeg22 on 2010-05-30
Does it matter if one uses an newer version of libtommath?
[http://f241vc15.wordpress.com/2008/05/06/reading-e-books-in-linux](http://f241vc15.wordpress.com/2008/05/06/reading-e-books-in-linux)

This advice sues an older version of libtommath, but the .40 may not work with these instructions. And why is Calibre/ **** predicated on Libtommath?

---

### Post by CyberMeg22 on 2010-05-30
Hi folks, 
as you would have gathered, I need help getting .lit to work, via the c lit route. hit some problems sourcing libtommath 0.37-1_i386.deb 

Any other source?
Tx!
CM22

---

### Post by graphius on 2010-05-30
> I need the libtommath in order to then go to Calibre
should be in the repositories
> sudo apt-get install libtommath
I can't remember which version I originally installed calibre, but I just did a **_sudo apt-get install calibre_** if I recall

---

### Post by mikewhatever on 2010-05-30
How about the simple **sudo apt-get install calibre**

---

