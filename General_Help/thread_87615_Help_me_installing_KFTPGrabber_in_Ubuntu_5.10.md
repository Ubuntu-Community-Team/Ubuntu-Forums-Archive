---
title: "Help me installing KFTPGrabber in Ubuntu 5.10"
date: 2005-11-08
forum: General Help
---

### Post by k0An on 2005-11-08
Hello,

This is my first post as a member of this forum and great Ubuntu community. So, this is also a BIG HELLO to any1 :) 

I'm not a 100% newbie to linux, if I've spent already a lot of time in "playing" with different linux distro in the past 2years. Anyway, i'm more pleased by GUI than command line window ;)

I've tried Ubuntu 5.04 and upgraded to 5.10 only 1 week ago, and I have to admit i'm very satisfied. Robust, smooth and friendly are few of the great characteristics I've found in Ubuntu. In reality, I like debian-hearted linux, but i always did tryKDE based GUI linux (Xandros, Linspire, Mepis, Knoppix, and also Suse), and experienced ONLY troubles. Gnome gives the best of linux I finally, without KDE strange behaviours, like in Kubuntu 5.10 I did try just before Ubuntu.

Anyway, here I come with the very last feature i miss in linux : 
A very GOOD FTP client.
I've tried MANY of them, with and without GUI (gFTP, Kbear, IglooFTP, lftp, Nftp, kasablanca, Nautilus, Konqueror, Wine + win32 FTP clients, etc...) and NONE offered me what I'm looking for:
- SSL connection (both conection and file transfer)
- FXP transfer
- Bookmarks
- Queue
- File transfer analysis (speed, time left, sfv check, etc...)
- Stability OF COURSE
- Command line for different FTP server (ioFTPd, glFTPd, RaidenFTPd)
- Support for special letters in login, pass, path and address (like & also space).

The closest to "prefection" was lftp, but unfortunatly the support for special letters in login, pass, path and address (like & also space) was not possible (according to my tries). Moreover, lftp manual is a pain-in-the-ass to read and understand!

I've searched for other clients, found some here ([http://www.linuxrsp.ru/win-lin-soft/table-eng.html)](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)), but none satisfiying.

BUT, i've discovered KFTPGrabber, one closest to FlashFXP in windows (i'm a 10-years windows user), that does offers - or seems to offer  - what i'm looking for.
I did downloaded the tar.bz2 file but I'm not aware enough of the command-line process to install it with options required for Ubuntu (gcc, kde base lib, etc...).
I did search the web, as well as the official site ([http://kftpgrabber.sourceforge.net/](http://kftpgrabber.sourceforge.net/)) but I didn't find some details to help me installing it in Ubuntu.
O course, I've searched the Ubuntu forum too, and I saw some of you have already tried and successfully installed KFTPGrabber ([http://www.ubuntuforums.org/showthread.php?t=37278&page=2&highlight=kftpgrabber)](http://www.ubuntuforums.org/showthread.php?t=37278&page=2&highlight=kftpgrabber)), but NO explications were given to help me.

So, here is the reason why I do this topic, to find some detailed help for installing KFTPGrabber (prefered v0.7.0-beta1 to other past versions) within Ubuntu 5.10.

Thank you for reading, I hope I'm clear enough and someone will help me.

Cheers,
k0An

---

### Post by mustang on 2005-11-08
I know exactly how you feel. There is no real alternative to FlashFXP under linux. Although this doesn't help you with KFTPGrabber, if you don't get it to work, use wine and emualte flashfxp **2.1**, not the new one (3.0 I believe?)

It's still a little buggy but it's better than nothing.

---

### Post by k0An on 2005-11-08
mustang,

Thank you for your fast response.
I did try Wine 0.9 + FlashFXP 2.x, and it crashed while logging at any site I tried. No joy...

I'm gonna try FTPGrabber all alone, and maybe find my own answers...

Cheers,
k0An

---

### Post by k0An on 2005-11-08
weird things happen:

$ sudo ./configure --prefix=`kde-config --prefix`

gives me an error saying I don't have acceptable C compiler in path.

But gcc 3.3.4 & 4.x.x are installed!!!!

Maybe I need to use special option commands to force a better C compiler checking, but i'm not used to such a task..

any idea?

---

### Post by k0An on 2005-11-09
except gcc, what seems to be necessary for installing KFTPGrabber in Ubuntu 5.10 ?

---

### Post by k0An on 2005-11-09
1 Idea is coming....:

from KFTPGrabber site, i've read deb package are available for Kubuntu:

```
KUbuntu repository
To get the latest packages, put this in your sources.list:

deb http://dinton.no-ip.org/ kubuntu main
deb-src http://dinton.no-ip.org/ kubuntu main
```

is it possible to use them within Ubuntu and what should I need to make it work?

Cheers,
k0An

---

### Post by dominik on 2005-11-11
i use Kubuntu, but this works for me:

>  	
svn co -N svn://anonsvn.kde.org/home/kde/trunk/extragear/network
cd network
svn up kftpgrabber
svn co svn://anonsvn.kde.org/home/kde/branches/KDE/3.5/kde-common/admin
make -f Makefile.cvs
./configure --prefix=`kde-config --prefix` --enable-debug=full
./configure
make
sudo make install


---

### Post by mustang on 2005-11-16
[QUOTE=k0An]mustang,

Thank you for your fast response.
I did try Wine 0.9 + FlashFXP 2.x, and it crashed while logging at any site I tried. No joy...

I'm gonna try FTPGrabber all alone, and maybe find my own answers...

Cheers,
k0An[/QUOTE]

Sorry for the late response.

Really? I'm using FlashFXP 2.1 and it runs fine. Are you sure you're using the latest wine version?

---

