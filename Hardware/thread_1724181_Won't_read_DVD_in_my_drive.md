---
title: "Won't read DVD in my drive?"
date: 2011-04-08
forum: Hardware
---

### Post by pivotraze on 2011-04-08
My DVD drive will not read a PS2 disc I put in?

I know it's DVD (I can play normal DVDs on it)

I am trying to use PCSX2, but my computer won't read the DVD drive so I can make an ISO out of the disc :\

PCSX2 Version: 0.9.7.0
Ubuntu Version: Ubuntu 11.04 beta 1
Computer Model: Gateway MX8734

---

### Post by wolfen69 on 2011-04-08
As far as I know, PS2 disks are made in a proprietary format, and you need a PS2 to read them. I don't believe they are regular DVD's.

---

### Post by pivotraze on 2011-04-08
It reads fine on my bro's Windows PC :\

---

### Post by wolfen69 on 2011-04-08
> **pivotraze said:**
> It reads fine on my bro's Windows PC :\

OK. Maybe installing **libdvdcss2** would help. People need to install that to watch copy protected DVD's.

---

### Post by pivotraze on 2011-04-08
> **wolfen69 said:**
> OK. Maybe installing **libdvdcss2** would help. People need to install that to watch copy protected DVD's.

sudo apt-get install cody@cody-MX8734:~$ sudo apt-get install libdvdcss2
[sudo] password for cody: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libdvdcss2' has no installation candidate

---

### Post by SeijiSensei on 2011-04-08
> **wolfen69 said:**
> As far as I know, PS2 disks are made in a proprietary format, and you need a PS2 to read them. I don't believe they are regular DVD's.

wolfen69 is correct.  If your brother's machine somehow "plays" a PS2 disc, he hacked something to do so.  

libdvdcss2 and friends only help with ordinary commercial DVDs.

---

### Post by pivotraze on 2011-04-08
No offense to my brother or anyone here, but my brother knows nothing of computers. Hacking is not in his knowledge base. 

All he has to do is pop a disc in his dvd drive, and all the contents are readable. Not that he can "do" anything with that disc, because PCSX2 doesn't work with DX11 ha. 

If you look at my log, libdvdcss2, I get:
E: Package 'libdvdcss2' has no installation candidate

Are you taking into account that it is Ubuntu 11.04?

---

### Post by wolfen69 on 2011-04-08
For 11.04 do:
```
sudo apt-get install libdvdread4
```
then
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

If it comes down to it, you might be able to extract the image from a windows pc and transfer it to your ubuntu machine.

---

