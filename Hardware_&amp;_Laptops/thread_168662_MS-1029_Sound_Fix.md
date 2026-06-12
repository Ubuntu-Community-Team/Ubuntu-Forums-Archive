---
title: "MS-1029 Sound Fix"
date: 2006-04-30
forum: Hardware &amp; Laptops
---

### Post by WhiteHorse on 2006-04-30
To get sound going on the MS-1029 aka MSI Megabook 635 you have to recompile alsa with atiixp options. Do this as follows:

1. Download latest alsa source code: I used 

[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.10.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.10.tar.bz2)

2. Move that file to your source directory and compile: I used

cd ~/Desktop
sudo su
mv alsa-driver-1.0.10.tar.bz2 /usr/src
cd /usr/src
tar jxvf alsa-driver-1.0.10.tar.bz2
cd alsa-driver-1.0.10
./configure --with-card=atiixp
make
make install

3. Reboot and enjoy :)

---

### Post by crazy22 on 2006-12-24
> **WhiteHorse said:**
> To get sound going on the MS-1029 aka MSI Megabook 635 you have to recompile alsa with atiixp options. Do this as follows:

1. Download latest alsa source code: I used 

[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.10.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.10.tar.bz2)

2. Move that file to your source directory and compile: I used

cd ~/Desktop
sudo su
mv alsa-driver-1.0.10.tar.bz2 /usr/src
cd /usr/src
tar jxvf alsa-driver-1.0.10.tar.bz2
cd alsa-driver-1.0.10
./configure --with-card=atiixp
make
make install

3. Reboot and enjoy :)


is it working with msi megabook s420 (1024) also .....
Thanks!

---

### Post by woland on 2007-02-09
Thanks for the HOWTO!

Well it does make the sound card working, however there is the annoying problem of jack sensing not working. When I plug the headphones, I get sound from both speakers and headphones.

I've tried alsa versions 1.0.10 and 1.0.14rc2. 

I have MSI MegaBook S420, running Ubuntu Edgy.

---

### Post by zazkia on 2007-02-21
Hiya woland, I've got thesame MSI 420 but still no sound at all, despite installing & compiling whitehorses driver properly. The IEC is turned off (in alsamixer) and I've chmodded dev/dsp and now the well of ideas run dry. Any hints?

---

### Post by crazy22 on 2007-03-10
> **zazkia said:**
> Hiya woland, I've got thesame MSI 420 but still no sound at all, despite installing & compiling whitehorses driver properly. The IEC is turned off (in alsamixer) and I've chmodded dev/dsp and now the well of ideas run dry. Any hints?

Have tou tried this:

[http://www.ubuntuforums.org/showthread.php?t=329412](http://www.ubuntuforums.org/showthread.php?t=329412)

---

### Post by zazkia on 2007-03-14
Aye, that we did. But of no avail. Also we've just updated the BIOS (which was a lot of trouble, because the MSI live update doesn't work the way it should) to the 7.something version. And still no sound. :(

---

### Post by zazkia on 2007-03-19
Crazy's recipe actually did work perfectly :) 
The problem was that I never tested whether we got sound through the speaker  outlet. 

There are some error outputs in the kernel that lead us to add a position fix in the  which caused the login sound to repeat over and over again. As I never recognized the login sound into the repeated login sound I thought it was err well...some accidental...  

anyhow the moral of the story: don't try to outsmart the crazy!


:guitar: 

WOOOOHOOO Sound.... 

Anyhow I read somewhere that it is already known by alsa that the channel routing something bla bla prevents the sound from going through the speaker. So I have high hopes that it'll work properly one day.

---

