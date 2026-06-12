---
title: "micretek 4850 scanner unsuported by sane"
date: 2018-11-05
forum: Hardware
---

### Post by oneleded on 2018-11-05
i was using Synaptic Package Manager to down load XSANE, to see if this would work..  while downloading, i knocked the power cord out of my PC, and the download was interrupted. now i cant use synaptic manager. i get an error code.
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

this has more options than i know how to do, to fix the problem. the 2nd command doesnt work. ()  seems to cause a problem. well,, that is where i am at,, stuck..

---

### Post by Autodave on 2018-11-06
I am confused: what second command?  There is only one command to run and that normally will fix everything.

Losing power will upgrading anything is not good.  You may have a system that cannot be fixed at this point.  How much of a hassle would it be to reinstall?  You can use the installer to gain access to any file on the HD and back them up to an external source first.

---

### Post by oneleded on 2018-11-06
i thought -catch->open() failed, please report., was a second command..
when you said one command would fix everything,, it got me to thinking.. the site i got that of of, didnt have sudo in the command line, or i just copied it wrong. WHEN i used sudo; 
sudo dpkg --configure -a  ; everything when back to normal.
the only thing that wasnt working was,, Snaptic Package Manager.. now it does
the way i write confuses me, is true. thanks for the help.. 

what i wrote above, some is wrong. i did use sudo in the command line.. i think i had to sign in before anything would happen. i will double check this, and then may have to re-edit this thread.

---

### Post by oneleded on 2018-11-09
[http://sane-project.org/sane-mfgs.html](http://sane-project.org/sane-mfgs.html)  ;; while at this site i found out my scanner is not supported by sane, and sand back door wont work. at least that is what i believe i found. now i need to find out if there is a work around. help
did i post this thread in the right place or should it be in hardware?

---

### Post by oneleded on 2018-11-10
bump

---

### Post by SeijiSensei on 2018-11-11
Try VueScan.

[https://www.hamrick.com](https://www.hamrick.com)

---

### Post by slickymaster on 2018-11-11
*Thread moved to **Hardware**.*

---

### Post by oneleded on 2018-11-15
thanks

---

### Post by oneleded on 2018-11-16
> **SeijiSensei said:**
> Try VueScan.

[https://www.hamrick.com](https://www.hamrick.com)
i am not handling, my downloads properly.  proper folder and such. what is the correct path? should i ask this somewhere else?

---

### Post by oneleded on 2018-11-23
i downloaded VueScan.. now for the installation part. the download is in archive manager. i also have it on the desktop.
i want to know if these commands are correct, to install VueScan?
$ wget -c [www.hamrick.com/files/vuex3292.tgz](www.hamrick.com/files/vuex3292.tgz)
$ tar -xvf vuex3296.tgz
 $ cd VueScan 
 $ sudo chmod +x vuescan 
 $ ./vuescan
this didnt work for me..

---

### Post by oneleded on 2018-11-24
> **SeijiSensei said:**
> Try VueScan.

[https://www.hamrick.com](https://www.hamrick.com) i read i need to install wine for VueScan to work.. that was for linux mint in 2009, near 10 years ago. no mention of lubuntu, with that site. i have looked on the internet, for the command, to install,, either from the desktop, or, archive manager. the internet ranks searches anymore, so i get the same thing over and over. i did manage to get one download to work off the internet. i cant remember how i did it. so i'm stuck for the moment. help

---

### Post by kurt18947 on 2018-11-24
When I use Vuescan, I don't install anything. There are 3 files, the VueScan executable and a couple others. I just copied the 3 files into a folder on the hard drive where I could find them again, made sure the main Vuescan file was marked executable and created a launcher on the desktop. Click the launcher and VueScan starts. Simples.

---

### Post by oneleded on 2018-12-05
> **kurt18947 said:**
> When I use Vuescan, I don't install anything. There are 3 files, the VueScan executable and a couple others. I just copied the 3 files into a folder on the hard drive where I could find them again, made sure the main Vuescan file was marked executable and created a launcher on the desktop. Click the launcher and VueScan starts. Simples.
thanks, i will give it a try

---

### Post by oneleded on 2018-12-16
i didnt know you had to pay for Vuescan till tonight.. its not doing anything anyway. i marked files executable. still nothing. i clicked on each file, then properties, then made them excutable..
anyone heard of [Quiteinsane gimp plugin] ?? supposedly if you install this, it will help to find your scanner. i have to get back to tell your what it runs in. KDE? for instance. found it an here ya go..
this is what i found. [QuiteInsane is a graphical frontend for SANE ("Scanner Access Now Easy"). It requires Qt2.2.x or
Qt >=3.0.1 (KDE2/KDE3 optional)].
however, if new scanners are cheaper these days, why not just get a new scanner, linux friendly? 32/64 bit. or something of that nature.

---

### Post by oneleded on 2019-05-24
i havent give up the ghost on this, getting my old scanner to work. there is a back door approach to this. i was close. i will still try. it's the principal of the thing. hope ya understand.
i thought i posted a picture, of where i was at. it dont matter now, as i cant find the bookmark.
linux friendly seems to be a recurring them for obsolete.. nuff said...

---

