---
title: "Please help me. It's a slight emergency."
date: 2008-06-23
forum: Hardware
---

### Post by Milkium on 2008-06-23
I know it's hard, but PLEASE proceed to read this wall of text.
Please if it's possible, answer as quickly as possible, but don't feel too pressured. I understand that this IT is free and you guys are doing it on your own freetime. Thanks.

Anyway.
I'm running Ubuntu Hardy Heron 8.04.
I'm using WINE 1.0.

I have a Brother MFC-240c printer. And I HAVE to get it to work with Linux. Or else I'm dead. (Figure of speech, don't call 911 xD). But seriously. My problem is the driver. According to their website: ( [http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html) ) they don't yet have a driver for Ubuntu.

So I downloaded the XP driver for the printer, and ran the .exe setup file in WINE. Except, it's not working. The error is:

An error occurred during the installation process.
Please restart the computer, and ensure all applications are closed.
-Then reinstall "MFl-pro suite".
(IS026-MakePcfxFile - 1)

What the hell? All applications were closed.
Could it be that I'm using the wrong version of WINE? Perhaps should I upgrade to 2.1?
I also noticed that this error usually occurs at "Writing registry information" or something like that.
So yeah, sorry for making you read all this. But if what I'm trying to do is impossible, is there ANYTHING else that will solve my problem? I just want to print without having to buy a new printer. :(

---

### Post by dfreer on 2008-06-23
EDIT: You can use the debian driver, it should work :D

---

### Post by Milkium on 2008-06-23
> **dfreer said:**
> EDIT: You can use the debian driver, it should work :DYeah. The package called CUPSwrapper or something?
Thanks man. I got it.

BUT. I'm really bad with installing packages. And all the tutorials I've googled didn't help me too much. For some reason, something would go wrong.

So I either need you to walk me through it on AIM or you can do it here too I guess. Pleasseeee. I'm desperate. My summer vacation is riding on this.

---

### Post by Milkium on 2008-06-23
Okay, so I got it, and tried to install it with 

lee@lee-desktop:~$ sudo dpkg -i --force-architecture mfc240ccupswrapper-1.0.1-1.i386.deb

And it gave me

dpkg: error processing mfc240ccupswrapper-1.0.1-1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 mfc240ccupswrapper-1.0.1-1.i386.deb

Huh?

---

### Post by ljonesj on 2008-06-23
down load the .deb file to ur desktop then just click on the file it auto installs for u

---

### Post by Sef on 2008-06-23
> down load the .deb file to ur desktop then just click on the file it auto installs for u

It should install it.  If it doesn't, then it will tell you why.  If it does that, then post that message here.

---

