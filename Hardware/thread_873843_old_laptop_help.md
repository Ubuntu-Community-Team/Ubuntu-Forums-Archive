---
title: "old laptop help"
date: 2008-07-29
forum: Hardware
---

### Post by rico002 on 2008-07-29
ok im not home right now, 
but i have this old laptop (ibm) and i was told that xubuntu is good for old laptops, and i cant seem to get it to install, there was an OS of windowds xp pro, but i get this message "unmountable boot volume" so i decided to put xubuntu on it, but it wont work, it tries to install and then goes to a black screen, and just stays like that, can someone/anyone please please please hlep me....all help/suggestions would help thanks

it has like 128 mb of ram, ithnk
and like 80 or 60 of hdd

---

### Post by snowpine on 2008-07-29
Hi Rico, if you do indeed have 128 mb of ram, you should install the Xubuntu Alternate CD, which you can download from the same place you got the Live CD. You need 192mb to install using the regular method. Good luck!

---

### Post by snowpine on 2008-07-29
ps You may find this thread helpful: [http://ubuntuforums.org/showthread.php?t=873112](http://ubuntuforums.org/showthread.php?t=873112)

---

### Post by rico002 on 2008-07-29
thanks, ppl 

i got xubuntu from a torrent, and would u suggest visiting the xubuntu site and see if they have it there, or google-ing it...ill try and post all the specs later today after work.

---

### Post by snowpine on 2008-07-29
Assuming you are in the US, here is the link: [http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/8.04/release/](http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/8.04/release/)

Download the file called xubuntu-8.04.1-alternate-i386.iso and there is also a torrent.

The difference is it's a text-based installer rather than graphical, so it needs less ram, but it has the same functionality.

---

### Post by rico002 on 2008-07-29
> **snowpine said:**
> Assuming you are in the US, here is the link: [http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/8.04/release/](http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/8.04/release/)

Download the file called xubuntu-8.04.1-alternate-i386.iso and there is also a torrent.

The difference is it's a text-based installer rather than graphical, so it needs less ram, but it has the same functionality.

yeaaaa....thanks, ill give that shot, thanks again

---

### Post by rico002 on 2008-07-30
ok so i thnk i got installed, but it will take me to the boot screen and login, i do that and then it says sumthing bout sudo and to visit the ubuntu website, and there is a command line but i dont kno wut to do or type there, is this how its going to be, no desktop or anything??????????????????

---

### Post by snowpine on 2008-07-30
> **rico002 said:**
> ok so i thnk i got installed, but it will take me to the boot screen and login, i do that and then it says sumthing bout sudo and to visit the ubuntu website, and there is a command line but i dont kno wut to do or type there, is this how its going to be, no desktop or anything??????????????????

Try typing 'startx' does that work?

If not,it sounds like maybe you installed the command line but not the desktop. That's okay; assuming you are connected to the internet, at the command line, just type

```
sudo apt-get install xubuntu-desktop
```

then enter your password (your normal user password, you do not need a separate root password in ubuntu) and it should install what you need. Reboot the computer and you should get the graphical login.

If things still don't work and you are not connected to the internet, it's possible you chose the wrong option when you installed, in which case you may need to go back to the install disk. We'll cross that bridge if we get to it.

---

### Post by rico002 on 2008-07-30
i get this

failed to fetch cdfrom :[Xubuntu hardy....
pool/main/a/app-install-data-ubuntu/app-install-data_0.5.10.3_all.deb Hash sum mismatch
E: unable to fetch some archives, maybe run apt-get update or try wit --fix-missing

so wut might be the problem

---

### Post by rico002 on 2008-08-02
can anyone help??????????

---

### Post by snowpine on 2008-08-04
> **rico002 said:**
> i get this

failed to fetch cdfrom :[Xubuntu hardy....
pool/main/a/app-install-data-ubuntu/app-install-data_0.5.10.3_all.deb Hash sum mismatch
E: unable to fetch some archives, maybe run apt-get update or try wit --fix-missing

so wut might be the problem

Try 

```
sudo apt-get update
```

---

