---
title: "Persistence in Ubuntu 9.04"
date: 2009-07-19
forum: Installation &amp; Upgrades
---

### Post by macintard on 2009-07-19
Hey, I was wondering if the persistence is working in Ubuntu 9.04? I've tried Ubuntu, and Xubuntu and neither work with persistence. My settings are not saved. I'm also wondering where the casper-rw file goes? Pendrivelinux.com does not tell you that I can see, but I'm not exactly an expert at linux and often get quite frustrated with it. I have a Sandisk Cruzer 8GB that is pretty new, so would love to be able to use at least 4GB of that. BTW, is it true you can partition part of that as ext3 or whatever and use that as well? There is so much out there on the internet. Googling hardly brings up anything relevant anymore. I've even tried other search engines like ask.com and no go. Thanks in advance!

---

### Post by JHan816 on 2009-07-19
I am running Ubuntu 9.04 now on my 8GB HP thumb drive with a 4GB casper-rw loop file. It does work for me.  In windows, the installer program "u904.exe" will create a directory called "U904p" with everything in it. 

A default 1GB casper-rw file is in that directory. They also give you links to download a 2,3, and 4 gb casper file on the site. You move the larger casper file in that directory and replace the default 1gb casper file. 

[http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/)

--John

---

### Post by macintard on 2009-07-19
Hey thanks I'll give that a shot! Wine works pretty well, and I'm running Fedora 11 right now and it won't even make a 2GB persistence with it's default LiveUSB creator. I was asked to sbumit a bug report but felt daunted since I think someone would have noticed something like that already and don't really have time to do that sort of thing. I appreciate it and going to give that a shot. Have a great week!

Joe

---

### Post by Mighty_Joe on 2009-07-20
I ran into a [couple ]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/321544")of [bugs ]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/277865")with Ubuntu's Live USB Creator. I ended up just installing Ubuntu to my flash drive.  It's faster than using the Live CD image and you can use all the space on your drive.  Have a look at my [post here]("http://ubuntuforums.org/showthread.php?t=1193680") if you are interested.

---

### Post by macintard on 2009-07-20
> **JHan816 said:**
> I am running Ubuntu 9.04 now on my 8GB HP thumb drive with a 4GB casper-rw loop file. It does work for me.  In windows, the installer program "u904.exe" will create a directory called "U904p" with everything in it. 

A default 1GB casper-rw file is in that directory. They also give you links to download a 2,3, and 4 gb casper file on the site. You move the larger casper file in that directory and replace the default 1gb casper file. 

[http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/)

--John


That .exe had issues making the USB drive bootable since I ran it with WINE and I don't have windows...so I am wondering if it works with DOSBOX? I suppose I can try..thanks!

Joe

---

### Post by JHan816 on 2009-07-21
> **macintard said:**
> That .exe had issues making the USB drive bootable since I ran it with WINE and I don't have windows...so I am wondering if it works with DOSBOX? I suppose I can try..thanks!
 
Joe
 
I don't know about Wine but you will get permission errors using Vista when it gets to the point of making the USB drive bootable. It does copy all the files to the USB pendrive. 
 
What I did to complete the procedure -- go to the directory in the **USB drive** that the exe file created, and right click on the makeboot.bat file and select "Run as administrator". At that point it made the usb drive bootable.  
 
Just make sure you are in the USB drive's directory when you run the makeboot batch file. It does ask you the drive letter.
 
I have done this Pendrivelinux procedure for many versions of Linux just to test and it worked very well. 
 
Now I have to decide which one I like......
 
--John

---

### Post by JHan816 on 2009-07-21
> **Mighty_Joe said:**
> I ran into a [couple ]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/321544")of [bugs ]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/277865")with Ubuntu's Live USB Creator. I ended up just installing Ubuntu to my flash drive. It's faster than using the Live CD image and you can use all the space on your drive. Have a look at my [post here]("http://ubuntuforums.org/showthread.php?t=1193680") if you are interested.
 
Joe, Thanks for the information. Looks like a better use of all the drive's space and a longer life for it too. 
 
--John

---

### Post by squashpup on 2009-08-23
[http://ubuntuforums.org/showthread.php?t=1247384&highlight=usb+persistence](http://ubuntuforums.org/showthread.php?t=1247384&highlight=usb+persistence)

---

